## Domains
São o conjunto de regras e classes que guardam essas regras que são importantes para o negócio, que não podem depender de libs externas, frameworks e nem nada, em um bom sistema essas regras bem estruturadas devem ser menos dependente possivel de coisas externas
### Entities
São literalmente as entidades do sistema, como produtos, clientes, e o recomendado é separar eles em uma classe separada com toda a lógica que eles possui de validações, como os campos e o seu molde. Essas Entidades geralmente possuem ValueObjects em seus campos, como CPF, Email, Telefone ou outras informações que necessitam de validações complexas
### ValueObjects
São classes que   validam informações que estão ligadas as regras de negócio
como o exemplo citado email, CPF e outros campos que precisam ter uma lógica de validação, e precisa ser desacoplado das entities da aplicação até para poder seu reutilizada
### Repositories
São classes focadas em ter o contato entre as regras de negócio e o banco de dados, onde vão ter implementações concretas de consultas, inserts ...



## Application
A camada de aplicação é responsável por orquestrar a execução da lógica de negócio do sistema. Ela não contém lógica de domínio propriamente dita, mas coordena a interação entre as diferentes partes do sistema para cumprir os casos de uso definidos.
### UseCases
São os responsáveis por implementar as regras propostas como domains  / regras de negócio, Estão mais ligadas a funcionalidades que o sistema vai possuir, como cadastro de clientes que vai precisar ter uma entidade de cliente com suas validações de informações e regras de negócio
Os casos de uso são instâncias específicas da camada de aplicação que descrevem e implementam os fluxos de trabalho do sistema. Cada caso de uso encapsula um cenário específico de interação com o sistema e define como os serviços de domínio e repositórios devem ser utilizados para alcançar o objetivo desse cenário.
### Contracts
Os contratos são essenciais para definir as interfaces e garantir que diferentes partes do sistema possam se comunicar de forma clara e desacoplada.