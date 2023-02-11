# Wat is een relationele databank

De "relationele" database is waarschijnlijk de meestgebruikte soort database. Dit type database is uitgewerkt in de jaren 1970 en steunt op de wiskundige verzamelingenleer.

Zonder deze wiskundige fundering in veel detail te behandelen: het basisidee is dat "interessante gehelen" van informatie in verzamelingen van één soort data worden opgedeeld. Deze "interessante gehelen" noemen we "entiteiten" en de verzamelingen noemen we "entiteittypes".

Tussen deze verzamelingen bestaan verbanden. Deze noemen we "relaties" (en een groepje pijlen met dezelfde betekenis noemen we een "relatietype").

Onderstaande figuur illustreert dit. Op deze figuur zijn de entiteittypes personen en boeken. Deze twee verzamelingen bestaan los van elkaar, maar er is een relatietype: sommige personen hebben sommige boeken gelezen.

{% hint style="warning" %}
Soms zeggen we gemakshalve "entiteit" of "relatie" wanneer we "entiteittype" of "relatietype" bedoelen. Uit de context moet dan duidelijk zijn wat bedoeld wordt.
{% endhint %}

![](../../.gitbook/assets/heeft-gelezen.png)

Er kunnen veel relatietypes zijn. We kunnen bijvoorbeeld een tweede verband hebben dat uitdrukt dat een bepaalde persoon een bepaald boek heeft geschreven:

![](../../.gitbook/assets/auteur-van.png)

Om dit in een elektronisch systeem voor te stellen, maken we geen tekeningen, maar gebruiken we tabellen. We stellen zowel entiteittypes als relatietypes voor door middel van tabellen, meerbepaald één tabel per entiteittype en één tabel per relatietype.

Voor de eerste tekening zou een tabelvoorstelling van de verzamelingen van entiteiten er zo kunnen uitzien:

| Voornaam | Familienaam | Geboortejaar |
| :--- | :--- | :--- |
| Vincent | Nys | 1987 |
| Esther | Nys | 1990 |
| Michiel | Nys | 1984 |
| William | Shakespeare | 1564 |
| Ted | Chiang | 1967 |
| Kazuo | Ishiguro | 1954 |

| Titel | Jaar van uitgave |
| :--- | :--- |
| The Tempest | 1623 |
| Exhalation: Stories | 2019 |
| Never Let Me Go | 2005 |

Eén **rij** (of "record") stelt dus één **entiteit** voor. Eén **kolom** stelt één eigenschap of **veld** van een entiteittype voor.

Ook het verband zou kunnen worden uitgedrukt met een tabel. Hoe dat precies werkt is voor later, maar een vereenvoudiging die een goed beeld geeft is als volgt:

| Lezer | Titel |
| :--- | :--- |
| Michiel | The Tempest |
| Vincent | Exhalation: Stories |
| Esther | Never Let Me Go |

Eén **rij** (of "record") stelt dus één **relatie** voor. Eén **kolom** stelt één deelnemer in de relatie voor.

Zowat alle DBMS'en voor relationele databases spreken \(ongeveer\) dezelfde taal: de "Structured Query Language" of SQL. Deze taal is ook gebaseerd op de relationele algebra's en ze maakt dat je vrij snel kan leren werken met één relationele database als je al met een andere relationele database overweg kan. Elk DBMS spreekt wel een eigen "dialect" van SQL, dus je kan niet verwachten dat code voor bijvoorbeeld PostgreSQL \(een type relationele database\) letterlijk kan worden uitgevoerd in SQLite \(een ander type relationele database\). Maar normaal moet je er niet veel aan aanpassen.

Typisch voor relationele databases is dat je op voorhand moet vastleggen wat de structuur van je database is: welke tabellen er zijn en wat voor gegevens hier in mogen worden geplaatst. Deze structuur noemen we het "schema". Als je nieuwe gegevens wil bijhouden die niet passen binnen de structuur, moet je eerst de structuur aanpassen. Dit is niet bij alle soorten databanken zo. Andere types databanken hebben soms een heel losse structuur. Dit geeft hen soms meer flexibiliteit, maar zorgt er soms ook voor dat ze minder kunnen waken over de integriteit van hun gegevens.

