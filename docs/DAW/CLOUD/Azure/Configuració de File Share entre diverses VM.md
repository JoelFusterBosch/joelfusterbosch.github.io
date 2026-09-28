## Creació d’un compte d’emmagatzemament 
Primerament anem a posar el navegador `Cuenta de almacenamiento` i vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Compte d&apos;emmagatzematge.png" alt="Compte d'emmagatzematge en el buscador" width="600"/>
</p>
<p align="center"><em>Compte d'emmagatzematge en el buscador</em></p>

Ara li apretem al botó que diu `Crear` i posarem el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Botó Crear.png" alt="Botó per a crear el File Share" width="150"/>
</p>
<p align="center"><em>Botó per a crear el File Share</em></p>

### Dades bàsiques
Ara ja dins de la pàgina per a crear el compte d’emmagatzemament posarem les següents dades:

- Subscripció: Azure subscription o Azure for Students
- Grup de recursos: cloudazure1

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Grup de recursos.png" alt="Grup de recursos" width="600"/>
</p>
<p align="center"><em>Grup de recursos</em></p>

- Nom del compte de emmagatzemament: cloudazurestorage1
- Regió: `(Europe) Spain Central`
- Tipus de emmagatzematge preferit: `Azure Files`
- Rendiment: `Estandar`
- Facturació de recursos compartits de fitxers: `Recursos compartidos de paga por uso`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Detalls de la instancia.png" alt="Detalls de la instància" width="800"/>
</p>
<p align="center"><em>Detalls de la instancia</em></p>

I li apretem a següent que ens dura al apartat de `Avanzado`.

### Avançat
En l’apartat de avançat posarem les següents dades en els següents apartats:
En seguretat habilitem la transferència segura per a les operacions d’API REST i l’accés a la clau del compte, posarem la versió 1.2 del TLS i per al àmbit posarem des de qualsevol compte:

- Requerir transferència segura para las operacions de API de REST: `Habilitada`
- Permetre l’accés anònim en contenidors individuals: `Deshabilitada`
- Habilitar l’accés a la clau del compte de emmagatzematge: `Habilitada`
- El valor predeterminat es l’autorització de Microsoft Entra en Azure Portal: `Deshabilitada`
- Versió del TLS: `Versión 1.2`
- Àmbit permès per a les operacions de copia (versión preliminar): `Desde cualquier cuenta de almacenamiento`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Seguretat.png" alt="Apartat de seguretat" width="800"/>
</p>
<p align="center"><em>Apartat de seguretat</em></p>

En l’espai de noms jeràrquic i els protocols d’accés habilitarem l’espai de noms jerarquics i el sistema de fitxers de xarxa v3:

- Habilitar l’espai de noms jerarquics: `Habilitat`
- Habilitar SFTP: `Deshabilitat`
- Habilitar el sistema de fitxers de xarxa v3: `Habilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Espai de noms jeràrquic.png" alt="Espai de noms jeràrquic" width="800"/>
</p>
<p align="center"><em>Espai de noms jeràrquic</em></p>

En l’emmagatzematge de blobs el nivell d’accés el posarem en frecuent:

- Permetre recopilació entre inquilins: `Deshabilitat`
- Nivell d’accés: `Frecuente`

I en Azure Files ho deixem en Habilitat:

- Habilitar recursos compartits de fitxers grans: `Habilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Emmagatzematge de blobs.png" alt="Emmagatzematge de blobs" width="800"/>
</p>
<p align="center"><em>Emmagatzematge de blobs</em></p>

I li apretem a següent que ens dura al apartat de `Redes`.

### Xarxes
En accés public li donem a la opció `Deshabilitar`:
Accés a la red publica: `Deshabilitar`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Accés públic.png" alt="Accés públic" width="800"/>
</p>
<p align="center"><em>Accés públic</em></p>

En el punt de connexió privat li donem al botó `Agregar punto de conexión privado` i se’ns obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Punt de connexió privat.png" alt="Punt de connexió privat" width="900"/>
</p>
<p align="center"><em>Punt de connexió privat</em></p>

I l’emplenarem amb les següents dades:

- Subscripció: Azure subscription o Azure for Students
- Grup de recursos: cloudazure1
- Ubicació: `Spain Central`
- Nom: `pcp-spain-central`
- Subrecurs de emmagatzematge: `file`

Xarxes:

- Xarxa virtual: vnet-cloudazure01
- Subxarxa: `default`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Punt de connexió privat emplenat.png" alt="Punt de connexió privat emplenat" width="800"/>
</p>
<p align="center"><em>Punt de connexió privat emplenat</em></p>

I en la integració del DNS privat posarem el següent:

