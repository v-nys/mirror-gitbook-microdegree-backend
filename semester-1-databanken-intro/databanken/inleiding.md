# Inleiding

Een database \(of gegevensbank\) is een gestructureerde verzameling elektronische gegevens \(of data\) die door één of meerdere gebruikers \(of users\) gelijktijdig kunnen gemanipuleerd worden. De enorme hoeveelheden gegevens van banken worden beheerd in ultramoderne databases.

De database zelf, dat zijn dus de geordende gegevens. Maar gegevens zijn pas waardevol als er iets mee gedaan wordt. Het is de taak van een database management system \(DBMS\) om gegevens op te vragen, aan te passen, enzovoort.

Het DBMS moet er bovendien over waken dat de integriteit van de database behouden blijft. "Waken over integriteit" betekent bijvoorbeeld dat het juiste telefoonnummer bij de juiste persoon blijft horen, dat er geen personen zonder adres in het systeem geplaatst worden,...

Maar het DBMS doet veel meer dan alleen waken over integriteit. Zonder DBMS is het onmogelijk gegevens in een database onder andere te bekijken, te wijzigen, te verwijderen... Alleen het DBMS weet waar en hoe de gegevens in de database verwerkt moeten worden.

Een DBMS zal uiteraard nooit uit zichzelf de gegevens in een database opzoeken, wijzigen of verwijderen. Om dit te doen is steeds een specifieke opdracht van de gebruiker nodig. Bijvoorbeeld: "Verander het telefoonnummer van Jan Claessens van \(02\) 568 95 65 in \(03\) 574 23 84".

Dit soort instructie wordt echter niet in een natuurlijke taal gegeven. De meeste DBMS beschikken over een eigen taal voor instructies. Die taal heeft een specifieke "syntax", een stel regels om instructies te ontleden in hun bestanddelen. Deze regels gelijken een beetje op de regels die wij hanteren wanneer we Nederlands spreken. "Ga op die bank zitten" is een verstaanbare opdracht. We kunnen zeggen wat de taak is van elk woordje in deze Nederlandse zin. "Bank daar zitten ga op" is geen geldige zin. We kunnen als mensen nog wel raden naar de betekenis van deze zin, maar hij volgt de regels van de taal niet. Een machine zou het dan ook veel moeilijker hebben om er iets van te maken.

De regels van de talen waarmee men opdrachten kan geven aan een DBMS zijn dus veel strikter dan de regels voor het Nederlands: ze laten geen ruimte voor fouten. Een komma verkeerd volstaat om de opdracht onverstaanbaar en dus onuitvoerbaar te maken.

## **Voorbeeld 1**

Een klassiek voorbeeld daarvan is een lijst met de namen en adressen. Die lijst kan er als volgt uitzien:

| Naam     | Voornaam | Adres            | Postcode | Gemeente   | Telefoon     | Verdieping |
| -------- | -------- | ---------------- | -------- | ---------- | ------------ | ---------- |
| PIETERS  | PIeter   | Tralalastraat 25 | 2660     | Hoboken    | 03 333 33 33 | 1          |
| JANSSENS | Jan      | Jasstraat 2      | 2000     | Antwerpen  | 03 222 22 22 | 1          |
| DEBONDT  | Ron      | Jopstraat 5      | 2100     | Deurne     | 03 111 11 11 | 3          |
| JORIS    | Joost    | Boedreef 25      | 2600     | Berchem    | 03 444 44 44 | 2          |
| VOET     | Bart     | Plopstraat 9     | 2630     | Aartselaar | 03 888 88 88 | 3          |

In bovenstaand voorbeeld is de eerste rij de aanduiding van de kolommen (veldnamen).

Bovenstaand voorbeeld bevat dus vijf rijen (records) die telkens bepaalde waarden bevatten, hier gaat het over de "Naam", "Voornaam", "Adres", "Postcode", "Gemeente", "Telefoon" en "Verdieping".

## **Voorbeeld 2**

Een bedrijf in de productiesector zal onder andere volgende gegevens willen bijhouden, nl.:

* Personeelsgegevens&#x20;
* De zgn. productiegegevens. Hierbij kunnen we denken aan bv. de productsamenstelling
* De gegevens betreffende de noodzakelijke bestellingen
* De gegevens van de bestaande klanten&#x20;
* De gegevens van de leveranciers
* De gegevens m.b.t. de goederen die nog in stock zijn en/of de goederen die besteld moeten worden

In dit geval is het best om voor elk bullet point een aparte tabel te voorzien. Groepjes gegevens die sterk aan elkaar gelinkt zijn (bijvoorbeeld "voornaam werknemer" en "familienaam werknemer" komen in dezelfde tabel). Groepjes gegevens die losser gelinkt zijn komen in verschillende tabellen. Er zijn nog andere redenen om verschillende tabellen te gebruiken. Die komen later.

## **Voorbeeld 3**

Een bank houdt per rekening van een bepaalde klant geen box bij met daarin het geld van een klant. Het bedrag op de rekening van die klant is een cijfer dat wordt bijgehouden in een database. Er zou bijvoorbeeld een tabel `Rekeningen` kunnen zijn, die je je zo kan voorstellen:

| Klantnummer | Bedrag    | Type          |
| ----------- | --------- | ------------- |
| 123456789   | 15.000    | spaarrekening |
| 456789123   | 2.124.000 | belegging     |
| 789123456   | 11.000    | spaarrekening |

Daarnaast heeft de bank nog allerlei informatie, bijvoorbeeld over hypotheken,... Die zullen vermoedelijk in andere tabellen staan. De volledige verzameling tabellen vormt de database van de bank.
