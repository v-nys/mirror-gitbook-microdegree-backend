# Let's Encrypt

Let's Encrypt is een gratis en openbaar certificaat voor het beveiligen van websites met behulp van HTTPS. Het biedt SSL/TLS-certificaten die automatisch worden gegenereerd en gevalideerd, waardoor het eenvoudiger wordt om een beveiligde verbinding op te zetten voor je website.

Om Let's Encrypt te installeren en te automatiseren met behulp van een SSH-verbinding vanaf je lokale machine naar een server, kun je de volgende stappen volgen:

### 1) Log in op je server via SSH:

```bash
ssh username@hostname
```

{% hint style="info" %}
Vervang `username` en `hostname` met de inloggegevens van jou server.
{% endhint %}

### 2) Installeer de Certbot-client op de server:

```bash
sudo apt-get update
sudo apt-get install certbot
```

### 3) Een certificaat verkrijgen en installeren op jou domein:

Voer de volgende opdracht:

```bash
sudo certbot --apache -d jouw-domein.com
```

### 4) Automatiseren van je certificaat:

Voer de volgende opdracht zodat je certificaat automatisch wordt vernieuwd:

```bash
sudo certbot renew --dry-run
```

Dit is het basisproces om Let's Encrypt te installeren en te automatiseren met behulp van een SSH-verbinding vanaf je lokale machine naar een server. Zorg ervoor dat je de nodige aanpassingen maakt aan de commando's om deze aan te passen aan jouw specifieke serveromgeving!

\
