# Paginatie
In deze stap zullen we overzichtspagina's voor alle profielen en clubs maken. Omdat er veel profielen / clubs in het systeem kunnen zijn, zullen we niet meteen alle profielen en clubs inladen. In plaats daarvan zullen we gebruik maken van **paginatie**. Dit houdt in dat resultaten beetje bij beetje ingeladen worden.

![](<../.gitbook/assets/profile-overview.png>)

Om dit te realiseren, zullen we enkele nieuwe concepten introduceren:

- de clausule `LIMIT ... OFFSET ...`. Hiermee kan je een gewenst aantal resultaten verkrijgen voor een SQL-query en hoef je niet te starten vanaf het resultaat. Je kan met andere woorden vastleggen dat de eerste 10 resultaten "pagina 1" vormen, de volgende 10 resultaten "pagina 2", enzovoort.
- de `LEFT JOIN` en `RIGHT JOIN` clausules. Dit zijn uitbreidingen op de reeds behandelde `INNER JOIN`. Deze zullen van pas komen om **alle** profielen / clubs in de overzichtspagina te laten zien, terwijl toch voorrang gegeven wordt aan profielen / clubs waarmee de gebruiker al een link heeft.
