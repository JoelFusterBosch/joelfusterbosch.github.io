# Creació de la màquina virtual e instal·lació del sistema
## Creació de la màquina virtual en VirtualBox

Creem la màquina virtual i li posem com a nom “DAW_nombreapellido”:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Creació de la màquina virtual.png" alt="Creació de la màquina virtual" width="500"/>
 </p>
 <p align="center"><em>Creació de la màquina virtual</em></p>
Ara li posem 2048MB de RAM i 1 nucli del nostre processador:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Memòria RAM i procesadors.png" alt="Memòria RAM i processadors de la màquina virtual" width="500"/>
 </p>
 <p align="center"><em>Memòria RAM i processadors</em></p>
Ara li donem 25GB de emmagatzematge o superior a la màquina virtual:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Enmagatzenament.png" alt="Emmagatzematge de la màquina virtual" width="500"/>
 </p>
 <p align="center"><em>Emmagatzematge de la màquina virtual</em></p>

### Red de la màquina virtual en Adaptador pont

!!! nota
    En aquesta pràctica s’utilitzarà **NAT** perquè permet accedir al servidor
    amb `localhost:PORT`.  
    L’Adaptador pont també funciona, però donarà una IP LAN diferent.

Ara canviem la red en lloc de NAT que ve per defecte, el canviem per Adaptador pont si voleu, en el cas d'esta pràctca s'usara en NAT.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Red Adaptador pont.png" alt="Red de la màquina virtual en adaptador pont" width="500"/>
 </p>
 <p align="center"><em>Red de la màquina virtual en adaptador pont</em></p>

### Red de la màquina virtual en NAT
Fem el mateix que abans per a canviar la connexió, però ens fixem on diu `Avançat`, li cliquem i li apretem on diu `Reenvió de ports`, i ens apareixerà el següent i posem el següent contingut amb esta icona: <p>
    <img src="../imatges/Instal·lació de Apache/Botó de posar port.png" alt="Botó per a posar el port en le red NAT" width="50"/>
 </p>
 
I per a entrar al Apache posem `localhost:8086` o `127.0.0.1:8086`, i en esta pràctica s'usara una máquina virtual configurada en NAT.
<p align= "center">
    <img src="../imatges/Instal·lació de Apache/Reenvio de ports.png" alt="Resultat del reenviament de ports" width="500"/>
 </p>
 <p align="center"><em>Resultat del reenviament de ports</em></p>

## Instal·lació de la màquina virtual Ubuntu Server 24.04 + Instruccions per a tindre la IP automàtica amb DHCP
### Llenguatge del idioma del sistema i del teclat
En este apartat posem tant l'idioma del sistema com la del teclat en `Espanyol`.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Idioma de la màquina.png" alt="Idioma de la màquina virtual" width="500"/>
 </p>
 <p align="center"><em>Idioma de la màquina virtual</em></p>

 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Idioma del teclat.png" alt="Idioma del teclat" width="500"/>
 </p>
 <p align="center"><em>Idioma del teclat</em></p>

### Sistema operatiu i “drivers”
En este apartat marquem l'opció de `Ubuntu Server` per a que s'instal·le per complet el servidor i posem que volem instal·lar els drivers de tercers.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Drivers.png" alt="Instal·lació dels drivers" width="500"/>
 </p>
 <p align="center"><em>Instal·lació dels drivers</em></p>

### Connexions de red
En l'apartat de connexió de red anem a configurar el DHCP perque s'assigne una IP de forma automàtica:  
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Pantalla de configuració de xarxa.png" alt="Pantalla de configuració de xarxa" width="500"/>
 </p>
 <p align="center"><em>Pantalla de configuració de xarxa</em></p>

Ens fixem en l'apartat de `enp0s3` i li fem un `intro` .
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/enp0s3.png" alt="enp0s3" width="500"/>
 </p>
 <p align="center"><em>enp0s3</em></p>

S'obrira un menú, ens fixem en l'opció de `Edit IPv4`, i li fem altre `intro`.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Menú enp0s3.png" alt="Menú enp0s3" width="500"/>
 </p>
 <p align="center"><em>Menú enp0s3</em></p>
I ací posem que ens pose la IP de forma automàtica en l'opció `Automàtic (DHCP)` i guardarem la configuració.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Configuració del DHCP.png" alt="Configuració del DHCP" width="500"/>
 </p>
 <p align="center"><em>Configuració del DHCP</em></p>
 
### Partició del disco (LVM)
En l'apartat de partició del disc marquem l'opció d'usar tot el disc de la màquina virtual i marquem l'opció per a poder dividir el disc amb ajuda de LVM.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/LVM.png" alt="Pantalla del LVM" width="600"/>
 </p>
 <p align="center"><em>Pantalla del LVM</em></p>

 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Resultats LVM.png" alt="Resultats de la pantalla del LVM" width="500"/>
 </p>
 <p align="center"><em>Resultats de la pantalla del LVM</em></p>

### Configuració del perfil del servidor
En l'apartat de configuració del perfil posarem el següent:
- Nom: nombreapellidos
- Nom del servidor: daw_nombreapellidos
- Nom del usuari: nombreapellidos
- Contrasenya: daw1234
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Configuració del usuari.png" alt="Configuració del usuari" width="500"/>
 </p>
 <p align="center"><em>Configuració del usuari</em></p>
 
