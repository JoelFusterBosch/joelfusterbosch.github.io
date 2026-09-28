# Model MVC en Laravel
En laravel usa el sistema MVC (<b>M</b>odel, <b>V</b>ista, <b>C</b>ontrolador), els quals és trobraran en les següents carpetes dins del projecte laravel:

- Model:
```bash
/app/Models
```
- Vista:
```bash
/resources/views
```
- Controlador:
```bash
/app/Http/Controllers
```
## Configuració per a la web
### Afegir endpoints en laravel
Per a afegir endpoints a laravel hem de crear un fitxer de php nou amb la terminació `blade.php` en la carpeta `resource/views` amb el contingut que tu vullgues:
```php
//Fitxer index.blade.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    <h1>Holaa</h1>
</body>
</html>
```
I després afegir-lo a el fitxer `web.php` en la ruta `routes/web.php` de la següent forma:
```php
<?php
Route::view('/index', 'landing.index')-> name('landing.index');
```
Quedant de la següent forma:
```php
<?php

use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});

Route::view('/index', 'landing.index')-> name('landing.index');

```
Guardes els canvis, i com tenim el servidor de nginx no fa falta reiniciar-lo i podem accedir al contingut mitjançant <a href="http://localhost:8080/index">http://localhost:8080/index</a>, però si no disposes de un servidor de nginx pots executar el següent comand per a alçar un xicotet servidor que ja té php:

```bash
php artisan serve
```

### Afegir layouts
Per a evitar les repeticions en la estructura de la pàgina podem reutilitzar parts de la pàgina web per a estalviar-mo'n codi, és pot realitzar de la següent forma:

1. Crea una carpeta anomenada `_layouts` per a organitzar el contingut dels layouts sempre en la primera carpeta

2. Crea un fitxer, per exemple `base.blade.php` i pots posar el contingut corresponent:
```php
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>
        // Esta etiqueta de blade permet modificar el contingut del que n'hi haga en la etiqueta mantenint la estructura
        @yield('tittle') // En este cas cambiara el titol
    </title>
</head>
<body>
    <header>
        @yield('head') // En este cas cambiara la capçalera
    </header>
    <main>
        @yield('content') // En este cas cambiara el contingut
    </main>
    <footer>
        <p>Peu de pàgina &copy; 2025</p>
    </footer>
</body>
</html>
``` 
3. Ara posem-lo en les altres pàgines usant etiquetes de blade
```php
@extends('_layouts.base') {{--Exten el contingut del fitxer base.blade.php--}}

@section('tittle', 'Home') {{--Posem com a titol "Home"--}}

@section('head') {{--Obrim la secció de la capçalera--}}
    <h1>Pàgina de inici</h1> {{--Ací posarem la capçalera--}}
@endsection {{--Tanquem la secció de la capçalera--}}

@section('content') {{--Obrim la secció del contingut--}}
    <p>Benvolguts al meu primer lloc web!</p> {{--Ací posarem el contingut--}}
@endsection {{--Tanquem la secció del contingut--}}
```
4. Posem les pàgines en el fitxer `web.php` i verifiquem els resultats
```php
<?php
Route::view('/index2', 'blade.index')-> name('blade.index');
Route::view('/about2', 'blade.about')-> name('blade.about');
Route::view('/services', 'blade.services')-> name('blade.services');
Route::view('/contact', 'blade.contact')-> name('blade.contact');
```

### Afegir components
Al igual que el layout podem utilitzar els components per a emplenar la pàgina sense repetir tant el codi, i es pot realitzar de la següent forma:

1. Crees un fitxer `card.blade.php` en una carpeta anomenada `_components` per a posar el contingut que anem a substituir:
```php
<div class="card">
    <h2>{{ $title }}</h2> //Titol que tindra el component
    <img src="{{ asset('assets/images/servicio.png') }}" alt="Servei" width="128px"> {{--Ací insertarem una imatge que si volem que es mostre al public la tenim que posa en la carpeta "assets", creem una carpeta "images" i dins d'eixa carpeta posem la imatge--}}
    <p>{{ $content }}</p> //Text que tindra el paragraf
</div>
```
2. La forma en la que s'utilitzen els components per a definir en altres pàgines és la següent:
    ```php
        //Usem la etiqueta "slot" per a usar components
        @slot('Nom de la variable','Valor de la variable'); 
    ```
    o és pot també d'esta forma
    ```php
    //Usem la etiqueta "slot" per a usar components
    @slot('Nom de la variable')
        {{--Entre el apartat de "slot" i "endslot" posarem el contingut de HTML--}}
        <p>Contingut en HTML</p>
        {{--Usem la etiqueta "endslot" per a tancar els components--}}
    @endslot
    ```

