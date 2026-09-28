## Habilita els mòduls neccesaris en el servidor HTTP de Apache.
Habilitem els mòduls proxy, proxy_http i proxy_ajp de Apache amb els següents comands:
```bash
sudo a2enmod proxy
```

```bash
sudo a2enmod proxy_http
```

```bash
sudo a2enmod proxy_ajp
```

<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Habilitació del proxy en Apache.png" alt="Habilitació del proxy en Apache" width="800"/>
 </p>
<p align="center"><em>Habilitació del proxy en Apache</em></p> 

Ara anem a configurar Apache com a proxy invers per a Tomcat, utilizant daw2.com:
Primerament obrim el fitxer de configuració de catadaw2 per a redirigir el tràfic a Tomcat.

I ara editem el fitxer de configuració i dins del bloc de `VirtualHost *:80`, i per a això anem a afegir una redirecció des de la ruta `/app` de daw2 a Tomcat, la ruta será `/examples/servlets/`. 

<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Configuració del fitxer de daw2.png" alt="Modificacions al fitxer de daw2 per a hailitar el proxy" width="800"/>
 </p>
<p align="center"><em>Modificacions al fitxer de daw2 per a hailitar el proxy</em></p> 
 
I per últim reiniciem el servei de Apache amb:
```bash
sudo systemctl restart apache2
``` 
 
## Configura Tomcat per a habilitar les solicituts de Apache.
Revisa el fitxer de configuració de Tomcat `server.xml` que es troba en `/opt/tomcat/conf/server.xml`, obrint-lo.
<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Fitxer de configuació del servidor.png" alt="Obrim el fitxer de server.xml" width="800"/>
 </p>
<p align="center"><em>Obrim el fitxer de server.xml</em></p>  

Troba el següent bloc i asegurat de que estiga activat, descomentant-lo:
```xml
<Connector 
protocol="AJP/1.3" 
address="::1" port="8009" redirectPort="8443" maxParameterCount="1000" 
/>
```

<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Bloc del fitxer de configuració comentat.png" alt="Codi comentat" width="800"/>
 </p>
<p align="center"><em>Codi comentat</em></p> 
 
<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Bloc del fitxer de configuració descomentat.png" alt="Codi descomentat" width="800"/>
 </p>
<p align="center"><em>Codi descomentat</em></p> 

Guarda els canvis i reinicia Tomcat amb `/opt/tomcat/shutdown.sh` i `/opt/tomcat/startup.sh`.
 
## Prova una aplicació en Tomcat.
Verifica que pots accedir a l'aplicació `servlet examples` de Tomcat, mitjançant el navegador i usant la URL `http://localhost:8080/examples/servlets/`. 

<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Tomcat.png" alt="Resultat del procés" width="800"/>
 </p>
<p align="center"><em>Resultat del procés</em></p> 
 
## Comprova la integració. 
Obri el teu navegador i accedeix a la URL `http://daw2/app`. Apache deu de proccesar esta solicitud i després reenviarla a Tomcat, mostrant la seua aplicació d'exemple de servlet de Tomcat. Apache proccesa les solicituts en el port 80 y redirigeix les solicituts dinàmiques a Tomcat en el port 8080.

<p align= "center">
    <img src="../../imatges/Proxy i proxy invers en Tomcat/Tomcat des de Apache.png" alt="Resultat del procés" width="800"/>
 </p>
<p align="center"><em>Resultat del procés</em></p> 