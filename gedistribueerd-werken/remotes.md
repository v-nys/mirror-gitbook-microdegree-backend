# Remotes

## Basisidee

Git wordt niet alleen gebruikt voor lokaal versiebeheer. Het wordt ook **gedistribueerd** gebruikt, dat wil zeggen over meerdere machines heen. De machines waarmee jij samenwerkt hebben ook een repository voor hetzelfde project. Als onze eigen repository geconfigureerd is om te communiceren met deze andere repositories, noemen we de andere repositories **remotes**.

Waarom willen we nu communiceren met deze remotes? De remotes zijn repositories voor hetzelfde project. Dat wil zeggen dat ze normaal een heel gelijkaardige tijdlijn bevatten. Omdat in zowel de lokale repository als op de remote wijzigingen aan de tijdlijn gedaan kunnen worden, is het nodig dat we regelmatig informatie uitwisselen met de remotes om de tijdlijnen zo goed mogelijk in overeenstemming te houden. Dat gebeurt niet automatisch, maar met commando's die we verderop zullen bespreken.

Merk op: omdat de remotes over hetzelfde project gaan en dezelfde tijdlijn hebben, kunnen ze dienen als backups. Het zijn dan geen backups van één specifieke toestand van onze code, maar wel van **heel de geschiedenis** van ons project. Dit maakt versiebeheer veel geschikter voor beheer van code dan een gedeelde Dropbox of OneDrive.

## Technische aspecten

Elke remote heeft een adres, zodat we deze kopie kunnen contacteren. Dit kan zijn om updates aan de remote in ons eigen project te integreren of om onze eigen verbeteringen te delen. We kiezen voor elke remote ook een naam, zodat we er makkelijk naar kunnen verwijzen.

Vaak maken we een remote aan op een dienst zoals Gitlab, Github,... Dit zijn hostingdiensten die het werken met remotes **vergemakkelijken**. Let wel op dat deze diensten niet essentieel zijn. Ze staan je gewoon toe een repository te maken, maar dan op een andere machine dan die waarop je normaal werkt.

### Misverstand

Een gewone kopie van een repository is geen remote van die repository. Dat komt omdat informatie over remotes wordt bijgehouden in de map `.git`.  Als je bestanden letterlijk kopieert, zal er geen nieuwe informatie aan deze map worden toegevoegd, dus het is onmogelijk dat de remotes op deze manier up-to-date worden gehouden.

## Conventie

Elke repository houdt zijn eigen remotes bij, maar in een groot project kan dat het moeilijk maken als je regelmatig alle remotes wil synchroniseren. Daarom wordt er typisch afgesproken dat één remote aangeduid wordt als centraal aanspreekpunt. Dit centraal punt wordt bijna altijd `origin` genoemd.

| commando                                    | omschrijving                                                                                                        |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `git remote`                                | geef een overzicht van alle remotes                                                                                 |
| `git remote add <naam-van-de-remote> <url>` | voeg een remote toe met een naam naar keuze, op het gegeven adres                                                   |
| `git remote remove <naam-van-de-remote>`    | vergeet dat de gegeven remote bestaat (dit wil dus niet zeggen dat de repository op de andere machine gewist wordt) |
