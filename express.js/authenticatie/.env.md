# Environment Variables

## Wat zijn Environment Variables?&#x20;

Letterlijk vertaald betekent het omgevingsvariabelen. Ze bieden informatie over de werkomgeving van een Node project.&#x20;

**Omgevingsvariabelen in Node worden gebruikt om:**

* Gevoelige gegevens op te slaan, zoals wachtwoorden, API-referenties en andere informatie die niet rechtstreeks in je code mag worden geschreven om beveiligingsrisico's te voorkomen.&#x20;
* Instellingen te configureren die kunnen verschillen tussen omgevingen. Denk maar aan poorten en verwijzingen naar databanken (development, staging, test of productie).

Je hebt out of the box toegang tot omgevingsvariabelen in Node.js. Wanneer je een Node server opstart, biedt het automatisch toegang tot alle bestaande omgevingsvariabelen door een `env`-object te maken binnen het globale `process` object.

Ga je gang en probeer het globale `process` object en daarvan de `env` eigenschap eens te loggen in je console. Maak een lege map met de naam **env-tryout.** Maak vervolgens een bestand met de naam **server.js** en voeg de onderstaande code eraan toe.

```javascript
// server.js
console.log(process.env);
```

Deze code retourneert alle omgevingsvariabelen die op het object `process.env` leven. Om toegang te krijgen tot een specifieke variabele, benader je deze zoals een eigenschap van een object:

```javascript
console.log('The value of PORT is:', process.env.PORT);
```

Wanneer je nu `node server.js` uitvoert, zou je een bericht moeten zien met de tekst _"The value of PORT is: undefined"_.

Je omgevingsvariabele is er niet omdat de eigenschap PORT geen standaard variabele is van het `process.env` object. We moeten deze zelf definiëren. Laten we eens kijken naar manieren waarop we dit kunnen oplossen.

* Met behulp van de **terminal**;
* Met behulp van een **.env-bestand**;

#### Terminal

De eenvoudigste manier om de PORT variabele een waarde te geven, is door deze in je terminal tijdens de opstart van je server te declareren. Je geeft de naam van de variabele op, gevolgd door het gelijkteken en de waarde. Roep vervolgens je Node.js-app aan.

```
PORT=3000 node server.js
```

Normaliter zie je nu het volgende bericht:  _"The value of PORT is: 3000"_.

Je kan dit patroon herhalen en ook andere variabelen toevoegen. Hier is een voorbeeld van het doorgeven van twee omgevingsvariabelen.

```
PORT=3000 NODE_ENV=development node server.js
```

#### Een .env-bestand

Als je er eenmaal een aantal hebt gedefinieerd, zal je snel merken dat het een onderhoudsnachtmerrie wordt. Stel je voor dat je een tiental omgevingsvariabelen gebruikt. Dit schaalt niet goed als je ze allemaal op één regel moet typen.

**Omgevingsvariabelen uitvoeren vanaf een terminal is zeker handig. Maar het heeft zijn nadelen:**

* Je kan de lijst met variabelen niet raadplegen;
* Het is veel te gemakkelijk om een ​​typefout te maken;

Een populaire oplossing voor het organiseren en onderhouden van je omgevingsvariabelen is het gebruik van een `.env`-bestand. Het helpt ons om alle omgevingsvariabelen op één plek te definiëren en indien nodig te wijzigen.

Maak het `.env`-bestand in de hoofdmap van je app en voeg je variabelen en waarden eraan toe.



{% code title=".env" %}
```json
NODE_ENV=development
PORT=3000
# Zet je database/API connectie informatie hier
API_KEY=**************************
API_URL=**************************
```
{% endcode %}

#### Een .gitignore-bestand

Een .`env`-bestand is een geweldige manier om al je omgevingsvariabelen op één plek te verzamelen. Zorg er wel voor dat je het `.env`-bestand niet in een version control systeem zoals [Git](https://git-scm.com/) plaatst. Anders bevat je version control historiek referenties van je omgevingsvariabelen. Dit zou een beveiligingsrisico vormen aangezien er gevoelige informatie in je omgevingsvariabelen kan staan.

Maak een `.gitignore`-bestand en voeg er `.env` aan toe, zoals weergegeven in de volgende afbeelding.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Bron: <a href="https://medium.com/the-node-js-collection/making-your-node-js-work-everywhere-with-environment-variables-2da8cdf6e786">https://medium.com/the-node-js-collection/making-your-node-js-work-everywhere-with-environment-variables-2da8cdf6e786</a></p></figcaption></figure>

{% hint style="info" %}
Het `.gitignore`-bestand vertelt het version control systeem om de bestanden (of folders) die je opsomt te negeren.
{% endhint %}

#### dotenv npm-module

Je hebt je omgevingsvariabelen gedefinieerd in het `.env`-bestand maar hoe worden de waarden uit dit bestand ingeladen? De gemakkelijkste manier is door een npm-module genaamd `dotenv` te gebruiken. Installeer de module eenvoudig via npm:

```
npm install dotenv
```

Voeg daarna de volgende regel helemaal bovenaan je server.js toe:

{% code title="server.js" %}
```javascript
require('dotenv').config();
```
{% endcode %}

Deze code laadt automatisch het `.env`-bestand in de hoofdmap van je project en initialiseert de waarden, waarbij alle reeds vooraf ingestelde variabelen worden overgeslagen.

Laten we onze server.js file een beetje bewerken:

{% code title="server.js" %}
```javascript
console.log(`Your port is ${process.env.PORT}`); // undefined
const dotenv = require('dotenv');
dotenv.config();
console.log(`Your port is ${process.env.PORT}`); // 3000
```
{% endcode %}

Voer de code uit vanaf de terminal zonder expliciet een PORT variabele door te geven, met behulp van de volgende opdracht:

```
node server.js
```

De code geeft de beginwaarde weer van de `PORT`-omgevingsvariabele, die `undefined` zal zijn. Vervolgens importeer je de `dotenv`-package en voer je daarvan de `config()` functie uit, die het .env-bestand leest en de omgevingsvariabelen instelt. De laatste coderegel geeft degelijk de correcte waarde van `PORT` terug, namelijk 3000.

### Conclusie

**Custom omgevingsvariabelen gebruiken in Node stappenplan:**

1. Maak een `.env`-bestand:
   1. Het bestand moet in de hoofdmap van je project worden geplaatst;
2. Installeer de `dotenv`-bibliotheek:&#x20;
   1. npm install dotenv;
3. require dotenv zo vroeg mogelijk:&#x20;
   1. `require('dotenv').config({path: __dirname + '/.env'})`;

#### Resources

* [Wat zijn Omgevingsvariabelen en hoe maak je een .env file aan?](https://www.codementor.io/@parthibakumarmurugesan/what-is-env-how-to-set-up-and-run-a-env-file-in-node-1pnyxw9yxj)
* [Inladen van .env variabelen](https://www.npmjs.com/package/dotenv)
