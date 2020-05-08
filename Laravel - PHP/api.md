# API REST para prototipo

## Instalação

Instale o laravel pelo composer

```CMD
composer global require laravel/installer
```

Inicie um projeto

```CMD
laravel new api
```

## Banco de dados

Tendo o projeto criado, precisa criar o banco de dados e configurar no .env a conexão, caso ja tenha pule este passo e vá direto para o .env

Primeiro vamos criar a base de dados no MySql com o comando abaixo

```CMD
mysql -uroot -p
```

Digite a senha para entrar no banco vc vai precisar criar a base de dados

```CMD
create database supermercado collate utf8mb4_unicode_ci;
```

> Nota: comando sendo usado no mysql 5.7 ou superior

Banco criado vamos configurar a conexão no arquivo .env

> DB_CONNECTION=mysql
>
> DB_HOST=127.0.0.1
>
> DB_PORT=3306
>
> DB_DATABASE=supermercado
>
> DB_USERNAME=root
>
> DB_PASSWORD=

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

Crie um model para ser responsavel pela comunicação entre o banco e a framework.

```CMD
php artisan make:model Products
```

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

Crie um controler para ser responsavel pela comunicação entre a requisição e o model.

```CMD
php artisan make:controller Api/ProductController --api
```

o parametro api retira as funções responsaveis por exibir a view de criação e edição.

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
Route::namespace('Api')->group(function(){
    Route::prefix('products')->group(function(){
        Route::get('/', 'ProductController@index');
        Route::get('/{id}', 'ProductController@show');
        Route::post('/', 'ProductController@save');
        Route::put('/', 'ProductController@update');
        Route::patch('/', 'ProductController@update');
        Route::delete('/{id}', 'ProductController@delete');
});
});
```

Como opção você pode criar uma rota resourses:

```PHP
Route::namespace('Api')->group(function(){
    Route::resource('products')-'ProductController');
});
```

Na rota resources por padrao nos verbos show, update/patch e destroy, esperam um {parametro} na url

para testar as rotas coloque o seguinte retorno nas funções do controller.

```PHP
return response()->json(['message' => 'Você entrou na função'.__METHOD__]);
```

Agora chame pelo postman pelo get e ve se funcionou tudo certo.

## Resource / Response

para melhorar o retorno dos models e ter um controle do que é retornado iremos criar um
resource para os produtos para apenas mostrar alguns campos.

```CMD
php artisan make:resource ProductResource
```

Quando abrir o arquivo coloque este código na função toArray, ela contem o array para ser
convertido para json, caso queira outros campos, só atualizar.

```PHP
public function toArray($request)
{
    return [
        'name' => $this->name,
        'price' => $this->price,
        'description'=> $this->description
    ];
}
```

caso queira retornar todos campos coloque este retorno

```PHP
return $this->resource->toArray();
```

caso precise de varios itens no retorno, vamos gerar uma resource collection

```CMD
php artisan make:resource Product --collection
```

Quando abrir o arquivo coloque este código na função toArray, ela contem o array para ser
convertido para json, caso queira outros campos, só atualizar.

```PHP
- public function toArray($request)
{
    return [
        'data' => $this->collection
    ];
}
```

ela retorna uma collection com uma paginação

## Request personalizado

Para criar validações dos campos da sua api vc vai criar um request personalizado e fazer as validações dentro dele

```CMD
php artisan make:request ProductRequest
```

Será criado dentro de http/request o arquivo que iremos modificar.

no arquivo teremos 2 metodos, authorize e rules.

Authorize: vc fará validações caso tenha niveis de permissao para essa request que esta criando ou seja, vc autoriza ou nao a requisição que o usuario fez.

Rules: Nesse metodo vc valida os campos recebidos na request com condições.

exemplo de rules:

```PHP
public function rules()
{
    return [
        'name'         => 'required',
        'price'        => 'required',
        'description'  => 'required'
    ];
}
```

Vc pode consultar a documentação do laravel para especificar outras condições.

Ao criar e especificar as regras, vc pode alterar todos os metodos recebem como parametro o $request.

```PHP
public function show(Request $request)
{
  //sua lógica
}
```

```PHP
public function show(ProductRequest $request)
{
  //sua lógica
}
```

Ao mandar uma requisição ja fará as validações antes de entrar no metodo e caso falhe em alguma condição ele retornará um json com todas os campos que deram false.

> Status code retornado é o 422.
