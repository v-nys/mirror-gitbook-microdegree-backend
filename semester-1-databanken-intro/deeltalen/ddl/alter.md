# ALTER

Niet elke `CREATE`-instructie is volmaakt. Soms moet een tabel doorheen de tijd aangepast worden. Er kunnen kolommen bij komen en verdwijnen, het kan blijken dat kolommen niet het geschikte datatype hebben gekregen of dat de naamgeving niet ideaal was. In dit soort situaties komt `ALTER TABLE` van pas. `ALTER TABLE` verandert de structuur van een tabel, zonder bestaande data te beschadigen. Het is dus een DDL-instructie (en de tegenhanger van de DML-instructie `UPDATE`, die data aanpast maar niet de structuur ervan).

Al deze structurele aanpassingen beginnen met de tekst `ALTER TABLE`, gevolgd door de tabelnaam, gevolgd door een of meerdere subcommando's.

## een kolom schrappen
Het subcommando `DROP COLUMN` schrapt een kolom. Dit vereist alleen de naam van de te schrappen kolom. Bijvoorbeeld:

```sql
ALTER TABLE Books DROP COLUMN ISBNNumber;
```

## een kolom toevoegen
De `ADD COLUMN` clausule voegt een nieuwe kolom toe. De syntax om een kolom toe te voegen is dezelfde als die in een `CREATE`-instructie. Dat wil zeggen: eerst de naam, dan het datatype gevolgd door eventuele extra beperkingen zoals `NOT NULL`.

```sql
ALTER TABLE Books ADD COLUMN Publisher VARCHAR(150) NOT NULL;
```

## een kolom wijzigen

Dit gebeurt via het subcommando `CHANGE`:

```sql
ALTER TABLE TableName CHANGE OldColumnName NewColumnName NewColumnType;
```

Bijvoorbeeld, om het ISBN-nummer van een boek iets beknopter te benoemen en om het verplicht te maken:

```sql
ALTER TABLE Books CHANGE ISBNNumber ISBN varchar(13) not null;
```

