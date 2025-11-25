# Què és MkDocs
MkDocs es una eina que converteix els fitxers `Markdown`(.md) en pàgines web estàtiques amb un disseny net — ideal per a apunts, documentació o blogs tècnics. 
## Com instal·lar-lo
Per a instal·lar `MkDocs` has de tindre `Python` instal·lat en el sistema, després en la terminal hauras d'executar el següent:

```bash
pip install mkdocs
```

Si vols vore si s'ha executat correctament pots executar el següent comando:

```bash
mkdocs --version
```

## Com crear nous projectes en MkDocs

```bash
mkdocs new nom-del-projecte
```
Quan l'executes creara la següent estructura de directoris i fitxers:
```css
mis-apuntes/
│
├── mkdocs.yml        ← configuració del lloc web
└── docs/
    └── index.md      ← la teua primera pàgina 
```
Ara en Github aneu al vostre perfil i creeu un nou repositori, exactament té que ser de la següent forma:
```bash
NomUsuari.github.io
```
**IMPORTANT**
No poseu ni README, ni .gitignore ni res més i és recomanable que el nom del repositori siga en `*MINUSCULES*
`.
Ara tornem a la terminal, perque tenim que vincular-lo al repositori de Github que acabem de crear, conseguint-ho de la següent forma en el vostre terminal:
```bash
git init
git remote add origin https://github.com/NomUsuari/NomUsuari.github.io.git
git add .
git commit -m "Primer commit"
git push -u origin main (o master, depén de com es diga)

```
I per a iniciar-lo usarem el següent comando
```bash
mkdocs gh-deploy
```
Si dona problemes podeu forçar-lo:
```bash
python -m mkdocs gh-deploy --force
```
### Opcional
#### Canviar el tema
Si voleu posar un tema podeu fer-lo de la següent forma:
```bash
pip install mkdocs-material
```
I en el `mkdocs.yml` agregueu el següent:

```yaml
site_name: Nom de la web
theme:
  name: material

```
Inclòs pots posar un botó per a canviar el tema de clar a fosc de la següent forma:
```yaml
site_name: Nom de la web
theme:
  name: material
  palette:
  - scheme: default # Tema de color per defecte
    toggle:
      icon: material/weather-night # icona per a identificar el fons
      name: Tema fosc # Nom del tema que vullgues posar
  - scheme: slate # Tema que pots canviar
    toggle:
      icon: material/weather-sunny
      name: Tema clar
```

I amb estes línies s'habilitara el botó per a canviar el tema
```yaml
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
```
  
#### Posar un botó per a copiar codi
Pots posar el botó de copiar amb el següent:
```yaml
features:
    - content.code.copy
    - palette.toggle
```
Servira per a poder copiar amb facilitat el codi