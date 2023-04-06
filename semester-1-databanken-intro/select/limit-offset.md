# Gegevens segmenteren
Wanneer de volledige resultatenset van een query groter dan gewenst is,
kan het keyword `LIMIT` gebruikt worden om de set te beperken tot een kleiner aantal elementen.

## Basis
Veronderstel bijvoorbeeld een database die een bloggingplatform ondersteunt.
Volgende query zou alle posts kunnen tonen:

```sql
SELECT * FROM Posts;
```

Oudere posts zijn waarschijnlijk minder relevant. Via `LIMIT` kan het aantal posts beperkt worden tot pakweg 10:

```sql
SELECT * FROM Posts LIMIT 10;
```

De 10 recentste posts kunnen verkregen worden door dit te combineren met de `ORDER BY`-constructie:

```sql
SELECT * FROM Posts ORDER BY PostDate DESC LIMIT 10;
```

De `LIMIT` wordt dus pas op het einde toegepast om het aantal resultaten te beperken.

## Offset
Een "offset" is een "verschuiving" van de resultaten. Deze komt van pas om de resultatenset te beperken, maar niet tot de **eerste** resultaten.

Bijvoorbeeld:

```sql
SELECT * FROM Posts
LIMIT 5, 10;
```

Dit toont posts 6 tot en met 15. Dat komt omdat de eerste vijf posts genegeerd worden en de volgende 10 geselecteerd worden. Een alternatieve schrijfwijze is `LIMIT 10 OFFSET 5`. Let op: hier is de volgorde omgekeerd ten opzichte van de schrijfwijze hierboven.

### Toepassing: paginatie
Een offset wordt vaak gebruikt om "paginatie" te realiseren. Dit wil zeggen dat een zoekopdracht niet meteen alle resultaten te zien krijgt, maar slechts een beperkt aantal resultaten per pagina. Hierbij wordt het paginanummer - 1 vermenigvuldigd met het aantal resultaten per pagina om de offset te bepalen.
