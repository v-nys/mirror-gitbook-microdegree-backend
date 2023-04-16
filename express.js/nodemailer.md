# `nodemailer`
E-mails verzenden gebeurt via het SMTP-protocol. Node-applicaties (inclusief Express.js) hoeven dit protocol niet volledig zelf te implementeren om e-mails te verzenden. Ze kunnen beroep doen op [nodemailer](https://www.npmjs.com/package/nodemailer). 

Dit package gebruiken kan via `import nodemailer from 'nodemailer'`.

Om met behulp van `nodemailer` mails te versturen, is een "transporter" nodig. Dit is een object dat geïnitaliseerd is met de nodige connectiegegevens, bijvoorbeeld:

```javascript
let transporter = nodemailer.createTransport({
  host: "smtp.ethereal.email", // het adres van de mailserver
  port: 587, // de poort waarop deze SMTP verwacht
  secure: false, // als de verbinding niet beveiligd hoeft te zijn
  // logingegevens
  auth: {
    user,
    pass
  },
});
```

Eens je een transporter hebt, kan je een e-mail versturen als volgt:

```javascript
transporter.sendMail({
  from: '"Fred Foo" <foo@example.com>',   // afzender
  to: "bar@example.com, baz@example.com", // lijst met ontvangers
  subject: "Hello",
  text: "Hello world?",
});
```

{% hint style="warning" %}
Verschillende SMTP-servers vereisen verschillende settings. Raadpleeg de documentatie van de SMTP-server die je wil gebruiken om te weten wat je moet invullen. Raadpleeg de documentatie van `nodemailer` om te weten hoe je een bepaalde optie specifieert. Ze zijn hier niet allemaal gegeven!
{% endhint %}
