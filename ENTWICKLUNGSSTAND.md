# Entwicklungsstand

**Stand:** 06.10.2026

## Aktuelle Entwicklungsphase

Die grundlegende Planung der Pflichtsysteme ist weit fortgeschritten. Der aktuelle technische Schwerpunkt liegt auf der **datengetriebenen Weltkarte, den Gebietssystemen und der dynamischen EventMap**.

Die maßgebliche Datenrichtung lautet:

```text
DB = eigentliche Datenquelle
C# = Vermittler zwischen Spiel und DB
Spielsysteme = benutzen die gelieferten Daten
```

Grundregel:
- bestehende Skriptnamen bleiben unverändert
- vorhandene Prefab-/Inspector-/Map-Abhängigkeiten bleiben kompatibel
- neue Systeme werden über Loader/Manager ergänzt
- C# bleibt Logikschicht
- Inhalte und Balance wandern schrittweise in die Datenbanken

## Architektur

**C# = Logik und Systeme**  
**`.json.db` = strukturierte Spielinhalte und Balance im Ordner `database`**  
**JSON = Einstellungen/Config**  
**.sgsave = Spielstand**

## Weltkarte und Standardmaps

Die Weltkarte ist technisch funktionsfähig.

Bestätigt:
- 30 dauerhafte Maps + Weltkarte in den Build Settings
- `WorldMapUI.cs` ist aktiv im Einsatz
- Marker-Hover
- InfoPanel
- BETRETEN
- Szenenwechsel über `WorldMapTravel.cs`
- Rückkehr über `WorldMapExit.cs`
- jede Standardmap verwendet `Prefab_MapBoundsAndExits`

### WorldMapExit-Korrektur

Der bisherige Exit-Code prüfte den exakten Objektnamen `"Player"`. Der tatsächliche Spieler wird jedoch als `Prefab_Player` verwendet und trägt den Tag `Player`.

Der Exit wurde deshalb robust umgestellt:
- primäre Erkennung über Tag `Player`
- zusätzlicher Fallback über `PlayerMovement` im Parent
- keine Abhängigkeit mehr vom konkreten GameObject-Namen
- die Korrektur wirkt zentral auf alle Maps, die `Prefab_MapBoundsAndExits` verwenden

## Dynamische EventMap

Die gemeinsame Szene `EventMap` wurde erfolgreich als skalierbare technische Basis bestätigt.

Grundaufbau:
```text
EventMap
├── Main Camera
├── Directional Light
├── Prefab_Player
├── EventManager
├── EventSpawnRoot
├── BorderRoot
└── EventGround
```

### EventGround

Der Boden wird nicht mehr vollständig zur Laufzeit neu erzeugt. Ein vorhandener `EventGround` dient als sichere physische Grundfläche.

Zur Laufzeit wird dieser Boden auf die vom Event gewünschte Größe skaliert.

Spielerstart:
```text
Position   X: 0   Y: 1   Z: 0
```

### Randaufbau

Der Rand wird dynamisch nach demselben Grundprinzip wie die Standardmaps aufgebaut:

```text
Eventfläche
↓
umlaufender Rückkehrtrigger auf allen 4 Seiten
↓
physische Border / Runterfallschutz außen
```

Aktuell im Test sichtbar:
- Grün = Rückkehrtrigger
- Rot = physischer Runterfallschutz

Für die spätere Produktionsfassung werden nur die Renderer ausgeblendet; Collider und Trigger bleiben aktiv.

### Erfolgreicher Mehrgrößen-Test

Drei gleichzeitig aktive Events wurden auf der Weltkarte erzeugt und nacheinander betreten:

- Testevent 1: 10 × 10 UE
- Testevent 2: 15 × 20 UE
- Testevent 3: 20 × 12 UE

Ergebnis:
- alle drei Größen wurden korrekt aufgebaut
- dieselbe `EventMap`-Szene wurde wiederverwendet
- Boden, Trigger und Border wurden passend skaliert
- Spielerstart blieb bei `(0, 1, 0)`
- Rückkehr zur Weltkarte funktionierte
- Eventmarker wurden danach wieder korrekt registriert
- die Weltkartenposition eines Events bleibt über seine Laufzeit erhalten

Damit ist das Kernprinzip der dynamischen Eventkarte technisch nachgewiesen.

## Eventmarker

Temporäre Events verwenden weiterhin dynamische Marker:
- gelber Stern
- 40 × 40
- Rotation 15°/s
- Parent `MapData`
- Positionierung innerhalb der Convex Hull der festen Gebietsmarker
- Sicherheitsabstand zu normalen Markern
- Sicherheitsabstand zur Außenkontur
- Position wird pro Event einmal gewählt und danach beibehalten

Die bestehende `WorldMapUI.cs`-Logik wird weiterverwendet; es entsteht kein zweites paralleles Weltkarten-UI.

## Nächster technischer Umbau

Der erfolgreiche Testcode ist noch kein finales Eventsystem. Als nächster Schritt wird er datengetrieben:

```text
events.json.db
↓
Event-Loader / EventManager
↓
aktive Event-ID
↓
EventMap
↓
Größe / Dauer / Gegner / Loot / Ressourcen / Layout
```

Danach muss der Eventzustand in das Save-System integriert werden.

## Pflichtsysteme bis zur vollständig spielbaren Fassung

Für diese Arbeitsphase werden **Grafik, Audio, Shader und finales optisches Polishing ausgeklammert**.

Noch funktional zu schließen sind insbesondere:

1. Eventsystem aus DB statt Testcode
2. Gegner-Spawning und Gegnerbasis
3. Ressourcen- und Loot-Spawns vollständig datengetrieben
4. Survivalwerte vollständig verbinden
5. Inventar, Ausrüstung, Haltbarkeit und Item-Nutzung
6. Crafting, Werkbänke und Produktion
7. Basisbau, Upgrades, Abriss und Horden
8. XP, Level, Skills und Forschung zur Laufzeit
9. Quest-/Storysystem inklusive Storyflags und SECRET-Inhalten
10. produktionsreifes Save-/Load-System
11. Händler, Economy und Shop
12. Begleiter- und NPC-KI
13. Fahrzeuge und Weltreise
14. zentrale Zeit-, Offline- und Eventlogik
15. vollständige Integrations- und Referenztests

Die ausführliche Checkliste wird in [FORTSCHRITT.md](FORTSCHRITT.md) gepflegt.

## Aktuelle Fortschrittseinschätzung

Ohne Grafik, Audio, Shader und finales optisches Polishing:

- Planung / Systemdesign: ca. 80 %
- Datenbanken / strukturierte Inhalte: ca. 65 %
- technische Kernsysteme / Prototypen: ca. 50 %
- Weltkarte / Gebietsgrundsystem: ca. 70 %
- Eventkarten-Grundsystem: ca. 65 %
- eigentliche Gameplay-Inhalte / Kartenbefüllung: ca. 20 %
- funktional spielbare Gesamtfassung: ca. 40 %

Die Werte sind bewusst Näherungswerte und werden nach größeren abgeschlossenen Systemblöcken neu bewertet.