### Configuració de SSH
En l'apartat de SSH podem prescindir d'ell degut a que no es necesari per a esta pràctica, però és recomanable instal·lar-lo degut a que és útil si vols utilitzar la terminal del servidor en la teua màquina real.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/OpenSSH.png" alt="Configuració del OpenSSH" width="500"/>
 </p>
 <p align="center"><em>Configuració del OpenSSH</em></p>
 
# Instal·lació de Apache, configuració i execució.
## Instal·lació i execució 
Ara instal·larem apache amb el siguiente command.
```bash
sudo apt update
sudo apt install apache2 -y
``` 
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Instal·lació de Apache.png" alt="Command d'instal·lació de Apache" width="700"/>
 </p>
 <p align="center"><em>Command d'instal·lació de Apache</em></p>

I posarem la IP de la màquina si estem en adaptador pont però en el cas en el que estem en NAT posarem `localhost:8086` o `127.0.0.1:8086` en el navegador per a vore la pàgina principal del servidor de Apache.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Pàgina per defecte de Apache.png" alt="Pàgina per defecte de Apache" width="500"/>
 </p>
 <p align="center"><em>Pàgina per defecte de Apache</em></p>

## Configuració d'una segona pantalla en Apache
Ara amb el servidor funcionant, crearem un fitxer anomenat `secondarypage.html` i li afegim el següent contingut:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Creació del fitxer secondarypage.html.png" alt="Creació del fitxer secondarypage.html" width="700"/>
 </p>
 <p align="center"><em>Creació del fitxer secondarypage.html</em></p>
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Contingut de secondarypage.html.png" alt="Contingut de secondarypage.html" width="800"/>
 </p>
 <p align="center"><em>Contingut de secondarypage.html</em></p> 

Després ens desplacem el fitxer a la següent ruta: `/var/www/html`
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Desplaçament de secondarypage.html.png" alt="Desplaçament del fitxer secondarypage.html" width="700"/>
 </p>
 <p align="center"><em>Desplaçament del fitxer secondarypage.html</em></p> 
I d'allí tornem al navegador i afegim el següent: `localhost:8086/secondarypage.html`
  <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Resultats de seconarypage.html.png" alt="Resultats de seconarypage.html" width="800"/>
 </p>
 <p align="center"><em>Resultats de seconarypage.html</em></p> 

## Configuració d'un nou fitxer per defecte
Ara ens desplacem a la arrel de la màquina virtual i anem a la carpeta “etc” on està el fitxer de configuració de Apache, més específicament en `etc/apache2/sites-available` i modificarem el fitxer `000-default.conf`.
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Redirecció a sites-available.png" alt="Redirecció a sites-available" width="700"/>
 </p>
 <p align="center"><em>Redirecció a sites-available</em></p> 
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Modificació del fitxer de configuració.png" alt="Command per a la modificació del fitxer de configuració" width="700"/>
 </p>
 <p align="center"><em>Command per a la modificació del fitxer de configuració</em></p> 
Dins del fitxer voras el següient:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Contingut del fitxer de configuració.png" alt="Contingut del fitxer de configuració" width="700"/>
 </p>
 <p align="center"><em>Contingut del fitxer de configuració</em></p> 

El que tenim que fer es canviar el  `DocumentRoot` de `var/www/html` a `var/www/daw`
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/DocumentRoot a daw.png" alt="DocumentRoot a la carpeta daw" width="700"/>
 </p>
 <p align="center"><em>DocumentRoot a la carpeta daw</em></p> 

Ara canviarem de directori, en lloc de `sites-available` ens desplaçarem a `mods-enabled`, més específicament a `/etc/apache2/mods-enabled`, i allí modificarem el fitxer anomenat `dir.conf` que conte el següent:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Contingut de dir.conf.png" alt="Contingut del fitxer dir.conf" width="700"/>
 </p>
 <p align="center"><em>Contingut del fitxer dir.conf</em></p>  
I el modificarem de la següent forma:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Modificació de dir.conf.png" alt="Modificació del fitxer dir.conf" width="700"/>
 </p>
 <p align="center"><em>Modificació del fitxer dir.conf</em></p>  

Com noteu sols hem afegit el nom del fitxer creat anteriorment, i sols això és necessari per a que aparega per defecte, i el posarem el primer perque és lo primer que veu i sera el que carregara.
Per a acabar desplacem/copiem el fitxer de `var/www/html` a `var/www/daw` i li modifiquem els permisos:
 <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Desplaçament de secondarypage.html.png" alt="Desplaçament del fitxer secondarypage.html" width="700"/>
 </p>
 <p align="center"><em>Desplaçament del fitxer secondarypage.html</em></p>   
   <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Permisos de secondarypage.html.png" alt="Permisos del fitxer secondarypage.html" width="700"/>
 </p>
 <p align="center"><em>Permisos del fitxer secondarypage.html</em></p> 

I per últim sols posem en el navegador `localhost:NumPuerto` i vorem els resultats.
  <p align= "center">
    <img src="../imatges/Instal·lació de Apache/Resultat de la pràctica.png" alt="Resultat de la pràctica" width="600"/>
 </p>
 <p align="center"><em>Resultat de la pràctica</em></p> 

#### comando apache para verificar sintaxis
apache2ctl configtest

##### Futura actualització
Explcació també en adaptador pont