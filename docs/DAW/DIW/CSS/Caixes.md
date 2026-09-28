Quan parlem de les caixes o etiquetes `<div>` solen tractar de 4 atributs per a poder usar i manipular el contingut en CSS:

- Margin
- Border
- Padding
- Contingut

## Margin

Distància des del border fins l’element en què està contingut l’objecte.

=== "HTML"
    ```html
    <!--Exemple del marge-->
    <p class="exemple_margin">Exemple Margin</p>
    ```
=== "CSS"
    ```css
    .exemple_margin{
        margin: 25px 50px 75px 100px;
    }
    ```
=== "Resultat"
    <p class="exemple_margin">Exemple Margin</p>
    <style>
    .exemple_margin{
        margin: 25px 50px 75px 100px;
    }
    </style>

## Border
Línia que separa el margin del padding

=== "HTML"
    ```html
    <!--Exemple de la vora-->
    <p class="exemple_border">Exemple de la vora</p>
    ```
=== "CSS"
    ```css
    .exemple_border{
        border: 2px solid red;
    }
    ```
=== "Resultat"
    <p class="exemple_border">Exemple de la vora</p>
    <style>
    .exemple_border{
        border: 2px solid red;
    }
    </style>

També pots fer les vores arredonides per si vols arredonirles

=== "HTML"
    ```html
    <!--Exemple de la vora arredonida-->
    <p class="exemple_border_arredonit">Exemple de la vora arredonida</p>
    ```
=== "CSS"
    ```css
    .exemple_border_arredonit{
        border: 2px solid red;
        border-radius: 10px;
    }
    ```
=== "Resultat"
    <p class="exemple_border_arredonit">Exemple de la vora arredonida</p>
    <style>
    .exemple_border_arredonit{
        border: 2px solid red;
        border-radius: 10px;
    }
    </style>

## Padding
Distància entre el border i el contingut

=== "HTML"
    ```html
    <!--Exemple del padding-->
    <div class="exemple_padding">
        <p>Exemple Padding</p>
    </div>
    ```
=== "CSS"
    ```css
    /* Aci és poden fer de 2 formes: tot en un padding o diguent individualment la direcció del padding i la distancia */
    .exemple_padding {
        padding-top: 50px;
        padding-right: 30px;
        padding-bottom: 50px;
        padding-left: 80px;
    }

    .exemple_padding {
        padding: 25px 50px 75px 100px;
    }
    ```
=== "Resultat"
    <div class="exemple_padding">
        <p>Exemple Padding</p>
    </div>
    <style>
    .exemple_padding {
        background-color: #936767;
        padding-top: 50px;
        padding-right: 30px;
        padding-bottom: 50px;
        padding-left: 80px;
    }
    </style>

## Contingut
Aquest es el que pot variar com per exemple:

- imatges
- text
- colors