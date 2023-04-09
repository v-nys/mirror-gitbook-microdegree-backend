# LEFT JOIN / RIGHT JOIN

## Startpunt

Volgende voorbeelden zijn gebaseerd op dit calibratiescript. Voer het uit in Workbench als je de voorbeelden wil kunnen uitvoeren:

```sql
CREATE DATABASE  IF NOT EXISTS `ApDB` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;
USE `ApDB`;
-- MySQL dump 10.13  Distrib 8.0.19, for Linux (x86_64)
--
-- Host: localhost    Database: ModernWays
-- ------------------------------------------------------
-- Server version    8.0.17

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `Boeken`
--

DROP TABLE IF EXISTS `Boeken`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `Boeken` (
  `Titel` varchar(200) NOT NULL,
  `Id` int(11) NOT NULL AUTO_INCREMENT,
  `Personen_Id` int(11) DEFAULT NULL,
  PRIMARY KEY (`Id`),
  KEY `fk_Boeken_Personen` (`Personen_Id`),
  CONSTRAINT `fk_Boeken_Personen` FOREIGN KEY (`Personen_Id`) REFERENCES `Personen` (`Id`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Boeken`
--

LOCK TABLES `Boeken` WRITE;
/*!40000 ALTER TABLE `Boeken` DISABLE KEYS */;
INSERT INTO `Boeken` VALUES ('Norwegian Wood',1,10),('Kafka on the Shore',2,10),('American Gods',3,16),('The Ocean at the End of the Lane',4,16),('Pet Sematary',5,17),('Good Omens',6,18),('The Talisman',7,17),('Beowulf',1,NULL);
/*!40000 ALTER TABLE `Boeken` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `Personen`
--

DROP TABLE IF EXISTS `Personen`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `Personen` (
  `Voornaam` varchar(25) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Familienaam` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Id` int(11) NOT NULL AUTO_INCREMENT,
  `AanspreekTitel` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Straat` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Huisnummer` varchar(5) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Stad` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Commentaar` varchar(1000) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL,
  `Biografie` text CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci,
  PRIMARY KEY (`Id`)
) ENGINE=InnoDB AUTO_INCREMENT=20 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Personen`
--

LOCK TABLES `Personen` WRITE;
/*!40000 ALTER TABLE `Personen` DISABLE KEYS */;
INSERT INTO `Personen` VALUES ('Samuel','Ijsseling',1,NULL,NULL,NULL,NULL,NULL,NULL),('Jacob','Van Sluis',2,NULL,NULL,NULL,NULL,NULL,NULL),('Emile','Benveniste',3,NULL,NULL,NULL,NULL,NULL,NULL),('Evert W.','Beth',4,NULL,NULL,NULL,NULL,NULL,NULL),('Rémy','Bernard',5,NULL,NULL,NULL,NULL,NULL,NULL),('Robert','Bly',6,NULL,NULL,NULL,NULL,NULL,NULL),('timothy','gowers',7,NULL,NULL,NULL,NULL,NULL,NULL),(NULL,'?',8,NULL,NULL,NULL,NULL,NULL,NULL),(NULL,'Ovidius',9,NULL,NULL,NULL,NULL,NULL,NULL),('Haruki','Murakami',10,NULL,NULL,NULL,NULL,NULL,NULL),('David','Mitchell',11,NULL,NULL,NULL,NULL,NULL,NULL),('Nick','Harkaway',12,NULL,NULL,NULL,NULL,NULL,NULL),('Thomas','Ligotti',13,NULL,NULL,NULL,NULL,NULL,NULL),('Neil','Gaiman',16,NULL,NULL,NULL,NULL,NULL,NULL),('Stephen','King',17,NULL,NULL,NULL,NULL,NULL,NULL),('Terry','Pratchett',18,NULL,NULL,NULL,NULL,NULL,NULL),('Peter','Straub',19,NULL,NULL,NULL,NULL,NULL,NULL);
/*!40000 ALTER TABLE `Personen` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;
```

## LEFT JOIN

Het vertrekpunt van een `LEFT JOIN` is een `INNER JOIN`. Met andere woorden: een koppeling tussen twee tabellen aan de hand van een foreign key.

De `INNER JOIN` produceert een combinatie van kolommen van tabel `A` (de "linkertabel") met kolommen van tabel `B` (de "rechtertabel") aan de hand van de voorwaarde in `ON`. Typisch wil dit zeggen: wanneer er een match is tussen foreign key en primary key.

De `LEFT JOIN` doet dit ook, maar als een rij van tabel `A` nooit de check van de `ON` doorstaat, wordt ze **toch** gebruikt. Ze wordt dan opgevuld met extra `NULL`-waarden. De `LEFT JOIN` bevat dus **altijd alle** resultaten van de `INNER JOIN`, maar bevat er **meer** wanneer sommige rijen van de linkertabel de `ON`-test niet doorstaan.

### Syntax

```sql
SELECT <kolommen uit A en/of uit B>
FROM A LEFT JOIN B 
-- hier veronderstellen we dat de vreemde sleutel in B staat
-- hij kan ook in A staan, dan is het A.B_Id = B.Id
ON A.Id = B.A_Id
```

Dit wordt vaak als volgt genoteerd:

![Venn diagram left join](<../.gitbook/assets/venndiagramleftjoin.png>)

De doorsnede geeft aan dat er overlapping is tussen primary en foreign key.

{% hint style="warning" %}
Hoewel het Venn diagram een klassieke weergave is voor verzamelingen, zie je dit hier best eerder als een geheugensteuntje.
{% endhint %}

### Voorbeeld
Als je alle personen wilt tonen ongeacht of ze een boek hebben geschreven of niet kan je een `LEFT JOIN` gebruiken. In tegenstelling tot bij `INNER JOIN` maakt het een groot verschil of je `A LEFT JOIN B` schrijft of `B LEFT JOIN A`. Met een `LEFT JOIN` worden alle rijen uit de linkse tabel geselecteerd, of er nu een match is of niet op basis van de sleutelkolommen.

Om de auteurs van alle boeken te zien, maar ook personen die geen boek geschreven hebben:

```sql
SELECT Personen.Voornaam, Personen.Familienaam, Boeken.Titel 
FROM Personen
LEFT JOIN Boeken ON Boeken.Personen_Id = Personen.Id
ORDER BY Personen.Familienaam, Personen.Voornaam, Boeken.Titel;
```

![Opvullen left join](<../.gitbook/assets/opvullenleftjoin.png>)

De aangeduide `NULL`-waarden staan er omdat `LEFT JOIN` gebruikt is. Bij `INNER JOIN` zouden deze rijen volledig ontbreken. Merk trouwens op dat `Titel` in de tabel `Boeken` niet `NULL` **kan** zijn, omdat de kolom gedefinieerd is als `NOT NULL`. Deze waarden **moeten** dus het resultaat van de bewerking zijn.

{% hint style="info" %}
De `LEFT JOIN` wordt ook wel `LEFT OUTER JOIN` genoemd. Er is geen verschil.
{% endhint %}

# RIGHT JOIN

`RIGHT JOIN` is een alternatieve syntax voor `LEFT JOIN`. Deze versie gebruikt sowieso elke rij van tabel `B`, of er nu een rij van tabel `A` aan gekoppeld kan worden of niet.

## Syntax

```sql
SELECT <kolommen uit A of uit B>
FROM A RIGHT JOIN B
-- opnieuw: schrijfwijze hangt af van waar foreign key staat
ON A.B_Id = B.Id
```

![Venn diagram right join](<../.gitbook/assets/venndiagramrightjoin.png>)

Volgende query toont alle boeken met hun auteur, maar toont ook boeken waarvan de auteur niet gekend is:

```sql
SELECT Personen.Voornaam, Personen.Familienaam, Boeken.Titel 
FROM Personen
RIGHT JOIN Boeken ON Boeken.Personen_Id = Personen.Id
ORDER BY Personen.Familienaam, Personen.Voornaam, Boeken.Titel;
```

Als de tabellen van plaats gewisseld worden, is de query equivalent met de eerdere `LEFT JOIN`:

```sql
SELECT Personen.Voornaam, Personen.Familienaam, Boeken.Titel 
FROM Boeken
RIGHT JOIN Personen ON Boeken.Personen_Id = Personen.Id
ORDER BY Personen.Familienaam, Personen.Voornaam, Boeken.Titel;
```

{% hint style="info" %}
Hier stelt zich de vraag: "Wanneer heb ik "left" nodig en wanneer "right"?"
Hier is geen objectief antwoord. De situatie zal bepalen welke schrijfwijze het handigst leest.
{% endhint %}
