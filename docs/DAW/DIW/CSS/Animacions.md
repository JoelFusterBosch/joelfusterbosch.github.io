Les animacions poden fer que en una part de la web es reproduisquen animacions de més simples a més complexes anem a vore alguns exemples de animacions:

## Bounce
=== "HTML"
    ```html
    <div class="box bounce">Rebot</div>
    ```
=== "CSS"
    ```css
    .box {
      width: 120px;
      height: 120px;
      background: #ffffff;
      border-radius: 10px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 14px;
      font-weight: bold;
      color: #333;
      text-align: center;
      border: 3px solid #333; /* Borde de la caixa */
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); /* Ombra per fer que sembli una caixa */
      transition: all 0.3s ease; /* Transició suau en l'animació */
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-50px); }
    }

    .bounce {
      animation: bounce 2s infinite;
    }
    ```
=== "Resultat"
    <div class="box bounce">Rebot</div>
    <style>
      .box {
        width: 120px;
        height: 120px;
        background: #ffffff;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 14px;
        font-weight: bold;
        color: #333;
        text-align: center;
        border: 3px solid #333; /* Borde de la caixa */
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); /* Ombra per fer que sembli una caixa */
        transition: all 0.3s ease; /* Transició suau en l'animació */
      }
      @keyframes bounce {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-50px); }
      }
      .bounce {
        animation: bounce 2s infinite;
      }
    </style>

### Rotació
=== "HTML"
    ```html
    <div class="box bounce">Rebot</div>
    ```
=== "CSS"
    ```css
    
    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    
    .rotate {
      animation: rotate 3s infinite linear;
    }
    ```
=== "Resultat"
    <div class="box rotate">Rotació</div>
    <style>
      @keyframes rotate {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }

      .rotate {
        animation: rotate 3s infinite linear;
      }
    </style>