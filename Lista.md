int minLista(Nodo *lista) {
    if (lista == NULL) return -1;
    int min = lista->info;
    for (Nodo *p = lista->prox; p != NULL; p = p->prox)
        if (p->info < min) min = p->info;
    return min;
}

int maxLista(Nodo *lista) {
    if (lista == NULL) return -1;
    int max = lista->info;
    for (Nodo *p = lista->prox; p != NULL; p = p->prox)
        if (p->info > max) max = p->info;
    return max;
}

int mediaLista(Nodo *lista) {
    if (lista == NULL) return 0;
    int soma = 0, count = 0;
    for (Nodo *p = lista; p != NULL; p = p->prox) {
        soma += p->info;
        count++;
    }
    return (count > 0) ? soma / count : 0;
}

int lenLista(Nodo *lista) {
    int count = 0;
    for (Nodo *p = lista; p != NULL; p = p->prox)
        count++;
    return count;
}
