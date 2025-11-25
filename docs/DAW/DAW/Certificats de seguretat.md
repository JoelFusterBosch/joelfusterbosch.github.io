# Certificats de seguretat
## Instal·lació i configuració de `ssl`
Habilitem el mòdul `mod_ssl` amb el següent comando:
```bash
sudo a2enmod mod_ssl
```
 <p align= "center">
    <img src="../imatges/Certificats de seguretat/Habilitació del mòdul ssl.png" alt="Habilitació del mòdul ssl" width="600"/>
 </p>
<p align="center"><em>Habilitació del mòdul ssl</em></p>  

Després reiniciem Apache amb 
```bash
sudo systemctl restart apache2
```
per a comprobar que el mòdulo `mod_ssl` funciona correctament i verifiquem que els fitxers `ssl.load` i `ssl.conf` estan en la carpeta `/etc/apache2/mods-enabled/` i creem la carpeta `/etc/apache2/certs/` i conprovem que s'ha creat correctament. 
 
 <p align= "center">
    <img src="../imatges/Certificats de seguretat/Fitxers de mods-enabled.png" alt="Fitxers de la carpeta mods-enabled" width="800"/>
 </p>
<p align="center"><em>Fitxers de la carpeta mods-enabled</em></p>  

 <p align= "center">
    <img src="../imatges/Certificats de seguretat/Fitxers de configuració de ssl.png" alt="Fitxers de configuració de ssl" width="100"/>
 </p>
<p align="center"><em>Fitxers de configuració de ssl</em></p>   

Veiem a vore que s'ha generat correctament
Generem un certificat SSL i una clau privada i completa les dades amb la següent informació:
```bash
Country Name (2 letter code) [AU]: ES
State or Province Name (full name) [Some-State]: Valencia
Locality Name (eg, city) []: Tavernes
Organization Name (eg, company) [Internet Widgits Pty Ltd]: IES
Organizational Unit Name (eg, section) []: DAW
Common Name (e.g. server FQDN or YOUR name) []: Your name
Email Address []: your_email@alu.edu.gva.es
```
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Comand de la llicencia.png" alt="Comand de la llicencia" width="800"/>
 </p>
<p align="center"><em>Comand de la llicencia</em></p>  

<p align= "center">
    <img src="../imatges/Certificats de seguretat/Execució del comand de llicencia.png" alt="Execució del comand de llicencia" width="700"/>
 </p>
<p align="center"><em>Execució del comand de llicencia</em></p>  
 
Verifiquem que el certificat i la clau és trobava en la carpeta `/etc/apache2/certs/` amb el comand `ls`
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Contingut de la carpeta certs.png" alt="Contingut de la carpeta propia 'certs'" width="600"/>
 </p>
    <p align="center"><em>Contingut de la carpeta propia 'certs'</em></p>
I si no estan dins podemredireccionar-los de la següent forma:
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Desplaçament del fitxer de clau i de crt.png" alt="Fitxers a ser redireccionats" width="600"/>
 </p>
<p align="center"><em>Fitxers a ser redireccionats</em></p> 

Reiniciem Apache per a comprovar que `mod_ssl` funciona correctament amb:
 ```bash
 sudo systemctl restart apache2
 ``` 
i si no ens dona error anem a configurar `mod_SSL` en VirtualHost de daw1.com.
Anem a configurar el VirtualHost per a que s'use el certificat SSL generat amb el següent contingut:

<p align= "center">
    <img src="../imatges/Certificats de seguretat/Contingut de daw1 amb ssl.png" alt="Contingut de daw1 amb ssl" width="600"/>
 </p>
<p align="center"><em>Contingut de daw1 amb ssl</em></p> 

I després reiniciem Apache amb: 
```bash
sudo systemctl restart apache2
```
per a aplicar els canvis i accedim a la pàgina mitjançant https://daw1.com:8443 i verifica que la connexió siga segura:
<p align= "center">
    <img src="../imatges/Certificats de seguretat/daw1 amb https.png" alt="Pàgina de DAW1 amb HTTPS" width="600"/>
 </p>
<p align="center"><em>Pàgina de DAW1 amb HTTPS</em></p> 

!!! nota
    Amb el candat amb signe de exclamació signica que no és del tot segura perque nosaltres mateixos hem firmat per a tindre https, i no l'ha firmat per una autoritat de certificació.

## Redireccionament de la pàgina de HTTP a HTTPS
Obrim el fitxer de configuració del lloc web daw1.com y creem altre bloc VirtualHost en el mateix archive, però en el port 80, amb el següent contingut:
```yaml
<VirtualHost *:80>
ServerName daw1.com
ServerAlias daw1.com www.daw1.com
Redirect / https://daw1.com
</VirtualHost>
```
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Contingut per a la redirecció.png" alt="Contingut per a la redirecció" width="600"/>
 </p>
<p align="center"><em>Contingut per a la redirecció</em></p>  

i ara reiniciem Apache amb
```bash
sudo systemctl restart apache2
```  
per a aplicar els canvis i accedim a http://daw1.com i verificar que es redirigeix automàticament a https://daw1.com.
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Prova de redrecció.png" alt="Provant la redirecció en HTTP" width="600"/>
 </p>
<p align="center"><em>Provant la redirecció en HTTP</em></p>  

<p align= "center">
    <img src="../imatges/Certificats de seguretat/daw1 amb https.png" alt="Prova de redirecció exitosa" width="600"/>
 </p>
<p align="center"><em>Prova de redirecció exitosa</em></p> 
  
## Instal·lació i configuració del mòdul `headers`
Habilitem el mòdul `headers` amb el següent comand:
```bash
sudo a2enmod headers
```
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Habilitació del mòdul headers.png" alt="Habilitació del mòdul headers" width="600"/>
 </p>
<p align="center"><em>Habilitació del mòdul headers</em></p> 

Ara obrim el fitxer de configuració del lloc daw1.com i afegim les següents línies dins del bloc <VirtualHost *:443> per a millorar la seguretat:
```yaml
Header always set X-Frame-Options "DENY"
Header always set X-Content-Type-Options "nosniff"
Header always set X-XSS-Protection "1; mode=block"
```
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Contingut de daw1 amb headers.png" alt="Contingut de daw1 amb headers" width="600"/>
 </p>
<p align="center"><em>Contingut de daw1 amb headers</em></p> 
 
i reiniciem una última vegada Apache per a aplicar els canvis
```bash
sudo systemctl restart apache2
```  
i provem el funcionamient: accedeix a https://daw1.com i usa les `ferramentes de desenvolupador del navegador`(pestaña Red o Network) per a comprovar que les capçaleres de seguretat s'han afegit correctament.
 
<p align= "center">
    <img src="../imatges/Certificats de seguretat/Resultats dels headers.png" alt="Resultats dels headers de la web" width="800"/>
 </p>
<p align="center"><em>Resultats dels headers de la web</em></p> 