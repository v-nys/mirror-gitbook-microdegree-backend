### data ordenen

Er zijn veel manieren om geselecteerde data te groeperen, maar de simpelste is `ORDER BY`. Als je dit toevoegt aan een `SELECT`-statement, kan je de rijen in een andere volgorde weergeven. Bijvoorbeeld:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY Titel;
```

Je kan ook een tweede (en derde,...) kolom gebruiken om knopen door te hakken:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY Voornaam, Titel;
```

De kolomnamen die je op deze manier gebruikt, hoeven **niet** getoond te worden in je resultaat.

{% hint style="warning" %}
Let op: de sorteervolgorde zal niet altijd overeenstemmen met wat je intuïtief verwacht. Ze hangt af van de gebruikte methode om stukken tekst te vergelijken, de zogenaamde "collation".
{% endhint %}

Er is ook een kortere, maar beperktere manier om te sorteren:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY 1, 2;
```

Dit sorteert eerst volgens de eerste kolom en dan volgens de tweede.


