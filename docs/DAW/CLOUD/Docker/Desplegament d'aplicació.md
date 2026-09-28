## Crear els contenidors de Docker
Crear una nova xarxa en Docker per als contenidors de mongo i express anomenada `xarxa-mongo`.
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Creació de la xarxa per al contenidor de mongodb.png" alt="Creació de la xarxa per al contenidor de mongodb" width="300"/>
</p>
<p align="center"><em>Creació de la xarxa per al contenidor de mongodb</em></p> 

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Resum de les xarxes.png" alt="Resum de les xarxes disponibles" width="300"/>
</p>
<p align="center"><em>Resum de les xarxes disponibles</em></p> 

Ara despleguem el contenidor en la xarxa que hem creat `xarxa-mongo`.
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Iniciament de mongo.png" alt="Iniciament de l'aplicació de mongo" width="300"/>
</p>
<p align="center"><em>Iniciament de l'aplicació de mongo</em></p> 

Per a desplegar el contenidor d’express ho fem amb el port predefinit `8081:8081`, mitjançant variables d’entorn per a connectar-lo al contenidor `mongodb` amb el user i pass de mongo. El contenidor s’anomenarà `mongo-express`.
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Iniciament de mongodb.png" alt="Iniciament de l'aplicació de mongodb" width="300"/>
</p>
<p align="center"><em>Iniciament de l'aplicació de mongodb</em></p>

Verifiquem que els dos contenidors estan creats i llançats correctament, amb mapeig de ports, amb el nom de mongo canviat, etc
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Resum de les imatges de Docker.png" alt="Resum de les imatges de Docker" width="300"/>
</p>
<p align="center"><em>Resum de les imatges de Docker</em></p>

## Accedir a la web i crear la base de dades de `user-account`
Comprova que funciona l’entorn visual web de express en un navegador amb:

```bash
docker logs mongo-express
```

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Logs del contenidor de mongodb.png" alt="Logs del contenidor de mongodb" width="300"/>
</p>
<p align="center"><em>Logs del contenidor de mongodb</em></p>

I en el navegador posem el següent:

```bash
http://localhost:8081
```

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Login.png" alt="Login de la app de mongodb" width="300"/>
</p>
<p align="center"><em>Login de la app de mongodb</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Pàgina de l&apos;aplicació.png" alt="Pàgina de l&'aplicació" width="300"/>
</p>
<p align="center"><em>Pàgina de l&'aplicació</em></p>

Creem la DB `user-account` en l’entorn visual:
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Creació de la DB.png" alt="Creació de la DB" width="300"/>
</p>
<p align="center"><em>Creació de la DB</em></p>

## Actualitzar el perfil en la app de Node.js
En el fitxer server.js del projecte (App), canviem el valor de la variable databaseName que serà la DB creada per a que connectem a ella: `user-account`.

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Canvi nom BD en el server.js.png" alt="Canvi nom BD en el server.js" width="300"/>
</p>
<p align="center"><em>Canvi nom BD en el server.js</em></p>

I també canviem la variable tant la local com la de Docker al usuari i la contrasenya corresponent, en este cas:

- Usuari: admin
- Contrasenya: password 

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Canvis a la url.png" alt="Canvis a la url" width="300"/>
</p>
<p align="center"><em>Canvis a la url</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Canvis actualitzats.png" alt="Canvis actualitzats" width="300"/>
</p>
<p align="center"><em>Canvis actualitzats</em></p>

Des de dins del directori de l’aplicació llancem el servidor node i ha d’eixir el següent:
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Iniciament de node.js.png" alt="Iniciament de node.js" width="300"/>
</p>
<p align="center"><em>Iniciament de node.js</em></p>

Provem l’aplicació en local en un navegador posant el següent:

```bash
http://localhost:3000
```

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/url express.png" alt="url de la app de node" width="300"/>
</p>
<p align="center"><em>url de la app de node</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Pàgina de node.png" alt="Pàgina de la app de node" width="300"/>
</p>
<p align="center"><em>Pàgina de la app de node</em></p>

Editem el nom i interessos mitjançant navegador per a veure com la nostra DB funciona correctament amb el botó `Edit Profile`.

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Update Profile.png" alt="Actualitzant el perfil" width="300"/>
</p>
<p align="center"><em>Actualitzant el perfil</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Updating.png" alt="Actualitzant el perfil" width="300"/>
</p>
<p align="center"><em>Actualitzant el perfil</em></p>

I quan acabem li apretem al boto de `Update Profile`:

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Canvis actualitzats.png" alt="Canvis actualitzats" width="300"/>
</p>
<p align="center"><em>Canvis actualitzats</em></p>

Entrem en l’entorn d’express per a vore la DB i els atributs modificats en el següent ordre amb el boto que posa `View`:
User-account -> users 
<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/DB creada.png" alt="DB User-account" width="300"/>
</p>
<p align="center"><em>DB User-account</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Taula users.png" alt="Col·lecció users" width="300"/>
</p>
<p align="center"><em>Col·lecció users</em></p>

<p align= "center">
    <img src="../imatges/Desplegament de la aplicació/Resultat de la modificacó.png" alt="Resultat de la modificació del perfil en la app de node" width="300"/>
</p>
<p align="center"><em>Resultat de la modificació del perfil en la app de node</em></p>