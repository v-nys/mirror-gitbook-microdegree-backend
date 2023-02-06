# git init

{% hint style="success" %}
[Kennisclip](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=933d67bb-6e8d-4269-81bb-ad8d00dc5bd9)
{% endhint %}

## Wat doet `git init`?

Het commando `git init` is het eerste dat we moeten uitvoeren vooraleer we met versiebeheer aan de slag kunnen gaan. We voeren dit uit in de zgn. **root** (in het Engels: "wortel") van ons project. Dat is de map waarin alle files die met ons project te maken hebben rechtstreeks of onrechtstreeks staan. Dus ook files in mappen die zelf in deze map staan, behoren tot het project. We spreken van een root omdat een bestandensysteem een boomstructuur heeft.

Wanneer we `git init` uitvoeren, verschijnt er een verborgen map `.git` met informatie over de tijdlijn (en een aantal andere zaken). Door die map toe te voegen via dat commando, transformeren we onze root van een gewone map naar een **git repository**, d.w.z. een mappenstructuur die met Git beheerd wordt. **De map `.git` passen we nooit met de hand aan.** We verwijderen ze ook niet, want dan zijn we heel onze tijdlijn kwijt.

## Aandachtspuntjes

Er zijn een paar plaatsen waar je dit commando niet mag uitvoeren:

* Binnenin een repository. Technisch kan dit, maar het is niet wat je als beginner wil en zal tot vreemde fouten leiden. Je kan hier op controleren door, voor je `git init` uitvoert, een commando uit te voeren dat nooit iets aanpast (zoals [`git status`](git-status.md)). Dat zal je dan vertellen of je in een Git repository staat.
* In een map die automatisch synchroniseert (een OneDrive of Dropbox). Dat zal op het eerste zich werken, maar af en toe leidt het tot corruptie van onze data. Gelukkig is er een andere manier om backups van Git projecten in de cloud te plaatsen, waarover later meer.

## Demonstratie

Voor een demonstratie van dit commando, zie de kennisclip bovenaan de pagina.

## Gevolgen

Omdat alles wat te maken heeft met versiebeheer opgeslagen is in de map `.git`, kunnen we volgende conclusies trekken:

* Je mag een Git repository verplaatsen of kopiëren (zelfs naar een andere computer), op voorwaarde dat je `.git` meeneemt.
* **Je kan een kopie maken van je repository voor je commando's uitvoert die je nog niet volledig begrijpt. Je doet dit ook best,** want beginners schieten soms in paniek na een klein foutje. Met het systeem kan je terug naar oude versies, maar enkel als je zorgvuldig te werk gaat.

## Geheugensteuntjes

| commando   | omschrijving                            |
| ---------- | --------------------------------------- |
| `git init` | maak versiebeheer van deze map mogelijk |
