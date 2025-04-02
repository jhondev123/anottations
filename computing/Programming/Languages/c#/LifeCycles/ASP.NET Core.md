1. Inicialização do Servidor Web
	1. Servidor IIS/Kestrel recebe a requisição e a repassa para a pipeline do asp.net core
2. Pipeline de Middleware
	1. Cada Middleware registro no Program processa a req
	2. Exemplos: Autenticação, Autorização, Logging
3. Roteamento
	1. O roteador do asp.net determina o controller será acionado
4. Execução do Controller
	1. O método correspondente é executado
5. Geração da resposta
	1. O resultado da execução é processado e enviado de volta ao cliente
6. Finalização da requisição
	1. O ASP.NET Core finaliza a requisição