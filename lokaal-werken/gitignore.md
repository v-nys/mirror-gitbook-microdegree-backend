# gitignore

{% hint style="success" %}
* [Kennisclip basis](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=ed0a016d-8b01-44c6-a9e8-ad9e00e46e55)
* [Kennisclip niet-letterlijke patronen](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=a926940c-dbf6-4697-9211-ad9f0087379b)
{% endhint %}

Je wil niet altijd alle data die je produceert bijhouden in versiebeheer. Dat hoeft ook niet. De file `.gitignore` staat je toe bepaalde bestanden uit te sluiten.

Enkele voorbeelden van bestanden die je niet wil bijhouden:

* tijdelijke bestanden die aangemaakt worden wanneer je een programma compileert
  * hiervan kom je een voorbeeld tegen bij de compilatie van C#-programma's: voor je je eigen code uitvoert (dit is anders bij executables), worden er mappen `bin` en `obj` aangemaakt. Deze bevatten data die nodig is om je programma uit te voeren, maar die volledig gegenereerd wordt uit jouw code.
    * een voorbeeld hiervan vind je terug in de kennisclip
* bestanden die specifiek zijn voor jouw systeem
  * voorbeeld: settingsbestand met daarin persoonlijke logingegevens

Omdat er in bijna elk project wel van die bestanden zijn, staat Git toe om ze uit te sluiten van versiebeheer. Dat betekent dat ze als het ware onzichtbaar zijn: ze kunnen alleen bestaan in de working directory en worden niet vermeld in berichten gegenereerd door Git.

Om een bestand te negeren, moet je eerst een bestand `.gitignore` aanmaken. Je bestand moet dus letterlijk `.gitignore` heten, dus met een punt als eerste karakter en zonder bestandsextensie. Daarin plaats je dan per regel de naam van een bestand dat niet meer zichtbaar mag zijn voor Git. Je kan ook namen van mappen schrijven (om alle bestanden in die mappen te negeren).

Wij zullen voorlopig .gitignore altijd in de root van onze boomstructuur plaatsen. Je kan ook .gitignore-bestanden in submappen plaatsen, maar dat is niet zonder gevolgen. Leer eerst de basis.

{% hint style="info" %}
Weet je niet goed wat bedoeld wordt met "in de root"? Bekijk dan nog eens de uitleg over boomstructuren op de pagina over [git init](git-init.md).
{% endhint %}

## Verdere details

Je hebt bijvoorbeeld een bestand .gitignore dat er als volgt uitziet:

.gitignore:

```
a.txt
b.sql
d.svg
cache
```

Je files zien er bijvoorbeeld zo uit:

```
root
├─.git
├─.gitignore
├─a.txt
├─b.sql
├─c.html
├─d.svg
└─cache
  ├─urls.txt
  └─names.md
```

Als je dan de files a.txt, b.sql, c.html, d.svg, cache/urls.txt, cache/names.md maakt, dan kan je enkel c.html **en .gitignore zelf** verplaatsen naar de staging area (en van daar naar de projectgeschiedenis). Van de map `.git` hoef je je niets aan te trekken, je moet je geen geschiedenis van je geschiedenis bijhouden.

{% hint style="warning" %}
**.gitignore sluit alleen untracked bestanden uit!** Als a.txt bijvoorbeeld al deel uitmaakte van de projectgeschiedenis voor .gitignore is aangemaakt, blijft a.txt deel uitmaken van de projectgeschiedenis en kan je wijzigingen aan a.txt stagen en committen alsof er geen .gitignore was.
{% endhint %}

## De rol van folderstructuur

Normaal gesproken matcht een patroon op elk niveau in de boomstructuur. Het maakt dus niet uit of een te negeren bestand in de root staat of in een submap. Veronderstel dat je hetzelfde bestand `.gitignore` hebt als tevoren en volgende bestandenstructuur:

```
root
├─ .git
├─ .gitignore
├─ a.txt
├─ bin
│  ├─ a.txt
│  ├─ cache
│  │  └─ e.gv
│  └─ pkg
│  └─ f.pkg
├─ b.sql
├─ cache
│  ├─ names.md
│  └─ urls.txt
├─ c.html
└─ d.svg
```

Met deze folderstructuur kan je `.gitignore`, `c.html` en `f.pkg` (in de map `bin/pkg`) stagen en committen. Je kan de files die in .gitignore vermeld zijn niet stagen en committen. Dus ook niet `e.gv`, want die is een onderdeel van `cache`!

De map `pkg` zal dan weer genegeerd worden, want Git houdt geen rekening met lege mappen.

## Demonstratie

* maak de .gitignore file en de folderstructuur van hierboven na
* run `git status -u` (details volgen later)
* run `git add --all` (omdat dit dus niet echt "alle bestanden" betekent)
* run `git status -u`

## Niet-letterlijke patronen

Het is niet altijd praktisch om elk bestand te benoemen dat je wil negeren. Soms heb je meer algemene regels nodig. Er zijn dan ook een aantal zaken die je kan noteren in `.gitignore` die niet letterlijk gelezen worden als bestandsnamen. We geven hier slechts een kort overzicht van de meest voorkomende. Op termijn kom je misschien in een situatie waarin je meer nodig hebt. Dan kijk je best naar [de officiële documentatie](https://git-scm.com/docs/gitignore).

### Commentaar

Soms wil je een woordje uitleg toevoegen om te zeggen wat de redenering achter een bepaald patroon is. Dan begin je een regel met een `#`. Deze stemt niet overeen met een `#` in de naam van een map of van een bestand, maar zorgt ervoor dat de regel niet bekeken wordt door het systeem. Als je toch ooit een bestand wil uitsluiten dat begint met een `#`, kan dat door `\#` te noteren in je `.gitignore`.

### Directory separator

Een `/` geeft de grens tussen mappen aan. We noemen de `/` daarom ook de directory separator (_directory_ = map, _separator_ = iets dat een scheiding aangeeft). Zo kan je bijvoorbeeld, met de mappenstructuur iets hoger op deze pagina, `bin/cache` wel negeren en `cache` net onder de root niet. Deze directory separator is geen letterlijk symboo,l want op Windows wordt de grens tussen mappen aangegeven met een `\`, dus een backslash, maar toch schrijven we in `.gitignore` een `/`.

### Asterisk

Soms wil je hele groepen bestanden negeren op basis van hun naam of bestandsextensie. Je hebt misschien een reeks `.pdf` bestanden met gegenereerde documenten. In de plaats van `document1.pdf`,... kan je beter alle `.pdf`-bestanden in dat project negeren. Om dit te doen, schrijf je `*.pdf`. Een `*` matcht met alles, behalve een directory separator. In de praktijk kan het misschien lijken alsof `*` ook matcht met een directory separator, maar dat is omdat, zoals eerder gezegd, een patroon matcht op elk niveau in de bestandenstructuur.

## Verdere mogelijkheden

Zoals je ziet, kan `.gitignore` soms wat puzzelwerk vragen. Bovendien zijn er nog veel meer mogelijkheden. Leer dus de mogelijkheden die we hier besproken hebben en zoek de rest op in de officiële documentatie wanneer je ze nodig hebt.