3. Ací un exemple de com és poden usar de les 2 formes esmentades anteriorment:
    - Forma simple:
    ```php
        @slot('title', 'Servici 1');
    ```
    - Forma amb html
    ```php
        @slot('content')
            <p>Descripció breu del servici 1.</p>
        @endslot
    ```
4. Quan tingam el fitxer podem utilitzar-lo per a fer una llista de productes/serveis com en el següent exemple anomenat `services.blade.php`
```php

@section('content')
    <p>Llistat de serveis oferits</p>
    @component('_components.card')
        {{--Sí son etiquetes compostes, el "slot" que no tinga contingut HTML 
        no es posara la etiqueta "endslot", mentres les que si tenen contingut HTML si tindran 
        la etiqueta "endslot"--}}
        @slot('title', 'Servici 1');
        @slot('content')
            <p>Descripció breu del servici 1.</p>
        @endslot
    @endcomponent
    @component('_components.card')
        @slot('title', 'Servici 2');
        @slot('content')
            <p>Descripció breu del servici 2.</p>
        @endslot
    @endcomponent
    @component('_components.card')
        @slot('title', 'Servici 3');
        @slot('content')
            <p>Descripció breu del servici 3.</p>
        @endslot
    @endcomponent
@endsection

``` 
## Model
Per a afegir els models necesitem els valors de la base de dades sense modificar-la, així que abans de fer els models anem a explicar i fer migracions
### Afegir migracions
Pots afegir una migració amb el següent comand:
```bash
php artisan make:migration Nom_de_la_migració
```
I quan crees la migració voras que s'ha creat un fitxer php rn la carpeta `src/database/migrations` en la qual es mostrara le data en la que has fet la migració amb el següent contingut:
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        //
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        //
    }
};
```
Si vols crear les taules de la base de dades anem a la funció que és diu `up()` i seguirem el següent exemple:
```php
<?php
public function up(): void
    {
        //Aquesta linia permet crear la taula per a la base de dades
        Schema::create('exemple', function (Blueprint $table){
            /*
            CAMPS
            */
            //Esta línia diu que este camp és un "id"
            $table->id('id');

            //Esta línia diu que este camp és una cadena de text
            $table->string('Hola');

            //Esta línia diu que este camp és una cadena de text molt llarga
            $table->text('Lorem_Ipsum');

            //Esta línia diu que este camp és un enter
            $table->integer('edat');

            //Esta línia diu que este camp és un "booleano"
            $table->boolean('actiu');

            //Esta línia diu que este camp és una data
            $table->date('data');

            //Esta línia diu que este camp és un conjunt de valors
            $table->enum('Rol', ['usuari', 'administrador', 'conserge']);

            //Esta línia diu que este camp és un número decimal
            //que te els següents parametres: 
            //float(nom, total de digits, dígits_decimals)
            $table->float('preu',8,2);

            //Esta línia diu que este camp és un número decimal molt gran
            //que té els mateixos parametres que "float"
            //double(nom, total de digits, dígits_decimals)
            $table->double('pi',8,9);
            /*
            o també
            $table->decimal('pi',8,9);
            */

            //Esta línia diu que esta columna és un json
            $table->json('usuaris');

            /*
            MODIFICADORS
            */

            //Aquest modificador permet que el valor puga tindre el valor "null"
            $table->string('columna_NO_nul·lable')->nullable();

            //Aquest modificador NO permet que el valor puga tindre el valor "null"
            $table->string('columna_nul·lable')->notNullable();

            //Aquest modificador permet posar un valor per defecte
            $table->string('columna_per_defecte')->default("Sense valor");

            //Aquest modificador permet que un camp puga ser únic
            $table->string('Camp_amb_valor_unic')->unique();

            //Aquest modificador permet crear un index per al camp
            $table->string('Camp_amb_index')->index();

            //Aquest modificador permet crear una clau foranea
            $table->unsignedBigInteger('clau_foranea');
            $table->foreign('clau_foranea')->references('id')->on('taula');
            // o també ho pots fer de la següent forma
            $table->foreignId('clau_foranea')->constrained('taula_a_referenciar')->onDelete('cascade');
            // o també
            $table->foreignId('clau_foranea')
                   ->references('id')
                   ->on('taula_a_referenciar')
                   ->onDelete('cascade');
            //Aquest modificador permet crear un camp sense signe
            $table->string('Camp_sense_signe')->unsigned();
            
            //Aquest modificador permet colocar el camp després d'un altre camp
            $table->string('Cognom')->after('Nom');

            //Aquest modificador permet colocar el camp abans d'un altre camp
            $table->string('Nom')->before('Cognom');

            //Aquest modificador permet fer que un camp siga la clau primaria
            $table->string('Clau primaria')->primary();

            /*
            IMPORTANT, pots mesclar més d'un modificador en un camp, per exemple:
            */
            $table->string('titol', 255)->notNullable()->unique();
        });
    }
