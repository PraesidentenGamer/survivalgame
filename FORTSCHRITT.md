# Projektfortschritt

**Stand:** 06.10.2026

Diese Datei ist die kompakte Arbeitsübersicht für den aktuellen Projektstand. Sie trennt bestätigte/fertige Systeme von offenen Pflichtpunkten für eine vollständig spielbare Fassung.

## Aktueller Schwerpunkt

**Dynamische Eventgebiete stabilisieren und anschließend die noch fehlenden Kernsysteme für eine vollständig spielbare Fassung schließen.**

Aktuelle Architektur:
```text
DB = eigentliche Datenquelle
C# = Vermittler zwischen Spiel und DB
Spielsysteme = benutzen die gelieferten Daten
```

Grundregel:
- bestehende Werte erhalten
- spätere ausdrücklich bestätigte Entscheidungen ersetzen ältere Vorschläge
- unbekannte Werte nicht erfinden
- keine doppelte Pflege derselben Daten in C# und DB
- C# führt Logik aus; Inhalte und Balance werden möglichst datengetrieben
- bestehende funktionierende UI-/Prefab-/Inspector-Strukturen bleiben kompatibel

## Geschätzter Gesamtfortschritt

Die Prozentwerte beziehen sich auf die erste vollständig spielbare Fassung. Grafik, Audio, Shader und finales optisches Polishing sind bei dieser Einschätzung **vorerst ausdrücklich ausgeklammert**.

| Bereich | Geschätzter Stand |
|---|---:|
| Planung / Regeln / Systemdesign | ca. 80 % |
| Datenbanken / strukturierte Inhalte | ca. 65 % |
| technische Kernsysteme / Prototypen | ca. 50 % |
| Weltkarte / Gebietsgrundsystem | ca. 70 % |
| Eventkarten-Grundsystem | ca. 65 % |
| eigentliche Gameplay-Inhalte / Kartenbefüllung | ca. 20 % |
| funktional spielbare Gesamtfassung ohne Grafik/Audio/Shader-Polish | **ca. 40 %** |

Die Prozentwerte bleiben Näherungswerte. Viele Systeme sind bereits geplant oder prototypisch vorhanden, müssen aber noch vollständig miteinander verbunden, mit Inhalten gefüllt und getestet werden.

## Datenbankstatus

| Bereich | Stand | Offene Punkte |
|---|---|---:|
| Gegner | fertig, 53 Gegner | 0 |
| Gebiete | 30 dauerhafte Gebiete; `areas.json.db` ist die maßgebliche Datenquelle | Integrations-/Praxistests |
| Rezepte | fertig | 0 |
| Welt/Reise | fertig | 0 |
| Skills Spieler | fertig, 75 normale Skills + SECRET-System | 0 |
| Forschung | fertig, 133 Knoten | 0 |
| Items | integriert, 326 historische Slots + Systemitems | Referenz-/Qualitätsprüfung |
| Ressourcen | strukturell fertig | Restwerte schließen |
| Loot | strukturell fertig | Restwerte schließen |
| Fahrzeuge | strukturell fertig | Restwerte schließen |
| Events | strukturell vorbereitet | echte Laufzeitanbindung |
| Einstellungen | strukturell fertig | Restwerte schließen |
| Progression/XP | vollständig erzeugt | Qualitäts-/Referenzprüfung |
| Pakete/Belohnungen | vollständig erzeugt | Item-Referenz-/Stackprüfung |
| Quests/Story | aktive Planungsphase | DB und Laufzeitsystem offen |
| Shop | noch nicht gebaut | offen |
| Händler | noch nicht gebaut | offen |
| Economy | noch nicht gebaut | offen |
| Begleiter/NPC-KI | Regeln weitgehend definiert | DBs + Laufzeitsystem offen |

## Aktueller Weltkarten- und Eventkarten-Stand

### Weltkarte

Bestätigt und funktionsfähig:
- 30 dauerhafte Maps + Weltkarte in den Build Settings
- Hover und Auswahl der Marker
- InfoPanel mit Gebietsinformationen
- BETRETEN über bestehenden Reiseablauf
- dynamische Eventmarker unter `MapData`
- Convex-Hull-Positionierung innerhalb der nutzbaren Marker-Kontur
- Sicherheitsabstände zu festen Markern und Außenkontur
- Eventmarker behalten während ihrer Laufzeit ihre einmal gewählte Weltkartenposition

### WorldMapExit.cs

Der Map-Exit-Fehler wurde behoben.

Frühere Ursache:
- Prüfung auf den exakten Objektnamen `"Player"`

