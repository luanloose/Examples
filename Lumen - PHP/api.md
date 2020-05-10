# API REST para prototipo

## Instalação

Instale o lumen pelo composer

```CMD
composer global require "laravel/lumen-installer"
```

Inicie um projeto

```CMD
lumen new api
```

## Banco de dados

Tendo o projeto criado, precisa criar o banco de dados e configurar no .env a conexão, vamos usar o sqlite como database.

Crie o arquivo database.sqlite detro da pasta database do lumen

Vá até o arquivo .env e deixe apenas a linha abaixo

    DB_CONNECTION=sqlite

Para testar a conexão rode o comando

```CMD
php artisan migrate:install
```

Ele vai rodar as migrations iniciais e se tiver tudo certo com a conexão podemos seguir.

Vamos criar as migrations para alimentar a base recem criada

```CMD
php artisan make:migration create_table_products --create=products
```

Exemplo migration

```PHP
public function up()
    {
        Schema::create('products', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->float('price');
            $table->text('description');
            $table->string('slug');
            $table->timestamps();
        });
    }
```

Rode o comando abaixo para criar a tabela da migration.

```CMD
php artisan migrate
```

## Model

Crie um model para ser responsavel pela comunicação entre o banco e a framework na pasta \app.

Exemplo de model:

```PHP
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Product extends Model
{
    protected $fillable = [
        'name', 'price', 'description', 'slug'
    ];
}
```

- Crie a valiavel fillable para colocar os campos permitidos na tabela.
- Crie as relaçoes entre as tabelas caso tenha.

## Controler

Crie um controler para ser responsavel pela comunicação entre a requisição e o model na pasta controlers em app\http\controller

Exemplo de função para a api, salvar produto

```PHP
public function save(Request $request)
{
    $data = $request->all();
    $product = $this->product->create($data);

    return response()->json($product);
}
```

- Faça todas as funçoes solicitadas show, save, delete, uptade para o passo a seguir.

## Rotas

Crie os endpoints para sua api ser consumida baseada nas funções criadas no controller

```PHP
$router->group(['prefix' => 'produtos'], function() use($router){

    $router->get('/', 'ProdutoController@index');
    $router->get('/{produto}', 'ProdutoController@show');

    $router->post('/','ProdutoController@store');
    $router->put('/{produto}', 'ProdutoController@update');
    $router->delete('/{produto}', 'ProdutoController@destroy');

});
```

para testar as rotas coloque o seguinte retorno nas funções do controller.

```PHP
return response()->json(['message' => 'Você entrou na função'.__METHOD__]);
```

Agora chame pelo postman pelo get e ve se funcionou tudo certo.