```
Amb l'exemple explicat procedim a fer una migració propia, per exemple:
```php
<?php
public function up(): void
    {
        Schema::create('paises', function (Blueprint $table){
            $table->id('id');
            $table->string('nombre_pais');
        });
    }
```
I quan estiga pots fer el següent comand per a fer la migració i crear les taules en la base de dades de forma automàtica:
```bash
php artisan migrate
```
### Afegir models
Per a crear un model podem fer el següent comand:
```bash
php artisan make:model Nom_del_model
```
O este altre per a crear el model i la migració:
```bash
php artisan make:model Nom_del_model -m
```
Quan executeu qualsevol dels 2 apareixer el model en la carpeta `src/app/Models` i apareixera un fitxer php amb el nom que li hages posat en el comand del model
!!! important
    Al crear el model assegurat que el crees en la primera lletra en majuscula i en singular, Exemple: `Usuari` perque laravel reconeix per defecte esta estructura i redirijira a la taula `usuaris`, però es pot modificar la redirecció per si tens una taula `u$uaris` per exemple, però ho vorem més endavant.
Ara amb el fitxer ja creat apareixera el següent:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Nom_del_model extends Model
{
    //
}
```
!!! nota
    Pots especificar el nom de la taula de la següent forma:
    ```php
    <?php
    namespace App\Models;
    use Illuminate\Database\Eloquent\Model;
    class Note extends Model
    {
        // Especificar el nom de la taula
        protected $table = 'app_model';
    }
    ```
Amb el model ja creat anem a construïrlo de la següent forma:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Pais extends Model
{
    // Aquesta propietat pemet posar la clau primaria al camp de la base de dades
    protected $primaryKey = 'id';

    //Aquesta propietat permet posar els camps necesaris de la base de dades
    protected $fillable = ['nom_pais'];

    //Aquesta propietat no permet assignar els camps a la base de dades
    protected $guarded

    //Aquesta propietat permet convertir automàticament els tipus dels camps
    protected $casts

    //Aquesta propietat permet no mostrar els camps en el JSON 
    protected $hidden
}
```
Amb l'exemple explicat procedim a fer un model propi, per exemple:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Pais extends Model
{
    protected $primaryKey = 'id';
    protected $fillable = ['nombre_pais'];
}
```
I amb això ja tenim el model ja fet, ara anirem al següent apartat el `controlador`
## Controlador
### Exemple sencill
Per a crear un controlador hem de executar el següent comand:
```bash
php artisan make:controller Nom_del_controlador
```
En este cas crearem un controlador anomenat `UserController`:
```bash
php artisan make:controller UserController
```
I quan l'executem tindrem el següent resultat:
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class Nom_Controlador extends Controller
{
    //
}
```
Que en UserController es voria de la següent forma:
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class UserController extends Controller
{
    //
}
```
I per a comprovar el seu funcionament posarem el següent dins la funció:
```php
<?php
class UserController extends Controller
{
    public function index() {
        dd('Hola desde UserController@index');
    }
}
```
Ara en el fitxer `web.php` posarem el següent:
```php
<?php

use Illuminate\Support\Facades\Route;
//Indica la ruta al controlador
use App\Http\Controllers\UserController;

// Endpoint al que apuntara la funció del endpoint
Route::get('/', [UserController::class, 'index'])->name('usuario.index');
```
I en el navegador quan poseu `http:localhost:8080` apareixerà el següent:
``` php
"Hola desde UserController@index" // app/Http/Controllers/UserController.php:10
```
### MVC real
Veiem que s'ha generat correctament, però amb els controladors és poden fer moltes més coses, continuant en el UserController anem a crear la vista de usuaris en `/views/users/index.blade.php` el qual tindra el següent contngut:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Usuaris</title>
</head>
<body>
    <h1>Lista de usuaris</h1>
