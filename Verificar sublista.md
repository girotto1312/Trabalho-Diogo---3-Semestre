int isSubLista(Nodo* L1, Nodo* L2) {
    if (L2 == NULL) return 1;
    while (L1 != NULL) {
        Nodo *p1 = L1;
        Nodo *p2 = L2;
        while (p1 != NULL && p2 != NULL && p1->info == p2->info) {
            p1 = p1->prox;
            p2 = p2->prox;
        }
        if (p2 == NULL) return 1;
        L1 = L1->prox;
    }
    return 0;
}
