---
description: >-
  De Thunder Client is een VS Code-extensie dat je in staat stelt om API's
  direct in de editor te testen.
---

# thunder client

## Wat is Thunder Client?

De Thunder Client extensie maakt het gemakkelijk om API-aanvragen te maken en te testen in Visual Studio Code. De extensie biedt een gebruiksvriendelijke interface om API-endpoints in te voeren en parameters te configureren, en geeft een duidelijk overzicht van de API-respons. De extensie kan ook worden gebruikt om opgeslagen aanvragen opnieuw te versturen of te bewerken voor herhaald gebruik.

### Thunder Client downloaden en installeren

Om de VScode extensie thunder client te gebruiken, moet deze eerst worden geïnstalleerd in VScode. Dit kan door naar de VScode Marketplace te gaan en te zoeken naar "Thunder Client" of door direct naar de extensie-pagina te gaan via deze link: [https://marketplace.visualstudio.com/items?itemName=Thunder-Client](https://marketplace.visualstudio.com/items?itemName=Thunder-Client).

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

Na de installatie van de extensie, kan deze worden geopend door naar de commando-palet te gaan (`CTRL + SHIFT + P`) en "Thunder Client: Open" te selecteren. Dit opent het Thunder Client-venster in VScode.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

#### Aanmaken en versturen van een aanvraag (request)

In het Thunder Client-venster kan je nieuwe aanvragen maken door op "**New Request**" te klikken. Dit opent een nieuw aanvraagvenster waar je de aanvraagdetails kunt invoeren, zoals de URL, het aanvraagtype (`GET`, `POST`, etc.), het aanvraaglichaam (body) en de headers.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Als je een aanvraag hebt gemaakt, kan je deze uitvoeren door op de "Send" knop te klikken in de rechterbovenhoek van het aanvraagvenster. Dit zal de aanvraag uitvoeren en het resultaat weergeven in het venster daarnaast, inclusief de aanvraagstatus, het aanvraaglichaam en de headers.

<figure><img src="../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

#### Activity tabblad

Het tabblad Activity toont de geschiedenis van je recente API-verzoeken. Door met de rechtermuisknop op een aanvraag te klikken kan je bewerkingen uitvoeren zoals opslaan in een collectie, hernoemen, dupliceren en meer, zoals weergegeven in de afbeelding.

Je kan ook aanvragen opslaan en laden door op de "Save" en "Load" knoppen te klikken in de linkerbovenhoek van het aanvraagvenster. Dit maakt het gemakkelijker om vaak gebruikte aanvragen op te slaan en later te laden voor hergebruik.

<figure><img src="../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>

#### Aanmaken van een collectie

Collecties zijn een groep API-verzoeken. Met Thunder Client kan je werken met collecties of een enkel individueel verzoek maken met de knop "New Request".

Om met collecties te werken, klik je op het tabblad "**Collections**" en vervolgens op het pictogram waarnaar de pijl wijst in de onderstaande afbeelding. Dit toont een vervolgkeuzelijst waarin je selecteert of je een nieuwe collectie wilt aanmaken of een bestaande collectie wilt importeren.

<figure><img src="../.gitbook/assets/image (11) (2).png" alt=""><figcaption></figcaption></figure>

#### Omgevingsvariabelen

Je kan omgevingsvariabelen toevoegen door op het tabblad "**Env**" te klikken en vervolgens op het pictogram te klikken waarnaar de pijl wijst in de onderstaande afbeelding. Dit toont een vervolgkeuzelijst om de `env`-variabelen voor verzoeken in te stellen. Je kan ook bestaande variabelen importeren.

<figure><img src="../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

#### Type aanvragen

Afhankelijk van het type verzoek biedt Thunder Client een lijst met HTTP-VERBS voor verzoeken zoals `GET`, `POST`, `PUT`, `DELETE` en `PATCH`. Je kan het type verzoek aanpassen in de linkerbovenhoek van het aanvraagvenster.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

#### Query Parameters

Er is ook ondersteuning voor query parameters, headers, autorisatie, body en tests.

**Query parameters** stellen je in staat informatie mee te geven via de url.

<figure><img src="../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption></figcaption></figure>

#### HTTP-headers

Met headers kan je HTTP-headers instellen, zoals `authorization`, `content-type`, `origin`, `user-agent`, `accept-language`, `referrer`, enzovoort.

Als je wilt dat headers optioneel zijn, zorg er dan voor dat je ze niet aanvinkt voor het verzoek.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

#### Authentication

Om toegang te krijgen tot resources, heb je tokens nodig die deze authenticeren (Bv. een [JSON Web Token](../express.js/authenticatie-en-autorisatie/json-web-token-jwt.md)). Met Thunder Client kan je op het tabblad **Auth** het gewenste type Auth selecteren en inloggegevens toevoegen.

In ons geval kiezen we voor `Bearer`; vervolgens hebben we een JSON Web Token in het tekstgebied geplakt. De token zal met het voorvoegsel 'Bearer' worden verstuurd naar de server.

{% code title="server ontvangt:" overflow="wrap" %}
```
Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIiwicGFzc3dvcmQiOiJzZWNyZXQiLCJpYXQiOjE2NzA2OTQ0Mzl9.WUiqM0RAZQDKAA9Z-nLYSo6O-XcOowIXLTM1q3d-Cm0
```
{% endcode %}

<figure><img src="../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

#### Body (payload)

Je kan een payload meesturen bij het verzenden van een verzoek. Om de payload toe te voegen, selecteer je het tabblad **Body** en zie je verschillende gegevensindelingen die door de extensie worden ondersteund.

In het onderstaande voorbeeld wordt er een JSON object verstuurd naar de server met behulp van een `POST` verzoek:

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

### Bronnen

* [https://www.freecodecamp.org/news/thunder-client-for-vscode/](https://www.freecodecamp.org/news/thunder-client-for-vscode/)
