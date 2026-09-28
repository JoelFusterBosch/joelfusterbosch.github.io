## Introducció
En esta pràctica vorem com podem usar una imatge de docker, en este cas de Redis, un magatzem de dades de codi obert, que funciona com una base de dades i caché.
## Instal·lar Docker
En el terminal de la vostra confiança d'un sistema operatiu Linux, més específic Ubuntu executarem el següent comand per a instal·lar Docker:
```bash
sudo apt install docker.io
```
## Descarrega de la imatge de Redis i creació dels contenidors
Ara ens dirigim a la pàgina de [Docker Hub](https://hub.docker.com/) i ens dirigim a la imatge de Redis en la oficial que posa `Docker Official Image`, allí mirem com es diu, en este cas es `7.2.11-alpine3.21`, amb eixa informació anem al terminal i executarm els següents comands per a tant tindre la imatge com per a fer els contenidors de Docker:

```bash
# El que fa això es descarregar la imatge de redis
docker pull redis:7.2.11-alpine3.21
```
Ara amb la imatge descarregada crearem els contenidors de Docker de la següent forma:

```bash
# docker run és el coman principal, el que fa es que si no tens una imatge te la descarrega i s'executa automàticament
# -it éss que el contenidor s'executa de forma iterativa
# -p és els ports que podem designarli al contenidor
# --name és el nom que podem posar al contenidor
docker run -it -p 5000:6379 --name redis1 redis:7.2.11-alpine3.21 redis-server
```
I creem la segona amb algunes diferències:
```bash
# Canviem el nom per a que no entre el conflicte, enlloc de "redis1" posem "redis2"
# Canviem el port pr a que no n'hi haja conflicte al voler accedir des del navegador
docker run -it -p 5005:6379 --name redis2 redis:7.2.11-alpine3.21 redis-server
```

### Comprovació dels contenidors

Per a comprovar que els contenidors estan, sols hem de fer el comand `docker ps` i es vora tota la informació dels contenidors, però si voleu la informació més detallada podeu usar `docker ps -a`.
<p align= "center">
    <img src="../imatges/Instàncies en Docker/Instàncies del docker.png" alt="Comprovació dels contenidors de Docker amb docker ps -a" width="1500"/>
</p>
<p align="center"><em>Comprovació dels contenidors de Docker amb docker ps -a</em></p> 