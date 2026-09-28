Com hem vist els atributs de CSS és poden fer de la següent forma:

```css
element {
    property: value;
}
```

I com a tal és poden fer d'elements selectors els següents:

## Etiquetes HTML

=== "HTML"
    ```html
    <!--Negreta de color blau-->
    <b>Hola</b>
    ```
=== "CSS"
    ```css
    b {
        color: blue;
    }
    ```
=== "Resultat"
    <b>Hola</b>
    <style>
        b {
            color: blue;
        }
    </style>

## Per classes (`.`)

=== "HTML"
    ```html
    <!--Exemple de classe-->
    <p class="classe_exemple">Hola</p>
    ```
=== "CSS"
    ```css
    .classe_exemple {
        font-size: 20px;
    }
    ```
=== "Resultat"
    <p class="classe_exemple">Hola</p>
    <style>
        .classe_exemple {
            font-size: 20px;
        }
    </style>

## Per identificador (`#`)

=== "HTML"
    ```html
    <!--Exemple d'identificador-->
    <p id="identificador_exemple">Hola</p>
    ```
=== "CSS"
    ```css
    #identificador_exemple {
        font-family: 'Inter', sans-serif;
        font-size: 15px;
        color: grey;
    }
    ```
=== "Resultat"
    <p id="identificador_exemple">Hola</p>
    <style>
        #identificador_exemple {
            font-family: 'Inter', sans-serif;
            font-size: 15px;
            color: grey;
        }
    </style>

## Descendents:

=== "HTML"
    ```html
    <!--Exemple d'identificador-->
    <p>Consulteu la pàgina del <a href="www.w3.org">W3C</a></p>
    ```
=== "CSS"
    ```css
    /* Només els enllaços que siguen descendents d’un element p seran de color roig. */
    p a { 
        color: red; 
    }
    ```
=== "Resultat"
    <p>Consulteu la pàgina del <a href="www.w3.org">W3C</a></p>
    <style>
        p a { 
            color: red; 
        }
    </style>

## Grups d'identificadors

=== "HTML"
    ```html
    <!--Exemple d'identificador-->
    <b>Negreta</b>
    <ins>Subrallat</ins>
    ```
=== "CSS"
    ```css
    /* Només els enllaços que siguen descendents d’un element p seran de color roig. */
    b, ins {
        font-family: Trebuchet, sans;
        color: olive;
        margin-left: 30px;
    }
    ```
=== "Resultat"
    <b>Negreta</b>
    <ins>Subrallat</ins>
    <style>
    b, ins {
        font-family: Trebuchet, sans;
        color: olive;
        margin-left: 30px;
    }
    </style>

## Selectors pseudo-classe

=== "HTML"
    ```html
    <!--Exemple d'identificador-->
    <a href="#">Enllaç</a>
    ```
=== "CSS"
    ```css
    a:hover { 
        text-decoration: none;
        background-color: red;
        color: white;
    }
    ```
=== "Resultat"
    <a href="#" class="ex">Enllaç</a>
    <style>
    .ex:hover { 
        text-decoration: none;
        background-color: red;
        color: white;
    }
    </style>

## Selectors pseudo-elements

=== "HTML"
    ```html
    <!--Exemple d'identificador-->
    <b>Primer paràgraf</b>
    <b>Segon paràgraf</b>
    ```
=== "CSS"
    ```css
    b::first-letter { 
        font-size: 200%;
    }
    ```
=== "Resultat"
    <b>Primer paràgraf</b>
    <b>Segon paràgraf</b>
    <style>
    b::first-letter { 
        font-size: 200%;
    }
    </style>

## Selector universal (`*`):

```css
*:hover { 
    color: red;
}
```