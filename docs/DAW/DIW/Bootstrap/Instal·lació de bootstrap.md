N'hi han 2 formes de usar `Bootstrap` les cuals són:

## Importar la llibreria de `bootstrap` en el propi fitxer html de la següent forma:
Per a aquesta "instal·lació" sols hem de importar les següents 2 linies:

```html
<!--El minim necessari per a que els efectes bàsics de Bootstrap apareguen-->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-sRIl4kxILFvY47J16cr9ZwB07vP4J8+LH7qKQnuqkuIAvNWLzeN8tE5YBujZqJLB" crossorigin="anonymous">

<!---->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js" integrity="sha384-FKyoEForCGlyvwx9Hj09JcYn3nv7wiPVlz7YYwJrWVcXK/BmnVDxM+D2scQbITxI" crossorigin="anonymous"></script>
```

## Instal·lar `bootstrap` des de `npm`:
Per a instal·lar bootstrap per npm hem de tindre un projecte en `Node.js`

```bash
npm init -i
```

I de alli instal·lem bootstrap per npm

```bash
npm install bootstrap@latest
```