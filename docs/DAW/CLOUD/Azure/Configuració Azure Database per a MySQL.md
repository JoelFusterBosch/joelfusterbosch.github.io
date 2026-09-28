## Creació de servidors per a `Azure Database for MySQL`
Primerament busca `mysql` en la barra i agafa la opció `Servidores de Azure Database for MySQL`:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Busqueda de Azure Database for MySQL.png" alt="Busqueda de Azure Database for MySQL" width="600"/>
</p>
<p align="center"><em>Busqueda de Azure Database for MySQL</em></p>

Quan li apretes a `Servidores de Azure Database for MySQL` apareixera el següent:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Servidors de Azure Database for MySQL.png" alt="Menú de Azure Database for MySQL" width="700"/>
</p>
<p align="center"><em>Menú de Azure Database for MySQL</em></p>

Li apretarem on diu `Crear` i s’obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Serveis de Azure.png" alt="Serveis de Azure per a Azure Database for MySQL" width="600"/>
</p>
<p align="center"><em>Serveis de Azure per a Azure Database for MySQL</em></p>

Seleccionarem el `Servidor flexible` amb la opció `Creación avanzada`.

### Dades bàsiques
Posarem les següents dades en els següents apartats:

- Subscripció: Azure subscription o Azure for Students
- Grup de recurs: cloudazure2

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Grup de recursos de Azure.png" alt="Grup de recursos" width="900"/>
</p>
<p align="center"><em>Grup de recursos</em></p>

- Nom del servidor: mysql-cloudazure
- Regió: `Spain Central`
- Versió de MySQL: 8.0
- Tipus de carrega de treball: `Desarrollo/pruebas`
- Zona de disponibilitat: `Sin preferencias`

!!! Nota
    Zona de disponibilitat posada per defecte i deshabilitada per a la modificació amb la subscripció Azure subscription o Azure for Students

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Detalls del servidor.png" alt="Detalls del servidor" width="900"/>
</p>
<p align="center"><em>Detalls del servidor</em></p>

- Alta disponibilitat: Deshabilitat

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Alta disponibilitat.png" alt="Alta disponibilitat" width="900"/>
</p>
<p align="center"><em>Alta disponibilitat</em></p>

Autenticació:

- Mètode d’autenticació: `Autenticació de MySQL`
- Inici de sessió del administrador: cloudazure
- Contrasenya: La contrasenya que vullgues, que tinga entre `8 i 32 caracters`, `Majúscules i minúscules`, `números` i un `caràcter especial`(`@`,`$`,`%`,`&`... etc). 

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Autenticació.png" alt="Autenticació" width="700"/>
</p>
<p align="center"><em>Autenticació</em></p>

### Xarxes
En l’apartat de xarxes li diguem que el mètode de connectivitat siga d’accés públic i el port el que ve per defecte en mysql, el 3306:

- Mètode de connectivitat: `Acceso público (direcciones IP permitidas) y puntós de conexión privado`.
- Port de la base de dades: `3306`

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Conectividad de red.png" alt="Conectividad de la xarxa" width="700"/>
</p>
<p align="center"><em>Conectividad de la xarxa</em></p>

Habilitem el accés públic mitjançant Internet:

- Permetre l’accés públic a este recurs mitjançant Internet mitjançant una IP pública: `Habilitat`

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Accés público.png" alt="Accés públic" width="900"/>
</p>
<p align="center"><em>Accés públic</em></p>

I per últim ficarem les `regles de firewall` per a que puguen entrar des de la IP `0.0.0.0` fins a la IP `255.255.255.255`, li apretaràs on diu `Agregar 0.0.0.0 – 255.255.255.255`:

- Nom de la Firewall: `AllowAll`
- Direcció IP inicial: 0.0.0.0
- Direcció IP final: 255.255.255.255

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Firewall.png" alt="Regles del firewall" width="700"/>
</p>
<p align="center"><em>Regles del firewall</em></p>

### Configuració addicional
Per a la configuració addicional anem a deixar les opcions que venen per defecte, que son:

- `lower_case_table_names`: 1 (valor predeterminat)
- Clau de xifrat de dades: Clau administrada per el servei

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Parametres del servidor.png" alt="Configuració addicional" width="700"/>
</p>
<p align="center"><em>Configuració addicional</em></p>

### Etiquetes

| Etiquetes               | Noms                     | Valor     |
|:------------------------|:-------------------------|----------:|
| Etiqueta 1              | Proyecto                 | SA03      |
| Etiqueta 2              | version                  | 1.0       |

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Etiquetes.png" alt="Etiquetes" width="900"/>
</p>
<p align="center"><em>Etiquetes</em></p>

### Revisar i crear
Allí revisem si s’ha creat correctament, si s’ha creat apreta-li on diu `Crear` per a crear el MySQL

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Revisar i crear.png" alt="Revisar i crear" width="600"/>
</p>
<p align="center"><em>Revisar i crear</em></p>

### Implementació
#### Instal·lació del client de MySQL en Windows 
Instal·lem un servei de mysql mitjançant la pàgina oficial de mysql en Windows:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Instal·lador de MySQL.png" alt="Instal·lador de MySQL" width="600"/>
</p>
<p align="center"><em>Instal·lador de MySQL</em></p>

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Instal·lador de MySQL per a Windows.png" alt="Instal·lador de MySQL per a Windows" width="900"/>
</p>
<p align="center"><em>Instal·lador de MySQL per a Windows</em></p>

I quan estiga instal·lat fes la combinació `Windows+S` o busca `Editar variables de entorno`

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Variables del entorn del sistema.png" alt="Variables del entorn del sistema" width="400"/>
</p>
<p align="center"><em>Variables del entorn del sistema</em></p>

Quan estigues allí apreta on diu `variables de entorno` i voras el següent:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Variables de entorn de Windows.png" alt="Variables de entorn de Windows" width="500"/>
</p>
<p align="center"><em>Variables de entorn de Windows</em></p>

Li apretes 2 vegades a `Path` i s’obrira el següent:

<p align= "center">
    <img src="../imatges/Configuració Azure Database per a MySQL/Variables del entorn.png" alt="Variables del entorn" width="500"/>
</p>
<p align="center"><em>Variables del entorn</em></p>

Li apretes a `Nuevo` i copia el següent contingut:

```powershell
C:\Program Files\MySQL\MySQL Shell 8.0\bin\ 
```

I ja podries usar MySQL

#### Instal·lació del client de MySQL en Linux
Simplement executa en el terminal el següent comand i ja podràs usar el client de mysql:

```bash
sudo apt install mysql-client
```

#### Implementació
Amb el client de mysql ja instal·lat podem executar el següent comand i entrar a la base de dades:

```bash
mysql -h “NomBD”.mysql.database.azure.com -u “Nom del usuari” -p
```

Canviant les variables quedaria aixi:

```bash
mysql -h mysql-cloudazure.mysql.database.azure.com -u cloudazure -p
```