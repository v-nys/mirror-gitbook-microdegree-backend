# vreemde sleutels

## Concept

Primaire sleutels dienen om rijen uniek te identificeren. Dit is alleen zinvol als er ook ergens naar deze rijen verwezen wordt. Met andere woorden, als kolom A een primaire sleutel is van tabel B, is het logisch in kolom C van tabel D over deze sleutel te spreken. Dit zit ook in het systeem achter een vestiaire: het is niet zinvol **alleen** een nummer op een kledingstuk te hangen **of** aan een persoon te overhandigen. Beide moeten samen gebeuren.

Wanneer we in één record via een bepaalde kolom verwijzen naar (de sleutel van) een ander record, spreken we over een **vreemde sleutel** of **foreign key**. Hij is "vreemd" omdat hij verwijst naar een **ander** record.

Kolommen die dienst doen als foreign key moeten in ieder geval van hetzelfde type zijn als de primary key kolommen waarmee ze overeenstemmen. Het zou ook geen steek houden om in een vestiaire Romeinse cijfers te gebruiken voor de kaartjes op kledingstukken en Arabische cijfers voor de kaartjes die aan de gasten overhandigd worden.

Daarnaast kan een SQL-systeem afdwingen dat waarden in een foreign key kolom **altijd** bij een waarde in de overeenkomstige primary key kolom horen. Anders gezegd: er mag in principe niemand met het ticketje "100" op een feest rondlopen wanneer dat zelfde ticketje niet op een kledingstuk hangt.

## Gebruik in een nieuwe tabel

Er spelen drie zaken mee:

1. de naam van de constraint
2. de kolom die moet dienen als foreign key
3. de kolom die dienst doet als primary key in de tabel waarnaar verwezen wordt

Dat ziet er bijvoorbeeld zo uit, als je een tabel `Books` koppelt aan hun auteur, die al ergens bestaat in een tabel `Persons`:

```sql
CREATE TABLE Books (
  Id INT AUTO_INCREMENT PRIMARY KEY,
  Persons_Id INT,
  CONSTRAINT fk_Books_Persons FOREIGN KEY (Persons_Id)
  REFERENCES Persons(Id)
);
```

Dit wil zeggen: "maak een tabel voor boeken met een uniek identificatienummer (de primary key); boeken kunnen ook verwijzen naar specifieke records in de tabel die personen voorstelt; deze verwijzingen worden voorgesteld met de kolom `Persons_Id` **in de tabel voor boeken**".

Hierbij gebruiken we enkele **afspraken**:

* De naam van **de kolom** die dienst doet als foreign key is de naam van de tabel waarnaar verwezen wordt, gevolgd door `_Id`.
* De naam van een foreign key **constraint** is altijd `fk_`, gevolgd door de naam van de tabel waarop de constraint toegepast is, gevolgd door de naam van de tabel waarnaar verwezen wordt.

{% hint style="warning" %}
In tegenstelling tot een `PRIMARY KEY` constraint, impliceert een `FOREIGN KEY` constraint niet dat een kolom `NOT NULL` is. Het kan in bovenstaand voorbeeld dus dat een boek geen auteur heeft.
{% endhint %}

## Gebruik in een bestaande tabel

Een tabel uitbreiden met een foreign key gebeurt via de `ALTER`-instructie. Als je bijvoorbeeld al een tabel voor boeken had zoals hierboven, maar zonder de kolom `Persons_Id`, zou je dit schrijven:

```sql
ALTER TABLE Books
ADD COLUMN Persons_Id INT,
ADD CONSTRAINT fk_Books_Persons
  FOREIGN KEY (Persons_Id)
  REFERENCES Persons(Id);
```

## Constraint verwijderen

Je kan een foreign key constraint verwijderen via de naam, bijvoorbeeld:

```sql
ALTER TABLE Books
DROP FOREIGN KEY fk_Books_Persons;
```

{% hint style="warning" %}
Dit verwijdert de kolom niet. Het zorgt er alleen voor dat het DBMS niet meer afdwingt dat de verwijzingen naar een primary keywaarde op een andere plaats zijn.
{% endhint %}
