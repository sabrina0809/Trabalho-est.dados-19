#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#define TAMANHO 5

int stack[TAMANHO];
int top = -1;

bool isEmpty(){
    return top == -1;
}

bool isFull() {
    return top == TAMANHO - 1;
}

void push(int data){
    if(isFull()){
        printf("Pilha Cheia!\n");
        return;
    }
    top++;
    stack[top] = data;
    printf("Valor %d empilhado com sucesso.\n", data);
}

int pop(){
    if(isEmpty()){
        printf("Pilha Vazia!\n");
        return -1;
    }

    int temp = stack[top];
    top--;
    return temp;
}

void imprime_pilha(){
    if(isEmpty()){
        printf("Pilha Vazia!\n");
        return;
    }

    printf("Conteúdo da Pilha:\n");
    for(int i = 0; i <= top; i++){
        printf("%d -> ", stack[i]);
    }
    printf("topo\n");
}

void topo_valor(){
    if(isEmpty()){
        printf("Pilha Vazia!\n");
        return;
    }

    printf("Topo da pilha: %d\n", stack[top]);
}

int main(){
    int opcao, valor;

    do {
        printf("\n====== MENU PILHA ======\n");
        printf("1. Empilhar (push)\n");
        printf("2. Desempilhar (pop)\n");
        printf("3. Imprimir pilha\n");
        printf("4. Mostrar topo\n");
        printf("0. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &opcao);

        switch(opcao){
            case 1:
                printf("Informe um valor para empilhar: ");
                scanf("%d", &valor);
                push(valor);
                break;
            case 2:
                valor = pop();
                if (valor != -1)
                    printf("Valor desempilhado: %d\n", valor);
                break;
            case 3:
                imprime_pilha();
                break;
            case 4:
                topo_valor();
                break;
            case 0:
                printf("Encerrando o programa...\n");
                break;
            default:
                printf("Opção inválida! Tente novamente.\n");
        }

    } while(opcao != 0);

    return 0;
}
