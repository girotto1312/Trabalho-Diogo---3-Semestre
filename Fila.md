void imprimirFila(Fila *f) {
    Nodo *aux = f->ini;
    while (aux != NULL) {
        printf("%d ", aux->info);
        aux = aux->prox;
    }
    printf("\n");
}

void editarElementoFila(Fila *f, int antigo, int novo) {
    Nodo *aux = f->ini;
    while (aux != NULL) {
        if (aux->info == antigo) {
            aux->info = novo;
            return;
        }
        aux = aux->prox;
    }
}

void removerElementoFila(Fila *f, int valor) {
    Nodo *ant = NULL, *atual = f->ini;
    while (atual != NULL) {
        if (atual->info == valor) {
            if (ant == NULL)
                f->ini = atual->prox;
            else
                ant->prox = atual->prox;

            if (atual == f->fim)
                f->fim = ant;

            free(atual);
            return;
        }
        ant = atual;
        atual = atual->prox;
    }
}

void removerRepetidosFila(Fila *f) {
    Nodo *aux = f->ini;
    int vistos[1000] = {0};
    Nodo *ant = NULL;
    while (aux != NULL) {
        if (vistos[aux->info]) {
            Nodo *rem = aux;
            if (ant != NULL)
                ant->prox = aux->prox;
            else
                f->ini = aux->prox;
            if (rem == f->fim)
                f->fim = ant;
            aux = aux->prox;
            free(rem);
        } else {
            vistos[aux->info] = 1;
            ant = aux;
            aux = aux->prox;
        }
    }
}

void removerParesFila(Fila *f) {
    Nodo *aux = f->ini;
    Nodo *ant = NULL;
    while (aux != NULL) {
        if (aux->info % 2 == 0) {
            Nodo *rem = aux;
            if (ant != NULL)
                ant->prox = aux->prox;
            else
                f->ini = aux->prox;
            if (rem == f->fim)
                f->fim = ant;
            aux = aux->prox;
            free(rem);
        } else {
            ant = aux;
            aux = aux->prox;
        }
    }
}
