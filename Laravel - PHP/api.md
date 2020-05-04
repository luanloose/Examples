# API REST para prototipo

## Criar api do zero para processo seletivo ou prototipo

```CMD
laravel new api
```

Configurar no .env conexão com o banco de dados

    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=homestead
    DB_USERNAME=homestead
    DB_PASSWORD=secret

Caso seja um projeto próprio cria a migration para startar o banco de dados

```CMD
php artisan make:migration create_table_products --create=products 
```

Crie um controler para ser responsavel pela comunicação entre o banco e a framework.

```CMD
php artisan make:model Products 
```

- crie a valiavel fillable para colocar os campos permitidos na tabela.
- crie as relaçoes entre as tabelas caso tenha.

Crie um controler para ser responsavel pela comunicação entre a requisição e o model.

```CMD
php artisan make:controller Api/ProductController
```

Voce pode criar um controller como recurso que é para o laravel possa criar as rotas
com todos verbos http.

```CMD
php artisan make:controller Api/ProductController --resourses --api
```

o parametro api retira as funções responsaveis por exibir a view de criação e edição.

Exemplo de função para a api, salvar produto

```PHP
- public function save(Request $request)
    {
    	$data = $request->all();
    	$product = $this->product->create($data);

    	return response()->json($product);
    }
```

- Faça todas as funçoes solicitadas show, save, delete, uptade para o passo a seguir.

Crie os endpoints para sua api ser consumida baseada nas funções criadas caso nao seja um 
controller resourses 

```PHP
- Route::namespace('Api')->group(function(){
	//Products route
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

Caso tenha criado um resourses a rota é a seguinte

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
