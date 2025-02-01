[[Tipos de Valor]]
[[Tipos de Referência]]
[[Gambiarra]]
Utilidade:
É uma palavra-chave para inferência de tipo em tempo de compilação. O compilador determina o tipo com base no valor atribuído. Usado para simplificar a escrita do código, especialmente quando o tipo é longo ou óbvio.

Tamanho do valor armazenado:
Depende do tipo inferido pelo compilador. Se o compilador inferir int, será 4 bytes; se for double, será 8 bytes; se for string, será um tipo de referência com ponteiro de 4 ou 8 bytes.

Tipo de valor ou referência:
Depende do tipo inferido. Se for um tipo de valor (int, double, bool), será value type. Se for um objeto (string, List<T>, dynamic), será reference type.

⚠️ Observações:
var NÃO é um tipo dinâmico como dynamic. O tipo é definido em tempo de compilação e não pode mudar depois da atribuição.
O uso de var é recomendado quando o tipo é óbvio, mas evite quando deixa o código menos legível.