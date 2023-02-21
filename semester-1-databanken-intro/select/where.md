# SELECT met WHERE
In de meeste gevallen zijn we niet geïnteresseerd om alle rijen uit een tabel te selecteren. We willen over de mogelijkheid beschikken om alleen de rijen, die aan een bepaalde voorwaarde voldoen, te kunnen selecteren.

De oplossing bestaat erin de `WHERE`-clausule te gebruiken. De `WHERE`-clausule bevat een **booleaanse expressie**. Dit is een expressie die als resultaat voor een bepaalde rij `TRUE` of `FALSE` moet opleveren. In tegenstelling tot de meeste programmeertalen gebruikt SQL ook een derde mogelijke waarde: `NULL`. Deze waarde komt voor wanneer we niet kunnen bepalen of iets waar of niet waar is.

Om de `WHERE` te gebruiken, zet je hem na de `FROM Tabel`.

Bijvoorbeeld:

```sql
USE ApDB;
SELECT Voornaam, Familienaam, Titel 
FROM Boeken
-- deze vergelijking levert TRUE of FALSE of NULL op
WHERE Familienaam = 'Augustinus';
```

Je krijgt `NULL` wanneer je bijvoorbeeld vergelijkt met een niet-ingevulde waarde, ook geschreven als `NULL`. Zelfs `NULL` is niet gelijk aan `NULL`.

Zelfs in een tabel die `NULL` als titel toelaat, levert volgende query dus nooit een resultaat op:

```sql
USE ApDB;
SELECT Voornaam, Familienaam, Titel 
FROM Boeken
WHERE Titel = NULL;
```

Ook deze query levert nooit een resultaat op:

```sql
USE ApDB;
SELECT Voornaam, Familienaam, Titel 
FROM Boeken
-- <> betekent het omgekeerde van =
WHERE Titel <> NULL;
```

**Het ligt niet aan de data! Vergelijkingen met `NULL` via `=` en `<>` zijn zinloos!** Als je wil controleren of de waarde in een bepaalde kolom ontbreekt, schrijf dan `IS NULL` in plaats van `= NULL`!
