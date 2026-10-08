# Entwicklungsstand

**Stand:** 09.10.2026

## Aktuelle Entwicklungsphase

Die grundlegende Planung der Pflichtsysteme ist weit fortgeschritten. Der aktuelle kurzfristige Schwerpunkt liegt auf dem **ersten externen Testbuild**; parallel bleiben die datengetriebene Weltkarte, Gebietssysteme und die dynamische EventMap die technische Basis.

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


## Hauptmenü und globales Pause-System

Für den ersten Testbuild wurde der Menü-/Pause-Bereich deutlich erweitert.

Bestätigter Stand:
- Hauptmenü mit eigenem Hintergrundbild
- Menüstruktur für Neues Spiel, Spiel laden, Einstellungen und Beenden
- Einstellungsoberfläche für Grafikmodus, Auflösung, Vollbild sowie Lautstärke
- Pausemenü mit Fortsetzen, Speichern, Laden, Einstellungen, Hauptmenü und Beenden
- `Prefab_PersistentPauseSystem` bündelt `Canvas_PauseMenu` und `PauseMenuManager`
- `PersistentPauseSystem.cs` hält das System per `DontDestroyOnLoad` über Szenenwechsel hinweg aktiv
- nur eine globale Instanz ist vorgesehen
- das Pause-System muss dadurch nicht manuell in alle 30 Maps eingebaut werden
- ein global abgesichertes `EventSystem` stellt die Interaktion der Pause-Buttons nach Szenenwechseln sicher
- vorhandene Szenen-`EventSystem`-Instanzen werden berücksichtigt

Festgelegte Pause-Regel:
- normales Gameplay pausiert vollständig
- Produktionen dürfen während der Pause weiterlaufen
- Events dürfen während der Pause weiterlaufen
- bei komplett geschlossenem Spiel laufen nur Events weiter

Die Ausnahmen Produktion/Events müssen in den jeweiligen Laufzeitsystemen ausdrücklich zeitunabhängig von `Time.timeScale` umgesetzt werden.


## Musik und Audio-Struktur

Die Musikstruktur wurde vorbereitet:
- gemeinsames `Prefab_IngameMusik`
- Hauptmenü-Musik eingebunden und funktionierend
- Weltkartenmusik als eigener Bereich
- `music/Feste_Gebiete` mit getrennten Ordnern für die 30 festen Gebiete
- `Test_Kiefernwald_v01` bleibt ausgeschlossen
- `EventMap` verwendet unabhängig vom konkreten Event eine gemeinsame Eventmusik
- Musik wird als `.ogg` organisiert
- weitere Titel werden schrittweise generiert und ergänzt

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


## Windows-Testbuild und Datenbanken

Ein erster Windows-x86_64-Build wurde erzeugt. Dabei wurde ein echter Buildfehler gefunden: Die externen `.json.db`-Datenbanken wurden nicht automatisch mit ausgeliefert.

Aktueller Lösungsstand:
- `Assets/StreamingAssets/database` wurde als Build-Datenbankpfad vorbereitet
- `AreaData.cs` verwendet primär `Application.streamingAssetsPath/database/areas.json.db`
- ältere Projekt-/Buildpfade bleiben vorerst nur als Fallback erhalten
- der nächste Build muss prüfen, ob die Datenbanken nun unter `<Spiel>_Data/StreamingAssets/database` enthalten und erreichbar sind

## Erster Tester-Build

Der erste externe Build soll gezielt den vorhandenen Kern prüfen, nicht bereits alle späteren Spielsysteme enthalten.

Vorhanden bzw. testbar vorgesehen sind insbesondere Hauptmenü, Einstellungen, Pausemenü, Inventar, Sammeln, Loot, vorhandener Kampfstand, Basis, Weltkarte, Gebietswechsel, EventMap und Save/Load-Prototyp.

Der Windows-Build wurde bereits grundsätzlich erzeugt. Vor der Ausgabe an die Tester fehlt im Wesentlichen nur noch der erneute Build mit korrekt ausgelieferten Datenbanken und ein kurzer Start-/DB-Zugriffstest.

**Geschätzter Stand bis zum ersten auslieferbaren externen Testbuild: ca. 95 %.**

## Aktuelle Fortschrittseinschätzung

Ohne Grafik, Audio, Shader und finales optisches Polishing:

- Planung / Systemdesign: ca. 80 %
- Datenbanken / strukturierte Inhalte: ca. 65 %
- technische Kernsysteme / Prototypen: ca. 50 %
- Weltkarte / Gebietsgrundsystem: ca. 70 %
- Eventkarten-Grundsystem: ca. 65 %
- eigentliche Gameplay-Inhalte / Kartenbefüllung: ca. 20 %
- funktional spielbare Gesamtfassung: ca. 40 %
- endgültiges Spiel inklusive vollständiger Inhalte, Grafik, Audio und Polishing: **ca. 30 %**

**Noch offen bis zum endgültigen Spiel: ca. 70 %.** Der größte Rest liegt in der vollständigen Umsetzung und Verbindung der noch offenen Systeme sowie in Story/Quests, Kartenbefüllung, Grafik, Audio, Animationen, Balance, Optimierung und abschließender Qualitätssicherung.

Die Werte sind bewusst Näherungswerte und werden nach größeren abgeschlossenen Systemblöcken neu bewertet.

## Planungsstand Siedlung und Horror

Die Siedlungsplanung wurde deutlich konkretisiert. Der aktuelle Gebäudekern umfasst 14 Hauptbereiche: Zentrale/Verwaltung, Medizinzentrum, Technikzentrum, Markt, Zentrallager/Depot, Funk- und Expeditionszentrum, Forschungszentrum, Versorgungszentrum, Verteidigungszentrum, Industriezentrum, Wohnbereich, Landwirtschaft/Gewächshaus, Fahrzeugdepot und Gemeinschaftshaus.

Verbindliche Planungsregeln:
- Gebäude maximal Stufe 3
- Ausbauzeit pro Stufe maximal 30 Minuten
- ein Hauptmodell pro Gebäude genügt; Baufortschritt kann über Gerüste/Materialstapel/etc. gezeigt werden
- Fach-NPCs benötigen Wohnraum plus passendes Gebäude in der nötigen Stufe
- Expeditionen nur in der Siedlung und nur mit eigenem Expeditionsfahrzeug
- geplantes Siedlungs-Bewegungstempo ca. +25 %
- Strom und Wasser getrennt; Energiemangel führt in einen Notmodus
- Generatoren als Grundversorgung, Solaranlage später ergänzend; Wasserkraftwerk derzeit nur optionale Idee
- Wachhunde gehören funktional zum Verteidigungszentrum, normale Hunde bleiben an der Spielerbasis

Zusätzlich wurde das Horror-/Gruselsystem geplant:
- optionale Abschaltung der Horror-/Gruseleffekte
- normale Ersatzgegner übernehmen bei deaktivierter Darstellung 1:1 Lebenspunkte, Schaden, Geschwindigkeit, Fähigkeiten, Resistenzen/Schwächen, Loot, Spawnregeln sowie Quest-/Event-/Storyfunktion
- Gegnerkategorien: Normal, Spezial, Elite, Boss, Event/Story
- Bossregel: genau eine Kampfphase pro Boss

Die vollständigen Detailplanungen liegen in den TXT-Dateien unter `docs/`.
