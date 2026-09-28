# Creació i utilitzzació de tokens en Node.js
## Llibreries
Abans de començar a tocar res tenim que instal·lar la llibreria `jsonwebtoken` mitjançant `npm` amb el següent comand:
```bash
npm install jsonwebtoken
```
Quan s'instal·le deurieu de vore el següent en el fitxer `package.json` en l'arrel del vostre projecte:
```json
"dependencies": {
    "jsonwebtoken": "^9.0.2",
    // Resta de llibreries
  }
```
## Implementació
Ara ja en la llibreria instal·lada anem a explicar com generar el token i firmar-lo, és pot fer d'esta forma:
```javascript
const secretKey = "secret";

const token = jwt.sign({ name: name }, secretKey, { expiresIn: "1h" });
```

Explicació:

- `secretKey`: Clau en la que encriptara el token.
- `jwt.sign`: Firma el token per a que siga vàlid.
- `"expiresIn: 1h"`: Duració en la que el token caducara.

En este codi pots generar i firmar el token, però sense la  verificació necessaria no serveix per a molt més, però pots fer una funció per a verificar el token:
```javascript
function verifyToken(req, res, next) {
  const header = req.header("Autorització") || "";
  const token = header.split(" ")[1];
  if (!token) {
    //Error per la falta de token
    return res.status(401).json({ message: "Token not provied" });
  }
  try {
    //Verifica el token
    const payload = jwt.verify(token, secretKey);
    req.username = payload.username;
    next();
  } catch (error) {
    //Error per el token que no correspon amb les dades del usuari
    return res.status(403).json({ message: "Token no valid!" });
  }
}
```

Explicació:

- `header.split(" ")[1];`: Separa un caracter per a que no sorgeixen problemes
- `jwt.verify()`: Funció per a verificar el token
I amb això ja pots aplicar-lo a les teues funcions de validació del usuari.
### Com és poden usar els tokens?
Podriem usar els tokens per a no fer tantes consultes a la base de dades i no tindre que iniciar sessió cada vegada que entres, podries aplicar-lo de la següent forma:

```javascript
app.post("/api/users/login", async (req, res) => {
  try {
    const { name, password } = req.body;

    const [results] = await connection.query(
      "SELECT * FROM users WHERE name = ?",
      [name]
    );

    if (results.length === 0) {
      return res.status(401).json({ message: "Usuari no trobat" });
    }

    const user = results[0];
    const passwordMatch = await bcrypt.compare(password, user.password);

    if (!passwordMatch) {
      return res.status(401).json({ message: "Contrasenya incorrecta" });
    }

    const token = jwt.sign(
      { id: user.id, name: user.name, role: user.role },
      secretKey,
      { expiresIn: "5m" }
    );

    return res.status(200).json({ message: "Login correcte" });
  } catch (error) {
    console.error(error);
    return res.status(500).json({ message: "Error intern del servidor" });
  }
});
```
I després pots verificar que el token s'haja generat:
```javascript
function verifyToken(req, res, next) {
  const token = req.cookies.auth_token;

  if (!token) {
    return res.status(401).json({ message: "Token no proporcionat" });
  }

  try {
    const payload = jwt.verify(token, secretKey);
    req.user = payload;
    next();
  } catch (error) {
    return res.status(403).json({ message: "Token no vàlid o expirat" });
  }
}
```