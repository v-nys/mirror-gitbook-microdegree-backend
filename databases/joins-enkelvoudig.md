# JOINs bij simpele relaties

Integriteit en performantie worden gegarandeerd door de database te "normaliseren". Dit wil in eerste instantie zeggen: "efficiënt uitsplitsen over tabellen". Door normalisering raakt informatie echter verspreid. Uitgebreide voorstellingen worden vervangen door *foreign key* kolommen. De gebruiker heeft daar niet veel aan. Primaire en vreemde sleutels zeggen de gebruiker niets. Anders gesteld, een tabel vol getallen zoals onderaan op [de pagina over primary keys](../semester-1-databanken-intro/deeltalen/ddl/sleutels-voor-identificatie.md) is op zich niet leesbaar. Er is dus een manier nodig om de informatie voor te stellen alsof die uit één tabel komt.

## CROSS JOIN

De eerste manier om data uit meerdere tabellen te combineren tot data die uit één tabel lijkt te komen, is de "cross join". Deze combineert elke rij uit tabel A met elke rij uit tabel B. Veronderstel bijvoorbeeld volgende tabellen om taken en personen voor te stellen:

| omschrijving         | Id |
| -------------------- | -- |
| bestek voorzien      | 1  |
| frisdrank meebrengen | 2  |
| aardappelsla maken   | 3  |

| voornaam | Id | Taken\_Id |
| -------- | -- | --------- |
| Yannick  | 1  | 2         |
| Bavo     | 2  | 1         |
| Max      | 3  | 3         |

Deze kunnen we op deze manier combineren en tonen:

```sql
SELECT *
FROM Taken
CROSS JOIN Leden
ORDER BY Taken.Id, Leden.Id;
```

Dit levert dan een resultaat dat er als volgt uitziet:

| omschrijving         | Taken.Id | voornaam | Leden.Id | Taken\_Id |
| -------------------- | -------- | -------- | -------- | --------- |
| bestek voorzien      | 1        | Yannick  | 1        | 2         |
| bestek voorzien      | 1        | Bavo     | 2        | 1         |
| bestek voorzien      | 1        | Max      | 3        | 3         |
| frisdrank meebrengen | 2        | Yannick  | 1        | 2         |
| frisdrank meebrengen | 2        | Bavo     | 2        | 1         |
| frisdrank meebrengen | 2        | Max      | 3        | 3         |
| aardappelsla maken   | 3        | Yannick  | 1        | 2         |
| aardappelsla maken   | 3        | Bavo     | 2        | 1         |
| aardappelsla maken   | 3        | Max      | 3        | 3         |

Er zijn hier 9 rijen, want elk van de drie rijen uit de eerste tabel kan gecombineerd worden met elk van de drie rijen uit de tweede. Niet elke combinatie is zinvol. De interessante rijen zijn die, die een persoon koppelen aan een toegewezen taak. Dat zijn de rijen waarin `Taken.Id` gelijk is aan `Taken_Id` (afkomstig uit `Leden`).

{% hint style="info" %}
Vergelijk dit met het systeem dat wordt toegepast in een vestiaire. Elke bezoeker kan elk kledingstuk opvragen, maar er mag enkel een koppeling gemaakt worden wanneer de bezoeker hetzelfde getal kan voorleggen dat ook op het kledingstuk gehangen is.
{% endhint %}

Je kan dus personen koppelen aan hun taak via:

```sql
SELECT *
FROM Taken
CROSS JOIN Leden
WHERE Taken.Id = Taken_Id;
```

Hier moet je `Taken.Id` schrijven omdat zowel `Taken` als `Leden` een kolom `Id` hebben. Door de tabelnaam toe te voegen, maak je duidelijk over welke kolom het precies gaat.

{% hint style="info" %}
Een andere schrijfwijze voor `FROM Taken CROSS JOIN Leden` is `FROM Taken, Leden`. Dit kan je misschien tegenkomen, maar in deze tekst wordt de explicietere schrijfwijze verkozen.
{% endhint %}

## INNER JOIN

Dit laatste voorbeeld werkt in MySQL, maar het wordt typisch anders geschreven. Meestal zal `CROSS JOIN` vervangen worden door `INNER JOIN`, terwijl `WHERE` vervangen wordt door `ON`. Wanneer we twee tabellen willen koppelen zodat **samenhorende** rijen uit tabel A en tabel B één nieuwe rij opleveren, zullen we deze conventie volgen.

Het resultaat zal er dus zo uitzien:

```sql
SELECT *
FROM Taken
INNER JOIN Leden
ON Taken.Id = Taken_Id;
```

Het resultaat is hetzelfde, maar in dit scenario wordt `INNER JOIN` verkozen. `ON` geen zuiver synoniem voor `WHERE`, want het kan alleen gebruikt worden in een `JOIN`-statement.
