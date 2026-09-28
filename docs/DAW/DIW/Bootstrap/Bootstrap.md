## Introducció i aclaració
Ara vaig a explicar com fer funcionar les propietats més bàsiques de bootsrap, però no vaig a fer-les totes perque n'hi han una muntanya de atributs per a decorar una web en bootstrap, el que si vaig a fer és posar un enllaç a la documentació de bootstrap per a que que ugau vore en detall:

https://getbootstrap.com/docs/5.3/getting-started/introduction/

Ja amb això explicat anem a vore com usar els atributs de bootstrap.

## Funcionament de Bootstrap
Ja amb bootstrap instal·lat anem a vore com usar bootstrap

A diferencia de `CSS` i `SCSS` no fa falta crear fitxers extra per a aplicar estils, tot és pot fer en el fitxer html corresponent, anem a vore un exemple:

Volem que aquest text canvie del color que ve per un blau, per exemple, en CSS és faria de la següent forma:

Per part de `CSS`:

=== "Codi"
    ```html
    <p class="color">Hola</p>
    <style>
        .color{
            color: blue;
        }
    </style>
    ```
=== "Resultat"
    <p class="color">Hola</p>
    <style>
        .color{
            color: blue;
        }
    </style>

Per part de Bootstrap:

=== "Codi"
    ```html
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-sRIl4kxILFvY47J16cr9ZwB07vP4J8+LH7qKQnuqkuIAvNWLzeN8tE5YBujZqJLB" crossorigin="anonymous">
    <p class="text-primary">Hola</p>
    ```
=== "Resultat"
    <p class="text-primary">Hola</p>
    <style>
        .text-primary{
            color: blue;
        }
    </style>

Com veiem bootstrap ocupa menys codi per a conseguir canviar el color del text, pot ser menys intuitiu a l'hora de les classes, però ens estalvia tindre més de 100 linies de codi sols per a CSS mentre que en bootstrap no afegeixes tantes.