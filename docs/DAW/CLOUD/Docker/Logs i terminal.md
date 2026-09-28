## Llançar els contenidos de Docker pel seu ID
Per a saber el id del contenidor fem “docker ps” o “docker ps -a”, i després per a iniciar-lo farem “docker start” i el id del contenidor, quedaria de la següent forma:
<p align= "center">
    <img src="../imatges/Logs i terminal/Instàncies i inici del docker.png" alt="Comprovació dels contenidors de Docker amb docker ps -a" width="300"/>
</p>
<p align="center"><em>Comprovació dels contenidors de Docker amb docker ps -a i iniciament dels contenidors de redis</em></p> 

## Canviar els noms dels contenidors per “redis-00” i “redis-05”
Fem “docker ps” o “docker ps -a” per a vore el nom dels contenidors, i quan els sabem usarem “docker rename” per a cambiar el nom dels contenidors:
<p align= "center">
    <img src="../imatges/Logs i terminal/Instàncies del docker.png" alt="Comprovació dels contenidors de Docker amb docker ps -a" width="300"/>
</p>
<p align="center"><em>Comprovació dels contenidors de Docker amb docker ps -a</em></p> 

## Visualitzar els logs de redis
Per a vore els “logs” en docker es tan simple com fer “docker logs nom_del_contenidor” per a vore tots els logs, ací es mostraran els logs dels 2 contenidors que tenim:

- Redis-00:

<p align= "center">
    <img src="../imatges/Logs i terminal/Logs del contenidor redis-00.png" alt="Logs del contenidor redis-00" width="300"/>
</p>
<p align="center"><em>Logs del contenidor redis-00</em></p> 

- Redis-05:

<p align= "center">
    <img src="../imatges/Logs i terminal/Logs del contenidor redis-05.png" alt="Logs del contenidor redis-05" width="300"/>
</p>
<p align="center"><em>Logs del contenidor redis-05</em></p> 

### Enviar els logs a un fitxer anomenat `logs_redis.txt`
Per a enviar els `logs` a un fitxer apart, podem usar:

```bash
docker logs nom_del_contenidor > nom_del_fitxer
```

<p align= "center">
    <img src="../imatges/Logs i terminal/Pasar el contingut dels logs al fitxer logs_redis.txt.png" alt="Comand per a dirigir els logs a un fitxer" width="300"/>
</p>
<p align="center"><em>Comand per a dirigir els logs a un fitxer</em></p> 

Ara iniciem els contenidors per a crear noves instancies al fitxer:
<p align= "center">
    <img src="../imatges/Logs i terminal/Iniciament dels contenidors.png" alt="Iniciament dels contenidors per a generar logs" width="300"/>
</p>
<p align="center"><em>Iniciament dels contenidors per a generar logs</em></p> 

Per últim obrim el fitxer i vorem el següent:
<p align= "center">
    <img src="../imatges/Logs i terminal/Contingut del fitxer logs_redis.txt.png" alt="Contingut del fitxer logs_redis.txt" width="300"/>
</p>
<p align="center"><em>Contingut del fitxer logs_redis.txt</em></p> 

## Executar el contenidor de `redis-05`
Per a executar el contenidor de Docker hem de utilitzar:

```bash
docker exec -it nom_del_contenidor sh o /bin/bash
```

<p align= "center">
    <img src="../imatges/Logs i terminal/Sistema operatiu del contenidor.png" alt="Sistema operatiu del contenidor" width="300"/>
</p>
<p align="center"><em>Sistema operatiu del contenidor</em></p> 

## Vore la informació del sistema
Per a vore la informació del sistema sols fa falta fer:

```bash
uname -a
```

## Fer un llistat en la carpeta `/etc`
Simplement hem de fer el comand:

```bash
ls -l
```

per a vore tot el llistat del directori /etc, i clar accedir a ella amb:

```bash
cd etc
```

<p align= "center">
    <img src="../imatges/Logs i terminal/Contingut del contenidor.png" alt="Contingut del contenidor de redis" width="300"/>
</p>
<p align="center"><em>Contingut del contenidor de redis</em></p> 