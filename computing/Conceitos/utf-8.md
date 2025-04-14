
**Unicode Transformation Format** 
8 [[Bit]]s é uma codificação de caracteres amplamente utilizada na informática que faz parte do padrão Unicode. Ela foi projetada para representar de forma eficiente todos os caracteres possíveis do Unicode, que inclui símbolos de diversas linguagens e sistemas de escrita, como latim, chinês, árabe, emojis, entre outros.

Principais características do UTF-8:
Codificação variável: Cada caractere pode ser representado por 1 a 4 bytes, dependendo da sua complexidade. Caracteres mais comuns, como letras do alfabeto latino, são codificados com 1 byte, enquanto caracteres menos comuns, como caracteres de idiomas asiáticos ou emojis, podem usar até 4 bytes.

Compatibilidade com [[ASCII]]: Os primeiros 128 caracteres de UTF-8 (valores de 0 a 127) são idênticos ao  [[ASCII]]. Isso significa que qualquer texto [[ASCII]] válido também é válido em UTF-8, o que facilita a transição entre os dois.

Eficiência: Caracteres que são mais comuns em idiomas ocidentais (como os da língua inglesa) são codificados de maneira mais eficiente, usando apenas 1 [[Computing/Conceitos/Byte|Byte]].