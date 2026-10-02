# Entwicklungsstand

**Stand:** 02.10.2026

## Aktuelle Entwicklungsphase

Der Schwerpunkt liegt weiterhin auf den zwingend erforderlichen Kernsystemen für die erste vollständig spielbare Version. Gleichzeitig werden die Datenstrukturen bereits so vorbereitet, dass spätere Updates neue Inhalte, Gebiete, Systeme und Balancingwerte möglichst ohne größere Umbauten ergänzen können.

Wichtig: Nicht jedes geplante System muss in der ersten vollständig spielbaren Version bereits aktiv sein. Spätere Funktionen dürfen vorbereitet, deaktiviert oder mit **„Kommt bald“** gekennzeichnet werden.

## Entwicklungsgrundsatz für Version 1

Die erste vollständig spielbare Version konzentriert sich auf einen geschlossenen Kern-Gameplay-Loop:

**Vorbereiten -> Reisen -> Sammeln/Kämpfen -> Beute sichern -> Verarbeiten/Bauen -> Fortschritt -> nächstes Gebiet**

Pflichtsysteme werden zuerst vollständig geplant und anschließend technisch umgesetzt. Spätere Großsysteme werden so vorbereitet, dass Updates darauf aufbauen können.

## Datenarchitektur

**C# = Logik und Systeme**  
**.db = Inhalte, Werte, Zuordnungen, Balance und Freischaltungen**

Geplante Datenbereiche:
- Items und Ressourcen
- Rezepte
- Werkbänke und Produktionszeiten
- Lootpools
- Gebietsressourcen
- Gegner und KI-Werte
- Händler
- Fahrzeuge
- Freischaltungen
- Quests und Story
- Events
- Dialoge
- XP- und Levelwerte
- Schwierigkeitsprofile
- Weltkartendaten

Spielstände und Spieldatenbanken bleiben strikt getrennt.

## Item- und Materialstand

Die normale Itemliste wurde auf aktuell **340 Einträge** erweitert.

Neue bzw. neu eingeordnete Einträge ab ID 327:
- 327 Eisenerz
- 328 Lithiumrohstoff
- 329 Lithium
- 330 Bleibatterie
- 331 Lithiumbatterie
- 332 Chlor
- 333 Salpetersäure
- 334 Industriereiniger
- 335 Dekontaminationsmittel
- 336 Verseuchte Kiste
- 337 Gereinigte Kiste
- 338 Panzerglas
- 339 Antriebsmodul
- 340 Prototypenmodul

Wichtige Bereinigungsregeln:
- Spezialwaffe bleibt nur Kategorie, kein allgemeines konkretes Item
- Maschinenrahmen bleibt gestrichen
- Getriebebauteil wird als **Antriebsmodul** geführt
- Chemikalien werden als **Allgemeine Chemikalien** geführt
- Metalllogik wird vereinheitlicht zu **Erz -> Metall -> Bauteil**
- unnötige Roh-/Barren-Doppelstufen werden entfernt
- Stahl bleibt ein einziges normales Material; keine zusätzlichen Stahlarten
- Kabel-Grundrezept: **Kupfer + Gummi -> Kabel**
- Panzerglas ist die höchste und extrem stabile Glasstufe; genaue Werte folgen beim Balancing

## Produktions- und Werkbankstand

Die große Stationsbereinigung ist abgeschlossen und die wichtigsten Stationen wurden bereits auf die neue Materiallogik angepasst.

Wichtige Regeln:
- einfache Gegenstände dürfen teilweise direkt hergestellt werden
- komplexe Gegenstände benötigen passende Stationen
- Produktionsketten sollen im Regelfall höchstens etwa 5 Verarbeitungsschritte besitzen
- Eingabeslots von Produktionsstationen: maximal 20 Stück pro Slot
- Produktionsstationen erhalten interne 10-Slot-Lager
- Produktionswarteschlangen unterstützen Reihenfolge, Pause, Löschen und mehrere Durchläufe
- fehlende Materialien pausieren Aufträge
- Offline-Produktion ist vorgesehen
- Stationslevel erhöhen nicht das 20er-Eingabelimit, können aber Rezepte, Tempo, Ausbeute und Effizienz verbessern

