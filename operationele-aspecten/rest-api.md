---
description: >-
  REST (afkorting van representational state transfer) is gebaseerd op een
  vooraf gedefinieerde reeks staatloze bewerkingen waarmee gebruikers toegang
  hebben tot webgegevens en deze kunnen manipuleren.
---

# REST API

## **Wat is een API? (herhaling)**

Een van de meest besproken termen binnen de programmeerwereld van vandaag is 'API'. Veel mensen weten niet precies wat een API is. API staat voor Application Programming Interface.

**Het is, zoals de naam al zegt, een interface waarmee mensen - ontwikkelaars, gebruikers, consumenten - kunnen communiceren met gegevens.**

Je kunt een API zien als een barman. Je vraagt ​​de barman om iets te drinken en hij geeft je wat je wil. Hij is de '**middleman**' die de bestelling van de klant opneemt en vervolgens de bestelling, in dit geval bv. een drankje, tot aan de klant levert.

Sinds de start van het moderne web is het bouwen van API's niet zo ingewikkeld geweest als er vaak wordt gezegd. **Maar API's leren en begrijpen wel.** Ontwikkelaars vormen de meerderheid van de mensen die een API zullen gebruiken om iets te bouwen of om gewoon gegevens te consumeren. **Een API moet dus zo proper en intuïtief mogelijk zijn.** Een goed ontworpen API is heel gemakkelijk te gebruiken en aan te leren.

## Wat is REST?

Het architecturale principe van REST wordt al meer dan tien jaar gebruikt door ontwikkelaars. Het vereenvoudigt de communicatie tussen machines en ondersteunt vele gegevensformaten, zoals JSON, XML of YAML. Ondanks het feit dat het duidelijk een van de meest populaire benaderingen is in de bedrijven van vandaag, met steun van grote giganten zoals Google en Netflix, heeft het nog steeds bepaalde gebreken die de toepasbaarheid ervan beperken.

REST (afkorting van **RE**presentational **S**tate **T**ransfer) is gebaseerd op een uniforme en vooraf gedefinieerde reeks staatloze bewerkingen waarmee gebruikers toegang hebben tot webgegevens en deze kunnen manipuleren. API's die voldoen aan REST-ontwerpprincipes worden meestal **RESTful API's** genoemd.

In REST-architectuur stellen API's hun functionaliteit bloot als bronnen, dit zijn alle soorten services, gegevens of objecten waartoe een client toegang heeft. Elke bron wordt geleverd met zijn eigen unieke URI (Uniform Resource Identifier) waartoe een client toegang kan krijgen door een verzoek naar de server te sturen.

{% hint style="info" %}
Een bepaalde bron van een API wordt ook wel eens een **endpoint** genoemd!
{% endhint %}

#### Endpoint

Het endpoint (of route) is de url waar je om vraagt. Het volgt deze structuur:

```
root-endpoint/path
```

