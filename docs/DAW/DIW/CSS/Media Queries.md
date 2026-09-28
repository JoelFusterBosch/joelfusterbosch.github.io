## Que són les `Media Queries`?

Les `Media Queries` són el punt de tall per a que el contingut de la pàgina haja de redistribuir-se quan arribe un cert tamany de pantalla.

I com funciona?

Funciona paregut a un condicional `if`, sols has de posar a quina resolució/tamany de pantalla vols que és reorganitze el contingut, és pot fer les condicions de la següent forma:

- Amplada i alçada: Especifica la mida de la pantalla
    - `height`
    - `width`
    - `max-width`
    - `min-width`
- Resolució: Determina la densitat de pixels del dispositiu:
    - `resolution`
    - `min-resolution`
    - `max-resolution`
- Orientació: Identifica si el dispositiu és troba de forma horizontal o de forma vertical:
    - `orientation: portrait`
    - `orientation: landscape`

I ací els operadors de comparació.

- `<`: Menor que
- `<=`: Menor o igual que
- `>`: Major que
- `>=`: Major o igual que

Amb això ja comentat anem a vore un exemple de com ho podriem utilitzar:
```css
.classe{
    background-color: var(--color, black)
}

@media (width <= 100){
    .classe{
        --color: red;
    }
}

@media (width >= 1000){
    .classe{
        --color: green;
    }
}
```

Com veiem si la pantalla és menor o igual a 100 px aleshores el color de fons serà roig mentres que pel contari sí és més gran o igual a 1000 px aleshores el color de fons serà verd i si no compleix ningun dels 2 casos el color de fons serà negre.

En este cas sols hem canviat el color del fons, però és pot fer molt més, com he dit abans per a reestructurar la aplicació per a dispositius més menuts com podria ser un mòbil o ordinadors amb una pantalla menuda.