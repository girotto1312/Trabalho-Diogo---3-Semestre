Nodo* appendLista(Nodo* L1, Nodo* L2) {
    if (L1 == NULL) return L2;
    Nodo *p = L1;
    while (p->prox != NULL)
        p = p->prox;
    p->prox = L2;
    return L1;
}
