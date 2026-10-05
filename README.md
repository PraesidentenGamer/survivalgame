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

Der aktuelle Schwerpunkt liegt auf der **vollständigen Datenbank- und Regeldefinition**, bevor weitere Loader/Manager gebaut werden. Gegner, Gebiete, Rezepte, Welt/Reise, Spieler-Skills und Forschung sind bereits weitgehend bzw. vollständig festgelegt. Aktuell werden Quests, Begleiter/NPC-KI sowie die noch offenen Balancewerte fertiggestellt.

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

Aktuell gilt bewusst: **Datenbanken und Regeln zuerst, Loader/Code danach.**

Reihenfolge:
1. Begleiter-/NPC-KI-Regeln abschließen
2. Quest-/Story-DB finalisieren
3. offene Werte in Items, Ressourcen, Loot, Settings, Fahrzeuge und Events schließen
4. Progression/Pakete auf Referenzen und Item-IDs prüfen
5. Shop, Händler und Economy als Datenbanken planen
6. vollständige Integritätsprüfung
7. anschließend EnemySpawnManager, Loader/Manager und weitere C#-Systeme weiterbauen

Details: [FORTSCHRITT.md](FORTSCHRITT.md)
