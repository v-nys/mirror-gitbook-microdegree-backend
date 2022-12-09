# Voorbeeld oefening JWT in NodeJS

```javascript
// Importeer de nodige packages
const express = require("express");
const bodyParser = require("body-parser");
const jwt = require("jsonwebtoken");

// Maak een express-app
const app = express();

// Zet body-parser in om het request-lichaam te parsen
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// Maak een JWT geheim
const JWT_SECRET = "secretkey";

// Maak een route om JWT tokens te genereren
app.post("/login", (req, res) => {
  // Haal de gebruikersgegevens op uit het request-lichaam
  const user = {
    username: req.body.username,
    password: req.body.password,
  };

  // Genereer een JWT token met behulp van de gebruikersgegevens en een geheime sleutel
  const token = jwt.sign(user, JWT_SECRET);

  // Stuur het JWT token terug naar de gebruiker
  res.json({ token });
});

// Maak een route om de JWT token te verifiëren en de gebruikersgegevens terug te sturen
app.get("/profile", (req, res) => {
  // Haal het JWT token op uit de request headers
  const token = req.headers["authorization"];

  // Controleer of het token geldig is met behulp van de geheime sleutel
  jwt.verify(token, JWT_SECRET, (err, user) => {
    if (err) {
      // Stuur een foutbericht als het token ongeldig is
      res.sendStatus(403);
    } else {
      // Stuur de gebruikersgegevens terug als het token geldig is
      res.json(user);
    }
  });
});

// Start de server op poort 3000
app.listen(3000, () => console.log("Server gestart op poort 3000"));
```
