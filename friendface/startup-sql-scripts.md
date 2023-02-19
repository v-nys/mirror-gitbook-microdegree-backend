# SQL-scripts uitvoeren tijdens het opstarten
We hebben SQL-scripts geschreven om een tabel met gebruikers aan te maken en om deze op te vullen met testdata. Helaas moeten deze scripts manueel opnieuw uitvoeren wanneer we een nieuwe development container opstarten. Dat kan regelmatig zijn.

Er is een betere oplossing. Net zoals we eerder gezorgd hebben dat de nodige packages geïnstalleerd worden bij opstart van een container, kunnen we er voor zorgen dat de SQL-scripts die we reeds geschreven hebben automatisch uitvoeren wanneer de container wordt opgestart.
