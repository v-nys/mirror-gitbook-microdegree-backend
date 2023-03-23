# VARIABELEN

Een variabele dient om data via een naam te kunnen aanspreken. Binnen een stored program is het mogelijk om variabelen te declareren.

## DECLARE

Een variabele declareer je als volgt.

```sql
DECLARE naam_variabele datatype [DEFAULT default_waarde];
```

De mogelijke datatypes zijn dezelfde als die voor kolommen, bv. `INT`, `DATE`, `VARCHAR(100)`, enz.

{% hint style="warning" %}
Je kan een variabele **alleen** declareren vlak na een `BEGIN` \(of na declaratie van een andere variabele\) van een stored program. Dat is geen probleem, want je kan hem wel nog van waarde veranderen na andere statements.
{% endhint %}

## SCOPE

Zoals ook het geval bij programmeertalen heeft een variabele een bepaalde "scope", dus een bereik of levensduur. Een variabele die binnen een stored program is gedeclareerd zal niet meer bruikbaar zijn wanneer het `END` statement wordt bereikt. Dit stemt overeen met een lokale variabele in een algemene programmeertaal: de variabele **bestaat enkel binnen die uitvoering van de body**.

Een variabele die met het @-symbool begint is een **sessievariabele**. Deze is beschikbaar zolang de sessie \(verbinding met de DB, bijvoorbeeld via Workbench\) niet is beëindigd en je hoeft hem niet te declareren. Dit stemt ruwweg overeen met een globale variabele in een algemene programmeertaal. Daarom gebruiken we variabelen zonder `@` waar we kunnen en enkel variabelen met `@` wanneer lokale scope te begrensd is.

### Waarden geven

Je kan een variabele een waarde geven op twee manieren:

* via `SELECT <uitdrukking> FROM <TABEL> INTO <naam variabele>`
  * de `SELECT` mag subclausules zoals `FROM`, `WHERE`,... bevatten
  * je mag de `INTO` ook voor de `FROM` zetten
* via `SET <variabele> = <waarde>`

## VOORBEELD

```sql
USE `aptunes`;
DROP procedure IF EXISTS `GetAantalLidmaatschappen`;

DELIMITER $$
CREATE PROCEDURE `GetAantalLidmaatschappen` ()
BEGIN
    DECLARE TotaalLidmaatschap INT DEFAULT 0;
    SELECT COUNT(*)
    INTO TotaalLidmaatschap
    FROM Lidmaatschappen;
    SELECT TotalLidmaatschap;
END$$

DELIMITER ;
```

Hierbij declareren we een \(lokale\) `INT` variabele `TotaalLidmaatschap`, die we dan een waarde geven met het uitvoeren van het SQL-statement, waarna de inhoud van deze variabele via de tweede `SELECT` wordt geselecteerd. Je hebt de variabele niet nodig voor deze taak, maar het voorbeeld toont de syntax.
