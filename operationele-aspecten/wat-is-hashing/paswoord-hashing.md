---
description: >-
  Het gebruik van paswoord hashing zal er voor zorgen dat niet de originele
  paswoorden worden opgeslagen in de databank maar in plaats daarvan hun
  hashed-versie.
---

# Paswoord Hashing

Een eenvoudige manier om paswoorden op te slaan, is door een tabel in een databank te maken die een gebruikersnaam koppelt aan een paswoord. Wanneer een gebruiker inlogt, krijgt de server een authenticatieverzoek met een payload die een gebruikersnaam en een wachtwoord bevat. We zoeken de gebruikersnaam op in de tabel en vergelijken het opgegeven paswoord met het opgeslagen paswoord. Een match geeft de gebruiker toegang tot de applicatie.

De sterkte en veerkracht van dit model hangt af van hoe het paswoord is opgeslagen. Het meest elementaire, maar ook het minst veilige wachtwoordopslagformaat is leesbare tekst (plain teskt).

Als een aanvaller zou inbreken in de database en toegang krijgt tot de tabel met paswoorden, zou de aanvaller toegang hebben tot elk gebruikersaccount. Dit probleem wordt nog verergerd door het feit dat veel gebruikers een enkel paswoord hergebruiken of variaties gebruiken, waardoor de aanvaller mogelijk toegang krijgt tot andere services dan degene die is gecompromitteerd. Dat klinkt allemaal als een beveiligingsnachtmerrie!

De aanval kan vanuit de organisatie komen. Een malafide software-engineer met toegang tot de database kan die toegangsbevoegdheid misbruiken, de leesbare inloggegevens achterhalen en toegang krijgen tot elk account.

Een veiligere manier om een wachtwoord op te slaan, is door het om te zetten in gegevens die niet kunnen worden teruggezet naar het oorspronkelijke wachtwoord. Met andere woorden paswoord hashinh

## Hashen van paswoorden

Als paswoorden in plain tekst worden bewaard in een databank, kan iedereen met interne toegang ze zien. Om nog maar te zwijgen van het feit dat als de database wordt gelekt, hackers de inloggegevens ook duidelijk zouden zien. Dus elk bedrijf dat op zijn minst de basisbeveiligingspraktijken volgt, zal je paswoord nooit als plain tekst in de databank bewaren.

Het gebruik van paswoord hashing zal er voor zorgen dat niet de originele paswoorden worden opgeslagen in de databank maar in plaats daarvan hun hashed-versie.

Het is onmogelijk om van een hash terug te gaan naar het oorspronkelijke paswoord (**eenrichtingsproces**). Dit maakt het zeer moeilijker voor aanvallers om toegang te krijgen tot de originele gegevens, zelfs als de databank wordt gekraakt.

Bovendien kunnen vergelijkingen tussen hashes worden uitgevoerd zonder dat de oorspronkelijke paswoorden ergens opgeslagen moeten worden. Dit betekent wanneer een gebruiker inlogt, wordt het getypte paswoord gehasht en vergeleken met de gehashte invoer uit de databasetabel. Als er een match is, voila! De gebruiker mag doorgaan.

{% hint style="info" %}
Dit is mogelijk omdat dezelfde hash altijd wordt bekomen voor dezelfde invoer!
{% endhint %}

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>source: <a href="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/CPT-Hashing-Password-Login.svg/1200px-CPT-Hashing-Password-Login.svg.png">https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/CPT-Hashing-Password-Login.svg/1200px-CPT-Hashing-Password-Login.svg.png</a></p></figcaption></figure>

Het gebruik van hashing voor paswoorden is niet perfect, aangezien het nog steeds mogelijk is om hashes te hacken door middel van bijvoorbeeld [brute force-aanvallen](https://www.fortinet.com/resources/cyberglossary/brute-force-attack). Daarom wordt het aanbevolen om hash-functies te gebruiken die zeer moeilijk te hacken zijn en om extra beveiliging te implementeren, zoals [salt](paswoord-salting.md), om de beveiliging van paswoorden te verbeteren.

#### Bronnen

* [https://cybernews.com/security/hashing-vs-encryption/](https://cybernews.com/security/hashing-vs-encryption/)
* [https://www.appsealing.com/hashing-algorithms/](https://www.appsealing.com/hashing-algorithms/)
* [https://www.sentinelone.com/cybersecurity-101/hashing/](https://www.sentinelone.com/cybersecurity-101/hashing/)
* [https://auth0.com/blog/hashing-passwords-one-way-road-to-security/](https://auth0.com/blog/hashing-passwords-one-way-road-to-security/)
