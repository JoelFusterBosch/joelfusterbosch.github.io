# HTML
HTML és un llenguatge de marques que dona forma a les pàgines web i és molt utilitzat al voltant del mon.
## Etiquetes HTML
### Etiquetes principals
#### html
`<html>`: Etiqueta princincipal dels documents html i que en un document HTML podem crear la següent estructura en VSCode amb `!` i `Tab`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
   <!--Contingut del HTML--> 
</body>
</html>
```

#### head
`<head>`:
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
```

#### body
`<body>`: Part principal del cos del HTML i on es posara la major part de les etiquetes.
```html
<body>
    Este és el contingut del HTML.
</body>
```
### Etiquetes de text
#### Capçaleres
`<h1>, <h2>, <h3> ...`: Estes etiquetes serveixen per a fer capçaleres en HTML.
=== "Codi"
    ```html
    <h1> Soc una capçalera.</h1>
    <h2>I jo soc una altra</h2>
    <h3>I jo soc una altra més</h3>
    ```
=== "Resultat"
    <h1> Soc una capçalera.</h1>
    <h2>I jo soc una altra</h2>
    <h3>I jo soc una altra més</h3>

#### br
`<br>`: Esta etiqueta permet fer un bot de linia.
=== "Codi"
    ```html
    Este és un text<br> separarat en 2 línies
    ```
=== "Resultat"
    Este és un text<br> separarat en 2 línies
#### p
`<p>`: Esta etiqueta permet escriure amb paragrafs, que també fa bots de linia.
=== "Codi"
    ```html
    <p>Este és un paragraf</p>
    <p>I este també és un paragraf</p>
    ```
=== "Resultat"
    <p>Este és un paragraf</p>
    <p>I este també és un paragraf</p>
#### b
`<b>`: Esta etiqueta permet posar el text en negreta.
=== "Codi"
    ```html
    <b>Este text està en negreta.</b>
    ```
=== "Resultat"
    <b>Este text està en negreta.</b>
#### i
`<i>`: Esta etiqueta posa el text en cursiva.

=== "Codi"
    ```html
    <i>Este text està en cursiva</i>
    ```
=== "Resultat"
    <i>Este text està en cursiva</i>

#### ins
`<ins>`: Esta etiqueta subralla el text.
=== "Codi"
    ```html
    <ins>Este text està en subrallat</ins>
    ```
=== "Resultat"
    <ins>Este text està subrallat</ins>

#### mark
`<mark>`: Esta etiqueta marca el text.
=== "Codi"
    ```html
    <mark>Este text està marcat</mark>
    ```

#### a
`<a>`: Esa etiqueta permet transformar els texts en links gracies a la etiqueta `href`.
=== "Codi"
    ```html
    <html>
    <!--Redirecció de Fitxers-->
    <a href="./altre_fitxer.html">Link del fitxer de referència</a>
    <!--Redirecció de pàgines web-->
    <a href="https://www.google.com/">Link de la pàgina web de referència</a>
    </html>
    ```
=== "Resultat"
    <html>
    <!--Redirecció de Fitxers-->
    <a href="./altre_fitxer.html">Link del fitxer de referència</a><br>
    <!--Redirecció de pàgines web-->
    <a href="https://www.google.com/">Link de la pàgina web de referència</a>
    </html>
### Etiquetes de formularis
#### form
Per crear i usar formularis en HTML necessitem usar la etiqueta `<form>`, i esta etiqueta també té altres propietats com per exemple:
##### fieldset
Aquesta etiqueta permet posar l'area definida per al formulari
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camp1">Camp1:</label>
                <input type="text" id="camp1" name="camp1"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camp1">Camp1:</label>
                <input type="text" id="camp1" name="camp1"><br>
            </fieldset>
        </form>
    </body>
##### legend

Aquesta etiqueta permet posar un titol al formulari:
=== "Codi"
    ```html
    <body>
        <form>
            <legend>Titol del formulari</legend>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <legend>Titol del formulari</legend>
        </form>
    </body>
##### label
Aquesta etiqueta permet posar un nom a un camp en el formulari 
=== "Codi"
    ```html
    <body>
        <form>
            <label for="camp">Nom del camp:</label>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <label for="camp">Nom del camp:</label>
        </form>
    </body>
