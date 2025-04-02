A compilação é o processo de transformação do código fonte escrito em uma linguagem de alto nível para um código de máquina entendido e executado pelo PC
## Etapas

1. Análise Léxica (Tokenização)
	1. O compilador lê o código-fonte e divide em pequenos blocos chamados tokens(palavras-chaves, identificadores e operadores)
2. Análise Sintática (Parsing)
	1. Os tokens são organizados de acordo com a gramática da linguagem
	2. Se houver erros de sintaxe como um ; faltando, o compilador retorna mensagens de erro
3. Análise Semântica
	1. Verifica se o código faz sentido logicamente
4. Otimização do Código
	1. O compilador melhora a eficiência do código gerado, reduzindo redundâncias ou otimizando instruções
5. Geração do código (Linking)
	1.  O código-fonte é transformado em código de máquina ou bytecode, dependendo do compilador
6. Ligação(Linker)
	1. Se o código depende de bibliotecas externas, o linker adiciona essas dependências para criar o executável final