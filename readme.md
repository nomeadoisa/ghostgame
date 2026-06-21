# Projeto 6 - Policial e Ladrão Multiplayer (Nand2Tetris)

Este projeto é uma versão modificada do jogo Ghost para dois jogadores, desenvolvida em Jack para a unidade 6 da disciplina. Mudamos o tema original (Pacman) para um clássico **Policial e Ladrão** com mecânicas extras e mapas variados!

---

## Como Jogar e Controles

O jogo é multiplayer local (dois jogadores no mesmo teclado).

### Jogador 1 (Policial - P1)
* **Objetivo**: Capturar o ladrão antes que o tempo acabe ou ele roube todo o dinheiro.
* **Controles**:
  * `Seta para Cima`: Move para cima
  * `Seta para Baixo`: Move para baixo
  * `Seta para Esquerda`: Move para esquerda
  * `Seta para Direita`: Move para direita
  * `Tecla Ponto (.)`: Para o movimento

### Jogador 2 (Ladrão - P2)
* **Objetivo**: Roubar os 5 sacos de moedas espalhados pelo mapa antes do tempo acabar sem ser pego.
* **Controles**:
  * `Tecla W`: Move para cima
  * `Tecla S`: Move para baixo
  * `Tecla A`: Move para esquerda
  * `Tecla D`: Move para direita
  * `Tecla E`: Para o movimento

---

## O que a gente implementou para garantir o 10 (e os bônus)

1. **Tema de Polícia e Ladrão**: Criamos sprites em pixel art do zero usando escrita de memória (`Memory.poke`). P1 é uma viatura de polícia e P2 é um ladrãozinho com capuz e máscara preta.
2. **Seleção de 3 Mapas Diferentes (Bônus Extra)**: Em vez de um mapa fixo, o jogo sorteia aleatoriamente um entre 3 layouts de mapa diferentes toda vez que inicia.
3. **Lógica de Colisão de Paredes**: Os blocos do mapa funcionam como barreiras reais. Se um jogador tenta ir contra a parede, ele é bloqueado e seu movimento automático para.
4. **Coleta de Moedas**: Desenhamos 5 moedas/sacos de ouro no mapa. Se o Ladrão pegar as 5, ele vence o jogo na hora.
5. **Geração Dinâmica de Semente (Random Seed)**: O Nand2Tetris não tem gerador de números aleatórios nativo. Criamos um menu de início ("Pressione qualquer tecla para jogar...") onde um contador roda super rápido. O tempo que o jogador leva para pressionar a tecla vira a semente aleatória. Isso garante que os mapas e posições de spawn nunca se repitam de forma idêntica!
6. **Vantagem Inicial de 3 Segundos**: O ladrão tem 3 segundos no começo da rodada para se movimentar e se distanciar enquanto o policial fica congelado.
7. **Reinício e ESC**: Se alguém perder ou ganhar, o jogo exibe quem perdeu no centro da tela e reinicia em 3 segundos. Se apertar `ESC` a qualquer momento, o jogo fecha.

---

## Estrutura do Código

* `Main.jack`: Inicializa o jogo chamando a classe controladora.
* `GhostGame.jack`: A classe principal que gerencia o loop do jogo, as teclas pressionadas, as fases do relógio, a colisão de moedas/jogadores e a tela de Game Over. (Mantivemos o nome do arquivo para respeitar a estrutura modular do projeto exigida no classroom).
* `Map.jack`: Desenha as paredes, posiciona os saquinhos de moeda e checa se a coordenada que o player quer ir é uma parede ou se ele coletou alguma moeda.
* `Cop.jack`: Desenha a viatura policial (P1) e gerencia as coordenadas dele.
* `Thief.jack`: Desenha o ladrão (P2) e gerencia as coordenadas e movimento dele.
* `Random.jack`: Gerador de números pseudo-aleatórios usado para sortear o mapa e os locais de nascimento dos jogadores.

---

## Como Rodar

1. Use o `JackCompiler` do Nand2Tetris na pasta do projeto para compilar todos os arquivos `.jack` em arquivos `.vm`.
2. Abra o `VMEmulator` (versão de desktop recomendada).
3. Vá em *File* -> *Load Program* e selecione a pasta raiz deste projeto.
4. Coloque a velocidade de animação no máximo (**Fastest**) e no painel do fluxo escolha **No Animation** (Sem Animar) para o jogo rodar liso e rápido.
5. Clique em executar (botão de Play) e divirta-se!
