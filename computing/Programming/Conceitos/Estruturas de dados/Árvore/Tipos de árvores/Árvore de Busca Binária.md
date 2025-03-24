### **Tipos de Árvores Binárias e suas Definições**

1. **Árvore Binária de Busca (BST - Binary Search Tree)**
    
    - Cada nó segue a regra:
        - **Filho esquerdo** contém um valor **menor** que o nó pai.
        - **Filho direito** contém um valor **maior** que o nó pai.
    - Isso facilita operações como **busca, inserção e remoção** com tempo médio **O(log n)**.
    
    **📌 Exemplo de Uso:**
    
    - Implementação de **bancos de dados** para armazenar registros de forma ordenada e permitir buscas eficientes.
- Sistemas de **autocomplete** que precisam encontrar sugestões rapidamente.

```
        50  
      /    \  
    30      70  
   /  \    /  \  
  20  40  60  80  

```