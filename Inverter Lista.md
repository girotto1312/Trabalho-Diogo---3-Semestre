Nodo* reverseLista(Nodo* lista) {
    Nodo *prev = NULL, *current = lista, *next = NULL;
    while (current != NULL) {
        next = current->prox;
        current->prox = prev;
        prev = current;
        current = next;
    }
    return prev;
}
