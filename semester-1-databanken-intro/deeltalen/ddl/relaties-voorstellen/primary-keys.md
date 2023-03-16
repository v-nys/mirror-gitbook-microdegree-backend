# Sleutels voor identificatie

## Motivatie

In theorie kan alle informatie in een MySQL-databank bijgehouden worden in één grote tabel. Dit leidt echter tot veel herhaling. Indien bijvoorbeeld bij elk boek alle informatie over een auteur (voornaam, familienaam, geboortedatum) wordt bijgehouden, voegen heel veel cellen in de tabel geen nieuwe informatie toe. Niet alleen is dit verspilling van opslagruimte, het vergroot ook het risico op inconsistentie van de data. Het is in deze situatie aan te raden om de tabel op te splitsen in verschillende tabellen, waarbij een of meerdere rijen van de ene tabel terug gelinkt kunnen worden aan een of meerdere rijen van de andere tabel. Dit vereist dat elke rij duidelijk geïdentificeerd kan worden.

## Rijen identificeerbaar maken

God of War, Doom en Tomb Raider zijn allemaal remakes van oude games met dezelfde titel en dezelfde ontwikkelaar. Een stukje van een tabel met games zou er dus als volgt kunnen uitzien:

| Titel | Ontwikkelaar |
| :--- | :--- |
| Doom | ID Software |
| Doom | ID Software |
| Tomb Raider | Crystal Dynamics |
| Tomb Raider | Crystal Dynamics |
| God of War | SCE Santa Monica |
| God of War | SCE Santa Monica |

Voor SQL is er geen verschil tussen de oude en de nieuwe versies van deze games, maar het gaat in werkelijkheid wel om verschillende zaken. Hier is elke rij dus niet duidelijk identificeerbaar. Het toevoegen van extra onderdelen zoals de uitgever,... kan hier misschien bij helpen, maar uiteindelijk moet **elke** rij **uniek** identificeerbaar zijn aan de hand van een of meerdere kolommen. Een stel kolommen waarmee je een rij uniek kan identificeren, kan dan aangeduid worden als **primaire sleutel of primary key**. Deze verzameling kolommen \(of ene kolom\) hoeft niet noodzakelijk "leesbare" informatie te bevatten. Vaak is het gewoon een getal, zoals in dit voorbeeld, waarin de kolom `Id` een primaire sleutel is:

| Titel | Ontwikkelaar | Id |
| :--- | :--- | :--- |
| Doom | ID Software | 1 |
| Doom | ID Software | 2 |
| Tomb Raider | Crystal Dynamics | 3 |
| Tomb Raider | Crystal Dynamics | 4 |
| God of War | SCE Santa Monica | 5 |
| God of War | SCE Santa Monica | 6 |

Als een \(verzameling van\) kolom\(men\) aangeduid is als primaire sleutel, is het onmogelijk twee rijen aan te maken die niet van elkaar onderscheiden kunnen worden.

## Sleutels voor efficiënt gebruik van ruimte

Tabellen zoals we ze eerder soms hebben gezien, zijn ook niet bruikbaar voor \(middel\)grote systemen omwille van een efficiëntieprobleem. Sleutels staan toe op grotere schaal te werken.

Veronderstel dat je, in opdracht van een keten van videogamewinkels, een databank met videogames moet opstellen. De klant wil volgende informatie in het systeem opslaan:

| Titel | Platform |
| :--- | :--- |
| Anthem | PS4 |
| Anthem | XBox One |
| Anthem | Windows |
| Sekiro: Shadows Die Twice | PS4 |
| Sekiro: Shadows Die Twice | XBox One |
| Sekiro: Shadows Die Twice | Windows |
| Devil May Cry 5 | PS4 |
| Devil May Cry 5 | XBox One |
| Mega Man 11 | PS4 |
| Mega Man 11 | XBox One |
| Mega Man 11 | Nintendo Switch |
| Mega Man 11 | Windows |
| Mass Effect: Andromeda | PS4 |
| Mass Effect: Andromeda | XBox One |
| Mass Effect: Andromeda | Windows |
| Dark Souls 3 | PS4 |
| Dark Souls 3 | XBox One |
| Dark Souls 3 | Windows |

Hier is elke rij wel verschillend, maar toch is er een probleem. Denk eraan dat we in onze definities zo precies mogelijk uitdrukken of iets VARCHAR,... is, hoe veel karakters er in passen,... Dat is omdat een databank zuinig moet zijn voor goede performantie. Bovenstaande tabel is dat niet: er zijn heel veel stukken lange tekst die regelmatig terugkomen en die nemen elke keer heel wat bytes in.

