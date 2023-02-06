---
description: >-
  Bcrypt is een nodejs-module die gebruikt wordt om paswoorden te beveiligen
  door middel van hashing en salting.
---

# bcrypt

Bcrypt is een nodejs-module die gebruikt wordt om paswoorden te beveiligen door middel van [hashing](../paswoord-hashing.md). Zoals je ondertussen al weet is hashing een proces waarbij een paswoord wordt omgezet in een onleesbare tekenreeks, ook wel een hash genoemd. Het doel van hashing is om paswoorden te beschermen door ze op te slaan in een onleesbare vorm.

Bcrypt gebruikt het [Blowfish-hashing algoritme](https://en.wikipedia.org/wiki/Blowfish\_\(cipher\)), wat een zeer veilig en beproefd algoritme is. Het voordeel van Blowfish is dat het zeer efficiënt is, zonder concessies te doen aan de veiligheid. Bcrypt wordt veel gebruikt en bestaat al vele jaren (het is gemaakt in 1999). Gerapporteerde problemen zijn schaars en niemand heeft (tot nu toe) het Blowfish-algoritme kunnen kraken.

Met bcrypt kan je gemakkelijk salting toepassen op paswoorden. [Salting](../paswoord-salting.md) is een extra beveiligingslaag die aan het paswoord toegevoegd wordt tijdens het hashingsproces. Hierdoor wordt het moeilijker om paswoorden te achterhalen bij een eventuele datalek. Bij het toepassen van salting, wordt een unieke tekenreeks (het zogenaamde "salt") aan het paswoord toegevoegd. Hierdoor wordt het resulterende hash uniek, ook als twee gebruikers hetzelfde wachtwoord hebben.

Bcrypt verbetert de veiligheid van paswoorden door zowel het gebruik van een geavanceerd hashing algoritme als salting toe te passen. Hierdoor is het moeilijker voor aanvallers om paswoorden te achterhalen.

{% embed url="https://www.npmjs.com/package/bcrypt" %}

### Bronnen

* [https://www.makeuseof.com/nodejs-bcrypt-hash-verify-salt-password/](https://www.makeuseof.com/nodejs-bcrypt-hash-verify-salt-password/)
* [https://cryptocoached-com.ngontinh24.com/article/salt-and-hash-passwords-with-bcrypt](https://cryptocoached-com.ngontinh24.com/article/salt-and-hash-passwords-with-bcrypt)
