# COALESCE
De functie `COALESCE` \(Engels voor "samensmelten"\) in SQL retourneert de eerste niet-NULL expressie tussen de argumenten. Met deze functie kan je eenvoudig aangeven wat erin een `NULL` kolom moet worden getoond:

```sql
CREATE TABLE Personen (
  Voornaam VARCHAR(100) NOT NULL,
  Bijnaam VARCHAR(100) NULL,
  Familienaam VARCHAR(100) NOT NULL,
);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Fonsie', 'Foot', null);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Marje', 'Rappoport', 'Bigtax');
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Chelsey', 'Purkess', null);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Ladonna', 'Gioan', null);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Morty', 'Goatman', null);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Dukey', 'Strickland', null);
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Bidget', 'Hansmann', 'Job');
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Birdie', 'Seamen', 'Flexidy');
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Rene', 'Scroggins', 'Tempsoft');
INSERT INTO Personen (Voornaam, Familienaam, Bijnaam) values ('Rafaela', 'Moakler', 'Vagram');
SELECT Personen.Voornaam, COALESCE(Personen.Initialen,"Geen bijnaam"), Personen.Familienaam
FROM Personen;
```
