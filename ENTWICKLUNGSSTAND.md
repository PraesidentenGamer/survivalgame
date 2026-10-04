# Entwicklungsstand

**Stand:** 04.10.2026

## Aktuelle Entwicklungsphase

Die grundlegende Planung der Pflichtsysteme ist weit fortgeschritten. Parallel wurde der aktuelle Unity-/C#-Bestand vollständig geprüft: **42 vorhandene C#-Skripte** sind erfasst und eingeordnet.

Grundregel für den weiteren Ausbau:
- bestehende **Skriptnamen bleiben unverändert**
- vorhandene Strukturen, auf die Prefabs/Maps/Inspector-Zuweisungen bereits angewiesen sind, werden kompatibel weitergeführt
- neue Systeme dürfen über zusätzliche Loader/Manager ergänzt werden
- C# bleibt die Logikschicht; Inhalte und Balance wandern schrittweise in Datenbanken

## Architektur

**C# = Logik und Systeme**  
**`.json.db` = strukturierte Spielinhalte und Balance im Ordner `database`**  
**JSON = Einstellungen/Config**  
**.sgsave = Spielstand**

### Konfigurationsdateien
Normale Einstellungen dürfen als JSON gespeichert werden, z. B. Grafik, Audio, Steuerung, Interface und Gameplay.

### Spieldatenbanken
Die strukturierten Spieldaten liegen aktuell als `.json.db` im Projektordner `database`. Diese Dateien sind für strukturierte Inhalte vorgesehen, z. B.:
- Items
- Ressourcen
- Rezepte
- Lootpools
- Gegner
- Gebiete
- Quests
- Händler
- Events
- XP- und Balancewerte

Sie müssen nicht absichtlich unlesbar sein.

### Spielstände
Die endgültige Spielstand-Endung ist:

`.sgsave`

Geplant:
- strukturierte Save-Daten
- optional komprimiert
- AES-256-GCM verschlüsselt
- Integritätsprüfung beim Laden
- internes Support-/Save-Tool zum Lesen, Prüfen und Reparieren
- normale Spieler sollen die Daten nicht einfach mit einem Texteditor ändern können

## Save-System

Geplant:
- 10 manuelle Slots
- Autosave: Aus / 5 / 10 / 15 / 30 / 60 Minuten
- Pflichtsave bei Gebiets-/Szenenwechsel
- Recovery-Save bei Absturz/Fehler
- Save-Versionierung und Migration
- temp-Datei/atomarer Austausch statt direktes Überschreiben
- Save-Slots zeigen Ort, Datum/Uhrzeit, Spielzeit, Level und Storyfortschritt

Interne Save-Bereiche:
- Meta
- Player
- Inventory
- DeathSystem
- World
- Quests
- Events
- Trader
- Production
- Base
- Vehicles
- NPC
- Research
- spielstandsbezogene Settings

## Story- und Questsystem

Die Hauptstory soll deutlich größer als ein einzelner kurzer Kampagnenbogen werden.

Grundrichtung:
- mehrere große Akte und Kapitel
- ungefähr 150–250 Hauptquests als mögliche Zielgröße
- Tschernobyl ist sehr später Storyabschnitt, aber nicht endgültiges Ende
- spätere Storyupdates können weitere Sagas anschließen
- Hauptstory ist eng an Level und Fortschritt gekoppelt

Beispielhafte Levelbereiche:
- Akt 1–3: Level 1–20
- Akt 4–5: etwa 20–35
- Akt 6–7: etwa 35–50
- Akt 8–10: etwa 50–70
- Akt 11–13: etwa 70–85
- Akt 14–16: etwa 85–100

Dabei sollen Levelbereiche sich überschneiden dürfen. Normales ausgewogenes Spielen aus Hauptquests, Nebenquests, Looten, Farmen, Erkunden, Crafting und Kämpfen soll die nötigen Level ohne zähes Grinding erreichbar machen.

### XP-Event
Wiederkehrendes XP-Event vorgesehen, z. B. mit Bonus auf:
- Gegner
- Farmen/Sammeln
- Crafting/Produktion
- Erkunden
- Nebenquests

Hauptstory-XP muss nicht zwingend verstärkt werden.

## Freies Fliegen

Eine eigene Questreihe schaltet später **freies Fliegen ohne Fahrzeug** frei.

Grundrichtung:
- Mid-/Late-Game
- eigene Questreihe
- Forschungs-/Prototypenbezug
- nach Freischaltung eigener kleiner Skillbaum möglich
- getrennt vom Helikopter-/Luftfahrzeug-System
- bestimmte Innenräume/Bunker können Fliegen einschränken oder deaktivieren

## UI / HUD

Die visuelle Richtung ist festgelegt.

### HUD
Referenz:
- Gebiet oben links
- wichtige Gebietsinfo oben rechts
- Leben, Durst, Hunger unten links
- zusätzliche Statuswerte nur bei Bedarf
- Minimap unten rechts
- **keine klassische Schnellzugriffsleiste**

