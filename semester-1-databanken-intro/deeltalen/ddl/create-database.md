# `CREATE DATABASE`
Vooraleer je SQL-instructies kan schrijven, heb je een database nodig. Dit is niet hetzelfde als een Database Management System (DBMS), dus het volstaat niet om MySQL of een ander DBMS te installeren. Je moet een tabel aanmaken met volgende syntax:

```sql
CREATE DATABASE MyDatabase; -- de naam is vrij te kiezen
```

Dit zal een lege database aanmaken, zonder tabellen. Je kan alleen een database maken met een naam die nog niet bestaat op de server.

Om een foutmelding te vermijden indien de database al bestaat, kan je volgende instructie gebruiken:

```sql
CREATE DATABASE IF NOT EXISTS MyDatabase;
```

Dit kan handig zijn omdat foutmeldingen verhinderen dat latere code uitvoert.
