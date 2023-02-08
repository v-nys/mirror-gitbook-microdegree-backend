# FriendFace
Bij deze module hoort één project, *FriendFace*. FriendFace is een kleine sociale netwerksite met de belangrijkste functionaliteit van een typisch sociaal netwerk. Je kan veilig aanmelden, vriendschappen sluiten, berichten posten, reageren op berichten, lid worden van een groep,...

Je kan ook aanmelden als beheerder om allerlei statistieken op te vragen of om zaken manueel aan te passen.

Dit alles vereist een aantal zaken:

- Een database die je toestaat efficiënt informatie op te vragen en aan te passen, die je met TypeScript kan bevragen. MySQL is hier geschikt voor.
- Een web framework dat requests van een browser kan vertalen naar opdrachten voor de database. Dit doen we met Express.js.
- Een efficiënte setup van je werkomgeving, zodat je je code niet telkens hoeft aan te passen wanneer je ze op een andere machine wil gebruiken. Git, Docker en remote dev containers spelen hier een belangrijke rol.
- Een frontend voor je sociaal netwerk, die je zal opbouwen met kennis opgedaan in de vorige module. We blijven dus verder werken met React en we besteden nog steeds aandacht aan de eerder geziene concepten.
- Web hosting met een SSL-certificaat voor een makkelijk te bereiken, veilige website. Hiervoor configureren we SSH, DNS en een reverse proxy.