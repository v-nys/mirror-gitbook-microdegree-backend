# `DROP DATABASE`
Indien je een database niet meer nodig hebt, kan je ze verwijderen met volgende syntax:

```sql
DROP DATABASE MyDatabase; -- de naam is vrij te kiezen
```

Let op: dit verwijdert de volledige inhoud van de database.

Indien je niet zeker weet of de database wel bestaat, kan je een foutmelding vermijden als volgt:

```sql
DROP DATABASE IF EXISTS MyDatabase;
```

Dit heeft geen enkel effect als `MyDatabase` niet in gebruik is.
