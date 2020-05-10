# Lumen

* Instalar

```CMD
composer global require "laravel/lumen-installer"
```

* Criar um projeto

```CMD
lumen new api
```

* subir o servidor

```CMD
php -S localhost:8000 -t public
```

* Eloquent

Você precisa descomentar a linha da chamada da função

```PHP
$app->withEloquent()
```

no arquivo "bootstrap/app.php"
