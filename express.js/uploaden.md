# Files uploaden
Om files te uploaden kan je gebruik maken van de [express-fileupload](https://www.npmjs.com/package/express-fileupload) middleware.

{% hint style="info" %}
Voor dit package is geen ingebouwde TypeScript-ondersteuning, dus je moet de types apart installeren als development dependency.
{% endhint %}

Net zoals andere Express.js middleware moet deze middleware eerst geactiveerd worden via `app.use`. Hierbij geef je opties mee rond hoe het uploaden van files werkt, bijvoorbeeld:

```typescript
import fileUpload from 'express-fileupload';
// ...
// maximale filegrootte: 50MB
app.use(fileUpload({
  limits: { fileSize: 50 * 1024 * 1024 },
}));
```

Wanneer deze middleware actief is, wordt er een property `files` geassocieerd met requests. In het geval van een `POST`-request kan je dan de naam van een input van type `file` upvragen via het request, bijvoorbeeld:

- op de HTML-kant:
  - ergens een `<form method='POST' encType="multipart/form-data">...</form>` (`POST` omdat je iets aanmaakt op de server en het `encType` is nodig omdat je niet-tekstuele gegegevens verstuurt)
    - ergens daarin `<input type="file" id="myfile" name="myfile" />...`
- in Express.js: `const file = req.files?.myfile`
  - het vraagteken staat er omdat niet gegarandeerd is dat het `files`-veld bevolkt is
  - het type van `file` is dan:
    - `UploadedFile` (als het om één file gaat)
    - `UploadedFile[]` (als het om meerdere files gaat)
    - `undefined` (als dat specifieke veld niet was ingevuld - dit gaat dan specifiek over `myfile` en niet over `req.files` in het algemeen)
  - een `UploadedFile` beschikt over een methode `mv`. Als je deze oproept, kan je aangeven waar in het bestandensysteem de file moet terechtkomen.
