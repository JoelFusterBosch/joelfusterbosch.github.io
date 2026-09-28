## Creació de la primera màquina virtual
Primerament busquem `máquinas virtuales`
<p align= "center">
    <img src="../imatges/Configuració de VM/VM.png" alt="VM en el buscador" width="600"/>
</p>
<p align="center"><em>VM en el buscador</em></p> 

Ara en este apartat  apretem al botó `Crear` i se’ns obrira el següent menú:

<p align= "center">
    <img src="../imatges/Configuració de VM/Menú de la VM.png" alt="Menú de la VM" width="800"/>
</p>
<p align="center"><em>Menú de la VM</em></p> 

En este menú li apretem on diu `Máquina virtual`

<p align= "center">
    <img src="../imatges/Configuració de VM/Crear VM.png" alt="Servei necessari per a crear la VM" width="600"/>
</p>
<p align="center"><em>Servei necessari per a crear la VM</em></p> 

### Dades bàsiques
Ara ja dins procedim a crear la màquina virtual amb les següents dades:

- Subscripció: Azure Subscription o Azure for Students
- Grup de recursos: cloudazure1

<p align= "center">
    <img src="../imatges/Configuració de VM/Grup de recursos de la VM.png" alt="Grup de recursos de la VM" width="600"/>
</p>
<p align="center"><em>Grup de recursos de la VM</em></p> 

En esta captura posarem el nom de la màquina virtual, la regió, la imatge i arquitectura de la màquina virtual junt amb altres configuracions.

- Nom de la màquina virtual: maquina-salto-spain-central
- Regió: (Europe) `Spain Central`

!!! IMPORTANT
    La regió no està per defecte en `Spain Central`, és posa automàticament al entrar e eixir a l’hora de canviar la imatge o el tamany de la màquina virtual.

- Opcions de disponibilitat: `No se requiere redundancia de la infraestructura` 
- Tipus de seguretat: Estandar
- Imatge: `Ubuntu Server 24.04 LTS -x64 gen. 2`
- Arquitectura de la VM: `x64`
- Execució de Azure Spot amb descompte: `Desactivada`

<p align= "center">
    <img src="../imatges/Configuració de VM/Detalls de la VM.png" alt="Detalls de la VM" width="1200"/>
</p>
<p align="center"><em>Detalls de la VM</em></p> 

En esta captura posarem el nom d’usuari i la configuració de SSH:

- Nom d’usuari: cloudazure
- Orige de la clau pública SSH: `Buit`
- Tipus de clau SSH: `Formato Ed25519 SSH`
- Nom de parell de claus: ssh-azure-cloudazure 

<p align= "center">
    <img src="../imatges/Configuració de VM/Compte del administrador.png" alt="Nom del usuari de la VM i claus SSH" width="800"/>
</p>
<p align="center"><em>Nom del usuari de la VM i claus SSH</em></p>

Ací posarem la memòria RAM i processadors que tindrà la màquina virtual

- Tamany: `Standard_B1s – 1 vcpu, 1GiB de memòria`
- Habilitar hibernació: `No disponible`
- Tipus de autenticació: `Clave pública SSH`

<p align= "center">
    <img src="../imatges/Configuració de VM/Capacitat de la VM.png" alt="Capacitat i autenticació de la VM" width="800"/>
</p>
<p align="center"><em>Capacitat i autenticació de la VM</em></p>

### Discs
En este apartat podríem xifrar el disc en host, però no la podem activar amb la subscripció `Azure Subscription` o `Azure for Students`

<p align= "center">
    <img src="../imatges/Configuració de VM/Xifrat de la VM.png" alt="Xifrat de la VM" width="800"/>
</p>
<p align="center"><em>Xifrat de la VM</em></p>

Ara en el apartat del emmagatzemament posarem el espai disponible de la màquina virtual:

- Tamany del disc: 30 GiB
- Tipus del disc: `SSD estandar`
- Eliminar amb VM: `Activat`
- Administració de claus: `Clau administrada per la plataforma`
- Habilitar compatibilitat amb `Ultra Disks`: `No disponible amb  Azure Subscription o Azure for Students`

<p align= "center">
    <img src="../imatges/Configuració de VM/Disc del sistema operatiu.png" alt="Disc del sistema" width="600"/>
</p>
<p align="center"><em>Disc del sistema</em></p>

En este apartat no anem a habilitar discos per a la màquina virtual

<p align= "center">
    <img src="../imatges/Configuració de VM/Discs de dades de la VM.png" alt="Discs de dades de la VM" width="800"/>
</p>
<p align="center"><em>Discs de dades de la VM</em></p>

### Xarxes
En este apartat anem a assignar la xarxa de la màquina virtual amb les següents dades:

