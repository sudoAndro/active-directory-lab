# GPO: Systemsteuerung sperren

## Ziel

Verhindert dass Benutzer die Systemsteuerung und PC-Einstellungen öffnen können.
Typisch in Firmen um unkontrollierte Systemänderungen zu verhindern.

---

## GPO erstellen

> Tools → Gruppenrichtlinienverwaltung

1. Rechtsklick auf **"Gruppenrichtlinienobjekte"** → **"Neu"**
2. Name: `Systemsteuerung sperren` → OK

---

## GPO konfigurieren

Rechtsklick auf GPO → **"Bearbeiten"**

```
Benutzerkonfiguration
└── Richtlinien
    └── Administrative Vorlagen
        └── Systemsteuerung
            └── "Zugriff auf Systemsteuerung und PC-Einstellungen verhindern"
                → Aktiviert
```

Editor schliessen.

---

## GPO verknüpfen

Rechtsklick auf **"andro.lab"** → **"Vorhandenes GPO verknüpfen"** → `Systemsteuerung sperren`

---

## Testen

Im Client als Domain-Benutzer:
```cmd
gpupdate /force
```

Systemsteuerung öffnen → Zugriff verweigert ✅

```cmd
gpresult /r
```

"Systemsteuerung sperren" sollte unter angewendeten GPOs erscheinen.
