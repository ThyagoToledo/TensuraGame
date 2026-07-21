# TensuraGame

RPG 2D em pixel art inspirado no universo de Tensura, desenvolvido na IgnisEngine.

O projeto combina exploracao, dialogos e cutscenes orientadas por dados, combate por turnos e progressao narrativa. Modos de horda sao reservados a momentos da historia em que Rimuru enfrenta grupos grandes.

## Estado atual

- menu e despertar na Caverna do Selo;
- Rimuru Slime como ator persistente unico;
- cutscene inicial com Grande Sabio e confirmacao manual;
- exploracao, colisao, interacoes e galeria;
- primeiro encontro narrativo com Veldora;
- saida semantica da caverna apos Veldora;
- primeiro contato conversacional com os goblins na Floresta de Jura;
- cutscene goblin em pixel art com seis poses, alpha binario e escala inteira `3x`;
- replay deterministico da Caverna do Selo ate a floresta, com checkpoints
  semanticos que localizam a primeira divergencia;
- modelo de campanha, documento neutro, codec e cadeia de migracao para saves
  versionados, ainda sem escrita em disco no fluxo jogavel;
- batedor goblin, anciao pre-nomeacao e lobos pre-nomeacao preparados em quatro
  direcoes para a proxima fatia da aldeia;
- cutscenes sem listeners duplicados apos recompilacao, com fundo cinematografico
  cobrindo o viewport e absorcao animada de Veldora;
- arquitetura separada em `GameFlowController`, `ExplorationDirector`,
  `CutsceneDirector` e `GoblinContactDirector`.

## Estrutura

- `TensuraGame.ignis`: cena e configuracao do projeto;
- `project/`: assets, scripts, dados, bibliotecas e prefabs usados em runtime;
- `domain-lib/`: regras puras e testes do dominio;
- `tools/`: geradores auxiliares de assets e audio;
- `build.json`: configuracao de build da IgnisEngine.

## Abrir na IgnisEngine

1. Use uma versao atual da IgnisEngine.
2. Coloque este repositorio em `IgnisEngine-main/projects/TensuraGame`.
3. Abra `TensuraGame.ignis` no editor.
4. O projeto precisa manter a pasta `project/` ao lado do arquivo `.ignis`.

O editor deve mostrar o mapa e o objeto `Rimuru` na Hierarchy antes de qualquer Play.

## Testes

Dominio:

```powershell
mvn -q -f domain-lib/pom.xml test
```

No checkpoint de 20/07/2026, o dominio possui `88` testes verdes. A suite
completa da IgnisEngine possui `149` testes verdes e os `6` scripts do jogo
compilam pelo MCP.

## Pipeline de sprites direcionais

O extrator espera uma fonte alpha em grade `3x4`: colunas `walk A`, `idle` e
`walk B`; linhas `down`, `left`, `right` e `up`. Ele gera frames com pivot
centro-inferior, nearest-neighbor, paleta reduzida e uma folha de QA.

Requer Python com Pillow:

```powershell
python tools/extract_directional_sheet.py `
  --input project/assets/source/personagem_sheet_alpha.png `
  --output-dir project/assets/sprites/npcs/personagem `
  --prefix personagem `
  --canvas 64
```

## Projeto de fã

Este e um projeto de fã, nao comercial e nao oficial. Tensura e seus personagens pertencem aos respectivos titulares. Dialogos e implementacoes do jogo sao autorais e adaptados para esta experiencia.
