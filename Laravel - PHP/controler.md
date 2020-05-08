# Controler exemplos

## exemplos de query

Filtro com condição

* Explicação dos campos no where.

```PHP
$exp[0], $exp[1], $exp[2]
//campo, condição e valor.
```

```PHP
if($request->has('coditions')) {
    $expressions = explode(';', $request->get('coditions'));
        foreach($expressions as $e) {
            $exp = explode(':', $e);

            $this->model = $this->model->where($exp[0], $exp[1], $exp[2]);
    }
}

return $model->paginate(10);
```

Filtro de campos

* ex: nome, preço

```PHP
if($request->has('fields')) {
    $this->model = $this->model->selectRaw($request->get('fields'));
}
return $model->paginate(10);
```
