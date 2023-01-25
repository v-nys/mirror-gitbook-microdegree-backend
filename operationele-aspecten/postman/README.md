---
description: >-
  een API ontwikkelingstool die helpt bij het bouwen, testen en wijzigen van
  API's.
---

# Postman

## Wat is Postman <a href="#wat-is-postman" id="wat-is-postman"></a>

API's zijn essentieel voor het bouwen van software applicaties. Ze worden evenzeer voor grote als kleine projecten benut. Geschikte test- en testmethoden zijn dus ook vereist. Door API's te testen kan je fouten herkennen en tijdig elimineren. In dit deel van de cursus overlopen we het installatieproces en de basis functionaliteit van Postman.Wat is Postman? Eenvoudig uitgelegd is Postman een API ontwikkelingstool die helpt bij het bouwen, testen en wijzigen van API's. Vrijwel alle functionaliteit die een ontwikkelaar nodig zou hebben, is ingekapseld in deze tool. Het wordt elke maand door meer dan 5 miljoen ontwikkelaars gebruikt om hun API-ontwikkeling gemakkelijk en eenvoudig te maken. Het heeft de mogelijkheid om verschillende soorten HTTP-verzoeken uit te voeren (GET, POST, PUT, PATCH) en collecties te maken voor het testen van al je API requests.Postman gebruiken om API's te testenNavigeer naar "Workspaces" en klik op "My Workspace". Laten we het stapsgewijze proces bekijken voor het gebruik van Postman en de verschillende functies die Postman ons te bieden heeft voor het uittesten van API's!​​

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LnWOlafbkx3lC-AgBu0%2Fuploads%2FcHiidFIPdNwvKomvMTHC%2Fimage.png?alt=media&#x26;token=d7c8b1a4-f5a3-44dd-872f-f73d0751312c" alt=""><figcaption></figcaption></figure>

1. 1.**New** – Hier maak je een nieuwe request, collectie of environment aan.
2. 2.**Import** – Dit wordt gebruikt om een ​​collectie of environment te importeren.
3. 3.**Open New Tab** – Open een nieuw tabblad voor een nieuwe request aan te maken door op deze knop te klikken.
4. 4.**Invite** – Werk samen aan een workspace door teamleden uit te nodigen.
5. 5.**History** - Eerdere requests die je hebt verzonden, worden weergegeven in History. Dit maakt het gemakkelijk om requests die je eerder hebt uitgevoerd te raadplegen.
6. 6.**Collections** – Organiseer je API requests door collecties te maken. Elke collectie kan submappen en meerdere requests omvatten. **Een request of map kan ook worden gedupliceerd zodat je voor nieuwe requests niet van nul moet beginnen!**
7. 7.**Titel van een request** – Hier wordt de titel weergegeven van de request waaraan je werkt. Standaard wordt "**Untitled Request**" weergegeven voor requests waarvoor er nog geen titel is opgegeven.
8. 8.**HTTP-verzoek** - Als je hierop klikt, wordt een vervolgkeuzelijst weergegeven met verschillende verzoeken, zoals **GET, POST, COPY, DELETE**, enz. Voor deze cursus zal je alleen moeten werken met de **GET** methode.
9. 9.**Request URL** - Ook bekend als een **eindpunt**, dit is waar je de link identificeert waar de API mee zal communiceren.
10. 10.**Save** - Als er wijzigingen in een aanvraag zijn, is het klikken op "**Save**" een must, zodat nieuwe wijzigingen niet verloren gaan of worden overschreven.
11. 11.**Send** - Door op deze knop te drukken zal je request worden uitgevoerd en zal er een antwoord worden weergeven.
12. 12.**Params** - Hier schrijft je de parameters die nodig zijn voor een request.
13. 13.**Authorization** – Om toegang te krijgen tot API's is de juiste autorisatie vereist. Het kan de vorm hebben van een gebruikersnaam met wachtwoord, een token, enz.
14. 14.**Headers** - Je kan headers instellen, zoals inhoudstype JSON.
15. 15.**Body** - Hier kan je details aanpassen voor **POST** requests.
16. 16.**Pre-request Script** – Dit zijn scripts die vóór een request worden uitgevoerd.
17. 17.**Tests** – Dit zijn scripts die tijdens een request worden uitgevoerd.
18. 18.**Settings** - Hier kan je verschillende opties aanpassen omtrent de manier waarop de API wordt aangesproken.

