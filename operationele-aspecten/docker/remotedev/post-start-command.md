# `postCreateCommand` en `postStartCommand`
We kunnen niet alle taken die we zouden willen uitvoeren wanneer een container start afhandelen met een Dockerfile. Een Dockerfile dient namelijk om een *image* samen te stellen. Het kan lastig zijn na elke kleine aanpassing van de werkomgeving een nieuwe image te bouwen.

Dit kan opgevangen worden via de opties `postCreateCommand` en `postStartCommand` in `devcontainer.json`. Hier kan je commando's noteren die moeten uitvoeren **wanneer een dev container aangemaakt wordt** en **nadat een container gestart is** in Visual Studio Code. Bijvoorbeeld: applicatiepackages installeren zonder een nieuwe build te doen, een database vullen met geschikte gegevens, een applicatie automatisch starten, enzovoort.

Dit kan er als volgt uitzien in `devcontainer.json`:

```json
{
  "postCreateCommand": "npm install",
  "postStartCommand": "npm start"
}
```

In dit voorbeeld installeer je (op basis van `package-lock.json`) eerst de nodige dependencies van de applicatie en start je dan de applicatie op. De concrete commando's kan je hier zelf kiezen. Het voordeel van deze aanpak is dat je dus niet constant nieuwe versies van je image moet bouwen (bijvoorbeeld bij elk nieuw package dat je nodig hebt voor je applicatie).
