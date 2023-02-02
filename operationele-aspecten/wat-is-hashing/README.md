---
description: >-
  Hashing is een proces waarbij gegevens worden omgezet in een uniek
  cijferreeks, of een hash-waarde. Dit gebeurt door middel van een
  hashing-algoritme, zoals SHA-256 of SHA-512.
---

# Wat is Hashing

## Wat is hashing?

Hashing is een proces waarbij gegevens worden omgezet in unieke [ciphertext](../wat-is-cryptografie/ciphertext.md), of een hash-waarde. Dit gebeurt door middel van een hashing-algoritme, zoals `SHA-256` of `SHA-512`. Het doel van hashing is om gegevens te beveiligen en te beschermen tegen onbevoegde partijen.

Hashing is vergelijkbaar met [encryptie](../wat-is-cryptografie/encryptie.md) in die zin dat het gegevens versleuteld tot een onleesbare reeks tekens en letters ([ciphertext](../wat-is-cryptografie/ciphertext.md)).

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p><a href="https://www.appsealing.com/hashing-algorithms/">https://www.appsealing.com/hashing-algorithms/</a></p></figcaption></figure>

{% hint style="info" %}
Hashing verschilt echter aanzienlijk van encryptie doordat het een **eenrichtingsproces** is. Het kan dus niet worden gedecodeerd met behulp van een sleutel.

Er is geen sleutel, geen systeem van twee sleutels, geen openbaar toegankelijke sleutels, geen certificaten die je toegang geven tot de originele gegevens.
{% endhint %}

{% hint style="warning" %}
**Let op**: Eenmaal als je gegevens versleuteld met behulp van een hashing-algoritme kan je ze niet meer ontcijferen! Hashes kunnen niet worden teruggedraaid, dus als je alleen het resultaat kent van de hash, kan je de orginele gegevenss niet reconstrueren.
{% endhint %}

### Wat is een hash-algoritme?&#x20;

Hashes zijn de output van een hash-algoritme zoals `MD5` (Message Digest 5) of `SHA` (Secure Hash Algorithm). Deze algoritmen zijn in wezen gericht op het produceren van [ciphertext](../wat-is-cryptografie/ciphertext.md) met een vaste lengte.

Aangezien elk bestand op een computer uiteindelijk slechts gegevens zijn die in binaire vorm kunnen worden weergegeven, kan een hashing-algoritme die gegevens nemen, er een complexe berekening op uitvoeren en een reeks met een vaste lengte teruggeven als resultaat. Het resultaat is de hash-waarde van het bestand.

#### Alle hash-algoritmen zijn:

1. **Wiskundig**: Er zijn strikte richtlijnen die de basis vormen voor een hashing algoritme en deze regels kunnen niet worden veranderd.
   1. Bv. de hash-waarde zal altijd een vooraf gedefinieerde lengte hebben.
2. **Consistent**: Het algoritme comprimeert de gegevens en geeft voor dezelfde invoer altijd dezelfde hash terug.
   1. &#x20;Het is belangrijk op te merken dat dezelfde hash altijd wordt bekomen voor dezelfde invoer. Dit betekent dat als een gebruiker hetzelfde paswoord invoert, altijd dezelfde hash wordt berekend.
3. **Eenrichtingsproces**: Eenmaal getransformeerd door het algoritme, is het onmogelijk om de gegevens terug te zetten naar de oorspronkelijke staat.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>source: </p></figcaption></figure>

#### De voornaamste hash-algoritmes:

* **MD5**: Dit is een van de eerste algoritmen die brede adoptie kende. Het werd ontworpen in 1991 en werd destijds als opmerkelijk veilig beschouwd. Vandaag de dag kunnen hackers dit algoritme gemakkelijk binnen enkele seconden kraken. Het MD5 algoritme is m.a.w. niet meer veilig is voor gebruik!
* **SHA-2**: Deze cryptografische hashfunctie is ontwikkeld door de NSA en bouwt voort op het oudere SHA-1-algoritme. De SHA-2-familie van hash-algoritmen zijn de meest gebruikte hash-functies. `SHA-256` wordt vandaag de dag nog steeds gebruikt.
* **BCrypt**:  Deze hash-functie is ontworpen om traag te zijn, met de bedoeling om het kraken van paswoorden tijdrovender te maken en cybercriminelen te ontmoedigen om snelle aanvallen uit te voeren.

#### Bronnen

* [https://cybernews.com/security/hashing-vs-encryption/](https://cybernews.com/security/hashing-vs-encryption/)
* [https://www.appsealing.com/hashing-algorithms/](https://www.appsealing.com/hashing-algorithms/)
* [https://www.sentinelone.com/cybersecurity-101/hashing/](https://www.sentinelone.com/cybersecurity-101/hashing/)
