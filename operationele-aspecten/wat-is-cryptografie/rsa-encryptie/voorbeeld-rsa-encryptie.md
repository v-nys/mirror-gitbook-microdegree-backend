---
description: >-
  Demonstratie van het encrypteren en decrypteren van gegevens aan de hand van
  RSA
---

# Voorbeeld RSA Encryptie

Voor deze demonstratie over wat cryptografie is, hebben we een webgebaseerde tool ([https://www.devglan.com/online-tools/rsa-encryption-decryption](https://www.devglan.com/online-tools/rsa-encryption-decryption)) die je zal helpen om het proces van RSA-codering beter te begrijpen. Zoals je waarschijnlijk al weet, valt RSA onder asymmetrische sleutelcryptografie, wat betekent dat er twee sleutels worden gebruikt: een openbare sleutel en een privésleutel.

### Stap 1: Genereren van RSA sleutels

Je hebt de keuze uit de sleutelgrootte bij RSA, waarmee je prioriteit kunt geven aan snelheid of extra complexiteit, afhankelijk van je vereisten. Voor deze demonstratie kies je voor de sleutelgrootte van 4096 bits en genereer je het sleutelpaar.

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Het verschil tussen 1024-bit RSA en 4096-bit RSA is de grootte van de sleutel die wordt gebruikt voor encryptie en decryptie.

Een 1024-bit RSA-sleutel heeft 1024 bits, wat betekent dat er 1024 cijfers zijn die gebruikt worden om de sleutel te genereren. Dit is een standaardgrootte voor RSA-sleutels en wordt vaak gebruikt voor encryptie van gegevens.

Een 4096-bit RSA-sleutel heeft 4096 bits, wat betekent dat er 4096 cijfers zijn die gebruikt worden om de sleutel te genereren. Dit is een grotere sleutelgrootte en biedt daarom een hogere beveiliging voor de gegevens omdat het veel moeilijker is om te hacken.

In het algemeen wordt aangeraden om een grotere sleutelgrootte te gebruiken voor grotere beveiliging.
{% endhint %}

### Stap 2: Encrypteren van de gegevens

Probeer het woord "**AP Hogeschool**" te coderen in dit voorbeeld. Je moet beslissen of de sleutel die wordt gebruikt voor codering privé of openbaar is, omdat dit invloed heeft op het proces van het versleutelen van de informatie. Gebruik voor dit voorbeeld de openbare sleutel. Je hebt ook de mogelijkheid om aangepaste cijfers te gebruiken, maar voor nu volstaat het om gewone RSA te gebruiken.

<img src="../../../.gitbook/assets/image (7) (3).png" alt="" data-size="original">

Vervolgens kan je de gegevens versleutelen door op de knop **Encrypt** te klikken.

![](<../../../.gitbook/assets/image (25) (1).png>)

### Stap 3: Decrypteren van de ciphertext

Om het bericht te versturen naar de ontvanger, moet je eerst de ciphertext genereren. De ontvanger moet al in het bezit zijn van de bijbehorende privésleutel die is gegenereerd uit hetzelfde paar als de openbare sleutel die je hebt gebruikt voor codering. Er kan geen andere privésleutel worden gebruikt om het bericht te decoderen. Je moet de privésleutel van de ontvanger hier plakken en selecteren. Let erop dat het cijfer dat wordt gebruikt voor decodering overeen moet komen met het cijfer dat is gebruikt tijdens het coderingproces.

![](<../../../.gitbook/assets/image (2) (3).png>)&#x20;

Zodra je op **Decrypt** klikt, krijg je de originele tekst te zien.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Bronnen

* [https://www.simplilearn.com/tutorials/cryptography-tutorial/what-is-cryptography](https://www.simplilearn.com/tutorials/cryptography-tutorial/what-is-cryptography)
