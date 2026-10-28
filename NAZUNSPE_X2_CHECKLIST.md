# Nazúŋspe-X2 – Inbetriebnahme-Checkliste

**Projekt:** Tenlog TL-D3 Pro Custom IDEX Rebuild  
**Ziel:** Zuverlässiger Klipper-IDEX-Drucker für zwei Materialien. Copy/Mirror erst nach erfolgreichem Zweimaterialbetrieb.  
**Hardware:** BTT Manta M8P V2.0, TMC2240, zwei CAN-Toolheads, BERD-Air.  
**Aktueller Ansatz:** Optische Z-Endstops, manuelles Bettleveling; MicroProbe noch nicht aktiv.

> **Status:** Die Kästchen sind absichtlich nicht vorab abgehakt. `- [x]` erst setzen, wenn die jeweilige Funktion überprüft wurde. Bei unsicherer Endstop-Erkennung kein Z-Homing ausführen.

## 1. Klipper-Grundkonfiguration
- [x ] MCUs und CAN-Bus-Verbindungen prüfen
- [x] Pinbelegung und Motorzuordnung kontrollieren
- [x ] Heizungen, Thermistoren und Temperaturgrenzen prüfen
- [x ] Lüfter, BERD-Air und sonstige Ausgänge prüfen
- [x ] Not-Aus und Schutzfunktionen testen

## 2. Achsen und Bewegungsrichtung
- [x ] X0, X1, Y und beide Z-Motoren einzeln prüfen
- [x ] Bewegungsrichtungen und `rotation_distance` kontrollieren
- [x ] Microsteps, Motorströme und Treiber prüfen
- [x ] Mechanische Bewegungsgrenzen feststellen
- [x ] Geschwindigkeit und Beschleunigung zunächst konservativ einstellen

## 3. Endstops und Homing
- [x ] Alle Endstops mit `QUERY_ENDSTOPS` prüfen
- [x ] **Optische Z-Endstops auf zuverlässige Signalerkennung testen**
- [x ] X0-, X1- und Y-Homing einzeln prüfen
- [x ] Dual-Z-Homing und Endstop-Phase bei zuverlässiger Erkennung kalibrieren
- [x ] Wiederholgenauigkeit über mehrere Homing-Vorgänge kontrollieren

## 4. IDEX-Grundkonfiguration
- [ ] `[dual_carriage]` und `safe_distance` kontrollieren
- [ ] T0 und T1 korrekt zuordnen
- [ ] Parkpositionen beider Schlitten festlegen
- [ ] Werkzeugwechsel T0/T1 ohne Extrusion testen
- [ ] Kollisionsfreie Bewegungsabläufe überprüfen

## 5. Druckbett und Z-Referenz
- [ ] Druckbett auf Betriebstemperatur bringen
- [ ] Bett mechanisch ausrichten
- [ ] Z-Nullpunkt für T0 festlegen
- [ ] Düsenhöhenversatz T0/T1 ermitteln
- [ ] Erste Schicht beider Toolheads separat überprüfen

## 6. Extruder und Hotends
- [ ] Extrudermotoren und Förderrichtung prüfen
- [ ] `rotation_distance` beider Extruder kalibrieren
- [ ] PID-Regelung beider Hotends kalibrieren
- [ ] Materialförderung und Düsendurchmesser prüfen
- [ ] Extrusions- und Retraktionsverhalten testen

## 7. Bauteilkühlung
- [ ] BERD-Air-Steuerung und Pumpenleistung prüfen
- [ ] Luftverteilung beider Düsen prüfen
- [ ] PLA- und PETG-Kühlprofile anlegen
- [ ] Überkühlung und Warping beobachten
- [ ] Kühlung für Überhänge und Brücken optimieren

