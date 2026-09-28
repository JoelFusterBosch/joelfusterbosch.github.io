## Introducció
Abans de tocar res de Azure anem a fer un fork en el següent repositori de Github:

```bash
https://github.com/cefireazure2505/php-docs-hello-world 
```

I li apretem on diu `Fork` i s’obrira la següent pestanya:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Repositori php-docs-hello-world.png" alt="Contingut de la carpeta var" width="900"/>
</p>
<p align="center"><em>Contingut de la carpeta var</em></p>

Ara en esta pestanya podem canviar.li el nom del repositori, però no ho anem a fer i li apretem on diu `Create fork`.

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Fork del repositori.png" alt="Fork del repositori" width="700"/>
</p>
<p align="center"><em>Fork del repositori</em></p>

I veiem com tenim el repositori en el nostre perfil de github

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Repositori php-docs-hello-world.png" alt="Repositori php-docs-hello-world" width="800"/>
</p>
<p align="center"><em>Repositori php-docs-hello-world</em></p>

## Creació de la App Service
Ara en Azure posem el següent en el buscador i localitzem on diu `App Services`:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/App Services.png" alt="App Services en el buscador" width="900"/>
</p>
<p align="center"><em>App Services en el buscador</em></p>

Li apretem i s’obrirà el següent:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Menú del App Services.png" alt="Menú del App Services" width="600"/>
</p>
<p align="center"><em>Menú del App Services</em></p>

Ara li apretem on diu `Crear`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Botó Crear.png" alt="Botó per a crear el App Service" width="150"/>
</p>
<p align="center"><em>Botó per a crear el App Service</em></p>

I s’obrira un desplegable en unes quantes opcions, elegirem la opció de `Aplicació Web`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/App web.png" alt="Desplegable per a crear la app web" width="300"/>
</p>
<p align="center"><em>Desplegable per a crear la app web</em></p>

### Dades bàsiques
En l’apartat de dades bàsiques hem de posar el següent:
Detalls del projecte:

- Subscripció: Azure subscription o Azure for Students
 - Grup de recurs: cloudazure2

Detalls de la instància:

- Nom: cloudazure-webapp01
- Nom del host: `Habilitat`
- Publicar: `Código`
- Pila d’entorn en temps d’execució: `PHP-8.2`
- Sistema operatiu: `Linux`
- Regió: `Spain Central`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Detalls del projecte i de la instancia.png" alt="Detalls del projecte i de la instancia" width="800"/>
</p>
<p align="center"><em>Detalls del projecte i de la instancia</em></p>

Pla de preus:

- Pla de Linux (Spain Central): `(Nuevo) PHP-cloudazure`
- Pla de preus: `Bàsic B1 (Total de ACU: 100, 1,75 GB de memòria, 1vCPU)`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Pla de preus.png" alt="Pla de preus" width="900"/>
</p>
<p align="center"><em>Pla de preus</em></p>

Redundancia de la zona: `Deshabilitat per defecte`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Redundancia de la zona.png" alt="Redundancia de la zona" width="900"/>
</p>
<p align="center"><em>Redundancia de la zona</em></p>

### Base de dades
En l’apartat de la base de dades deixarem la opció deshabilitada:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Base de dades.png" alt="Apartat de base de dades" width="1200"/>
</p>
<p align="center"><em>Apartat de base de dades</em></p>

### Implementació
En l’apartat de implementació habilitarem la `implementació continua`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Configuració de implementació continua.png" alt="Configuració de implementació continua" width="1200"/>
</p>
<p align="center"><em>Configuració de implementació continua</em></p>

En este apartat posarem el nostre perfil de github junt al repositori que li havíem fet fork en anterioritat, per a això li apreteu al botó que diu `Añadir cuenta` i s’obrira la següent finestra diguent si vols que Azure es connecte a github, li apretes a autoritzar:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Sincronitzar el App Service al repositori.png" alt="Sincronitzar el App Service al repositori" width="400"/>
</p>
<p align="center"><em>Sincronitzar el App Service al repositori</em></p>

