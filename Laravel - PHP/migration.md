# Migrations exemplos

* Tabela com relação entre imóvel e usuário.

```PHP
public function up()
    {
        Schema::create('imovel', function (Blueprint $table) {
            $table->id();
            $table->unsignedBigInteger('user_id');

            $table->string('title');
            $table->string('description');
            $table->text('content');
            $table->float('price', 10, 2);
            $table->integer('bathrooms');
            $table->integer('bedrooms');
            $table->integer('property_area');
            $table->integer('total_property_area');
            $table->string('slug');

            $table->timestamps();

            $table->foreign('user_id')->references('id')->on('users');
        });
    }
```

* Tabela com relação entre perfil e usuário.

```PHP
public function up()
    {
        Schema::create('user_profile', function (Blueprint $table) {
            $table->id();
            $table->unsignedBigInteger('user_id');

            $table->text('about')->nullable(true);
            $table->text('social_networks')->nullable(true);
            $table->string('phone');
            $table->string('mobile_phone');
            $table->timestamps();
            $table->foreign('user_id')->references('id')->on('users');
        });
    }
```

* Tabela pivo com relação entre imovel e categoria.

```PHP
public function up()
    {
        Schema::create('imovel_categories', function (Blueprint $table) {
            $table->unsignedBigInteger('imovel_id');
            $table->unsignedBigInteger('category_id');

            $table->foreign('imovel_id')->references('id')->on('imovel');
            $table->foreign('category_id')->references('id')->on('categories');

        });
    }
```

* Tabela categoria.

```PHP
public function up()
    {
        Schema::create('categories', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('description');
            $table->string('slug');
            $table->timestamps();
        });
    }
```

* Tabela com relação entre imovel e photos do imovel

```PHP
public function up()
    {
        Schema::create('imovel_photos', function (Blueprint $table) {
            $table->id();
            $table->unsignedBigInteger('imovel_id');
            $table->string('photo');
            $table->boolean('is_thumb');
            $table->timestamps();
            $table->foreign('imovel_id')->references('id')->on('imovel');
        });
    }
```
