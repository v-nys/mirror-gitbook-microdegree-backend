---
description: >-
  Salting is een proces waarbij een unieke willekeurige tekenreeksen wordt
  toegevoegd aan een paswoord vooraleer het wordt gehasht.
---

# paswoord salting

## Wat is Salting?

Salting is een proces waarbij een unieke willekeurige tekenreeksen wordt toegevoegd aan een paswoord vooraleer het wordt gehasht. Dit wordt gedaan om de hash-waarde van een paswoord een extra laag beveiliging te geven. De tekenreeks die aan het paswoord wordt toegevoegd, wordt de **salt** genoemd. Een salt kan voor of achter een paswoord worden toegevoegd.

{% hint style="info" %}
Bijvoorbeeld: Als je een account aanmaakt op een site met het paswoord: `myPassword`.&#x20;

Tijdens het aanmaken van je account wordt het paswoord verzonden naar de server. Vooraleer het paswoord wordt gehasht, wordt er een salt-waarde aan toegevoegd. Als de salt-waarde voor die specifieke site of gebruiker `AP%2023` is, wordt je salted-paswoord `myPasswordAP%2023`.

Het salted-paswoord wordt vervolgens gehasht en tenslotte samen met de salt in de database opgeslagen.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>source: <a href="http://www.troyhunt.com/content/images/2016/02/12341233image_thumb4.png">http://www.troyhunt.com/content/images/2016/02/12341233image_thumb4.png</a></p></figcaption></figure>

### Aanvallen op niet salted-paswoorden

In de loop der jaren hebben cybercriminelen talloze manieren ontwikkeld om in te breken en miljoenen gehashte wachtwoorden te kraken. En met elk datalek worden die methoden alleen maar beter. Er zijn drie belangrijke manieren om een gehasht wachtwoord te kraken zonder salt-encryptie:

* **Brute force**: Brute force zou de meest simplistische manier kunnen worden genoemd om gehashte paswoorden te kraken. Het is gewoon elke mogelijke paswoord combinatie raden en deze vervolgens door een hash-algoritme laten lopen. Zodra je een match hebt, weet je het oorspronkelijke paswoord. Brute force werkt het beste met kortere reeksen karakters. Hoe langer paswoorden zijn, hoe meer rekenkracht er nodig is om ze te kraken.
* **Dictionary attacks:** Een dictionary attack is een meer geavanceerde versie van brute force. In plaats van volledig willekeurig te raden, probeert de computer de meest voorkomende paswoorden en tekencombinaties uit. Dit is de reden waarom dictionary attacks met elk datalek beter worden — elke keer komen criminelen meer te weten over de manier waarop we onze paswoorden maken.
* **Rainbow tables**: Rainbow tables zijn vooraf berekende databases met gedecodeerde hash-paswoorden. Een hacker kan dus eenvoudig door de database zoeken om de gewenste hash te krijgen. Net als bij dictionary attacks worden rainbow tables bij elk datalek groter.

### Paswoord salting

Paswoord salting is dus het proces waarbij extra, willekeurige tekens aan paswoorden worden toegevoegd. Zodra er een salt is toegevoegd aan een paswoord, komt deze hoogstwaarschijnlijk niet meer overeen met de uitvoer van een rainbow table.

De aanvaller zou kunnen beginnen met het toevoegen van willekeurige tekens aan de rainbow table om te proberen de exacte salt voor het paswoord te vinden maar de kans op het scoren van een match is zo astronomisch klein dat het de aanvaller zijn tijd niet waard is.

### Waarom paswoord salting belangrijk is

Hashing op zich is niet bijzonder veilig. Hoewel het een beveiligingslaag toevoegt aan het opslagen van paswoorden, kunnen de meeste cybercriminelen gemakkelijk een "ongezouten" hash omzeilen met tools zoals een rainbow table. Het toevoegen van een uniek salt aan elk paswoord draagt exponentieel bij aan de veiligheid van de hash.

Geen enkele beveiliging is perfect, maar het goed salten van een sterk paswoord is de beste manier om de veiligheid van opgeslagen paswoorden te garanderen.

#### Bronnen

* [https://www.makeuseof.com/what-is-salting/](https://www.makeuseof.com/what-is-salting/)
* [https://cybernews.com/security/hashing-vs-encryption/](https://cybernews.com/security/hashing-vs-encryption/)
* [https://nordpass.com/blog/password-salt/](https://nordpass.com/blog/password-salt/)