De **root-endpoint** is het startpunt van de API die je aanvraagt. De root-endpoint van de API van Github is [https://api.github.com](https://api.github.com), terwijl de API van het root-endpoint van Twitter [https://api.twitter.com](https://api.twitter.com) is.

Het **pad** is de bron die je aanvraagt. Zie het als een automatisch antwoordapparaat dat je vraagt om op 1 te drukken voor een dienst, op 2 voor een andere dienst, 3 voor nog een andere dienst enzovoort.

```
root-endpoint/users/:id
```

in het voorbeeld hierboven is **users/:id** is het pad.

#### HTTP Methodes (verzoeken)

&#x20;Veel gangbare REST-implementaties gebruiken de standaard HTTP-methoden (**GET, POST, PUT, DELETE** en **PATCH**) om een server aan te roepen.

| Naam van het verzoek | Betekenis van het verzoek                                                                                                                                                                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GET                  | Dit verzoek wordt gebruikt om een bron van een server op te halen. Als je een `GET`-verzoek uitvoert, zoekt de server naar de door jou opgevraagde gegevens en stuurt deze naar je terug. Met andere woorden, een 'GET'-verzoek voert een 'READ'-bewerking uit. Dit is de standaard HTTP-methode. |
| POST                 | Dit verzoek wordt gebruikt om een nieuwe bron op een server te creëren. Als je een `POST`-verzoek uitvoert, maakt de server een nieuw item in de database aan en vertelt je of het maken degelijk is gelukt. Met andere woorden, een `POST`-verzoek voert een `CREATE`-bewerking uit.             |
| PUT en PATCH         | Deze twee verzoeken worden gebruikt om een bron op een server bij te werken. Als je een `PUT`- of `PATCH`-verzoek uitvoert, werkt de server een item in de database bij en vertelt je of de update is gelukt. Met andere woorden, een `PUT`- of `PATCH`-verzoek voert een `UPDATE`-bewerking uit. |
| DELETE               | Dit verzoek wordt gebruikt om een bron van een server te verwijderen. Als je een `DELETE`-verzoek uitvoert, verwijdert de server een item in de database en vertelt je of het verwijderen is gelukt. Met andere woorden, een 'DELETE'-verzoek voert een 'DELETE'-bewerking uit.                   |

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2FpOb0MaXg8He0cJTcaXXz%2Fimage.png?alt=media&#x26;token=2c2944c1-79d8-4f5d-93b1-ee7bcc253935" alt=""><figcaption></figcaption></figure>

#### HTTP Status codes:

Wanneer een client een RESTful API aanroept, reageert de server met een weergave van de status van de opgevraagde bron.

1. **200+** betekent dat het verzoek is gelukt;&#x20;
2. **300+** betekent dat het verzoek wordt omgeleid naar een andere URL;&#x20;
3. **400+** betekent dat er een fout is opgetreden die afkomstig is van de client;&#x20;
4. **500+** betekent dat er een fout is opgetreden die afkomstig is van de server;

{% hint style="info" %}
Dit betekent dat wanneer een RESTful API wordt aangeroepen, de server een weergave van de status van de aangevraagde bron naar de client zal overdragen.
{% endhint %}

### SWAPI REST API voorbeeld

SWAPI is een API voor het ophalen van alle gegevens uit het Star Wars universum en een perfect voorbeeld om de werking van REST uit te leggen.

Een REST API kan je aanroepen door een bepaalde URI aan te spreken. In het geval van Swapi is dit: [https://swapi.dev/api/](https://swapi.dev/api/)

Je kan bepaalde resources opvragen door achter `api/` iets op te geven. Je kan daar natuurlijk niet zo maar iets typen, er zijn hiervoor bepaalde endpoints voor voorzien. Je kan alle endpoints terugvinden in de [documentatie](https://swapi.dev/documentation) van Swapi.

Voor het ophalen van alle personen in Star Wars kan je het endpoint [https://swapi.dev/api/people/](https://swapi.dev/api/people/) gebruiken. Indien je 1 persoon wilt opvragen dan kan je dat doen a.d.h.v. een ID.

* `/people/` -- Fetch alle personen
* `/people/:id/` -- Fetch een specifieke persoon

Laten we samen als voorbeeld de persoon met id 1 ophalen. We krijgen een object terug met data van Luke Skywalker.

{% code title="GET https://swapi.dev/api/people/1/" %}
```yaml
HTTP 200 OK
Content-Type: application/json
Vary: Accept
Allow: GET, HEAD, OPTIONS

{
    "name": "Luke Skywalker", 
    "height": "172", 
    "mass": "77", 
    "hair_color": "blond", 
    "skin_color": "fair", 
    "eye_color": "blue", 
    "birth_year": "19BBY", 
    "gender": "male", 
    "homeworld": "http://swapi.dev/api/planets/1/", 
    "films": [
        "http://swapi.dev/api/films/1/", 
        "http://swapi.dev/api/films/2/", 
        "http://swapi.dev/api/films/3/", 
        "http://swapi.dev/api/films/6/"
    ], 
    "species": [], 
    "vehicles": [
        "http://swapi.dev/api/vehicles/14/", 
        "http://swapi.dev/api/vehicles/30/"
    ], 
    "starships": [
        "http://swapi.dev/api/starships/12/", 
        "http://swapi.dev/api/starships/22/"
    ], 
    "created": "2014-12-09T13:50:51.644000Z", 
    "edited": "2014-12-20T21:17:56.891000Z", 
    "url": "http://swapi.dev/api/people/1/"
}
```
{% endcode %}

Zoals je hierboven te zien krijgt, worden er bij sommige object keys een URI of een array van URI's terug. Bv. de '`homeworld`' van Luke Skywalker heeft als waarde "`http://swapi.dev/api/planets/1/`"

Indien we de data van de `homeworld` willen opvragen moeten we het boven vernoemde endpoint aanspreken.



{% code title="GET https://swapi.dev/api/planets/1/" %}
```yaml
HTTP 200 OK
Content-Type: application/json
Vary: Accept
Allow: GET, HEAD, OPTIONS

{
    "name": "Tatooine", 
    "rotation_period": "23", 
    "orbital_period": "304", 
    "diameter": "10465", 
    "climate": "arid", 
    "gravity": "1 standard", 
    "terrain": "desert", 
    "surface_water": "1", 
    "population": "200000", 
    "residents": [
        "http://swapi.dev/api/people/1/", 
        "http://swapi.dev/api/people/2/", 
        "http://swapi.dev/api/people/4/", 
        "http://swapi.dev/api/people/6/", 
        "http://swapi.dev/api/people/7/", 
        "http://swapi.dev/api/people/8/", 
        "http://swapi.dev/api/people/9/", 
        "http://swapi.dev/api/people/11/", 
        "http://swapi.dev/api/people/43/", 
        "http://swapi.dev/api/people/62/"
    ], 
    "films": [
        "http://swapi.dev/api/films/1/", 
        "http://swapi.dev/api/films/3/", 
        "http://swapi.dev/api/films/4/", 
        "http://swapi.dev/api/films/5/", 
        "http://swapi.dev/api/films/6/"
    ], 
    "created": "2014-12-09T13:50:49.641000Z", 
    "edited": "2014-12-20T20:58:18.411000Z", 
    "url": "http://swapi.dev/api/planets/1/"
}
```
{% endcode %}

**Je zal niet altijd alle data nodig hebben van een persoon. Het is dus onnodig om bij elke request de hele waslijst van gegevens te retourneren.**

In plaats daarvan geeft SWAPI voor sommige velden een URI terug die op haar beurt kan worden aangeroepen indien de consument toch meer informatie wenst. Door niet alle data in een request terug te sturen los je het probleem van **overfetching** op.

Het principe van URI's terug te sturen als data is een good practice voor het bouwen van REST API's. **één groot nadeel is wel dat je verschillende endpoints moet aanspreken indien je toch bepaalde informatie nodig hebt.** Er zullen dus **meerdere roundtrips naar de server** worden gedaan waardoor de performantie van je front-end aftakelt!

### Overfetching en Underfetching

Overfetching treedt op wanneer een eindpunt overbodige gegevens retourneert dan eigenlijk nodig is. Omgekeerd houdt underfetching in dat een eindpunt niet voldoende van de vereiste gegevens kan retourneren.

* **Overfetching:** treedt op wanneer een endpoint overbodige gegevens retourneert dan eigenlijk nodig is.
* **underfetching:** houdt in dat een endpoint niet voldoende van de vereiste gegevens kan retourneren.

Aangezien een REST-API een gegevensstructuur heeft die ontworpen is om voorgeschreven gegevens te retourneren, kan je onnodige gegevens krijgen of gedwongen worden om meerdere roundtrips naar de server te doen voordat je de relevante gegevens krijgt. **Deze tekortkomingen vergroten ook de tijd die de server nodig heeft om alle gevraagde informatie terug te sturen.**

