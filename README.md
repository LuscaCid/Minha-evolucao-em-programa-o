# Minha-evolucao-em-programa-o
//Neste projeto pretendo demonstrar um menu que tem como função designar, a partir da escolha do usuário, qual o sentido que o programa vai tomar.
#include <stdio.h>

int funcaoprimoanterior(int naofoiprimo){
    int parada = 0;
    int restos = 0;
    int proximoprimo = naofoiprimo;
    while(parada == 0){
        proximoprimo--;
        restos = 0;
        for(int cont = proximoprimo; cont > 0; cont--){
            if(proximoprimo % cont == 0)restos++;
        }
        if(restos == 2) parada = 1;
    }
    printf("\no valor primo anterior eh %d", proximoprimo);
    return proximoprimo;
}

int funcaoproximoprimo(int naofoiprimo){
    int parada = 0;
    int restos = 0;
    int proximoprimo = naofoiprimo;
    while(parada == 0){
        proximoprimo++;
        restos = 0;
        for(int cont = proximoprimo; cont > 0; cont--){
            if(proximoprimo % cont == 0)restos++;
        }
        if(restos == 2) parada = 1;
    }
    printf("\no proximo valor primo eh %d", proximoprimo);
    return proximoprimo;
}

int funcaoverificacao(int ehprimo)
{
    int restos = 0;
    for(int count = ehprimo; count > 0; count--){
        restos += (ehprimo % count == 0) ? 1:0;
    }
    return restos == 2? 1:0;
}

int main()
{
    int soma;
    int valor;
    while(1){
    printf("\n\t*menu*\n1-para verificar se eh primo\n2- para mostrar o proximo e o anterior a eles e calc a media\n3- para somar todos os numeros entre o proximo primo e o anterior\n4- para sair. ");
    int opcao;
    scanf("%d", &opcao);
    if(opcao == 4)break;
        switch (opcao){
            case 1:
                printf("informe o valor");
                scanf("%d",&valor);
                int resposta = (funcaoverificacao(valor))? printf("%d eh primo", valor) : printf("o valor %d nao foi primo\n", valor);funcaoproximoprimo(valor);
                break;
            case 2:
                printf("informe um valor para procurar o proximo primo e o anterior e calcular a media\n");
                scanf("%d", &valor);
                int proximo = funcaoproximoprimo(valor);
                int anterior = funcaoprimoanterior(valor);
                int media = (anterior + proximo)/ 2;
                printf("\n%d foi a media entre %d e %d", media, anterior, proximo);
                break;
            case 3:
                 printf("informe um valor para somar todos os numeros entre o primo anterior e o proximo\n");
                 scanf("%d", &valor);
                 int proximo3 = funcaoproximoprimo(valor);
                 int anterior3 = funcaoprimoanterior(valor) + 1;
                 while(anterior3 < proximo3){
                    soma+=anterior3;
                    anterior3++;
                 }
                 printf("\na soma foi de: %d",soma);
        }
    }
    return 0;
}
