
- Diferente de uma BST, um nó pode ter **mais de dois filhos**.
- Mantém os dados **balanceados**, garantindo buscas, inserções e remoções em **O(log n)**.
- Minimiza o número de acessos ao disco, sendo ideal para **bancos de dados e sistemas de arquivos**.

📌 **Usada em:**  
✔️ **Índices de bancos de dados** (MySQL, PostgreSQL, SQL Server, etc.)  
✔️ **Sistemas de arquivos** (NTFS, EXT4, HFS+)

```
        [10, 20]
       /    |    \
 [5, 6, 7] [12, 17] [30]

```