- Integrar amb la zona de DNS privada: `Si`
- Zona DNS privada: `(Nuevo) privatelink.blob.core.windows.net`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Integració del DNS privat.png" alt="Integració del DNS privat" width="1200"/>
</p>
<p align="center"><em>Integració del DNS privat</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Resum del blob.png" alt="Resum del blob" width="1000"/>
</p>
<p align="center"><em>Resum del blob</em></p>

I per últim en l’enrutament de xarxa posem la opció d’enrutament de la xarxa de Microsoft:

- Preferència d’enrutament: `Enrutamiento de red de Microsoft`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Enrutament de la xarxa.png" alt="Enrutament de la xarxa" width="1000"/>
</p>
<p align="center"><em>Enrutament de la xarxa</em></p>

I li apretem a següent que ens dura al apartat de `Protección de datos`.

### Protecció de dades
En l’apartat de recuperació deshabilitem la eliminació temporal per als blobs i per als contenidors:

- Habilitar la restauració a un moment donat per als contenidors: `Deshabilitat`
- Habilitar la eliminació temporal per als blobs: `Deshabiliitada`
- Habilitar l’eliminació temporal per als contenidors: `Deshabilitat`
- Habilitar l’eliminació temporal per als recursos compartits de fitxers: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Recuperació.png" alt="Apartat de recuperació" width="1200"/>
</p>
<p align="center"><em>Apartat de recuperació</em></p>

En seguiment ho deixem com està per defecte:

- Habilitar el control de versions per als blobs: `Deshabilitat`
- Habilitar la font de canvis del blob: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Seguiment.png" alt="Apartat de seguiment" width="1200"/>
</p>
<p align="center"><em>Apartat de seguiment</em></p>

I en el control d’accés també ho deixem com està per defecte: 

- Habilitar la compatibilitat amb la immutabilitat de nivell de versió: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Control d&apos;accés.png" alt="Control d'accés" width="1500"/>
</p>
<p align="center"><em>Control d'accés</em></p>

I li apretem a següent que ens dura al apartat de `Cifrado`.

### Xifrat

En el xifrat ho deixem com està per defecte:

- Tipus de xifrat: `Claves administrades por Microsoft (MMK)`
- Habilitar la compatibilitat amb claus administrades pel client: `Solo blobs y archivos`

Habiliitar xifrat d’infraestructura: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Xifrat.png" alt="Apartat de xifrat" width="700"/>
</p>
<p align="center"><em>Apartat de xifrat</em></p>

### Etiquetes
I en les etiquetes posarem el següent:

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA02      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Etiquetes.png" alt="Etiquetes" width="1200"/>
</p>
<p align="center"><em>Etiquetes</em></p>

I li apretem a següent que ens dura al apartat de `Revisar i crear`.

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Revisar i crear.png" alt="Revisar i crear" width="900"/>
</p>
<p align="center"><em>Revisar i crear</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Implementació del blob.png" alt="Implementació del blob" width="1200"/>
</p>
<p align="center"><em>Implementació del blob</em></p>

### Creació del FileShare
Ara entrem dins del compte d’emmagatzematge que havíem creat en anterioritat i quan li apretem s’obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Recursos compartits.png" alt="Barra lateral per als recursos compartits" width="300"/>
</p>
<p align="center"><em>Barra lateral per als recursos compartits</em></p>

Obrim on diu `Almacenamiento de datos` i li apretem on diu `Recursos compartidos de archivos`.
I dins d’això li apretem on diu `Recurso compartido de archivos`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Menú recursos compartits.png" alt="Menú de recursos compartits" width="300"/>
</p>
<p align="center"><em>Menú de recursos compartits</em></p>

I se’ns obrira el següent:

### Dades bàsiques
Dins del recurs compartit posarem les següents dades:

- Nom: `cloudazuresharedfiles01`
- Nivell d’accés: `Transacción optimizada`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Dades bàsiques del sharedfiles.png" alt="Dades bàsiques del sharedfiles" width="800"/>
</p>
<p align="center"><em>Dades bàsiques del sharedfiles</em></p>

### Copia de seguretat
En l’apartat de copia de seguretat la deixem deshabilitada.

- Habilitar copia de seguretat: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Copia de seguretat.png" alt="Copia de seguretat" width="1200"/>
</p>
<p align="center"><em>Copia de seguretat</em></p>

### Revisar i crear
Ací revisem que s’ha creat correctament i si s’ha creat li apretem a `Crear`.

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Revisr i crear el recurs compartit.png" alt="Revisar i crear el recurs compartit" width="700"/>
</p>
<p align="center"><em>Revisar i crear el recurs compartit</em></p>

