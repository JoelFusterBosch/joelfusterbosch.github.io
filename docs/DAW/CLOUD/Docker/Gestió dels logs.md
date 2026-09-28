## Crear el fitxer ultimsLogs.txt
Creem el fitxer `ultimsLogs.txt` amb:

```bash
nano ultimsLogs.txt
```

<p align= "center">
    <img src="../imatges/Gestió dels logs/Creació del fitxer ultimsLogs.txt.png" alt="Creació del fitxer ultimsLogs.txt" width="300"/>
</p>
<p align="center"><em>Creació del fitxer ultimsLogs.txt</em></p> 

## Consultar les últimes 5 linies de `mongo-express`
Per a vore les úlimes 5 linies dels logs de mongo-express hem de realizar el següent comand:

```bash
docker logs –tail 5 nom_del_contenidor
```

<p align= "center">
    <img src="../imatges/Gestió dels logs/Obtenció dels últims 5 logs.png" alt="Comand per a la obtenció dels últims 5 logs" width="300"/>
</p>
<p align="center"><em>Comand per a la obtenció dels últims 5 logs</em></p> 

## Consultar les últimes 8 linies de `mongodb`

El mateix que l’anterior, sols canvien les linies que volem vore i el nom del contenidor:

```bash
docker logs –tail 8 nom_del_contenidor
```

<p align= "center">
    <img src="../imatges/Gestió dels logs/Obtenció dels últims 8 logs.png" alt="Comand per a la obtenció dels últims 8 logs" width="300"/>
</p>
<p align="center"><em>Comand per a la obtenció dels últims 8 logs</em></p> 

## Enviar els logs al fitxer `ultimsLogs.txt`
Per a enviar els 2 logs al fitxer `ultimsLogs.txt` hem de realitzar el següent comand de la següent forma:

<p align= "center">
    <img src="../imatges/Gestió dels logs/Contingut del fitxer ultimsLogs.txt.png" alt="Contingut del fitxer ultimsLogs.txt" width="300"/>
</p>
<p align="center"><em>Contingut del fitxer ultimsLogs.txt</em></p> 