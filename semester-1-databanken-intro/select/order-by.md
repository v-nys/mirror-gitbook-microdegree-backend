# data ordenen

Er zijn veel manieren om geselecteerde data te groeperen, maar de simpelste is `ORDER BY`. Als je dit toevoegt aan een `SELECT`-statement, kan je de rijen in een andere volgorde weergeven. Bijvoorbeeld:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY Titel;
```

Je kan ook een tweede (en derde,...) waarde gebruiken om knopen door te hakken:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY Voornaam, Titel;
```

In dit geval wordt nog steeds op voornaam gesorteerd, maar als twee voornamen gelijk zijn, wordt op titel gesorteerd. Vergelijk met hoe het telefoonboek in de eerste plaats op familienaam sorteert, maar de voornaam gebruikt om de knoop door te hakken.

De kolomnamen die je op deze manier gebruikt, hoeven **niet** getoond te worden in je resultaat. Zie het alsof de volgorde **eerst** wordt vastgelegd **vooraleer** de uiteindelijke kolommen getoond worden.

{% hint style="warning" %}
Let op: de sorteervolgorde zal niet altijd overeenstemmen met wat je intuïtief verwacht. Ze hangt af van de gebruikte methode om stukken tekst te vergelijken, de zogenaamde "collation".
{% endhint %}

Er is ook een kortere, maar beperktere manier om te sorteren:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY 1, 2;
```

Dit sorteert eerst volgens de eerste kolom en dan volgens de tweede. In deze tekst verkiezen we meestal de syntax met de kolomnamen.

## richting van de ordening
Normaal gesproken wordt oplopend gesorteerd, dus van "laag" naar "hoog". Dat kan zijn van A naar Z, van kleine naar grote getallen,...

Je kan de sorteerrichting vastleggen door de keywords `ASC` en `DESC` toe te voegen aan de waarden die gebruikt worden om te sorteren. Bijvoorbeeld:

```sql
USE ApDB;
SELECT * FROM Boeken ORDER BY Voornaam DESC, Titel ASC;
```

Dit sorteert nog steeds boeken volgens voornaam van de auteur en gebruikt ook de titel om knopen door te hakken, maar de auteurs wiens voornaam begint met een "Z" komen vooraan. Boeken van auteurs met dezelfde voornaam verschijnen wel van A naar Z. Dit zou bijvoorbeeld de output van deze query kunnen zijn:

| Voornaam | Familienaam | Titel |
|-|-|-|
| Steve | Klabnik | The Rust Programming Language |
| James | Corey | Caliban's War |
| James | M.R. | Collected Ghost Stories |
| James | M.R. | Count Magnus and Other Ghost Stories |
| James | Corey | Leviathan Wakes |
| Alexander | Theroux | Darconville's Cat |
| Albert | Camus | La Peste |
