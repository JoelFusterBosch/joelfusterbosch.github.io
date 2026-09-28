## Configuració del AzureFileStorage
### Creació d’un contenidor
Primerament anem al compte d’emmagatzematge que havíem creat fa unes quantes pràctiques anteriors

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Compte de emmagatzematge.png" alt="Compte de emmagatzematge a utilitzar" width="1200"/>
</p>
<p align="center"><em>Compte de emmagatzematge a utilitzar</em></p>

Quan entrem anem al menú de l’esquerra:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Barra de informació.png" alt="Barra lateral del compte de emmagatzematge" width="300"/>
</p>
<p align="center"><em>Barra lateral del compte de emmagatzematge</em></p>

I elegim l’opció `Contenedores`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Emmagatzematge de dades.png" alt="Emmagatzematge de dades" width="300"/>
</p>
<p align="center"><em>Emmagatzematge de dades</em></p>

Quan li apretem apareixerà el següent:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Menú dels contenidors.png" alt="Menú dels contenidors" width="900"/>
</p>
<p align="center"><em>Menú dels contenidors</em></p>

Ara dins crearem un contenidor en el botó que diu `Agregar contenedor`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Afegir contenidor.png" alt="Botó d'afegir contenidor" width="300"/>
</p>
<p align="center"><em>Botó d'afegir contenidor</em></p>

I s’obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Nou contenidor.png" alt="Formulari del nou contenidor" width="300"/>
</p>
<p align="center"><em>Formulari del nou contenidor</em></p>

Crearem un contenidor anomenat `comprimits`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Nom del nou contenidor.png" alt="Nom del nou contenidor" width="300"/>
</p>
<p align="center"><em>Nom del nou contenidor</em></p>

Li apretarem al botó que diu `Crear` i apareixerà el següent:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Informació sobre el contenidor.png" alt="Contenidor creat" width="800"/>
</p>
<p align="center"><em>Contenidor creat</em></p>

Ara crearem un altre contenidor anomenat `descomprimits` de la mateixa forma en la que hem creat el contenidor de `comprimits`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Nou cotenidor.png" alt="Nou contenidor anomenat descomprimits" width="300"/>
</p>
<p align="center"><em>Nou contenidor anomenat descomprimits</em></p>

Si s’ha fet bé, es deurien de vore els 2 contenidors creats:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Contenidors disponibles.png" alt="Contenidors creats" width="900"/>
</p>
<p align="center"><em>Contenidors creats</em></p>

### Informació general
Ja amb els contenidors creats anirem altra vegada al menú de l’esquerra i anirem on diu `Información general`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Barra de informació.png" alt="Barra de informació" width="300"/>
</p>
<p align="center"><em>Barra de informació</em></p>

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Menu del contenidor comprimits.png" alt="Menú del contenidor comprimits" width="900"/>
</p>
<p align="center"><em>Menú dels contenidor comprimits</em></p>

Ja allí, crearem en la nostra màquina un comprimit que s’anomenara `comprimits`

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Carpeta comprimits.png" alt="Carpeta comprimits" width="1200"/>
</p>
<p align="center"><em>Carpeta comprimits</em></p>

I la carregarem en `Información general` mitjançant l’opció de `Cargar`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Carregar.png" alt="Botó de Carregar" width="400"/>
</p>
<p align="center"><em>Botó de Carregar</em></p>

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Menú per a carregar el contenidor.png" alt="Menú per a carregar el contenidor" width="500"/>
</p>
<p align="center"><em>Menú per a carregar el contenidor</em></p>

Arrastrarem la carpeta comprimida i vorem que la agafa:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Carpeta comprimits llençada al contenidor.png" alt="Carpeta comprimits llençada al contenidor" width="500"/>
</p>
<p align="center"><em>Menú per a carregar el contenidor</em></p>

Ara li apretem on diu `Cargar` i vorem el següent: 

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Menú amb el blob afegit.png" alt="Menú amb el contenidor afegit" width="900"/>
</p>
<p align="center"><em>Menú amb el contenidor afegit</em></p>

Ara podríem anar al navegador per a vore com es veu..., però donara error de permisos, així que primerament haurem de generar el SAS per a que funcione, així que anem a ello. 

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Error de permisos.png" alt="Error de permisos" width="800"/>
</p>
<p align="center"><em>Error de permisos</em></p>

Tornem al apartat de `Información General` i vorem els següents apartats:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Pestanya informació general.png" alt="Pestanya informació general" width="400"/>
</p>
<p align="center"><em>Pestanya informació general</em></p>

