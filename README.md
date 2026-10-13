# A Jornada de Moacir

Jogo de tabuleiro digital inspirado no "Jogo da Vida", feito em **GameMaker Studio 2** (GML) para **PC (Windows)** e **Android**. O jogador gira uma roleta, anda pelas casas de um tabuleiro com caminhos alternativos e enfrenta eventos que mexem com dinheiro, poupança e mesada. O foco é a educação financeira para o público infantil, por isso os valores são mantidos baixos e fáceis de contar.

> **Status:** em desenvolvimento (projeto de TCC).

---

## Funcionalidades

**Jogabilidade**
- Roleta de 1 a 10, acionada por clique/toque ou pela barra de espaço.
- Movimento do personagem casa a casa, com efeito elástico (squish) e espelhamento conforme a direção.
- Bifurcações no tabuleiro, com **popup de decisão** para escolher o caminho. Algumas escolhas têm custo (por exemplo, fazer o cursinho).
- Casas obrigatórias, que interrompem o movimento mesmo com passos sobrando (como o fim do tabuleiro).
- Casa de **fim de jogo**, com resumo do dinheiro final.

**Eventos de casa** 
- Ganhar e perder dinheiro, ganhar Moeda do Moacir, pular rodada e avançar casas.
- Mesada: iniciar, aumentar e receber.
- Poupança com slider, loteria (escolha de 1 a 10) e escolha de passatempo.

**Progressão e personalização**
- **Skins:** carrossel de personagens, compradas com o dinheiro obtido nas partidas. As bloqueadas aparecem em silhueta preta. Cada skin tem um sprite único.
- **Seleção de tabuleiros:** carrossel com prévia, visão expandida (nome, dificuldade, descrição e botão Jogar).
- **Placar local (Top 5)** e **placar online (Top 10)**, em abas.
- **O cadastro de nome** é feito assim que o jogo inicia.

**Interface e sistema**
- Menu de pause e menu de opções: volume (slider), tela cheia (somente Windows), mudar nome e resetar progresso (somente na tela de título).
- Transição de telas com efeito de pixelação.
- Uma música diferente por sala.
- Suporte a mouse, toque e teclado.

---

## Como o jogo funciona

1. Na primeira execução, o jogo pede o nome do jogador.
2. Na tela de título, o jogador pode jogar, trocar de skin, ver o placar ou abrir as opções.
3. Na tela de seleção, pode escolher entre os dois tabuleiros.
4. No tabuleiro, gira a roleta e o personagem anda a quantidade sorteada de casas.
5. Ao parar numa casa de evento (ou ao passar por uma obrigatória), um popup mostra o que aconteceu e só aplica o efeito quando o jogador clica em **OK**.
6. Ao chegar na ultima casa, o dobro da poupança é somado ao dinheiro, o resultado é mostrado e o recorde é checado nos dois placares (online e offline).

---

## Sistema de eventos das casas

**Tipos implementados**

| Tipo | Efeito |
|---|---|
| `ganhar dinheiro` / `perder dinheiro` | Soma ou subtrai o valor ao clicar OK. |
| `ganhar moeda` | Soma Moedas do Moacir (substitui o termo "LIFE"). |
| `pular rodada` | O próximo giro da roleta é perdido. |
| `mover casas` / `avancar espacos` | Avança casas ao clicar OK e aplica a casa onde parar. |
| `iniciar mesada` / `aumentar mesada` / `ganhar mesada` | Define, aumenta ou paga a mesada. |
| `guardar poupanca` | Slider de depósito, até o limite da casa e o dinheiro disponível. |
| `loteria` | Aposta num número. Resolve no próximo giro: ganha o prêmio ou perde R$10. |
| `escolher passatempo` | Escolha de música, artes ou dança (`global.passatempo`). |
| `decisao caminho` | Popup de bifurcação com custo opcional na opção A. |

---

## Dados salvos (`config.ini`)

| Seção | Chaves |
|---|---|
| `audio` | `volume` |
| `video` | `fullscreen` |
| `player` | `nome`, `dinheiro` (saldo para comprar skins) |
| `skins` | `selecionado` e uma chave por skin |
| `ranking` | `nome`, `pontuacao`, `sprite` (placar local de 1 a 5) |

O **Resetar progresso** (visível só na tela de título) apaga nome, saldo, skins e o placar local. O placar online não é afetado.

---

## Créditos e licença

- **Programador:** `Henrique Silveira`
- **Artes:** `Gabriel Ferreira & Guilherme Negro`
- **Auxíliar Administrativo:** `João Furini`
- **Orientador:** `Prof. Dr. Carlos Alberto Diniz`
- **Licença:** [CC BY-NC 4.0](LICENSE.TXT) — uso e adaptação permitidos com atribuição e sem fins comerciais.
