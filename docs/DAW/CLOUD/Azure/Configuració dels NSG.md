## Com crear un NSG de forma detallada
### Nom i grup del NSG
Primerament anem a la nostra pàgina principal de Azure i posem en el buscador `grupos de Seguridad de red`:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Grups de seguretat de la xarxa.png" alt="Grups de seguretat de la xarxa en el buscador" width="600"/>
</p>
<p align="center"><em>Grups de seguretat de la xarxa en el buscador</em></p> 

Quan li apretem vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Menu dels grups de seguretat de la xarxa.png" alt="Menú dels grups de seguretat de la xarxa" width="800"/>
</p>
<p align="center"><em>Menú dels grups de seguretat de la xarxa</em></p> 

Ara li apretem al botó que diu `Crear`:
<p align= "center">
    <img src="../imatges/Configuració dels NSG/Barra lateral per a la creació dels grups de seguretat.png" alt="Barra lateral per a la creació dels grups de seguretat" width="1200"/>
</p>
<p align="center"><em>Barra lateral per a la creació dels grups de seguretat</em></p> 

- Grup de recursos: cloudazure01
- Nom: http-https-in-spain-central

Regió: Spain Central

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Detalls del projecte i la instancia.png" alt="Grup de recursos i nom de la instancia.png" width="800"/>
</p>
<p align="center"><em>Grup de recursos i nom de la instancia</em></p> 

I li apretem on diu `Siguiente` per a accedir a posar les etiquetes.

### Etiquetes del NSG
En el apartat d’etiquetes sols en centrarem el següent:

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA02      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Etiquetes.png" alt="Etiquetes" width="800"/>
</p>
<p align="center"><em>Etiquetes</em></p> 

### Revisió del NSG
En este apartat és un resum dels camps que hem emplenat, sols fixat que et pose `Validación superada` abans de crear el NSG.

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Revisar i crear grup de seguretat.png" alt="Revisar i crear" width="800"/>
</p>
<p align="center"><em>Revisar i crear</em></p> 

I de allí li apretes on diu `Crear`.

## Configuració del NSG
Quan creem apretem on diu `Ir a recurso` o des del menu principal accedim on tenim la red de seguretat i vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Informació sobre el grup de seguretat.png" alt="Informació sobre el grup de seguretat" width="800"/>
</p>
<p align="center"><em>Informació sobre el grup de seguretat</em></p> 

Anem al menú de la part dreta on diu `Configuración` i vorem el següent desplegable:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Barra lateral per a la configuració dels grups de seguretat.png" alt="Barra lateral per a la configuració dels grups de seguretat" width="300"/>
</p>
<p align="center"><em>Barra lateral per a la configuració dels grups de seguretat</em></p>

I de allí anem on diu `Reglas de Seguridad de entrada` vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regles de entrada per als grups de seguretat.png" alt="Regles de entrada per als grups de seguretat per a http http i https" width="800"/>
</p>
<p align="center"><em>Regles de entrada per als grups de seguretat per a http http i https</em></p>

I se’ns obrira la següent finestra i tenim que omplir-la amb les següents dades:

- Origen: Any
- Intervals de ports des del origen: *
- Servei: HTTP
- Prioritat: 100
- Nom: AllowAnyHTTPInbound
- Descripció: Permet connexions des del port 80

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 1.1.png" alt="Regla d'entrada per a HTTP 1" width="600"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 1.2.png" alt="Regla d'entrada per a HTTP 2" width="600"/>
</p>
<p align="center"><em>Regla d'entrada per a HTTP</em></p>

Quan acabem li apretem al botó que diu `Agregar`.

En el segon és casi el mateix, sols cambiant el servei de HTTP a HTTPS i la prioritat més alta:

- Origen: Any
- Intervals de ports des del origen: *
- Servei: HTTPS
- Prioritat: 110
- Nom: AllowAnyHTTPSInbound
- Descripció: Permet connexions des del port 80

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 2.1.png" alt="Regla d'entrada per a HTTPS 1" width="600"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 2.2.png" alt="Regla d'entrada per a HTTPS 2" width="600"/>
</p>
<p align="center"><em>Regla d'entrada per a HTTPS</em></p>

I li apretem a `Agregar`.

Al final té que quedar de la següent forma:

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Resum dels grups de seguretat.png" alt="Resum dels grups de seguretat" width="800"/>
</p>
<p align="center"><em>Resum dels grups de seguretat</em></p>

## Creació i configuració del NSG de forma resumida
La creació de la segona NSG és el mateix, sols canviant el nom a `ssh-in-spain-central`

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Grup de recursos i nom de la instancia.png" alt="Grup de recursos i nom de la instancia" width="300"/>
</p>
<p align="center"><em>Grup de recursos i nom de la instancia</em></p> 

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Etiquetes del grup de seguretat.png" alt="Etiquetes del grup de seguretat" width="600"/>
</p>
<p align="center"><em>Etiquetes del grup de seguretat</em></p> 

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Revisar i crear.png" alt="Revisar i crear grup de seguretat" width="600"/>
</p>
<p align="center"><em>Revisar i crear grup de seguretat</em></p> 

I les regles de seguretat és el mateix, sols cambiant-li el nom i el servei:

- Origen: Any
- Intervals de ports des del origen: *
- Servei: SSH
- Prioritat: 100
- Nom: AllowSshInbound
- Descripció: Permet connexions des del port 80

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 3.1.png" alt="Regla de entrada per al SSH" width="600"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració dels NSG/Regla de entrada 3.2.png" alt="Regla de entrada per al SSH" width="600"/>
</p>
<p align="center"><em>Regla de entrada per al SSH</em></p> 

I per últim si vos apareix una senyal de advertència en el ssh no vos preocupeu, això no afectara al ús de la regla.

<p align= "center">
    <img src="../imatges/Configuració dels NSG/Resum de les regles de entrada.png" alt="Resum de les regles de entrada per al SSH" width="800"/>
</p>
<p align="center"><em>Resum de les regles de entrada per al SSH</em></p> 