## Configurando página de erro
### `error_page 400 404 401 /erro.html;`
configura uma página a ser exibida casos tenha os erros configurados

## Criando um proxy reverso
        `location / {`
            `proxy_pass http://localhost:8080;`
        `}`
ele vai redirecionar para a outra rota

## Diferença de usar barra no final da url
por exemplo: proxy_pass http://localhost:8080; e proxy_pass http://localhost:8080/;
- **Sem a barra**: O caminho original é mantido após o redirecionamento.
- **Com a barra**: O caminho original é substituído pelo caminho após o domínio do `proxy_pass`.


## Conceito de API Gateway
É um servidor que fica responsável por direcionar para outras aplicações e microserviços, geralmente ele vai saber direcionar a requisição para esses servidores trazendo várias vantagens, um exemplo bem simples
`server {`
    `listen 80;`
    `location / {`
        `include fastcgi_params;`
        `fastcgi_pass php:9000;`
        `fastcgi_index index.php;`
        `fastcgi_param SCRIPT_FILENAME /var/www/html$fastcgi_script_name;`
    `}`
    `location /servico1 {`
        `proxy_pass http://localhost:8080/;`
    `}`
    `location /servico2 {`
    `proxy_pass http://localhost:8000/;`
    `}`
`}`
`server {`
    `listen 8080;`
    `location / {`
        `return 200 "serviço1";`
    `}`
`}`
`server {`
    `listen 8000;`
    `location / {`
        `return 200 "serviço2";`
    `}`
`}`
Nesse exemplo ele tem uma aplicação na rota principal do servidor mas ele traz uma forma de acessar outros serviços acessando por localhost/servico1

## Configurando Logs
Para configurar Logs você pode definir dentro do http do seu nginx.conf como no exemplo 
    `log_format main 'Remote Addr: $remote_addr, Time: [$time_local], '`
                            `'"Request: $request", Status: $status, Referer:  $http_referer ';`
perceba que a palavra main é o nome do formato desse log podendo ser criando outros formatos diferentes, e dentro de cada server nosso nos podemos adicionar ele 
`server{`
    `listen 8003;`
    `access_log /etc/nginx/logs/load_balancer.log main;`
    `server_name localhost;`
    `location / {`
        `proxy_pass http://servicos;`
    `}`
`}`
Perceba a utilização do main que é o nome do formato escolhido
### Resolvendo problema das aplicações pegarem o ip do load balancer como ip do host
Quando uma aplicação recebe requisições que vieram de um load-balancer os logs que gravarem o `$remote_addr` vão pegar o ip do load-balancer,
#### Uma das soluções é criar um cabeçalho http
Para criar um cabeçalho http vamos no nosso load_balancer e usamos
        `proxy_set_header X-Real-IP $remote_addr`
        e no nosso log format usamos esse cabeçalho
            `log_format main 'Remote Addr: $http_x_real_ip, Time: [$time_local], '`
  `'"Request: $request", Status: $status, Referer:  $http_referer ';`

## Distribuindo a carga entre os servidores
Usando de exemplo esse load balancer
`upstream servicos{`
    `server localhost:8080;`
    `server localhost:8000;`
`}`
`server{`
    `listen 8003;`
    `access_log /etc/nginx/logs/load_balancer.log main;`
    `server_name localhost;`
    `location / {`
        `proxy_set_header X-Real-IP $remote_addr;`
        `proxy_pass http://servicos;`
    `}`
`}`
Se eu quiser distribuir uma carga diferença entre os servidores ou um peso maior para algum deles por ele ter melhor hardware ficaria assim
`upstream servicos{`
    `server localhost:8080 weight=2;`
    `server localhost:8000;`
`}`
bem simples mas funcional, ele distribui proporcionalmente então se eu colocar peso em um de 5 e o outro de 2, ele vai interpretar que a cada 7 requisições 5 devem caior no primeiro e 2 no segundo 

## Métodos de load balancer

### Round Robin
Ele vai distribuir as requisições igualitáriamente é comum usar quando temos vários servidores iguais 
#### Round Robin Weight
É um Round Robin porém você pode definir pesos em um servidor dando a ele prioridade para receber as requisições, é comum em casos que um servidor tem mais performance que o outro

### Least Connection
É uma forma que ele distribui as requisições com base em quantas cada servidor possui ativas no momento, ou seja se tiver 4 requisições ativas, 2 em cada servidor, e uma acabar em 1 servidor, a próxima que chegar vai nele. é comum usar quando possuir serviços que podem demorar tempos diferentes para encerrar a conexão, assim balanceando melhor a carga. Porém tem um custo maior de performance do que a round robin

## Definindo um servidor de backup
Para definir um servidor que vai ficar responsável pelo backup quando algum der problema podemos adicionar a diretiva backup no upstream que caso houver algum problema com o servidor 1, ele vai ficar responsável, e no servidor que pode apresentar problemas podemos definir o fail_timeout para colocar um intervalo de tempo para ele receber novas requisições quando estiver fora, podemos definir também o numero de requisições até ele ser considerato indisponível, mas o normal é 1
`upstream servicos{`
    `server localhost:8080 fail_timeout=120s;`
    `server localhost:8000 backup;`
`}`

## CGI vs FastCGI
CGI e fastCGI são protocolos que podemos usar para passar dados de um servidor web para um servidor de aplicação, sendo mais rápido que o http, o FastCGI obviamente é mais rapído e o mais comumente usado, principalmente em php

## Criando Cache HTTP e ativando a compressão dos dados
nesse código incluimos os mime types para o nginx reconhecer outros tipos de arquivos, ativamos o gzip que tem a funcionalidade de comprimir os dados e colocamos os tipos de arquivos que ele deve comprimir a lista dos tipos
<https://gist.github.com/kilhage/7f0e7546457716dc9174>
nois adicionamos um header para ele manter as conexões abertas para reduzir a latencia e o gasto de processamento, depois criamos uma rota que pode receber requisições solicitando arquivos png e definir que expira em 30 dias o cache e adicionamos por ultimo o formato que o cache vai se comportar, no caso publico
    `include mime.types;`
    `gzip on;`
    `gzip_types text/css text/javascript;`
    `add_header Keep-Alive "timeout=5, max=1000";`
    `location ~ \.png$ {`
        `expires 30d;`
        `add_header Cache-Control public;`
    `}` 
`}`

## Fazendo Cache no servidor com FastCGI
Aqui criamos cache de uma página carregada por fastcgi dessa forma ele vai fazer o cache da aplicação para que possa ter uma boa velocidade de resposta para o cliente e menor processamento
`fastcgi_cache_path /var/cache/nginx levels=1:2 keys_zone=fpm:10m;`
`server{`
    `listen 8004;`
    `location / {`
        `# include fastcgi.conf; não funciona`
        `include fastcgi_params;`
        `fastcgi_pass php:9000;`
        `fastcgi_index index.php;`
        `fastcgi_cache fpm;`
        `fastcgi_cache_key $request_uri;`
        `fastcgi_cache_valid 5m;`
        `# add_header X-Cache-Status $upstream-cache-status;`
        `fastcgi_param SCRIPT_FILENAME /var/www/html$fastcgi_script_name;`
    `}`
`}`