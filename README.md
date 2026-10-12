# Remnants of Tomorrow (RoT)

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

## Update 13.10.2026 – Basis-Horden: Angriffe und Spielstandtests

**Lokal in Unity 2017.2.5f1 bestätigt:** Ein eigenständiges Basis-Hordensystem erzeugt Gegnergruppen mit zufälliger Hordenstufe und Angriffsrichtung. Die festgelegten Gruppengrößen sind 10, 25 oder 50 Gegner; Testdurchläufe mit 10 und 25 Gegnern funktionierten. Abschüsse verringern den Restzähler; nach dem letzten Abschuss endet der Angriff. Stirbt der Spieler während einer Horde, wird diese sofort beendet und ihre übrigen Gegner werden entfernt. Das normale Gebietsspawnsystem bleibt getrennt.

**F5/F11 bestätigt:** Sowohl eine vollständige Horde als auch der Restbestand einer teilweise besiegten Horde wurden wiederhergestellt. Konkreter Test: **10 → 8 (F5) → 5 → 8 (F11)**. Die lokale Spielstandstruktur ist inzwischen **Version 9**; die vorhandene `.rotsave`-/`.sgsave`-Verarbeitung mit **AES-256-CBC und HMAC-SHA256** bleibt bestehen.

**Abgrenzung:** Die exakte Wiederherstellung individueller Gegner-Lebenspunkte und -Positionen, Szenenwechsel während aktiver Angriffe, die automatische Zeitsteuerung mit Warnung und Angriffe auf echte Basisbauteile sind noch nicht separat getestet. Unterschiedliche Gegnerklassen und Bauschaden sind noch nicht fertig integriert. Die Ergebnisse belegen einen getesteten Prototyp, kein vollständig abgeschlossenes Basis-/Hordensystem.

Dieses GitHub-Update dokumentiert den lokalen Entwicklungsstand; es veröffentlicht keine lokalen Unity-C#-Dateien.

## Update 12.10.2026 – Test-Jeep: Fahrzeugschaden, Reparatur und verschlüsselter Spielstand

**Bestätigte Unity-Tests (2017.2.5f1), ausschließlich am vorhandenen Test-Jeep:**

- **Kollisionsschaden:** Aufpralle reduzieren die Haltbarkeit tatsächlich; die Unity-Console protokolliert die abgezogenen Schadenspunkte.
- **Fahrzeug-HUD:** `VehicleStatusHUD.cs` liest beim nicht aufgebauten Test-Jeep jetzt den tatsächlichen Wert aus `VehicleFuelRuntime.TryGetTestJeepDurability()`. Der Zahlenwert und der grüne Balken wurden im Spiel korrekt aktualisiert (beispielsweise **266/300** statt fälschlich 300/300).
- **Fahrsperre:** Bei **höchstens 10 %** Resthaltbarkeit (Jeep: **30/300 oder weniger**) ist der Jeep nicht mehr fahrbereit; das wurde im Test bestätigt.
- **Testreparatur:** Die Wiederherstellung der Jeep-Haltbarkeit wurde erfolgreich getestet. Sie ist nicht mit dem vollständigen, materialabhängigen Reparatursystem gleichzusetzen.
- **Simulierte Feldreparatur:** `TestJeepWorkshopSimulator.cs` benötigt **kein** Szenen-/Werkstatt-Testobjekt; mit **K** wird am stehenden Jeep eine provisorische Reparaturbedienung geöffnet. Eine laufende Reparatur mit Restzeit und Fortschrittsbalken wurde im Editor sichtbar bestätigt. **Materialabzug, regulärer Reparaturabschluss und persistenter Reparaturfortschritt sind noch nicht gesondert als bestanden bestätigt.**
- **Spielstände:** Beschädigte Jeep-Haltbarkeit wurde per **F5** gespeichert und per **F11** sowie nach vollständigem Neustart wiederhergestellt. Die aktuelle **Spielstandversion 8** nutzt `.rotsave` mit **AES-256-CBC und HMAC-SHA256**; `.sgsave` bleibt Reserve. Die vorhandene Verschlüsselungs- und Integritätslogik wurde für diese Tests nicht umgebaut.

