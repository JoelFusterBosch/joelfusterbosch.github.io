## Relacions 1 a 1

Per a les relacions 1 a 1 les relacions tenen les següents etiquetes en el model:

- `hasOne()`
- `belongsTo()`

Anem a dir que tenim un model i una migració `User` i un model de `Phone` per a fer les relacions:

- User:

    - Migració:

        ```php
        <?php
        return new class extends Migration
        {
            Schema::create('users', function (Blueprint $table) {
                $table->id();
                $table->string('name');
                $table->string('email')->unique();
                $table->string('password');
                $table->timestamps();
            });
        }
        ```

    - Model:

        ```php
        <?php
        class User extends Model
        {
            protected $fillable = [
                'name',
                'email',
                'password',
            ];
        }
        ```

- Phone:

    - Migració:

        ```php
        <?php
        return new class extends Migration
        {
            Schema::create('phones', function (Blueprint $table) {
                $table->id();
                $table->integer('prefix')->default(34);
                $table->unsignedBigInteger('number')->unique(); // Important el "unique" per a no transformar la relació de 1 a 1 a 1 a m
                $table->unsignedBigInteger('user_id');
                $table->foreign('user_id')->references('id')->on('users');
                $table->timestamps();
            });
        }
        ```  

    - Model:

        ```php
        <?php
        class Phone extends Model
        {
            protected $fillable = [
                'prefix',
                'number',
                'user_id',
            ];
        }
        ```

I ara per a fer les relacions has de fer funcions a les classes necessaries: 

- Funció en el model `User`:
    ```php
    <?php
    // Funció per a fer la relació en la classe Phone
    public function phone()
    {
        // Crida a la classe Phone per a mostrar/usar les seues variables 
        return $this->hasOne(Phone::class);
        /*
        o
        return $this->hasOne(Phone::class, 'user_id', 'id');
        */
    }
    ```
- Funció en el model `Phone`:
    ```php
    <?php
    // Funció per a fer la relació en la classe User
    public function user()
    {
        // Crida a la classe Phone per a assignar el id del usuari
        return $this->belongsTo(User::class);
        /*
        o
        return $this->belongsTo(User::class, 'user_id', 'id');
        */
    }
    ```

!!! Important
    El que realment Laravel espera en `hasOne()`, `hasMany()`, `belongsTo()` s'espera el següent, vos mostre un exemple:

    ```php
    <?php
    return $this->hasOne("Related", "fk", "pk");
    ```

    - `Related`: Classe de la relació
    - `fk`: Columna de la taula relacionada (id de la taula relacional/ForeignKey)
    - `pk`: Columna d'eixe model (id/localKey)

    Aleshores és mostraria de la següent forma:

    ```plaintext
    phones.user_id = users.id
    ```

    Però Laravel si sols poses la classe Laravel interpreta la FK com en el nostre cas la FK(`user_id`) i en la PK(`id`).

    Sols has d'escriure-lo d'aquesta forma si es trenquen les conviccions de Laravel, per exemple:

    - En `User` en lloc de `id` és `id_user`
    - En `Phone` en lloc de `user_id` és `id_user`

    Perque Laravel l'interpetra de la següent forma:
    ```plaintext
    "nom del model en singular i en minuscula" + "_id"
    ```
    Exemples:
    User -> user_id
    Phone -> phone_id
    Product -> product_id

    Si es trenquen 1 o les 2 has de ficar-ho de la forma abans esmentada:

    ```php
    <?php
    /*
    Recordeu ficar en l'ordre correcte
    return $this->hasOne("Related", "fk", "pk");
    En la primera fica la clau foranea
    I en la segona fica la clau local
    */
    return $this->hasOne(Phone::class, 'id_user', 'id_user');
    ```

## Relacions `1 a m` i `m a 1`
En aquest apartat anem a gastar la mateixa relació entre `User` i `Phone` degut a que 1 usuari pot tindre molts telefons, pero 1 telefon sols pot tindre 1 usuari asociat.

Sols anem a canviar el `hasOne()` pel `hasMany()` per a fer la relació `1 a m`:

