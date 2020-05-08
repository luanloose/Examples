# Artisan Commands

## Segue abaixo uma lista de comandos e suas ações

```PHP
php artisan serve
```

executa a aplicação no servidor de desenvolvimento do PHP.

```PHP
php artisan clear-compiled
```

Sempre que o Framework é colocado em produção as classes principais são compiladas para o carregamento seja mais rápido. Esse processo é feito em cache e caso você queira remover esse cache basta usar o comando clear-compiled.

```PHP
php artisan down
```

Caso sua aplicação esteja em produção e você precise realizar alguma manutenção que a aplicação necessite ficar alguns minutos fora de operação o comando: php artisan down, fará com que sua aplicação apresenta a tela manutenção padrão do Laravel e não fique off-line.

```PHP
php artisan up
```

Assim que a equipe de desenvolvimento concluir a manutenção basta apenas digitar o seguinte comando no prompt de comando: php artisan up.

```PHP
php artisan env
```

O comando: php artisan env, apresenta o ambiente de desenvolvimento que está sendo utilizado.

```PHP
php artisan optimize
```

O comando: php artisan optimize, realiza o cast no Framework para que o Laravel tenha sua melhor performance.

```PHP
php artisan help
```

O comando: php artisan help, lista todas as ajudas para o Framework.

```PHP
php artisan tinker
```

O comando: php artisan tinker, permite a interação com a aplicação.Como por exemplo a inserção de dados nas tabelas do banco de dados.

```PHP
php artisan migrate
```

O comando: php artisan migrate, executa as operações no banco de dados, criando tabelas, rodando script sql entre outros.

```PHP
php artisan list
```

O comando: php artisan list, executa a listagem de todos os comandos;

```PHP
php artisan make
```

O make possibilita a criação de código fonte, tornando assim o desenvolvimento altamente produtivo.

### Exemplos make

* php artisan make:controller : cria uma nova classe controller;

* php artisan make:model : cria uma nova classe model;

* php artisan make:migration : cria um novo arquivo de migração;

```PHP
php artisan route
```

O route possibilita a criação de rotas, tornando a aplicação mais segura.

### Exemplos route

* php artisan route:cache : cria um arquivo de rota cache de registro rápido;

* php artisan route:clear : remove o arquivo de rota do cache;

* php artisan route:list : apresenta todas as rotas registradas na aplicação;

```PHP
php artisan optimize
```

O php artisan optimize cria um arquivo compilado de classes comumente usadas em outras para reduzir a quantidade de arquivos que devem ser incluídos em cada solicitação.

```PHP
php artisan config:cache
```

Para dar ao seu aplicativo um ganho de velocidade, o comando combinará todas as opções de configuração para seu aplicativo em um único arquivo que será carregado rapidamente pela estrutura.

```PHP
php artisan key:generate
```

O comando é usado para gerar uma chave aleatória. Este comando atualizará a chave armazenada no arquivo de ambiente do aplicativo.
