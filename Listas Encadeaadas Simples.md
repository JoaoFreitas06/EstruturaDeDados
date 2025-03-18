# Listas Encadeadas Simples
Conceito
Uma lista encadeada simples é uma estrutura de dados onde cada elemento (nó) contém um valor e uma referência para o próximo nó.

O último nó aponta para null, indicando o fim da lista.

As operações básicas incluem: inserção, exclusão, busca e contagem de elementos.

Operações Básicas
1. Inserção no Início
csharp
Copy
```csharp
void insereInicio(Node novo)
{
    if (this.primeiro != null)
        novo.setProx(this.primeiro);
    else
    {
        if (this.primeiro == null)
            this.primeiro = novo;
        this.ultimo = novo;
    }
}
```
Explicação: Insere um novo nó no início da lista. Se a lista estiver vazia, o novo nó se torna o primeiro e o último.

2. Inserção no Fim
csharp
```csharp
void insereFim(Node novo)
{
    novo.setProx(null);
    if (this.primeiro == null)
        this.primeiro = novo;
    if (this.ultimo != null)
        this.ultimo.setProx(novo);
    this.ultimo = novo;
}
```
Explicação: Insere um novo nó no final da lista. Se a lista estiver vazia, o novo nó se torna o primeiro e o último.

3. Inserção em Posição Específica
csharp
```csharp
void InserePosicao(Node novo, int pos)
{
    Node aux = primeiro;
    int qtde = contaNos();
    int pos_aux;

    if (pos == 0)
    {
        novo.setProx(primeiro);
        if (primeiro == ultimo)
        {
            ultimo = novo;
        }
        primeiro = novo;
    }
    else
    {
        if (pos <= qtde)
        {
            pos_aux = 1;
            while (aux != null && pos > pos_aux)
            {
                aux = aux.getProx();
                pos_aux++;
            }
            aux.setProx(novo);
        }
        else
        {
            if (pos > qtde)
            {
                ultimo.setProx(novo);
                ultimo = novo;
            }
        }
    }
}
```
Explicação: Insere um novo nó em uma posição específica. Se a posição for 0, insere no início. Se for maior que o tamanho da lista, insere no final.

4. Exclusão de um Nó
csharp
```csharp
void excluiNo(Object item)
{
    Node aux = primeiro;
    while (aux != null && aux.getItem() != item)
    {
        aux = aux.getProx();
    }
    aux.setProx(aux.getProx().getProx());
    if (ultimo == aux.getProx())
        ultimo = aux;
}
```
Explicação: Remove um nó da lista com base no valor do item. O nó anterior ao removido é atualizado para apontar para o próximo nó.

5. Busca de um Nó
csharp
```csharp
Node buscaNo(Object item)
{
    int i = 0;
    Node aux = primeiro;
    while (aux != null)
    {
        if (aux.getItem() == item)
        {
            return aux;
        }
        i++;
        aux = aux.getProx();
    }
    return null;
}
```
Explicação: Percorre a lista para encontrar um nó com o valor especificado. Retorna o nó se encontrado, ou null caso contrário.

6. Contagem de Nós
csharp
```csharp
public int contaNos()
{
    int tam = 0;
    Node aux = primeiro;
    while (aux != null)
    {
        tam++;
        aux = aux.getProx();
    }
    return tam;
}
```
Explicação: Retorna o número de nós na lista.
