Com be diu el nom CSS pot transformar elements ja siga la grandari el color etc amb `transform` o `scale` anem a vore un exemples:

## Scale
=== "HTML"
    ```html
    <div class="item">
    <p>Item</p>
    </div>
    ```
=== "CSS"
    ```css
    .item{
        width: 200px;
        height: 200px;
        background-color: #936767;
    }
    .item:hover{
        background-color: #936767;
        transform: scale(1);
    }
    ```
=== "Resultat"
    <div class="item">
    <p>Item</p>
    </div>
    <style>
    .item{
        width: 200px;
        height: 200px;
        text-align: center;
        background-color: #936767;
    }
    .item:hover{
        background-color: #936767;
        transform: scale(1.25);
    }
    </style>

A part és pot fer com si fora un espill el contingut veiem un exemple:

=== "HTML"
    ```html
    <div class="item1">
    <p>Item 1</p>
    </div>
    <div class="item2">
    <p>Item2</p>
    </div>
    <div class="item3">
    <p>Item3</p>
    </div>
    ```
=== "CSS"
    ```css
    .item1, .item2, .item3{
        width: 200px;
        height: 200px;
        text-align: center;
        background-color: #936767;
    }

    .item1:hover{
        transform: scale(-1);
    }

    .item2:hover{
        transform: scaleX(-1);
    }

    .item3:hover{
        transform:scaleY(-1);
    }
    ```
=== "Resultat"
    <div class="item1">
    <p>Item 1</p>
    </div>
    <div class="item2">
    <p>Item2</p>
    </div>
    <div class="item3">
    <p>Item3</p>
    </div>
    <style>
    .item1, .item2, .item3{
        width: 200px;
        height: 200px;
        text-align: center;
        background-color: #936767;
    }
    .item1:hover{
        transform: scale(-1);
    }
    .item2:hover{
        transform: scaleX(-1);
    }
    .item3:hover{
        transform:scaleY(-1);
    }
    </style>

