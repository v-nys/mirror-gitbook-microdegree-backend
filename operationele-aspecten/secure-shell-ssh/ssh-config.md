# SSH config

Als je regelmatig verbinding maakt met meerdere externe systemen via SSH, zal je merken dat het moeilijk is om alle externe IP-adressen, verschillende gebruikersnamen, niet-standaardpoorten en verschillende commando's te onthouden.

## Wat is een ssh-configuratiebestand?

Een ssh-configuratiebestand is een tekstbestand dat al je ssh-verbindingsinformatie bevat. Dit omvat de hostnaam van de server waarmee je verbinding maakt, de gebruikersnaam die je gebruikt om verbinding te maken, het poortnummer en het protocol dat je wilt gebruiken. Je kan ook een sleutelbestand specificeren om te gebruiken voor authenticatie, evenals andere opties.

### Waarom zou ik een SSH-configuratiebestand gebruiken?

Het gebruik van een SSH-configuratiebestand heeft veel voordelen. Enkele van de meest voorkomende voordelen zijn:

* **Consistente instellingen op alle servers** – Dit maakt het gemakkelijk om je instellingen consistent te houden op al je servers. Je kan afzonderlijke configuraties maken voor elke server waarmee je verbinding maakt, of je kan algemene configuraties maken die van toepassing zijn op alle servers.
* **Eenvoudige configuratie voor meerdere verbindingen** – Je kan voor elke situatie afzonderlijke configuraties maken, zodat je eenvoudig verschillende instellingen voor verschillende situaties kunt opgeven. Je kan bijvoorbeeld een configuratie maken die een specifiek sleutelbestand gebruikt wanneer je verbinding maakt vanuit AP, en een andere configuratie die een ander sleutelbestand gebruikt wanneer je verbinding maakt vanuit huis.

### Locatie van SSH-configuratiebestand

Het SSH-configuratiebestand heeft de naam `config` en wordt opgeslagen in de `.ssh`-directory onder de homedirectory van de gebruiker.

De map `~/.ssh` wordt automatisch gemaakt wanneer je een ssh-opdracht voor de eerste keer uitvoert. Als de map niet op je systeem bestaat, maak je deze aan met de onderstaande opdracht:

```bash
mkdir -p ~/.ssh && chmod 700 ~/.ssh
```

Standaard bestaat het SSH-configuratiebestand mogelijk niet, dus moet je het mogelijk aanmaken met de opdracht `touch`:

```bash
touch ~/.ssh/config
```

Dit bestand moet alleen leesbaar en beschrijfbaar zijn voor de gebruiker en mag niet toegankelijk zijn voor anderen:

```bash
chmod 600 ~/.ssh/config
```

### Structuur en patronen van een SSH-Configuratiebestand

Het SSH-configuratiebestand heeft de volgende structuur:

```bash
Host hostname1
    SSH_OPTIE value
    SSH_OPTIE value

Host hostname2
    SSH_OPTIE value

Host *
    SSH_OPTIE value
```

De inhoud van het configuratiebestand van de SSH-client is georganiseerd in strofen (secties). Elke strofe begint met de Host-richtlijn en bevat specifieke SSH-opties die worden gebruikt bij het tot stand brengen van een verbinding met de externe SSH-server.

{% hint style="info" %}
Inspringen is niet vereist, maar wordt wel aanbevolen, omdat dit het bestand gemakkelijker leesbaar maakt.
{% endhint %}

De Host-richtlijn kan één patroon of een door spaties gescheiden lijst met patronen bevatten. Elk patroon kan nul of meer niet-witruimtetekens of een van de volgende patroonspecificaties bevatten:

* \* - Komt overeen met nul of meer tekens. Host \* komt bijvoorbeeld overeen met alle hosts, terwijl 192.168.0.\* overeenkomt met hosts in het subnet 192.168.0.0/24.
* ? - Komt overeen met precies één karakter. Het patroon, Host 10.10.0. ? komt overeen met alle hosts in het bereik 10.10.0.\[0-9].&#x20;
* ! - Wanneer gebruikt aan het begin van een patroon, wordt de match teniet gedaan. Host 10.10.0. \* !10.10.0.5 komt bijvoorbeeld overeen met elke host in het subnet 10.10.0.0/24 behalve 10.10.0.5

De SSH-client leest het configuratiebestand strofe voor strofe en als meer dan één patroon overeenkomt, hebben de opties uit de eerste overeenkomende strofe voorrang. Daarom moeten er meer hostspecifieke verklaringen aan het begin van het bestand worden gegeven en meer algemene overrides aan het einde van het bestand.

Je kan een volledige lijst met beschikbare ssh-opties vinden door `man ssh_config` in je terminal te typen of door [`de manpagina ssh_config`](http://man.openbsd.org/OpenBSD-current/man5/ssh\_config.5) te bezoeken.

### SSH-configuratiebestand voorbeeld

Nu we de basis van het SSH-configuratiebestand hebben behandeld, gaan we naar het volgende voorbeeld kijken.

Wanneer je via SSH verbinding maakt met een externe server, geef je doorgaans de externe username, hostnaam en poort op. Als je zich bijvoorbeeld vanaf de terminal wilt aanmelden als een gebruiker met de naam john bij een host met de naam dev.ap.be op poort 2322, typ je:

```bash
ssh john@dev.example.com -p 22
```

Om verbinding te maken met de server met behulp van dezelfde opties als in de bovenstaande opdracht, typ je eenvoudigweg `ssh ap` en plaats je de volgende regels in je `~/.ssh/config`-bestand:

```
Host ap
    HostName dev.ap.be
    User john
    Port 22
```

Wanneer je nu `ssh ap` typt, zal de ssh-client het configuratiebestand lezen en de verbindingsdetails gebruiken die zijn opgegeven voor de ap-host:

```bash
ssh ap
```

#### Bronnen

* [https://linuxize.com/post/using-the-ssh-config-file/](https://linuxize.com/post/using-the-ssh-config-file/)
* [https://www.howtouselinux.com/post/ssh-config-file-with-examples](https://www.howtouselinux.com/post/ssh-config-file-with-examples)
