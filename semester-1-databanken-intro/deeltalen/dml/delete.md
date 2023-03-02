# DELETE

Om een of meerdere **volledige rijen** uit een tabel te verwijderen (maar niet de tabel zelf), gebruiken we het `DELETE` statement.

Volgend statement verwijdert bijvoorbeeld **alle** boeken uit de tabel `Boeken` (maar laat de tabel wel staan):

```sql
/* Het aanpassen van SQL_SAFE_UPDATES is geen deel van de DELETE instructie zelf,
   maar zorgt dat MySQL ons niet "beschermt" tegen het verwijderen van data.
   Dit is niet voor alle soorten DELETE-instructies nodig, maar de reden zou ons te ver leiden. */
SET SQL_SAFE_UPDATES = 0;
DELETE
FROM Boeken;
SET SQL_SAFE_UPDATES = 1; -- dit zet de veiligheidschecks terug aan
```

Meestal willen we specifieke records verwijderen en geen volledige tabellen leegmaken. Daarom ondersteunt `DELETE` dezelfde `WHERE`-clausule als `SELECT`. Ook hier schrijf je dus een booleaanse voorwaarde en enkel de rijen waarvoor deze `TRUE` oplevert, worden gewist.

Als je geen WHERE clausule gebruikt, worden alle rijen uit de tabel verwijderd en blijft alleen de structuur van de tabel over. Wees daar dus voorzittig mee, want als de rijen gedeletet zijn, kan je ze niet meer terughalen.

De syntax van `DELETE` lijkt ook verder erg op die van `SELECT`, maar in plaats van bepaalde rijen te tonen, zal MySQL ze gewoon wissen. Je kan ook geen specifieke kolommen wissen (dat zou eerder via `UPDATE` zijn), dus je schrijft `DELETE FROM Boeken` en **niet** `DELETE * FROM Boeken` of `DELETE Voornaam FROM Boeken`.

{% hint style="info" %}
De gelijkenis tussen `SELECT` en `DELETE` is erg handig. **Voer altijd eerst een `SELECT *` uit in plaats van een `DELETE` en dan weet je steeds welke gegevens precies gewist zullen worden.**
{% endhint %}

{% hint style="danger" %}
De vergelijking van strings in MySQL is standaard **niet hoofdlettergevoelig**! Je zou dus wel eens rijen kunnen verwijderen zonder dat dat je bedoeling is.
{% endhint %}