**Verbindliche Reparatur-/Montageregel:** Reparaturen bei **1–99 %** sind auch **unterwegs** am stehenden Fahrzeug mit Werkzeug, Material und ausdrücklicher Bestätigung erlaubt – **ohne Minispiel**. **0 %** erfordert die Generalreparatur in der Hauptbasis-Werkstatt. Ein **Montage-Minispiel** ist nur für den erstmaligen Wiederaufbau geborgener Fahrzeugwracks vorgesehen. Die spätere Fahrzeugwerkstatt darf der Spieler **selbst platzieren**.

**Aktualisierte Arbeitsreihenfolge (12.10.2026):** Aktuell ausschließlich (1) die bestehende Fahrzeugreparatur am Test-Jeep technisch vervollständigen und (2) konkret fehlende Verbindungen zwischen vorhandener Treibstoff-/Lager-/Speicherlogik prüfen. Frei platzierbare Gebäude/Werkstatt-Bau, Fahrzeugbergung/Erstaufbau/Montage-Minispiel sowie andere Spielsysteme wie Gegner, Crafting, Story und Events werden nicht jetzt begonnen; dafür werden später die passenden Grafiken/Modelle und Spielobjekte benötigt. Bis dahin keine neuen provisorischen Gebäudesysteme, Fahrzeugmodelle oder unnötigen doppelten Testobjekte.  **Grafiken, 3D-Modelle, Animationen, visuelle Gestaltung und endgültige Benutzeroberflächen erst ganz am Ende.** Die anderen sieben Fahrzeugmodelle und ihre individuellen Fahrtests werden bis dahin nicht mit zusätzlichen Provisorien erzwungen. Das vorhandene Ressourcen-Spawnsystem (`AreaSpawnManager`) bleibt bestehen.

Details und offene Arbeiten: [FORTSCHRITT.md](FORTSCHRITT.md) und [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md). Die Änderungen auf GitHub dokumentieren den lokal getesteten Stand; sie laden nicht automatisch Unity-C#-Dateien hoch.

## Update 11.10.2026 – Fahrzeugreise und Tanksystem (in Unity getestet)

**Remnants of Tomorrow befindet sich weiter in der Entwicklung.** Die letzten Tests mit Unity 2017.2.5f1 haben den Jeep-Prototyp, die Fahrzeugreise und das Tanksystem deutlich vorangebracht:

- **Weltkartenreisen:** 30 permanente Gebietsmarker und ein vorläufiges Netz aus 40 Verbindungen; der Jeep fährt entlang berechneter Routenknoten. Die Fahrt zum Hafen, Ankunft mit Fahrzeug und erneutes Verlassen des Gebiets wurden getestet. Wasserwege zur Insel sind für den Jeep gesperrt.
- **Treibstoff:** Jeep-Tank mit 180 Punkten; 8 Punkte je angefangenem Fahrzeitblock von 150 Sekunden *aktiver* Fahrt. Beim Stillstand bleibt die bereits bezahlte Zeit erhalten; ohne ausreichenden Treibstoff und ohne Restfahrzeit ist kein weiterer Antrieb möglich.
- **Tankstellen:** Zwei getrennte Vorräte für Hauptbasis und Siedlung (je 50.000 Punkte normal, 50.100 absolut). Manuelles Nachfüllen aus dem lokalen Vorrat sowie automatisches Betanken eines geparkten Jeeps wurden erfolgreich geprüft.
- **Mindestreserve:** Automatische Entnahme respektiert die geschützte Reserve; die Freigabe einer manuellen Entnahme unter die Reserve wurde im isolierten Test erfolgreich geprüft.
- **Spielstände:** `.rotsave` speichert Jeep-Tank, bezahlte Restfahrzeit, Tankstellenvorräte, Mindestreserven und die getrennten Ein-/Aus-Einstellungen der Automatik. F5, F11 und die Wiederherstellung nach Neustart des Unity-Play-Modus wurden geprüft.

