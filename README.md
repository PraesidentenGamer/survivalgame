# Survival Game

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

Das Projekt befindet sich in einer frühen, aber inzwischen breit geplanten Entwicklungsphase. Die vorhandene Unity-/C#-Basis wurde vollständig geprüft; aktuell sind **42 C#-Skripte** im Projektbestand erfasst.

## Aktueller Stand

Den ausführlichen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)

## Ideen und Vorschläge

Spätere Ideen und optionale Erweiterungen werden getrennt gesammelt:

- [IDEEN.md](IDEEN.md)

## Aktueller Schwerpunkt

Die Planungsblöcke für viele Pflichtsysteme sind inzwischen weit fortgeschritten. Zusätzlich wurde der aktuelle technische Bestand Script für Script geprüft.

Wichtige Festlegungen:
- bestehende C#-Skriptnamen bleiben unverändert
- vorhandene Inspector-/Prefab-/Map-Abhängigkeiten werden kompatibel weitergeführt
- C# bleibt die Logikschicht
- .db-Dateien enthalten strukturierte Spielinhalte und Balance
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
