# Remnants of Tomorrow (RoT)

## Update 23.10.2026 – Neue Datenbankstruktur und Produktionsstationen

Die Datenhaltung für Werkbänke, Öfen und sonstige Produktionsstationen wird zur besseren Übersicht, Wartbarkeit und späteren Erweiterbarkeit neu geordnet. Zwei **zusätzliche JSON-Datenbanken sind geplant**:

- `stations.json.db`: Stammdaten der Produktionsstationen, Eingabeslots, Brennmaterial-Slot und Lager-/Queue-Regeln.
- `burnmaterials.json.db`: Zulässige Brennmaterialien und individuelle Brenndauern. Der geplante Anfangskatalog umfasst Holz, Kohle, Holzkohle, Torf, Pressbrennstoff und Holzspäne.

Die bestehenden `items.json.db` und `recipes.json.db` bleiben erhalten. **Die jeweils benötigte Station bleibt weiterhin im Feld `station` jedes Rezepts eingetragen**; die neue Stationsdatenbank ersetzt diese Zuordnung nicht. Fahrzeugtreibstoff und Brennmaterial für Produktionsstationen sind getrennte Systeme.

**Geplante Regeln der normalen Werkbänke in der Hauptbasis:** keine Stationsausbaustufen; Rezeptfreigabe über Spielerlevel und gegebenenfalls zusätzliche Forschung; feste Produktionswarteschlange für maximal 20 einzelne Aufträge; ein fertiger Gegenstand je Produktionsdurchlauf; Eingabeslots mit höchstens 20 gleichen Gegenständen; eigene Ausgabe mit 10 Slots zu höchstens 50 Stück pro Stapel (individuelle Gegenstände bleiben einzeln). Gleiche Produkte werden automatisch gestapelt. Der Spieler kann fertige Waren freiwillig entnehmen, aber nicht selbst in die Ausgabe einlagern. Produktionsmaterialien dürfen nur in dafür vorgesehene Eingabeslots. Das Spielerinventar muss für eine laufende Produktion nicht frei sein; bei voller Stationsausgabe wartet ein fertiger Auftrag auf Lagerplatz.

Wenn eine Station Brennmaterial benötigt, liegt der Brennmaterial-Slot bei zwei Eingabeslots unten und bei größeren Anordnungen unten links. Nicht jedes Rezept benötigt Brennmaterial. Bereits aktivierte Brenndauer bleibt erhalten und wird auch bei leerem Brennmaterial-Slot genutzt; fehlt danach neuer Brennstoff, wird der Produktionsfortschritt ohne Verlust angehalten. Die sechs Brenndauern (Holz 60 s, Kohle 180 s, Holzkohle 120 s, Torf 90 s, Pressbrennstoff 240 s, Holzspäne 30 s) dienen vorerst als **Balancing-Planungswerte**, nicht als getestete Implementierung. Produktion und Brenntimer laufen nicht weiter, wenn das Spiel vollständig geschlossen ist.

**Siedlung:** Separates, bereits geplantes Gebäudesystem mit bis zu drei Ausbaustufen; dessen Regeln werden nicht ungeprüft durch die festen Hauptbasis-Werte ersetzt.

**Status:** Dieser Eintrag beschreibt den aktuellen **Planungsstand**. Die neuen Datenbankdateien, die Umstellung der bestehenden Crafting-Skripte, die endgültige Rezeptabstimmung und die Unity-Integration sind **noch nicht umgesetzt oder erfolgreich getestet**. Interne Projektdateien und vollständige lokale Datenbanken werden durch dieses Dokumentationsupdate nicht veröffentlicht.


## Update 19.10.2026 – 25 Eventkonzepte und lokale Eventdatenbanken vorbereitet

**Neuer Planungs- und Datenstand:** Für **25 größere Events** liegen bestätigte Konzepte sowie lokal vorbereitete, getrennte Eventdatenbanken vor. Ein zentraler `event_index.json.db` ordnet die Eventdateien zu. Die Dateien tragen Namen nach dem Muster `event_1_beispielname.json.db`; die Endung `.json.db` bezeichnet weiterhin **JSON-Inhalte, keine SQL-Datenbank**. Die detaillierten Eventplanungen, Inhalte und internen Datenbankdateien bleiben außerhalb des öffentlichen Repositories.

**Spielstatus:** Das Vorliegen der Datenbanken ist **kein Nachweis einer fertigen oder in Unity erfolgreich eingelesenen Eventfunktion**. Die Verbindung zu Eventmanager, Quest-/Belohnungslogik, Weltkarte, Speichersystem und Oberflächen sowie Integrationstests stehen noch aus. Käufe und Verkäufe vergeben grundsätzlich **keine XP**. Grafik, Modelle und endgültige Shopgestaltung folgen in einer späteren Phase.

Die älteren, datierten Angaben in diesem Repository zu sieben Einträgen in `events.json.db` beschreiben einen **früheren Prototypstand** und nicht diese neue Sammlung der 25 großen Eventdatenbanken. Einzelne kurzfristige Zufalls-/Mini-Events werden getrennt von den großen Eventkonzepten betrachtet.

