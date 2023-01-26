# Transport Layer Security (TLS)

## Wat is Transport Layer Security (TLS)?&#x20;

Transport Layer Security, of TLS, is een algemeen geaccepteerd beveiligingsprotocol dat is ontworpen om privacy en gegevensbeveiliging voor communicatie via internet te vergemakkelijken. Een primaire use case van TLS is het versleutelen van de communicatie tussen webapplicaties en servers, zoals webbrowsers die een website laden. TLS kan ook worden gebruikt om andere communicatie zoals e-mail, berichten en voice over IP (VoIP) te versleutelen. Wij zullen ons toespitsen op de rol van TLS in de beveiliging van webapplicaties.

{% hint style="info" %}
TLS is voorgesteld door de **Internet Engineering Task Force** (IETF), een internationale normalisatieorganisatie, en de eerste versie van het protocol is gepubliceerd in 1999. De meest recente versie is TLS 1.3, die in 2018 is gepubliceerd.
{% endhint %}

TLS is de opvolger van het oudere **Secure Sockets Layer** (SSL) protocol en is ontworpen om een veilige verbinding te garanderen tussen een webclient en een webserver. TLS gebruikt een combinatie van certificaten en encryptie om gegevens te beschermen tegen ongeoorloofde toegang, manipulatie en afluisteren.

1. Het helpt bij het verifiëren van de identiteit van de server waarmee de client communiceert, waardoor het risico van phishing en andere beveiligingsrisico's wordt verminderd.
2. TLS wordt vaak gebruikt in combinatie met HTTPS, waardoor een veilige verbinding wordt gegarandeerd voor online transacties en het delen van gevoelige informatie.

### Wat is het verschil tussen TLS en SSL?

TLS is voortgekomen uit een eerder versleutelingsprotocol genaamd Secure Sockets Layer (SSL), ontwikkeld door Netscape. TLS versie 1.0 begon eigenlijk met de ontwikkeling als SSL versie 3.1, maar de naam van het protocol werd vóór publicatie gewijzigd om aan te geven dat het niet langer geassocieerd was met Netscape. **Vanwege deze geschiedenis worden de termen TLS en SSL soms door elkaar gebruikt.**

{% hint style="warning" %}
SSL is een ouder protocol dat werd ontwikkeld in de jaren 90. TLS is de opvolger van SSL en is ontworpen om de beveiligingsproblemen van SSL op te lossen.

SSL gebruikt een beperkt aantal ciphers voor encryptie terwijl TLS meer opties biedt voor ciphers
{% endhint %}

### Wat is het verschil tussen TLS en HTTPS?

HTTPS is een implementatie van TLS-codering bovenop het HTTP-protocol, dat door alle websites en door enkele andere webservices wordt gebruikt. Elke website die HTTPS gebruikt, maakt daarom gebruik van TLS-codering.

HTTPS definieert het formaat van berichten waarmee webbrowsers en webbrowsers communiceren en definieert hoe een webbrowser moet reageren op een webverzoek. Het voorkomt ook dat websites hun informatie als plain tekst verzenden dat gemakkelijk zichtbaar is voor iedereen met negatieve bedoelingen.

{% hint style="info" %}
**HTTPS** is gericht op encryptie van data tijdens transport en authenticatie van de identiteit van de server waarmee je communiceert.
{% endhint %}

Elke website, vooral die waarvoor inloggegevens nodig zijn, moet HTTPS gebruiken. Je kan zien of een website SSL/TLS heeft geïmplementeerd door naar de URL te kijken, aangezien het SSL/TLS-certificaat websites in staat stelt de URL van HTTP naar HTTPS om te zetten.

![](<../../.gitbook/assets/image (2).png>)

De website van AP heeft een TLS/SSL certificaat dat de verbinding beveiligd. Je kan zien aan de URL dat het begint met HTTPS.

![](<../../.gitbook/assets/image (1).png>)

De website columbia.edu heeft geen TLS/SSL certificaat en is met andere woorden niet beveiligd. De gegevens die vanuit de website worden verstuurd zijn niet geëncrypteerd. M.a.w. kwaadwillige personen kunnen de informatie onderscheppen, lezen en zelfs veranderen. Om dit te voorkomen moet columbia.edu een TLS/SSL certificaat aanschaffen dat de verbinding via HTTPS beveiligd.

{% hint style="info" %}
In moderne webbrowsers zoals Google Chrome worden websites die geen gebruik maken van HTTPS anders gemarkeerd. Het hangslot in de URL-balk geeft aan dat de webpagina veilig is.
{% endhint %}

### Wat doet TLS?

Het TLS-protocol bestaat uit drie hoofdcomponenten: encryptie, authenticatie en integriteit.

* **Encryptie**: verbergt de gegevens die worden overgedragen van derden.
* **Authenticatie**: zorgt ervoor dat de partijen die informatie uitwisselen, zijn wie ze beweren te zijn.
* **Integriteit**: controleert of de gegevens niet zijn aangepast of vervalst.

#### Bronnen

* [https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/](https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/)
