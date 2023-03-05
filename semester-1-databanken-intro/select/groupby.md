# SELECT met GROUP BY

Eerst hebben we een relationele databank vooral gebruikt om individuele records bij te houden en op te vragen. Via aggregaatfuncties hebben we informatie over alle records gebundeld. Soms zoeken we iets dat in het midden ligt: informatie die niet handelt over individuele records, maar over groepen records. Typisch zijn dit records met dezelfde waarde in bepaalde velden. De oplossing schuilt in een `GROUP BY` clausule.

## basisidee

Met de GROUP BY operator kan je rijen "samenpersen" en de gewenste informatie uit de samengeperste rijen halen. Dit "samenpersen" gebeurt eerst, voor de gewenste informatie wordt geselecteerd. Beeld je in dat er een tussenliggende tabel wordt aangemaakt op basis van de tabel waarin je wenst te zoeken.

Veronderstel dat je onderstaande tabel `Honden` hebt:

| naam    | leeftijd | geslacht   |
| ------- | -------- | ---------- |
| Ming    | 10       | mannelijk  |
| Swieber | 14       | mannelijk  |
| Misty   | 7        | vrouwelijk |

Informatie die over groepen records gaat, kan dan zijn: "hoeveel mannelijke honden zijn er in het systeem?" of "wat is de gemiddelde leeftijd per geslacht?" Deze vragen kan je beantwoorden met behulp van `GROUP BY`. `Honden GROUP BY Honden.Geslacht` moet je zien als een tijdelijke tabel die er als volgt uitziet:

| namen per geslacht | leeftijd per geslacht | geslacht   |
| ------------------ | --------------------- | ---------- |
| \[Ming,Swieber]    | \[10,14]              | mannelijk  |
| \[Misty]           | \[7]                  | vrouwelijk |

{% hint style="warning" %}
Je moet dit enkel zien als een hulpmiddel om over `GROUP BY` na te denken! Je kan deze tussenliggende tabel niet zomaar tonen.
{% endhint %}

De kolom na `GROUP BY` neemt geen nieuwe vorm aan, maar komt in de resultaten nog één keer voor per waarde. Er is dus precies één rij met de waarde `"mannelijk"` en één rij met de waarde `"vrouwelijk"`. De andere kolommen veranderen eigenlijk van datatype: de kolom voor de naam bevat een sequentie van `VARCHAR(50)` per rij in plaats van een `VARCHAR(50)` per rij. De kolom voor de leeftijd bevat een sequentie van getallen in plaats een getal per rij. Dit is hier aangegeven door de verschillende waarden tussen rechte haakjes te zetten, **maar een gewone `SELECT` zal dit niet tonen**. Er is gekozen voor deze notatie omdat dit lijkt op het gebruik van lijsten in de meeste programmeertalen. De kolom voor het geslacht bevat nog steeds één waarde `"mannelijk"` of `"vrouwelijk"`, want op deze waarde is gegroepeerd.

Je kan bij gebruik van `GROUP BY` de data **die in het voorbeeld tussen rechte haakjes staat** niet rechtstreeks tonen. Je kan er wel een aggregatiefunctie op toepassen. Als je wil weten wat de gemiddelde leeftijd per geslacht is, schrijf je dit:

```sql
SELECT AVG(Leeftijd), Geslacht
FROM Honden
GROUP BY Geslacht;
```

Als je `GROUP BY` gebruikt, wordt een aggregatiefunctie dus **niet meer over heel de kolom** toegepast, maar per groep. `Geslacht` mag je wel rechtstreeks tonen want daar heb je op gegroepeerd, dus die data staan niet tussen rechte haakjes.

Een speciaal geval is `COUNT(*)`. Dit vertelt je hoe veel elementen er gegroepeerd zijn.

```sql
SELECT COUNT(*), Geslacht
FROM Honden
GROUP BY Geslacht;
```

De tussenliggende tabel is een hulpmiddel om hierover na te denken; volgende code zou niet werken:

```sql
SELECT Leeftijd
FROM Honden
GROUP BY Geslacht;
```

Ze levert: "Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'ApDB.Honden.Leeftijd' which is not functionally dependent on columns in GROUP BY clause". Het probleem is dus dat je data groepeert en dan geen aggregatiefunctie toepast op de data die in het voorbeeld hierboven tussen rechte haakjes wordt getoond.

Je ziet dit duidelijk als je de `GROUP_CONCAT` functie toepast. Dit is een aggregatiefunctie die alles in één groep omzet naar een string. Hiermee kan je dus bovenstaand hulpmiddel wel visueler maken. Bijvoorbeeld:

```sql
SELECT GROUP_CONCAT(Leeftijd)
FROM Honden
GROUP BY Geslacht;
```

{% hint style="warning" %}
Bovenstaande foutmelding zal je vroeg of laat zeker op je scherm krijgen. Lees dan aandachtig over welke kolom het gaat en teken dan voor jezelf uit wat wel gegroepeerd wordt.
{% endhint %}

## uitbreiding: meerdere expressies

`GROUP BY` hoeft niet gevolgd te worden door één kolom, maar kan door **een opeenvolging van expressies** gevolgd worden. In dat geval groepeer je records **per unieke combinatie** van uitgerekende waarden. Je kan bijvoorbeeld dit doen:

```sql
SELECT COUNT(*), Geslacht, Leeftijd
FROM Honden
GROUP BY Geslacht, Leeftijd
ORDER BY Leeftijd, Geslacht;
```

Dit toont je hoeveel mannelijke en hoeveel vrouwelijke honden er zijn van elke leeftijd die in het systeem voorkomt. Er zijn na uitvoering van het calibratiescript bijvoorbeeld 6 vrouwelijke honden van 1 jaar oud en 4 mannelijke honden van 1 jaar oud. We kunnen ter controle ook dit even doen:

```sql
SELECT COUNT(*), Leeftijd
FROM Honden
GROUP BY Leeftijd;
```

Dit toont ons dat er 10 (dus 6 vrouwelijke en 4 mannelijke) honden zijn van 1 jaar oud. Anders gezegd: hoe meer kolommen je vermeldt na `GROUP BY`, hoe meer onderverdelingen je zal zien.

Meestal groeperen we op basis van kolommen, maar dat hoeft helemaal niet. Volgende code toont bijvoorbeeld hoe veel honden een naam hebben die begint met 'A', 'B', 'C',...

```sql
SELECT COUNT(*), LEFT(Naam,1)
FROM Honden
GROUP BY LEFT(Naam,1);
```

Per hond bepalen we de eerste letter. Alle honden met dezelfde uitkomst voor `LEFT(Naam,1)` worden in een eigen groepje gezet.