Bereits überarbeitet wurden unter anderem:
- Sägewerk
- Steinbearbeitung
- Metallwerkbank
- Schmelzofen
- Schmiede
- Bauwerkbank
- Betonmischer
- Glaswerkbank
- Werkzeugwerkbank
- Waffenwerkstatt
- Rüstungswerkbank
- Reparaturstation
- Schneiderei
- Elektronikwerkbank
- Batteriewerkbank
- Elektrostation
- Generatorwerkstatt
- Kochstation
- Metzger
- Landwirtschaftsstation
- Wasserwerk
- Medizinische Station
- Chemielabor
- Apotheke
- Recyclingstation
- Ölraffinerie
- Fahrzeugwerkstatt
- Maschinenwerkstatt
- Fallenwerkbank
- Forschungsstation
- High-End-Forschung
- Prototypenbereich
- Brecheranlage
- Hochtemperatur-/Gießereibereich
- Webstuhl
- Mühle
- Destillieranlage
- Funk-/Kommunikationsstation
- Strahlenschutzstation
- Gewächshaus
- Uranverarbeitung
- Dekontaminationsbecken

## Survival- und Statussysteme

Aktueller Plan:
- Leben 100/100
- Hunger 100/100
- Durst 100/100
- Temperatur gebietsabhängig ungefähr -40 °C bis +40 °C
- Strahlung als eigener Belastungswert
- Infektion als eigener Belastungswert
- Geruch beeinflusst bei passenden Gegnern die Erkennungsreichweite
- normale Dusche entfernt Geruch/Schmutz
- Dekontaminationsdusche entfernt die dafür vorgesehenen negativen Umwelt-/Kontaminationseffekte
- Kleidung und Spezialausrüstung können Belastungen reduzieren oder vollständig ausgleichen
- Grundwerte fallen nicht unter 0; negative Werte gibt es nur bei ausdrücklich vorgesehenen Effekten

## Tod und Leichen

Festgelegt:
- komplettes Inventar einschließlich Main Hand und Second Hand geht beim Tod grundsätzlich in die Leiche
- Rückholzeit: 2 Stunden aktive Spielzeit
- Timer pausiert bei geschlossenem Spiel
- Leiche verschwindet sofort, wenn sie vollständig geleert wurde
- maximal 3 Leichen gleichzeitig
- Kartenmarker für Leichen

Sonderregel für abgelaufene Eventgebiete:
- befindet sich der Spieler noch im Eventgebiet, darf er dort bleiben, auch wenn der Eventtimer abgelaufen ist
- stirbt er danach und das Gebiet wäre nicht mehr erneut erreichbar, behält er sein komplettes Inventar
- sollte durch einen Fehler dennoch ein unerreichbarer Inventarverlust entstehen, ist vollständige Wiederherstellung plus zusätzliche Entschädigung aus einem Selten-/Episch-/Legendär-Pool vorgesehen

Leitregel: **Das Spiel darf schwierig sein, aber nicht unfair.**

## Weltkarte

Die Weltkarte wurde als eigener Pflichtblock vorbereitet.

Version-1-Gebiete:
- Basis
- Kiefernwald
- Steinbruch
- Eisenmine
- Kohlemine
- Stadt-Ruinen
- Sumpfgebiet
- Hafen
- Bunker A
- mindestens ein temporäres Eventgebiet

Geplant sind weiterhin ungefähr 30 dauerhafte Hauptgebiete; temporäre Events zählen nicht dazu.

Gebietsdaten enthalten unter anderem:
- Name
- Gebietstyp
- Schwierigkeit
- Hauptressourcen
- mögliche Beute
- besondere Gefahren
- empfohlene Ausrüstung
- Reisezeit
- Freischaltbedingungen
- permanent/temporär
- Eventdauer
- erforderliche Spielversion

Weltkarten-Infopanel:
- Gebietsname
- Schwierigkeit
- Vorschaubild
- Hauptressourcen
- mögliche Beute
- besondere Gefahren
- empfohlene Ausrüstung
- Reisezeit
- Betreten

Die Anzeige orientiert sich am nützlichen Grundprinzip bekannter Survival-Weltkarten, erhält aber eine eigene Optik, eigene Gebiete und eigene Regeln.

## KI-System

KI ist ein Pflichtsystem für Version 1.

Gemeinsame Grundlage für:
- Gegner
- Tiere
- NPCs
- Begleiter

Mindestens vorgesehen:
- Warten/Idle
- Umherlaufen
- Verfolgen
- Angreifen
- Fliehen
- Folgen
- Arbeiten
- Bewachen
- Wahrnehmung über Sicht, Geräusch und später Geruch
- NavMesh/Wegfindung
- Freund-/Feind- bzw. Fraktionslogik
- Festhänge-Recovery
- Performance-Abstufung für entfernte KI
- Speicherung wichtiger NPC-Zustände

Dialoge und Sprachausgabe kommen später.

## Kampf, Rüstung und Resistenz

Erster Systementwurf steht.

Schadensarten:
- Physisch
- Ballistisch
- Explosiv
- Feuer
- Kälte
- Elektro
- Gift/Chemisch
- Strahlung
- Infektion

