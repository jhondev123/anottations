

Para **inverter uma árvore binária**, seguimos um processo recursivo onde, para cada nó, **trocamos a posição de seus filhos esquerdo e direito**. Esse processo se aplica recursivamente a todos os nós da árvore, começando pela raiz.

---

### **Passo a Passo da Inversão**

1️⃣ **Se a árvore estiver vazia**, não há nada para inverter, então retornamos diretamente.  
2️⃣ **Se o nó atual existir**, trocamos seus filhos esquerdo e direito.  
3️⃣ **Chamamos a inversão recursivamente** para os filhos, garantindo que toda a árvore seja invertida.  
4️⃣ **Ao final, a estrutura da árvore estará espelhada**, mantendo a hierarquia, mas com os filhos trocados.

ARVORE ORIGINAL 
```
        1
       / \
      2   3
     / \  / \
    4   5 6  7

```

```
        1
       / \
      3   2
     / \  / \
    7   6 5  4

```