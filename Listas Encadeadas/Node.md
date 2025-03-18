<h1 align="center">
   Listas Encadeadas com Nó (Node)
</h1>

## Conceito:
- A lista encadeada com nó é implementada usando uma classe Node que representa cada elemento da lista.

- Cada nó contém um valor (item) e uma referência para o próximo nó (prox).

Classe Node
```csharp
class Node
{
    private Object item;
    private Node prox;

    Node(object item)
    {
        this.item = item;
        prox = null;
    }

    public Object getItem()
    {
        return item;
    }

    public void setProx(Node prox)
    {
        this.prox = prox;
    }

    public Node getProx()
    {
        return prox;
    }
}
```
## Explicação:

- **item**: Armazena o valor do nó.

- **prox**: Referência para o próximo nó.

- O construtor inicializa o nó com um valor e define prox como null.
