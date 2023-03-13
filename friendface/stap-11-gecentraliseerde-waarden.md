# Stap 11: gecentraliseerde waarden
Momenteel hebben we overal in onze code hardgecodeerde waarden die gekppeld zijn aan de configuratie van ons systeem: wachtwoorden, gebruikersnamen,...

In de praktijk wordt dit anders gedaan. Hardgecodeerde waarden zorgen ervoor dat we onze software niet kunnen aanpassen aan verschillende omgevingen, zoals ontwikkeling tegenover productie. Bovendien maken ze gevoelige informatie zichtbaar in de code.

Het is beter informatie zoals gebruikersnamen, wachtwoorden, URL's voor diensten,... bij te houden in een bestand met omgevingsvariabelen. Dit bestand wordt niet onder versiebeheer geplaatst, zodat de logica van de code gescheiden is van gevoelige informatie over een deployment.
