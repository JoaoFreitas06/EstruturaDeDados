<h1 align="center"> 
   Listas Ordenadas
</h1>

# Conceito
- Em uma lista ordenada, os elementos são mantidos em uma ordem específica (crescente ou decrescente).
- A inserção de um novo nó deve garantir que a ordem seja mantida.

## Inserção em Lista Ordenada
```csharp
void insereNoOrdenado(Node novo)
{
    Node aux;
    // Verificando se a lista está vazia
    if (primeiro == null || contaNos() == 0)
    {
        novo.setProx(primeiro);
        primeiro = novo;
    }
    else
    {
        aux = primeiro;
        int valorNovo = Convert.ToInt32(novo.getItem());
        int valorAux = Convert.ToInt32(aux.getItem());
        while (aux.getProx() != null && valorNovo > valorAux)
        {
            aux = aux.getProx();
        }
        novo.setProx(aux.getProx());
        aux.setProx(novo);
    }
}
```
## Explicação:
- Insere um novo nó na posição correta para manter a ordem da lista. Se a lista estiver vazia, o novo nó se torna o primeiro. Caso contrário, o método percorre a lista até encontrar a posição correta.
