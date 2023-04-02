# `UNION ALL`
Sommige queries worden best geschreven als de resultaten van meerdere queries onder elkaar. Dit kan met de `UNION ALL` constructie.

## Syntax

```sql
SELECT * FROM Tabel1
UNION ALL
SELECT * FROM Tabel2
```

Dit levert dan alle rijen van `Tabel1` met meteen daaronder alle rijen van `Tabel2`. De hoofdingen zijn die van de eerste resultatenset, met andere woorden die van `Tabel1`.

`UNION ALL` werkt met alle soorten `SELECT`-queries, niet alleen met `SELECT *`. Bovendien is het noodzakelijk dat `Tabel1` en `Tabel2` verschillen. Het is ook mogelijk meerdere queries op dezelfde tabel onder elkaar te plaatsen.

## Beperkingen
- `UNION ALL` kan alleen gebruikt worden wanneer de twee resultatensets hetzelfde aantal kolommen hebben.
- De hoofding van elke kolom is die van diezelfde kolom in de eerste resultatenset.

Het is mogelijk deze tweede beperking te omzeilen door de kolom te hernoemen, al gaat dat niet in combinatie met `SELECT *`:

```sql
SELECT Kolom1A AS GeschikteNaam1, Kolom2A as GeschikteNaam2 FROM Tabel1
UNION ALL
SELECT Kolom1B, Kolom2B FROM Tabel2
```
