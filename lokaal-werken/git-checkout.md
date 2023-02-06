# git checkout

In de eerdere voorbeelden heb je gezien dat je bijvoorbeeld eerst een beetje werk op een branch `main` kan doen, dan wat werk op `react`, dan wat werk op `angular`, dan weer op `main`. Maar we hebben nog niet in detail uitgelegd **hoe** dat werkt.

Bij een echte boom alle takken tegelijk een beetje. In Git niet. In Git is er meestal één tak **actief**. Die tak heeft een naam, gekozen door de ontwikkelaar zoals `main` of `react` of `angular`. Maar er is ook een algemene naam voor **de actieve tak** en dat is `HEAD`. Wanneer we committen schuift de tak waarnaar we verwijzen met `HEAD` dus een beetje op. Alsof de groeiknop wat verder vooruit beweegt omdat er hout ontstaat.

Via `git checkout <naam-van-branch>` kunnen we onze working directory terug laten overeenstemmen met een andere commit _en_ een andere branch de rol van `HEAD` laten spelen. Zo kunnen we een andere tak actief maken en dus code toevoegen op een branch naar keuze.

We bekijken een voorbeeld als tekening. Voer deze stappen zelf uit in een testrepository en vergelijk telkens de output van `git log --graph --all` met de tekening.

{% file src="../.gitbook/assets/stappen-met-checkout.pdf" %}
Reeks tekeningen voor onderstaand voorbeeld. Bekijk deze terwijl je de stappen bekijkt.
{% endfile %}

1. We starten met een nieuwe, lege repo. Er is nog geen enkele commit.
2. We doen een eerste commit op defaulttak `main`: vanaf dan is de waarde van `HEAD` `main` (en `main` verwijst naar de eerste commit, die we `abcdef` zullen noemen)
3. We doen een tweede commit op `main`: de waarde van `HEAD` blijft `main` (maar `main` verwijst nu naar de tweede commit, `fedcba`)
4. We maken een nieuwe branch, `featureA`: `HEAD` is nog steeds `main` en dat is nog steeds de tweede commit
5. We voeren een aanpassing uit op de actieve tak en committen die: `HEAD` blijft `main` (maar `main` verwijst nu naar de derde commit, `acebdf`)
6. We gebruiken `git checkout featureA`:
   * de (tracked) files in onze working directory zijn terug zoals ze waren na het uitvoeren van de tweede commit
   * `featureA` is nu `HEAD`
7. We committen iets
   * `featureA` blijft `HEAD`
   * maar `featureA` duidt nu de nieuwe commit `fdbeca` aan

Een tak hoeft niet te ontstaan op het uiteinde van een andere tak. In de natuur kan er een knop verschijnen halverwege een tak. In Git kan dat ook. Daarvoor gebruiken we eerst `git checkout <commit hash naar keuze>` om te springen naar een bepaald punt op onze "boom". Wanneer we dit doen (zelfs als de commit overeenkomt met een bestaande branch!), kunnen we niet meer zeggen welke tak `HEAD` is. `HEAD` moet immers **altijd** naar een branchnaam verwijzen. Op dat moment is je repository "headless" en kan je niet committen. Dat is niet erg. Het enige dat je moet doen om dit in orde te brengen, is zorgen dat er terug een groeiknop aangeduid wordt als actief. Dat kan door op die plaats op de boom een extra groeiknop aan te maken en die te activeren:

* `git branch <naam van de nieuwe branch>`
* `git checkout <naam van de nieuwe branch>`

Hier heb je een demonstratie in code. Je kan deze meevolgen door onderstaande zip te downloaden. Bekijk telkens goed het resultaat van de `git log` commando's. Wanneer er in Git bash tussen haakjes een commit hash staat en geen naam van een branch, bevindt de repository zich in een "headless" toestand.

{% file src="../.gitbook/assets/VoorbeeldRepo.zip" %}
Voorbeeldrepository. Download deze, navigeer er naartoe in git bash, voer onderstaande commando's uit en zorg dat het voor jezelf duidelijk is wat er telkens gebeurt.
{% endfile %}

* `git log --graph --all`
* `git checkout 960e777ef4b4eb4fa8c11ce9e6651f3c94db6554`
* `git log --graph --all`
* `git branch mijnnieuwebranch`
* `git checkout mijnnieuwebranch`
* `git log --graph --all`

En dan kan je committen op die nieuwe tak. Je kan nog steeds terug naar alle commits die je in het verleden hebt gemaakt. Je kan bijvoorbeeld terug switchen naar de tak die er al was via `git checkout main`.
