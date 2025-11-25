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
## Afegir endpoints en laravel
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

## Afegir layouts
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
    <p>Benvolguts al meu lloc</p> {{--Ací posarem el contingut--}}
@endsection {{--Tanquem la secció del contingut--}}
```
4. Posem les pàgines en el fitxer `web.php` i verifiquem els resultats
```php
Route::view('/index2', 'blade.index')-> name('blade.index');
Route::view('/about2', 'blade.about')-> name('blade.about');
Route::view('/services', 'blade.services')-> name('blade.services');
Route::view('/contact', 'blade.contact')-> name('blade.contact');
```

## Afegir components
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
        {{--Entre l'apartat de "slot" i "endslot" posarem el contingut de HTML--}}
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

### GET
```php
Route::get('/home', function () {
    return view('home');
});
```
### POST
```php
Route::post('/submit', function () {
    return 'Formulario enviado';
});
```
### PUT
```php
Route::put('/profile', function () {
    return 'Perfil actualizado';
});
```
### DELETE
```php
Route::delete('/post', function () {
    return 'Publicación eliminada';
});
```