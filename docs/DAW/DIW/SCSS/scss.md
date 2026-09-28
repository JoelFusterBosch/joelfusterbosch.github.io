## Com compilar els fitxers Saas?
Per a compilar fitxers Saas i observar com va cambiant dinàmicament mentres anem modificant el fitxer es consegueix de la següent forma:
```bash
sass --watch input.scss:output.css
``` 

Però si no vols vore com es va actualitzant pots realizar el següent comand què és molt paregut:
```bash
sass input.scss output.css
```
!!! important
    Sols va a funcionar si existeix tant el fitxer `input.scss` tant el fitxer `output.css`.

## Com usar Sass
### Variables
A diferència de `css`, `scss` pot usar variables paregut a com és fa en `PHP`:
```scss
$color: blue
/*El que fara sera aplicar el valor que li hem posat en la variable, 
en este cas el color del cos sera blau  */
body{
    background-color: $color
}
```
També pots posar variables dins de funcions de css, però aquestes funcionaran de forma local dins de la funció de css i no és poden dur fora d'aquestes, veiem un exemple:
```scss
/*Variable global */
$grandaria_del_text: 24px;

body{
    /*Variable local */
    $color: blue;
    background-color: $color
    font-size: $grandaria_del_text
}

footer{
    /*En este cas la variable grandaria seria correcta i és pot usar en altres funcions de css */
    font-size: $grandaria_del_text
    /*Mentres que està variable donaria ERROR degut a que s'havia implementata en la funció 
    'body' i sols pot ser usada en eixa funció*/
    background-color: $color
}
```

### Anidament
Una altra de les funcions de scss és que podem anidar funcions de css dins d'altres funcions de scss, veiem un exemple:
```scss
    nav {
        ul {
            list-style: none;
        }
        li {
            display: inline-block;
        }
        a {
            text-decoration: none;
        }
    }
```
Com podem vore tenm els elements `ul`, `li`, i `a` dins del element `nav`, i el que permetra és assignarli estils als elements `ul`, `li`, i `a` que estiguen dins del element `nav`.

### @import
Què és `@import`?

`@import` és una funció que permet importar variables d'un fitxer scss a un altre, veiem un exemple:

- Fitxer `_variables.scss`:
```scss
$color-primary: #3498db;
$font-size-heading: 24px;
```
- Fitxer `styles.scss`:
```scss
@import 'variables';

body {
  background-color: $color-primary;
  font-size: $font-size-heading;
}

a {
  color: $color-primary;
}
```
Com veiem s'han importat les varibles `color-primary` i `font-size-heading` desde els fitxers de `variables.scss` i és poden utilitzar en el fitxer `styles.scss`.

!!! important
    Notem que el fitxer amb les variables comença amb un guió baix (_). Aquesta assignació indica que el fitxer és destinat a ser importat i no ha de ser compilat independentment.

### @extend
Què és `@extend`?

`@extend` fa una funció similar a `@import`, però a diferencia de `@import`, però sense necessitat d'importa altres variables des d'un altre fitxer, el que fa és com una funció més de css per a reutilitzar codi, veiem-ho millor amb un exemple:
```scss
// Definició d'un estil que volem reutilitzar
.estil-compartit {
  font-weight: bold;
  color: blue;
}

// Utilitzant @extend per heretar l'estil
.element1 {
  @extend .estil-compartit;
  font-size: 16px;
}

.element2 {
  @extend .estil-compartit;
  text-decoration: underline;
}
```
Com podem vore la classe `estil-compartit` té un bloc de codi que és pot reutilitzar en altres funcions css mitjançant `@extend`, i quan exportem a css es voria de la següent forma:
```css
.estil-compartit, .element1, .element2 {
  font-weight: bold;
  color: blue;
}

.element1 {
  font-size: 16px;
}

.element2 {
  text-decoration: underline;
}
```

### Mapes de colors
Els mapes de colors son casos especials, els mapes de colors fan referència a l'ús de mapes per a gesstionar i organitzar els colors en una fulla d'estils.

Veiem un exemple complet de `mapes de colors`:
```scss
// Definició d'un mapa de colors
$colors: (
  primary: #3498db,
  secondary: #2ecc71,
  accent: #e74c3c,
);

// Utilització dels colors
body {
  background-color: map-get($colors, primary);
  color: map-get($colors, secondary);
}

.button {
  background-color: map-get($colors, accent);
  color: #fff;
}
```
Com veiem per a utilitzar els mapes usem la etiqueta `map-get('nom del mapa', 'nom de la variable de dins del mapa')`, i per a definir el mapa, en lloc d'usar claus (`{}`) s'usen parentesis (`()`)

### if
El `if` és una condició que si és cumpleix fa una cosa, i si no és compleix fa una altra cosa, ací teniu un exemple de com implementar-lo en scss i que eixira sí es compleix la codició o no.
```scss
$color: blue;
.element {
     @if $color == blue {
       background-color: $color;
     } @else {
       background-color: red;
     }
}
``` 
Resultat si es compleix:
```css
.element {
    background-color: blue;
}
```
Resultat si no es compleix:
```css
.element {
    background-color: red;
}
```
### while
While és un bucle que sí no es compleix una condició continuara executant-se fins que complisca la condició:
```scss
$i: 1;
@while $i < 4 {
     .element-#{$i} {
       width: 100px * $i;
     }
     $i: $i + 1;
}
```
Com veiem mentres la i siga menor a 4 la classe sel element anira fent-se més gran fins que no es reproduïsca més i així és voria exportata css:
```css
.element-1 {
    width: 100px;
}
.element-2 {
    width: 200px;
}
.element-3 {
    width: 300px;
}
``` 
### for 
For és el mateix que while, pero no es necesari posar `$i = $i+1` perque ja suma 1 quan executa una vegada el codi, veiem-ho mitllor en un exemple:
```scss
@for $i from 1 through 3 {
     .element-#{$i} {
       font-size: 10px * $i;
     }
}
```
Com veiem per cada vegada que anem en el for va creant-se una classe nova amb un tamany de lletra major, així es voria exportat en un css:
```css
.element-1 {
    font-size: 10px;
}
.element-2 {
    font-size: 20px;
}
.element-3 {
    font-size: 30px;
}
```
### each
El each és una llista d'elements que funciona com una especie de bucle, però sense ser-ho, assignara cada element de la llista que tinga a la funció assignada, veiem-ho amb un exemple.
```scss
$colors: red, green, blue;
@each $color in $colors {
     .element-#{$color} {
       background-color: $color;
     }
}
```
Com veiem per cada element de la llista va assignant el nom de la subclasse i el valor a la variable `background-color`.