### Inventar / Container
Grundlayout:
- Spielerinventar links
- Tasche + Rucksack
- Container rechts
- Aktionen unten
- Main Hand / Second Hand und Ausrüstung später integriert

Die Oberfläche soll auf starken Geräten stark transparent/gläsern wirken. Zielrichtung: sehr niedrige Deckkraft der Flächen, während Rahmen, Text und Icons klar lesbar bleiben.

### Questbuch
Optische Richtung festgelegt:
- Kategorien links
- Questliste mittig
- Details rechts
- Hauptstory, Nebenquests, Events, Forschung, Siedlung, Händler, Abgeschlossen
- Questziele, Fortschritt, empfohlenes Level, Gebiet, Belohnungen und Voraussetzungen sichtbar

### Weltkarte
Der obere Bereich des bestehenden Weltkarten-Mockups dient als Referenz:
- große Weltkarte
- Gebietsmarker mit Namen und Symbol
- Schwierigkeitsfarbe
- Legende ein-/ausblendbar
- gesperrte/spätere Gebiete sichtbar markierbar
- Eventtimer/Marker später integrierbar

### Einstellungen
Optische Richtung festgelegt:
- dunkle Survival-Optik
- transparente Flächen
- Kategorien Spiel, Grafik, Audio, Steuerung, Interface, Gameplay, Barrierefreiheit
- Presets:
  - Schwache Geräte
  - Automatik
  - Starke Geräte
  - Benutzerdefiniert

UI-Transparenz wird abhängig von der Systemleistung reduziert. Automatik darf CPU/GPU/RAM/VRAM und Grafikfähigkeiten über normale Unity-/SystemInfo-Abfragen berücksichtigen. Keine Windows-Dienste oder tiefe Systemintegration notwendig.

## Aktueller Weltkarten-Stand

Die Weltkarte ist technisch funktionsfähig.

Aktuell bestätigt:
- **30 dauerhafte Maps + Weltkarte** sind in den Unity **Build Settings** eingetragen
- `WorldMapUI.cs` ist aktiv im Einsatz
- Gebietsmarker reagieren auf **Hover**
- ein **InfoPanel** zeigt die vorgesehenen Gebietsinformationen
- Gebiete können über die Weltkarte **betreten** werden
- die vorhandene Reise-/Szenenstruktur bleibt mit `WorldMapExit.cs` und `WorldMapTravel.cs` kompatibel
- die 30 dauerhaften Gebiete bleiben die feste Hauptstruktur; Event-/Storygebiete werden getrennt behandelt

Damit ist die Weltkarte kein reines Mockup mehr, sondern eine funktionierende technische Basis für die weitere Entwicklung.

## Kamera

`CameraFollow.cs` bleibt bestehen.

Spätere Erweiterungen:
- zoombare Kamera
- Zoom bis in First Person
- Third Person und First Person im gemeinsamen Kamerasystem
- Kollisions-/Wandprüfung
- Innenraum-/Fahrzeugparameter

### Gebäude
Beim Betreten eines Gebäudes soll die störende Decke vollständig ausgeblendet werden. Bei mehrstöckigen Gebäuden nur die relevante obere Ebene. Umsetzung voraussichtlich über separates Sichtbarkeits-/Trigger-Script, nicht direkt in `CameraFollow.cs`.

## Inhaltsregeln

Das Spiel richtet sich an Erwachsene; Zielrichtung ist **18+ nach deutschem Maßstab**.

Wichtig:
- deutliche Gewalt und Blut möglich
- Blutdarstellung einstellbar: Aus / Schwach / Normal / Stark
- bei Aus/Schwach stattdessen neutrale Farbflecken als Trefferfeedback
- keine illegalen/recreationalen Drogen als Spielsystem
- Medikamente bleiben erlaubt
- Alkohol darf vorkommen
- Destillieranlage bleibt möglich
- bei jedem Spielstart erscheint ein Inhalts-/Alters-Hinweis
- offizielle USK-Kennzeichnung wird nicht vorweggenommen; bis zu einer Prüfung nur Zielrichtung 18+

## Zeit / Offline

Zentrales Zeitsystem vorgesehen.

Aktuell:
- 24-Stunden-Ingame-Uhr
- Tageslänge konfigurierbar
- 6 Echtzeitstunden = 24 Ingame-Stunden als vorläufiger Standard
- Produktion/Bau/Forschung/geeignete Events können offline weiterlaufen
- Hunger/Durst sinken offline nicht blind weiter
- Leichentimer pausiert offline
- Horden dürfen offline näher rücken, eigentlicher Angriff startet aber erst bei aktivem Spieler

## Area-/Spawn-System

Das vorhandene System ist bereits ein echter Kernbestandteil.

### `AreaData.cs`
- verwaltet die festen/permanenten Gebiete
- 30 dauerhafte Hauptgebiete bleiben zentrale Zielstruktur
- Story-/Eventgebiete werden getrennt behandelt
- bestehende Struktur bleibt kompatibel

