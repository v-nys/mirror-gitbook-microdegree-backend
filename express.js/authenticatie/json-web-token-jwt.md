# JSON Web Token (JWT)

## Wat zijn JSON Web Tokens?

JWT's of JSON Web Tokens worden voornamelijk gebruikt om een geverifieerde gebruiker te identificeren. Ze worden uitgegeven door een authenticatieserver en worden gebruikt door de client-server (om de API's te beveiligen).

### Waarvoor worden JWT's gebruikt en waarom is het nodig?&#x20;

**Hier zijn enkele scenario's waarin JSON Web Tokens nuttig zijn:**

* **Autorisatie**: dit is het meest voorkomende scenario voor het gebruik van JWT. Zodra de gebruiker is ingelogd, bevat elk volgend verzoek de JWT, waardoor de gebruiker toegang krijgt tot routes, services en bronnen die alleen toegankelijk zijn tot ingelogde gebruikers.&#x20;
* **Informatie-uitwisseling**: JSON Web Tokens zijn een goede manier om veilig informatie tussen partijen te verzenden. Omdat JWT's kunnen worden ondertekend, bijvoorbeeld met behulp van public/private sleutelparen, kan je er zeker van zijn dat de afzenders zijn wie ze zeggen dat ze zijn. Aangezien de handtekening wordt berekend met behulp van de header en de payload, kan je bovendien controleren of er niet met de inhoud is geknoeid.

Je vraagt je misschien af waarom de authenticatieserver de informatie niet gewoon als een gewoon `JSON`-object kan verzenden en waarom deze moet worden omgezet in een "**token**".

Als de auth-server het als een gewone JSON verzendt, kan de client niet controleren of de inhoud die ze ontvangen correct is. Een kwaadwillende aanvaller zou bijvoorbeeld de gebruikers-ID kunnen wijzigen en de client zou op geen enkele manier kunnen weten dat dat is gebeurd.

Vanwege dit beveiligingsprobleem moet de authenticatieserver deze informatie verzenden op een manier die kan worden geverifieerd door de client, en hier komt het concept van een "token" in beeld.

Simpel gezegd, een token is een string die bepaalde informatie bevat die veilig kan worden geverifieerd. Het kan een willekeurige set alfanumerieke tekens zijn die naar een ID in de database verwijzen, of het kan een gecodeerde JSON zijn die door de client zelf kan worden geverifieerd.

### Wat is de JSON Web Token-structuur?&#x20;

In zijn compacte vorm bestaan JSON Web Tokens uit drie delen gescheiden door punten (.), namelijk:

1. **Header**, Bestaat uit twee delen:
   1. Het ondertekeningsalgoritme dat wordt gebruikt;
   2. Het type token, dat in dit geval "`JWT`" is;
2. **Payload**:
   1. De payload bevat de claims of het JSON-object;
3. **Signature**:
   1. Een tekenreeks die wordt gegenereerd via een cryptografisch algoritme dat kan worden gebruikt om de integriteit van de JSON-payload te verifiëren;

Daarom ziet een JWT er meestal als volgt uit.

```json
header.payload.signature
```

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Bron: <a href="https://supertokens.com/blog/what-is-jwt">https://supertokens.com/blog/what-is-jwt</a></p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p><a href="https://jwt.io/#debugger-io">https://jwt.io/#debugger-io</a></p></figcaption></figure>

Laten we de verschillende onderdelen opsplitsen.

#### Header&#x20;

De header bestaat doorgaans uit twee delen:&#x20;

1. Het type token, dat **JWT** is;
2. Het ondertekeningsalgoritme dat wordt gebruikt, zoals **HMAC** **SHA256** of **RSA**;

Bijvoorbeeld:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Vervolgens is deze JSON Base64Url-gecodeerd om het eerste deel van de JWT te vormen.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Encoded header (algorithm and token type)</p></figcaption></figure>

#### Payload&#x20;

Het tweede deel van het token is de payload, die de claims bevat. Claims zijn uitspraken over een entiteit (meestal de gebruiker) en aanvullende gegevens.&#x20;

Een JWT kan bijvoorbeeld een claim met de naam `name` bevatten die beweert dat de naam van de gebruiker "AP user" is. In een JWT wordt een claim weergegeven als een **key/value-pair** waarbij de key altijd een tekenreeks is en de value een JSON-waarde kan zijn. Het volgende JSON-object bevat bijvoorbeeld drie claims (`sub`, `name`, `iat`):

```json
{
   "sub": "1234567890",
   "name": "AP user",
   "iat": "1516239022"
}
```

Vervolgens de payload ook JSON Base64Url-gecodeerd om het tweede deel van de JWT te vormen.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Encoded payload (claims)</p></figcaption></figure>

#### Signature

Om het handtekeninggedeelte te maken, moet je de gecodeerde header, de gecodeerde payload, een geheim, het algoritme gespecificeerd in de header nemen en dat ondertekenen.

Als je bijvoorbeeld het HMAC SHA256-algoritme wilt gebruiken, wordt de handtekening op de volgende manier gemaakt:

```json
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

De handtekening wordt gebruikt om te verifiëren dat het bericht onderweg niet is gewijzigd, en in het geval van tokens die zijn ondertekend met een geheim (`secret`), kan het ook verifiëren dat de afzender van de JWT is wie het zegt te zijn.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Encoded header, payload en secret</p></figcaption></figure>

### Alles bij elkaar zetten

De uitvoer bestaat uit drie Base64-URL-tekenreeksen gescheiden door punten die gemakkelijk kunnen worden doorgegeven in HTML- en HTTP-omgevingen.

Het volgende toont een JWT met de vorige header en payload gecodeerd en is ondertekend met een geheim.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Een JWT met de vorige header en payload gecodeerd en ondertekend met een geheim</p></figcaption></figure>

{% hint style="info" %}
Als je met JWT wilt spelen en deze concepten in de praktijk wilt brengen, kan je [jwt.io Debugger](https://jwt.io/#debugger-io) gebruiken om JWT's te decoderen, verifiëren en genereren.
{% endhint %}

### Hoe werken JSON-webtokens?

Wanneer een gebruiker zich succesvol aanmeldt met zijn inloggegevens, wordt er een JSON-web token geretourneerd. Aangezien een JWT wordt gebruikt voor authenticatie, moet grote zorg worden besteed aan het voorkomen van beveiligingsproblemen. Over het algemeen mag je tokens niet langer bewaren dan nodig is.

Houd er ook mee rekening dat voor ondertekende tokens informatie, hoewel beschermd tegen manipulatie, voor iedereen leesbaar is. Plaats geen geheime informatie in de payload of header-elementen van een JWT, tenzij deze versleuteld zijn.

Telkens wanneer de gebruiker toegang wil tot een beschermde route of bron, moet de gebruiker in kwestie de JWT mee verzenden in de header van de request. De beveiligde routes van de server controleren op een geldige JWT in de Authorization-header en als deze aanwezig is, krijgt de gebruiker toegang tot beveiligde bronnen.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Bron: <a href="https://www.simplilearn.com/tutorials/nodejs-tutorial/jwt-in-express-js">https://www.simplilearn.com/tutorials/nodejs-tutorial/jwt-in-express-js</a></p></figcaption></figure>

#### Resources

* [Wat is JWT?](https://jwt.io/introduction)
* [Waar en hoe kan je het toepassen?](https://supertokens.com/blog/what-is-jwt)
* [https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-token-claims](https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-token-claims)
* [JWT in express met jsonwebtokens, crypto en dotenv](https://www.digitalocean.com/community/tutorials/nodejs-jwt-expressjs)
