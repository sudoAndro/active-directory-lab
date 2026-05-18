# 🏢 Active Directory Lab

> Vollständiges Active Directory Lab auf Windows Server 2022 – Domain Controller, GPOs, DNS Filtering & Logging.
> Aufgebaut in VMware Workstation Pro als Lernumgebung für die ICT Professional SIZ Ausbildung.

---

## 🎯 Ziel

Praxisnahes Erlernen von Active Directory Grundlagen:
- Domain Controller aufsetzen
- Benutzer und Gruppen verwalten
- Gruppenrichtlinien (GPOs) erstellen und anwenden
- DNS für Webseitensperrung nutzen
- DNS Logging für Monitoring aktivieren

---

## 🖥️ Lab Umgebung

| Komponente | Details |
|---|---|
| **Hypervisor** | VMware Workstation Pro 26H1 |
| **Server OS** | Windows Server 2022 Standard Evaluation |
| **Client OS** | Windows 11 Pro |
| **Domain** | andro.lab |
| **Domain Controller** | ANDRO0 |
| **Client** | ANDRO-CLIENT1 |
| **Netzwerk** | VMware NAT (192.168.204.0/24) |

---

## 🏗️ Architektur

```
andro.lab
│
├── ANDRO0 (Domain Controller)
│   ├── AD DS
│   ├── DNS Server
│   ├── IP: 192.168.204.10
│   └── GPOs
│       ├── Systemsteuerung sperren
│       ├── Passwort Richtlinie
│       └── Desktop Hintergrund
│
└── ANDRO-CLIENT1 (Windows 11)
    ├── Domain Member
    ├── IP: DHCP (192.168.204.x)
    └── DNS: 192.168.204.10
```

---

## 📸 Screenshots

### GPOs angewendet (gpresult /r)
![gpresult](screenshots/Screenshot_2026-05-18_212847.png)

### DNS Sperrung — facebook.com & youtube.com
![dns-sperren](screenshots/Screenshot_2026-05-18_213434.png)

### DNS Log
![dns-log](screenshots/Screenshot_2026-05-18_213904.png)

### Passwort Richtlinie GPO
![passwort-gpo](screenshots/Screenshot_2026-05-18_205542.png)

---

## 📂 Struktur

```
active-directory-lab/
├── README.md
├── setup/
│   ├── dc-setup.md         ← Domain Controller einrichten
│   ├── client.md           ← Client in Domain joinen
│   └── dns-sperren.md      ← Webseiten per DNS sperren
├── gpo/
│   ├── systemsteuerung.md  ← Systemsteuerung sperren
│   ├── passwort.md         ← Passwort Richtlinie
│   └── hintergrund.md      ← Desktop Hintergrund erzwingen
├── dns/
│   └── dns-logging.md      ← DNS Logging aktivieren
└── screenshots/            ← Beweise 😄
```

---

## ✅ Was wurde umgesetzt

- [x] Windows Server 2022 installiert
- [x] Active Directory Domain Services (AD DS) installiert
- [x] Domain `andro.lab` erstellt
- [x] Windows 11 Client in Domain gejoint
- [x] Benutzer und Gruppen erstellt
- [x] GPO: Systemsteuerung gesperrt
- [x] GPO: Passwort Richtlinie gesetzt
- [x] GPO: Desktop Hintergrund erzwungen
- [x] DNS: Webseiten gesperrt (facebook.com)
- [x] DNS Logging aktiviert

---

## 📖 Lessons Learned

- Domain Controller braucht eine **statische IP** im selben Subnetz wie die Clients
- Client muss den **DC als DNS-Server** nutzen damit Domain Join funktioniert
- GPOs gelten für **Domain-Benutzer**, nicht für lokale Administratoren
- `gpupdate /force` erzwingt sofortige GPO-Anwendung zum Testen
- `gpresult /r` zeigt welche GPOs auf einem Benutzer angewendet werden
- DNS Webseitensperrung funktioniert durch leere Forward-Lookupzone — genau wie Pi-hole!
- DNS Logging zeigt welcher Client welche Domain aufgerufen hat

---

## 🔜 Nächste Schritte

- [ ] Organisationseinheiten (OUs) erstellen
- [ ] GPOs auf OUs anwenden statt auf ganze Domain
- [ ] DHCP Server einrichten
- [ ] Windows Server Backup konfigurieren
- [ ] Azure AD Connect — Hybrid Identity
- [ ] Wazuh SIEM für AD Event Monitoring

---

*Teil von [andro-lab](https://github.com/sudoAndro/andro-lab) — Homelab & IT-Tools von Andrija Tadic*
