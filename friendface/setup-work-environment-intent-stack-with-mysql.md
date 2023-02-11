# Stack met MySQL
In de volgende stap willen we er voor zorgen dat er een database aanwezig is om de gegevens van FriendFace in bij te houden. We willen dat deze altijd actief is wanneer we met het project bezig zijn. Eén manier om dat te doen, zou zijn om deze in de bestaande development container voor Express.js te installeren, maar dat vereist veel systeembeheer en configuratie. Daarom zullen we gebruik maken van een tweede Docker container, die een kant-en-klare MySQL server bevat. Dit vereist dat we meerdere Docker containers automatisch opstarten wanneer we aan het project werken.

We delen dit opnieuw op in stappen:

1. Een MySQL database installeren in een gewone Docker container.
2. Connecteren met deze database via MySQL Workbench.
3. Een simpele instructie uitvoeren en bijhouden in een script.
4. Deze database server **samen** opstarten met een andere container.
5. Dit automatisch doen wanneer we FriendFace openen in Visual Studio Code.
6. Ons bestaand script automatisch laten lopen in de nieuwe database.
