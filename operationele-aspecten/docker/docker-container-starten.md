# docker container starten

## Starten van een docker container

Om een Docker-container uit te voeren, heb je een Docker-image nodig. Dit is het sjabloon dat de broncode, bibliotheken, afhankelijkheden, tools en andere bestanden bevat die nodig zijn om een container te laten werken. Je kan een Docker-image maken met behulp van een [Dockerfile](https://docs.docker.com/engine/reference/builder/) en de [docker build commando](https://docs.docker.com/get-started/02\_our\_app/), of je kan een image uit een register halen, zoals [Docker Hub](https://hub.docker.com/).

In deze zelfstudie zal je gebruik maken van de image "[denising/hallo-student](https://hub.docker.com/repository/docker/denising/hallo-student/)" dat terug te vinden is op Docker Hub.

Je kan de commando `docker run` gebruiken om een container uit te voeren. De commando [`docker run`](https://docs.docker.com/engine/reference/run/) heeft de volgende syntaxis:

```docker
## Syntaxis
docker run [options] IMAGE [COMMAND] [ARG...]
```

### Stap 1: download een image van Docker Hub

Het commando `docker images` geeft een lijst weer met de lokaal geïnstalleerde docker images.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

In dit voorbeeld zal je de image denising/hallo-student binnenhalen (van Docker Hub) met behulp van het commando `docker pull`. Kopieer de code hieronder en plak het in je terminal:

```docker
docker pull denising/hallo-student:latest
```

Als je nu opnieuw `docker images` uitvoert zal je zien dat denising/hallo-student er tussen staat.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Je kan je lokale images ook raadplegen in Docker Desktop -> Images.
{% endhint %}

### Stap 2: Aanmaken en uitvoeren van een container

Je kan een container aanmaken en uitvoeren met behulp van het commando `docker run`. Maak een container aan en voer deze uit door de onderstaande code te kopiëren naar je terminal:

```docker
docker run -p 3000:3000 denising/hallo-student
```

* `docker run` is het commando om een nieuwe container te starten
* `-p 3000:3000` is de optie voor het doorgeven van een poort, in dit geval wordt poort 3000 op de host doorgestuurd naar poort 3000 in de container.
* `denising/hallo-student` is de naam van de container-image die je wilt opstarten.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

#### docker/getting-started

Als je `docker run` uitvoert vooraleer je een image lokaal hebt binnengehaald met `docker pull`, zal docker automatisch gaan kijken op [Docker Hub](https://hub.docker.com/) indien de image bestaat en deze downloaden.

Start een nieuwe container op voor de image [docker/getting-started](https://hub.docker.com/r/docker/getting-started). Kopieer de onderstaande code uit in je terminal:

```
docker run -d -p 80:80 docker/getting-started
```

* `-d` is de optie voor detached mode, waarbij de container op de achtergrond wordt uitgevoerd.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Stap 3: verwijderen van een container

Het commando `docker ps -a` geeft een lijst weer van al je containers.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Indien je een container wilt verwijderen kan je het commando `docker rm CONTAINER_NAME` of `docker rm CONTAINER_ID` gebruiken.

Verwijder de container dat de image van denising/hallo-student gebruikt. Je kan de naam van je container terug vinden in de laatste kolom.

```docker
docker rm admiring_williamson
```

<figure><img src="../../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>

### Bronnen

* [https://tecadmin.net/docker-run/](https://tecadmin.net/docker-run/)
* [https://docs.docker.com/get-started/04\_sharing\_app/](https://docs.docker.com/get-started/04\_sharing\_app/)
