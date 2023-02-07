---
description: >-
  Een Dockerfile is een scriptbestand dat de stappen bevat die nodig zijn om een
  Docker image te bouwen.
---

# Dockerfile

## Wat is een Dockerfile?

Een Dockerfile is een scriptbestand dat de stappen bevat die nodig zijn om een Docker image te bouwen. Het is een tekstbestand met specifieke opdrachten die door Docker worden uitgevoerd om de Docker image op te bouwen en te configureren.

Een Dockerfile bevat informatie over de basisimage waarop de Docker image gebouwd wordt, de software en bibliotheken die moeten worden geïnstalleerd, de configuratie-instellingen die moeten worden toegepast en de commands die moeten worden uitgevoerd bij het opstarten van een Docker container.

De Dockerfile is essentieel voor het automatiseren van het bouwproces van Docker images en garandeert dat de Docker image altijd op dezelfde manier wordt gebouwd, ongeacht de machine waarop het draait of de ontwikkelomgeving.

### Voorbeeld van een Dockerfile

{% code title="Dockerfile" %}
```docker
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node message.js
```
{% endcode %}

#### Hier is wat de verschillende regels in het Dockerfile doen:

1. `FROM node:alpine`: Deze regel specificeert welke basis-image gebruikt moet worden voor de container. In dit geval wordt het '[node:alpine](https://hub.docker.com/\_/node)'-image gebruikt, wat een kleine en lichtgewichtte distributie van Node.js is gebaseerd op de Alpine Linux-distributie.
2. `COPY . /app`: Deze regel kopieert alle bestanden en mappen uit de huidige directory naar de `/app` directory in de container. Dit betekent dat alle bestanden uit de huidige directory (waarin de Dockerfile zich bevindt) zullen worden gekopieerd naar de `/app` directory in de container.
3. `WORKDIR /app`: Deze regel stelt de standaard werkdirectory in voor de container op `/app`. Dit betekent dat elke opdracht die uitgevoerd wordt binnen de container uitgevoerd zal worden vanuit de `/app` directory.
4. `CMD node message.js`: Deze regel specificeert de opdracht die uitgevoerd moet worden wanneer de container opgestart wordt. In dit geval wordt het `node` commando uitgevoerd met `message.js` als argument, wat betekent dat de `message.js`-applicatie uitgevoerd zal worden bij het opstarten van de container.

Dus in het algemeen, bouwt de Dockerfile een Docker-container die de Node.js-applicatie bevat en deze uitvoert wanneer de container opgestart wordt.
