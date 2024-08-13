// Jogo-Da-Velha-em-C

#include <stdio.h>

void inicializa_matriz(char matriz[3][3]){
  for (int linha = 0; linha < 3; linha ++){
    for (int coluna = 0; coluna < 3; coluna ++){
      matriz[linha][coluna] = ' ';
    }
  }
}

int coordenadavalida(char matriz[3][3], int posicaolinha, int posicaocoluna) {
  if (posicaolinha < 0 || posicaolinha > 2 || posicaocoluna < 0 || posicaocoluna > 2) {
    return 0; // POSIÇÃO INVALIDA
  } 
  if (matriz[posicaolinha][posicaocoluna] != ' ') {
      return 0;
  }
  return 1;
}

void imprimir_matriz(char matriz[3][3]){
  printf("\n");
  printf(" %c | %c | %c \n", matriz[0][0], matriz[0][1], matriz[0][2]);
  printf("---|---|---\n");
  printf(" %c | %c | %c \n", matriz[1][0], matriz[1][1], matriz[1][2]);
  printf("---|---|---\n");
  printf(" %c | %c | %c \n", matriz[2][0], matriz[2][1], matriz[2][2]);
}

int main(void) {
  char jogador01[20], jogador02[20], matriz[3][3];
  int posicaolinha, posicaocoluna;

  // fução para inicializar a matriz
  // função para impromir a matriz a cada jogada

  // Solicita o nome dos jogadores
  printf("Jogador 01, digite seu nome: ");
  scanf("%s", jogador01);
  printf("Jogador 02, digite seu nome: ");
  scanf("%s", jogador02);

  // Cria e inicializa o tabuleiro com espaços
  inicializa_matriz(matriz);

  // Imprime o tabuleiro
  printf("\n*** J O G O  D A  V E L H A***\n******************************\nNome do Jogador 01: %s\nNome do Jogador 02: %s\n\nBoa sorte jogadores %s e %s!\n******************************\n", jogador01, jogador02, jogador01, jogador02);

  imprimir_matriz(matriz);

  for (int i = 0; i < 9; i ++){
    posicaolinha = 0;
    posicaocoluna = 0;


    if (i % 2 == 0){
      printf("\n%s, digite a posição onde você quer jogar em linhas: ", jogador01);
    }
    else{
      printf("\n%s, digite a posição onde você quer jogar em linhas: ", jogador02);
    }
    scanf("%d", &posicaolinha);


    if (i % 2 == 0){
      printf("\n%s, digite a posição onde você quer jogar em colunas: ", jogador01);
    }
    else{
      printf("\n%s, digite a posição onde você quer jogar em colunas: ", jogador02);
    }
    scanf("%d", &posicaocoluna);


    // VERIFICAÇÃO SE A COLUNA EXISTE
    while (coordenadavalida(matriz, posicaolinha, posicaocoluna) == 0){
    printf("\nOpção inválida! Tente novamente\n");
      if (i % 2 == 0){
        printf("\n%s, digite a posição onde você quer jogar em linhas: ", jogador01);
      }
      else{
        printf("\n%s, digite a posição onde você quer jogar em linhas: ", jogador02);
      }
      scanf("%d", &posicaolinha);


      if (i % 2 == 0){
        printf("\n%s, digite a posição onde você quer jogar em colunas: ", jogador01);
      }
      else{
        printf("\n%s, digite a posição onde você quer jogar em colunas: ", jogador02);
      }
      scanf("%d", &posicaocoluna);
    }


    if (i % 2 == 0){
      matriz[posicaolinha][posicaocoluna] = 'X';
    }
    else{
      matriz[posicaolinha][posicaocoluna] = 'O';
    }
    imprimir_matriz(matriz);
    if ((matriz[0][0] == 'X' && matriz[1][0] == 'X' && matriz[2][0] == 'X') || (matriz[0][1] == 'X' && matriz[1][1] == 'X' && matriz[2][1] == 'X') || (matriz[0][2] == 'X' && matriz[1][2] == 'X' && matriz[2][2] == 'X') || (matriz[0][0] == 'X' && matriz[0][1] == 'X' && matriz[0][2] == 'X') || (matriz[1][0] == 'X' && matriz[1][1] == 'X' && matriz[1][2] == 'X') || (matriz[2][0] == 'X' && matriz[2][1] == 'X' && matriz[2][2] == 'X') || (matriz[0][0] == 'X' && matriz[1][1] == 'X' && matriz[2][2] == 'X') || (matriz[0][2] == 'X' && matriz[1][1] == 'X' && matriz[2][0] == 'X'))
    {
      printf("\nParabéns! %s é o vencedor!", jogador01);
      break;
    }
    if ((matriz[0][0] == 'O' && matriz[1][0] == 'O' && matriz[2][0] == 'O') || (matriz[0][1] == 'O' && matriz[1][1] == 'O' && matriz[2][1] == 'O') || (matriz[0][2] == 'O' && matriz[1][2] == 'O' && matriz[2][2] == 'O') || (matriz[0][0] == 'O' && matriz[0][1] == 'O' && matriz[0][2] == 'O') || (matriz[1][0] == 'O' && matriz[1][1] == 'O' && matriz[1][2] == 'O') || (matriz[2][0] == 'O' && matriz[2][1] == 'O' && matriz[2][2] == 'O') || (matriz[0][0] == 'O' && matriz[1][1] == 'O' && matriz[2][2] == 'O') || (matriz[0][2] == 'O' && matriz[1][1] == 'O' && matriz[2][0] == 'O'))
    {
      printf("\nParabéns! %s é o vencedor!", jogador02);
      break;
    }
  }
  return 0;
}
