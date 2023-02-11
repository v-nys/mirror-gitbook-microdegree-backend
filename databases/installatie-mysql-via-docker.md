# Installatie MySQL via Docker

Er bestaan verschillende manieren om MySQL te installeren en ze kunnen leiden tot licht verschillend gedrag van het DBMS. Om te garanderen dat dit gedrag *niet* afhankelijk is van jouw setup, geven we hier de procedure voor een installatie binnenin een Docker container. Elke dergelijke installatie zal zich identiek hetzelfde gedragen als elke andere installatie (van dezelfde versie) in een Docker container.

## Eerste opstart
Om een nieuwe container met naam `some-mysql` op te starten, met gebruiker `root`, wachtwoord `my-secret-pw` en toegang via poort 3306, gebruik je: `docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:8.0.32`.

## Herstarten
Als je je container hebt afgesloten (bijvoorbeeld via `docker container stop` of gewoon door je systeem af te sluiten) kan je hem herstarten via `docker container start some-mysql` (omdat `some-mysql` de naam van de container is).

## Bron
Deze instructies zijn een korte samenvatting van de informatie op [Docker hub](https://hub.docker.com/_/mysql).
