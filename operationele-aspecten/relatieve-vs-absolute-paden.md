---
description: >-
  We gebruiken absolute en relatieve paden regelmatig wanneer we website gaan
  ontwikkelen. Ze worden gebruikt bij verwijzingen (links) of bij het opvragen
  van externe gegevens (scripts, stylesheet, afbe
---

# Relatieve vs absolute paden

### absolute verwijzing <a href="#absolute-verwijzing" id="absolute-verwijzing"></a>

Wanneer je wil verwijzen naar een webpagina die bij een andere website hoort, ga je gebruik maken van een absolute URL (Uniform Resource Locator). Bij een absolute verwijzing start de URL met het protocol van de verbinding, meestal `https`, gevolgd door de domeinnaam van de website. Eventueel met een specifieke locatie.\<a href="https://www.ap.be/graduaat/programmeren">Graduaat Programmeren\</a>

### relatieve verwijzing <a href="#relatieve-verwijzing" id="relatieve-verwijzing"></a>

Wanneer we echter gaan verwijzen naar pagina's van dezelfde website, hoeven we hiervoor de domeinnaam niet mee te geven. De browser weet namelijk al op welke website we aan het surfen zijn.\<p>Je kan ons \<a href="contact.html">hier\</a> contacteren.\</p>Relatieve verwijzingen bevatten vaak speciale symbolen die ervoor zorgen dat we kunnen bladeren op de webserver waarop we aan't werken zijn. Deze symbolen zijn afkomstig van de manier waarop webservers ontwikkeld worden en zijn gebasseerd op Linux.

* Starten met “/”: ga terug naar de _root directory_ en start hier
* Starten met “../”: ga 1 niveau omhoog en start daar
* Starten met “../../”: ga 2 niveaus omhoog en start daar
* Om niveaus te dalen, schrijf je de naam van het niveau gevolgd door een schuine streep
