# Domain Controller einrichten

## Voraussetzungen

- Windows Server 2022 Standard (Desktop Experience) installiert
- VMware Tools installiert
- Statische IP gesetzt

---

## 1. Statische IP setzen

```
IP-Adresse:      192.168.204.10
Subnetzmaske:    255.255.255.0
Standardgateway: 192.168.204.2
DNS (primär):    127.0.0.1
DNS (alternativ):8.8.8.8
```

> Netzwerk-Icon → Adapteroptionen → IPv4 → Eigenschaften

---

## 2. Computername ändern

> Rechtsklick Start → System → "PC umbenennen"

```
ANDRO0
```

Neustart erforderlich.

---

## 3. AD DS Rolle installieren

> Server-Manager → Verwalten → Rollen und Features hinzufügen

- Weiter → Weiter → Weiter
- Serverrollen: **Active Directory-Domänendienste** ✅
- Features hinzufügen → Weiter → Installieren

---

## 4. Server zum Domain Controller heraufstufen

> Server-Manager → Flagge ⚠️ → "Diesen Server zu einem Domänencontroller heraufstufen"

- **Neue Gesamtstruktur hinzufügen**
- Rootdomänenname: `andro.lab`
- Weiter → DSRM Passwort setzen
- Weiter → Weiter → Weiter → Installieren

Server startet automatisch neu.

---

## 5. Anmeldung nach Neustart

Nach dem Neustart:
```
ANDRO\Administrator
```

---

## 6. Benutzer und Gruppen erstellen

> Tools → Active Directory-Benutzer und -Computer

**Benutzer:**
- Rechtsklick Users → Neu → Benutzer
- Anmeldename: `t.user`

**Gruppen:**
- Rechtsklick Users → Neu → Gruppe
- `IT-Admin` (Global, Sicherheit)
