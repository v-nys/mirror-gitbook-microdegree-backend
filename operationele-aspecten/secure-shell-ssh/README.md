# Secure Shell (SSH)

Secure Shell (SSH) is een netwerkprotocol dat veilige communicatie tussen twee computers mogelijk maakt. Het wordt vaak gebruikt om op een veilige manier toegang te krijgen tot een externe computer via internet, bijvoorbeeld om in te loggen op een server en opdrachten uit te voeren, of om bestanden veilig over te zetten tussen computers. SSH maakt gebruik van encryptie om de gegevens die worden verzonden te beschermen, wat het moeilijk maakt voor onbevoegden om de informatie te onderscheppen en te lezen. Het is een belangrijk hulpmiddel voor netwerkbeveiliging.

Het biedt een op tekst gebaseerde interface met behulp van een externe [shell](../wat-is-een-shell.md). Nadat je verbinding hebt gemaakt, worden alle opdrachten die je in je lokale terminal typt, naar de externe server verzonden en daar uitgevoerd.

### Hoe werkt SSH?

Wanneer je verbinding maakt via SSH, word je in een shell-sessie gedropt, een op tekst gebaseerde interface waar je met je server kan communiceren. Voor de duur van je SSH-sessie worden alle opdrachten die je in je lokale terminal typt, door een gecodeerde SSH-tunnel verzonden en uitgevoerd op de server.

De SSH-verbinding wordt geïmplementeerd met behulp van een client-servermodel. Dit betekent dat om een SSH-verbinding tot stand te brengen, de externe machine een stukje software moet draaien dat een **SSH-daemon** wordt genoemd. Deze software luistert naar verbindingen op een specifieke netwerkpoort, verifieert verbindingsverzoeken en brengt de juiste omgeving tot stand als de gebruiker de juiste inloggegevens verstrekt.

De computer van de gebruiker moet een **SSH-client** hebben.

### Authenticatie met SSH

Gebruikers authenticeren zich over het algemeen met wachtwoorden (minder veilig en niet aanbevolen) of **SSH-sleutels**.

Wachtwoordaanmeldingen zijn gecodeerd en zijn gemakkelijk te begrijpen voor nieuwe gebruikers. Geautomatiseerde bots en kwaadwillende gebruikers kunnen echter herhaaldelijk proberen zich te authenticeren bij accounts die op wachtwoorden gebaseerde logins toestaan. Om deze reden wordt er aangeraden om voor de meeste configuraties altijd op SSH-sleutel gebaseerde authenticatie in te stellen.

SSH-sleutels zijn een overeenkomende set cryptografische sleutels die kunnen worden gebruikt voor authenticatie. Elke set bevat een **public key** en een **private** **key**. De public key kan vrij en zonder zorgen worden gedeeld. De private key moet worden bewaakt en mag aan niemand worden blootgesteld.

{% hint style="info" %}
De publieke sleutel is vergelijkbaar met je brievenbus. Iedereen ziet dat ze van jou is en je kan er normaal alleen documenten in deponeren. De private sleutel is vergelijkbaar met de sleutel van je brievenbus. Enkel jij hebt er een en deze staat je toe informatie terug uit de brievenbus te halen.
{% endhint %}

Om te authenticeren met behulp van SSH-sleutels, moet een gebruiker een SSH-sleutelpaar op zijn lokale computer hebben. Op de **externe** server moet de **openbare** sleutel worden gekopieerd naar een bestand in de thuismap van de gebruiker op `~/.ssh/authorized_keys`. Dit bestand bevat een lijst met openbare sleutels, één per regel, die zijn geautoriseerd om in te loggen op dit account.

Wanneer een client SSH-sleutelauthenticatie wil gebruiken, zal deze de server op de hoogte stellen van zijn intentie en de server vertellen welke public key moet worden gebruikt. De server controleert vervolgens het bestand `authorized_keys` op de public key, genereert een willekeurige reeks en versleutelt deze met behulp van de public key. Dit versleutelde bericht kan alleen worden ontsleuteld met de bijbehorende private key. De server stuurt dit versleutelde bericht naar de klant om te testen of deze daadwerkelijk over de bijbehorende pirvate key beschikt.

#### Resources

* [SSH essentials](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#client-side-configuration-options)
