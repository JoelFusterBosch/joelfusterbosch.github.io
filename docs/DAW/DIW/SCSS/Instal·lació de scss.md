# Instal·lació de Saas
N'hi han moltes formes per a instal·lar Saas, el qual ens permetra usar scss, ací van unes quantes formes miitjançant sistemes operatius i altres formes:
## Windows
Per a instal·lar SCSS ha d'anar a la següent direcció url per a instal·lar `Ruby` i d'allí instal·lem scss:
https://rubyinstaller.org/downloads/

O també desde la terminal de Windows si disposeu de chocolatey:
```cmd
choco install sass
```

## Linux
En linux sols fa falta fer el següent comand en la terminal:
```bash
sudo apt install ruby-full
```
I ara des de Ruby fem el següent:
```bash
sudo gem install sass
```

## Mitjaçant Node
Primer instal·lem Node.js si no el teniu

Ara creem un nou projecte de Node.js:
```bash
npm init
```

Quan es cree instal·lem el paquet de scss de forma global:

```bash
npm install -g saas 
```

I per a vore si s'ha instal·lat correctament verifica el fitxer de `packages.json`:
```json
    {
      "dependencies": {
        "sass": "^1.97.2"
      }
    }
``` 