---
description: >-
  Docker Compose-bestanden werken door meerdere opdrachten toe te passen die
  worden gedeclareerd in een enkel docker-compose.yml-configuratiebestand.
---

# docker-compose.yml

## Docker Compose-bestandsstructuur

Nu dat je weet hoe je Docker Compose moet downloaden, moet je begrijpen hoe Compose-bestanden werken. Het is eigenlijk eenvoudiger dan het lijkt. Kortom, Docker Compose-bestanden werken door meerdere opdrachten toe te passen die worden gedeclareerd in een enkel `docker-compose.yml`-configuratiebestand.

De basisstructuur van een Docker Compose YAML-bestand ziet er als volgt uit:

```yaml
version: 'X'

services:
  app:
    build: .
    ports:
     - "3000:3000"
    volumes:
     - .:/code
  database:
    image: mysql/mysql-server:5.7
```

Laten we nu eens kijken naar een realistisch voorbeeld van een Docker Compose-bestand en het stap voor stap opsplitsen om dit allemaal beter te begrijpen. Houd er rekening mee dat alle clausules en trefwoorden in dit voorbeeld industriestandaard zijn en vaak worden gebruikt.

Met alleen deze kan je een ontwikkelingsworkflow starten. Er zijn enkele meer geavanceerde trefwoorden die je in productie kunt gebruiken, maar laten we voor nu beginnen met de belangrijke clausules.

<pre class="language-yaml"><code class="lang-yaml">version: '3'
services:
  app:
    # Pad naar dockerfile.
    # '.' vertegenwoordigt de huidige map waarin
    # docker-compose.yml aanwezig is.
    build: .

    # Mapping van containerpoort naar host
    ports:
      - "5000:5000"

    # Link database container naar app container voor bereikbaarheid.
    links:
      - "database:backenddb"
    
  database:

    # image om te halen van Docker Hub
    image: mysql/mysql-server:5.7

    # Omgevingsvariabelen voor opstartscript
<strong>    # Container zal deze variabelen gebruiken om de container te starten.
</strong>    environment:
      - "MYSQL_ROOT_PASSWORD=root"
      - "MYSQL_USER=testuser"
      - "MYSQL_PASSWORD=admin123"
      - "MYSQL_DATABASE=backend"
      
    # de databankgegevens worden opgeslagen in het volume db
    # onder de map /data/db
    volumes:
      - db:/data/db
      
# benoemde volumes die onze gegevens levend houden na opnieuw opstarten.
volumes:
  db:
</code></pre>

#### versie '3'

dit geeft aan dat we versie 3 van Docker Compose gebruiken en dat Docker de juiste functies zal bieden. Op het moment van schrijven van deze zelfstudie is versie 3.7 de nieuwste versie van Compose.

#### services

dit gedeelte definieert alle verschillende containers die we zullen maken. In ons voorbeeld hebben we twee services, **web** en **database**.

#### app en database

dit zijn de namen van onze Node-app en mySQL databank. Docker Compose maakt containers met de door ons opgegeven naam.

#### build

dit specificeert de locatie van onze Dockerfile, en . vertegenwoordigt de map waar het bestand `docker-compose.yml` zich bevindt.

#### ports

Dit wordt gebruikt om de poorten van de container toe te wijzen aan de hostmachine.

#### volumes

Een volume in Docker Compose is een mechanisme waarmee bestanden en data uit een Docker container op een permanente manier kunnen worden opgeslagen. Hierdoor blijven deze data behouden, zelfs als de container wordt verwijderd of opnieuw gebouwd. Volumes kunnen worden gedefinieerd in de `docker-compose.yml`-bestand en koppelen aan een hostmap of een externe opslagbron. Dit maakt het mogelijk om data en configuratiebestanden te delen tussen verschillende containers of tussen containers en het host-besturingssysteem.

#### links

De `links` optie in Docker Compose maakt het mogelijk om containers met elkaar te verbinden. Hiermee kunnen containers op elkaar reageren en informatie uitwisselen, wat nuttig is als je bijvoorbeeld een database in een container wilt gebruiken vanuit een andere container met een webapplicatie. De `links` optie geeft een lijst van containers waarmee de huidige container verbonden moet worden.

#### image

als we geen Dockerfile hebben en een service willen uitvoeren met een vooraf gebouwde image, specificeren we de image-locatie hier. Compose zal een image downloaden van Docker Hub van en daarvan een container aanmaken.

#### environment

De clausule stelt ons in staat om een [omgevingsvariabele](../../../express.js/authenticatie-en-autorisatie/environment-variables.md) in de container in te stellen. Dit is hetzelfde als het argument `-e` in Docker bij het uitvoeren van een container.

{% hint style="info" %}
Voor meer informatie omtrent de docker compose file, bekijk d[e officiële documentatie](https://docs.docker.com/compose/compose-file/)!
{% endhint %}
