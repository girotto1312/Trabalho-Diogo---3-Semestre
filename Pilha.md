int buscaPilha(Pilha *p, int valor) {
    Nodo *aux = p->topo;
    while (aux != NULL) {
        if (aux->info == valor) return 1;
        aux = aux->prox;
    }
    return 0;
}

void buscaRemovePilha(Pilha *p, int valor) {
    Pilha aux;
    criaPilha(&aux);
    while (!pilhaVazia(p)) {
        int v = pop(p);
        if (v != valor)
            push(&aux, v);
    }
    while (!pilhaVazia(&aux)) {
        push(p, pop(&aux));
    }
}

void removeParesPilha(Pilha *p) {
    Pilha aux;
    criaPilha(&aux);
    while (!pilhaVazia(p)) {
        int v = pop(p);
        if (v % 2 != 0)
            push(&aux, v);
    }
    while (!pilhaVazia(&aux)) {
        push(p, pop(&aux));
    }
}

void removeRepetidosPilha(Pilha *p) {
    Pilha aux;
    criaPilha(&aux);
    int vistos[1000] = {0}; // Supondo intervalo pequeno
    while (!pilhaVazia(p)) {
        int v = pop(p);
        if (!vistos[v]) {
            vistos[v] = 1;
            push(&aux, v);
        }
    }
    while (!pilhaVazia(&aux)) {
        push(p, pop(&aux));
    }
}