Quan tornes a Azure posaras el següent:

- Organització: `El teu usuari de GitHub`
- Repositori: `php-docs-hello-world` o el nom del repositori que li hages posat
- Rama: `master`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Informació del repositori i la branca.png" alt="Informació del repositori i la branca per al App Service" width="700"/>
</p>
<p align="center"><em>Informació del repositori i la branca per al App Service</em></p>

Configuració d’autenticació:

- Autenticació bàsica: Deshabilitar

### Xarxes
En l’apartat de xarxes posarem el següent:

- Habilitar l’accés públic: Activat
- Habilitar la integració de la red virtual: Desactivat

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Xarxes.png" alt="Apartat de xarxes" width="600"/>
</p>
<p align="center"><em>Apartat de xarxes</em></p>

### Supervisió i protecció
En el apartat de supervisió i protecció seleccionarem el següent:
Applicattion Insights:

- Habilitar Applicattion Insights: No

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Application Insights.png" alt="Application Insights" width="600"/>
</p>
<p align="center"><em>Application Insights</em></p>

Microsoft Defender for Cloud:

- Habilitar Defender per a App Service: `Deshabilitat`

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Microsoft Defender for Cloud.png" alt="Microsoft Defender for Cloud" width="600"/>
</p>
<p align="center"><em>Microsoft Defender for Cloud</em></p>

### Etiquetes
En l’apartat de etiquetes posarem el següent:

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA02      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Etiquetes.png" alt="Apartat de etiquetes" width="700"/>
</p>
<p align="center"><em>Apartat de etiquetes</em></p>

### Revisar i crear
En este apartat revisem si tot s’ha creat correctament, si es així li apretem on diu `Crear` i esperem uns minuts a que s’acabe d’implementar.

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Revisar i crear.png" alt="Apartat de revisar i crear" width="500"/>
</p>
<p align="center"><em>Apartat de revisar i crear</em></p>

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Implementació completada.png" alt="Implementació completada del App Services" width="500"/>
</p>
<p align="center"><em>Implementació completada del App Services</em></p>

### Implementació del repositori
Quan acabe d’implementar-se si encara esteu en la pantalla de implementació li apreteu on diu `Ir a recurso`:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Tornar al recurs.png" alt="Botó de tornar al recurs" width="300"/>
</p>
<p align="center"><em>Botó de tornar al recurs</em></p>

S’obrira el següent i li feu clic on diu `Dominio predeterminado`:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Informació del App Service.png" alt="Informació del App Service" width="900"/>
</p>
<p align="center"><em>Informació del App Service</em></p>

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Comprovació del funcionament.png" alt="Comprovació del funcionament" width="600"/>
</p>
<p align="center"><em>Comprovació del funcionament</em></p>

### Modificació del fitxer `index.php` en el repositori i resultat
Ara tornem al repositori de GitHub en el que havíem fet el el fork i modifiquem el fitxer `index.php` de açò:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Fitxer index.php des del repositori.png" alt="Fitxer index.php des del repositori" width="300"/>
</p>
<p align="center"><em>Fitxer index.php des del repositori</em></p>

A açò:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Alteració del fitxer index.php del repositori.png" alt="Alteració del fitxer index.php del repositori" width="300"/>
</p>
<p align="center"><em>Alteració del fitxer index.php del repositori</em></p>

Ara esperem uns minuts a que s’actualitze la informació i en el navegador apreteu `F5` o `Ctrl+R` i voreu que el contingut ha canviat per el que havíem posat en el fitxer `index.php` en el repositori de GitHub:

<p align= "center">
    <img src="../imatges/Configuració primer Azure App Service/Comprovació del funcionament després de modificar el fitxer index.php.png" alt="Comprovació del funcionament després de modificar el fitxer index.php" width="500"/>
</p>
<p align="center"><em>Comprovació del funcionament després de modificar el fitxer index.php</em></p>