### `AreaSpawnManager.cs`
- zentrale Spawnlogik für Ressourcen im Gebiet
- nutzt `ResourceSpawnRule[]`
- würfelt Min-/Max-Mengen
- hält Mindestabstände ein
- verwendet die `AreaSpawnZone`
- ist für alle Maps als gemeinsamer Kern gedacht

### `AreaSpawnZone.cs`
- definiert den räumlichen Bereich, in dem dynamische Inhalte erscheinen dürfen
- BoxCollider/Bounds liefern gültige Zufallspositionen

Grundregel:
**GM/AM entscheidet, was und wie viel; SpawnZone definiert, wo es erscheinen darf.**

Eventgebiete erhalten eigene Regelpakete und werden nicht wie normale Ressourcengebiete behandelt.

## 42 vorhandene C#-Skripte

Der komplette aktuelle Bestand wurde geprüft.

Feste Regel:
**Bestehende Skriptnamen bleiben unverändert.**

Bereits als wichtige Kernbasis bestätigt:
- AreaData.cs
- AreaSpawnManager.cs
- AreaSpawnZone.cs
- CameraFollow.cs
- GameManager.cs
- PlayerCombat.cs
- PlayerCoordinates.cs
- PlayerHealth.cs
- PlayerInteraction.cs
- PlayerInventory.cs
- PlayerMovement.cs
- ResourceSpawnData.cs
- SaveGameData.cs
- SaveSystem.cs
- WorldMapExit.cs
- WorldMapTravel.cs
- DemoLootChest.cs
- DemoLootEntry.cs
- DemoChestItem.cs
- DemoDoor.cs
- DemoZombie.cs

Die gleichartigen Demo-Ressourcenskripte bleiben ebenfalls erhalten. Sie werden später schrittweise datengetrieben, ohne ihre bestehenden Dateinamen oder die bereits verwendete Manager-Struktur zu brechen.

### Wichtige technische Feststellungen

- `ResourceSpawnData.cs` muss strukturell kompatibel bleiben, da der AreaSpawnManager und die 30 Maps bereits darauf aufbauen.
- `DemoLootChest.cs` enthält bereits einen umfangreichen Loot-/Container-Prototypen mit einmaliger Lootgenerierung, Stacklogik, Alles nehmen, Mengenübertragung und Alles einlagern.
- `PlayerInventory.cs` besitzt bereits Stack-, Kapazitäts-, Entfernen- und Transfergrundlagen.
- `WorldMapExit.cs` hängt an den Kartenrand-Triggern Nord/Süd/Ost/West.
- `WorldMapTravel.cs` übernimmt die Gegenrichtung von der Weltkarte ins Zielgebiet.
- `DemoZombie.cs` besitzt bereits einfache Erkennung, Verfolgung, Angriff und Tod.
- `GameManager.cs` ist als persistente Singleton-Schaltstelle vorbereitet.

## Nächster technischer Schwerpunkt

Der nächste konkrete Entwicklungsblock ist das Gegner-Spawn-System.

### 1. `EnemySpawnManager.cs`
Geplant:
- Anbindung an die vorhandene Area-/Spawn-Struktur
- Gegner-Prefabs bzw. Gegnerdefinitionen pro Gebiet
- Min-/Max-Anzahl pro Gebiet
- zufällige gültige Spawnpositionen innerhalb der `AreaSpawnZone`
- Mindestabstand zum Spieler
- keine Spawns außerhalb der gültigen Kartenfläche
- Vorbereitung auf gebietsabhängige Schwierigkeitsstufen
- erneute Zufallsverteilung beim erneuten Betreten normaler Ressourcengebiete
- Event-/Storygebiete können später eigene Regeln verwenden

### 2. Datenanbindung
Gegnerdaten sollen schrittweise aus den vorhandenen `database/*.json.db`-Dateien geladen werden. Dazu gehören insbesondere:
- Gegnertyp
- Gebietszuordnung
- Spawngewicht/Wahrscheinlichkeit
- Mindest-/Maximalanzahl
- Leben
- Schaden
- Bewegung
- weitere spätere KI-/Loot-/Statuswerte

### 3. `DemoZombie.cs` kompatibel weiterentwickeln
Der bestehende Dateiname bleibt unverändert. Die vorhandene Erkennung, Verfolgung, Angriff und Tod werden schrittweise aus der hart codierten Demo in eine allgemeiner nutzbare Gegnerlogik überführt.

Erster Testgegner bleibt bewusst einfach:
- schwacher Zombie
- ungefähr 5 Leben
- Bewegungstempo ungefähr 0,5
- Schaden ungefähr 0,5 pro Treffer
- erster Einsatz im grünen Kiefernwald

### Danach
Vorgesehene Reihenfolge nach dem Gegner-Spawn-System:
1. Gegnerdaten/AI weiter verallgemeinern
2. Lootverteilung stärker über GM/AM und Datenbank zentralisieren
3. AreaState und Gebiets-Persistenz
4. Survivalwerte und Tod-/Leichensystem
5. XP-/Levelsystem
6. Quest-/Storysystem
7. Produktion/Werkbänke und weitere Progressionssysteme