- Red virtual: vnet-cloudazure01
- Subred: `default`
- IP publica: `(nuevo) maquina-salto-spain-central-ip`
- Grup de seguretat de red de NIC: `Opciones avanzadas`
	- Configurar el grupo de Seguridad de red: `(nuevo) ssh-in-spain-central`
	- Eliminar la IP publica i NIC quan s’elimine la VM: `Habilitat` 

<p align= "center">
    <img src="../imatges/Configuració de VM/Interficie de xarxa per a la VM.png" alt="Interficie de xarxa per a la VM" width="700"/>
</p>
<p align="center"><em>Interficie de xarxa per a la VM</em></p>

En este apartat podem habilitar els ports necessaris, però en este cas no serà necessari.

<p align= "center">
    <img src="../imatges/Configuració de VM/Regles de ports d&apos;entrada.png" alt="Regles de ports d'entrada" width="600"/>
</p>
<p align="center"><em>Regles de ports d'entrada</em></p>

El mateix passa amb l’equilibri de carrega

<p align= "center">
    <img src="../imatges/Configuració de VM/Equilibri de carrega.png" alt="Equilibri de carrega" width="600"/>
</p>
<p align="center"><em>Equilibri de carrega</em></p>

### Administració
En el apartat de administració habilitem `Microsoft Defender for Cloud`

<p align= "center">
    <img src="../imatges/Configuració de VM/Administració de la VM.png" alt="Administració de la VM" width="600"/>
</p>
<p align="center"><em>Administració de la VM</em></p>

En la següent imatge no toquem res, deixem la opció de `Opciones de orquestación de revisiones` en `Valor predeterminado de la imagen`

<p align= "center">
    <img src="../imatges/Configuració de VM/Apagat, cpoia i actualitzacions.png" alt="Apagat, copia i actualitzacions" width="600"/>
</p>
<p align="center"><em>Apagat, copia i actualitzacions</em></p>

### Supervisió
En l’apartat de supervisió sols habilitem el diagnòstic d’arranc en l’opció `Habilitar amb el compte registrat`

<p align= "center">
    <img src="../imatges/Configuració de VM/Supervivisó de la VM.png" alt="Supervivisó de la VM" width="600"/>
</p>
<p align="center"><em>Supervivisó de la VM</em></p>

### Configuració avanzada
En este apartat no posem ninguna extensió

<p align= "center">
    <img src="../imatges/Configuració de VM/Extensions de la VM.png" alt="Extensions de la VM" width="800"/>
</p>
<p align="center"><em>Extensions de la VM</em></p>

Al igual amb les dades personals i cloud-init

<p align= "center">
    <img src="../imatges/Configuració de VM/Dades personalitzades i cloud-init.png" alt="Dades personalitzades i cloud-init" width="800"/>
</p>
<p align="center"><em>Dades personalitzades i cloud-init</em></p>

Igualment com en les dades del usuari

<p align= "center">
    <img src="../imatges/Configuració de VM/Dades del usuari i rendiment.png" alt="Dades del usuari i rendiment" width="600"/>
</p>
<p align="center"><em>Dades del usuari i rendiment</em></p>

I igualment com en el apartat dels hosts.

<p align= "center">
    <img src="./imatges/Configuració de VM/Host reserves de capacitat i grups amb ubicació per proximitat.png" alt="Host reserves de capacitat i grups amb ubicació per proximitat" width="700"/>
</p>
<p align="center"><em>Host reserves de capacitat i grups amb ubicació per proximitat</em></p>

### Etiquetes

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA02      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
    <img src="../imatges/Configuració de VM/Etiquetes.png" alt="Etiquetes per fer" width="800"/>
</p>
<p align= "center">
    <img src="../imatges/Configuració de VM/Etiquetes creades.png" alt="Etiquetes" width="800"/>
</p>
<p align="center"><em>Etiquetes</em></p>

### Revisar i crear
I per últim en el apartat de revisar i crear revisem si les dades són correctes.

<p align= "center">
    <img src="../imatges/Configuració de VM/Revisar i crear.png" alt="Revisar i crear" width="600"/>
</p>
<p align="center"><em>Revisar i crear</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/Termes.png" alt="Termes" width="600"/>
</p>
<p align="center"><em>Termes</em></p>

### Connexió amb ssh
Descarrega el fitxer que conté el ssh quan crees la màquina virtual, et servira per a accedir a la màquina virtual amb ssh

<p align= "center">
    <img src="../imatges/Configuració de VM/Clau ssh de Azure.png" alt="Clau ssh de Azure" width="900"/>
</p>
<p align="center"><em>Clau ssh de Azure</em></p>

Mirem la informació dins de la màquina virtual per a vore quina és la seua IP pública

<p align= "center">
    <img src="../imatges/Configuració de VM/Informació de la VM.png" alt="Informació de la VM" width="700"/>