</body>
</html>
```
Quan tingam la vista haurem de posar-la en el controlador de la següent forma:
```php
<?php
class UserController extends Controller
{
    public function index() {
        return view('users.index');
    }
}
```
#### Com usar els models en els controladors
En el controlador posarem el següent:
```php
<?php
use App\Models\User;
```
Quedant de la següent forma:
```php
<?php

namespace App\Http\Controllers;
use App\Models\User;

use Illuminate\Http\Request;

class UserController extends Controller
{
    public function index() {
        return view('users.index');
    }
}
```
Això el que permet és usar els models en els controladors, quedant de la següent forma:
```php
<?php
namespace App\Http\Controllers;
use App\Models\User;
use Illuminate\Http\Request;
class UserController extends Controller
{
    public function index() {
        $usuarios = User::all();
        return view('users.index');
    }
}
```
Amb això ja podem usar els objectes dels models en els controladors
#### Pasar dades a la vista
Per a pasar dades a la vista podem fer-lo de la següent forma:
```php
<?php
return view('usuarios.index', compact('usuarios'));
```
El que fa això és pasar un `array` de forma asociativa on la clau dels usuaris contindra la col·lecció d'usuaris que hem recuperat de la base de dades.
I quedaria de la següent forma la funció index:
```php
<?php
public function index() {
    $usuarios = User::all();
    return view('users.index', compact('usuarios'));
}
```
Ara modificarem el fitxer `index.blade.php` que haviem creat en anterioritat de la següent forma:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Usuaris</title>
</head>
<body>
    <h1>Llista de usuaris</h1>
    <ul>
        @foreach ($usuarios as $usuario)
            <li>{{ $loop->iteration }}. {{ $usuario->name }} ({{ $usuario->age }} años)</li>
        @endforeach
    </ul>
</body>
</html>
```
!!! nota
    el que fa la etiqueta `@foreach` es que fa un bucle `foreach` amb els usuaris que havíem configurat en el controlador de usuaris que haviem modificat en anterioritat en `UserController.php`, i altes funcions per a recorrer la llista podrien ser: 

    - $loop->first: Indica si es el primer elemento del bucle.
    - $loop->last: Indica si es el último elemento del bucle.
    - $loop->index: Indica el índice actual del bucle (empezando desde 0).
    - $loop->remaining: Indica cuántos elementos quedan por recorrer.
    - $loop->depth: Indica la profundidad del bucle (en caso de bucles anidados).

I podem modificarla per a que si no n'hi han usuaris diga que no n'hi han usuaris disponibles:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Usuaris</title>
</head>
<body>
    <h1>Llista de usuaris</h1>
    @if ($usuarios->isEmpty())
        <p>No hi han usuaris disponibles.</p>
    @else
        <ul>
            @foreach ($usuarios as $usuario)
                <li>{{ $loop->iteration }}. {{ $usuario->name }} ({{ $usuario->age }} años)</li>
            @endforeach            
        </ul>
    @endif
</body>
</html>
```
I per últim per a mitlllorar encara més el codi podriem usar la etiqueta `@switch` per a fer condicions en el `@foreach` establert anteriorment:
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Usuaris</title>
</head>
<body>
    <h1>Lista de usuarios</h1>
    @if ($usuarios->isEmpty())
        <p>No hay usuarios disponibles.</p>
    @else
        <ul>
            @foreach ($usuarios as $usuario)
            @switch(true)
                @case($usuario->age < 18)
                    <p>{{ $usuario->name }} es menor de edad.</p>
                    @break
        
                @case($usuario->age >= 18 && $usuario->age <= 65)
                    <p>{{ $usuario->name }} es adulto.</p>
                    @break
        
                @default
                    <p>{{ $usuario->name }} es jubilado.</p>
            @endswitch
        @endforeach          
        </ul>
    @endif
</body>
</html>
```
#### Crear dades de prova
##### utils
Pots usar el hsaah per a les contrasenyes de la següent forma:
```php
<?php
use Illuminate\Support\Facades\Hash;
```
Ja amb els utils necessaris anem a crear 2 usuaris inventats en el controlador.
!!! nota
    Sols són propòsits experimentals, per a insertar usuaris de forma correcta deuriem de usar els de la base de dades.
