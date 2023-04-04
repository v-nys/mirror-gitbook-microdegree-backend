# Berekende kolommen
Sommige informatie is impliciet aanwezig in een tabel, terwijl het handig zou zijn als deze expliciet aanwezig was. In deze situatie kan de impliciete informatie expliciet gemaakt worden met behulp van een **gegenereerde** kolom. Deze bevat geen fysiek opgeslagen data, maar **berekende** data.

## Voorbeelden

### Een impliciete berekening
Het is geen goed idee om de volledige naam van een persoon op te slaan. Deze zal vaak van pas komen, maar zal soms ook in gesplitste vorm nodig zijn. De gesplitste voorstellingen en de samengestelde voorstelling opslaan is dan weer verspilling van ruimte. Bovendien verhoogt dit het risico op inconsistenties in de data.

Deze informatie kan ook voorgesteld worden met een gegenereerde kolom. De syntax hier is vergelijkbaar met die voor een gewone kolom, maar na het type volgt `GENERATED ALWAYS AS (...)`. De expressie moet tussen haakjes staan.

Voor de leeftijd kan dit bijvoorbeeld zijn:

```sql
CREATE TABLE Persons (
  FirstName varchar(100) not null,
  LastName varchar(100) not null,
  FullName varchar(200) GENERATED ALWAYS AS (concat(FirstName, ' ', LastName))
);
```

### Extra constraints toepassen
Een gegenereerde kolom kan ook onderworpen worden aan beperkingen. Dit kan handig zijn wanneer er iets vastgelegd moet worden over de **combinatie** van kolommen, bijvoorbeeld:

```sql
CREATE TABLE Persons (
  FirstName varchar(100) NOT NULL,
  LastName varchar(100) NOT NULL,
  PhoneNumber varchar(20),
  Email varchar(100),
  ContactInfo varchar(100) NOT NULL GENERATED ALWAYS AS (coalesce(PhoneNumber, Email))
);
```

Hoewel noch het telefoonnummer, noch het e-mailadres op zich verplicht zijn, is het wel verplicht een contactadres te hebben. Dit wordt afgedwongen omdat `COALESCE` als uitkomst `NULL` heeft wanneer **alle** argumenten `NULL` zijn.

### Beperkingen
Gegenereerde kolommen zijn onderworpen aan een aantal beperkingen. De volledige lijst is terug te vinden in [de documentatie van MySQL](<https://dev.mysql.com/doc/refman/5.7/en/create-table-generated-columns.html>), maar de voornaamste zijn:

- er mag geen gebruik gemaakt worden van stored functies
- er mag geen gebruik gemaakt worden van non-deterministische functies
