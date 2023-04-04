# Vriendschappen toevoegen
Een sociaal netwerk vereist per definitie connecties tussen gebruikers. In FriendFace spreken we over "vriendschappen". In deze stap zullen we gebruikers toestaan mekaars profiel te bekijken en vriendschap te sluiten.

Dit houdt een veel-op-veel verband tussen gebruikers en andere gebruikers in. Dit werkt technisch hetzelfde als andere veel-op-veel verbanden, maar het is iets moeilijker te vatten. Verder is hier ook een symmetrie aanwezig: als gebruiker A bevriend is met gebruiker B, geldt ook het omgekeerde.

Om dit voor te stellen en foute voorstellingen van de data te vermijden, zullen we manieren introduceren om informatie die impliciet is in de database expliciet voor te stellen. Meerbepaald: stored functions, views en gegenereerde kolommen.

Om ons verder te wapenen tegen SQL-injectie, zullen we ook prepared statements introduceren. Dit is een robuuster alternatief voor stringinterpolatie. Die laatste aanpak is nog steeds kwetsbaar als we meerdere queries met één `excecute` uitvoeren.
