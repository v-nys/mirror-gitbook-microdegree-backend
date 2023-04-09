# Clubs koppelen aan sneezes

In de volgende stap van het project zullen we er voor zorgen dat niet alleen profielen, maar ook clubs sneezes kunnen posten. Je kan dit vergelijken met hoe Facebookgroepen ook berichten kunnen posten:

![](<../.gitbook/assets/mixed-timeline.png>)

Dit zal gebeuren door een `Sneezes` te voorzien van **twee** foreign keys, waarvan ten allen tijden slechts één verschilt van `NULL`. Dit wordt afgedwongen met een aantal nieuwe concepten:

- signals
  - Dit zijn "meldingen" in MySQL die onder andere gebruikt kunnen worden wanneer er iets mis loopt.
- control flow
  - Dit ken je al van TypeScript. Het gaat hem over de MySQL-versie van `if`, `while` en `do while`.
- triggers
  - Deze vormen een manier om code in bepaalde situaties vanzelf uit te voeren. Bijvoorbeeld bij elke `INSERT` of `UPDATE` in een bepaalde tabel.

Met deze concepten zal je steeds nagaan of een sneeze **exact één** ingevulde foreign key waarde heeft. Zo niet, dan zal je een foutmelding genereren.
