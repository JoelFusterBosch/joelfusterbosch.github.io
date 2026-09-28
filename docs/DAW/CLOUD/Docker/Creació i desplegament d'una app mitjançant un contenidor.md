Anem a crear un fitxer Dockerfile que  tindrà els següents paràmetres: 

- Especifica la versió de node (entra a Docker hub si s’escau)
- user i pass de mongo mitjançant variables d’entorn
- Creació del directori de l’aplicació dins del contenidor
- Còpia del directori local on esta l’app al directori del contenidor

Este deuria de ser el resultat:

<p align= "center">
    <img src="../imatges/Creació i desplegament de una app mitjançant un contenidor/Contingut del Dockerfile.png" alt="Contingut del Dockerfile" width="300"/>
</p>
<p align="center"><em>Contingut del Dockerfile</em></p> 

## Crea la imatge adequadament amb nom `my-app:1.0`

<p align= "center">
    <img src="../imatges/Creació i desplegament de una app mitjançant un contenidor/Construcció de l&apos;aplicació.png" alt="Construcció de l'aplicació" width="300"/>
</p>
<p align="center"><em>Construcció de l'aplicació</em></p> 

I per últim executem docker images:
<p align= "center">
    <img src="../imatges/Creació i desplegament de una app mitjançant un contenidor/Construcció de l&apos;aplicació.png" alt="Construcció de l'aplicació" width="300"/>
</p>
<p align="center"><em>Construcció de l'aplicació</em></p> 

## Demostra que llançant la nova imatge (contenidor) el servidor esta escoltant al port 3000

Primerament iniciem el contenidor amb:

```bash
docker start “nom o id del contenidor”
``` 

Si no esta iniciat i després fem un Docker logs per a comprovar que estiga funcionant el contenidor
<p align= "center">
    <img src="../imatges/Creació i desplegament de una app mitjançant un contenidor/Logs del contenidor de express.png" alt="Logs del contenidor de express" width="300"/>
</p>
<p align="center"><em>Logs del contenidor de express</em></p> 

### Accedeix al Shell del contenidor i llista amb un `ls -l` el contingut del directori de la app
Entrem dins del contenidor amb:
```bash
# (verifica amb el comand docker ps -a)
docker exec -it nom o id del contenidor
```  

i entrem on estiga la carpeta app, en el meu cas esta en:
```bash
/home/joel/Escritorio/app
```  
i amb:
```bash
cd /home/joel/Escritorio/app
```  
i executem el comand:
```bash
ls -l
```

<p align= "center">
    <img src="../imatges/Creació i desplegament de una app mitjançant un contenidor/Contingut de l&apos;aplicació.png" alt="Contingut de l'aplicació" width="300"/>
</p>
<p align="center"><em>Contingut de l'aplicació</em></p> 