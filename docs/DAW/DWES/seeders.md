Els seeders ens permeten posar dades per defecte en la BD, sense la necessitat de posar dades de forma manual i automatitzant i poblant la BD de dades.

## Creació dels seeders
Per a crear un seeder nou has de executar el següent comand:
```bash
php artisan make:seeder "Nom del seeder"
```

Ara per exemple per al seeder el podem crear de la següent forma:
```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use App\Models\Product;

class ProductSeeder extends Seeder
{
    /**
    * Run the database seeds.
    */
    public function run(): void
    {
        // Creem un producte d'exemple
        Product::create([
            'name' => 'Tomaques',
            'short_description' => 'Tomaques de Joel',
            'description' => 'Tomaques fresques de la horta de Joel al millor qualitat i preu',
            'price' => 2.99,
        ]);
    }
}
```
## Execució dels seeders
### Execució d'un sol seeder

Ara per a executar el seeder que hem creat sols hem d'executar el següent comand:

```bash
php artisan db:seed --class=ProductSeeder
```
El que fara és sols executar el seeder que té eixe nom exacte.


Si vols executar tots els seeders pots executar  este altre comand:

```bash
php artisan db:seed
```

Aquest executara tots els seeders que n'hi hagen en la carpeta `database/seeders`