## 8. Bewegungs- und Extrusionskalibrierung
- [ ] Testwürfel auf Maßhaltigkeit prüfen
- [ ] Schwingungen und mechanisches Spiel untersuchen
- [ ] Input Shaper messen oder mit Testdrucken einstellen
- [ ] Pressure Advance je Extruder und Material kalibrieren
- [ ] Geschwindigkeit und Beschleunigung schrittweise optimieren

## 9. Slicer einrichten
- [ ] IDEX-Druckerprofil mit zwei Extrudern erstellen
- [ ] Werkzeugzuordnung und Düsenabstände einstellen
- [ ] Start-, End- und Werkzeugwechsel-G-Code festlegen
- [ ] Materialprofile für beide Extruder erstellen
- [ ] Purge-Line, Skirt und ggf. Prime-Tower konfigurieren

## 10. Start-, End- und Wechselmakros
- [ ] `START_PRINT` für beide Extruder einrichten
- [ ] T0/T1-Makros einschließlich Parken und Aktivierung testen
- [ ] Standby-Temperaturen und Retract/Prime konfigurieren
- [ ] Purge-Line für beide Werkzeuge integrieren
- [ ] `END_PRINT` mit Parkpositionen und Abschaltung prüfen

## 11. Einzelmaterial-Testdrucke
- [ ] First-Layer-Test mit T0 drucken
- [ ] First-Layer-Test mit T1 drucken
- [ ] Kalibrierwürfel mit beiden Extrudern separat drucken
- [ ] Haftung, Warping und Oberflächenqualität prüfen
- [ ] Funktionierende Einstellungen dokumentieren

## 12. Zweimaterial-IDEX-Druck
- [ ] Beide Materialien vorbereiten
- [ ] XY-Düsenversatz mit Kalibriermuster einstellen
- [ ] Mehrfache T0/T1-Wechsel testen
- [ ] Oozing und Materialverschleppung reduzieren
- [ ] Komplettes Zweimaterial-Testobjekt drucken

## 13. Zuverlässigkeit und Fehlerfälle
- [ ] Pause und Resume testen
- [ ] Filamentwechsel und Abbruchverhalten prüfen
- [ ] Idle-Timeout und Motorabschaltung testen
- [ ] Fehlerbehandlung und ggf. Wiederaufnahme prüfen
- [ ] Längeren Testdruck mit Werkzeugwechseln durchführen

## 14. Erweiterte IDEX-Modi – später
- [ ] Copy-Modus einrichten und testen
- [ ] Mirror-Modus einrichten und testen
- [ ] Sicherheitsabstände und Druckbereich je Modus prüfen
- [ ] Slicer-Profile für beide Modi erstellen

## 15. Abschluss und Dokumentation
- [ ] Funktionierende Konfiguration sichern
- [ ] GitHub-Backup und Versionsstand prüfen
- [ ] Makros und Slicer-Profile dokumentieren
- [ ] Referenzdrucke und Kalibrierwerte festhalten
- [ ] Stabilen Betriebsstand als Release kennzeichnen

---

## Aktuelle offene Punkte (Stand: 27.10.2026)

- **Z-Endstop:** LED reagierte auf Unterbrechung, Klipper meldete zeitweise weiterhin `open`. Vor erneutem Homing zuverlässig beheben.
- **Erste Schicht / PETG:** Manuelles Bettleveling und Haftung prüfen; langes Bauteil hat sich gelöst und verzogen.
- **IDEX-Makros:** Werkzeugwechsel, Parken nach Druckende und Purge-Line im realen Ablauf prüfen.
- **Priorität:** Normaler Zweimaterialbetrieb vor Copy/Mirror.

## Fortschrittsnotizen

| Datum | Phase / Test | Ergebnis | Nächster Schritt |
|---|---|---|---|
| 2026-10-27 | Z-Endstop | Zeitweise nicht von Klipper erkannt | Signalweg prüfen |
| 2026-10-27 | PETG-Testdruck | Haftung/Warping auffällig | Bett manuell leveln |