**Abgrenzung:** Dies sind getestete **Prototypfunktionen**, keine fertige Fahrzeug-/Tankstellenimplementierung für alle acht Fahrzeuge. Die Fahrstrecken verbinden vorerst Gebietsmarker geradlinig; exakte Straßen- und Brückenverläufe, Betankung aus Fahrzeuglagern, Inventar-/Item-Anbindung, fertige Tankstellen-GUIs und Grafik fehlen noch. Dieser Abschnitt dokumentiert den älteren Teststand vom 11.10.; inzwischen ist **AES-256-CBC mit HMAC-SHA256** für die `.rotsave`-Spielstände (Version 8) integriert und erfolgreich verwendet worden. Der Quellcode dieses lokalen Unity-Prototyps wird durch die Dokumentationsaktualisierung nicht automatisch auf GitHub veröffentlicht.

## Aktueller Stand

Den ausführlichen Entwicklungsstand findest du hier:

- [ENTWICKLUNGSSTAND.md](ENTWICKLUNGSSTAND.md)
- [FORTSCHRITT.md](FORTSCHRITT.md) – kompakte Arbeitsübersicht und Pflichtpunkte bis zur vollständig spielbaren Fassung
- [IDEEN.md](IDEEN.md) – spätere Ideen und optionale Erweiterungen

## Aktueller Schwerpunkt

Aktuell steht die **schrittweise Fertigstellung der Spielsysteme** im Vordergrund, insbesondere der datenbankgesteuerten Fahrzeug- und Tankstellenmechanik. Der endgültige Build-/Installertest folgt erst in der Abschlussphase.

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

## Nächster Entwicklungsblock (ab 11.10.2026)

1. **Fahrzeuglager-Treibstoffquelle vorbereiten:** pro Fahrzeug ausdrücklich freigebbar; bei Abwesenheit des Spielers nur lokaler Tankstellenvorrat und gegebenenfalls freigegebenes Fahrzeuglager, niemals das Spielerinventar.
2. **Weltkarten-Fahrten abrechnen:** die Fahrzeit bzw. die zurückgelegte Route korrekt in den Tankverbrauch einbeziehen, ohne die bewährte Verbrauchslogik zu verändern.
3. **Tankstellenregeln vervollständigen:** Standort-/Näheprüfung, weitere Fahrzeuge, Vorratswarnstufen, konfigurierbare Schwellenwerte und Weltkartenanzeige.
4. **Spielstandschutz:** AES-256-CBC und HMAC-SHA256 unter Unity 2017.2.5f1 getrennt testen und erst danach in `.rotsave` integrieren; bestehende Spielstände dürfen nicht verloren gehen.
5. **Weitere Pflichtsysteme:** Events, Gegner, Loot, Crafting, Basisbau, Story, Skills, Begleiter und alle übrigen Kernmechaniken schrittweise integrieren.
6. **Abschlussphase:** Gegenstände aus der Item-Datenbank, Modelle, Grafik, Audio sowie GUIs anbinden bzw. nur dort überarbeiten, wo es nötig ist. Vollständiger Kompatibilitäts-/Installertest erst zum Abschluss; Windows 7 SP1 ist verbindlich, Windows XP SP3 ist ein optionaler zusätzlicher Härtetest.

Die bisherigen Schätzungen des ersten Testbuilds sind ältere Planungswerte, **keine** aktuelle Aussage, das fertige Spiel sei nahezu abgeschlossen. Neue Windows-Builds und Installer werden nicht allein wegen dieses Dokumentationsupdates erstellt.

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
