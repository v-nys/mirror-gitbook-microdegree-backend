# Remote development containers
Containers lossen, omdat ze reproduceerbaar zijn, veel oude problemen met systeemspecifieke configuratie op. Een recente evolutie is het gebruik van containers niet alleen voor de applicatie zelf, maar ook voor de ontwikkelomgeving. De voordelen hiervan zijn vergelijkbaar: om aan een project te werken, is het niet langer nodig dat een ontwikkelaar zijn IDE tot in de puntjes configureert, allerlei ondersteunende software installeert, enzovoort.

De koploper op dit gebied is de **Remote Development** extensie voor Visual Studio Code. Deze plugin staat je als ontwikkelaar toe te connecteren met een container en in deze container te werken alsof Visual Studio Code er op geïnstalleerd was. Bovendien kan je vastleggen welke plugins en dergelijke voorzien zijn wanneer je op deze manier met een container connecteert. Ten slotte, omdat containers *portable* zijn, kan je je volledige ontwikkelomgeving "meenemen" naar een andere machine door gewoonweg de nodige configuratiebestanden (`devcontainer.json` en eventuele `Dockerfile` en/of `docker-compose.yml`) te kopiëren.

![Animatie Microsoft](https://microsoft.github.io/vscode-remote-release/images/remote-containers-readme.gif)

Om gebruik te maken van deze extensie, moet je ze eerst installeren. De snelste manier is door in Visual Studio Code de snelkoppeling Ctrl+P te gebruiken en dan het volgende in te plakken: `ext install ms-vscode-remote.remote-containers`

## Meer informatie
- [Pluginpagina Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
