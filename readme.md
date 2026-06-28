# Projeto 6: "Ghostgame" 

Este projeto é uma modificação do jogo "Ghost" para dois jogadores, desenvolvido em Jack (do livro do NAND2TETRIS) para a Unidade 6 da disciplina de Elementos de Sistemas Computacionais. O tema foi adaptado para a dinâmica de Policial e Ladrão, incluindo mecânicas de coleta, sistema de colisão e mapas variados.

## Como Jogar

O jogo é multiplayer local (ambos os jogadores dividem o mesmo teclado).

**Jogador 1 (Policial)**
Objetivo: Capturar o ladrão antes que o tempo esgote ou que ele fuja com o dinheiro.
* **Mover:** Setas Direcionais (Cima, Baixo, Esquerda, Direita)
* **Parar:** Tecla `.` (Ponto)

**Jogador 2 (Ladrão)**
Objetivo: Roubar os 5 sacos de moedas espalhados pelo mapa ou sobreviver até o tempo acabar.
* **Mover:** Teclas W, A, S, D
* **Parar:** Tecla `E`

## Funcionalidades Implementadas

* **Sprites Customizados:** Arte gerada utilizando manipulação direta de memória (`Memory.poke`) para desenhar a viatura e o ladrão.
* **Mapas Dinâmicos** O sistema sorteia um entre três layouts de mapas diferentes a cada inicialização.
* **Colisão de Cenário:** Os blocos e as paredes contem colisão, bloqueando a movimentação automática caso o jogador tente atravessá-los.
* **Condição de Vitória Alternativa:** A coleta das 5 moedas garante a vitória instantânea ao Ladrão.
* **Seed Aleatória Dinâmica:** A semente (seed) do gerador pseudoaleatório é definida pelo tempo de reação do usuário na tela de início, garantindo partidas únicas.
* **Vantagem Inicial:** O Ladrão recebe 3 segundos no início da rodada para se distanciar antes do Policial ser liberado para agir.
* **Interface e Reinício:** O jogo exibe o resultado da rodada no centro da tela, reiniciando automaticamente após 3 segundos. Pressionar `ESC` encerra a aplicação.

## Estrutura de Arquivos

* `Main.jack`: Inicializa a classe controladora e encerra o loop do jogo.
* `GhostGame.jack`: Gerencia a lógica central, captura de teclado, estágios do relógio e sistema de colisões.
* `Map.jack`: Responsável por desenhar as paredes, posicionar os itens e validar as coordenadas de colisão.
* `Ghost.jack`: Representa a viatura policial (P1) e gerencia suas coordenadas no grid.
* `Thief.jack`: Representa o ladrão (P2) e gerencia sua movimentação.
* `Random.jack`: Gerador de números pseudoaleatórios utilizado no sorteio de mapas e pontos de spawn.

## Como Executar no Simulador

1.  Compile o diretório do projeto utilizando o utilitário `JackCompiler`.
2.  Abra o `VMEmulator` e carregue a pasta raiz (*File -> Load Program*).
3.  Ajuste a velocidade da animação para **Fastest**.
4.  No painel de fluxo (Animate), selecione a opção **No Animation** para garantir a fluidez do jogo.
5.  Clique em executar (Play) e divirta-se!