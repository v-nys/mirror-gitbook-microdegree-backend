# JOINs via tussenliggende tabel

De aanpak voor een één-op-één-relatie of een één-op-veel-relatie met één `JOIN` werkt niet wanneer er meer dan twee tabellen nodig zijn om data te combineren. Dit is het geval voor releases van games op platformen.

Om entiteiten gekoppeld via een M-op-N-relatie aan elkaar te koppelen, moet je eerst de informatie langs de M-kant koppelen met de tabel die de relatie voorstelt en vervolgens de informatie langs de N-kant koppelen.

Veronderstel volgende tabel met informatie over releases:

| Games\_Id | Platformen\_Id |
| :--- | :--- |
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 1 |
| 2 | 2 |
| 2 | 3 |
| 3 | 1 |
| 3 | 2 |
| 4 | 1 |
| 4 | 2 |
| 4 | 3 |
| 4 | 4 |

Informatie over de game waarop de release betrekking heeft kan als volgt worden toegevoegd:

```sql
SELECT Games_Id, Platformen_Id, Titel
FROM Releases
INNER JOIN Games
ON Games_Id = Games.Id;
```

Dit voegt langs de rechterkant gewoon de details over de uitgebrachte game. Het is dus een meer uitgebreide versie van de tabel `Releases`. Omdat het toegelaten is meerdere `JOIN`-operaties te combineren, kan deze stap herhaald worden. Dit staat toe ook informatie over de platformen te tonen:

```sql
SELECT Games_Id, Platformen_Id, Titel, Naam
FROM Releases
INNER JOIN Games
ON Games_Id = Games.Id
INNER JOIN Platformen
ON Platformen_Id = Platformen.Id;
```

Om enkel de relevante informatie te verkrijgen, moeten alleen de geselecteerde kolommen veranderen:

```sql
SELECT Titel, Naam
FROM Releases
INNER JOIN Games
ON Games_Id = Games.Id
INNER JOIN Platformen
ON Platformen_Id = Platformen.Id;
```
