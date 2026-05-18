# GPO: Passwort Richtlinie

## Ziel

Erzwingt sichere Passwörter für alle Domain-Benutzer.
Standard in jeder Unternehmensumgebung.

---

## GPO erstellen & konfigurieren

> Gruppenrichtlinienverwaltung → Neu → `Passwort Richtlinie` → Bearbeiten

```
Computerkonfiguration
└── Richtlinien
    └── Windows-Einstellungen
        └── Sicherheitseinstellungen
            └── Kontorichtlinien
                └── Kennwortrichtlinien
```

---

## Einstellungen

| Richtlinie | Wert |
|---|---|
| Kennwortlänge (Minimum) | 10 Zeichen |
| Komplexitätsvoraussetzungen | Aktiviert |
| Maximales Kennwortalter | 90 Tage |
| Minimales Kennwortalter | 1 Tag |
| Kennwortchronik erzwingen | 5 (letzte 5 nicht wiederverwendbar) |

---

## GPO verknüpfen

Rechtsklick auf **"andro.lab"** → **"Vorhandenes GPO verknüpfen"** → `Passwort Richtlinie`

---

## Komplexitätsanforderungen

Mit aktivierter Komplexität muss ein Passwort enthalten:
- Grossbuchstaben (A-Z)
- Kleinbuchstaben (a-z)
- Zahlen (0-9)
- Sonderzeichen (!@#$%...)
