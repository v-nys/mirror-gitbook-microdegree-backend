# Functies
Functies in SQL staan je toe een waarde te berekenen aan de hand van eventueel reeds gekende inputs.

## SUBSTRING

Deze functie gebruik je om een deel van een stuk tekst over te houden. Je kan bijvoorbeeld dit doen om de eerste twee letters van de familienaam van een auteur te tonen:

```sql
SELECT SUBSTRING(Familienaam,1,2) FROM Boeken;
```

Je bent ook niet beperkt tot kolomwaarden, je mag ook gewone constanten gebruiken:

```sql
SELECT SUBSTRING('Hallo',1,2);
```

Je kan wel net zo goed dit doen:

```sql
SELECT 'Ha';
```

Als je alleen het begin van een string wil, kan je ook `LEFT` gebruiken:

```sql
SELECT LEFT('Hallo',2);
```

## CONCAT

Deze functie gebruik je om stukken tekst aan elkaar te hangen. Je kan dus dit doen om de volledige naam van auteurs te tonen:

```sql
SELECT CONCAT(Voornaam,' ',Familienaam) FROM Boeken;
```

Je kan dit ook duidelijker laten weergeven in Workbench met:

```sql
SELECT CONCAT(Voornaam,' ',Familienaam) AS Naam FROM Boeken;
```

## CHAR\_LENGTH

Hiermee bereken je de lengte van een stuk tekst. Je kan bijvoorbeeld dit doen:

```sql
SELECT CHAR_LENGTH(Familienaam) FROM Boeken;
```

Dit zal je niet de familienaam van elke auteur tonen, maar wel het aantal letters in hun familienaam.

Net zo kan je dit doen:

```sql
SELECT CHAR_LENGTH('abc');
```

Dan zal je als resultaat `3` krijgen.

{% hint style="warning" %}
Gewoonweg `LENGTH` bestaat ook, maar er is een subtiel verschil. Die functie geeft de lengte in bytes van een stuk tekst. Als je buiten het ASCII-alfabet gaat, kan die hoger liggen dan `CHAR_LENGTH`.
{% endhint %}

## Wiskundige operaties

Ook standaard wiskundige operaties zijn functies. Bijvoorbeeld:

```sql
SELECT 1 + Duurtijd FROM Nummers;
SELECT Duurtijd - 1 FROM Nummers;
```

## RAND

Deze functie heeft *geen* invoer nodig en produceert een willekeurig getal tussen 0 en 1. In principe kan ze 0 opleveren, maar nooit exact 1. Bijvoorbeeld:

```sql
SELECT RAND();
```

{% hint style="info" %}
Hiermee heb je een beeld van enkele typische functies, maar MySQL voorziet er veel meer. Raadpleeg [de officiële documentatie](https://dev.mysql.com/doc/refman/8.0/en/functions.html) als je een bewerking nodig hebt waarvoor je verwacht dat de functionaliteit al voorzien zou kunnen zijn.
{% endhint %}
