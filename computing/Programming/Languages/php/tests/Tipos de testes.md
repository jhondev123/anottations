
![[piramide_testes.png]]
Quanto mais perto da base da pirâmide melhor, mais confiável, menos custoso e menos provável de dar erros é o teste

## Testes de Unidade (!Teste unitários)
Comumente chamado de testes unitários mas faz mais sentido chamar de unidade
São testes que testam a menor parte do sistema, mais específico a menor parte de uma classe, um método publico

## Dubles de testes
Geralmente nossas classes no sistema possuem dependências de outras classes, e para não utilizar a classe real que pode trazer problemas nos nossos testes, criamos uma classe de dublê que simula a classe que dependemos

## Testes de integração
Geralmente são testes que usam mais de uma classe para integrar uma funcionalidade
como uma consulta no banco, um envio de email, bem focado em funcionalidades completas e é bem comum também esses testes usarem dependências externas

## Testes E2E ou Testes de ponta a ponta
é um teste que já é mais próximo ai um cenário real onde testamos as funcionalidades na prática, ou seja um envio de formulário, uma pesquisa no site, o click de um botão e geralmente é feito por ferramentas externas para automatizar o processo

## Testes manuais
Testes realizados pelos devs de testarem as funcionalidades manualmente, é o pior e mais custoso dos testes

## A realidade
A realidade é um pouco diferente da teoria, os testes manuais são os mais comuns quando deveriam ser os menos comuns
![[real_piramide_testes.png]]

## Testes de performance 
Testa a velocidade da nossa aplicação como o tempo de resposta de um site, o tempo de resposta de uma consulta no banco ...

## Testes de mutação
São testes que pegamos testes unitários que e adicionamos bugs neles propositalmente para ver se o teste unitário vai quebrar com o bug

## BDD
É uma forma de criar o código e criar os testes em conjunto de forma humanizada para um usuário entender o seu teste