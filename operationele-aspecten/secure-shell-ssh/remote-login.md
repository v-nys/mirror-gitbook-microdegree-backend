# remote login

Om via SSH verbinding te maken met een systeem op afstand, gebruiken we de opdracht `ssh`.

De meest eenvoudige vorm van de opdracht is:

```bash
ssh remote_host
```

De `remote_host` in dit voorbeeld is het IP-adres of de domeinnaam waarmee je verbinding probeert te maken.

Deze opdracht gaat ervan uit dat je gebruikersnaam op het externe systeem dezelfde is als je gebruikersnaam op je lokale systeem.

Als je gebruikersnaam op het externe systeem anders is, kan je deze specificeren met behulp van deze syntaxis:

```bash
ssh remote_username@remote_host
```

Nadat je verbinding hebt gemaakt met de server, wordt je mogelijk gevraagd je identiteit te verifiëren door een paswoord op te geven. Je kan hiervoor ook een sleutelpaar genereren om te gebruiken in plaats van wachtwoorden. Bekijk het hoofdstuk omtrent een [SSH-sleutelpaar genereren](een-ssh-sleutelpaar-genereren.md) voor meer informatie.

Om de ssh-sessie af te sluiten en terug te keren naar je lokale shell-sessie, typ je:

```bash
exit
```

#### Bronnen

* [https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server)
