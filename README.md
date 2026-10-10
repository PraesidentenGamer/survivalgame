# Survival Game

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

## Aktueller Stand

Den ausführlichen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)
- [FORTSCHRITT.md](FORTSCHRITT.md) – kompakte Arbeitsübersicht und Pflichtpunkte bis zur vollständig spielbaren Fassung
- [IDEEN.md](IDEEN.md) – spätere Ideen und optionale Erweiterungen

## Aktueller Schwerpunkt

Der kurzfristige Schwerpunkt liegt auf der **Ausgabe des ersten externen Testbuilds**. Der Windows-Build ist grundsätzlich möglich; aktuell wird noch die sichere Mitlieferung der externen Datenbanken über `StreamingAssets` abgeschlossen.

Aktuelle Datenrichtung:

```text
DB
↓
C#-Loader / Manager
↓
Spielsysteme
```

Bestehende Skript-, Prefab- und Inspector-Strukturen bleiben dabei kompatibel.

## Technische Basis

Bereits vorhanden bzw. als Prototyp bestätigt sind unter anderem:
- Spielerbewegung
- Kamera
- Spielerleben
- Kampfgrundlage
- Interaktion
- Inventar/Stacks
- Koordinaten
- Save-Prototyp
- Weltkarten-Ausgänge und Reisen
- funktionsfähige Weltkarte mit `WorldMapUI.cs`
- Hover-/InfoPanel-Anzeige und Betreten von Gebieten
- 30 Maps + Weltkarte in den Build Settings
- `Prefab_MapBoundsAndExits` als gemeinsamer Rand-/Exit-Aufbau der Standardmaps
- AreaData
- AreaSpawnManager
- AreaSpawnZone
- Ressourcen-Spawning
- Lootkisten/Container
- Türsystem
- Testzombie
- GameManager


## Neu: Hauptmenü und globales Pause-System

Für den ersten Testbuild sind jetzt zusätzlich vorhanden:
- Hauptmenü mit eigenem Hintergrundbild
- Einstellungen für Grafikmodus, Auflösung, Vollbild und Lautstärke
- Pausemenü mit Fortsetzen, Speichern, Laden, Einstellungen, Hauptmenü und Beenden
- globales `Prefab_PersistentPauseSystem` mit `DontDestroyOnLoad`
- global abgesichertes `EventSystem` für funktionierende UI-Interaktion nach Szenenwechseln
- keine manuelle Pause-System-Kopie in allen 30 Maps erforderlich

Pause-Regel:
- Gameplay steht
- Produktionen und Events dürfen während der Pause weiterlaufen
- bei komplett geschlossenem Spiel laufen nur Events weiter

**Geschätzter Stand bis zum ersten auslieferbaren externen Testbuild: ca. 95 %.**


## Musikstruktur

Aktuell vorbereitet:
- `Prefab_IngameMusik`
- funktionierende Hauptmenü-Musik
- eigener Bereich für Weltkartenmusik
- je ein Musikordner für die 30 festen Gebiete unter `music/Feste_Gebiete`
- gemeinsame Musik für die `EventMap`, unabhängig vom jeweiligen temporären Event
- `Test_Kiefernwald_v01` ist ausgeschlossen
- Musikdateien werden als `.ogg` organisiert

## Neu bestätigt: dynamische EventMap

Eine einzige gemeinsame `EventMap`-Szene kann unterschiedlich große temporäre Events darstellen.

Erfolgreich getestet:
- 10 × 10 UE
- 15 × 20 UE
- 20 × 12 UE

Dabei werden dynamisch angepasst:
- `EventGround`
- umlaufender Rückkehrtrigger auf allen vier Seiten
- physische Border / Runterfallschutz
- Eventinhalte

Der Spieler startet bei jedem Event bei:

```text
Position   X: 0   Y: 1   Z: 0
```

Die Rückkehr zur Weltkarte verwendet die gemeinsame `WorldMapExit`-Logik.

## WorldMapExit

Die Spielererkennung wurde korrigiert:
- Tag `Player` als primäre Erkennung
- `PlayerMovement` im Parent als Fallback
- keine Abhängigkeit mehr vom Objektnamen

