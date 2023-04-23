# Een React.js applicatie "Dockerizen"
Tijdens het ontwikkelproces is het gebruikelijk om `npm start` te gebruiken om een React.js-applicatie op te starten. Dit start een handige server met live reloading van de code. Wanneer een frontend echter online moet worden geplaatst, is dit type server minder geschikt. Het is niet wenselijk dat elke aanpassing meteen zichtbaar is en, omdat deze server voor ontwikkelaars geschreven is, biedt hij in bepaalde opzichten minder functionaliteit en veiligheid dan een server die geschreven is voor deployment.

De Apache web server is wel geschreven voor deployment. Deze server is uitstekend voor het hosten van statische files. HTML-pagina's in een dergelijke server kunnen gebruik maken van relatieve verwijzingen enzovoort. Een React-applicatie kan omgezet worden naar een reeks statische files via het commando `npm run build`. Dit creëert een map `build`, met daarin een productieversie van de applicatie. Deze kan in een Apache web server gehost worden. Door de Apache web server in kwestie te "Dockerizen", kan men dus een statische versie van een React.js applicatieaanbieden, die zo online geplaatst kan worden.

Een simpele `Dockerfile` om de container in kwestie te bouwen kan er dus als volgt uitzien:

```
FROM httpd:2.4
COPY ./build/ /usr/local/apache2/htdocs/
COPY httpd.conf /usr/local/apache2/conf/
```

Dit veronderstelt dat je de React-applicatie reeds lokaal gebouwd is (in dezelfde folder waar de Dockerfile zich bevindt). Het veronderstelt ook dat het configuratiebestand `httpd.conf` voor de Apache server voorzien is.