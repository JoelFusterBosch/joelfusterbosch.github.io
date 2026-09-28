## Implementació
### Creació de la base de dades i l’usuari.
Entrem a la base de dades amb el següent comand i podem entrar de a següent forma:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Accés al mysql mitjançant el la BD de Azure.png" alt="Accés a la BD desde el terminal" width="800"/>
</p>
<p align="center"><em>Accés a la BD desde el terminal</em></p>

Ara crearem la base de dades `prova` junt amb l’usuari `prova` amb els següents comands:

```bash
CREATE DATABASE prova;
```

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Creació de la BD prova.png" alt="Creació de la BD prova" width="300"/>
</p>
<p align="center"><em>Creació de la BD prova</em></p>

```bash
CREATE USER 'prova'@'%' IDENTIFIED BY 'ContrasenyaSegura';
GRANT ALL PRIVILEGES ON prova.* TO 'prova'@'%';
FLUSH PRIVILEGES;
```

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Crear l&apos;usuari prova i assignant-li permisos.png" alt="Creació de l'usuari prova i assignant-li permisos" width="600"/>
</p>
<p align="center"><em>Creació de l'usuari prova i assignant-li permisos</em></p>

```bash
USE prova;
```

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Creació de la taula prova.png" alt="Creació de la taula prova" width="400"/>
</p>
<p align="center"><em>Creació de la taula prova</em></p>

```bash
CREATE TABLE prova (
id INT AUTO_INCREMENT PRIMARY KEY,
contingut TEXT
);
```

I ja tindriem la base de dades i l’usuari creat

### Variables d’entorn en l’App Service
Anem a l’App Service que havíem configurat en anterioritat 

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/App Service.png" alt="App Service a utilitzar" width="1200"/>
</p>
<p align="center"><em>App Service a utilitzar</em></p>

I anem al menú de l’esquerra i apretem al desplegable on diu `Configuración`:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Desplegable de configuracions.png" alt="Desplegable de configuracions" width="300"/>
</p>
<p align="center"><em>Desplegable de configuracions</em></p>

I s’obrira el següent:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Variable d&apos;entorn.png" alt="Variables d'entorn" width="300"/>
</p>
<p align="center"><em>Variables d'entorn</em></p>

Li apretem a `Variables de entorno` i s’obrira el següent:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Menú de variables d&apos;entorn.png" alt="Menú de variables d'entorn" width="900"/>
</p>
<p align="center"><em>Menú de variables d'entorn</em></p>

Li apretem a `Agregar` i posarem les següents dades:

```bash
DB_HOST: mysql-cloudazure.mysql.database.azure.com
DB_PASSWORD: prova
DB_USER: prova
```

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Creació de la variable de entorn.png" alt="Formulari per a la creació de la variables d'entorn" width="600"/>
</p>
<p align="center"><em>Formulari per a la creació de la variables d'entorn</em></p>

Deuria de vore’s de la següent forma:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Creació de la variable de entorn.png" alt="Formulari per a la creació de la variables d'entorn" width="700"/>
</p>
<p align="center"><em>Formulari per a la creació de la variables d'entorn</em></p>

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Resum de les variables d&apos;entorn.png" alt="Resum de les variables d'entorn" width="800"/>
</p>
<p align="center"><em>Resum de les variables d'entorn</em></p>

Ara crearem un fitxer anomenat `connexió.php` amb el següent contingut:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Codi de la aplicació.png" alt="Codi del fitxer connexió.php" width="700"/>
</p>
<p align="center"><em>Codi del fitxer connexió.php</em></p>

i el pujarem al repositori de Github:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Afegint els canvis al repositori.png" alt="Afegint els canvis al repositori" width="800"/>
</p>
<p align="center"><em>Afegint els canvis al repositori</em></p>

Per últim sincronitzem els canvis:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Canis afegits al repositori.png" alt="Canvis afegits al repositori" width="800"/>
</p>
<p align="center"><em>Canvis afegits al repositori</em></p>

I ja podrem vore en el navegador usant la url de la app Service en l’endpoint `/connexio.php`:

<p align= "center">
    <img src="../imatges/Connexió de App Service amb MySQL/Demostració de la aplicació en funcionament.png" alt="Demostració de la aplicació en funcionament" width="900"/>
</p>
<p align="center"><em>Demostració de la aplicació en funcionament</em></p>