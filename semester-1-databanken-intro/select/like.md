# LIKE

In veel gevallen weten we maar bij benadering wat we willen zoeken. We kennen een deel van de naam, het begin of het einde of iets tussenin. Met de `LIKE` operator kan je in SQL naar patronen zoeken. Dit wordt ook wel **pattern matching** genoemd. Je kan met de `LIKE` operator naar patronen in tekst zoeken. Je combineert de `LIKE` operator met jokers (**wildcards**) om een booleaanse expressie te vormen, dus om `TRUE`, `FALSE` of `NULL` te produceren. De set van jokers bestaat uit symbolen die één of meer ontbrekende tekens voorstellen.

De LIKE operator vergelijkt een tekstuitdrukking in het linkerlid met een patroon tussen aanhalingstekens in het rechterlid. Een patroon is een veralgemeende tekstuitdrukking. d.w.z. een tekst waarin nog enige vrijheid bestaat.

De betekenis van de wildcards in SQL is als volgt:

* `%`: nul, één of meer willekeurige tekens
* `_`: exact één willekeurig teken

Om alle boeken te selecteren waarvan de familienaam van de auteur begint met B:

```sql
SELECT Voornaam, Familienaam, Titel
FROM Boeken
WHERE Familienaam LIKE 'B%';
```

Om alle boeken te selecteren waarvan de familenaam van de auteur eindigt op een s:

```sql
SELECT Voornaam, Familienaam, Titel
FROM Boeken
WHERE Familienaam LIKE '%s';
```

Om boeken waarvoor in de titel het woord economie voorkomt, te selecteren:

```sql
SELECT Voornaam, Familienaam, Titel, Verschijningsjaar
FROM Boeken
WHERE Titel LIKE '%economie%';
```

{% hint style="warning" %}
De `LIKE` wordt door beginners vaak vergeten. Je komt soms dingen tegen als `WHERE Voornaam = 'Ma%ijs'`. Dat zal geen resultaten opleveren, want niemand heeft letterlijk de voornaam "Ma%ijs". `WHERE Voornaam LIKE 'Ma%ijs'`, daarentegen, zal je iedereen met de voornaam `Matijs`, `Mathijs` of `Mattijs` opleveren.
{% endhint %}
