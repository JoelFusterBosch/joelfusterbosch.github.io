# Sanctum
## Què és Sanctum?
`Sanctum` és un paquet dins de `Laravel` que permet la creació de `tokens` de forma senzilla basades en `APIs`, el qual permet generar múltiples tokens API, estos tokens poden tindre diverses funcions/àmbits els quals poden permetre a l'hora d'executar-se.
## Instal·lació de Sanctum
Primerament, necessitem instal·lar el gestor de APIs de Laravel, si estàs en la versió 12 o superior, si no pots botar-te este pas:
```bash
php artisan install:api
```
Per a importar el paquet `Sanctum`, necessitem executar els següents comands:
```bash
composer require laravel/sanctum
```
Este comand crea el paquet de `Sanctum`:
```bash
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```
I per últim alcem les migracions de `Sanctum`:
```bash
php artisan migrate
```
## Implementació
### Models
Ja quan tingueu `Sanctum` correctament instal·lat i configurat ja podem usar-lo per a posar-li els tokens a l'usuari, però primer hem de modificar el model dels usuaris abans de fer els controladors de la següent forma:

```php
<?php
// Importem la llibreria de Sanctum de "HasApiTokens"
use Laravel\Sanctum\HasApiTokens;

// Implementem Authenticaable per a que puga autenticar i protrgir les rutes.
/*
IMPORTANT
Authenticable hereta de Model, així que ja té totes les funcions de "Eloquent/Model"
*/
class User extends Authenticatable
{
    use HasApiTokens, HasFactory, Notifiable;
}
```
!!! IMPORTANT
    Authenticable hereta de Model, així que ja té totes les funcions de "Eloquent/Model"

### Controladors i peticions
Ara suposem que ja tenim un controlador i peticions en el qual pugues:

- Crear usuaris (Register)

    ```php
    <?php
    // Request/Petició
    // Exten de FormRequest
    class UserRequest extends FormRequest
    {
        /**
         * Defineix els camps a omplir en el formulari:
         * nom: String obligatori màxim 255 caracters
         * email: String obligatori màxim 255 caracters que no es pot tornar a repetir
         * password: String obligatori
         */
        public function rules()
        {
            return [
                'name' => 'required|string|max:255',
                'email' => 'required|string|email|max:255|unique:users',
                'password' => 'required|string'
            ];
        }
    }
    ```

    ```php
    <?php
    // Controlador
    /**
    * Crea un usuari mitjançant:
    *  - nom
    *  - correu electrònic
    *  - contrassenya
    */
    public function createUser(UserRequest $request)
    {
        // Passa el nom, correu i contrassenya per a crear-lo
        $user = User::create([
                'name' => $request->name,
                'email' => $request->email,
                'password' => Hash::make($request->password),
             ]);
        // Resposta en forma de JSON
        return response()->json([
            'status' => 'true',
            'message' => 'Usuari creat correctament'
        ], 200);
    }
    ```

- Autenticar usuaris (Login)

    ```php
    <?php
    // Request/Petició
    class LoginUserRequest extends FormRequest
    {
        /**
         * Defineix els camps a omplir per al formulari
         * email: String obligatori màxim 255 caracters
         * password: String obligatori
         */
        public function rules()
        {
            return [
                'email' => 'required|string|email|max:255',
                'password' => 'required|string'
            ];
        }
    }
    ```
    
    ```php
    <?php
    // Controlador
    public function loginUser(LoginUserRequest $request)
    {
        // Condicional d'error si l'usuari s'enganya al posar les credencials
        if (!Auth::attempt($request->only(['email', 'password']))) {
            // Resposta en JSON
            return response()->json([
                'status' => 'false',
                'message' => 'Credencials incorrectes',
            ], 401);
        }
        // Verifica el usuari
        $user = User::where('email', $request->email)->first();
        // Resposta en JSON
        return response()->json([
            'status' => 'true',
            'message' => 'Usuari autenticat correctament',
        ], 200);
    }
    ```

#### Creació del token en el controlador
Per a proporcionar-li el token a l'usuari, hem de ficar una línia extra en la resposta, la qual s'anomena `token`, que es creara de la següent forma:

```php
<?php
// 'token': Etiqueta JSON que creara el token
// createToken('api-token')->plaintext: Funció que creara el token en forma de "text pla"
return response()->json([
    'token' => $user->createToken('api-token')->plaintext
], 200)
```

I perquè estiguen en les funcions anteriors de `Register` i `Login` sols hem d'afegir la línia anterior al codi abans esmentat en la resposta del JSON:

```php
<?php
return response()->json([
    'status' => 'true',
    'message' => 'Usuari creat correctament',
    'token' => $user->createToken('api-token')->plaintext
], 200);
```
### Creació de les rutes i els middlewares necessaris
Ara que ja tenim creat el controlador per a crear els usuaris amb els tokens ara necessitem provar-los i que es puguen accedir mitjançant rutes, en el fitxer `api.php` que es troba en la següent ruta `routes/api.php`, suposem que també les teníem en anterioritat:

```php
<?php
// Endpoint /register
// Registra un usuari 
Route::post('/register', [AuthController::class, 'createUser'])
    ->name('register');
// Endpoint /login
// Autentica un usuari
Route::post('/login', [AuthController::class, 'loginUser'])
    ->name('login');
``` 

Amb això tot el món pot accedir sense necessitat del token, i tot el món podria accedir, inclòs sense falta d'autenticació, així que ara afegirem un middleware perquè sols es puga accedir si l'usuari està registrat:

```php
<?php
// Executa el middleware de Sanctum abans de fer la petició
Route::middleware('auth:sanctum')
    // Si funciona fa el endpoint de "/user"
    ->get('/user', function (Request $request) {
        return $request->user();
    })->name('user');
```

Ara sols fa falta provar els endpoint de `/user` per a vore si funciona correctament, si tot ha funcionat deuria de:

- Donar error si no has fet login.

<p align= "center">
    <img src="" alt="Error" width="500"/>
 </p>
<p align="center"><em>Fig 1: Error per falta de tokens</em></p> 

- Funcionar correctament si has fet login.

<p align= "center">
    <img src="" alt="Execució correcta" width="500"/>
 </p>
<p align="center"><em>Fig 2: Execució correcta pels tokens</em></p> 
