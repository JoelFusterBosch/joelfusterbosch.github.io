## Instal·lació de Docker-compose
Entrem com a administrador `root` i executem el següent comand que servira per a tindre els paquets e instal·lar-lo:
<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Instal·lació del docker-compose.png" alt="Instal·lació del docker-compose" width="300"/>
</p>
<p align="center"><em>Instal·lació del docker-compose</em></p> 

Ara li donem permisos de escritura:
<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Permisos per al docker-compose.png" alt="Permisos per al docker-compose" width="300"/>
</p>
<p align="center"><em>Permisos per al docker-compose</em></p> 

I eixim de root i fem docker-compose –version per a vore quina versió de Docker-compose tenim:
<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Versió del docker-compose.png" alt="Versió del docker-compose" width="300"/>
</p>
<p align="center"><em>Versió del docker-compose</em></p> 

## Creació i configuració del Docker-compose
Per a executar el docker-compose necessitem tindre un `docker-compose.yaml` amb el següent contingut:

```bash
nano docker-compose.yaml
```

<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Creació del fitxer docker-compose.yaml.png" alt="Creació del fitxer docker-compose.yaml" width="300"/>
</p>
<p align="center"><em>Creació del fitxer docker-compose.yaml</em></p> 

<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Contingut del docker-compose.yaml 1.png" alt="Contingut del docker-compose.yaml" width="300"/>
</p>
<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Contingut del docker-compose.yaml 2.png" alt="Contingut del docker-compose.yaml" width="300"/>
</p>
<p align="center"><em>Contingut del docker-compose.yaml</em></p> 

I quan acabem de modificar el docker-compose.yaml executem el següent comand per a crear els contenidors i les xarxes que hem introduït en el yaml:

<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Execució del docker-compose.yaml.png" alt="Execució del docker-compose.yaml" width="300"/>
</p>
<p align="center"><em>Execució del docker-compose.yaml</em></p> 

Quan acabe de construir-se anem al navegador i posem 

```bash
http://localhost:8081
```

i deuria de aparèixer el següent:

<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/Login en la pàgina de mongo.png" alt="Login en la pàgina de mongo" width="300"/>
</p>
<p align="center"><em>Login en la pàgina de mongo</em></p> 

I quan poses el usuari i la contrasenya deuria de aparèixer la pàgina correctament:

<p align= "center">
    <img src="../imatges/Iniciar contenidors en Yaml/App mongo.png" alt="App mongo funcionant" width="300"/>
</p>
<p align="center"><em>App mongo funcionant</em></p> 