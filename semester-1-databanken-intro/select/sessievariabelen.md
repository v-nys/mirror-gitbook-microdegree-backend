# Tussenresultaten opslaan in sessievariabelen

Wanneer een SQL-instructie een waarde vereist die door een andere query geproduceerd kan worden, kunnen sessievariabelen helpen een script eenvoudig te houden. Subqueries komen vaak van pas om één waarde te berekenen die dan gebruikt wordt in een grotere query. Wanneer we een query gebruiken om precies één waarde te produceren, noemen we die waarde een **scalar**.

Bijvoorbeeld: je wil alle personen te zien krijgen die ouder zijn dan gemiddeld. Volgende query produceert een scalar, namelijk de gemiddelde leeftijd van personen in een tabel:

```sql
select avg(Leeftijd) from Personen;
```

Je kan nu iedereen zien die ouder is dan gemiddeld door dit resultaat bij te houden in een sessievariabele.

### sessievariabelen

Een sessievariabele is vergelijkbaar met een variabele uit een _general purpose_ programmeertaal zoals C# of TypeScript. Het is met andere woorden een koppeling tussen een naam en een waarde. Je kan een sessievariabele als volgt een waarde geven:

```sql
set @gemiddeldeLeeftijd = (select avg(Leeftijd) from Personen);
```

Een sessievariabele begint **altijd** met `@`. Hiermee kan je  het volgende doen:

```sql
set @gemiddeldeLeeftijd = (select avg(Leeftijd) from Personen);
select * from Personen
where Leeftijd > @gemiddeldeLeeftijd;
```

Wanneer je verbinding met de MySQL-databank verbroken wordt, verdwijnen al je sessievariabelen.
