# UPDATE

## Basisprincipe

Soms maken we fouten bij het ingeven van data. Soms verouderen gegevens. In beide situaties willen we bestaande rijen wel bewaren, maar bepaalde kolomwaarden aanpassen. We kunnen het `UPDATE` statement hier voor gebruiken.

Bijvoorbeeld:

```sql
/* Het aanpassen van SQL_SAFE_UPDATES is geen deel van de UPDATE instructie zelf,
   maar zorgt dat MySQL ons niet "beschermt" tegen het aanpassen van data.
   Dit is niet voor alle soorten UPDATE-instructies nodig, maar de reden zou ons te ver leiden. */
SET SQL_SAFE_UPDATES = 0;
UPDATE Boeken SET Categorie = 'Metafysica';
SET SQL_SAFE_UPDATES = 1;
```

Dit zet de kolom `Categorie` van **alle** boeken op "Metafysica".

Je kan ook de inhoud van meer dan één kolom aanpassen. Dat zou je als volgt doen:

```sql
UPDATE Boeken 
SET Categorie = 'Wetenschap', 
    Titel = 'Een boek';
```

Zonder verdere specificatie zet het eerste stukje code de kolom `Categorie` van alle rijen op "Metafysica".

## Verfijnd aanpassen

Het zou kunnen dat alle boeken in de categorie "Metafysica" thuishoren. En in dat geval doet het statement precies wat je er van verwacht. Maar meestal willen wie niet alle rijen op dezelfde manier aanpassen. We moeten dus in het UPDATE statement specifiëren in welke rij we de kolom `Categorie` willen updaten. We moeten één bepaalde rij eruit filteren. Dat doen we met de `WHERE` clausule. We beperken de update tot de records die we met een SELECT zouden laten zien:

```sql
UPDATE Boeken
SET Categorie = 'Wiskundige logica'
WHERE Titel = 'Logicaboek';
```

De `WHERE` clausule werkt hier net hetzelfde als bij de `SELECT`-instructie. In de clausule staat een booleaanse expressie. Als die expressie in de context van een rij `TRUE` oplevert, wordt de aanpassing doorgevoerd. Anders niet.

{% hint style="danger" %}
De vergelijking van strings in MySQL is standaard **niet hoofdlettergevoelig**! Je zou dus wel eens rijen kunnen aanpassen zonder dat dat je bedoeling is.
{% endhint %}

## Aanpassen in functie van bestaande data

Waar je een nieuwe waarde instelt, mag je ook weer een expressie gebruiken die een waarde oplevert. Je kan bijvoorbeeld een waarde instellen die berekend wordt door strings aan elkaar te hangen of een substring te bepalen:

```sql
/* CONCAT plakt tekst aan elkaar
   het tweede argument, Categorie, staat niet tussen quotes
   dus de tekst "Categorie: " wordt voor de reeds ingevulde categorie geplaatst
   het eindresultaat wordt bijvoorbeeld 'CATEGORIE: Wetenschap' */
UPDATE Boeken SET Categorie = CONCAT('CATEGORIE: ', Categorie);
/* ander voorbeeld:
   iedereen krijgt er op 1 januari een jaar anciënniteit bij */
UPDATE Werknemers SET Ancienniteit = Ancienniteit + 1;
```
