# git clone

{% hint style="success" %}
[Kennisclip](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=709e7633-87a4-47af-96c3-ad9d00e2dfd1)
{% endhint %}

## Wat doet dit commando?

Je weet intussen dat het mogelijk is samen te werken aan hetzelfde project door middel van remotes. We hebben ook gezien dat je een remote kan toevoegen met `git remote add`, maar wat als je gewoon wil beginnen meewerken aan een bestaand project?

Dan gebruik je het commando `git clone`. Dit commando haalt de huidige tijdlijn van een bestaand project af **en** stelt dat bestaand project meteen in als remote.

{% hint style="danger" %}
Net als `git init`, moet je dit commando maar één keer uitvoeren per project. Nog specifieker: je moet **ofwel** `git init` ofwel `git clone` één keer per project uitvoeren, maar nooit een combinatie van beide. Beide zorgen voor een map `.git`.
{% endhint %}

## Demonstratie

Het gebruik van `git clone` met Gitlab wordt gedemonstreerd in de kennisclip.