Zuinig zijn is bovendien niet alleen belangrijk voor performantie, maar helpt ook fouten te voorkomen. Hoe vaker een waarde herhaald moet worden, hoe groter de kans dat er fouten geïntroduceerd worden.

Het zou al zuiniger zijn elke game en elk platform aan te duiden met een uniek identificatienummer. Dat bespaart heel wat ruimte. Je kan bijvoorbeeld het volgende afspreken voor de titels:

* Anthem: 1
* Sekiro: Shadows Die Twice: 2
* Devil May Cry 5: 3
* Mega Man 11: 4
* Mass Effect: Andromeda: 5
* Dark Souls 3: 6

Voor de platformen:

* PS4: 1
* XBox One: 2
* Windows: 3
* Nintendo Switch: 4

Dan krijg je voor de hele tabel:

| Titel | Platform |
| :--- | :--- |
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 1 |
| 2 | 2 |
| 2 | 3 |
| 3 | 1 |
| 3 | 2 |
| 4 | 1 |
| 4 | 2 |
| 4 | 4 |
| 4 | 3 |
| 5 | 1 |
| 5 | 2 |
| 5 | 3 |
| 6 | 1 |
| 6 | 2 |
| 6 | 3 |

Merk op dat ook de mappings van games / platformen op getallen ook in tabellen passen. Deze tabellen hebben dan telkens 2 kolommen \(de game/het platform en het volgnummer\). Op deze manier blijft de oorspronkelijke informatie aanwezig in de database, maar is de voorstellingswijze zuiniger.

## Primaire sleutel toevoegen/verwijderen

### Toevoegen

#### Aan een bestaande tabel

Volgende instructie voegt een nieuwe kolom toe aan de tabel `Books`. Deze doet meteen dienst als primaire sleutel voor die tabel:

```sql
ALTER TABLE Books ADD COLUMN Id INT AUTO_INCREMENT PRIMARY KEY;
```

Het feit dat een kolom een primaire sleutel is, is een **constraint**. Men spreekt van een constraint als iets een beperking is. Als je een rij zou toevoegen met een `Id` waarvan de waarde reeds in een andere rij bestaat, krijg je een foutmelding. Een ander voorbeeld van een constraint is `NOT NULL`. Deze constraint is zwakker dan de `PRIMARY KEY` constraint \(omdat NULL niet geschikt is om een rij te identificeren\), dus je hoeft ze nooit toe te voegen aan een kolom die dient als primaire sleutel.

#### `AUTO_INCREMENT`

Het is vaak handig om de `Id` door SQL zelf te laten toekennen. De eigenschap `AUTO_INCREMENT` zorg hiervoor. In een nieuwe kolom volgt deze syntax op de declaratie van de kolom. Zorg ervoor dat je op die kolom een primary key constraint hebt staan:

```sql
CREATE TABLE Persons (
    Id INT AUTO_INCREMENT PRIMARY KEY,
    FirstName varchar(255) NOT NULL,
    LastName varchar(255) NOT NULL,
    Age int
);
```

Rijen zullen dan automatisch genummerd worden, te beginnen vanaf 1. Het is mogelijk te starten vanaf een ander getal door een waarde toe te kennen aan de `AUTO_INCREMENT` van een **tabel**:

```sql
ALTER TABLE Books AUTO_INCREMENT = 5;
```

Dit kan van pas komen als je al een deel van de data hebt en meer data wil importeren. SQL zal dan alleen voor de nieuwe data de nummers genereren.


#### Aan een nieuwe tabel

Het is niet erg handig om telkens de primaire sleutel achteraf toe te voegen. Het is ook mogelijk deze meteen toe te voegen bij aanmaak:

```sql
CREATE TABLE Books(
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Title varchar(100) NOT NULL
    Genre varchar(50) NOT NULL,
);
```

{% hint style="info" %}
Het is ook mogelijk `PRIMARY KEY` bij meerdere kolommen te schrijven. Dit wil dan zeggen dat deze kolommen **samen** een rij uniek identificeren en heet een "compound key". In deze tekst wordt hier verder geen gebruik van gemaakt.
{% endhint %}


### Verwijderen

Een constraint behoort tot de definitie van de tabel, dus deze wordt verwijderd via een subcommando van `ALTER TABLE`:

```sql
ALTER TABLE Boeken DROP PRIMARY KEY;
```


