# Aplicació de mòduls en Apache
1. Crea un document anomenat about.html en la ruta `/var/www/daw`.
Creem un fitxer en eixa carpeta amb el següent comand:
```bash
sudo nano about.html
```
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Creació del fitxer about.html.png" alt="Creació del fitxer about.html" width="600"/>
 </p>
 <p align="center"><em>Creació del fitxer about.html</em></p> 
Amb el següent contingut:
 
I si no et deixa editar-lo després pots realitzar:
`sudo chown “nom d'usuari” “nombre del fitxer amb la terminació (.txt, .html…,etc)”`
```bash
sudo chown joelfusterbosch about.html
```
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Canvi del propietari del fitxer.png" alt="Canvi del propietari del fitxer" width="600"/>
 </p>
 <p align="center"><em>Canvi del propietari del fitxer</em></p>  

2. Comprova si el mòdul `mod_rewrite` está habilitat
Usa el següent comand en la terminal per a verificar que `rewrite` esta activat:
```bash
apache2ctl -M | grep rewrite
```
 <p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Comprovació del mòdul rewrite.png" alt="Comprovació del mòdul rewrite" width="600"/>
 </p>
 <p align="center"><em>Comprovació del mòdul rewrite</em></p>  

3. Habilita el mòdul `mod_rewrite` (si no está activat).
Si no ho està, és tan simple com executar el següent comando:
```bash
sudo a2enmod rewrite
```
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Habilitació del mòdul rewrite.png" alt="Habilitació del mòdul rewrite" width="600"/>
 </p>
 <p align="center"><em>Habilitació del mòdul rewrite</em></p>  

I ara li fem cas al que diu el comand  realitzem:
```bash
sudo systemctl restart apache2
```
 <p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Reiniciar el servidor de apache.png" alt="Reiniciar el servidor de apache" width="600"/>
 </p>
 <p align="center"><em>Reiniciar el servidor de apache</em></p> 

4. Configura el fitxer `.htaccess` per a reescriuire les URLs
- Edita o crea un fitxer `.htaccess` en el directori del teu lloc web `/var/www/daw` amb:
```bash
sudo nano .htaccess.
``` 
 <p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Creacio-modificació del fitxer .htaccess.png" alt="Creacio/modificació del fitxer .htaccess" width="600"/>
 </p>
 <p align="center"><em>Creacio/modificació del fitxer .htaccess</em></p> 

- Afegeix les següents normes per a redirigir a una URL amigable:
```bash
RewriteEngine On
RewriteRule ^about-us$ about.html [L]
```
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Redirecció de url.png" alt="Redirecció de la URL" width="600"/>
 </p>
 <p align="center"><em>Redirecció de la url</em></p> 
 
5. Permet les sobrescritures de configuració en el fitxer de configuració del lloc
- Obri el fitxer de configuració de Apache per al teu lloc (normalment en la ruta `/etc/apache2/sites-available/000-default.conf`).
 <p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Fitxer 000-default.conf.png" alt="Fitxer 000-default.conf" width="600"/>
 </p>
 <p align="center"><em>Fitxer 000-default.conf</em></p> 
- Dins del bloc `<VirtualHost>`, asegúrat de que el directori permitisca l'ús de `.htaccess` afegint el següent:
```bash
<Directory /var/www/daw>
AllowOverride All
</Directory>
```
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/AllowOverride.png" alt="AllowOverride" width="600"/>
 </p>
 <p align="center"><em>AllowOverride</em></p> 

6. Reinicia Apache per a aplicar els canvis amb:
```bash
sudo systemctl restart apache2.
```
 <p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Reiniciar el servidor de apache.png" alt="Reiniciar el servidor de apache" width="600"/>
 </p>
 <p align="center"><em>Reiniciar el servidor de apache</em></p> 

7. Prova el funcionamient
Accedeix a la URL o http://localhost:8086/about-us i verifica que redirigeix correctament a `about.html`.
<p align= "center">
    <img src="../imatges/Aplicació de moduls en Apache/Resultat.png" alt="Fitxer 000-default.conf" width="600"/>
 </p>
 <p align="center"><em>Fitxer 000-default.conf</em></p> 