- Migració:

    - Phone:

    ```php
    <?php
    /*Sols llevar el "unique per a que puga acceptar altres ids" */
        $table->unsignedBigInteger('number');
        $table->unsignedBigInteger('user_id');
    ```

- Model:
    - User:
        ```php
        <?php
        // Funció per a fer la relació en la classe Phone, la cual serà la clau que tindra la PK
        public function phones()
        {
            // Crida a la classe Phone per a mostrar/usar les seues variables 
            return $this->hasMany(Phone::class);
        }
        ```
    - Phone:
        ```php
        <?php
        // Funció per a fer la relació en la classe User, la cual serà la clau que tindra la FK
        public function user()
        {
            // Crida a la classe Phone per a assignar el id del usuari
            return $this->belongsTo(User::class);
        }
        ```

`hasMany()` és exactament igual a `hasOne()` en estructura, però en funcionalitat és diferent degut a que pot tornar una col·lecció i no soles 1 model
## Relacions m a m
Per a fer les relacions de `m a m` anem a crear una nova migració i un nou model, els `Roles`:

- Roles:

    - Migracions:

        ```php
        <?php
        public function up(): void
        {
            Schema::create('roles', function (Blueprint $table) {
                $table->id();
                $table->string('name')->unique();
                $table->timestamps();
            });
        }
        ```
        
    - Models:

        ```php
        <?php
        class Role extends Model
        {
            protected $guarded = [];

            public function users()
            {
                return $this->belongsToMany(User::class, 'role_user', 'role_id', 'user_id');
            }
        }
        ```

- Users:

    - Models:
    
        ```php
        <?php
        class User extends Authenticatable
        {
            use HasApiTokens, Notifiable;

            protected $guarded = [];

            public function roles()
            {
                return $this->belongsToMany(Role::class, 'role_user', 'user_id', 'role_id');
            }
        }
        ```

!!! important
    En `hasOne()` i `hasMany()` Laravel buscava:

    - phones.user_id = users.id  

    Però en `belongsToMany()` Laravel fa: 

    - users.id = role_user.user_id
    - roles.id = role_user.role_id

    És a dir:

    - Laravel passa obligatòriament per la taula pivot.

    I si el nom de la `taula pivot` és diferent al que s'espera Laravel, s'nterpretara de la següent forma:
    ```php
    <?php
    return $this->belongsToMany("Related", 'taula_pivot', 'Clau_foranea_taula_pivot', 'Clau_relacionada_taula_pivot');
    ```

    - `Related`: Classe de la relació
    - `taula_pivot`: Nom de la taula pivot
    - `Clau_foranea_taula_pivot`: Nom de la clau foranea relacionada en la taula pivot
    - `Clau_relacionada_taula_pivot`: Nom de la clau relacionada en la taula pivot

Ara per a fer la relació `m a m` correctament hem de fer una taula intermitja, també coneguda com a `Taula pivote`, i per a això anem a crear la migració i el model de la taula intermitja amb el següent comand:

```bash
php artisan make:migration create_role_user_table
```

I ara tocara crear el contingut de la taula pivote:

```php
<?php
 /**
 * Run the migrations.
 */
public function up(): void
{
    Schema::create('role_user', function (Blueprint $table) {
        $table->id();

        // claus foranees
        $table->foreignId('user_id');
        $table->foreignId('role_id');

        // camp extra (dades addicionals de la relació)
        $table->string('added_by')->nullable();

        $table->timestamps();

        // evita duplicats
        $table->unique(['user_id', 'role_id'], 'user_role_unique');
    });
}
/**
 * Reverse the migrations.
 */
public function down(): void
{
    Schema::dropIfExists('role_user');
}
```

!!! important
    Què significa aquesta línia?

    ```php
    <?php
    $table->unique(['user_id', 'role_id']);
    ```

    El que fa és:

    - User 1 -> admin
    - User 1 -> admin `ERROR`

    Per tant un usuari no pot tindre el mateix rol dues vegades.
Per a finalitzar l'estrucrua de la relació `m a m` quedaria de la següent forma:

- users.id  <----> role_user.user_id
- roles.id  <----> role_user.role_id