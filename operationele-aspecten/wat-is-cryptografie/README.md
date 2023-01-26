---
description: Cryptografie is een techniek die gebruikt wordt om informatie te beveiligen.
---

# Wat is Cryptografie?

## Cryptografie

Cryptografie is de wetenschap van het versleutelen en ontcijferen van informatie om onbevoegde toegang te voorkomen. Bij cryptografie worden gegevens en persoonlijke informatie getransformeerd van 'plain' text naar een willekeurige reeks cijfers en letters die moeilijk te ontcijferen zijn. Alleen de juiste ontvanger kan het bericht ontcijferen en aldus toegang krijgen tot de informatie.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://binarycoders.dev/">https://binarycoders.dev/</a></p></figcaption></figure>

{% hint style="info" %}
**De kunst van cryptografie wordt al duizenden jaren gebruikt om berichten te coderen.** In films zien we vaak dat rechercheurs gebruik maken van specifieke codewoorden om informatie uit te wisselen. Alleen als beide partijen het juiste codewoord bevestigen, gaan ze verder met de transactie. Dit is een voorbeeld van hoe cryptografie gebruikt wordt om communicatie veilig te houden.
{% endhint %}

Vandaag de dag is cryptografie is een belangrijk onderdeel van de informatica, vooral als het gaat om de beveiliging van data en communicatie. Het is dus een techniek die gebruikt wordt om informatie te coderen zodat alleen degenen met de juiste **coderingssleutel** de informatie kunnen lezen of gebruiken.

{% hint style="info" %}
Een **coderingssleutel** wordt gebruikt om gegevens te **coderen** of te **decoderen**.

Dat betekent in feite dat een coderingssleutel in staat is om de gegevens te vermengen tot onleesbare tekens, en het kan die onleesbare tekens terugzetten naar gewone tekst.
{% endhint %}

### symmetrische en asymmetrische cryptografie

Er zijn drie hoofdtypen van cryptografie: symmetrische, asymmetrische cryptografie en hashing.&#x20;

#### Symmetrische cryptografie

Bij symmetrische cryptografie wordt dezelfde sleutel gebruikt om de informatie te coderen en te decoderen. Dit is eenvoudig te implementeren, maar het is belangrijk om de sleutel veilig te houden, omdat iedereen die de sleutel heeft, de informatie kan ontcijferen.

#### Asymmetrische cryptografie

Asymmetrische cryptografie, ook wel publieke sleutelcryptografie genoemd, gebruikt twee sleutels: een **publieke sleutel** en een **privésleutel**. De publieke sleutel wordt gebruikt om de informatie te coderen, terwijl de privésleutel wordt gebruikt om de informatie te decoderen. Dit maakt het veel veiliger, omdat alleen degenen met de juiste privésleutel de informatie kunnen ontcijferen.

#### Hashing

Hashing is een techniek waarmee informatie wordt omgezet in een unieke code waarmee de authenticatie van de data kan worden geverifieerd zonder dat de oorspronkelijke data wordt uitgelezen. Hashing is een **eenrichtingsproces**, zonder sleutel om de invoer in zijn oorspronkelijke formaat te ontgrendelen.

### Historische betekenis van cryptografie

De twee beroemdste voorbeelden van cryptografie in de oudheid zijn:

* Caesar cijfer
* Enigma-machine

#### Ceasar cijfer

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Het Caesar-cijfer is een oud en eenvoudig type encryptie dat vernoemd is naar Julius Caesar, die het gebruikte om zijn privé-correspondentie te beschermen. Het werkt door elke letter in een tekst te verplaatsen naar een andere letter in het alfabet, gebaseerd op een bepaalde sleutel.

Bijvoorbeeld, als de sleutel 3 is, dan wordt elke letter in de tekst verplaatst naar de derde letter ernaast in het alfabet. Dus de letter "A" wordt veranderd in "D", "B" wordt veranderd in "E" en zo verder.

Het Caesar-cijfer is een voorbeeld van een substitutie-cijfer, omdat het vervangt letters met andere letters. Het is echter zeer eenvoudig te kraken omdat er slechts 26 mogelijke sleutels zijn (één voor elke letter van het alfabet) en een gerichte aanval kan gemakkelijk de juiste sleutel vinden.

In de moderne tijd, Caesar-cijfer wordt meestal gebruikt als een educatief hulpmiddel om te leren over encryptie, in plaats van een beveiligingsmechanisme. Er zijn veel geavanceerde encryptie methodes die worden gebruikt voor echte beveiliging, zoals RSA.

#### Enigma machine

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Enigma machine - <a href="https://ariaturns.files.wordpress.com/2015/01/enigma.jpg">https://ariaturns.files.wordpress.com/2015/01/enigma.jpg</a></p></figcaption></figure>

De Enigma-machine was een mechanische encryptie-apparaat dat werd gebruikt in de Tweede Wereldoorlog door de Duitsers om hun geheime communicatie te coderen en te decoderen. Het apparaat bestond uit een reeks rotors die de letters van de tekst vervangen met andere letters, gebaseerd op een bepaalde sleutel.

De rotors konden worden geconfigureerd in verschillende posities, waardoor er miljoenen mogelijke sleutels waren. De Enigma-machine was echter niet onkraakbaar. De geallieerden wisten het te ontcijferen dankzij de inspanningen van de beroemde codebrekers Alan Turing en zijn team.

## Conclusie

Als webdeveloper zul je waarschijnlijk te maken krijgen met cryptografie, vooral als je werkt met beveiliging van websites of mobiele apps. Bijvoorbeeld bij online betalingen of inloggen, hier worden vaak **TSL** certificaten gebruikt.&#x20;

{% hint style="info" %}
**TSL** (**Transport Layer Security**) is een protocol voor internetbeveiliging dat wordt gebruikt om gegevens te coderen die worden verzonden tussen een webbrowser en een webserver. Dit wordt gedaan om te voorkomen dat onbevoegde personen de gegevens kunnen lezen of gebruiken.
{% endhint %}

**TSL** is een vorm van asymmetrische cryptografie die gebruikt wordt om de informatie tussen de gebruiker en de website te coderen. TSL komt later in de cursus nog aanbod! Het is belangrijk om te begrijpen hoe deze technieken werken en hoe je ze kunt implementeren in je projecten.&#x20;

Daarnaast is het ook belangrijk om op de hoogte te zijn van de nieuwste ontwikkelingen en technieken in de cryptografie om de beveiliging van de data te versterken. Als webdeveloper zal je vaak verantwoordelijk zijn voor de beveiliging van de data en het bewaken van de beveiliging van de website of app.

#### Bronnen

* [https://www.jigsawacademy.com/blogs/cyber-security/what-is-cryptography/](https://www.jigsawacademy.com/blogs/cyber-security/what-is-cryptography/)
* [https://www.simplilearn.com/tutorials/cryptography-tutorial/what-is-cryptography](https://www.simplilearn.com/tutorials/cryptography-tutorial/what-is-cryptography)
* [https://www.fortinet.com/resources/cyberglossary/what-is-cryptography](https://www.fortinet.com/resources/cyberglossary/what-is-cryptography)
