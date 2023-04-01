# Clubs toevoegen
In deze stap zullen we "clubs" toevoegen aan FriendFace. Het zijn organisaties waarvan gebruikers lid kunnen worden, typisch gekoppeld aan een bepaald onderwerp, zoals een hobby, regio of iets anders dat de gebruikers nauw aan het hart ligt.

Net zoals er een verband is tussen gebruikers en sneezes ("gebruiker A heeft sneeze B gepost") is er een verband tussen gebruikers en clubs. Anders dan bij sneezes zijn de **multipliciteiten** van dit verband. Bij sneezes was het zo:

- één gebruiker kan meerdere sneezes posten
- één sneeze behoort altijd toe aan één gebruiker

Bij clubs is het zo:

- één gebruiker kan aansluiten bij meerdere clubs
- één club kan meerdere leden tellen

Dit valt niet voor te stellen met de concepten die tot hiertoe in het project aan bod gekomen zijn. Er is wel een standaardmanier om dit soort verbanden voor te stellen: een tussenliggende tabel met meerdere foreign keys. Ook weergeven wie aangesloten is bij welke club is niet vanzelfsprekend. Ook hiervoor bestaat een standaardtechniek: meerdere `JOIN`-operaties na elkaar.