**Datenschutz der Planung:** Dieses Update veröffentlicht nur einen spoilerarmen Fortschrittsstand; keine internen Missionstexte, versteckten Inhalte, einzelnen Shopangebote, Preislisten, kryptografischen Schlüssel oder lokalen Unity-Projektdateien.



## Update 14.10.2026 – Computersystem und GEAM OS: Planungsstand gesichert

Die umfangreichen verbindlichen Festlegungen zum PC-System, zu Hardware, Reparaturen, Diagnose, GEAM OS, Installation, Programmmedien, Programmkiste und zur Flugdatenschreiberanalyse stehen jetzt gesammelt in [Computer- und GEAM-OS-Planungsstand](docs/Remnants_of_Tomorrow_Computersystem_Planungsstand.txt). Die Spielcomputer verwenden GEAM OS, inklusive Versionsupgrades, Mehrfachstart, Wiederherstellung und Rettungsmedien. Die Analyse erfolgt auf einem PC mit zuvor gefundenem/installiertem Programm, NICHT an einer separaten Analysestation. **Ausschließlich Planung; keine neue Unity-Implementierung oder DB-Migration erfolgt.**


## Update 14.10.2026 – Eventplanung in Systemregeln und Einzel-Events getrennt

Die weitere Eventplanung ist jetzt in **zwei getrennten Dokumenten** nachvollziehbar: [Allgemeine Eventregeln](docs/Remnants_of_Tomorrow_Eventsystem_Regeln_Planungsstand.txt) · [Einzelplanung der Events](docs/Remnants_of_Tomorrow_Events_Einzelplanung.txt).

**Übergreifende Regeln:** Höchstens 1 normales Zufalls-Event sowie unabhängig davon höchstens 2 temporäre Mini-Events; Basis-Horden, Kalender- und Saisonereignisse belegen diese Plätze nicht. Neue Zufalls-Events entstehen nur im geöffneten Spiel, laufende Eventtimer laufen auch offline. Zwischen zwei Starts temporärer Mini-Events liegen mindestens 24 Ingame-Stunden. Die bestehende dynamische EventMap und ihr gelber rotierender Sternmarker bleiben erhalten. Temporäre Eventgebiete enthalten Gegner; normale Events bleiben außerhalb ausdrücklich definierter Kampfbereiche friedlich. Eventbeute und Gegnerzustände werden pro Instanz nur einmal erzeugt und persistiert. Abgelaufene Gebiete bleiben bis zum Verlassen bestehen, wenn der Spieler noch darin ist; nach Tod im Event schützt die besondere Rückgaberegel verloren gegangene Gegenstände vor endgültigem Verlust durch das Verschwinden des Gebiets.

**Einzel-Events:** Die vorhandene Datenbank V2 enthält 7 Eventeinträge; „Zerstörter Konvoi“ ist als achter Typ geplant, aber **noch nicht in die DB eingetragen**. Für ihn sind 6 Kisten und insgesamt mindestens 6 seltene Gegenstände (nur Normal/Selten) festgelegt. Flugzeugabsturz und Konvoi sind ab Level 1 möglich und auf höchstens 60 Minuten begrenzt. Weitere Eventlevel (Rahmen Level 10–20), Gegnerzahlen, Wahrscheinlichkeiten und Saisonabläufe bleiben teils offen.

**Technischer Status:** Dies ist eine **Planungsaktualisierung**, keine neue Unity-Funktionsprüfung und keine Änderung an `events.json.db`. Spätere Eventwerte werden vollständig datenbankgesteuert. Grafik, Audio und Modelle folgen am Ende.

## Update 14.10.2026 – Hauptspiel: Entwicklungsstand und offene Kernsysteme

**Stand der Hauptspielentwicklung:** Remnants of Tomorrow bleibt in aktiver Entwicklung. Die vorhandenen Unity-Grundlagen (Spieler/Kamera, Weltkarte und Gebietswechsel, Ressourcen- und Inventarprototypen, Fahrzeug-/Tankstellenprototyp, Speichern/Laden sowie Basis-Hordentests) sind keine Bestätigung eines bereits vollständig spielbaren Hauptspiels. Die zuvor dokumentierten konkreten Unity-Tests bleiben unverändert gültig.

**Nächstes technisches Gesamtziel:** Ein zusammenhängender Spielablauf von der Hauptbasis in den grünen Kiefernwald, dort Ressourcen sammeln und Gegner bekämpfen, zurückkehren, Materialien verarbeiten beziehungsweise etwas bauen und den gesamten Fortschritt anschließend sicher speichern und laden. Dieser vollständige Ablauf ist **noch nicht als durchgängig bestanden bestätigt**.

**Weiterhin offen oder unvollständig:** XP/Level und Freischaltungen; Inventar, Ausrüstung und Lager; Ressourcenabbau und Loot; Crafting mit Werkbänken und Produktionszeiten; rasterbasierter Basisbau samt Ausbaustufen; Gegner/Kampf; Hordenautomatik und Bauschaden; Hunger, Durst und Gebietseinflüsse; Reisen und Storyfreischaltungen; verbleibende Fahrzeug-/Tankstellenregeln; Quests und Story; Begleiter, Siedlung und weitere Regionen; vollständige Save-/Load-Integration.

