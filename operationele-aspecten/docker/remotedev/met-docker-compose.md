# Remote development container met meerdere actieve containers
In het eenvoudigste scenario gebruik je een development container om code in te schrijven en te testen. Dit heeft zijn beperkingen: indien je applicatie beroep doet op diensten zoals een database, zou je de database in de development container moeten installeren. Zo gaat je ontwikkelomgeving sterk afwijken van je productieomgeving en zo moet je complexe images bouwen.

Een beter alternatief bestaat erin de mogelijkheden van Docker Compose te benutten in combinatie met een remote development container. Dit lijkt sterk op werken met een Dockerfile, maar er zijn enkele verschillen:

- in `devcontainer.json`:
  - heb je geen property `build` nodig, maar wel een property `dockerComposeFile`, met als waarde de naam van je Docker Compose file, relatief ten opzichte van `devcontainer.json`
  - heb je een property `service` nodig met als waarde de naam van de "primaire" service
    - bijvoorbeeld, als je een service `app` in `docker-compose.yml` hebt, is deze waarde `app`
  - heb je een property `workspaceFolder` nodig die aangeeft waar in het bestandensysteem van de container je lokale bestanden moeten staan. Typisch is dit iets zoals `/workspace/${localWorkspaceFolderBasename}`, zodat je in je container een map `workspace` hebt met daarin een map met dezelfde naam als je lokale projectmap.
  - moet je `forwardPorts` aanvullen met entries van de vorm `secondaryService:portNumber`. `secondaryService` is hier de naam van een andere service dan de eerder vermelde (voor de primaire service mag je gewoon het nummer geven). `portNumber` is het poortnummer dat je zichtbaar wenst te maken op je lokale machine.
    - **dit is zelfs nodig als je een onderdeel `ports` hebt voorzien in `docker-compose.yml`!**
- in `docker-compose.yml`
  - moet je je bestanden ergens in de primaire container zichtbaar maken
    - dit doe je door de `volumes` property een waarde te geven
      - je kan best de parent folder (of, afhankelijk van je setup, nog een verdere voorouder) afbeelden op een folder `/workspace` of iets dergelijks
  - moet je zorgen dat je primaire container niet automatisch afsluit
    - je kan bijvoorbeeld `command: sleep infinity` toevoegen
