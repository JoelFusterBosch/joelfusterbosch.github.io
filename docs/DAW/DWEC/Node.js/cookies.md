# Creació i utilitzzació de cookies en Node.js
## Llibreries
Abans de fer res hem d'instal·lar la llibreria `cookie-parser` mitjançant `npm` amb el següent comand:
```bash
npm install cookie-parser
```
Quan s'instal·le deurieu de vore el següent contingut en el fitxer `package.json` localitzat en l'arrel del vostre projecte:
```json
"dependencies": {
    "cookie-parser": "^1.4.7",
    // Resta de llibreries
  }
```
## Implementació
Ara ja amb la llibreria de cookies instal·lada, és pot crear cookies de la següent forma:
```javascript
res.cookie("auth_token", token, {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "strict",
      maxAge: 5 * 60 * 1000
    });
```

### Com usar les cookies
Pots combinar-lo amb els tokens de la següent forma:
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

    res.cookie("auth_token", token, {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "strict",
      maxAge: 5 * 60 * 1000
    });

    return res.status(200).json({ message: "Login correcte" });
  } catch (error) {
    console.error(error);
    return res.status(500).json({ message: "Error intern del servidor" });
  }
});
```