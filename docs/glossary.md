# Glossary

Reference. What lives in `glossary/`, the same files in every language repository. `<code>` is the
`language` of `pack.json` (`es-ES`, `it`, `pt-BR`, `pl`): it names the rendering column, and no tool
reads a fixed `es`.

The glossary outranks the corpus. It is consulted before measuring; a count over the delivered text
decides only where the glossary is silent.

## overrides.json

Hand-decided terms, on top of the generated `ffxiv-corpus-en/glossary/characters.json`, `places.json` and `tribes.json` (names that exist as sheet
rows). Two arrays: `terms` and `emotes`. A term:

```json
{
  "en": "Temple Knights",
  "fr": "éclaireur des templiers",
  "ja": "捜索中の神殿騎士",
  "es-ES": "los Caballeros del Templo",
  "protect": false,
  "note": "The order, not any knight of it; the singular is a description and stays lower case."
}
```

| Field | What it is |
|---|---|
| `en` | The characters the corpus contains. The key every check matches on. |
| `fr`, `ja` | The official renderings, copied from observed lines. Empty when that language uses no fixed term. |
| `<code>` | The agreed rendering in this language, used everywhere. |
| `protect` | `true` = reproduce the English verbatim; `false` = translate, and `<code>` is what it becomes. |
| `forbidden` | Renderings the validator rejects, with the plural allowed: `["mercader"]`. |
| `note` | The ruling and the traps. Never the history. |

An entry whose `en` starts with `_` is a convention or a divider, not a term: `_comment`,
`_deferred_place_names_comment`, `_divider`. A divider is a heading and carries no rule.

An emote is `en` and `<code>` only: stage directions FFXIV writes as on-screen text, `\<sigh>`.

## register.json

How each speaker addresses the player and, where it matters, other characters. JSONC: the rules
are `//` comments at the top. Keys are the normalised speaker token, letters and digits upper-cased:
`Kan-E-Senna` is `KANESENNA`.

```jsonc
"ALFONSE": {
  "player": "tú",
  "others": { "GAIUS": "usted" },
  "confidence": "high",
  "why": "Werlyt: elder brother of the orphans. Formal, principled voice.",
  "voice": "Never contracts; addresses officers by rank.",
  "examples": ["quest/041/AktKba101_04102#TEXT_AKTKBA101_04102_ALFONSE_000_002"]
}
```

`confidence` says how much the entry weighs: `high` and `medium` are measured against the corpus,
with the reason in `why` and the rows in `examples`; `low` has no rows cited and is followed until
the scenes contradict it. `voice` is the speaker's tic: an accent, a catchphrase, a way of naming
themselves. The axis in `player` is the language's own; the file says which forms exist.

## What is not here

A speaker's gender is a fact of the game and the same for every language, so
`gender-overrides.json` lives beside the English corpus, in `ffxiv-corpus-en/glossary/`, keyed by the
same speaker token as `register.json`.

## label-widths.json

What was seen to fit or overflow on screen, per row, as text and never as pixels. `fits` raises the
floor of the slot, `overflows` lowers its ceiling, and the validator measures every candidate against
both. An observation, not a decision, which is why it is not inside `overrides.json`.

```json
{ "gameKey": "Addon#1075", "fits": "Bono de grupo", "overflows": "Bonificacion de grupo", "note": "Party member panel." }
```

## toponym-reviews.json

Place-name findings somebody has already looked at, so the validator does not ask twice. Being in
the file is being reviewed; `review_action` says whether the finding is shown again. `en` and
`target` are fingerprints copied from the validator's report, never recomputed. Translators never
edit it: they deliver reviews and the coordinator merges them.

## A new language

What is copied from an existing repository, and what starts empty:

| File | Copy |
|---|---|
| `overrides.json` | The `protect: true` terms with `en`, `fr`, `ja` and `protect`; no rendering, no note. They say what stays English. |
| `register.json` | The `//` rules with the language's own forms, and an empty `register`. |
| `label-widths.json`, `toponym-reviews.json` | The comments and an empty array. |
