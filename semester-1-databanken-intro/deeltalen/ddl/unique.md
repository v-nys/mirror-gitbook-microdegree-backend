# `UNIQUE`
De `UNIQUE` constraint zorgt ervoor dat een combinatie van waarden uniek is voor elke rij in een tabel. Indien deze constraint is voorzien en de gebruiker toch probeert een rij toe te voegen met een combinatie van waarden die al bestaat, genereert MySQL een foutmelding.

## Syntax

### `CREATE`
Na het opsommen van de kolommen volgt het sleutelwoord `UNIQUE`, gevolgd door een groepering van de waarden die **samen** uniek moeten zijn.

```sql
CREATE TABLE Bookings (
  Room VARCHAR(5) NOT NULL,
  TimeSlot ENUM('Morning','Afternoon','Evening') NOT NULL, -- beperkt mogelijkheden tot deze 3 opties
  UNIQUE (Room, TimeSlot);
);
```

Hierna is het mogelijk bijvoorbeeld één reservering te maken voor lokaal 03.18 in de namiddag, maar geen twee. Het is wel mogelijk om een reservering voor een ander lokaal te maken of voor een ander tijdstip. Enkel deze exacte combinatie van waarden, in exact deze volgorde, kan niet meer gebruikt worden.
