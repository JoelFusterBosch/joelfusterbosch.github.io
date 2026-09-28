## Com declarar les variables de CSS

Per a declarar variables en CSS, hem de usar `--` i després el nom de l'element, dos punts: `:` i per últim el valor, eiem-ho amb un exemple:

```css
element{
    --nom_variable: valor;
}
```

### Variable `:root`

La variable `:root` és la variable la qual estiga disponible en tot el fitxer HTML associat a eixe CSS, en poques paraules el selector `:root` fa referència a l'element arrel (`<html>`), veiem-ho millor amb un exemple:

```css
:root { 
  --main-bg-color: brown; 
}
```

!!! Important
    Els noms de les propietats personalitzades són sensibles a majúscules i minúscules, així `--my-color` i `--My-color` es consideren propietats diferents.

## Utilització de les variables

Per a usar les variables hem de usar `var(--'nom de la variable')`, mireu el següent exemple:

```css
:root{
    --color-principal: blue;
}

.classe { 
  propietat: var(--color-principal); 
}
```

També `var()` té la capacitat de rebre un segon parametre opcional el qual s'usara si el primer no existeix i s'usara com a valor de reserva, per exemple:

```css
:root{
    --color-principal: blue;
}
/*Ací m'he enganyat aposta per a fer que no agafe la variable "color-principal" 
aleshores el color en lloc de ser el de "color-principal" sera de color roig
*/
.classe { 
  propietat: var(--color-prlncipal, red); 
}
```