Li apretem on diu `Generar SAS` i s’obrirà el següent:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Menú generar SAS.png" alt="Menú generar SAS en comprimits.zip" width="800"/>
</p>
<p align="center"><em>Menú generar SAS en comprimits.zip</em></p>

Plenem el formulari posant que la data d’inici siga este moment i que caduque el 23 de desembre a les 11:59:59

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Formulari del SAS.png" alt="Formulari del SAS emplenat" width="600"/>
</p>
<p align="center"><em>Formulari del SAS emplenat</em></p>

I li apretem al botó que diu `Aceptar`

Ara anem altra vegada al menú de l’esquerra i ens fixem en l’apartat `Seguridad y redes` en el subapartat `Claves de acceso`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Pestanya.png" alt="Menú general" width="300"/>
</p>
<p align="center"><em>Menú general</em></p>

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Pestanya Seguretat i xarxa.png" alt="Desplegable de seguretat i xarxa" width="300"/>
</p>
<p align="center"><em>Desplegable de seguretat i xarxa</em></p>

Quan li apretem s’obrirà el següent:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Claus d&apos;accés.png" alt="Claus d'accés" width="800"/>
</p>
<p align="center"><em>Claus d'accés</em></p>

Ara ens fixem en qualsevol de les 2 claus d’accés que conté i anem on diu `Cadena de conexión` li apretem on diu `Mostrar` per a que és mostre el contingut:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Valor de la clau.png" alt="Valor de la clau" width="600"/>
</p>
<p align="center"><em>Valor de la clau</em></p>

Ara copiarem la cadena de connexió, ens servira per al següent apartat en les variables d’entorn, les App Services.

## Configuració de l’App Service
### Variables d’entorn
Ens dirigim a l’AppService que vam crear fa unes quantes practiques abans i li apretem:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/App Service de l&apos;aplicació.png" alt="App Service de l'aplicació" width="1200"/>
</p>
<p align="center"><em>App Service de l'aplicació</em></p>

Ja dins d’ell anem al menú de l’esquerra:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Barra lateral.png" alt="Barra lateral del App Service" width="300"/>
</p>
<p align="center"><em>Barra lateral del App Service</em></p>

I anem on diu `Variables de entorno`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Configuració.png" alt="Desplegable de Configuració per a anar a Variables d'entorn" width="300"/>
</p>
<p align="center"><em>Barra lateral del App Service</em></p>

Ara dins de les variables d’entorn anem a assignar la següent variable d’entorn i en el valor peguem el que havíem copiat en les claus d’accés:

- Nom: `AZURE_STORAGE_CONNECTION_STRING`
- Valor: `Valor de les claus d’accés`

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/afegir o editar configuració de la aplicació.png" alt="Afegir variable d'entorn" width="700"/>
</p>
<p align="center"><em>Afegir variable d'entorn</em></p>

Li apretem a crear i es tindrà que vore de la següent forma:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Resultat d&apos;afegir la configuració.png" alt="Resultat d'afegir la configuració" width="900"/>
</p>
<p align="center"><em>Resultat d'afegir la configuració</em></p>

Si tot ha anat bé la podem vore junt amb les altres variables d’entorn creades anteriorment per a la base de dades:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Resum de les variables de entorn.png" alt="Resum de les variables de entorn" width="700"/>
</p>
<p align="center"><em>Resum de les variables de entorn</em></p>

### Creació del fitxer `storage_cloudazure.php` i pujar-lo al repositori
Per últim necessitarem el següent fitxer php que s’anomenara `storage_cloudazure.php`:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Codi de la aplicació.png" alt="Codi de la aplicació" width="700"/>
</p>
<p align="center"><em>Codi de la aplicació</em></p>

I el pujarem al repositori de Github que havíem creat anteriorment:

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Afegir canvis al github.png" alt="Afegir canvis al repositori" width="600"/>
</p>
<p align="center"><em>Afegir canvis al repositori</em></p>

<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Fer el commit.png" alt="Fer el commit" width="600"/>
</p>
<p align="center"><em>Fer el commit</em></p>

Per últim li donem a `Commit changes` i esperem uns moments a que s’actualitze i ja podem accedir als comprimits des de la App Service:

### Resultat final
<p align= "center">
    <img src="../imatges/Configuració i connexió de App Service en Azure Storage/Resultat final.png" alt="Resultat final" width="1000"/>
</p>
<p align="center"><em>Resultat final</em></p>