## Creació del fitxer index.php i mostrar la ip en la web de la màquina de servici
### Creació del fitxer index.php

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/sharedfiles.png" alt="Sharedfiles a utilitzar" width="1200"/>
</p>
<p align="center"><em>Sharedfiles a utilitzar</em></p>

Ara amb el recurs compartit ja creat entrem dins d’ell i li apretem al botó que diu `Conectar`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Menú del compte de emmagatzematge.png" alt="Menú del sharedfile" width="700"/>
</p>
<p align="center"><em>Menú del sharedfile</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Botó conectar.png" alt="Botó per a conectar el sharedfile" width="300"/>
</p>
<p align="center"><em>Botó per a conectar el sharedfile</em></p>

I s’obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Menú per a conectar el sharedfiles.png" alt="Menú per a conectar el sharedfiles" width="600"/>
</p>
<p align="center"><em>Menú per a conectar el sharedfiles</em></p>

Ara li apretem a `Mostrar script` i modifiquem el punt de muntatge a `/var/www/html`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Punt de muntatje.png" alt="Punt de muntatje" width="600"/>
</p>
<p align="center"><em>Punt de muntatje</em></p>

I amb el punt de muntatge ja modificat copiem el script i accedim a la màquina virtual de salto i després a la màquina virtual de servei.

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Menu VM de salto.png" alt="Menú VM de salto" width="900"/>
</p>
<p align="center"><em>Menú VM de salto</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Accedir al blob per ssh.png" alt="Accedir a la VM per ssh" width="1200"/>
</p>
<p align="center"><em>Accedir a la VM per ssh</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Accés a la VM hhtp.png" alt="Accés a la VM http" width="1500"/>
</p>
<p align="center"><em>Accés a la VM http</em></p>

Ja dins de la màquina virtual de servei executem el script que havíem copiat del recurs compartit i deuria d’haver-se creat la carpeta `/var/www/html` dins de la carpeta de `media`, si tot ha anat bé executarem estos 2 comands per a canviar-li el propietari i els permisos:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Permisos.png" alt="Permisos" width="1500"/>
</p>
<p align="center"><em>Permisos</em></p>

Ara fem:
```bash
sudo apt update
```

E instal·larem `php-fpm`:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Actualitzar el sistema.png" alt="Actualitzar el sistema" width="1500"/>
</p>
<p align="center"><em>Actualitzar el sistema</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Instal·lació de php-fpm.png" alt="Instal·lació de php-fpm" width="1500"/>
</p>
<p align="center"><em>Instal·lació de php-fpm</em></p>

Quan ja estiga instal·lat crearem el fitxer index.php i posarem el següent contingut:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Creació del fitxer index.php.png" alt="Creació del fitxer index.php" width="1500"/>
</p>
<p align="center"><em>Creació del fitxer index.php</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Contingut de index.php.png" alt="Contingut de index.php" width="900"/>
</p>
<p align="center"><em>Contingut de index.php</em></p>

### Modificació del fitxer default
Ara anem a modificar el fitxer `default` que es troba en `/etc/nginx/sites-available/default` amb el següent contingut:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Creació del default.png" alt="Creació del fitxer default" width="1500"/>
</p>
<p align="center"><em>Creació del fitxer default</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Contingut del default sites-available.png" alt="Contingut del default sites-available" width="600"/>
</p>
<p align="center"><em>Contingut del default sites-available</em></p>

### Resultat en el navegador
Ara reiniciem el servici de nginx:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Reinici del servei de nginx.png" alt="Reiniciament del servei de nginx" width="1500"/>
</p>
<p align="center"><em>Reiniciament del servei de nginx</em></p>

I ens dirgim al navegador de la vostra confiança i posem la ip de la màquina virtual de servei i deuríem de vore el següent:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Resum VM http.png" alt="Resum VM http e IP de la VM" width="900"/>
</p>
<p align="center"><em>Resum VM http e IP de la VM</em></p>

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Resultat.png" alt="Resultat del procés" width="900"/>
</p>
<p align="center"><em>Resultat del procés</em></p>

## El mateix en la màquina de bot
Executa este comand:

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Comand per a montar.png" alt="Comand per a montar el sharedfile" width="1500"/>
</p>
<p align="center"><em>Comand per a montar el sharedfile</em></p>

I voras com apareix `index.php` en la carpeta `/media/var/html`

<p align= "center">
    <img src="../imatges/Configuració de File Share entre diverses VM/Contingut de la carpeta var.png" alt="Contingut de la carpeta var" width="900"/>
</p>
<p align="center"><em>Contingut de la carpeta var</em></p>