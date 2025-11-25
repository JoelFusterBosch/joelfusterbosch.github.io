# VirtualHosts
## Creació de les carpetes de daw1 i daw2
Primerament anem a crear les carpetes `daw1` i `daw2` amb el següent comand:

```bash
sudo mdir daw1.com && mdir daw2.com
```

<p align= "center">
    <img src="../imatges/VirtualHosts/Creació carpetes daw1 i daw2.png" alt="Creació de les carpetes de daw1 i daw2" width="600"/>
 </p>
<p align="center"><em>Creació de les carpetes de daw1 i daw2</em></p>      

Ara fem `ls -l` per a vore si s'han creat les carpetes correctament:

```bash
ls -l
```

<p align= "center">
    <img src="../imatges/VirtualHosts/Comprovació de la exstencia de les carpetes de daw1 i daw2.png" alt="Comprovació de la exstencia de les carpetes de daw1 i daw2" width="600"/>
 </p>
<p align="center"><em>Comprovació de la exstencia de les carpetes de daw1 i daw2</em></p>  

Ara anem a modificar els permisos de la carpeta `/var/www` per a que no ens done problemes de permisos a l'hora de voler entar a les webs, executarem el següent comand:
```bash
sudo chmod -R -755 /var/www
```
### Permisos en la carpeta /var/www

<p align= "center">
    <img src="../imatges/VirtualHosts/Modificació dels permisos de la carpeta var-www.png" alt="Modificació dels permisos de la carpeta /var/www" width="600"/>
 </p>
<p align="center"><em>Modificació dels permisos de la carpeta /var/www</em></p> 

## Creació dels fitxers de configuració i modificació dels hosts
### Creació dels fitxers de confguraciió
Ara anem a crear els 2 fitxers de confguració per a `daw1` i `daw2` respectivament:
<p align= "center">
    <img src="../imatges/VirtualHosts/Creació del fitxer de configuració de daw1.png" alt="Creació del fitxer de configuració de daw1" width="600"/>
 </p>
<p align="center"><em>Creació del fitxer de configuració de daw1</em></p> 
<p align= "center">
    <img src="../imatges/VirtualHosts/Creació del fitxer de configuració de daw2.png" alt="Creació del fitxer de configuració de daw2" width="600"/>
 </p>
<p align="center"><em>Creació del fitxer de configuració de daw2</em></p>
I cadascu tindra el seu contingut corresponent:
<p align= "center">
    <img src="../imatges/VirtualHosts/Contingut del fitxer de configuració de daw1.png" alt="Contingut del fitxer de configuració de daw1" width="600"/>
 </p>
<p align="center"><em>Contingut del fitxer de configuració de daw1</em></p>
<p align= "center">
    <img src="../imatges/VirtualHosts/Contingut del fitxer de configuració de daw2.png" alt="Contingut del fitxer de configuració de daw2" width="600"/>
 </p>
<p align="center"><em>Contingut del fitxer de configuració de daw2</em></p>

### Modificació en els hosts
#### Hosts en la màquina virtual
Ara amb els fitxers de configuració ja creats anem a modificar els `hosts` tant de la màquina virtual tant la local, primer anem a modificar la màquina virtual, anem a la ruta `etc`:
```bash
cd /etc
```
I li canviem els permisos:
```bash
sudo chmod -R -777 hosts
```
<p align= "center">
    <img src="../imatges/VirtualHosts/Canvi de permisos en el fitxer hosts.png" alt="Canvi de permisos en el fitxer hosts" width="600"/>
 </p>
<p align="center"><em>Canvi de permisos en el fitxer hosts</em></p>

Ara que ja li hem canviat els permisos anem a modificar el fitxer `hosts`:

```bash
sudo nano hosts
```
<p align= "center">
    <img src="../imatges/VirtualHosts/Hosts Linux.png" alt="Modificació dels hosts de la màquina virtual" width="600"/>
 </p>
<p align="center"><em>Modificació dels hosts de la màquina virtual</em></p>

Com veieu hem posat la ip (en NAT) i el alias en el que anem a escriure la URL

#### Hosts en la màquina local (Windows)
Ara en la màquina local, en el meu cas Windows anem a modificar el fitxer `hosts.txt`
!!! nota  
    En Windows podem trobar el fitxer `hosts.txt` en la ruta `C:\Windows\System32\drivers\etc`

<p align= "center">
    <img src="../imatges/VirtualHosts/Hosts Windows.png" alt="Modificació dels hosts de la màquina local" width="600"/>
 </p>
<p align="center"><em>Modificació dels hosts de la màquina local</em></p>    
Al igual que en la màquina virtual posem la ip, com es en nat 127.0.0.1 o localhost i el alias en el que anem a escriure en el navegador.  

## Habilitar els llocs web i accés
### Habilitar els llocs web
Per últim habilitem els llocs web wn la màquina virtual i reiniciem el servidor de Apache:
```bash
sudo a2ensite daw1.com.conf
```
<p align= "center">
    <img src="../imatges/VirtualHosts/Comand per a la habilitació de la web de daw1 i daw2.png" alt="Comand per a la habilitació de la web de daw1 i daw2" width="600"/>
 </p>
<p align="center"><em>Comand per a la habilitació de la web de daw1 i daw2</em></p>

```bash
sudo systemctl restart apache2
```
<p align= "center">
    <img src="../imatges/VirtualHosts/Reiniciar servidor Apache.png" alt="Comand per a reiniciar servidor Apache" width="600"/>
 </p>
<p align="center"><em>Comand per a reiniciar servidor Apache</em></p> 

### Accés als llocs web i comprovació
Per últiim anem al navegador i posem http://AliasDeLaPagina:NumPort i voreu el següent:

<p align= "center">
    <img src="../imatges/VirtualHosts/URL DAW1.png" alt="URL de la pàgina de DAW1" width="600"/>
 </p>
<p align="center"><em>URL de la pàgina de DAW1</em></p>  

<p align= "center">
    <img src="../imatges/VirtualHosts/Resultat web DAW1.png" alt="Contingut de la pàgina de DAW1" width="600"/>
 </p>
<p align="center"><em>Contingut de la pàgina de DAW1</em></p>  

<p align= "center">
    <img src="../imatges/VirtualHosts/URL DAW2.png" alt="URL de la pàgina de DAW2" width="600"/>
 </p>
<p align="center"><em>URL de la pàgina de DAW2</em></p>  
 
<p align= "center">
    <img src="../imatges/VirtualHosts/Resultat web DAW2.png" alt="Contingut de la pàgina de DAW2" width="600"/>
 </p>
<p align="center"><em>Contingut de la pàgina de DAW2</em></p>  