### Werken met GET requests&#x20;

GET requests worden gebruikt om informatie van de opgegeven URL op te halen. **Er worden geen wijzigingen aangebracht aan het eindpunt.**

We zullen de volgende URL gebruiken voor alle voorbeelden in deze Postman-zelfstudie:

```
https://swapi.dev/api/
```

**Stel je HTTP-verzoek in op GET**. Voer in het veld URL van de request de link in. Klik vervolgens op "**Send**". Je zal vanonder, in de body, een antwoord krijgen en een statuscode van **200 OK**. Er zouden 5 resultaten in de body moeten staan die aangeven dat je request succesvol is uitgevoerd.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Opmerking** :eyes:: het kan voorkomen dat de request in Postman niet succesvol is. Dit kan te wijten zijn aan een ongeldige request URL.
{% endhint %}

### Request Parameters&#x20;

Parameters instellen is een van de handigste functies van Postman. In plaats van dezelfde requests met verschillende gegevens te maken, kan je variabelen (**parameters**) gebruiken. Deze gegevens kunnen afkomstig zijn uit een gegevensbestand of een omgevingsvariabele. **Het gebruik van parameters helpt herhaling van dezelfde requests te voorkomen**.

Parameters worden gemaakt door het gebruik van dubbele accolades: `{{sample}}`. Laten we eens kijken naar een voorbeeld van het gebruik van parameters:

#### Laten we nu een GET request maken met behulp van een parameter.

**Stap 1)** Stel je HTTP-verzoek in op GET&#x20;

1. Voer volgende link in: [https://swapi.dev/api/people](https://swapi.dev/api/people).&#x20;
2. Vervang het eerste deel van de link door een parameter zoals `{{url}}`.&#x20;
3. Je endpoint zou nu `{{url}}/people` moeten zijn.&#x20;
4. Klik op verzenden.&#x20;

**Er zou geen reactie moeten zijn omdat we de bron van onze parameter niet hebben ingesteld.**

<figure><img src="../../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Stap 2)** Om de parameter te gebruiken, moet je een **globale** **environment variabele** instellen:

1. Klik op het oogpictogram in de rechterbovenhoek.&#x20;
2. Klik op "**Add**" bij "**Globals**" om de variabele in te stellen op een globale omgeving die in alle collecties kan worden gebruikt.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

**Stap 3)** Voeg je globale variabele toe.

1. Maak een nieuwe variabele aan genaamd `url`.
2. Stel de `initial value` in op de [https://swapi.dev/api/](https://swapi.dev/api/).
3. klik op "**Save**".

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Stap 4)** Ga terug naar je GET request en klik nogmaals op "**Send**". Je zou nu wel een resultaat moeten terug krijgen!

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Opmerking** :eyes:: Zorg er altijd voor dat je parameters een bron hebben zoals een omgevingsvariabele om fouten te voorkomen!
{% endhint %}

### Aanmaken van een Collectie&#x20;

Collecties spelen een belangrijke rol bij het organiseren van je API requests. Het kan worden geïmporteerd en geëxporteerd, waardoor het gemakkelijk is om collecties met een team te delen. In deze zelfstudie leer je hoe je een collectie kan aanmaken en gebruiken.

Laten we beginnen met het maken van een collectie:

**Stap 1)** Klik op de knop "**New**" in de linkerbovenhoek van de zijbalk en selecteer **Collection**.

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

**Stap 2)** Je hebt een nieuwe collectie aangemaakt met de naam "**New Collection**". Klik in de zijbalk op je nieuwe collectie en verander de naam van de collectie door op het pen icoontje te klikken in het middelste scherm zoals hieronder weergegeven. Geef je collectie de naam "**Postman Test Collection**".

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Stap 3)** Ga terug naar je vorige GET request, `{{url}}/people`. Klik op "**Save**", klik vervolgens op de naam van je nieuwe collectie en nogmaals op de knop "**Save**" in de rechter **** onderhoek van de pop-up.

<figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Stap 4)** Je Postman collectie zou nu één request moeten bevatten.

<figure><img src="../../.gitbook/assets/image (9) (1) (2).png" alt=""><figcaption></figcaption></figure>

**Stap 5)** Maak een nieuwe request aan voor `{{url}}/planets` en herhaal stap 3 , zodat de collectie nu twee verzoeken bevat.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
