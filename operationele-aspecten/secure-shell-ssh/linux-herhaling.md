# Linux (Herhaling)

Als je op een server werkt via SSH, ben je verbonden met een command line interface in een Linux-besturingssysteem. Dit betekent dat je de opdrachten van het besturingssysteem rechtstreeks kunt invoeren in de terminal, om taken uit te voeren en om de server te beheren.

Als je niet bekend bent met de Linux-commando's en hun functies, kan het werken via de terminal in het begin een uitdaging zijn en kan het ook fouten veroorzaken. Het kennen van de commando's en hun toepassingen zal je helpen om taken efficiënter en effectiever uit te voeren, en zal je ook in staat stellen om problemen op te lossen en fouten te vinden wanneer deze zich voordoen.

Om effectief te kunnen werken op een server via SSH, is het daarom essentieel om de basisbeginselen van Linux-commando's te begrijpen en te kennen. Dit omvat taken uitvoeren zoals het maken van mappen, bestanden kopiëren of verplaatsen, bestanden bewerken, beheerdersrechten verkrijgen en beheren van services op de server. Bovendien kun je met de commando's scripts en geautomatiseerde taken schrijven om het beheer van de server te vereenvoudigen.

Daarnaast zijn Linux-commando's over het algemeen draagbaar en beschikbaar op verschillende Linux-distributies en servers, wat betekent dat als je eenmaal de commando's kent, je ze op elke Linux-server kunt gebruiken zonder dat je je zorgen hoeft te maken over specifieke verschillen tussen distributies!

| Commando         | Betekenis               | Omschrijving                                                                                                                   |
| ---------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| pwd              | Print working directory | Toont de werkmap waarin je zich bevindt.                                                                                       |
| cd `arg`         | Change directory        | Hiermee kan je de werkmap wijzigen in de ingevoerde map, ter vervanging van `arg`.                                             |
| cd `..`          | Change directory        | Hiermee kan je de werkmap wijzigen, een niveau hoger in de boomstructuur van je mappen.                                        |
| cd               | Change directory        | Als je geen argument opgeeft, kan je naar de hoofdmap van je server (home) navigeren.                                          |
| ls               | List                    | Geeft de inhoud van je werkmap weer.                                                                                           |
| mkdir `arg`      | Make directory          | Hiermee kan je een map aanmaken. Het argument (`arg`) is de naam van de map.                                                   |
| touch `arg`      | Touch                   | Maakt een leeg bestand aan met de naam die wordt genoemd in het `arg`-argument, als er nog geen bestand met deze naam bestaat. |
| rm `arg`         | Remove                  | Verwijdert het bestand dat wordt genoemd in het `arg`-argument.                                                                |
| rm -r `arg`      | Remove                  | Verwijdert de map die als `arg`-argument wordt genoemd, evenals de volledige inhoud ervan, recursief.                          |
| mv `arg1` `arg2` | Move                    | Hernoemt of verplaatst een element (gespecificeerd als `arg1`) naar een nieuwe plek (gespecificeerd als `arg2`).               |
