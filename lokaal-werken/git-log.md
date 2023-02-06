# git log

{% hint style="success" %}
[Kennisclip](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=b8ecd71f-c612-4940-bbd0-ad9e0084a817)
{% endhint %}

## Betekenis

Met het commando `git log` geef je de tijdlijn weer. Bovenaan in de uitvoer zie je de recentste commit en naarmate je naar beneden gaat, zie je oudere commits. Via `git log --graph` zie je de uitvoer duidelijker als een "tijdlijn", dus we raden aan dat je die versie van het commando gebruikt.

Elke commit bevat wat informatie, waaronder de naam van de persoon die de wijzigingen heeft uitgevoerd, het e-mailadres, de datum waarop de commit heeft plaatsgevonden en de commit message. Het belangrijkste stukje informatie is echter de **commit hash**. Dit is een code van 20 bytes genoteerd in een hexadecimale notatie, wat een reeks 40 symbolen van 0 tot 9 en A tot en met F oplevert.

De commit hash kan je zien als een "vingerafdruk" van elke commit. Hij identificeert elke individuele commit, want zowat elke wijziging aan je repository heeft een invloed op de volgende hash die berekend zal worden.

De hash is geschikter om een commit aan te duiden dan een datum. Dat heeft er mee te maken dat je aanpassingen niet altijd genoteerd worden op een tijdlijn in de volgorde waarin ze hebben plaatsgevonden. Hierop gaan we dieper in wanneer we [`git branch`](git-branch.md) bespreken. Het heeft er ook mee te maken dat meerdere personen rond dezelfde tijd aan een project kunnen werken.

## Geheugensteuntje

| commando          | omschrijving                                                                                                                           |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `git log --graph` | toon de tijdlijn vanaf het punt waar je nu zit, tot het begin, met telkens de commit hash, auteur, datum van de commit en de boodschap |
