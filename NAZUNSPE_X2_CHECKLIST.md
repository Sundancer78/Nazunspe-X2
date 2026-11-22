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
- [X ] `[dual_carriage]` und `safe_distance` kontrollieren
- [X ] T0 und T1 korrekt zuordnen
- [X ] Parkpositionen beider Schlitten festlegen
- [X ] Werkzeugwechsel T0/T1 ohne Extrusion testen
- [X ] Kollisionsfreie Bewegungsabläufe überprüfen

## 5. Druckbett und Z-Referenz
- [X ] Druckbett auf Betriebstemperatur bringen
- [X ] Bett mechanisch ausrichten
- [X ] Z-Nullpunkt für T0 festlegen
- [X ] Düsenhöhenversatz T0/T1 ermitteln
- [X ] Erste Schicht beider Toolheads separat überprüfen

## 6. Extruder und Hotends
- [X ] Extrudermotoren und Förderrichtung prüfen
- [x ] `rotation_distance` beider Extruder kalibrieren
- [x ] PID-Regelung beider Hotends kalibrieren
- [x ] Materialförderung und Düsendurchmesser prüfen
- [x ] Extrusions- und Retraktionsverhalten testen

## 7. Bauteilkühlung
- [x ] BERD-Air-Steuerung und Pumpenleistung prüfen
- [x ] Luftverteilung beider Düsen prüfen
- [x ] PLA- und PETG-Kühlprofile anlegen
- [x ] Überkühlung und Warping beobachten
- [x ] Kühlung für Überhänge und Brücken optimieren

## 8. Bewegungs- und Extrusionskalibrierung
- [x ] Testwürfel auf Maßhaltigkeit prüfen
- [x ] Schwingungen und mechanisches Spiel untersuchen
- [x ] Input Shaper messen oder mit Testdrucken einstellen
- [x ] Pressure Advance je Extruder und Material kalibrieren
- [x ] Geschwindigkeit und Beschleunigung schrittweise optimieren

## 9. Slicer einrichten
- [x ] IDEX-Druckerprofil mit zwei Extrudern erstellen
- [x ] Werkzeugzuordnung und Düsenabstände einstellen
- [x ] Start-, End- und Werkzeugwechsel-G-Code festlegen
- [x ] Materialprofile für beide Extruder erstellen
- [x] Purge-Line, Skirt und ggf. Prime-Tower konfigurieren

## 10. Start-, End- und Wechselmakros
- [x ] `START_PRINT` für beide Extruder einrichten
- [x ] T0/T1-Makros einschließlich Parken und Aktivierung testen
- [x ] Standby-Temperaturen und Retract/Prime konfigurieren
- [x ] Purge-Line für beide Werkzeuge integrieren
- [x ] `END_PRINT` mit Parkpositionen und Abschaltung prüfen

## 11. Einzelmaterial-Testdrucke
- [x ] First-Layer-Test mit T0 drucken
- [x ] First-Layer-Test mit T1 drucken
- [x ] Kalibrierwürfel mit beiden Extrudern separat drucken
- [x ] Haftung, Warping und Oberflächenqualität prüfen
- [x ] Funktionierende Einstellungen dokumentieren

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
