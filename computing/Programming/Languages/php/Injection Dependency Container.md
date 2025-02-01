É uma forma de não precisar instanciando mais de uma vez uma mesma classe sem necessidade, dessa forma o código fica guardado em um lugar só, facilitando a manutenção e organização do código, exemplo de container em php

## Container code Example
`<?php`
`use DI\ContainerBuilder;`
`use function DI\create;`
`use Jhonattan\LearningDiContainer\Repositorys\UserRepository;`
`$databasePath = "sqlite:" . __DIR__ . "/../learning_container_di.db";`
`$builder = new ContainerBuilder();`
`$builder->addDefinitions([`
    `PDO::class => create(PDO::class)`
        `->constructor($databasePath)`
        `->method('setAttribute', PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION)`
        `->method('setAttribute', PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC),`
    `UserRepository::class => create(UserRepository::class)`
        `->constructor(\DI\get(PDO::class)),`
`]);`
`return $builder->build();`
Nesse código ele cria o container definindo a conexão com o banco e definindo uma Model que vai receber a instancia da conexão com o banco, o exemplo sendo utilizado
`$container = require_once __DIR__ . "/config/DiContainer.php";`
`$userRepository = $container->get(UserRepository::class);`
`var_dump($userRepository->searchUsers());`
Nesse código a função $container->get('UserRepository::class') pesquisa dentro do container a existencia da classe UserRepository e auto magicamente quando encontra ele ve que precisa do PDO e verifica se também já tem o PDO no container e instancia ele também