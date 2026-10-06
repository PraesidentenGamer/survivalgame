# Survival Game

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

## Aktueller Stand

Den ausführlichen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)
- [FORTSCHRITT.md](FORTSCHRITT.md) – kompakte Arbeitsübersicht und Pflichtpunkte bis zur vollständig spielbaren Fassung
- [IDEEN.md](IDEEN.md) – spätere Ideen und optionale Erweiterungen

## Aktueller Schwerpunkt

Der aktuelle Schwerpunkt liegt auf der **datengetriebenen Weltkarte und der dynamischen EventMap**.

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
