# Survival Game

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

Das Projekt befindet sich weiterhin in einer frühen Entwicklungs- und Planungsphase. Der Schwerpunkt liegt jetzt darauf, die **zwingenden Kernsysteme für die erste vollständig spielbare Version** vollständig zu definieren und anschließend technisch umzusetzen.

## Aktueller Stand

Den vollständigen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)

## Ideen und Vorschläge

Spätere Ideen und optionale Erweiterungen werden getrennt gesammelt:

- [IDEEN.md](IDEEN.md)

Neue Vorschläge werden bewusst geparkt, damit laufende Entwicklungsblöcke abgeschlossen werden können und der Umfang nicht unkontrolliert wächst.

## Aktueller Schwerpunkt

Aktuell vorbereitet bzw. deutlich erweitert wurden unter anderem:

- Item- und Materialbereinigung bis aktuell 340 normale Item-Einträge
- Produktions- und Werkbanklogik
- Weltkarte und Version-1-Gebiete
- Loot- und Seltenheitssystem
- XP- und Levelsystem bis Level 100
- KI-Grundsystem
- Kampf, Rüstung und Resistenz
- Survival-/Statussysteme
- Tod/Leichen/Respawn
- Händlerlogik
- Eventgebiets-Persistenz
- Speichern/Autosave/Recovery
- Grafik-/Textur-/Audio-Pflichtumfang
- spätere Update- und Multiplayer-Architektur

## Grundprinzip der ersten vollständig spielbaren Version

Die erste Version muss nicht alle langfristig geplanten Systeme enthalten.

Wichtig ist ein stabiler Gameplay-Loop:

**Vorbereiten -> Reisen -> Sammeln/Kämpfen -> Beute sichern -> Verarbeiten/Bauen -> Fortschritt**

Spätere Systeme dürfen bereits vorbereitet sein und über Updates aktiviert oder erweitert werden.

## Datenarchitektur

**C# = Logik und Systeme**  
**.db = Inhalte, Werte, Balance und Freischaltungen**

Dadurch sollen spätere Updates neue Items, Rezepte, Gebiete, Händlerangebote, Events und Balancewerte möglichst ohne große Änderungen an den Kernsystemen ergänzen können.

## Hinweis

Für die erste Veröffentlichung ist zunächst nur der Schwierigkeitsmodus **Normal / Ausgeglichen** vorgesehen.

Singleplayer hat Priorität. Multiplayer ist als spätere Erweiterung vorgesehen, wird aber architektonisch bereits mitgedacht.
