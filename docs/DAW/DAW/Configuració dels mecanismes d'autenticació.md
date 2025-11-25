# Configuració dels mecanismes d'autenticació
## Creació i configuració del fitxer .htpasswd
1.1 Crea el archive `.htpasswd` per a emmagatzemar les credencials d'accés.

Per a crear el fitxer `.htpasswd` neccesitem executar el següent comand:
`sudo htpasswd -c /etc/apache2/.htpasswd Nombre_usuario`
```bash
sudo htpasswd -c /etc/apache2/.htpasswd joelfusterbosch
```
<p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Creació del fitxer .htpasswd.png" alt="Creació del fitxer .htpasswd" width="600"/>
 </p>
<p align="center"><em>Creació del fitxer .htpasswd</em></p>  

I quan l'executem ens demanara una contrasenya, en la línia que posa `New password` i posarem la mateixa en `Re-type new password` per a confirmar-la, ara visualitzem el contingut del `.htpasswd` per a assegurar-mo'n de que s'ha generat correctament.
 <p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Modificació del fitxer .htpasswd.png" alt="Modificació del fitxer .htpasswd" width="600"/>
 </p>
<p align="center"><em>Modificació del fitxer .htpasswd</em></p>  
 
Veurem el nom del usuari que havíem posat i la contrasenya xifrada per seguretat
<p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Verificació del fitxer .htpasswd.png" alt="Verificació del fitxer .htpasswd" width="600"/>
 </p>
<p align="center"><em>Verificació del fitxer .htpasswd</em></p>  

## Configuració de la autenticació del fitxer de configuració (`daw1.com.conf`)
Ara editarem el fitxer `daw1.com.conf` per a afegir que quan l'executem en el navegador ens diga de posar l'usuari i la contrasenya, i ho conseguirem amb el següent:
```bash
<Directory /var/www/daw1.com/html>
    AuthType Basic
    AuthName "Restricted Content"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

Quedant de la següent forma:
 <p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Contingut del fitxer daw1.com.conf.png" alt="Verificació del fitxer .htpasswd" width="600"/>
 </p>
<p align="center"><em>Verificació del fitxer .htpasswd</em></p>  
I reiniciem el servei d'Apache per a aplicar els canvis.
 <p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Reiniciar el servidor de Apache.png" alt="Comand per a reiniciar el servidor de Apache" width="600"/>
 </p>
<p align="center"><em>Comand per a reiniciar el servidor de Apache</em></p>  

## Comprovació en el navegador
!!!nota 
    Al comprobar en `http://www.daw1.com` deu solicitar el nom d'usuari i la contrasenya abans de permetre l'accés.
 <p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Verificació en la web.png" alt="Verificació en la web" width="800"/>
 </p>
<p align="center"><em>Verificació en la web</em></p> 

I al posar el nom i la contrasenya deuria entrar a la pàgina sense ningun problema. 
<p align= "center">
    <img src="../imatges/Configuració dels mecanismes de autenticació/Resultat.png" alt="Resultat del procés" width="800"/>
 </p>
<p align="center"><em>Resultat del procés</em></p> 