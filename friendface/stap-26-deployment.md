# Deployment
Nu de website over heel wat features beschikt, is het tijd om ze online te plaatsen. Omdat de website heel wat custom code omvat, met onder andere een database, zullen we dit doen op een **virtual private server** (VPS). Dit is een virtuele machine waarop je van op afstand kan inloggen en waarop je verder vrij spel hebt. Dit is iets meer werk dan een kant-en-klare hostingdienst, maar biedt het voordeel dat we volledig kunnen bepalen welke software we gebruiken.

Om op een VPS in te loggen, zullen we gebruik maken van **secure shell** (SSH). Dit is een systeem om veilige terminaltoegang te krijgen op een andere machine. Op die andere machine zullen we bijna dezelfde stack aan Docker containers opstarten die we gebruikt hebben tijdens het ontwikkelproces.

Ten slotte zullen we de applicatie enkel toegankelijk maken met het HTTPS-protocol. Dit impliceert een beveiligde *end-to-end* verbinding tussen de client en de surfer. Anders gesteld: wanneer data langs een tussenstop passeert, kan ze daar niet ontcijferd worden.
