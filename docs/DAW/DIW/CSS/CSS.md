## Aplicació d'estils
Per a que els efectes de CSS funcionen és pot fer de 2 maneres:

- En el propi fitxer HTML amb la etiqueta `<style>`:

=== "Codi"
    ```html
    <p class="color">Hola</p>
    <!--Aci començaria els estils de CSS-->
    <style>
        .color{
            color: red;
        }
    </style>
    ```
=== "Resultat"
    <p class="color">Hola</p>
    <style>
        .color{
            color: red;
        }
    </style>

- En un fitxer propi de CSS i que el HTML apunte a eixe fitxer.

=== "HTML"
    ```html
    <link rel="stylesheet" href="css/styles.css">
    <p class="color">Hola</p>
    ```
=== "CSS"
    ```css
    .color{
        color: red;
    }
    ```
=== "Resultat"
    <p class="color">Hola</p>
    <style>
        .color{
            color: red;
        }
    </style>
