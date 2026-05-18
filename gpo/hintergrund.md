# GPO: Desktop Hintergrund erzwingen

## Ziel

Setzt ein einheitliches Hintergrundbild auf allen Clients.
In Firmen oft mit Firmenlogo oder Sicherheitshinweisen verwendet.

---

## GPO erstellen & konfigurieren

> Gruppenrichtlinienverwaltung → Neu → `Desktop Hintergrund` → Bearbeiten

```
Benutzerkonfiguration
└── Richtlinien
    └── Administrative Vorlagen
        └── Desktop
            └── Desktop
                └── "Desktophintergrund"
                    → Aktiviert
```

---

## Einstellungen

| Feld | Wert |
|---|---|
| Name des Hintergrundbilds | `C:\Windows\Web\Wallpaper\Windows\img19.jpg` |
| Hintergrundbildstil | Füllen |

> ⚠️ Der Pfad muss auf dem **Client** existieren, nicht auf dem Server!
> Lokale Windows-Wallpapers unter `C:\Windows\Web\Wallpaper\` sind auf jedem Windows vorhanden.

---

## GPO verknüpfen

Rechtsklick auf **"andro.lab"** → **"Vorhandenes GPO verknüpfen"** → `Desktop Hintergrund`

---

## Testen

Im Client als Domain-Benutzer (nicht als Admin!):
```cmd
gpupdate /force
```

Dann ab- und wieder anmelden — Hintergrundbild wird geändert ✅

> ⚠️ Lokale Administratoren sind oft von Benutzer-GPOs ausgenommen.
> Immer als normaler Domain-Benutzer testen!