Dadurch funktioniert der Exit mit allen `Prefab_Player`-Instanzen und zentral auf allen Standardmaps, die `Prefab_MapBoundsAndExits` verwenden.

## Nächster Entwicklungsblock

### Bis zum ersten Tester-Build
1. Datenbanken über `StreamingAssets/database` vollständig mitliefern
2. Windows-x86_64-Build neu erzeugen
3. Start und Datenbankzugriff kurz prüfen
4. Build-Ordner zusammen mit der Tester-Prüfliste verteilen

### Danach
1. Event-Testdaten aus `EventMapTest.cs` herauslösen
2. `events.json.db` an den Eventmanager anbinden
3. Event-ID, Größe, Dauer, Loot, Gegner, Ressourcen und Layout aus DB laden
4. Eventzustand in Save/Load integrieren
5. danach Gegner-, Loot- und Ressourcen-Spawns vollständig anbinden
6. anschließend die offenen Pflichtsysteme aus [FORTSCHRITT.md](FORTSCHRITT.md) schließen

## Ziel „vollständig spielbar“

Für die aktuelle Arbeitsplanung werden **Grafik, Audio, Shader und finales optisches Polishing vorerst ausgeklammert**.

Die noch nötigen Kernblöcke sind insbesondere:
- produktionsreifes Eventsystem
- Gegner- und Kampfsystem
- Survivalwerte
- Inventar / Ausrüstung / Haltbarkeit
- Crafting / Werkbänke / Produktion
- Basisbau / Horden
- XP / Level / Skills / Forschung
- Quest / Story / Storyflags
- Save / Load
- Händler / Economy / Shop
- Begleiter / NPC-KI
- Fahrzeuge / Weltreise
- Zeit / Offline / Login / Events
- vollständige Integrations- und Referenztests

Aktuell geschätzter Stand der **funktional spielbaren Fassung ohne Grafik/Audio/Shader-Polish: ca. 40 %**.

Details: [FORTSCHRITT.md](FORTSCHRITT.md)

## Ziel „endgültiges Spiel“

Die funktional spielbare Fassung ohne finales Grafik-/Audio-/Shader-Polishing liegt weiterhin bei ungefähr **40 %**.

Für das tatsächlich endgültige Spiel inklusive vollständiger Systeme, Story, Quests, Karteninhalte, Gegner, Crafting/Produktion, Basisbau, Progression, Händler, Begleiter, Fahrzeuge, Events, Grafik, Modelle, Texturen, Animationen, Musik, Soundeffekte, Balance, Optimierung und abschließender Tests wird der aktuelle Gesamtstand auf ungefähr **30 %** geschätzt.

**Damit fehlen bis zum endgültigen Spiel noch ungefähr 70 %.**

## Aktuelle Planungsdokumente

Zusätzlich dokumentiert:
- `docs/Remnants_of_Tomorrow_Siedlungsgebaeude_Planungsstand.txt` – aktueller vollständiger Siedlungsgebäude- und Ausbauplan
- `docs/Remnants_of_Tomorrow_Horrorfiguren_Planung.txt` – Horrorfiguren sowie Regel für abschaltbare Horror-/Gruseleffekte
- `docs/Remnants_of_Tomorrow_Basis_Horden_Planungsstand.txt` – aktueller Basis- und Hordenplan
- `docs/Remnants_of_Tomorrow_Fahrzeuge_Planungsstand.txt` – aktueller vollständiger Fahrzeugplan inklusive Fund/Bergung, Wiederaufbau, Treibstoff, Reise, Reparatur, Überfahren, Lackierung und Farb-Rezepten
- `docs/Remnants_of_Tomorrow_Begleiter_Planungsstand.txt` – Begleiter, Sarah, Hunde, Passive Hilfe, Begleiter-KI und Siedlungs-NPCs; bestätigte Regeln und offene Punkte

