## Instal·lació del servei SFTP
Primerament actualitzem el sistema operatiu de la màquina virtual.

<p align= "center">
   <img src="../../imatges/sftp/Actualització del sistema.png" alt="Actualitzem el sistema" width="600"/>
</p>
<p align="center"><em>Actualitzem el sistema</em></p> 

Després instal·lem el servei neccesari per a proporcionar l'accés SFTP. El servei es openssh-server
 
<p align= "center">
   <img src="../../imatges/sftp/Instal·lació del servidor de openSSH.png" alt="Instal·lació del servidor de openSSH" width="600"/>
</p>
<p align="center"><em>Instal·lació del servidor de openSSH</em></p> 

Ara comprovem que el servei està correctament instal·lat i en execució amb el estat.
 
<p align= "center">
   <img src="../../imatges/sftp/Estat del ssh.png" alt="Estat del ssh" width="600"/>
</p>
<p align="center"><em>Estat del ssh</em></p> 

## Creació de l'usuari d'accés
Primerament crea un usuari anomenat `enric` amb la contrasenya `daw1234`.

<p align= "center">
   <img src="../../imatges/sftp/Creació del usuari enric.png" alt="Creació del usuari enric" width="600"/>
</p>
<p align="center"><em>Creació del usuari enric</em></p>

Ara crea el directori DEAW en la ruta: `/var/sftp/DEAW`.

```bash
sudo mkdir /var/sftp/DEAW
```
 
<p align= "center">
   <img src="../../imatges/sftp/Creació de la carpeta DEAW.png" alt="Creació de la carpeta DEAW" width="600"/>
</p>
<p align="center"><em>Creació de la carpeta DEAW</em></p>

Després assigna permisos a l'usuari en eixe directori:

```bash
sudo chown enric:enric /var/sftp/DEAW
```

<p align= "center">
   <img src="../../imatges/sftp/Modificació de permisos de la carpeta DEAW.png" alt="Modificació de permisos de la carpeta DEAW" width="600"/>
</p>
<p align="center"><em>Modificació de permisos de la carpeta DEAW</em></p>

## Configuració d'accés segur mitjançant SFTP
Ara configurare el servidor per a que l'usuari enric:

- Soles puga accedir mijançant SFTP.
- Estiga limitat al seu directori assignado.
- No puga accedir a la resta del sistema.

Per això n'hi ha que modificar la configuració de SSH. És troba en la carpeta `/etc/ssh/sshd_config`. 
I per a que complisca amb el demanat es deuria afegir les següents linies al fitxer de configuració:

```bash
Match User enric
ChrootDirectory /var/sftp
ForceCommand internal-sftp
AllowTcpForwarding no
X11Forwarding no
```

<p align= "center">
   <img src="../../imatges/sftp/Contingut del fitxer de configuració de ssh.png" alt="Modificació de permisos de la carpeta DEAW" width="600"/>
</p>
<p align="center"><em>Modificació de permisos de la carpeta DEAW</em></p>

Es important que el directori `sftp` se li donen permisos en `root`.
 
Per últim aplica els canvis i reinicia el servei corresponent.

<p align= "center">
   <img src="../../imatges/sftp/Reiniciar el servei de ssh.png" alt="Reiniciament del servei de ssh" width="600"/>
</p>
<p align="center"><em>Reiniciament del servei de ssh</em></p>

## Creació del fitxer de prova

1. Accedeix al sistema amb l'usuari enric.

   <p align= "center">
      <img src="../../imatges/sftp/Canvi al usuari enric.png" alt="Canvi al usuari enric" width="600"/>
   </p>
   <p align="center"><em>Canvi al usuari enric</em></p>

2. Crea el fitxer `DEAW.txt` dins del directori asignat.

   <p align= "center">
      <img src="../../imatges/sftp/Contingut del fitxer de configuració de ssh.png" alt="Contingut del fitxer de configuració de ssh" width="600"/>
   </p>
   <p align="center"><em>Contingut del fitxer de configuració de ssh</em></p>

3. Posa-li el contingut que vullgues

   <p align= "center">
      <img src="../../imatges/sftp/Contingut del fitxer DEAW.png" alt="Contingut del fitxer DEAW" width="600"/>
   </p>
   <p align="center"><em>Contingut del fitxer DEAW</em></p>
 
## Prova de connexió amb el client SFTP
Per últim anem a utilitzar un client SFTP per a conectar-mo'n al servidor. El port és el 22 per a SFTP. I en el servidor la IP que ens aparega en enp0s3 en la màquina virtual com per exemple FileZilla.
Per últim verifica que:

- Es possible accedir amb l'usuari creat.
- Es possible descarregar el fitxet DEAW.txt.
- No es possible accedir a alres directoris fora del assignat
 
<p align= "center">
   <img src="../../imatges/sftp/Contingut de la carpeta home desde FileZilla.png" alt="Contingut de la carpeta home desde FileZilla" width="600"/>
</p>
<p align="center"><em>Contingut de la carpeta home desde FileZilla</em></p>

<p align= "center">
   <img src="../../imatges/sftp/Descarregat el fitxer de DEAW.txt.png" alt="Descarregat el fitxer de DEAW.txt mitjançant el client de FileZilla" width="600"/>
</p>
<p align="center"><em>Descarregat el fitxer de DEAW.txt mitjançant el client de FileZilla</em></p>