**Eventsystem als eigenständiger großer Pflichtbereich:** Die gemeinsame dynamische `EventMap` und mehrere temporäre Testmarker wurden bereits erprobt. `events.json.db` enthält derzeit 7 Einträge: drei mit bekannten Grundregeln (Flugzeugabsturz, „Gleich eins aufs Maul“, Basis-Horde) und vier bislang nicht fertig ausgearbeitete Kalender-/Saisonideen. Es fehlen eine vollständige Eventdefinition (Arten, Startbedingungen/Zufall, Häufigkeit, Laufzeit, Ablauf und Ziele, Gegner/Loot, Belohnungen, Wiederholbarkeit, Schwierigkeit), die produktive Anbindung an die Eventdatenbank sowie persistente Zeit-, Weltkarten- und Speicherzustände. Die Datenbankeinträge und EventMap-Tests sind **kein Nachweis eines fertigen Eventsystems**.

**Verbindliche Entwicklungsreihenfolge:** Erst sämtliche Spielmechaniken und ihre technischen Verbindungen fertigstellen und testen. **Audio, endgültige Modelle, Texturen, Animationen, Effekte und grafische Gestaltung kommen ganz am Ende.** Bis dahin reichen vorhandene funktionale Testanzeigen und Platzhalter; keine zusätzlichen grafischen Provisorien erzwingen. Die bisherige engere Arbeitsplanung aus dem Fahrzeugblock beschreibt einen älteren Zwischenstand und schränkt diese Gesamt-Roadmap nicht ein.

Dieses Update aktualisiert ausschließlich die öffentliche Projektdokumentation; es lädt keinen lokalen Unity-Quellcode hoch.

Öffentlicher Entwicklungsstand, Roadmap und Ideensammlung für das Survival-Game-Projekt.

## Update 13.10.2026 – Basis-Horden: Angriffe und Spielstandtests

**Lokal in Unity 2017.2.5f1 bestätigt:** Ein eigenständiges Basis-Hordensystem erzeugt Gegnergruppen mit zufälliger Hordenstufe und Angriffsrichtung. Die festgelegten Gruppengrößen sind 10, 25 oder 50 Gegner; Testdurchläufe mit 10 und 25 Gegnern funktionierten. Abschüsse verringern den Restzähler; nach dem letzten Abschuss endet der Angriff. Stirbt der Spieler während einer Horde, wird diese sofort beendet und ihre übrigen Gegner werden entfernt. Das normale Gebietsspawnsystem bleibt getrennt.

**F5/F11 bestätigt:** Sowohl eine vollständige Horde als auch der Restbestand einer teilweise besiegten Horde wurden wiederhergestellt. Konkreter Test: **10 → 8 (F5) → 5 → 8 (F11)**. Die lokale Spielstandstruktur ist inzwischen **Version 9**; die vorhandene `.rotsave`-/`.sgsave`-Verarbeitung mit **AES-256-CBC und HMAC-SHA256** bleibt bestehen.

**Abgrenzung:** Die exakte Wiederherstellung individueller Gegner-Lebenspunkte und -Positionen, Szenenwechsel während aktiver Angriffe, die automatische Zeitsteuerung mit Warnung und Angriffe auf echte Basisbauteile sind noch nicht separat getestet. Unterschiedliche Gegnerklassen und Bauschaden sind noch nicht fertig integriert. Die Ergebnisse belegen einen getesteten Prototyp, kein vollständig abgeschlossenes Basis-/Hordensystem.

Dieses GitHub-Update dokumentiert den lokalen Entwicklungsstand; es veröffentlicht keine lokalen Unity-C#-Dateien.

## Dokumentationsabgleich 13.10.2026 – Datenbanken und Spielstände

- **Gegnerdaten:** Die vorhandene `enemies.json.db` enthält **53 Gegnereinträge**. Nicht alle Gegnertypen sind damit bereits als vollständige Unity-Gegner samt Modellen und KI eingebunden.
- **Eventdaten:** Die vorhandene `events.json.db` enthält **7 Einträge**. Drei besitzen bestätigte Grundregeln (Flugzeugabsturz, Nahkampf-Event und Basis-Horde); vier Kalender-/Saisonereignisse sind noch nicht abschließend definierte Ideen. Datenbankeinträge bedeuten keine fertige Laufzeitumsetzung.
- **Speicherregeln:** `.rotsave` ist das primäre Spielstandformat, `.sgsave` die Reserve. Für die Planung gelten **maximal 5 manuelle Speicherslots**. Die lokal verwendete Spielstandstruktur steht bei **Version 9**; die vorhandene AES-256-CBC-/HMAC-SHA256-Verarbeitung bleibt bestehen. Die Fertigstellung aller Speicherfunktionen ist damit noch nicht bestätigt.

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
