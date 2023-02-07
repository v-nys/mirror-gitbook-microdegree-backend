---
description: De voornaamste docker compose commands
---

# docker compose commands

Nu we weten hoe we een docker-compose-bestand moeten maken, gaan we de meest voorkomende Docker Compose-opdrachten bekijken die we met onze bestanden kunnen gebruiken. Houd er rekening mee dat we alleen de meest gebruikte commando's zullen bespreken.

### docker-compose

`docker-compose`: Elke Compose-opdracht begint met deze opdracht. Je kan ook `docker-compose --help` gebruiken om aanvullende informatie over argumenten en implementatiedetails te geven.

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### docker-compose build

`docker-compose build`: Deze opdracht bouwt afbeeldingen in het bestand docker-compose.yml. De taak van de opdracht build is om de afbeeldingen gereed te maken om containers te maken, dus als een service de vooraf gebouwde afbeelding gebruikt, wordt deze service overgeslagen.
