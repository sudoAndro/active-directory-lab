# Webseiten per DNS sperren

## Funktionsprinzip

Der Domain Controller ist DNS-Server für alle Clients.
Durch eine leere DNS-Zone für eine Domain wird sie unerreichbar —
der DNS-Server antwortet zwar, gibt aber keine IP zurück.

> Genau so funktioniert Pi-hole — nur automatisiert mit einer grossen Blockliste!

---

## Webseite sperren

> Tools → DNS → Forward-Lookupzonen → Rechtsklick → "Neue Zone"

- Weiter → Weiter → Weiter
- Zonenname: `facebook.com`
- Weiter → Fertig stellen

**Fertig!** Kein A-Record nötig — die leere Zone reicht.

---

## Testen

Im Client Browser: `facebook.com` aufrufen → Seite nicht erreichbar ✅

---

## Weitere Domains sperren

Gleichen Vorgang wiederholen für:
```
instagram.com
tiktok.com
youtube.com
```

---

## Sperrung aufheben

> DNS → Forward-Lookupzonen → Rechtsklick auf Zone → "Zone löschen"
