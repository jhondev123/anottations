# Boxing
É um processo de converter um tipo de valor como [[Int]], [[Double]], [[Boolean]] para tipo de referência como [[Object]] ou outro tipo de referência
## Como funciona
um valor do tipo de valor ele fica gravado na [[Computing/Conceitos/Stack]] e você tenta converter ele para um tipo de referência. internamente o tipo de valor vai ser copiado para um novo objeto na [[Heap]]
e o espaço que estava alocado na stack vai receber a referência que vai apontar para onde o valor foi gravado na heap

# Unboxing
É o processo Reverso do anterior, onde você pega um tipo de referência e transforma ele em um tipo de valor
## Como funciona
O valor gravado no heap é extraido e colocado novamente na stack. é necessário um [[Casting Explicíto]] pois um object pode contar qualquer tipo de dado

# Problemas com ambos
* Alocação de memória adicional no [[Heap]]
* Performance para executar conversão
* Exeção de unboxing caso tente fazer casting de um tipo de referência para outro
* Consumo de memória, No boxing resulta em uma duplicação dos dados pois ele deixa lá a memória que estava armazenando o valor e aloca mais uma quantidade para gravar a diferença