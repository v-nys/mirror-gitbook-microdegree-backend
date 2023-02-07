# Cookies & Sessions

## Session en cookies

### Cookies

### HTTP is stateless

HTTP is een stateless protocol. Dit betekent dat de server in principe geen informatie over de client bijhoudt. Als je een webpagina bezoekt, zal de server niet weten of je daarvoor al eens op die pagina bent geweest. Dit is een groot probleem, want hoe kan de server dan bijhouden dat je ingelogd bent? Of dat je een bepaalde product in je winkelmandje hebt gelegd?

Om dit probleem op te lossen, gebruiken we cookies. Een cookie is een klein stukje informatie dat de server naar de client stuurt. De client slaat deze informatie op en stuurt deze informatie bij elke volgende request naar de server. Op die manier kan de server bijhouden welke client welke informatie heeft.

### Cookies in Express

Als we willen dat Express cookies kan gebruiken, moeten we eerst de cookie-parser middleware installeren:

```bash
npm install cookie-parser
```

Deze library heeft geen built-in typescript types, dus we moeten de types van de `cookie-parser` library installeren:

```bash
npm install --save-dev @types/cookie-parser
```

We kunnen de cookie-parser middleware dan toevoegen aan onze applicatie:

```typescript
import express from 'express';
import cookieParser from 'cookie-parser';

app.use(cookieParser());
```

### Cookie aanmaken

Om een cookie aan te maken, gebruiken we de `res.cookie()` functie. Deze functie heeft twee parameters: de naam van de cookie en de waarde van de cookie.

```typescript
res.cookie('name', 'value'});
```

Als we bijvoorbeeld willen bijhouden hoeveel keer een gebruiker een pagina heeft bezocht, kunnen we een cookie aanmaken met de naam `visitCount` en de waarde `1`. Als de gebruiker de pagina opnieuw bezoekt, kunnen we de waarde van de cookie met 1 verhogen.

```typescript
app.get('/', (req, res) => {
  let currentCount;
  if (req.cookies.visitCount) {
    currentCount = parseInt(req.cookies.visitCount) + 1
  } else {
    currentCount = 1;
  }
  res.cookie('visitCount', currentCount)
  res.send('You have visited this page ' + currentCount + ' times.');
});
```

Hoewel dat cookies zeer belangrijk zijn voor authenticatie, is het niet veilig om de waarde van een cookie te vertrouwen. Een gebruiker kan namelijk de waarde van een cookie veranderen in de browser. We zien later nog hoe we dit probleem kunnen oplossen.

### Cookie verwijderen

Om een cookie te verwijderen, gebruiken we de `res.clearCookie()` functie. Deze functie heeft één parameter: de naam van de cookie die we willen verwijderen.

```typescript
res.clearCookie('name');
```

### Cookie opties

De `res.cookie()` functie heeft nog een aantal opties. Hier een overzicht van de belangrijkste opties die we later nog nodig zullen hebben:

* `maxAge`: de levensduur van de cookie in milliseconden. Als deze optie niet wordt meegegeven, dan wordt de cookie verwijderd wanneer de browser wordt afgesloten.
* `httpOnly`: als deze optie `true` is, dan kan de cookie niet worden gelezen door JavaScript. Dit is een veiligheidsmaatregel om cross-site scripting aanvallen te voorkomen.

## Sessions

Zoals we al gezien hebben, is het niet veilig om de waarde van een cookie te vertrouwen. Stel dat we de volgende code gebruiken om een cookie aan te maken na het inloggen van een gebruiker:

```typescript
app.get('/login', (req, res) => {
  let username = req.query.username;
  let password = req.query.password;

  if (username === 'admin' && password === 'admin') {
    res.cookie('loggedIn', true);
    res.redirect('/');
  } else {
    res.redirect('/login');
  }
});
```

Als we hier op vertrouwen en de waarde van de cookie niet controleren, dan kan een gebruiker de cookie waarde veranderen in `true` en zo de applicatie misbruiken.

Om dit probleem op te lossen, gebruiken we sessions. Een session is een object dat de server bijhoudt voor elke client. De server kan deze objecten gebruiken om informatie over de client bij te houden. Om sessions te kunnen gebruiken wordt er een unieke id gegenereerd voor elke client. Deze id wordt opgeslagen in een cookie. De server kan dan de id van de cookie gebruiken om de juiste session op te halen.

<figure><img src="../.gitbook/assets/image (1) (4).png" alt=""><figcaption><p><a href="https://dev.to/dennis1001/understanding-cookies-and-sessions-in-php-35k5">https://dev.to/dennis1001/understanding-cookies-and-sessions-in-php-35k5</a></p></figcaption></figure>

Je kan dit nakijken in je browser door de cookies te bekijken, je zal een cookie zien een waarde die op een lange string lijkt. Deze string is de id van de session.

### Sessions in Express

Het zou mogelijk zijn om zelf session objecten te maken en deze bij te maken en een id te genereren. Maar dit is een tijdrovende taak en er zijn al veel libraries die dit voor ons doen. We gaan gebruik maken van de `express-session` library.

Om sessions te kunnen gebruiken, moeten we eerst de express-session library installeren:

```bash
npm install express-session
npm install --save-dev @types/express-session
```

We kunnen de express-session middleware dan toevoegen aan onze applicatie:

```typescript
app.use(session({
  secret: "keyboard cat"
}));
```

Merk op dat we hier gebruik maken van een `secret` parameter. Deze parameter is nodig om de sessie te kunnen signen. Als je deze parameter niet meegeeft, dan zal je applicatie niet werken. Meestal halen we deze parameter uit een environment variable.

Nu kunnen we de session objecten gebruiken in onze applicatie. We kunnen bijvoorbeeld een `loggedIn` property toevoegen aan de session object:

```typescript
app.get('/login', (req, res) => {
  let username = req.query.username;
  let password = req.query.password;
  if (username === 'admin' && password === 'admin') {
    (req.session as any).loggedIn = true;
    res.redirect('/');
  } else {
    res.redirect('/login');
  }
});
```

Als je dan gaat kijken in je cookies in je browser, zal je zien dat er een cookie is aangemaakt met de naam `connect.sid`. Deze cookie bevat de id van de session. Er is geen vermelding meer van de `loggedIn` cookie.

{% hint style="danger" %}
Merk op dat we hier gebruik maken van de `as any` cast. Dit doen we omdat het type van de `req.session` property geen `loggedIn` property heeft. We kunnen dit oplossen door een interface te maken voor de session objecten. Maar dit is niet nodig voor dit voorbeeld.
{% endhint %}
