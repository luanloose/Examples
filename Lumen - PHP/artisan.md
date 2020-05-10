# Artisan Commands for Lumen 5.8

## Segue abaixo uma lista de comandos e suas ações

* Instalando o helper para funcionar os comandos

```CMD
composer require wn/lumen-generators
```

Estamos instalado esta [biblioteca](https://packagist.org/packages/wn/lumen-generators)

Para funcionar precisamos fazer duas alterações para funcionar de vez, uma delas é no arquivo do projeto lumen que esta no seguinte caminho.

```CMD
/lumen/app/Providers/AppServiceProvider.php
```

O arquivo precisa ficar assim

```PHP
<?php

namespace App\Providers;

use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        if ($this->app->environment() == 'local') {
            $this->app->register('Wn\Generators\CommandsServiceProvider');
        }
    }
}
```

Agora vamos para o arquivo

```CMD
/lumen/bootstrap/app.php
```

Descomente as 2 linhas abaixo

```PHP
//$app->withFacades();
//$app->withEloquent();
```

E depois descomente essa outra linha

```PHP
//$app->register(App\Providers\AppServiceProvider::class);
```

Agora execute o comando

```CMD
php artisan
```

Aparecerá a lista

```CMD

```
