# SELECT

## Inspecteren van je data

Je kan in MySQL Workbench wel rechtstreeks naar je tabellen kijken, maar om gerichter te zoeken, moet je het commando kennen dat achter de schermen wordt uitgevoerd. Dat is het `SELECT`-commando.

### de basis

De simpelste vorm van het `SELECT` commando toont gewoon alle data in een bepaalde tabel, bijvoorbeeld:

```sql
USE ApDB;
SELECT * FROM Boeken;
```

De asterisk is een "wildcard" of "joker". Ze geeft aan dat we **alle** kolommen willen zien. We kunnen ook kijken naar specifieke kolommen:

```sql
USE ApDB;
SELECT Voornaam, Titel FROM Boeken;
```

Tip: als je de namen van de kolommen niet uit het hoofd kent, typ dan eerst de naam van de tabel, gevolgd door een punt. Dan kan Workbench slim aanvullen:

```sql
SELECT Boeken.Voornaam, Boeken.Titel FROM Boeken;
```


