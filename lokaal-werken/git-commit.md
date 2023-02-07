# git commit

## Betekenis

Met het commando git commit verplaatsen we wijzigingen van de staging area naar een nieuwe punt (een **commit**) in de project history. We zetten "potlood" dus om naar "pen".

## Werking

Nadat je de gewenste wijzigingen in de staging area hebt geplaatst ("nadat je klad af is"), gebruik je het commando `git commit` . Dan wordt er een text editor geopend. Hier typ je een omschrijving die je helpt versies te doorzoeken, typisch een uitleg van wat de gemaakte wijzigingen hebben bereikt. Je kan ook gebruik maken van `git commit -m "<omschrijving>"` (waarbij je zelf een omschrijving van de commit invult, zonder `<` en `>`). Dat gaat soms wat sneller, omdat er geen text editor geopend moet worden.

## Demonstratie

Zie de kennisclip voor een demonstratie van dit commando in de praktijk.

| commando                            | omschrijving                                                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `git commit -m "<jouw tekst hier>"` | maak een nieuwe gebeurtenis op de tijdlijn door alle wijzigingen in de staging area te groeperen en toe te lichten met jouw tekst |
| `git commit`                        | hetzelfde, maar gebruik je text editor om de toelichting in te vullen                                                             |