</p>
<p align="center"><em>Informació de la VM</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/VM creades al moment.png" alt="VM creades al moment" width="800"/>
</p>
<p align="center"><em>VM creades al moment</em></p>

I per últim anem a la terminal i executem el següent comand:

```bash
ssh “nomusuariVM@IPVM -i ruta/al/fitxer/ssh-azure-cloudazure.pem”
```

<p align= "center">
    <img src="../imatges/Configuració de VM/Accés per ssh per la clau descarregada.png" alt="Accés per ssh per la clau descarregada" width="1500"/>
</p>
<p align="center"><em>Accés per ssh per la clau descarregada</em></p>

## Creació de la segona màquina virtual de forma resumida
Imatge del servidor i nom de la màquina virtual:

- Nom de la màquina virtual: Servicio-http-spain-central
- Regió: (Europe) `Spain Central`
- Opcions de disponibilitat: `No se requiere redundancia de la infraestructura` 
- Tipus de seguretat: Estandar
- Imatge: `Ubuntu Server 24.04 LTS -x64 gen. 2`
- Arquitectura de la VM: `x64`
- Execució de Azure Spot amb descompte: `Desactivada`

<p align= "center">
    <img src="../imatges/Configuració de VM/Dades bàsiques de la VM emplenades.png" alt="Dades bàsiques de la VM" width="900"/>
</p>
<p align="center"><em>Dades bàsiques de la VM</em></p>

RAM, cpu i nom del usuari:

- Tamany: `Standard_B1s – vcpu, 1GiB de memòria`
- Tipus d’autenticació: `Clave pública SSH`
- Nom d’usuari: cloudazure
- Orige de la clau publica SSH: `Usar la clave existente en Azure`

<p align= "center">
    <img src="../imatges/Configuració de VM/Tamany, i compte d&apos;administrador de la VM.png" alt="Tamany i compte d'administrador de la VM" width="800"/>
</p>
<p align="center"><em>Tamany i compte d'administrador de la VM</em></p>

Regles dels ports d’entrada

<p align= "center">
    <img src="../imatges/Configuració de VM/Regles de ports de entrada.png" alt="Regles de ports de entrada" width="900"/>
</p>
<p align="center"><em>Regles de ports de entrada</em></p>

Emmagatzematge:

- Tamany del disc del SO: 30GiB
- Tipus del disc del sistema operatiu: `SSD estandar`
- Elimina amb VM: `Habilitat`
- Administració de claus: `Clave administrada por la plataforma`
- Habilitar compatibilitat amb Ultra Disks: `Deshabilitada`

<p align= "center">
    <img src="../imatges/Configuració de VM/Disc del sistema operatiu.png" alt="Disc del sistema" width="900"/>
</p>
<p align="center"><em>Disc del sistema</em></p>

La xarxa tindrà el següent contingut:

- Xarxa virtual: vnet-cloudazure01
- Subxarxa: `default`
- IP publica: `(nuevo) Servicio-http-spain-central-ip`
- Grup de seguretat de red en NIC: `Opciones avanzadas`
	- Grup de seguretat de red: `http-https-in-spain-central`
	- Eliminar IP publica i NOC quan s’elimine la VM: `Habilitat`

<p align= "center">
    <img src="../imatges/Configuració de VM/Interfície de la xarxa.png" alt="Interfície de la xarxa" width="800"/>
</p>
<p align="center"><em>Interfície de la xarxa</em></p>

Equilibri de carrega

<p align= "center">
    <img src="../imatges/Configuració de VM/Equilibri de la carrega.png" alt="Equilibri de carrega" width="800"/>
</p>
<p align="center"><em>Equilibri de carrega</em></p>

Microsoft Defender

<p align= "center">
    <img src="../imatges/Configuració de VM/Microsoft Defender for Cloud.png" alt="Microsoft Defender for Cloud" width="900"/>
</p>
<p align="center"><em>Microsoft Defender for Cloud</em></p>

Apagat automàtic

<p align= "center">
    <img src="../imatges/Configuració de VM/Apagat, cpoia i actualitzacions.png" alt="Apagat, copia i actualitzacions" width="800"/>
</p>
<p align="center"><em>Apagat, copia i actualitzacions</em></p>

Alertes

<p align= "center">
    <img src="../imatges/Configuració de VM/Alertes, diagnòstic i estat.png" alt="Alertes, diagnòstic i estat" width="800"/>
</p>
<p align="center"><em>Alertes, diagnòstic i estat</em></p>

En l’apartat de dades personalitzades i cloud-init posarem el següent contingut per a tindre el servidor de nginx instal·lat en la màquina virtual:

<p align= "center">
    <img src="../imatges/Configuració de VM/Dades personals i cloud-init emplenats.png" alt="Dades personals i cloud-init" width="900"/>
