# FFXIV Language Pack (PT-BR)

Tradução de Final Fantasy XIV para o português do Brasil, servida dentro do jogo pelo
[Gubal Library](https://github.com/ashdam/gubal-library). Este repositório é o corpus: o texto
traduzido, o glossário que o rege e as releases do pack.

## O que há aqui

| | |
|---|---|
| `corpus/` | Uma linha para cada linha do jogo, espelhando `ffxiv-corpus-en/corpus/`. |
| `glossary/` | Os termos decididos, o registro de cada falante e as observações feitas na tela. [docs/glossary.md](docs/glossary.md). |
| `docs/` | Referência: macros, planilhas, glossário, processo. |
| `pack.json` | Quem é este pack e onde publica. |

## Como se traduz uma linha

Cada arquivo de `corpus/` tem o mesmo caminho do seu homólogo em `ffxiv-corpus-en/corpus/`, e cada
linha a mesma `gameKey`. Preenche-se `target`; `gameKey`, `hash` e `gameVersion` não se tocam.

```json
{ "gameKey": "quest/041/AktKba101_04102#TEXT_AKTKBA101_04102_ALFONSE_000_002", "hash": "95F09EC7040EEA03", "target": "" }
```

O inglês, o francês e o japonês dessa linha estão no arquivo homólogo de `ffxiv-corpus-en`. As
macros `<...>` são copiadas tal como estão. Um `target` vazio significa «não traduzido» para todo
mundo; nunca um marcador com texto.

Tutorial com capturas de tela: https://eorzea-in-spanish.ashdam.workers.dev/translate/pt-br.html

## O que está traduzido

Nada, ainda. A tabela é gerada pela contagem do projeto e não se edita à mão.

## Uma linha mal traduzida

https://github.com/ashdam/ffxiv-language-pack-pt-br/issues
