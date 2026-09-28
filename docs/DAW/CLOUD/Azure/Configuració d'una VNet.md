## Creació de la primera red/xarxa virtual de forma detallada
Ens dirigim a la pàgina personal de Azure i posem en el buscador `redes virtuales` i vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Xarxes virtuals.png" alt="Xarxes virtuals en el buscador" width="500"/>
</p>
<p align="center"><em>Xarxes virtuals en el buscador</em></p> 

Quan li apretem a `Redes Virtuales` apareixerà el següent menú:
<p align= "center">
    <img src="../imatges/Configuració de una VNet/Menu de les xarxes virtuals.png" alt="Menú de les xarxes virtuals" width="700"/>
</p>
<p align="center"><em>Menú de les xarxes virtuals</em></p> 

Li apretem al botó que diu `Crear`, l’apartat de creació es divideix en els següents apartats:

Dades bàsiques -> Seguretat -> Direccions IP -> Etiquetes

### Dades bàsiques
<p align= "center">
    <img src="../imatges/Configuració de una VNet/Creació de la xarxa virtual.png" alt="Dades buides de les xarxes virtuals" width="1200"/>
</p>
<p align="center"><em>Dades buides de les xarxes virtuals</em></p> 

En este apartat posarem tant el nom del grup de la red/xarxa, grup de recursos i la regió, posarem les següents dades en els camps:

- Nom del grup de recursos: `cloudazure01`

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Nom del grup de recursos.png" alt="Nom del grup de recursos" width="400"/>
</p>
<p align="center"><em>Nom del grup de recursos</em></p> 

Per a crear el grup de recursos has d’apretar el botó de crear nou, posar el nom i acceptar.

- Nom del grup de la red/xarxa: vnet-cloudazure01
- Regió (en anglés): (Europe) Spain Central

Tindrà que quedar de la següent forma:
<p align= "center">
    <img src="../imatges/Configuració de una VNet/Creació de la xarxa virtual plenada.png" alt="Dades bàsiques emplenades" width="1200"/>
</p>
<p align="center"><em>Dades bàsiques emplenades</em></p> 

### Seguretat

En el apartat de seguretat no fa falta tocar res, que quede de la següent forma: 

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Seguretat.png" alt="Xifrat i Azure Bastion" width="600"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració de una VNet/Firewall i DDoS.png" alt="Firewall i DDoS" width="600"/>
</p>
<p align="center"><em>Apartat de seguretat</em></p> 

### Direccions IP 
En este apartat assignarem la red i la subred de la red/xarxa virtual, en la xarxa 1 posem la IP 10.0.0.0 amb mascara 24: 10.0.0.0/24 i creem una subred amb les següents característiques:

- Nom: default
- Interval de IP: 10.0.0.0 - 10.0.0.15
- Mascara: /28 (16 direccions)

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Direccions IP.png" alt="Direccions IP per defecte" width="600"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració de una VNet/Direccions IP disponibles.png" alt="Direccions IP cambiades" width="600"/>
</p>
<p align="center"><em>Apartat de direccions IP</em></p> 

### Etiquetes
En este apartat anem a posar etiquetes a la red/xarxa virtual, en este cas posarem 2 etiquetes amb els següents valors:

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA02      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
<img src="../imatges/Configuració de una VNet/Etiquetes fetes.png" alt="Etiquetes creades" width="300"/>
</p>
<p align="center"><em>Etiquetes creades</em></p> 

### Resumen
Al final tindria que quedar de la següent forma:

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Revisar i crear.png" alt="Apartat de revisar i crear" width="800"/>
</p>
<p align="center"><em>Apartat de revisar i crear</em></p> 

## Creació de la segona red/xarxa virtual de forma resumida
En la segona red/xarxa virtual farem exactament el mateix, sols canviant el nom de red/xarxa virtual de `vnet-cloudazure01` a `vnet-cloudazure02`

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Nom vnet.png" alt="Nom de la xarxa virtual" width="600"/>
</p>
<p align="center"><em>Nom de la xarxa virtual</em></p> 

També anem a canviar com tenim configurada les IP de la segona xarxa/red virtual, la única diferencia es la red de 10.0.0.0/24 passem a 10.0.10.0/24 i farem dos subreds amb les següents característiques:

| Subxarxa                | Nom                      |  Interval de direccions IP                  | Mascara                    |
|:------------------------|:-------------------------|:--------------------------------------------|---------------------------:|
| Subxarxa 1              | front                    | 10.0.10.0 – 10.0.10.15                      | /28 (16 direccions)        |
| Subxarxa 2              | back                     | 10.0.10.16 – 10.0.10.31                     | /28 (16 direccions)        |

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Xarxes front i bac.png" alt="Creacio de les xarxes front i bac" width="800"/>
</p>
<p align="center"><em>Creacio de les xarxes front i bac</em></p> 

Totes les altres configuracions seran les mateixes
## Resultats
Amb les reds/xarxes virtuals creades es tenen que veure de la següent forma:

- Red/xarxa virtual 1:

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Resultat vnet1.png" alt="Xarxa virtual 1" width="800"/>
</p>
<p align="center"><em>Xarxa virtual 1</em></p> 

- Red/xarxa virtual 2:

<p align= "center">
    <img src="../imatges/Configuració de una VNet/Resultat vnet2.png" alt="Xarxa virtual 2" width="800"/>
</p>
<p align="center"><em>Xarxa virtual 2</em></p> 