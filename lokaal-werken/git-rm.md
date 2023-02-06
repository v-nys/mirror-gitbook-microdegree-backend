# git rm

{% hint style="success" %}
[Kennisclip](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=0f6dbb0a-5ff6-4d8a-8202-ad9d00e19ca3) (sterk aangeraden dat je zelf de commando's toepast in een nieuwe testrepository)
{% endhint %}

## Betekenis

Via het commando `git rm` kan je een file verwijderen uit de working directory **en** noteer je dit meteen in de staging area. Dat laatste is belangrijk. Als je een file gewoon verwijdert, bijvoorbeeld door hem naar de prullenbak te verplaatsen, wordt hij beschouwd als "modified" en niet als "staged". En je kan een file die al verwijderd is wel stagen, maar het ziet er vreemd uit. Onderstaande demonstratie toont dit in een diagram. In de kolommen staan de verschillende onderdelen van een momentopname van je Git repository. De rijen stellen punten in de tijd voor, dus hoe verder naar beneden je gaat, hoe later de momentopname. Tussen de rijen staan acties die zorgen voor wijzigingen.

Je kan met de tools die je al kent een file verwijderen uit je working directory en uit versiebeheer als volgt:

![](<../.gitbook/assets/Screenshot from 2021-09-09 09-04-49.png>)

Bij `git rm` wordt de file ook uit de working directory verwijderd en toont "changes to be committed" (via `git status`) dat de volgende commit de file niet meer zal bevatten (dus vanaf dan wordt hij weer untracked). Dan krijg je het volgende:

![](<../.gitbook/assets/Screenshot from 2021-09-09 09-06-18.png>)

Je ziet dus dat er een tussenstap minder is tegenover wanneer je verwijdert en dan staget. Het standaardgebruik van `git rm` is dus vooral een snellere manier van werken.

Je kan ook `git rm --cached` gebruiken om het verwijderen van de file te stagen, zonder de file zelf te verwijderen. Dat kan nuttig zijn als je de file zelf wil bewaren, maar hem niet meer in versiebeheer wil opvolgen. Hij wordt dan terug untracked en je kan hem eventueel toevoegen aan `.gitignore`.

Dat kan je het volgende opleveren:

![](<../.gitbook/assets/Screenshot from 2021-09-09 09-07-03.png>)

Als je een van deze commando's op een map wil toepassen in plaats van op een gewone file, moet je `-r` toevoegen

| commando             | omschrijving                                                                                                    |
| -------------------- | --------------------------------------------------------------------------------------------------------------- |
| `git rm`             | verwijder een file en stage de verwijdering van deze file                                                       |
| `git rm -r`          | verwijder een volledige map en stage de verwijdering van deze map                                               |
| `git rm --cached`    | laat de file staan, maar stage toch de verwijdering van deze file (waardoor hij terug untracked zal worden)     |
| `git rm -r --cached` | laat de map staan, maar stage toch de verwijdering van deze map (waardoor de inhoud terug untracked zal worden) |
