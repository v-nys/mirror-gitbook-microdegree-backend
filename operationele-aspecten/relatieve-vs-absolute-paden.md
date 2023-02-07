---
description: >-
  We gebruiken zowel absolute als relatieve paden regelmatig wanneer we een
  website ontwikkelen. Ze worden gebruikt bij links of bij het opvragen van
  externe gegevens.
---

# Relatieve vs absolute paden

### absolute verwijzing <a href="#absolute-verwijzing" id="absolute-verwijzing"></a>

Wanneer je wil verwijzen naar een webpagina die bij een andere website hoort, ga je gebruik maken van een absolute URL. Bij een absolute verwijzing start de URL met het protocol van de verbinding, meestal `https`, gevolgd door de domeinnaam van de website. Eventueel met een specifieke locatie. Bijvoorbeeld: `<a href="https://www.ap.be/graduaat/programmeren">Graduaat Programmeren</a>`.

### relatieve verwijzing <a href="#relatieve-verwijzing" id="relatieve-verwijzing"></a>

Wanneer we echter gaan verwijzen naar pagina's van dezelfde website, hoeven we hiervoor de domeinnaam niet mee te geven. De browser weet namelijk al op welke website we aan het surfen zijn. Bijvoorbeeld: `<p>Je kan ons <a href="contact.html">hier</a> contacteren.</p>`Relatieve verwijzingen bevatten vaak speciale symbolen die ervoor zorgen dat we kunnen bladeren op de webserver waarop we aan het werken zijn. Deze symbolen zijn afkomstig van de manier waarop webservers ontwikkeld worden en zijn gebaseerd op het UNIX-bestandensysteem.

* Starten met “/”: ga terug naar de _root directory_ en start hier
* Starten met “../”: ga 1 niveau omhoog vanaf de huidige locatie en start daar
* Starten met “../../”: ga 2 niveaus omhoog en start daar
* Om niveaus te dalen, schrijf je de naam van het niveau gevolgd door een schuine streep
* Soms zie je ook ”.”. Dat duidt dan op het huidige niveau. Zo kan je in `mijnbestand` verwijzen naar `anderbestand` als "anderbestand" of als "./anderbestand".
