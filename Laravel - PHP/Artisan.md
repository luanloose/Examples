# Artisan Commands

## Segue abaixo uma lista de comandos e suas ações:

> php artisan serve:

executa a aplicação no servidor de desenvolvimento do PHP.

> php artisan clear-compiled

Sempre que o Framework é colocado em produção as classes principais são compiladas para o carregamento seja mais rápido. Esse processo é feito em cache e caso você queira remover esse cache basta usar o comando clear-compiled.

> php artisan down

Caso sua aplicação esteja em produção e você precise realizar alguma manutenção que a aplicação necessite ficar alguns minutos fora de operação o comando: php artisan down, fará com que sua aplicação apresenta a tela manutenção padrão do Laravel e não fique off-line.

> php artisan up

Assim que a equipe de desenvolvimento concluir a manutenção basta apenas digitar o seguinte comando no prompt de comando: php artisan up.

> php artisan env

O comando: php artisan env, apresenta o ambiente de desenvolvimento que está sendo utilizado.

> php artisan optimize

O comando: php artisan optimize, realiza o cast no Framework para que o Laravel tenha sua melhor performance.

> php artisan help

O comando: php artisan help, lista todas as ajudas para o Framework.

> php artisan tinker

O comando: php artisan tinker, permite a interação com a aplicação.Como por exemplo a inserção de dados nas tabelas do banco de dados.

> php artisan migrate

O comando: php artisan migrate, executa as operações no banco de dados, criando tabelas, rodando script sql entre outros.

> php artisan list

O comando: php artisan list, executa a listagem de todos os comandos;

> php artisan make

O make possibilita a criação de código fonte, tornando assim o desenvolvimento altamente produtivo.

#### Alguns exemplos:
* php artisan make:controller : cria uma nova classe controller;

* php artisan make:model : cria uma nova classe model;

* php artisan make:migration : cria um novo arquivo de migração;

> php artisan route

O route possibilita a criação de rotas, tornando a aplicação mais segura.Alguns exemplos:
php artisan route:cache : cria um arquivo de rota cache de registro rápido;
php artisan route:clear : remove o arquivo de rota do cache;
php artisan route:list : apresenta todas as rotas registradas na aplicação;