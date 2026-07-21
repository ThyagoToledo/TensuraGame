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

No checkpoint de 20/07/2026, o dominio possui `68` testes verdes. A suite
completa da IgnisEngine possui `148` testes verdes e os `6` scripts do jogo
compilam pelo MCP.

## Projeto de fã

Este e um projeto de fã, nao comercial e nao oficial. Tensura e seus personagens pertencem aos respectivos titulares. Dialogos e implementacoes do jogo sao autorais e adaptados para esta experiencia.