Kurzregeln aus der neuen Planung:
- Siedlungsgebäude maximal Stufe 3, Ausbau pro Stufe maximal 30 Minuten
- Expeditionen ausschließlich über die Siedlung mit eigenem Expeditionsfahrzeug
- Horror-/Gruseleffekte optional; Ersatzgegner übernehmen sämtliche Gameplay-Eigenschaften 1:1
- jeder Boss hat genau eine Kampfphase
- Hauptstory Pflicht, Nebenstory/Nebenquests/SECRET optional
- Fahrzeuge werden überwiegend als Wracks gefunden und später in der Hauptbasis wieder aufgebaut
- Fahrzeugaufbau kann unterbrochen werden; jeder korrekt montierte Schritt wird dauerhaft gespeichert
- jedes Fahrzeug vorerst nur 1x
- keine Fahrzeug-Upgrades; feste Endwerte pro Fahrzeug
- 12 festgelegte Fahrzeugfarben mit festen Sprühdosen-Rezepten


## Stand 10.10.2026 – Fahrzeug-Funktionsplanung abgeschlossen

Die verbindlichen Regeln für die acht regulären Fahrzeuge sowie
Bergungs-Lkw, Treibstoff/Tankstellen, Reparaturen, Lager,
Begleitertransport, Weltkartenreisen und Sicherheitsfunktionen sind
dokumentiert:
[**Fahrzeug-Planungsstand**](docs/Remnants_of_Tomorrow_Fahrzeuge_Planungsstand.txt).
Die Umsetzung in Unity, Datenbankmigration und Tests folgen noch.
Die zuletzt dokumentierten Fortschritts-Schätzwerte sind keine
bestätigten Ergebnisse neuer Fahrzeugtests.

## Update 10.10.2026 – Fahrzeugprototyp und südliche Gebietsankunft (getestet)

Die zuvor abgeschlossene **Fahrzeug-Funktionsplanung** wird inzwischen durch erste tatsächlich getestete Unity-Prototypen ergänzt. Dies ist **keine** vollständige Fahrzeugimplementierung.

- `VehicleDatabaseLoader.cs` lädt die Fahrzeug-Hauptdatenbank (`Assets/StreamingAssets/database/vehicles.json.db`) mit **8 Fahrzeugen**.
- `VehicleSteeringDatabaseLoader.cs` lädt `vehicle_steering.json.db` mit **8 Fahrzeug-Steuerungsdatensätzen**. Die Physikwerte sind vorläufige Testwerte.
- `VehicleManager.cs` verwaltet die 8 Fahrzeuge zunächst gesperrt und nicht zusammengebaut; Freischaltungen, vollständige Persistenz und Spielmechaniken sind noch nicht fertig.
- Der datenbankgestützte Jeep-Fahrtest mit `VehiclePhysicsConfigurator.cs`, `VehicleWheelController.cs` und `VehicleInteraction.cs` wurde erfolgreich durchgeführt: **4 Räder, AWD, interne Geschwindigkeit 65, Unity-Höchstgeschwindigkeit 12,03 Einheiten/s**; Ein- und Aussteigen funktionieren im Test.
- `WorldMapArrival.cs` ergänzt die südliche Ankunft **ohne Eingriffe** in die bereits funktionierenden Skripte und Prefabs. Mit Unity **2017.2.5f1** getestet: in der zentrierten **200×200**-Standardkarte bei **X=0, Z=-90**, außerhalb des südlichen Weltkarten-Ausgangstriggers. Ankunft beim Wechsel zwischen verschiedenen Gebietskarten bestätigt; Bewegung über die Karte möglich.
- `WorldMapTravel.cs`, `WorldMapExit.cs`, `SaveSystem.cs`, `Prefab_Player`, `AreaSpawnManager.cs` und `AreaSpawnZone.cs` wurden für diese Änderung **nicht verändert**. Die Ressourcen-Spawnzone bleibt **190×190**.
- **Offen:** Fahrzeug auf der Weltkarte tatsächlich mitnehmen und im Zielgebiet mit Fahrer an Bord südlich erscheinen lassen; Reise-/Fahrzeugzustände in Save/Load integrieren; F11-Wiederherstellung nach Einführung des Arrival-Systems gesondert erneut testen.

Die Fortschrittsschätzungen bleiben unverändert (**ca. 40 %** funktionaler Umfang ohne finales Grafik-/Audio-Polishing, **ca. 30 %** endgültiges Spiel). Die Dokumentation beschreibt nur den bestätigten lokalen Entwicklungs-/Teststand; die genannten Unity-Quelldateien sind damit nicht automatisch im Repository eingecheckt.
