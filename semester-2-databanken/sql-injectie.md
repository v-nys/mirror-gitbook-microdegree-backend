# SQL injectie
Surfers zijn normaal **onrechtstreekse** gebruikers van een SQL-databank. Ze voeren handelingen op een website uit, die dan vertaald worden naar SQL-statements. Dit gebeurt typisch door middel van een SQL connector en maakt allerlei handige features mogelijk.

Het risico bestaat echter dat een gebruiker zich **rechtstreekse** toegang tot de databank toeëigent. Dit kan in het bijzonder wanneer een script geen onderscheid maakt tussen SQL-syntax en gegevens. Eenvoudiger gesteld: als een script of programma gebruikersinvoer in vooraf geschreven SQL-code plakt, kan de gebruiker zelf SQL-code intypen.

Hieronder een voorbeeld in TypeScript, maar dit kan in elke programmeertaal:

```typescript
// we maken twee variabelen aan
let typedUserName: string = input.question("Wat is je gebruikersnaam?");
let typedPassword: string = input.question("Wat is je wachtwoord?");
// we veronderstellen dat er al een connectie is, hoe je deze aanmaakt is hier niet belangrijk
// connection.execute betekent gewoonweg dat deze query wordt uitgevoerd
connection.execute(`SELECT * FROM Users WHERE UserName="${typedUserName}" and Password="${typedPassword}"`);
```

{% hint style="warning" %}
Deze code bevat nog andere tekortkomingen wanneer het op security aankomt. Het wachtwoord wordt getoond wanneer het wordt ingetypt. De kolom voor wachtwoorden is op geen enkele manier versleuteld. Dit is om het voorbeeld duidelijker te maken. Het principe van SQL-injectie staat hier los van.
{% endhint %}

De backticks (dus de "schuine enkele quotes") zorgen dat de ingetypte waarden worden ingevuld waar `${...}` staat. Dus hiermee krijgt de gebruiker normaal zijn / haar eigen gegevens te zien, op voorwaarde dat de combinatie van gebruikersnaam en wachtwoord klopt.

{% hint style="info" %}
Om precies te zijn: hiermee krijgt de gebruiker toegang tot deze gegevens. Er staat nog geen code om deze te tonen, maar in een volledig programma zou er meer code staan.
{% endhint %}

Veronderstel nu dat een aanvaller het programma als volgt gebruikt (de `>` geeft aan dat de gebruiker begint te typen):

```text
Wat is je gebruikersnaam?
> " OR TRUE; -- 
Wat is je wachtwoord?
> Who cares?
```

Dan is het effect dat volgende query wordt uitgevoerd:

```sql
SELECT * FROM Users WHERE UserName="" OR TRUE; -- " and Password="Who cares?"
```

Hier wordt de `WHERE` volledig uitgeschakeld. De aanvaller krijgt op deze manier toegang tot **alle** gebruikersgegevens. Het is **altijd** een risico om gebruikersinvoer in SQL-code te plakken zonder eerst een grens te trekken tussen syntax en data.
