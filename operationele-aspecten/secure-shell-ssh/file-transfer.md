---
description: >-
  SCP (secure copy) is een terminal opdracht waarmee je veilig bestanden en
  mappen tussen twee locaties kunt kopiëren.
---

# file transfer

## Het SCP commando

SCP (secure copy) is een terminal opdracht waarmee je veilig bestanden en mappen tussen twee locaties kunt kopiëren.

#### Met scp kun je een bestand of map kopiëren:

1. Van je lokale systeem naar een systeem op afstand;
2. Van een systeem op afstand tot je lokale systeem;
3. Tussen twee externe systemen vanaf je lokale systeem;

Bij het overdragen van gegevens met `scp` worden zowel de bestanden als het wachtwoord gecodeerd, zodat iedereen die het verkeer bespioneert niets gevoeligs kan afluisteren.

In deze zelfstudie zal je leren hoe de `scp`-opdracht gebruikt wordt door middel van praktische voorbeelden en gedetailleerde uitleg van de meest voorkomende scp-opties.

### SCP-opdracht syntaxis

Voordat we ingaan op het gebruik van de scp-opdracht, laten we eerst de basissyntaxis bekijken.

De syntaxis van de `scp`-opdracht heeft de volgende vorm:

```bash
scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2
```

* `OPTION` - scp-opties zoals codering, ssh-configuratie, ssh-poort, limiet, recursieve kopie ... enz;
* `[user@]SRC_HOST:]file1` - Bronbestand;
* `[user@]DEST_HOST:]file2` - Bestemmingsbestand;

Lokale bestanden moeten worden opgegeven met een absoluut of relatief pad, terwijl bestandsnamen op de server een gebruikers- en hostspecificatie moeten bevatten.

scp biedt een aantal opties die elk aspect van zijn gedrag beheersen.

#### De meest gebruikte opties zijn:

* `-P` - Specificeert de ssh-poort van de externe host;
* `-p` - Behoudt bestandswijziging en toegangstijden;
* `-C` - Deze optie dwingt `scp` om de gegevens te comprimeren wanneer deze naar de server worden verzonden;
* `-r` - Deze optie vertelt `scp` om mappen recursief te kopiëren;

### Voor dat je begint

Het `scp`-commando is afhankelijk van [`ssh`](een-ssh-sleutelpaar-genereren.md) voor gegevensoverdracht, dus het vereist een `ssh`-sleutel of wachtwoord om te authenticeren op de systemen op afstand.

De dubbele punt (`:`) is hoe `scp` onderscheid maakt tussen lokale en server locaties.

Om bestanden te kunnen kopiëren, moet je ten minste leesrechten hebben op het bronbestand en schrijfrechten op het doelsysteem.

{% hint style="warning" %}
Wees voorzichtig bij het kopiëren van bestanden die op beide systemen dezelfde naam en locatie hebben, `scp` zal bestanden zonder waarschuwing overschrijven.
{% endhint %}

{% hint style="info" %}
Bij het overzetten van grote bestanden is het aan te raden om de opdracht `scp` uit te voeren binnen een [screen](https://linuxize.com/post/how-to-use-linux-screen/)- of [tmux](https://linuxize.com/post/getting-started-with-tmux/)-sessie.
{% endhint %}

### Kopieer bestanden en mappen tussen twee systemen met scp

#### Kopieer een lokaal bestand naar een extern systeem met de opdracht scp

Voer de volgende opdracht uit om een bestand van een lokaal naar een extern systeem (server) te kopiëren:

```bash
scp file.txt remote_username@10.10.0.2:/remote/directory
```

`file.txt` is de naam van het bestand dat we willen kopiëren, `remote_username` is de gebruiker op de externe server, `10.10.0.2` is het IP-adres van de server. De `/remote/directory` is het pad naar de directory waarnaar je het bestand wilt kopiëren. Als je geen pad opgeeft, wordt het bestand gekopieerd naar de thuismap van de externe server.

Indien je geen [sleutelpaar hebt aangemaakt](een-ssh-sleutelpaar-genereren.md), word je gevraagd het gebruikerswachtwoord in te voeren vooraleer het overdrachtsproces wordt gestart.

{% code title="Output" %}
```
remote_username@10.10.0.2's password:
file.txt                             100%    0     0.0KB/s   00:00
```
{% endcode %}

Als je de bestandsnaam weglaat van de bestemmingslocatie, wordt het bestand met de oorspronkelijke naam gekopieerd. Als je het bestand onder een andere naam wilt opslaan, moet je de nieuwe bestandsnaam opgeven:

```bash
scp file.txt remote_username@10.10.0.2:/remote/directory/newfilename.txt
```

Als SSH op de externe host luistert op een andere poort dan de standaard (22), dan kan je de poort specificeren met het argument `-P`:

```bash
scp -P 2322 file.txt remote_username@10.10.0.2:/remote/directory
```

De opdracht om een map te kopiëren lijkt veel op het kopiëren van bestanden. Het enige verschil is dat je de vlag `-r` moet gebruiken voor het recursief uploaden van de onderliggende bestanden en mappen.&#x20;

Gebruik de optie `-r` om een map van een lokaal naar een extern systeem te kopiëren:

```bash
scp -r /local/directory remote_username@10.10.0.2:/remote/directory
```

#### Kopieer een extern bestand naar een lokaal systeem met behulp van de opdracht scp

Om een bestand van een extern naar een lokaal systeem te kopiëren, gebruik je de externe locatie als bron en de lokale locatie als bestemming.

Om bijvoorbeeld een bestand met de naam `file.txt` van een externe server met IP `10.10.0.2` te kopiëren, voer je de volgende opdracht uit:

```bash
scp remote_username@10.10.0.2:/remote/file.txt /local/directory
```

#### Bronnen

* [https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/)
