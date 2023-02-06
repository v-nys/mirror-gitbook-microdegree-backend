---
description: >-
  In dit hoofdstuk zal je leren werken met de node-module Bcrypt voor het salten
  en hashen van paswoorden in NodeJS.
---

# Paswoord salting en hashing met bcrypt

### Voorbeeld code

```typescript
const bcrypt = require('bcrypt');

// De grote van saltRounds bepaalt de moeilijkheidsgraad
// waarmee de hash met brute force kan gekraakt worden.
const saltRounds = 10;
const password = "mijnPaswoord"

// Genereert een salt m.b.v. saltRounds
bcrypt.genSalt(saltRounds, function(err, salt) {
// Genereert een hash m.b.v. de vooraf gegenereerde salt
    bcrypt.hash(password, salt, function(err, hash) {
        console.log(hash) // $2b$10$bRFjmlcWNag/YQkdvsFXxOsqj.JjIQk1GGtGQvHFmkcZ09yaPoYdu
        // Bewaar de hash in je databank.
    });
});

// Vergelijk en verifieer paswoorden
const passwordToCompare = "mijnPaswoord";
const hashedPassword = "$2b$10$bRFjmlcWNag/YQkdvsFXxOsqj.JjIQk1GGtGQvHFmkcZ09yaPoYdu";
bcrypt.compare(passwordToCompare, hashedPassword, function(err, result) {
    console.log(result);
    // result == true
});
```

In het bovenstaande voorbeeld genereren we eerst een salt met 10 rondes en gebruiken deze om het paswoord "`mijnPaswoord`" te hashen. Vervolgens vergelijken we het paswoord in plain tekst met het gehashte paswoord om te controleren of ze overeenkomen. De functie `compare` retourneert een Booleaanse waarde die aangeeft of de wachtwoorden overeenkomen of niet.

## Stap voor stap

### Stap 1: Installatie bcrypt

Creeër een folder genaamd "bcrypt-example" en open het in VScode en installeer de node-module bcrypt met behulp van de onderstaande commmando.

```
npm install bcrypt
```

Er zal een `package.json` file worden aangemaakt met de volgende inhoud.

```json
{
  "dependencies": {
    "bcrypt": "^5.1.0"
  }
}
```

### Stap 2: Importeer bcrypt

Maak een nieuwe file aan genaamd "bcrypt-example.ts" in je root folder en importeer bcrypt.

![](<../../../.gitbook/assets/image (2).png>)

{% code title="bcrypt-example.ts" %}
```typescript
const bcrypt = require("bcrypt")
```
{% endcode %}

### Stap 3: genereer een salt

Definieer de volgende twee constanten:

1. `saltRounds` met als waarde `10`
2. `password` met als waarde `mijnPaswoord`

Roep vervolgens de methode `bcrypt.genSalt()` aan om de salt te genereren. Deze methode accepteert een geheel getal, de kostenfactor die de tijd bepaalt die nodig is om een paswoord te hashen. Hoe hoger de kostenfactor, hoe meer tijd het algoritme nodig heeft en hoe moeilijker het is om de hash met brute force te kraken. Een goede waarde moet hoog genoeg zijn om het paswoord te beveiligen, maar ook laag genoeg om het proces niet te vertragen. Het varieert gewoonlijk tussen 5 en 15. In deze zelfstudie gebruiken we 10.

{% code title="bcrypt-example.ts" %}
```typescript
const bcrypt = require("bcrypt");

const saltRounds = 10;
const password = "mijnPaswoord";

// Genereert een salt m.b.v. saltRounds
bcrypt.genSalt(saltRounds, function (err, salt) {
  console.log(salt); // $2b$10$Hb1EplYMBx1l.GgMBvCDQO
});
```
{% endcode %}

### Stap 4: Hash het paswoord

Geef het paswoord en de gegenereerde salt door aan de `hash()` methode:

{% code title="bcrypt-example.ts" %}
```typescript
const bcrypt = require("bcrypt");

const saltRounds = 10;
const password = "mijnPaswoord";

// Genereert een salt m.b.v. saltRounds
bcrypt.genSalt(saltRounds, function (err, salt) {
  // Genereert een hash m.b.v. de vooraf gegenereerde salt
  bcrypt.hash(password, salt, function (err, hash) {
    console.log(hash); // $2b$10$A2PQc4H01oHtD54Fr3LM6uPMASpMeuICZYGVeOZWVqHVOnhu8FK4O
  });
});
```
{% endcode %}

Nadat je de hash hebt gegenereerd, kan je deze opslaan in de database. Je zult het gebruiken om een paswoord te verifiëren en een gebruiker te authenticeren die probeert in te loggen.

{% hint style="info" %}
In plaats van de salt en de hash afzonderlijk te genereren, kan je de salt en de hash ook automatisch genereren met één enkele functie.
{% endhint %}

```typescript
bcrypt.hash(password, saltRounds, function(err, hash) {
    // Bewaar de hash in je databank.
});
```

### Stap 5: Vergelijk en verifieer paswoorden met behulp van bcrypt

Om gebruikers te authenticeren, moet je het paswoord dat ze verstrekken vergelijken met dat in de database. `bcrypt.compare()` accepteert het paswoord in platte tekst en de hash die je hebt opgeslagen, samen met een callback-functie. Die callback levert een object met alle opgetreden fouten en het algehele resultaat van de vergelijking. Als het paswoord overeenkomt met de hash, is het resultaat `true`.

{% code title="bcrypt-example.ts" %}
```typescript
// Vergelijk en verifieer paswoorden
const passwordToCompare = "mijnPaswoord";
const hashedPassword = "$2b$10$bRFjmlcWNag/YQkdvsFXxOsqj.JjIQk1GGtGQvHFmkcZ09yaPoYdu";
bcrypt.compare(passwordToCompare, hashedPassword, function(err, result) {
    console.log(result);
    // result == true
});
```
{% endcode %}
