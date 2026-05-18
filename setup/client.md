# Client in Domain joinen

## Voraussetzungen

- Windows 11 installiert
- Gleicher VMware Netzwerkadapter wie Server (NAT)
- Domain Controller läuft

---

## 1. DNS auf Domain Controller zeigen

> Netzwerk-Icon → Adapteroptionen → IPv4 → Eigenschaften

```
Bevorzugter DNS:   192.168.204.10   ← IP des Domain Controllers!
Alternativer DNS:  8.8.8.8
```

> ⚠️ Ohne diesen Schritt funktioniert der Domain Join nicht!

---

## 2. Verbindung testen

```cmd
ping 192.168.204.10
```

Wenn keine Antwort → IP des Servers und Netzwerk prüfen.

---

## 3. Domain joinen

> Rechtsklick Start → System → "Domäne oder Arbeitsgruppe" → Ändern

- **Domäne** auswählen
- Eingeben: `andro.lab`
- Anmeldedaten: `Administrator` + Passwort

Bei Erfolg: "Willkommen in der Domäne andro.lab" 🎉

Neustart erforderlich.

---

## 4. Als Domain-Benutzer anmelden

Nach Neustart → Anderer Benutzer:
```
andro.lab\t.user
```

---

## 5. GPOs testen

```cmd
gpupdate /force
gpresult /r
```

Unter "Angewendete Gruppenrichtlinienobjekte" sollten die GPOs erscheinen.

> ⚠️ Als normaler Domain-Benutzer anmelden, nicht als Administrator!
> Administrators sind oft von GPOs ausgenommen.
