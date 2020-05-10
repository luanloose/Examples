# Sqlite exemplo

## Configuração

Crie o arquivo database.sqlite detro da pasta database do lumen

Vá até o arquivo .env e deixe apenas a linha abaixo

    DB_CONNECTION=sqlite

após configurado teste com o comando de migrations.

    php artisan migrate
