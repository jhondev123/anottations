### **🔷 Árvore B+Tree** (Versão otimizada da B-Tree)

- Diferente da B-Tree, **os dados reais ficam apenas nas folhas**.
- As folhas são **ligadas em uma lista encadeada**, permitindo **buscas sequenciais rápidas**.
- Usada em **bancos de dados relacionais** como MySQL e PostgreSQL para otimizar **queries e ordenações**.

📌 **Vantagem:**  
✔️ Melhora buscas ordenadas (Ex: `ORDER BY` em SQL).  
✔️ Ideal para **armazenamento em disco**, pois reduz acessos e melhora eficiência de leitura.

```
        [10, 20]
       /     |     \
    [5, 6, 7] [12, 17] [30]

```