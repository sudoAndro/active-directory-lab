# DNS Logging aktivieren

## Ziel

Protokolliert alle DNS-Anfragen — welcher Client welche Domain aufgerufen hat.
Wichtig für Sicherheitsmonitoring und Troubleshooting.

---

## DNS Logging aktivieren

> Tools → DNS → Rechtsklick auf Servername → "Eigenschaften" → Tab "Debugprotokollierung"

Folgendes aktivieren:
- ✅ Pakete für Debuggingzwecke protokollieren
- ✅ Abgehende Pakete
- ✅ Eingehende Pakete
- ✅ Anfragen/Übertragungen
- ✅ Antworten

Logdatei Pfad:
```
C:\dns_log.txt
```

---

## Log auslesen

```powershell
Get-Content C:\dns_log.txt | Select-String "facebook"
```

Oder einfach in Editor öffnen — jede Zeile zeigt:
- Zeitstempel
- Client IP
- Angefragte Domain
- Antwort

---

## Beispiel Log-Eintrag

```
17.05.2026 21:30:15 0DD0 PACKET  00000001A1234567 UDP Rcv 192.168.204.137 
QueryResponse NOERROR facebook.com. A
```

Bedeutet: Client `192.168.204.137` hat `facebook.com` angefragt.

---

## Praxisnutzen

- 🔍 Welche Webseiten werden aufgerufen
- 🔍 Verdächtige Domains erkennen (Malware, C2-Server)
- 🔍 Gesperrte Domains trotzdem versucht aufzurufen
- 🔍 Troubleshooting bei Verbindungsproblemen

> In Kombination mit einem SIEM (z.B. Wazuh) können diese Logs
> automatisch analysiert und Alarme ausgelöst werden.