</p>
<p align="center"><em>Dades personals i cloud-init</em></p>

Dades del usuari

<p align= "center">
    <img src="../imatges/Configuració de VM/Dades del usuari, Rendiment i Host.png" alt="Dades del usuari, rendiment i host" width="800"/>
</p>
<p align="center"><em>Dades del usuari, rendiment i host</em></p>

Etiquetes
<p align= "center">
    <img src="../imatges/Configuració de VM/Etiquetes.png" alt="Etiquetes de la VM" width="900"/>
</p>
<p align="center"><em>Etiquetes de la VM</em></p>

Revisar i crear
<p align= "center">
    <img src="../imatges/Configuració de VM/Preu de la VM.png" alt="Preu de la VM" width="800"/>
</p>
<p align="center"><em>Preu de la VM</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/Termes de la VM.png" alt="Termes de la VM" width="900"/>
</p>
<p align="center"><em>Termes de la VM</em></p>

Implementació completada

<p align= "center">
    <img src="../imatges/Configuració de VM/Implementació.png" alt="Implementació" width="700"/>
</p>
<p align="center"><em>Implementació</em></p>

Reserves de capacitat
<p align= "center">
    <img src="../imatges/Configuració de VM/Reserves de capacitat i grups amb ubicació de proximitat.png" alt="Reserves de capacitat i grups amb ubicació de proximitat" width="1000"/>
</p>
<p align="center"><em>Reserves de capacitat i grups amb ubicació de proximitat</em></p>

### Connexió a nginx
Ja quan hem acabat de configurar la segona màquina virtual farem el mateix que en la primera, mirar quina és la ip de la màquina virtual, que seria la que és veu en la imatge:
<p align= "center">
    <img src="../imatges/Configuració de VM/Menu VM.png" alt="Menú de la VM" width="800"/>
</p>
<p align="center"><em>Menú de la VM</em></p>

I ara ens dirigim al navegador i posem:

```bash
#IPVM = IP de la màquina virtal
http://IPVM
```

I vorem el següent:

<p align= "center">
    <img src="../imatges/Configuració de VM/Servidor nginx funcionant.png" alt="Servidor nginx funcionant" width="900"/>
</p>
<p align="center"><em>Servidor nginx funcionant</em></p>

### Connexió de la `maquina de salto` a la `maquina de Servicio`
En este apartat depenent del sistema operatiu farem uns comands o altres, en el meu cas com tinc Windows executeu estos 2 comands de baix per a activar el ssh si no el teniu activat:

Poweshell ssh :

```powershell
Set-Service -Name ssh-agent -StartupType Automatic
Start-Service ssh-agent
```

I després executeu el següent comand per a afegir el fitxer de azure:

<p align= "center">
    <img src="../imatges/Configuració de VM/Afegir el contingut de la VM en el ssh del sistema.png" alt="Afegir el contingut de la VM en el ssh del sistema" width="1200"/>
</p>
<p align="center"><em>Afegir el contingut de la VM en el ssh del sistema</em></p>

Ara entrem en a primera màquina virtual i ens dirigim a la carpeta `/etc/ssh`

<p align= "center">
    <img src="../imatges/Configuració de VM/Terminal de la VM de bot.png" alt="Accés i terminal de la VM de bot" width="800"/>
</p>
<p align="center"><em>Accés i terminal de la VM de bot</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/Contingut de la carpeta de ssh.png" alt="Contingut de la carpeta de ssh" width="1200"/>
</p>
<p align="center"><em>Contingut de la carpeta de ssh</em></p>

Ara el nostre objectiu serà accedir al fitxer anomenat `sshd_config` i buscar la següent línia i descomentar-la: 
<p align= "center">
    <img src="../imatges/Configuració de VM/Modificació de sshd_config.png" alt="Modificació de sshd_config" width="900"/>
</p>
<p align="center"><em>Modificació de sshd_config</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/AllowAgentFowarding.png" alt="Descomentar AllowAgentFowarding" width="300"/>
</p>
<p align="center"><em>Descomentar AllowAgentFowarding</em></p>

Ara reiniciem el servei de ssh i tractem d’accedir a la segona màquina virtual mitjançant la ip 10.0.0.5:  

<p align= "center">
    <img src="../imatges/Configuració de VM/Reiniciament del servei de ssh en la maquina de bot.png" alt="Reiniciament del servei de ssh en la maquina de bot" width="1500"/>
</p>
<p align="center"><em>Reiniciament del servei de ssh en la maquina de bot</em></p>

<p align= "center">
    <img src="../imatges/Configuració de VM/Conectant a la VM mitjançant la VM de bot.png" alt="Conectant a la VM mitjançant la VM de bot" width="800"/>
</p>
<p align="center"><em>Conectant a la VM mitjançant la VM de bot</em></p>

I vorem que podem accedir sense problemes.