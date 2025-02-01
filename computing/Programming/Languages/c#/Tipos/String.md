[[Tipos de Referência]]

Utilidade:
Usado para armazenar textos (sequências de caracteres Unicode). É amplamente utilizado para manipulação de dados textuais, como mensagens, logs e entrada de usuário.

Tamanho do valor armazenado:
Cada caractere Unicode ocupa 2 bytes (16 bits). O tamanho total depende do número de caracteres armazenados.
Além disso, como string é um tipo de referência, a variável armazena um ponteiro de 4 bytes (em sistemas de 32 bits) ou 8 bytes (em sistemas de 64 bits) para o local na memória onde o texto está armazenado.

É um tipo de referência ([[Tipos de Referência]]), mas se comporta de forma [[imutável]] ou seja, uma vez criada, uma string não pode ser modificada (qualquer alteração cria uma nova instância na memória).