```php
<?php
namespace App\Http\Controllers;
use App\Models\User;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Hash;
class UserController extends Controller
{
    public function index() {
        $usuaris = User::all();
        return view('users.index', compact('usuaris'));
    }
    public function create() {
        // Creem a l'usuari María utilizant el model
        $usuari = new User();
        $usuari->name = 'María García';
        $usuari->email = 'mgarcia@example.com';
        $usuari->password = Hash::make('123456');
        $usuari->age = 30;
        $usuari->address = 'Carrer Major 1';
        $usuari->zipCode = 28080;
        $usuari->save();
        
        // Creem a l'usuari Juan Pérez utilitzant el mètode create()
        User::create([
            'name' => 'Juan Pérez',
            'email' => 'jperez@example.com',
            'password' => Hash::make('password'),
            'age' => 25,
            'address' => 'Carrer Fals 123',
            'zipCode' => 28080
        ]);
    
        // Creem a l'usuari José Flores utilizant el mètode create()
         User::create([
            'name' => 'José Flores',
            'email' => 'jflores@example.com',
            'password' => Hash::make('flores'),
            'age' => 25,
            'address' => 'Carrer Fals 123',
            'zipCode' => 28080
        ]);
    
        // Redirigim a la vista de listat d'usuaris
        return redirect()->route('users.index');
    }
}
```
Una vegada creats posarem el endpoint al que ha d'apuntar en el fitxer `web.php`
```php
<?php
Route::get('/create', [UserController::class, 'create'])->name('users.create');
```
##### us dels where()
També podem usar els `where` per a fer condicionals per als que agafem de la base de dades, ací un exemple de com es poden usar:

- = 	Igual
- != 	Diferent
- `>`  	Major que
- `>=` 	Major o igual que
- < 	Menor que
- <= 	Menor o igual que
- LIKE 	Coincideix amb el patró
- NOT LIKE 	No coincideix amb el patró

#### Accés a bases de dades de forma alternativa
##### SQL pur
Pots conseguir una consulta de SQL pura de la següent forma:
```php
<?php
$usuarios = DB::select(DB::raw('SELECT * FROM users'));
```
I en esta seria per a fer `JOIN` amb altra taula de la base de dades:
```php
<?php
$usuarios = DB::select(DB::raw('SELECT users.*, posts.title FROM users INNER JOIN posts ON users.id = posts.user_id'));
```
###### Mètodes estatics
Amb els mètodes estatics es poden realitzar de la següent forma:
```php
<?php
//insert()
//Inserta un nou registre en la taula
DB::table('users')->insert(['name' => 'Pedro', 'email' => 'correo@example.com', 'password' => Hash::make('password')]);
//update()
//Actualiza un registro en la tabla.
DB::table('users')->where('id', 1)->update(['name' => 'Pedro Modificat']);
//delete()
//Elimina un registre de la taula.
DB::table('users')->where('id', 1)->delete();
//get()
//Recupera tots els registres de la taula.
DB::table('users')->get();
//find()
//Busca un registre pel seu ID.
DB::table('users')->find(1);
//first()
//Recupera el primer registre de la taula.
DB::table('users')->first();
//where()
//Filtra els resultats segons una condició.
DB::table('users')->where('age', '>=', 18)->get();
//whereIn()
//Filtra els resultats segons una llista de valors.
DB::table('users')->whereIn('zipCode', [28080, 28081])->get();
//orderBy()
//Ordena els resultats segonn un camp.
DB::table('users')->orderBy('name')->get();
//count()
//Compta el número de registres de la taula.
DB::table('users')->count();
//sum()
//Suma un camp de la taula.
DB::table('users')->sum('age');
//avg()
//Calcula el promedi de un camp de la taula.
DB::table('users')->avg('age');
//max()
//Torna el valor màxim d'un camp de la taula.
DB::table('users')->max('age');
//min()
//Torna el valor mínim d'un camp de la taula.
DB::table('users')->min('age');
```
## Peticions CRUD
#### GET
```php
<?php
Route::get('/home', function () {
    return view('home');
});
```
#### POST
```php
<?php
Route::post('/submit', function () {
    return 'Formulario enviado';
});
```
#### PUT
```php
<?php
Route::put('/profile', function () {
    return 'Perfil actualizado';
});
```
#### DELETE
```php
<?php
Route::delete('/post', function () {
    return 'Publicación eliminada';
});
```