##### input 
Aquesta etiqueta permet replenar del formulari, aquest últim té també unes quantes propietats que pots posar en el camp `type`:
 - text: El camp per a replenar en text
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camptext">Camp de text:</label>
                <input type="text" id="camptext" name="camptext"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camptext">Camp de text:</label>
                <input type="text" id="camptext" name="camptext"><br>
            </fieldset>
        </form>
    </body>
 - number: El camp per a replenar en numeros
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campnum">Camp de números:</label>
                <input type="number" id="campnum" name="campnum"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campnum">Camp de números:</label>
                <input type="number" id="campnum" name="campnum"><br>
            </fieldset>
        </form>
    </body>
 - tel: El camp per a replenar el numero de teleèfon valid
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camptel">Camp de telèfon:</label>
                <input type="tel" id="camptel" name="camptel"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camptel">Camp de telèfon:</label>
                <input type="tel" id="camptel" name="camptel"><br>
            </fieldset>
        </form>
    </body>
 - email: El camp per a replenar el numero de telèfon valid
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campemail">Camp de correu electrònic:</label>
                <input type="email" id="campemail" name="campemail"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campemail">Camp de correu electrònic:</label>
                <input type="email" id="campemail" name="campemail"><br>
            </fieldset>
        </form>
    </body>
 - date: El camp per a replenar amb una data format (dd/mm/aaaa)
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campdate">Data:</label>
                <input type="date" id="campdate" name="campdate"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="campdate">Data:</label>
                <input type="date" id="campdate" name="campdate"><br>
            </fieldset>
        </form>
    </body>
 - password: El camp per a replenar amb una contrasenya
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camppasswd">Data:</label>
                <input type="password" id="camppasswd" name="camppasswd"><br>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                <label for="camppasswd">Data:</label>
                <input type="password" id="camppasswd" name="camppasswd"><br>
            </fieldset>
        </form>
    </body>
 - ratio: Permet utilitzar la casella d'opció
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="radio" id="opcio1" name="opcions" value="opcio1"> <label for="opcio1">Opcio 1</label><br>
                    <input type="radio" id="opcio2" name="opcions" value="opcio2"> <label for="opcio2">Opcio 2</label><br>
                    <input type="radio" id="opcio3" name="opcions" value="opcio3"><label for="opcio3">Opcio 3</label>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="radio" id="opcio1" name="opcions" value="opcio1"> <label for="opcio1">Opcio 1</label><br>
                    <input type="radio" id="opcio2" name="opcions" value="opcio2"> <label for="opcio2">Opcio 2</label><br>
                    <input type="radio" id="opcio3" name="opcions" value="opcio3"> <label for="opcio3">Opcio 3</label>
            </fieldset>
        </form>
    </body>
 - checkbox: Permet utilitzar la casella de selecció multiple
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="checkbox" id="vehicle1" name="vehicle1" value="vehicle1">
                    <label for="vehicle1"> Vehicle1 </label><br>
                    <input type="checkbox" id="vehicle2" name="vehicle2" value="vehicle2">
                    <label for="vehicle2"> Vehicle2 </label><br>
                    <input type="checkbox" id="vehicle3" name="vehicle3" value="vehicle3">
                    <label for="vehicle3"> Vehicle3 </label>
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="checkbox" id="vehicle1" name="vehicle1" value="vehicle1">
                    <label for="vehicle1"> Vehicle1 </label><br>
                    <input type="checkbox" id="vehicle2" name="vehicle2" value="vehicle2">
                    <label for="vehicle2"> Vehicle2 </label><br>
                    <input type="checkbox" id="vehicle3" name="vehicle3" value="vehicle3">
                    <label for="vehicle3"> Vehicle3 </label>
            </fieldset>
        </form>
    </body>

 - button: Permet utilitzar botons
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="button" 
                    onclick="alert('Has fet clic al botó!')"
                    value="boto_clicat">
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="button" 
                    onclick="alert('Has fet clic al botó!')"
                    value="boto_clicat">
            </fieldset>
        </form>
    </body>
 - submit: Permet enviar la informació al servidor mitjançant un botó
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="submit" value="Enviar" action="enviar.js">
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="submit" value="Enviar" action="enviar.js">
            </fieldset>
        </form>
    </body>
 - reset: Permet eliminar la informació que hages posat en el formulari
=== "Codi"
    ```html
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="reset" value="Netejar">
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <fieldset>
                <legend>Formulari</legend>
                    <input type="reset" value="Netejar">
            </fieldset>
        </form>
    </body>
- selection: Camps per a seleccionar en un desplegable
=== "Codi"
    ```html
    <body>
        <form>
            <select id="desplegable" name="desplegable" required>
                <option value="opcio1">Opció 1</option>
                <option value="opcio2">Opció 1</option>
            </select>
        </form>
    </body>
    ```
=== "Resultat"
    <body>
        <form>
            <select id="desplegable" name="desplegable" required>
                <option value="opcio1">Opció 1</option>
                <option value="opcio2">Opció 1</option>
            </select>
        </form>
    </body>