Ausrüstung:
- Polizei = einfache Schutzstufe
- SWAT = stärkere Schutzstufe
- Spezialkleidung für Kälte, Strahlung, Sporen/Chemie und spätere High-End-Kombinationen

Rüstung reduziert Schaden; genaue Werte werden später über die .db balanciert.

## XP- und Levelsystem

Aktueller vollständiger Erstentwurf:
- Level 1 bis 100
- nichtlineare XP-Kurve
- ungefähr 4,76 Millionen XP von Level 1 bis 100 nach aktuellem Entwurf
- XP für Kämpfen, Sammeln, Crafting, Bauen, Erkunden, Forschung, Quests, Story und Events
- Hauptstory und Nebenstory werden getrennt bewertet
- Story-XP ist einmalig
- Item-XP wird datengetrieben verwaltet
- XP-Klassen 0 bis 6
- Level-Up-Belohnungen über Forschungspunkte, Münzen, Güterpakete und Meilenstein-Freischaltungen
- Level allein schaltet nicht alles frei; Story, Forschung und andere Bedingungen können zusätzlich erforderlich sein
- Level 100 ist zunächst Maximum; Gesamt-XP kann intern weitergeführt werden

## Loot- und Seltenheitssystem

Seltenheitsstufen:
- Grün = normal
- Blau = selten
- Gelb = episch
- Rot = legendär / höchste normale Seltenheit

Getrennte Lootquellen:
- Weltressourcen
- normale Kisten
- Versorgungskisten
- Technikkisten
- Sicherheits-/Militärkisten
- Spezialkisten
- Gegner
- Bosse
- Bunker
- Events
- Story
- Expeditionen
- Händler

Loot wird beim Erzeugen gespeichert, damit Neuladen keine neue Auswürfelung erzwingt.

## Händler

Der Händler wird als neutraler/friedlicher Sonder-NPC vorbereitet.

Festgelegt:
- pro Erscheinen verlangt er **genau 3 verschiedene Ressourcen**
- die drei Anforderungen bleiben für diesen Aufenthalt gleich
- beim nächsten Erscheinen werden neue Anforderungen bestimmt
- vollständige Lieferung gibt die normale Belohnung
- zusätzlicher Bonus aus eigenem Bonuspool möglich
- eigener Händler-Loot-/Angebotspool
- Händlerposition darf zwischen vorbereiteten Punkten rotieren
- Händlergebiet enthält keine normalen Zombie-/Feindspawns
- einige normale Ressourcen dürfen im Händlergebiet vorkommen
- wenn der Spieler den Händler angreift, wehrt er sich
- Händler greift nur innerhalb seiner Reichweite an
- er stoppt spätestens bei 10 Restleben des Spielers
- Handel/Interaktion bleibt bis zum erneuten Betreten des Gebiets gesperrt
- Händler ist grundsätzlich neutral und kein normaler Kampfgegner

## Eventgebiete

Neue Persistenzregel:
- wenn der Spieler innerhalb eines Eventgebiets offline geht, bleibt er dort gespeichert
- läuft der Eventtimer ab, wird er nicht automatisch entfernt
- beim nächsten Laden bleibt das Gebiet aktiv, solange der Spieler noch darin ist
- Eventgegner dürfen weiterhin angreifen
- erst nach dem Verlassen wird das abgelaufene Eventgebiet entfernt
- stirbt der Spieler nach Ablauf des Timers im nicht mehr erneut betretbaren Eventgebiet, bleibt sein Inventar erhalten

## Bausystem

Grundregeln:
- normales freies Spielerbauen verwendet ein 3x3-Raster
- keine allgemeine Statik-/Traglastsimulation
- Abriss gibt 25 % der Materialien zurück
- normale Bauteile bleiben bestehen, wenn sie gültig platziert wurden

Ausnahme:
**Von uns definierte Spezialgebäude sind so groß, tief und komplex, wie wir es festlegen.**

Beispiele:
- Bunker
- Forschungsanlagen
- Fabriken
- Kraftwerke
- große Siedlungsgebäude

Bei Bunkern befindet sich auf der normalen Ebene der Eingang; der eigentliche Bunker kann sich über mehrere unterirdische Ebenen fortsetzen.

## Speichern / Autosave / Recovery

Geplant:
- 10 manuelle Spielstände
- Autosave: Aus / 5 / 10 / 15 / 30 / 60 Minuten
- Gebiets-/Szenenwechsel speichert immer
- Recovery-Spielstand bei Absturz/Fehler
- Recovery wird beim nächsten Start angeboten, nicht erzwungen
- Save-Slots zeigen mindestens Ort, Datum/Uhrzeit, Spielzeit und Level
- Save-Versionierung und spätere Migration vorgesehen

## Zeit / Offline-Fortschritt

