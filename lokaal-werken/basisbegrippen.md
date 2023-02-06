# Basisbegrippen

## Wat bedoelen we met "fasen van data"?

Om Git goed te gebruiken, moet je goed beseffen op welke manier de tijdlijn voor ons project wordt opgebouwd. We noteren namelijk niet elke wijziging meteen op de tijdlijn - het zou bijvoorbeeld heel onoverzichtelijk zijn een nieuwe wijziging te noteren elke keer we een bestand opslaan. In plaats daarvan maken we voor elke gebeurtenis op de tijdlijn een soort "kladversie in potlood" en pas wanneer we tevreden zijn, zetten we de gebeurtenis "in pen" in op de tijdlijn. Je kan de tijdlijn dus zien als een gedetailleerd **logboek** van alle belangrijke aanpassingen die ooit gebeurd zijn in je project. We bekijken dit met een voorbeeld. We hebben code voor een website en we willen daaraan een "reset password" knop toevoegen. Welke stappen doorlopen we daarvoor? Onderstaande figuur toont ze alle vier, daarna volgt een uitleg van wat elke stap precies voorstelt.

### Oorspronkelijke tijdlijn

We hebben al code waaraan we deze nieuwe functionaliteit willen toevoegen. Ons beginpunt is dus een tijdlijn die al bestaat.

![Op 18 augustus hebben er "recente aanpassingen" plaatsgevonden](<../.gitbook/assets/Screenshot from 2021-09-03 11-34-56.png>)

### Eerste wijziging in potlood

Code om een wachtwoord te resetten staat normaal echter niet op dezelfde plaats als code voor de user interface. We doen eerst een eerste wijziging en voegen die "in potlood" toe aan ons klad.

![Bestaande tijdlijn met daarnaast nieuw klad in potlood](<../.gitbook/assets/Screenshot from 2021-09-03 11-35-52.png>)

### Alle wijzigingen staan samen in potlood

De volgende wijziging, die iets aanpast in de database, voegen we ook toe aan ons logboek.

![](<../.gitbook/assets/Screenshot from 2021-09-03 11-37-48.png>)

### Uitgebreide tijdlijn

Wanneer we tevreden zijn van onze kladversie, zetten we ze om naar een gebeurtenis op de tijdlijn.

![](<../.gitbook/assets/Screenshot from 2021-09-03 11-39-03.png>)

Het verschil tussen “niet genoteerd in het logboek”, “genoteerd in potlood” en “genoteerd in pen” bestaat ook in Git, maar wordt wat anders uitgedrukt.

## Overzichtsfiguur

Volgende figuur vertelt je de essentie van lokaal werken met Git. We raden aan dat je ze afdrukt, plastificeert en altijd in je laptoptas steekt:

![De essentie van lokaal werken met Git](<../.gitbook/assets/lifecycle (1).png>)

De figuur is uiterst nuttig, maar het is wel een vereenvoudiging. In het bijzonder de pijl "remove the file" verdient meer uitleg. Die komt aan bod bij de bespreking van [git rm](git-rm.md). Je mag hem voorlopig negeren.

{% hint style="warning" %}
Onderstaande uitleg moet je **door en door** begrijpen. Ook de termen zijn belangrijk. Wij spreken over "potlood" en "pen" om alles wat tastbaarder te maken, maar op de werkvloer doet men dat niet.
{% endhint %}

De toestanden kan je samenvatten als volgt:

* untracked: files met deze toestand staan wel in de **working directory**, dat wil zeggen in je bestandenstructuur beschouwd als gewone map en niet als Git repository, maar ze staan niet op de tijdlijn en niet in je kladwerk.
* staged: we hebben er iets over genoteerd in de **staging area**, dat wil zeggen "in potlood", maar moeten dat nog omzetten naar "pen" voor het op de tijdlijn komt. Er kan ook al oudere informatie op de tijdlijn staan.
* unmodified: alles staat in de **project history**, dat wil zeggen "op de tijdlijn". Anders gezegd, er is niets veranderd aan de file sinds er de laatste keer iets "in pen" over is genoteerd.
* modified: komt voor in de project history, maar bevat wijzigingen die nog niet terug te vinden zijn op de tijdlijn of in de staging area

## Voorbeeld

In de kennisclip wordt getoond hoe files van de ene toestand overgaan in de andere.
