# een SSH-sleutelpaar generen

Het genereren van een nieuw SSH-sleutelpaar met public en private keys op je lokale computer is de eerste stap naar authenticatie met een externe server zonder wachtwoord. Tenzij er een goede reden is om dit niet te doen, moet je altijd authenticeren met behulp van SSH-sleutels.

Er zijn een aantal cryptografische algoritmen die je kan gebruiken om SSH-sleutels te genereren, waaronder `RSA`, `DSA` en `ECDSA`. `RSA`-sleutels hebben over het algemeen de voorkeur en zijn het standaardsleuteltype.

Om een `RSA`-sleutelpaar op je lokale computer te genereren, typ je:

```
ssh-keygen
```

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Met deze prompt kan je de locatie kiezen om je `RSA` private key op te slaan. Druk op ENTER om dit als standaard te behouden, waardoor ze worden opgeslagen in de verborgen map `.ssh` in de thuismap van je gebruiker. Als je de standaardlocatie behoudt laat, kan je SSH-client de sleutels automatisch vinden.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Bij de volgende prompt kan je een wachtwoord van willekeurige lengte invoeren om je private key te beveiligen. Standaard moet je elke keer dat je de private key gebruikt je wachtwoord invoeren als extra beveiligingsmaatregel. Voel je vrij om op ENTER te drukken om dit leeg te laten als je geen wachtwoord wilt. Houd er echter rekening mee dat iedereen die de controle over je private key krijgt, hierdoor kan inloggen op je servers.

{% hint style="info" %}
**Let op**: Als je ervoor kiest om een wachtwoord in te voeren, wordt er niets weergegeven terwijl je typt. Dit is een veiligheidsmaatregel.
{% endhint %}

Deze procedure heeft een `RSA` SSH-sleutelpaar gegenereerd, dat zich bevindt in de verborgen map `.ssh` in de thuismap van je gebruiker.&#x20;

Deze bestanden zijn:

1. `~/.ssh/id_rsa`: De persoonlijke sleutel. DEEL DIT BESTAND NIET!&#x20;
2. `~/.ssh/id_rsa.pub`: De bijbehorende public key. Dit kan vrij worden gedeeld zonder gevolgen.

### Genereer van een SSH-sleutelpaar met een groter aantal bits&#x20;

SSH-sleutels zijn standaard 2048 bits. Dit wordt over het algemeen als goed genoeg beschouwd voor de beveiliging, maar je kan een groter aantal bits specificeren voor een sterkere sleutel.

Om dit te doen, neem je het argument `-b` op met het gewenste aantal bits. De meeste servers ondersteunen sleutels met een lengte van minimaal 4096 bits. Langere sleutels worden mogelijk niet geaccepteerd voor DDOS-beveiligingsdoeleinden:

```
ssh-keygen -b 4096
```

Als je eerder een andere sleutelpaar had aangemaakt, wordt er gevraagd of je de vorige sleutel wilt overschrijven:

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Als je "`y`" kiest, wordt je vorige sleutel overschreven en kan je met die sleutel niet meer inloggen op servers. Zorg er daarom voor dat je de sleutels voorzichtig overschrijft.

### Het wachtwoord van een private key verwijderen of wijzigen

Als je een wachtwoord voor je private key hebt gegenereerd en deze wilt wijzigen of verwijderen, kan dat eenvoudig.

{% hint style="info" %}
**Opmerking**: om het wachtwoord te wijzigen of te verwijderen, moet je het oorspronkelijke wachtwoord kennen. Als je het wachtwoord van de private key bent kwijtgeraakt, is er geen recuperatie mogelijk en moet je een nieuw sleutelpaar genereren.
{% endhint %}

Om het wachtwoord te wijzigen of te verwijderen, typ je eenvoudig:

```
ssh-keygen -p
```

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
