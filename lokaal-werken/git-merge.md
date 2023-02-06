# git merge

We hebben al gezien dat je bijvoorbeeld een aparte tak kan maken voor feature A, voor feature B, enzovoort. Maar in een realistische situatie wil je niet altijd één tak kiezen om mee verder te werken en al de rest overboord gooien. Je wil onafhankelijk ontwikkelde features vaak **samen** brengen in één versie van je code, die je dan aan de gebruiker aflevert. Om dat klaar te spelen, gebruiken we het het commando `git merge`. Meerbepaald: `git merge <naam van een andere tak>` zal een nieuwe commit maken waarin die andere tak terug samengevoegd wordt met het werk op `HEAD`.

Dat klinkt nogal technisch, maar het is ongeveer wat je hier ziet:

![Het kanaal splitst, maar komt terug samen in de rechterbenedenhoek.](../.gitbook/assets/splitsing-rivier.png)

Laat ons dat nu eens in code bekijken. Download onderstaande repository.

{% file src="../.gitbook/assets/VoorbeeldMerge (1).zip" %}

Bekijk de geschiedenis van deze repository met `git log --graph --all --oneline`. Na de eerste commit (met boodschap "Startpunt pagina") is er een splitsing geweest. Op `main` tak is er een contactpagina toegevoegd, op de andere tak (`mooie-layout`) er aanpassingen aan de layout gebeurd zijn. Daarna is, terwijl `HEAD` naar `main` wees, het commando `git merge mooie-layout` uitgevoerd. Dit leverde ons uiteindelijk een commit met alle wijzigingen samen.

Het commando `git merge` had hierbij geen hulp nodig van de programmeur. Dat komt omdat de wijzigingen op beide branches eigenlijk volledig los stonden van elkaar. Er zijn geen aanpassingen gebeurd aan dezelfde code. Vaak zal een merge iets meer denkwerk vereisen. Git ziet immers alleen tekst. Het begrijpt geen programmeertalen en kan ook niet raden wat jij uiteindelijk wil. Als je in zo'n situatie een merge probeert te doen, krijg je een "merge conflict". Dat wil niet zeggen dat een merge onmogelijk is, maar wel dat je een beetje zal moeten helpen om te bepalen hoe de nieuwe commit er precies moet uitzien.

Zo'n merge conflict is opgetreden toen we probeerden `layoutstijl2` te mergen in `layoutstijl1`.  Dat komt omdat beide branches aanpassingen aan dezelfde file bevatten. Om dit probleem op te lossen, hebben we een merge tool gebruikt.

{% embed url="https://meldmerge.org" %}
Meld is een goede merge tool met een duidelijke grafische interface. Download en installeer deze.
{% endembed %}

Met een merge tool zoals Meld kunnen we het beste van elke wereld overhouden en eventueel wat extra code toevoegen om fixes aan te brengen.

Probeer dit zelf eens als volgt (als het misloopt, kan je de repository opnieuw downloaden):

1. Zorg dat Meld geïnstalleerd is.
2. `git checkout b60cdc6` (dit brengt je naar het punt waarin we layoutstijl2 hebben samengesmolten)
3. `git branch herhaling-layout-stijl1` (dit maakt een nieuwe tak, waarin je het proces van de merge kan herhalen)
4. `git checkout herhaling-layout-stijl1`
5. `git merge layoutstijl2` (dit voegt die tak samen met de actieve tak)
6. `git mergetool` (dit geeft aan dat je een tool wil opstarten op het merge conflict op te lossen)
7. Kies in het middenste venster in Meld telkens de aanpassing die je wil overhouden. Je kan dit doen door op een pijltje vanuit het linkervenste of rechtervenster te klikken. Doe dit tot het voor elk conflict duidelijk is hoe je het wil oplossen.
8. Sla de middenste file op en sluit Meld.

Nadat we onze middenste file hebben opgeslagen met de gewenste aanpassingen, checken we even de status. Onze (samengevoegde) file is al gestaged. We zien ook dat er verschillende untracked files zijn bijgekomen. Deze mag je verwijderen. Ten slotte committen we alles wat al gestaged is. Dit levert ons een nieuwe commit die voortbouwt op beide branches. Dit is wat je in de output van git log `--graph --all --oneline` ook ziet bij `layoutstijl1`.

Nadat je een merge hebt uitgevoerd, ga zal je typisch de tak die in de andere tak gemerged is verwijderen. Dat zou hier als volgt zijn: `git branch -d layoutstijl2`

Een merge vindt kan niet alleen plaatsvinden wanneer je twee lokale takken samenvoegt. Hij kan ook plaatsvinden wanneer je via `git pull` werk van een remote samenvoegt met werk dat je lokaal al hebt gemaakt. Daarom kan je bij `git pull` soms een "merge conflict" krijgen. De manier om dit op te lossen is dezelfde als bij een lokale merge.

Schrik er dus niet van als er een merge conflict optreedt, want dat hoort er bij. Het betekent niet dat iemand een fout heeft gemaakt.

Als laatste kanttekening: een merge conflict kan optreden bij `git pull`, maar een `git push` kan verhinderd worden om dezelfde reden, namelijk dat er al werk op de remote staat dat we zelf nog niet hebben. Om dat op te lossen, doe je eerst een pull, dan los je het conflict op en daarna voer je de push uit.
