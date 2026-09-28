Per a instl·lar Laravel facilment clona este repositori:
```bash
git clone https://github.com/jbeteta-ies/laravelinit.git
```
Ara canviem a esta rama:
```bash
git checkout 5.3-inicio
```
Comenta la linia 34 de Dockerfile, perque php 8.4 ve instalat per defecte
```dockerfile
# RUN pecl install xdebug && docker-php-ext-enable xdebug
```
I borrem el el contingut dins de `src` de la carpeta `php` i borrem també el contingut de la carpeta `data` en la carpeta de `mysql` 
i després muntem els contenidors amb el següent comand:
```bash
docker compose up -d --build
```

Si en el contenidor de php ix buit, pots executar este comand per a instal·lar laravel:
```bash
composer create-project laravel/laravel .
```
Ara entrem al contenidor de `php` per a executar els següents comands per a canviar el propietari de `root` a `www-data`:
```bash
chown -R www-data:www-data /var/www/html/storage
```
```bash
chown -R www-data:www-data /var/www/html/database
```
Ara ves al fitxer `.env` que és troba en `src/.env` i descomenta les següents linies:
```bash
DB_CONNECTION=sqlite
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=laravel
# DB_USERNAME=root
# DB_PASSWORD=
```
I canvia al següent:
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=alumno
DB_PASSWORD=alumno
```