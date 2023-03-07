# Stap 10: login zonder wachtwoord
In deze stap zullen we gebruikers laten aanmelden als een bepaalde gebruiker. We zullen nog geen volledige login voorzien: de gebruiker geeft alleen een gebruikersnaam en, als deze gebruikersnaam bestaat in de database, zullen we er op vertrouwen dat de gebruiker mag inloggen.

We zullen hiervoor een route `/login` voorzien waarop de bezoeker een gebruikersnaam kan ingeven. De server zal dan controleren of deze gebruikersnaam bestaat. Als dit zo is, krijgt de bezoeker een "token" dat aantoont dat hij zich heeft aangemeld - zie dit als een virtueel polsbandje.

Op alle reeds bestaande pagina's zullen we ook controleren of de gebruiker wel over dit token beschikt. Indien dit niet zo is, geven we een serverfout 500 terug.
