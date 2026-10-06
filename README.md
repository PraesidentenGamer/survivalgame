# Survival Game

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

Das Projekt befindet sich in einer frühen, aber inzwischen breit geplanten Entwicklungsphase. Die vorhandene Unity-/C#-Basis wurde vollständig geprüft; aktuell sind **42 C#-Skripte** im Projektbestand erfasst.

## Aktueller Stand

Den ausführlichen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)
- [FORTSCHRITT.md](FORTSCHRITT.md) – kompakte Arbeitsübersicht mit Datenbankstatus

## Ideen und Vorschläge

Spätere Ideen und optionale Erweiterungen werden getrennt gesammelt:

- [IDEEN.md](IDEEN.md)

## Aktueller Schwerpunkt

Der aktuelle Schwerpunkt liegt auf der **datengetriebenen Weltkarte und den Gebietssystemen** sowie auf dem ersten dynamischen Eventkarten-Test.

Aktuelle Datenrichtung:

```text
areas.json.db
↓
AreaData.cs
↓
WorldMapUI / Spawn-Systeme / weitere Verbraucher
```

Die frühere fest codierte Gebietskonfiguration in C# soll damit nicht mehr die maßgebliche Datenquelle sein. Parallel werden offene Datenbankwerte und Regeln weiter vervollständigt.

Neu konkretisiert:
- 25 Hauptmissionen als aktueller Story-Grundbogen
- 12 SECRET-Missionen
- Sarah-Karma-/Vertrauenssystem
- universelles Begleiter-Skillsystem
- 75-%-Regel für aktive Begleiter / 100-%-Autonomie in der Siedlung
- 3-stufige **Passive Hilfe**
- getrenntes Hund-/Tierbegleitersystem
- datengetriebene NPC-Autonomie mit Lagerberechtigungen und spielergesteuertem Fallback

Wichtige Festlegungen:
- bestehende C#-Skriptnamen bleiben unverändert
- vorhandene Inspector-/Prefab-/Map-Abhängigkeiten werden kompatibel weitergeführt
- C# bleibt die Logikschicht
- strukturierte Spieldaten liegen aktuell als `.json.db` im Ordner `database`
- JSON wird für normale Einstellungen verwendet
- Spielstände verwenden später die eigene Endung `.sgsave`

## Save-Richtung

Geplant ist ein robustes Save-System mit:
- 10 manuellen Slots
- Autosave
- Recovery
- Save-Versionierung
- `.sgsave`
- AES-256-GCM
- internem Support-/Repair-Tool

## UI

Die visuelle Richtung ist inzwischen für folgende Bereiche festgelegt:
- HUD
- Inventar/Container
- Questbuch
- Weltkarte
- Hauptmenü/Einstellungen

Auf starken Geräten darf die Oberfläche stark transparent/gläsern wirken. Auf schwächeren Geräten wird die Transparenz automatisch reduziert.

## Story

Die Hauptstory soll sehr groß werden und eng mit dem Levelsystem verbunden sein. Tschernobyl ist ein sehr später Hauptstoryabschnitt, aber nicht das endgültige Ende des Spiels.

## Technische Basis

Bereits vorhanden bzw. als Prototyp bestätigt sind unter anderem:
- Spielerbewegung
- Kamera
- Spielerleben
- Kampf
- Interaktion
- Inventar/Stacks
- Koordinaten
- Save-Prototyp
- Weltkarten-Ausgänge und Reisen
- funktionsfähige Weltkarte mit `WorldMapUI.cs`
- Hover-/InfoPanel-Anzeige und Betreten von Gebieten
- 30 Maps + Weltkarte in den Build Settings
- AreaData
- AreaSpawnManager
- AreaSpawnZone
- Ressourcen-Spawning
- Lootkisten/Container
- Türsystem
- Testzombie
- GameManager

## Hinweis

Für die erste Veröffentlichung ist zunächst nur **Normal / Ausgeglichen** aktiv.

Singleplayer hat Priorität. Multiplayer bleibt eine spätere Erweiterung, wird aber architektonisch mitgedacht.

## Nächster Entwicklungsblock

Aktuelle Reihenfolge:
1. Convex-Hull-Positionierung des dynamischen Eventmarkers über mehrere Play-Neustarts prüfen
2. Eventmarker an Hover, Klick und bestehendes InfoPanel anbinden
3. BETRETEN für Eventkarten über den bestehenden Reiseablauf integrieren
4. echte Event-DB-/Dateianbindung umsetzen
5. Lootkisten vollständig an AreaData, Loot-DB und Item-DB anbinden
6. offene Datenbankwerte, Referenzen und Balance parallel weiter vervollständigen

Aktuell geschätzter Gesamtfortschritt der ersten vollständig spielbaren Fassung: **ca. 35 %**.

Details: [FORTSCHRITT.md](FORTSCHRITT.md)
