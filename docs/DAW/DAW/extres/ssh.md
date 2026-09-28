Redirecció de ports:
- Nom: ssh o el que tu vullgues
- Protocol: TCP
- IP anftitrió: buit
- Port anfitrio: Recomanable 2222
- IP invitat 10.0.2.15
- Port invitat: 22
Instal·lar ssh en la màquina virtual:
```bash
sudo apt install openssh-server -y
```
Habilititar i activar si no està en execució
```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

En la maquina propietaaria executes ssh de la següent forma:
```bash
ssh usuario@IP_DE_LA_VM
```
Per exemple:
```bash
ssh -p 2222 joelfusterbosch@127.0.0.1
```

Si tens problemes en la màquina anfitriona, en el meu cas en Windows pots borrar les dades de la anterior maquina amb el següent comand:
```powershell
ssh-keygen -R 127.0.0.1
```