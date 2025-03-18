<h1 align="center"> 
   Árvores Binárias
</h1>

# Conceito

- Uma árvore binária é um tipo especial de árvore onde cada nó tem no máximo dois filhos: um filho à esquerda e um filho à direita.
- Os nós à esquerda de um nó contêm valores menores que o nó pai, e os nós à direita contêm valores maiores.

***

# Classe BTreeNode
```csharp
class BTreeNode
{
    private int valor;
    private BTreeNode esq;
    private BTreeNode dir;

    BTreeNode(int valor)
    {
        this.valor = valor;
    }

    public void setValor(int valor)
    {
        this.valor = valor;
    }

    public void setEsq(BTreeNode esq)
    {
        this.esq = esq;
    }

    public void setDir(BTreeNode dir)
    {
        this.dir = dir;
    }

    public int getValor()
    {
        return valor;
    }

    public BTreeNode getEsq()
    {
        return esq;
    }

    public BTreeNode getDir()
    {
        return dir;
    }
}
```
## Explicação:

- **valor**: Armazena o valor do nó.
- **esq**: Referência para o filho à esquerda.
- **dir**: Referência para o filho à direita.
- O construtor inicializa o nó com um valor e define esq e dir como null.

***

# Inserção em Árvore Binária
## Método de Inserção
```csharp
class BTree
{
    private BTreeNode raiz;

    private BTreeNode inserir(BTreeNode arvore, int novo)
    {
        BTreeNode aux = null;
        if (arvore == null)
        {
            aux = new BTreeNode(novo);
            return aux;
        }
        else if (novo < arvore.getValor())
            arvore.setEsq(inserir(arvore.getEsq(), novo));
        else
            arvore.setDir(inserir(arvore.getDir(), novo));

        return arvore;
    }

    public void insertrNo(int novo)
    {
        raiz = inserir(raiz, novo);
    }
}
```
## Explicação:

- O método inserir insere um novo nó na árvore de forma recursiva.
- Se a árvore estiver vazia, o novo nó se torna a raiz.
- Se o valor a ser inserido for menor que o valor do nó atual, ele é inserido à esquerda.
- Se for maior, é inserido à direita.

***

# Exibição de Nós em Árvore Binária
## Métodos de Exibição
```csharp
public void exibirEsquerdo(BTreeNode arv)
{
    if (arv != null)
    {
        exibirEsquerdo(arv.getEsq());
        Console.WriteLine(arv.getValor());
    }
}

public void exibirDireito(BTreeNode arv)
{
    if (arv != null)
    {
        exibirDireito(arv.getEsq());
        Console.WriteLine(arv.getValor());
    }
}

public void ExibirRaiz()
{
    Console.WriteLine("Raiz: " + raiz.getValor());
}

public void exibirNoEsq()
{
    exibirEsquerdo(raiz);
}

public void exibirNoDir()
{
    exibirDireito(raiz);
}
```
## Explicação:

- **exibirEsquerdo**: Exibe os nós da subárvore esquerda em ordem crescente.
- **exibirDireito**: Exibe os nós da subárvore direita em ordem crescente.
- **ExibirRaiz**: Exibe o valor da raiz.
- **exibirNoEsq e exibirNoDir**: Chamam os métodos de exibição para a subárvore esquerda e direita, respectivamente.

***

# Exclusão de Nó em Árvore Binária
## Método de Exclusão
```csharp
public void exluirMio(int item)
{
    BTreeNode aux = raiz, pai = null, filho = raiz, temp;
    while (aux != null && aux.getValor() != item)
    {
        pai = aux;
        if (item < aux.getValor())
            aux = aux.getEsq();
        else
            aux = aux.getDir();
    }

    if (aux == null)
        Console.WriteLine("Valor não encontrado");
    else if (aux.getDir() == null)
    {
        if (pai.getEsq() == aux)
            pai.setEsq(aux.getEsq());
        else
            pai.setDir(aux.getEsq());
    }
    else if (aux.getEsq() == null)
    {
        if (pai.getEsq() == aux)
            pai.setEsq(aux.getDir());
        else
            pai.setDir(aux.getDir());
    }
    else
    {
        for (temp = aux, filho = aux.getEsq(); filho.getDir() != null; temp = filho, filho = filho.getDir());
        if (filho != aux.getEsq())
        {
            temp.setDir(filho.getEsq());
            filho.setEsq(aux.getEsq());
        }
        filho.setDir(aux.getDir());
        if (pai.getEsq() == aux)
            pai.setEsq(filho);
        else
            pai.setDir(filho);
    }
}
```
## Explicação:

- O método exluirMio remove um nó da árvore.
- Se o nó a ser excluído não tiver filhos à direita, o filho à esquerda é promovido.
- Se não tiver filhos à esquerda, o filho à direita é promovido.
- Se o nó tiver ambos os filhos, o maior nó da subárvore esquerda é promovido.