Aktueller Stand:
- primäre Erkennung über den Tag `Player`
- zusätzlicher Fallback über `PlayerMovement` im Parent
- funktioniert dadurch mit allen `Prefab_Player`-Instanzen
- `Prefab_MapBoundsAndExits` wird auf allen Standardmaps zentral weiterverwendet
- Korrektur wirkt damit automatisch auf alle Maps, die dieses Prefab verwenden

### Dynamische EventMap

Die gemeinsame Szene `EventMap` ist technisch bestätigt. Es wird **keine eigene Szene pro temporärem Event** benötigt.

Aktueller Szenenaufbau:
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

Bestätigt:
- `EventGround` bleibt als feste technische Bodenbasis in der Szene
- Eventgröße wird zur Laufzeit auf das ausgewählte Event angepasst
- Spielerstart liegt standardmäßig bei `X=0, Y=1, Z=0`
- `BorderRoot` erhält dynamisch den kompletten Randaufbau
- grüner Rückkehrtrigger läuft auf **allen vier Seiten umlaufend**
- rote physische Border / Runterfallschutz liegt außen herum
- Rückkehr nutzt die gemeinsame `WorldMapExit`-Logik
- `EventSpawnRoot` enthält dynamische Eventinhalte

### Erfolgreicher Mehrgrößen-Test

Drei gleichzeitig aktive Testevents wurden erfolgreich geprüft:

| Event | Größe |
|---|---:|
| Testevent 1 | 10 × 10 UE |
| Testevent 2 | 15 × 20 UE |
| Testevent 3 | 20 × 12 UE |

Bestätigtes Ergebnis:
- dieselbe `EventMap` wurde für alle drei Events verwendet
- `EventGround` wurde jeweils auf die passende Größe skaliert
- Border und umlaufender Rückkehrtrigger passten sich der jeweiligen Größe an
- Spielerstart blieb bei `(0, 1, 0)`
- Rückkehr zur Weltkarte funktionierte
- Eventmarker wurden danach wieder korrekt aufgebaut
- die einmal festgelegten Eventpositionen bleiben erhalten

Damit ist das zentrale Konzept **eine gemeinsame dynamisch skalierbare EventMap für unterschiedlich große temporäre Events** erfolgreich nachgewiesen.

## Pflichtpunkte bis „vollständig spielbar“

Grafik, Audio, Shader und finales optisches Polishing sind in dieser Liste bewusst nicht enthalten.

### 1. Eventsystem produktionsreif machen
- Testdaten aus `EventMapTest.cs` entfernen
- echte Eventdaten aus `events.json.db` laden
- Event-ID eindeutig bis in die `EventMap` transportieren
- Größe, Dauer, Loot, Gegner, Ressourcen und Layout aus Daten lesen
- Eventablauf und Entfernung sauber persistieren
- Verhalten beim Ablaufen eines Events während der Spieler im Gebiet ist definieren
- Eventzustand in Savegame integrieren
- mehrere gleichzeitig aktive Events sauber verwalten

### 2. Gebiets- und Spawnlogik abschließen
- alle 30 dauerhaften Maps auf gemeinsame Area-/DB-Logik prüfen
- Ressourcen-Spawning vollständig datengetrieben
- Gegner-Spawning vollständig datengetrieben
- Lootkisten-Spawning vollständig datengetrieben
- getrennte Spawnzonen für Ressourcen, Gegner und Loot
- Gebietsreset / erneute Zufallsverteilung beim erneuten Betreten
- permanente Gebiete und storygebundene Orte korrekt von Zufallsreset ausnehmen

### 3. Gegner- und Kampfsystem vollständig machen
- `EnemySpawnManager.cs` produktionsreif
- 53 Gegnerdaten tatsächlich anbinden
- gemeinsame Gegnerbasis statt reiner DemoZombie-Sonderlogik
- Nahkampf
- Fernkampf
- Schadensarten / Schwächen / Resistenzen
- Tod, Loot und Respawnregeln
- Bosslogik
- Aggro-, Verfolgungs- und Rückkehrverhalten

### 4. Spieler-Survival vollständig verbinden
- Leben
- Hunger
- Durst
- Temperatur
- Strahlung
- Infektion
- Status-Effekte
- Kleidungsschutz
- Tod und Leiche
- Rückholtimer
- spätere Keep-Inventory-Freischaltung
- saubere Speicherung aller Werte