- 24-Stunden-Ingame-Uhr
- Tagesdauer konfigurierbar
- Produktions-, Bau- und geeignete Eventzeiten können offline weiterlaufen
- Leichentimer pausiert offline
- Hunger/Durst werden nicht einfach offline weiter abgesenkt
- zeitabhängige Systeme verwenden zentrale Zeitregeln

## Grafik, Texturen und Audio

Für die erste vollständig spielbare Version zwingend:
- erkennbare und stimmige Grafik
- Boden-, Gebäude-, Objekt- und Itemtexturen
- Modelle für Spieler, Gegner, Tiere, NPCs, Fahrzeuge und Werkbänke
- UI-Grafiken und Weltkartenmarker
- Musik für Menü, Basis, Erkundung und Gefahr/Kampf
- Umgebungsgeräusche
- Oberflächen-Schritte
- grundlegende Effekte

Platzhalter und finale Assets werden getrennt geführt.

## Schwierigkeitsgrad

Für die erste Veröffentlichung ist nur **Normal / Ausgeglichen** aktiv.

Später mögliche Datenstruktur:
- `/Data/Schwierigkeit/leicht.db`
- `/Data/Schwierigkeit/normal.db`
- `/Data/Schwierigkeit/hardcore.db`

Zunächst wird nur `normal.db` benötigt. Weitere Modi werden erst nach echtem Spielerfeedback aktiviert.

## Multiplayer

Multiplayer ist **nicht Teil der ersten Version**, soll aber architektonisch mitgedacht werden.

Später möglich:
- Welt wie im Singleplayer hosten
- Freunde können beitreten
- optional dedizierter Server
- Whitelist/Rechte/Einladungen später

Singleplayer bleibt zuerst vollständig und unabhängig spielbar.

## Update-System

Spätere Richtung:
- ZIP-basierte Updates
- separater Updater
- wichtige Dateien vor Austausch als .bak/.old bzw. in Backup-Struktur sichern
- SHA-256-Prüfung möglich
- Rollback bei Fehler
- keine feste Annahme zur endgültigen Spielgröße
- kleine Updates können nur geänderte .db-/Asset-Dateien liefern
- vorbereitete Funktionen können über Feature-Flags, Abhängigkeiten oder Updates aktiviert werden

## Aktueller technischer Teststand

Bereits technisch geprüft:
- Spielerbewegung
- E-Interaktion
- Ressourcen sammeln/abbauen
- Inventar-Grundfunktion mit Stacks
- Gesundheit und Faustkampf
- Weltkarten-Ausgänge und Szenenwechsel
- zufälliges Ressourcen-Spawning mit Mindestabstand
- Gebäudehüllen und Eltern-/Kind-Struktur
- normale Tür mit E, Scharnier und Öffnung in beide Richtungen
- Lootkiste mit mehreren Loot-Einträgen
- zufällige Lootmengen und prozentuale Chancen
- mehrere Loot-Treffer
- Kiste kann nur einmal gelootet werden
- eigenes Kisten-Mini-Inventar
- einzelne Items nehmen
- Alles nehmen
- Spieler -> Kiste: Mengenübertragung
- Spieler -> Kiste: kompletter ausgewählter Stack mit Alles einlagern
- Stack- und Kapazitätsgrenzen
- geschlossene Kiste blockiert Einlagerung
- geöffnete Kiste erlaubt Einlagerung

Offener Testpunkt:
- beim aktuellen PlayerMovement-Test tritt sporadisch ein Richtungswechsel-/Bewegungsproblem auf; diagonale Bewegung funktioniert grundsätzlich. Der Fehler wird später gezielt weiter geprüft und blockiert die Planung derzeit nicht.

## Aktuelle Priorität

Zuerst werden die zwingenden Kernsysteme vollständig vorbereitet und danach technisch umgesetzt:

1. Spielersteuerung und Interaktion
2. Inventar und Itemsystem
3. KI-Grundsystem
4. Kampf und Schaden
5. Survival-/Statussysteme
6. Tod/Respawn/Leichen
7. Ressourcen und Gebietsmanager
8. Crafting und Produktion
9. Bausystem
10. Weltkarte und Reisen
11. Lootsystem
12. XP-/Levelsystem
13. Speichern/Autosave/Recovery
14. Zeit/Tag-Nacht/Offline
15. UI/HUD
16. Grafik/Texturen/Audio
17. Quest-/Storysystem
18. Händler
19. Eventsystem

Große spätere Systeme wie vollständige Siedlungsverwaltung, High-End-Forschung, Prototypen, große Kraftwerke, komplexe Expeditionen und umfangreiche Dialoge dürfen vorbereitet, aber zunächst deaktiviert sein.
