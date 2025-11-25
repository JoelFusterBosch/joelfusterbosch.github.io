# Formularis per a les aplicacions web
Per a fer els formularis en una aplicació web necessitem que és connecte a un backend que tinga funcions POST per a poder afegir dades a una base de dades, la qual també necessitem per a enmagatzemar les dades i no perdre-les quan parem e iniciem l'aplicació web, per a poder realitzar-lo el millor possible necessitem utilitzar les següents eines:

- HTML: Per a donar-li estructura a la aplicació web
- CSS: Per a donar-li estil a la aplicació web
- JavaScript: Per a donar-li funcionalitat i connectivitat a la aplicació web

## Formes
En este moment, n'hi han 2 formes de poder realitzar aquesta part, i són:
- Ocultant els camps mitjançant CSS
- Crear-los de forma modular amb JavaScript

### Forma 1: Ocultant els camps mitjançant CSS
#### Eines a utilitzar 
##### HTML
###### Formulari bàsic amb exemples
En HTML anem a donar-li la estructura necessaria per a que apareguen els formularis en la aplicació web, però per a fer-ho possible hem de connectar el fitxer HTML a CSS i amb JavaScript mitjançant les etiquetes `<script>` i `<style>` de la següent forma:
```html
<head>
    <link rel="stylesheet" href="style.css">
    <script src="formulari.js" defer></script>
</head>
```
N'hi ha més informació sobre els formularis en [l'apartat de HTML de DIW](https://joelfusterbosch.github.io/DAW/DIW/HTML/#form), però en que vos quedeu en com fer un formulari sobra.

Per a crear caixes usem l'etiqueta `div` principalment per a limitar en una caixa i donar facilitat a l'hora de donar-li estil al CSS i l'usarem per a ocultar els camps del desplegable que NO estiguen seleccionats.

- Exemple:

```html
<div id="Camp ocult" class="ocult">
    <label for="camp ocult">Camp ocult amb el element div:</label>
    <input type="text" id="camp ocult" name="camp ocult"><br>
</div>
```
##### CSS
En CSS anem a donar-li estil a l'aplicació web, però anem a usar-lo de moment per a ocultar els camps extra mentre no es seleccionen, en JavaScript activarem els que vullgam que teniem en html en la classe `ocult`.
```css
.ocult{
    display: none;
}
```
##### JavaScript
En JavaScript anem a donar-li funcionalitat al codi de html i a activar els camps ocults de css, però sols en els que ens interesse en eixe moment.
Farem una funció per a poder cridar-la des de HTML:
```javascript
function mostrarCampsPersona(){

}
```
Usarem `document` per a agafar els id dels html per a activar-los i desactivar-los a voluntat amb la classe `ocult` definida en el html.
```javascript
function mostrarCampsPersona(){
    document.getElementById('soci').classList.add('ocult');
}
```
Necessitarem saber quin de les opcións del dropdown s'ha elegit en el moment, definides en el html:
```html
<select id="classePersona" name="persona" onChange="mostrarCampsPersona()" required> <!-- Cridem a la funció de JavaScript en la funció onChange-->
    <option value="soci">Soci</option>
    <option value="administrador">Administrador</option>
</select><br>
```
Utilitzarem `document.getElementById()` per a agafar la classe de persona que teniem en el html i eliminem la classe `ocult` per a eliminar el `display:none` que haviem posat en el CSS:
```javascript
function mostrarCampsPersona(){
    const opcioSeleccionada = document.getElementById('classePersona').value; // La constant value ens permet saber el valor que hem selecionat en el desplegable
    // Amb el valor ja definit farem un condicional ja siga un "if" o un "switch" per a mostrar el contingut que correspon
    if(opcioSeleccionada === 'soci'){
        document.getElementById('soci').classList.remove('ocult'); // Li llevem la classe ocult que tenia el display: none que haviem posat en el CSS
    } else if(opcioSeleccionada === 'administrador'){
        document.getElementById('administrador').classList.remove('ocult') // Li llevem la classe ocult que tenia el display: none que haviem posat en el CSS
    }
} 
```
I el mateix per a recursos:
```javascript
function mostrarCampsRecurs(){
    document.getElementById('llibre').classList.add('ocult');
    document.getElementById('revista').classList.add('ocult');
    document.getElementById('pelicula').classList.add('ocult');

    const opcioSeleccionada = document.getElementById('classeRecurs').value;

    if(opcioSeleccionada === 'llibre'){
        document.getElementById('llibre').classList.remove('ocult');
    } else if(opcioSeleccionada === 'revista'){
        document.getElementById('revista').classList.remove('ocult')
    } else if(opcioSeleccionada === 'pelicula'){
        document.getElementById('pelicula').classList.remove('ocult')
    }
}
```
I per últim necessitem una altra funció que quan li apretem al botó de `reset` que teniem en el HTML que és deixe en la primera opció del desplegable i que actualitze per a que l'usuari no puga afegir dades d'altres al backend.
```javascript
window.addEventListener('DOMContentLoaded', () => {
    const formPersona = document.forms['persona']; //Agafa el formulari de Persones
    const formRecurs = document.forms['recurs']; //Agafa el formulari de Recursos

    // Quan li apretem al botó de reset s'actualitza el estat dels botons a "ocult"
    formPersona.addEventListener('reset', () => {
        document.getElementById('soci').classList.add('ocult');
        document.getElementById('administrador').classList.add('ocult');
        // Tornar a posar el "select" en la primera opció
        document.getElementById('classePersona').selectedIndex = 0;
    });

    // Quan li apretem al botó de reset s'actualitza el estat dels botons a "ocult"
    formRecurs.addEventListener('reset', () => {
        document.getElementById('llibre').classList.add('ocult');
        document.getElementById('revista').classList.add('ocult');
        document.getElementById('pelicula').classList.add('ocult');
        // Tornar a posar el "select" en la primera opció
        document.getElementById('classeRecurs').selectedIndex = 0;
    });
});
``` 
#### Resultat final
Al final els fitxers deurien de quedar de la següent forma:

##### Fitxer index.html
```html
<form name="persona" action="#" method="post">
    <fieldset>
        <legend>Persona</legend>
            <label for="nom">Nom:</label><br>
            <input type="text" id="nom" name="nom" required><br>
            <label for="dni">DNI:</label><br>
            <input type="text" id="dni" name="dni" required><br>
            <label for="persona">Tipus de persona:</label><br>
            <select id="classePersona" name="persona" onChange="mostrarCampsPersona()" required> <!-- Cridem a la funció de JavaScript en la funció onChange-->
                <option value="soci">Soci</option>
                <option value="administrador">Administrador</option>
            </select><br>
    
            <div id="soci" class="ocult">
                <label for="soci">Camp per a opció soci:</label>
                <input type="text" id="soci" name="soci"><br>
            </div>
            <div id="administrador" class="ocult">
                <label for="administrador">Tipus de administrador:</label><br>
                <input type="radio" id="ajudant" name="tipus_admin" value="ajudant" required> <label for="ajudant">Ajudant</label><br>
                <input type="radio" id="admin" name="tipus_admin" value="admin" required> <label for="admin">Administrador</label><br> 
            </div>
            <input type="submit" value="Enviar">
            <input type="reset" value="Reset">
    </fieldset>
</form>
```

##### Fitxer styles.css
```css
.ocult{
    display: none;
}
```

##### Fitxer form.js
```javascript
function mostrarCampsPersona(){
    document.getElementById('soci').classList.add('ocult');
    document.getElementById('administrador').classList.add('ocult');

    const opcioSeleccionada = document.getElementById('classePersona').value;

    if(opcioSeleccionada === 'soci'){
        document.getElementById('soci').classList.remove('ocult');
    } else if(opcioSeleccionada === 'administrador'){
        document.getElementById('administrador').classList.remove('ocult')
    }
}

```
I així es voria l'aplicació sencera en un bloc :

=== "Codi"
    ```html
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Formulari de html a node</title>
    </head>
    <body>
        <!-- Formulari de Persona-->
        <style>
            .ocult{
        display: none;
        }
        </style>
        <script>
        function mostrarCampsPersona(){
            document.getElementById('soci').classList.add('ocult');
            document.getElementById('administrador').classList.add('ocult');

            const opcioSeleccionada = document.getElementById('classePersona').value;

            if(opcioSeleccionada === 'soci'){
                document.getElementById('soci').classList.remove('ocult');
            } else if(opcioSeleccionada === 'administrador'){
                document.getElementById('administrador').classList.remove('ocult')
            }
        }
        function mostrarCampsRecurs(){
            document.getElementById('llibre').classList.add('ocult');
            document.getElementById('revista').classList.add('ocult');
            document.getElementById('pelicula').classList.add('ocult');

            const opcioSeleccionada = document.getElementById('classeRecurs').value;

            if(opcioSeleccionada === 'llibre'){
                document.getElementById('llibre').classList.remove('ocult');
            } else if(opcioSeleccionada === 'revista'){
                document.getElementById('revista').classList.remove('ocult')
            } else if(opcioSeleccionada === 'pelicula'){
                document.getElementById('pelicula').classList.remove('ocult')
            }
        }
        window.addEventListener('DOMContentLoaded', () => {
        const formPersona = document.forms['persona'];
        const formRecurs = document.forms['recurs'];

        // Cuando se resetea el formulario de persona, ocultar ambos bloques
        formPersona.addEventListener('reset', () => {
            document.getElementById('soci').classList.add('ocult');
            document.getElementById('administrador').classList.add('ocult');
            // Opcional: volver a poner el select en su primera opción
            document.getElementById('classePersona').selectedIndex = 0;
        });

        // Cuando se resetea el formulario de recurs, ocultar todos los bloques
        formRecurs.addEventListener('reset', () => {
            document.getElementById('llibre').classList.add('ocult');
            document.getElementById('revista').classList.add('ocult');
            document.getElementById('pelicula').classList.add('ocult');
            document.getElementById('classeRecurs').selectedIndex = 0;
        });
        });
        </script>
        <form name="persona" action="#" method="post">
            <fieldset>
                <legend>Persona</legend>
                    <label for="nom">Nom:</label><br>
                    <input type="text" id="nom" name="nom" required><br>
                    <label for="dni">DNI:</label><br>
                    <input type="text" id="dni" name="dni" required><br>
                    <label for="persona">Tipus de persona:</label><br>
                    <select id="classePersona" name="persona" onChange="mostrarCampsPersona()" required>
                        <option value="" disabled selected hidden>Selecciona una opció</option>
                        <option value="soci">Soci</option>
                        <option value="administrador">Administrador</option>
                    </select><br>
                    <div id="soci" class="ocult">
                        <label for="soci">Camp per a opció soci:</label>
                        <input type="text" id="soci" name="soci"><br>
                    </div>
                    <div id="administrador" class="ocult">
                        <label for="administrador">Tipus de administrador:</label><br>
                        <select id="administrador" name="administrador" required>
                            <option value="ajudant">Ajudant</option>
                            <option value="admin">Administrador</option>
                        </select><br>
                    </div>
                    <input type="submit" value="Enviar">
                    <input type="reset" value="Reset">
            </fieldset>
        </form>

        <form name="recurs" action="#" method="post">
            <fieldset>
                <legend>Recurs</legend>
                    <label for="titol">Titol:</label><br>
                    <input type="text" id="titol" name="titol" required><br>
                    <label for="exemplars">Número d'exemplars:</label><br>
                    <input type="number" id="exemplars" name="exemplars" required><br>
                    <label for="recurs">Tipus de recurs:</label><br>
                    <select id="classeRecurs" name="recurs" onChange="mostrarCampsRecurs()" required>
                        <option value="" disabled selected hidden>Selecciona una opció</option>
                        <option value="llibre">Llibre</option>
                        <option value="revista">Revista</option>
                        <option value="pelicula">Pel·lícula</option>
                    </select><br>
                    <div id="llibre" class="ocult">
                        <label for="autor">Nom de l'autor:</label>
                        <input type="text" id="autor" name="autor"><br>
                    </div>
                    <div id="revista" class="ocult">
                        <label for="publicacio">Data de publicació:</label><br>
                        <input type="date" id="publicacio" name="publicacio"><br>
                    </div>
                    <div id="pelicula" class="ocult">
                        <label for="director">Nom del director:</label><br>
                        <input type="text" id="director" name="director"><br>
                        <label for="genere">Gènere:</label><br>
                        <input type="text" id="genere" name="genere"><br>
                    </div>
                    <input type="submit" value="Enviar">
                    <input type="reset" value="Reset">
            </fieldset>
        </form>
    </body>
    ```
=== "Resultat"
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Formulari de html a node</title>
    </head>
    <body>
        <!-- Formulari de Persona-->
        <style>
            .ocult{
                display: none;
            }
        </style>
        <script>
        function mostrarCampsPersona(){
            document.getElementById('soci').classList.add('ocult');
            document.getElementById('administrador').classList.add('ocult');
            const opcioSeleccionada = document.getElementById('classePersona').value;
            if(opcioSeleccionada === 'soci'){
                document.getElementById('soci').classList.remove('ocult');
            } else if(opcioSeleccionada === 'administrador'){
                document.getElementById('administrador').classList.remove('ocult')
            }
        }
        function mostrarCampsRecurs(){
            document.getElementById('llibre').classList.add('ocult');
            document.getElementById('revista').classList.add('ocult');
            document.getElementById('pelicula').classList.add('ocult');
            const opcioSeleccionada = document.getElementById('classeRecurs').value;
            if(opcioSeleccionada === 'llibre'){
                document.getElementById('llibre').classList.remove('ocult');
            } else if(opcioSeleccionada === 'revista'){
                document.getElementById('revista').classList.remove('ocult')
            } else if(opcioSeleccionada === 'pelicula'){
                document.getElementById('pelicula').classList.remove('ocult')
            }
        }
        window.addEventListener('DOMContentLoaded', () => {
        const formPersona = document.forms['persona'];
        const formRecurs = document.forms['recurs'];
        // Cuando se resetea el formulario de persona, ocultar ambos bloques
        formPersona.addEventListener('reset', () => {
            document.getElementById('soci').classList.add('ocult');
            document.getElementById('administrador').classList.add('ocult');
            // Opcional: volver a poner el select en su primera opción
            document.getElementById('classePersona').selectedIndex = 0;
        });
        // Cuando se resetea el formulario de recurs, ocultar todos los bloques
        formRecurs.addEventListener('reset', () => {
            document.getElementById('llibre').classList.add('ocult');
            document.getElementById('revista').classList.add('ocult');
            document.getElementById('pelicula').classList.add('ocult');
            document.getElementById('classeRecurs').selectedIndex = 0;
        });
        });
        </script>
        <form name="persona" action="#" method="post">
            <fieldset>
                <legend>Persona</legend>
                    <label for="nom">Nom:</label><br>
                    <input type="text" id="nom" name="nom" required><br>
                    <label for="dni">DNI:</label><br>
                    <input type="text" id="dni" name="dni" required><br>
                    <label for="persona">Tipus de persona:</label><br>
                    <select id="classePersona" name="persona" onChange="mostrarCampsPersona()" required>
                        <option value="" disabled selected hidden>Selecciona una opció</option>
                        <option value="soci">Soci</option>
                        <option value="administrador">Administrador</option>
                    </select><br>
                    <div id="soci" class="ocult">
                        <label for="soci">Camp per a opció soci:</label>
                        <input type="text" id="soci" name="soci"><br>
                    </div>
                    <div id="administrador" class="ocult">
                        <label for="administrador">Tipus de administrador:</label><br>
                        <select id="administrador" name="administrador" required>
                            <option value="ajudant">Ajudant</option>
                            <option value="admin">Administrador</option>
                        </select><br>
                    </div>
                    <input type="submit" value="Enviar">
                    <input type="reset" value="Reset">
            </fieldset>
        </form>
        <form name="recurs" action="#" method="post">
            <fieldset>
                <legend>Recurs</legend>
                    <label for="titol">Titol:</label><br>
                    <input type="text" id="titol" name="titol" required><br>
                    <label for="exemplars">Número d'exemplars:</label><br>
                    <input type="number" id="exemplars" name="exemplars" required><br>
                    <label for="recurs">Tipus de recurs:</label><br>
                    <select id="classeRecurs" name="recurs" onChange="mostrarCampsRecurs()" required>
                        <option value="" disabled selected hidden>Selecciona una opció</option>
                        <option value="llibre">Llibre</option>
                        <option value="revista">Revista</option>
                        <option value="pelicula">Pel·lícula</option>
                    </select><br>
                    <div id="llibre" class="ocult">
                        <label for="autor">Nom de l'autor:</label>
                        <input type="text" id="autor" name="autor"><br>
                    </div>
                    <div id="revista" class="ocult">
                        <label for="publicacio">Data de publicació:</label><br>
                        <input type="date" id="publicacio" name="publicacio"><br>
                    </div>
                    <div id="pelicula" class="ocult">
                        <label for="director">Nom del director:</label><br>
                        <input type="text" id="director" name="director"><br>
                        <label for="genere">Gènere:</label><br>
                        <input type="text" id="genere" name="genere"><br>
                    </div>
                    <input type="submit" value="Enviar">
                    <input type="reset" value="Reset">
            </fieldset>
        </form>
    </body>
### Forma 2: Crear-los de forma modular amb JavaScript
En desenvolupament
### Extres
#### PopUps

=== "Codi"
    ```html
        <!-- Exemple PopUp-->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-modal/0.9.1/jquery.modal.min.js"></script>
        <link href="https://cdnjs.cloudflare.com/ajax/libs/jquery-modal/0.9.1/jquery.modal.min.css" rel="stylesheet"/>

        <div id="IdModal" class="modal">
            <p>Aço es un PopUp.</p>
            <a href="#" rel="modal:close">Tancar</a>
        </div>

        <p><a href="#IdModal" rel="modal:open">Exemple PopUp</a></p>
    ```
=== "Resultat"
    <!-- Exemple PopUp-->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-modal/0.9.1/jquery.modal.min.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/jquery-modal/0.9.1/jquery.modal.min.css" rel="stylesheet"/>

    <div id="IdModal" class="modal">
        <p class = "text">Aço es un PopUp.</p>
        <a href="#" rel="modal:close" class="link">Tancar</a>
    </div>
    <style>
    .text{
        color:black;
    }
    .link{
        color:black;
    }
    </style>
    <p><a href="#IdModal" rel="modal:open">Exemple PopUp</a></p>