### 5. Inventar / Ausrüstung / Gegenstände
- 10 Grundslots vollständig produktionsreif
- Rucksackstufen
- Main Hand / Second Hand
- Ausrüstungsslots
- Haltbarkeit
- Stapellogik
- Item-Nutzung
- Containertransfer
- Gewichts-/Bewegungseinfluss
- komplette Item-DB-Anbindung

### 6. Crafting / Werkbänke / Produktion
- Rezepte aus DB laden
- Herstellungszeiten
- Werkbankvoraussetzungen
- Produktionswarteschlangen
- Reparatur
- Upgrades
- Materialverbrauch
- Offline-Fortschritt für geeignete Produktion

### 7. Basisbau
- Rasterbau
- 3×3-Grundraster
- Wände / Türen / Böden / weitere Bauobjekte
- Abriss mit 25 % Materialrückgabe
- Bauobjekt-Upgrades
- Lager-Upgrades
- maximal vorgesehene Etagen
- Hordenangriffe
- Beschädigung / Reparatur der Basis

### 8. Progression
- XP-Laufzeitsystem vollständig
- Level 1–100
- Level-Up-Belohnungen
- Skillpunkte
- Forschungspunkte
- Level-Freischaltungen
- Skill-Reset
- Forschungsbaum anbinden
- Story- und Levelvoraussetzungen gemeinsam prüfen

### 9. Quest- und Storysystem
- Quest-Datenbank fertigstellen
- Hauptstory-Grundbogen technisch abbilden
- Questzustände
- Ziele
- Fortschritt
- Belohnungen
- Voraussetzungen
- Questbuch
- SECRET-Missionen
- Storyflags
- verzweigte Entscheidungen / Sarah-Karma

### 10. Save-/Load-System produktionsreif
- endgültige `.sgsave`-Struktur
- bis zu 10 manuelle Slots
- Autosave
- Pflichtsave bei Gebietswechsel
- Recovery-Save
- Save-Versionierung
- Migration
- Events, Weltzustände, Quests, Basis, Inventar, NPCs und Progression vollständig speichern
- Laden nach Absturz / fehlerhaften Saves robust behandeln

### 11. Händler / Economy / Shop
- Händlerdaten
- Kauf / Verkauf
- Preise
- Freischaltungen
- Währungen / Tauschsystem
- Shop-System
- Balancing und Persistenz

### 12. Begleiter / NPC-KI
- Begleiter-DBs erstellen
- Begleiter freischalten
- aktiver Begleiter
- Siedlungsbegleiter
- Passive Hilfe
- Lagerberechtigungen
- autonome Aufgaben
- Rückkehrzeiten
- Fehler-/Hängerzustände
- Skillverwaltung
- Hunde als getrenntes Begleitersystem

### 13. Fahrzeuge / Weltreise
- Fahrzeugfreischaltungen
- Fahrzeugzustand
- Fahrzeuglager
- Geschwindigkeit / Reise
- Reparatur
- Kraftstoff bzw. vorgesehene Ressourcenlogik
- Weltkartenintegration
- spätere Luftfahrzeuge getrennt behandeln

### 14. Zeit / Events / Offline
- zentrale Ingame-Uhr
- 6 Echtzeitstunden = 24 Ingame-Stunden als Standard
- Horde alle 24 Ingame-Stunden
- Warnung 2 Ingame-Stunden vorher
- tägliche Login-Belohnungen
- 30-Tage-Kalender
- temporäre Events
- Offline-Fortschritt nur für erlaubte Systeme

### 15. Funktions- und Integrationstests
- alle 30 Standardmaps betreten und verlassen
- sämtliche `Prefab_MapBoundsAndExits` prüfen
- Runterfallschutz nach Abschluss unsichtbar schalten, Collider aktiv lassen
- EventMap in mehreren Größen testen
- Szenenwechsel mehrfach hintereinander testen
- Save/Load über alle wichtigen Systemzustände testen
- keine verlorenen Referenzen in Prefabs / Inspector
- keine DB-IDs ohne gültige Referenz
- keine Blocker, durch die ein Spielstand nicht weitergespielt werden kann

## Nächste Arbeitsschritte

1. Erfolgreichen EventMap-Prototypen nicht weiter unnötig umbauen.
2. Testevent-Datenstruktur in eine echte Event-ID-/Eventdaten-Pipeline überführen.
3. `events.json.db` an den Eventmanager anbinden.
4. Danach Gegner-, Ressourcen- und Loot-Spawns für Events anbinden.
5. Anschließend die offenen Pflichtsysteme in der obigen Reihenfolge bis zur funktional vollständig spielbaren Fassung schließen.
