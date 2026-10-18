# Projektfortschritt

## Update 19.10.2026 – 25 Eventdatenbanken lokal vorbereitet

| Bereich | Stand / nächste Aufgabe |
|---|---|
| Große Eventkonzepte | **25 von 25** geplanten Events konzeptionell festgelegt |
| Lokale Eventdatenbanken | **25 separate `.json.db`-Dateien** und ein `event_index.json.db` vorhanden |
| Dateiformat | Reines JSON mit der Endung `.json.db`, keine SQL-Datenbank |
| Übertragung der Planung | Definitionen aus den internen TXT-Planungen in JSON-Strukturen überführt und ergänzt; die individuelle Spielbarkeit ist noch nicht geprüft |
| Original- und Sicherungsdateien | Vorhandene `.BAK`-/`.1BAK`-Sicherungen dürfen erhalten bleiben; der zukünftige Loader muss aktive Datenbankfassungen eindeutig auswählen |
| Eventshops | Datenseitig vorbereitet; **Käufe/Verkäufe geben keine XP**; grafische Ausarbeitung bleibt später |
| Unity-Integration | **Offen:** Lese- und Kompatibilitätstests unter Unity 2017.2.5f1, Loader, Eventmanager, Quest-Auslöser, Weltkarten-/Eventsteuerung, Belohnungsabwicklung |
| Spielerfortschritt | **Offen:** vollständige, zuverlässige Integration von Eventzuständen und Belohnungsstatus in `.rotsave` |
| Grafik-/Abschlussphase | Modelle, Audio, Animationen, visuelle Effekte und endgültige Shopoberflächen folgen später |

**Abgrenzung:** Gültiges JSON oder eine vorhandene Planungsdatei beweist keine funktionierende Unity-Anbindung. Frühere Einträge mit 7 Eventdatensätzen in `events.json.db` beziehen sich auf den älteren Prototyp und bleiben aus dokumentarischen Gründen im Verlauf erhalten. Temporäre Mini-Events und Basis-Horden haben teils eigene Regeln und sind nicht identisch mit den 25 großen Konzept-Events.

Dieses öffentliche Update enthält **keine internen Event-Datenbanken, geheimen Missionsabläufe, Einzelartikel, Einzelpreise oder Storyspoiler**. Lokale Spielskripte und der bestehende Spielstandschutz wurden für dieses Dokumentationsupdate nicht verändert.



## Update 14.10.2026 – Computersystem / GEAM OS (Planung)

**Detaillierter verbindlicher Planungsstand:** [Computer- und GEAM-OS-Planungsstand](docs/Remnants_of_Tomorrow_Computersystem_Planungsstand.txt). Enthält Hardware-Kompatibilität, PC-Funde/Seltenheiten, Transport und Ausbau, automatische Verkabelung, ausschließlich Luftkühlung, PC-/Laufwerkszustände, GEAM OS und seine Installationen, Software-/Datenträgermanagement, Programmkiste (10/20/30/40/50 Slots, Endstufe unbegrenzt), Installationspausen/Queue/Prioritäten, Wiederherstellung und Rettungsmedien, Reparaturen/Diagnose/Akkus sowie Flugdatenschreiberanalyse am PC (30 Minuten aktive Spielzeit, Queue und Strompausen). **Noch nicht umgesetzt oder vollständig getestet.** Keine neuen konkreten DB-Werte oder C#-Laufzeitfunktionen durch dieses Dokumentationsupdate.


## Update 14.10.2026 – Eventplanung in Systemregeln und Einzel-Events getrennt

**Dokumentation bewusst getrennt:** [Allgemeine Eventregeln](docs/Remnants_of_Tomorrow_Eventsystem_Regeln_Planungsstand.txt) · [Einzelplanung der Events](docs/Remnants_of_Tomorrow_Events_Einzelplanung.txt).

| Bereich | Planungsfortschritt / noch offen |
|---|---|
| Globale Eventplätze | Festgelegt: 1 normales Zufalls-Event plus höchstens 2 temporäre Mini-Events; Horden und Kalender/Saison separat |
| Entstehung und Zeit | Festgelegt: neue Zufalls-Events nur bei geöffnetem Spiel, laufende Timer offline aktiv, 24 Ingame-Stunden Mindestabstand zwischen temporären Starts |
| EventMap | Bereits mit variablen Flächen getestet; vorhandene räumlich getrennte gelbe Sternmarker beibehalten |
| Kampf und Frieden | Festgelegt: temporäre Events stets mit Gegnern; normale EventMap friedlich außer in ausdrücklich vorgesehenen Kampfbereichen |
| Loot und Gegner | Festgelegt: einmalige Instanzbefüllung/-erzeugung; entnommene Beute und besiegte Gegner bleiben weg, noch lebende Gegner und Restbeute bleiben |
| Eventende | Festgelegt: nicht vorzeitig nach Abschluss; Timer maßgeblich, bei Spieleraufenthalt im abgelaufenen Gebiet Entfernung erst nach Verlassen |
| Spielertod | Geplant: eventgebundener Rückgabe-/Verlustschutz bei abgelaufenem, nicht mehr erreichbarem Gebiet; keine Rückgabe beim lebenden Gebietswechsel |
| Einzel-Events | 7 Eventeinträge in DB V2; Konvoi als achter Typ geplant, noch nicht migriert; Konvoi mit 6 Kisten und mindestens 6 seltenen Items |
| Eventbalance | Noch offen: konkrete Gegnerzahlen/Spawns, reguläre Eventlevel 10–20, Zufallswahrscheinlichkeiten, Saisonabläufe |
| Integration | Noch offen: DB-Loader/Eventmanager, persistente Eventinstanzen, Offline-/Tod-/Ladeprüfungen |

**Status: Planungsfortschritt, keine neue Unity-Funktionsbestätigung.** Keine Änderung der lokalen Eventdatenbank oder C#-Skripte. Spielmechaniken vor abschließender Audio-/Grafik-/Modellphase.

## Aktualisierung 14.10.2026 – Offene Hauptspielarbeiten und Eventsystem

**Aktuelle Einordnung:** Das Hauptspiel ist weiterhin in Entwicklung. Einzelne Unity-Prototypen (Weltkarte/Gebiete, Test-Jeep und Treibstoff/Tankstellen, geschützte Spielstände, Basis-Horden) sind überprüft; daraus folgt **noch kein abgeschlossener Gesamt-Gameplay-Ablauf**. Der nächste zusammenhängende Funktionsnachweis soll die Strecke **Hauptbasis → grüner Kiefernwald → Ressourcen und Kampf → Rückkehr → Herstellung/Basisbau → Speichern/Laden** umfassen.

| Bereich | Nach jetzigem Kenntnisstand noch offen |
|---|---|
| Progression | XP-Vergabe, Levelaufstiege, Forschung, Level- und Storyfreischaltungen vollständig integrieren |
| Gegenstände und Gebiete | Inventar, Stacks, Rucksäcke, Lager, Ausrüstung, Ressourcenabbau, Loot und Spawnverteilung verknüpfen |
| Crafting und Bau | Werkbänke, Rezepte, Produktionszeiten, Rasterbau, Upgrades und Abriss spielfähig machen |
| Kampf und Survival | Gegner-/Kampfsystem, Hunger/Durst, Kälte, Strahlung und Infektion vervollständigen |
| Basis-Horden | Automatischer 24-Ingame-Stunden-Rhythmus, 2-Stunden-Warnung, Bauschaden und offene Save-/Load-Fälle |
| Reisen und Fahrzeuge | Gebiets-/Storyfreischaltungen, Reise- und Tanklogik, restliche Fahrzeugtypen und Reparaturabläufe integrieren |
| Langfristige Inhalte | Quest-/Storysystem, zweite Basis, Siedlung, Begleiter, weitere Regionen, Bunker und besondere Events |
| Spielstände | Neue Spielsysteme vollständig in `.rotsave` übernehmen und Wiederherstellung gezielt testen |

**Eventsystem ist ein eigenständiger noch unvollständiger Pflichtbereich.**
- **Vorhanden/getestet:** skalierbare gemeinsame `EventMap`, drei temporäre Testgebiete, dynamische Weltkartenmarker mit stabiler Position.
- **Datenbasis:** `events.json.db` mit **7 Einträgen**; bekannte Grundregeln für Flugzeugabsturz, „Gleich eins aufs Maul“ und Basis-Horde, vier weitere Kalender-/Saisonideen noch offen.
- **Noch zu definieren:** vollständiger Eventkatalog, Kategorien, Auslösebedingungen und Zufallsregeln, Häufigkeit, Zeitlimits, Ziele, Gegner, Belohnungen, Schwierigkeit, Wiederholung und gleichzeitige Ereignisse.
- **Noch umzusetzen/zu testen:** Datenbank-Loader/Manager, Event-ID und Inhalte in der gemeinsamen `EventMap`, Eventmarker und Fortschritt, Ende während Aufenthalt, Pause/Offline, Spielertod sowie Speichern/Laden aller Eventzustände.
- **Schon geplant:** kurzlebige Mini-Eventflächen (Richtwert 30 × 30 Meter; zum Beispiel eine Stunde), hochwertige Beute beim Flugzeugabsturz, eigenständige Eventkennfarbe. Details werden erst im vollständigen Evententwurf verbindlich abgeschlossen.

**Reihenfolge verbindlich:** Zuerst die Logik und sämtliche Gameplay-Systeme, dann technische Integration und Tests. **Audio, endgültige Modelle, Grafik, Texturen, Animationen, Effekte und grafische Verfeinerung erst ganz zum Schluss.** Bereits getestete Skripte und Prototypen nur bei echtem Änderungsbedarf anfassen. Frühere provisorische Arbeitsprioritäten bleiben als historische Einträge erhalten.

**Stand:** 14.10.2026 – aktualisierte Dokumentation, ohne neue Unity-Testergebnisse.

## Aktualisierung 13.10.2026 – Basis-Horden: bestätigte Funktionstests

**Geprüft in Unity 2017.2.5f1:** Eigenständiger Basis-Hordenspawner mit zufälliger Hordenstufe und Richtung. Testhorden mit 10 beziehungsweise 25 Gegnern wurden vollständig erzeugt. Der Restgegnerzähler reagiert auf Abschüsse; das Ende einer besiegten Horde sowie der sofortige Abbruch und das Entfernen verbleibender Gegner bei Spielertod wurden bestätigt. Die normalen Gebietsspawns bleiben unabhängig.

**F5/F11 bestanden:** Die aktive Gegnerzahl einer vollständigen Horde und der Speicherstand einer teilweise besiegten Horde wurden wiederhergestellt. Beispiel: **10 → 8 (F5) → 5 → 8 (F11)**. Lokale Spielstandstruktur **Version 9**; bestehende AES-256-CBC-/HMAC-SHA256-Verarbeitung und die `.rotsave`-/`.sgsave`-Dateien bleiben erhalten.

**Offene Arbeiten:** Prüfung einzelner Gegnerpositionen und Lebenspunkte, Szenenwechsel mit laufender Horde, regulärer Zeit- und Warnablauf, endgültige Gegnerklassen sowie das Angreifen echter Basisbauteile. Der bestätigte Testumfang ist keine fertige Gesamtimplementierung.

## Dokumentationsabgleich 13.10.2026 – Datenbanken und Speichervorgaben

**Referenzdaten:** `enemies.json.db` enthält **53 Gegnereinträge**. In `events.json.db` sind **7 Ereignisse** erfasst; drei haben bestätigte Grundregeln, vier sind noch nicht finalisierte Kalender-/Saisonideen. Die vollständige Laufzeitanbindung bleibt eine offene Aufgabe.

**Spielstände:** Primärformat `.rotsave`, Reserveformat `.sgsave`; **maximal 5 manuelle Speicherslots** sind vorgesehen. Der zuletzt lokal bestätigte Spielstand verwendet **Version 9** und die vorhandene AES-256-CBC-/HMAC-SHA256-Verarbeitung.

## Aktualisierung 12.10.2026 – bestätigte Jeep-Tests und nächste technische Arbeiten

**Tatsächlich am Test-Jeep in Unity 2017.2.5f1 bestätigt:** Kollisionsschaden wird als Haltbarkeitsverlust berechnet; `VehicleStatusHUD.cs` aktualisiert die Jeep-Haltbarkeit korrekt (beispielsweise 266/300); bei maximal 10 % Haltbarkeit ist der Jeep fahruntüchtig; die kostenlose Testreparatur stellt Haltbarkeit wieder her; beschädigte Haltbarkeit bleibt nach **F5/F11 und vollständigem Neustart** erhalten. Dies sind Tests am Jeep, **nicht** an den sieben anderen Fahrzeugtypen.

**Verschlüsselter Speicherstand:** Der aktuelle lokale Spielstand verwendet **Version 8**, `.rotsave` mit **AES-256-CBC + HMAC-SHA256** sowie `.sgsave` als Reserve. Frühere Ausführungen in diesem Dokument zu "Version 6" oder "noch unverschlüsseltem JSON" sind **historisch und inzwischen überholt**. Die AES-/HMAC-Logik blieb während der Jeep-Haltbarkeitsänderung unverändert.

**Reparatur:** Der eigenständige, nur im Unity-Editor verwendete `TestJeepWorkshopSimulator.cs` simuliert Feldreparaturen **ohne platziertes Werkstattobjekt**. Der Nutzer hat eine **laufende zeitgesteuerte Reparatur mit Fortschrittsbalken** gezeigt. Ein vollständig bestätigter Reparaturabschluss **mit echtem Materialabzug** oder dauerhafter Speicherung eines laufenden Reparaturvorgangs liegt noch nicht vor. Die spätere Hauptbasis-Werkstatt ist ein **vom Spieler selbst frei platziertes Gebäude**, nicht eine feste Szenenposition.

**Verbindliche Regeln:** Reparaturen bei **1–99 %** sind auch unterwegs direkt am stehenden Fahrzeug mit physisch anwesendem Spieler, Werkzeug (nicht verbraucht), Materialien und ausdrücklicher Bestätigung möglich; Teilreparaturen proportional mit Aufrundung, **ohne Minispiel**. **0 %** erfordert die vollständige Generalreparatur an der Hauptbasis. Nur der **erstmalige Aufbau von Fahrzeugwracks** benötigt ein Montage-Minispiel; sein Fortschritt soll dauerhaft gespeichert werden.

**Korrigierte nächste technische Schritte – Nutzerentscheidung vom 12.10.2026:**

1. **Nur die technische Fahrzeugreparatur am bestehenden Test-Jeep abschließen:** Materialverbrauch und Prüfung erlaubter Quellen, anteilige Reparaturen, ausdrückliche Bestätigung sowie Unterbrechen/Fortsetzen und später sichere Speicherung des Reparaturfortschritts. Keine neuen Werkstatt-Testobjekte oder grafischen Objekte.
2. **Nur vorhandene technische Fahrzeugsysteme gezielt vervollständigen**, soweit nachweislich nötig: Treibstoff, Fahrzeuglager, Zustandsverwaltung und verschlüsseltes F5/F11. Funktionierende C#-Systeme, Test-Jeep und AES-256-/HMAC-Logik unverändert lassen, wenn keine Änderung erforderlich ist.

**Bis passende Grafiken und Modelle vorhanden sind ausdrücklich zurückgestellt (keine aktuellen Arbeitspakete):**
- Frei platzierbarer Basisbau einschließlich der echten Fahrzeugwerkstatt und weiterer Gebäude: dafür müssten zunächst die Gebäudeinhalte bzw. grafischen Grundlagen vorbereitet werden.
- Fahrzeugbergung, freischaltbarer Erstaufbau und Montage-Minispiel: keine provisorische Umsetzung vor der späteren Asset-/Modellphase.
- Weitere inhaltliche Spielsysteme wie Gegner/Kampf, Werkbänke/Crafting, Story/Quests, Events und Begleiter: für deren praktische Ausarbeitung werden geeignete grafische Spielobjekte benötigt.

**Grafiken, endgültige 3D-Modelle, Animationen, visuelle Effekte und abschließende Benutzeroberflächen kommen erst ganz am Ende.** Bis dahin einfache Platzhalter verwenden und keine mehrfachen Oberflächen- oder Fahrzeugtests erzwingen. Quellcode bei künftigen Änderungen vollständig **direkt im Chat**, Dateien nur auf ausdrücklichen Wunsch. GitHub-Dokumentationsänderungen sind kein automatischer Upload lokaler Unity-Skripte.



**Stand:** 13.10.2026

Diese Datei ist die kompakte Arbeitsübersicht für den aktuellen Projektstand. Sie trennt bestätigte/fertige Systeme von offenen Pflichtpunkten für eine vollständig spielbare Fassung.

## Aktueller Schwerpunkt

**Weiterentwicklung der Fahrzeug- und Tankstellensysteme nach den erfolgreichen Jeep-Tests; danach weitere Pflichtmechaniken.** Der vollständige Windows-Build-/Installertest wird für die Abschlussphase zurückgestellt.

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

## Bestätigter Entwicklungsfortschritt vom 11.10.2026

### Fahrzeug- und Weltkartenreisen – getestet

- `vehicles.json.db`: acht Fahrzeugdatensätze vorbereitet; **der Jeep** wurde tatsächlich im Unity-Editor gefahren und getestet. Die übrigen Fahrzeuge sind noch nicht vollständig implementiert.
- `worldmap_routes.json.db`: 30 feste Routenknoten und 40 Verbindungen als erste, noch zu verfeinernde Geländegraph-Version.
- Die Fahrzeugreise prüft erlaubtes Gelände anhand der Datenbank (`terrainSupport`); Jeep-Fahrt zur Insel über Wasser wird abgelehnt, zum Hafen ist sie erlaubt.
- Das Reisesymbol folgt einer berechneten Folge von Markern statt der direkten Luftlinie zwischen Start und Ziel. Die Teilstrecken zwischen den Markern sind weiterhin gerade und müssen später an Straßen/Brücken angepasst werden.
- Fahrt zur Weltkarte, berechnete Route zum Hafen, Fahrzeugankunft mit Spieler im Jeep sowie erneutes Verlassen des Zielgebiets wurden im Prototyp bestätigt.

### Jeep-Treibstoff und Tankstellen – getestet

- Jeep-Tankkapazität **180 Punkte** und Verbrauch **8 Punkte** pro angefangenem Fahrzeitblock aus der Fahrzeugdatenbank; ein Block entspricht **150 Sekunden aktiver Fahrt**. Bereits bezahlte Restfahrzeit pausiert beim Stillstand; leerer Tank ohne Restzeit sperrt den Antrieb.
- Der separate Testtank und die bezahlte Restfahrzeit sind über `VehicleFuelRuntime` in `.rotsave` integrierbar und mit F5/F11 sowie nach einem Play-Modus-Neustart wiederhergestellt worden.
- Zwei voneinander unabhängige Tankstellen: **Hauptbasis** und **Siedlung**, jeweils **50.000** Punkte Normalvorrat und **50.100** Punkte absolute Obergrenze.
- Manuelle Entnahme aus dem lokalen Vorrat und Auffüllen des Jeep-Tanks wurden erfolgreich geprüft; die Tankstelle verliert nur die tatsächlich eingefüllten Punkte.
- Mindestreserven wurden erfolgreich getestet: automatische Entnahmen greifen nicht darauf zu; manuelle Entnahme unter die Grenze ist nur mit ausdrücklicher Freigabe möglich.
- Die Tankautomatik füllt im jetzigen Test alle **3 Sekunden bis zu 20 Punkte** in den stehenden Jeep nach. Sie ist standardmäßig **AUS** und verwendet bislang ausschließlich den lokalen Tankstellenvorrat.
- `.rotsave` (Save-Struktur **Version 6**) speichert Tankstellenvorräte, Mindestreserven und die getrennten Automatik-Einstellungen. Das Wiedereinlesen nach F11 und nach vollständigem Neustart des Play-Modus wurde bestätigt. Der Fehler durch die zuvor noch verwendete `SaveSystem.cs`-Version 5 wurde durch die aktualisierte Version behoben.

### Bekannte Grenzen / noch nicht umgesetzt

- Nur der Jeep-Prototyp ist in diesem Abschnitt fahrbereit getestet; keine Aussage über funktionierende Fahrt, Ankunft oder Tankautomatik aller acht Fahrzeuge.
- Keine echten Zapfsäulen-/Distanzprüfungen, keine Tankstellenoberflächen, keine Inventar-/Kraftstoffitem-Transaktionen und keine Betankung aus Fahrzeuglagern.
- Keine automatische Fahrzeugbetankung in **nicht geladenen Gebieten**; keine eigene Tankstellenproduktion. Kraftstoffherstellung ist als vorgelagerte Verarbeitung in den Rezeptdaten vorgesehen.
- Die Zeit einer Weltkarten-Fahrzeugreise wird noch nicht zuverlässig auf den bezahlten Treibstoffblock angerechnet.
- `.rotsave` ist derzeit JSON ohne Verschlüsselung/Manipulationsschutz; AES-256-CBC + HMAC-SHA256 bleibt ein geplanter Entwicklungsschritt.
- Die in den alten Dokumentabschnitten genannten Testbuild-Schätzwerte beschreiben frühere Planungsstände und sind keine aktuellen Abschlussquoten.

### Priorisierter nächster Arbeitsabschnitt

1. Optionale Nutzung des **Fahrzeuglagers** als eigene Treibstoffquelle vorbereiten: ausschließlich nach expliziter Freigabe pro Fahrzeug; bei Spielerabwesenheit niemals auf den Rucksack zugreifen.
2. Treibstoff-/Fahrzeitberechnung der **Weltkarten-Fahrzeugreisen** ergänzen und testen.
3. Lokale Tankstellen-/Abstandsregeln, weitere Fahrzeugtypen und Vorratswarnungen ausbauen; per Spielstand konfigurierbar.
4. Save-Verschlüsselung mit Integritätsprüfung zunächst separat erproben, danach verlustfreie Migration der bestehenden Spielstände.
5. Anschließend zu den weiteren Kernmechaniken (Events, Gegner, Loot, Produktion, Basisbau, Story, NPCs) übergehen. Grafiken, endgültige Items und GUI-Gestaltung folgen später; bereits gute, schlichte GUIs werden nicht unnötig ersetzt.

**Teststrategie:** Vollständige Build-, Installer- und Kompatibilitätsprüfungen am Ende der Spielentwicklung; Windows 7 SP1 ist verbindlich vorgesehen, Windows XP SP3 optional als zusätzlicher Härtetest.

---

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
| endgültiges Spiel inkl. vollständiger Systeme, Inhalte, Story, Kartenbefüllung, Grafik, Audio und Polishing | **ca. 30 %** |

Die Prozentwerte bleiben Näherungswerte. Viele Systeme sind bereits geplant oder prototypisch vorhanden, müssen aber noch vollständig miteinander verbunden, mit Inhalten gefüllt und getestet werden.



## Fortschritt bis zum endgültigen Spiel

Die bisherige 40-%-Angabe bezieht sich ausdrücklich auf eine funktional spielbare Gesamtfassung **ohne** finales Grafik-, Audio-, Shader- und Inhalts-Polishing. Für das tatsächlich endgültige Spiel muss zusätzlich der komplette geplante Inhalt umgesetzt und ausproduziert werden.

Aktuelle Gesamtschätzung:

- **Endgültiges Spiel: ca. 30 % fertig**
- **Noch offen: ca. 70 %**

Diese 70 % bestehen nicht nur aus Programmierung. Ein großer Anteil entfällt auf die vollständige Kartenbefüllung, Hauptstory und Quests, Gegner-/Kampfinhalte, Basisbau, Crafting/Produktion, Progression, Händler/Economy, Begleiter/NPCs, Fahrzeuge, Events, finale Spielbalance, vollständige Musik, Soundeffekte, Modelle, Texturen, Animationen, Beleuchtung, Effekte, Benutzeroberfläche, Optimierung und abschließende Tests.

Die Schätzung ist deshalb bewusst deutlich niedriger als der Stand des ersten Tester-Builds: Der Tester-Build prüft nur den bereits vorhandenen Spielkern, während das endgültige Spiel den vollständigen geplanten Umfang enthalten soll.

## Stand bis zum ersten externen Testbuild

Der erste Testbuild dient der Prüfung des bereits vorhandenen Spielkerns. Crafting und andere große spätere Systeme sind dafür noch nicht Voraussetzung.

Aktuell vorhanden bzw. vorbereitet:
- Hauptmenü mit Hintergrundbild und funktionierender Hauptmenü-Musik
- Neues Spiel / Spiel laden / Einstellungen / Beenden
- globales Pause-System mit `DontDestroyOnLoad` und persistent abgesichertem `EventSystem`
- Pause-System muss nicht in jede der 30 Maps einzeln eingebaut werden
- Inventar öffnen/schließen über `I`
- Basis, Weltkarte und feste Gebiete als Testpfad
- Sammeln, Loot und vorhandener Inventar-/Kampfstand als Kernfunktionen
- dynamische EventMap als vorhandener Testbereich
- Windows-x86_64-Build wurde bereits erzeugt
- Tester-Prüfliste wurde erstellt; sie weist ausdrücklich auf Platzhaltergrafik und die vorläufig unterstützte CPU-Luftkühlung hin
- erster Build zeigte, dass die externen Datenbanken nicht mit ausgeliefert wurden; `StreamingAssets/database` wurde dafür vorbereitet und `AreaData.cs` auf `Application.streamingAssetsPath` umgestellt

### Noch vor der Ausgabe an Tester

1. neuen Windows-Build mit enthaltenem `StreamingAssets/database` erzeugen
2. kurz prüfen, ob der Build die Gebietsdatenbank tatsächlich findet und bis in den Kern-Gameplay-Loop startet
3. kompletten Build-Ordner zusammen mit der Tester-Prüfliste verteilen

Die eigentliche breite Funktionsprüfung übernehmen anschließend die Tester anhand der Prüfliste.

**Geschätzter Stand bis zum ersten auslieferbaren Tester-Build: ca. 95 %.**

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
| Fahrzeuge | Planung stark konkretisiert | DB-Migration + Laufzeitsystem offen |
| Events | strukturell vorbereitet | echte Laufzeitanbindung |
| Einstellungen | strukturell fertig | Restwerte schließen |
| Progression/XP | vollständig erzeugt | Qualitäts-/Referenzprüfung |
| Pakete/Belohnungen | vollständig erzeugt | Item-Referenz-/Stackprüfung |
| Quests/Story | aktive Planungsphase | DB und Laufzeitsystem offen |
| Shop | noch nicht gebaut | offen |
| Händler | noch nicht gebaut | offen |
| Economy | noch nicht gebaut | offen |
| Begleiter/NPC-KI | Regeln weitgehend definiert | DBs + Laufzeitsystem offen |


## Musiksystem

Aktueller Stand:
- `Prefab_IngameMusik` ist als gemeinsame Musikstruktur vorbereitet
- Hauptmenü-Musik ist eingebunden und funktioniert
- Weltkartenmusik ist vorgesehen
- Musikdateien werden als `.ogg` organisiert
- für die 30 festen Gebiete existiert unter `music/Feste_Gebiete` je Gebiet ein eigener Ordner
- `Test_Kiefernwald_v01` ist ausdrücklich von der festen Musikstruktur ausgeschlossen
- `EventMap` erhält eine gemeinsame Eventmusik unabhängig vom konkreten temporären Event; dadurch ist keine eigene Musiklogik pro Event nötig
- pro Gebiet können mehrere Titel/Varianten abgelegt und später ausgetauscht werden
- weitere Gebietstitel werden schrittweise generiert und eingepflegt

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


## Neue Planungsstände: Siedlung, Horror und Bosse

Neu festgelegt bzw. als Planungsgrundlage bestätigt:
- Siedlungsgebäude werden bis maximal Stufe 3 ausgebaut.
- Jede einzelne Ausbauzeit bleibt bei maximal 30 Minuten.
- Grundsätzlich reicht ein Hauptmodell pro Gebäude; Bau-/Ausbauzustände können über Baustellenelemente dargestellt werden.
- Siedlung erhält einen geplanten Bewegungsbonus von ca. +25 %.
- Expeditionen sind ausschließlich über die Siedlung möglich und benötigen ein eigenes Expeditionsfahrzeug sowie mindestens Stufe 2 bei Funk-/Expeditionszentrum und Fahrzeugdepot.
- Strom/Wasser werden getrennt verwaltet; bei Energiemangel ist ein Notmodus statt vollständigem Zusammenbruch vorgesehen.
- Wasserkraftwerk ist aktuell nicht fest eingeplant; Generatoren bilden die Grundversorgung, Solar kann ergänzen.
- normale Begleit-/Zuchthunde bleiben an der Spielerbasis; Wachhunde können ab Verteidigungszentrum Stufe 2 in der Siedlung eingesetzt werden.
- Horror-/Gruseleffekte sind optional abschaltbar. Bei deaktivierter Darstellung erscheinen normale Ersatzgegner, die sämtliche spielerischen Eigenschaften 1:1 übernehmen.
- Boss-Grundregel: jeder Boss besitzt genau eine Kampfphase.
- Hauptstory ist Pflicht; Nebenstory, Nebenquests und SECRET-Inhalte sind optional. Nebenquests dürfen ausdrücklich als Zeitvertreib dienen.

Die vollständigen Planungsstände liegen zusätzlich in:
- `docs/Remnants_of_Tomorrow_Siedlungsgebaeude_Planungsstand.txt`
- `docs/Remnants_of_Tomorrow_Horrorfiguren_Planung.txt`

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
- endgültige `.rotsave`-Struktur (`.sgsave` als Reserve)
- maximal 5 manuelle Speicherslots (vorgesehen)
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
- Story-/Quest-Freischaltungen konkretisieren
- Fahrzeugwracks finden und zur Hauptbasis bergen
- gespeichertes Montage-Minispiel für den Erstaufbau
- Fahrzeugzustand und genau ein Exemplar je Fahrzeug
- feste Fahrzeuglager, Sitzplätze, Schutzwerte und Haltbarkeit
- feste Geschwindigkeiten und Weltkarten-Zeitreduktionen
- Treibstoffpunkte und Verbrauch pro angefangenen 10-Minuten-Block
- proportionale Reparatur 1–99 % und Generalreparatur bei 0 %
- automatischer Rücktransport bei 0 Haltbarkeit
- Tod außerhalb des Fahrzeugs: stehen lassen oder zur Basis schicken
- Überfahrregeln und Haltbarkeitskosten anbinden
- Gelände- und Größenbeschränkungen umsetzen
- optionale Fahrzeuglackierung mit 12 festgelegten Sprühdosen-Farben
- Weltkartenintegration und Save/Load vollständig anbinden
- alte Fahrzeug-DB auf den neuen bestätigten Planungsstand migrieren

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

### Kurzfristig: erster Tester-Build
1. Datenbanken vollständig über `StreamingAssets/database` mitliefern
2. Windows-x86_64-Testbuild neu erzeugen
3. Start und DB-Zugriff kurz gegenprüfen
4. kompletten Build-Ordner plus Tester-Prüfliste verteilen
5. Rückmeldungen der Tester sammeln und Blocker beheben

### Danach: weitere Entwicklung
1. erfolgreichen EventMap-Prototypen nicht unnötig umbauen
2. Testevent-Datenstruktur in eine echte Event-ID-/Eventdaten-Pipeline überführen
3. `events.json.db` an den Eventmanager anbinden
4. danach Gegner-, Ressourcen- und Loot-Spawns für Events anbinden
5. anschließend die offenen Pflichtsysteme in der obigen Reihenfolge bis zur funktional vollständig spielbaren Fassung schließen


## Update 09.10.2026 – Spielerbasis und Horden

Neu festgelegt:
- 8 reguläre Baustufen für Boden, Wand, Tür und Fenster: Holz, Pressholz, verstärktes Holz, Bruchstein, Ziegelstein, Steinmauer, verstärkte Stein-/Metallkonstruktion, Eisen.
- Boden kann durch Gegner/Horden nicht zerstört werden und ist nur durch Spielerabriss entfernbar.
- HP-Reihenfolge je Stufe: Wand > Tür > Fenster.
- neue HP-Kurve bis Stufe 8: Wand 6000 / Tür 4800 / Fenster 3600.
- Bau-/Upgrade-Kosten für alle 8 Baustufen festgelegt.
- Reparaturkosten: vollständige Reparatur kostet 50 % der Bau-/Upgrade-Kosten der aktuellen Stufe; Teilreparatur proportional.
- Lagerung bleibt vollständig über Kisten/Truhen; keine separaten Waffen-/Medizin-/Materialschränke als eigenes Lagersystem.
- Batteriesystem besteht aus leerer Batteriebank mit 6 Slots plus separaten Batterien; eingesetzte Batterien sind wiederaufladbar.
- Wassertanks und Pumpen gehören ausschließlich zur Siedlung, nicht zur normalen Spielerbasis.
- Horden bestehen nur aus normalen Gegnern:
  - Horde 1: insgesamt 10 leichte Gegner
  - Horde 2: insgesamt 25 Gegner, zufällige Mischung leicht/mittel
  - Horde 3: insgesamt 50 Gegner, zufällige Mischung leicht/mittel/schwer
- die Gesamtzahl je Hordenstufe bleibt fest; nur die Anteile der erlaubten Klassen werden zufällig bestimmt.
- keine Spezialgegner, Mini-Bosse oder Bosse in Standardhorden.
- Horde wird intern ausgelöst, ohne eigenes Hordengebiet auf der Weltkarte.
- Angriffsrichtung zufällig Nord/Süd/Ost/West.
- komplette Horde spawnt auf einmal, keine Wellen.
- Spieler außerhalb der Basis: Horde greift direkt den Spieler an.
- Spieler innerhalb der Basis: Horde greift die Basis an, um zum Spieler zu gelangen.
- stirbt der Spieler während des Hordenangriffs, wird der Angriff sofort beendet; bereits verursachter Basisschaden bleibt bestehen.

Detailstand:
- `docs/Remnants_of_Tomorrow_Basis_Horden_Planungsstand.txt`

### Noch offen in diesem Planungsblock
- exakte Bau-Schadenswerte der normalen Gegnerklassen
- finale Zuordnung der 53 Gegner zu leicht/mittel/schwer für Horden
- Spawnabstand und technische Spawnpunkt-Prüfung
- Warnanzeige/UI für die 2-Ingame-Stunden-Hordenwarnung
- Hordenstatus in Save/Load
- DB-Struktur für Baustufen, HP, Kosten, Reparatur und Hordenregeln


## Update 09.10.2026 – Fahrzeuge

Der Fahrzeugblock wurde weitgehend konkretisiert und in einer eigenen Referenzdatei dokumentiert.

Neu festgelegt:
- Reihenfolge: Motorrad -> Jeep -> Gepanzertes Auto -> Panzer -> Luftkissenboot -> Schnellboot -> Helikopter -> LSD Labor.
- Jedes Fahrzeug kann vorerst nur einmal besessen werden.
- Fahrzeuge haben keine Level und keine aufwertbaren Statistikstufen.
- Freischaltung über Story/Quest, nicht über Spielerlevel.
- Die meisten Fahrzeuge werden als Wrack/Schrotthaufen gefunden und in der Hauptbasis wieder aufgebaut.
- Erstaufbau als Montage-Minispiel mit groben Einbauzonen; der Spieler muss passende Teile selbst zuordnen.
- Montagefortschritt wird nach jedem korrekt montierten Teil dauerhaft gespeichert.
- Fehlende Teile dürfen später gefunden oder hergestellt werden; kein Neustart bei 0.
- Lager, Sitzplätze, Schutz, Haltbarkeit, Tank, Verbrauch, interne Geschwindigkeit und Weltkarten-Zeitreduktion sind für alle 8 Fahrzeuge festgelegt.
- Weltkartenreisen: maximal 60 Minuten, Treibstoffverbrauch pro angefangenen 10-Minuten-Block der tatsächlichen Fahrzeugreise.
- Geländetauglichkeit der Fahrzeuge wurde festgelegt.
- Bei 0 Haltbarkeit wird das Fahrzeug mit Lagerinhalt und Treibstoff zur Hauptbasis zurückgesetzt und bleibt bis zur Reparatur unbenutzbar.
- Kein einzelner Treffer darf ein voll intaktes Fahrzeug direkt auf 0 setzen.
- Tod außerhalb des Fahrzeugs: Fahrzeug am Todesort geschützt stehen lassen oder ohne Treibstoffkosten zur Hauptbasis schicken.
- Reparaturregeln und vollständige 0-%-Teilelisten für alle Fahrzeuge festgelegt.
- Überfahren ist nur mit Jeep, gepanzertem Auto, Panzer und LSD Labor möglich; Gegner-Matrix und Haltbarkeitskosten sind festgelegt.
- Boss-/Storyboss-Regel: niemals normal durch Überfahren beschädigbar.
- Lackierung optional; 12 Farben mit festen Sprühdosen-Rezepten; 1 Sprühdose färbt 1 komplettes Fahrzeug.

Detailstand:
- `docs/Remnants_of_Tomorrow_Fahrzeuge_Planungsstand.txt`

Noch offen:
- konkrete Story-/Questabläufe pro Fahrzeug
- exakter Bergungs-/Transportablauf eines Wracks zur Hauptbasis
- finale Montage-Minispiel-UI und Einbauzonen
- Kollisionsschaden gegen Umweltobjekte
- technische Migration der veralteten Fahrzeug-DB


## Update 10.10.2026 – Fahrzeugplanung abgeschlossen

**Planungsstatus Fahrzeugfunktionen: abgeschlossen.** Der Detailstand wurde
in [docs/Remnants_of_Tomorrow_Fahrzeuge_Planungsstand.txt](docs/Remnants_of_Tomorrow_Fahrzeuge_Planungsstand.txt)
um alle neu bestätigten Regeln ergänzt.

- Acht Fahrzeugtypen mit festen Werten, plus unzerstörbarer Bergungs-Lkw.
- 3 menschliche Begleiter plus Hund; Sitz- und Reiseregeln bestätigt.
- Fahrzeugschutz je nach Spieleranwesenheit, Tank und Haltbarkeit.
- Bergungszeiten, Montage, Feld-/Werkstattreparatur und Warteschlangen.
- Zwei eigenständige Tankstellen, Vorratsgrenzen, Reserve, Betankungs-
  automatik und Warnmeldungen.
- Fahrzeuglager mit direkten Transfers, Schutzmengen, Sortierung,
  Filtern, Beladelisten, Standort-Beladung und Leseansicht Weltkarte.
- Bestätigungsdialoge und atomare, absturzsichere Bestandstransaktionen.
- Sichere Ein-/Ausstiegsplätze und Befreiung feststeckender Fahrzeuge.

**Realisierungsstatus:** Diese Planung ist noch NICHT gleichbedeutend mit
fertigen oder getesteten Unity-Skripten. Fahrzeug-DB-Migration,
C#-Logik, UI, Prefabs, Weltkartenintegration und Tests sind weiterhin
offene Entwicklungsarbeit. Es liegen in diesem Dokument keine
Testergebnisse vor, die eine vollständige Fahrzeugimplementation belegen.

**Gesamtfortschritt:** Die bisherigen Schätzungen gelten vorläufig
weiter (funktionsfähige Fassung ohne Grafik-/Audio-Polish ca. 40 %,
endgültiges Spiel ca. 30 %). Allein durch Dokumentation erhöht sich
kein belegbarer Implementierungsfortschritt.

**Nächster technischer Schritt:** existierende vehicle-JSON-Datenbanken
mit den freigegebenen Fahrzeugwerten abgleichen, Datenvalidierung und
Save-Strukturen prüfen, danach Fahrzeug-Kernlogik mit Unity 2017.2.5f1
umsetzen und testen. Die bereits vorbereiteten Tester-Systeme dabei
nicht unnötig verändern.

## Update 10.10.2026 – Implementierungstests: Jeep und südliche Gebietsankunft

**Nachweislich getestete Prototypen (Unity 2017.2.5f1):**

- Fahrzeug-Hauptdatenbank `vehicles.json.db`: `VehicleDatabaseLoader.cs` meldet **8** erfolgreich geladene Fahrzeugdefinitionen.
- Fahrzeug-Steuerungsdatenbank `vehicle_steering.json.db`: `VehicleSteeringDatabaseLoader.cs` meldet **8** geladene Datensätze; Physikwerte weiterhin **vorläufig**.
- `VehicleManager.cs`: Grundverwaltung der **8 gesperrten, ungebauten** Fahrzeuge initialisiert. Das ist noch kein vollständiges Story-/Freischalt- oder Save-System.
- `VehiclePhysicsConfigurator.cs` + `VehicleWheelController.cs`: Jeep mit **4 Rädern**, **AWD**, interner Geschwindigkeitswert **65**, resultierende Höchstgeschwindigkeit **12,03 Unity-Einheiten/s** im Test bereit.
- `VehicleInteraction.cs`: Ein- und Aussteigen sowie Fahren/Bremsen am Test-Jeep erfolgreich erprobt; alter `TestJeep` als Referenz deaktiviert.
- Neu `WorldMapArrival.cs` (eigenständiges Laufzeitsystem): erkennt Gebietsboden und berücksichtigt südlichen `WorldMapExit`-Trigger. Nach Korrektur der Unity-2017-Inkompatibilität (`Scene.handle` entfernt) ohne Kompilierungsfehler getestet.
- Südlicher Spawn auf der **200×200**-Standardkarte: **X=0, Z=-90**, Blickrichtung **Norden (+Z)** im Code. Bei Wechseln zwischen verschiedenen Gebietskarten erneut Z=-90 bestätigt; der Spieler konnte die ganze Karte durchqueren.
- Bestehende Komponenten `WorldMapTravel.cs`, `WorldMapExit.cs`, `SaveSystem.cs`, `Prefab_Player`, `AreaSpawnZone.cs` und `AreaSpawnManager.cs` blieben unverändert. Der **190×190**-Ressourcenbereich bleibt erhalten.

**Noch nicht als fertig markieren:**

- Weltkarten-Fahrzeugreise mit Übernahme des konkreten Fahrzeugs in die Zielszene; Fahrer soll am südlichen Eingang **bereits im Fahrzeug sitzen**.
- Dauerhafte Speicherung von Fahrzeug, Standort, Tank, Haltbarkeit, Lager und Reisezustand; Freischaltung/Bergung/Montage/Produktion und sonstige Fahrzeugfunktionen.
- Eigener Regressionstest für F11/Save-Load und dort gespeicherte Spielerkoordinaten nach Einführung von `WorldMapArrival.cs`; das Verhalten des Save-Skripts wurde im Code nachvollzogen, aber hier nicht als erneut getestet gemeldet.
- Erweiterte Tests für Fahrzeuge mit anderem Platzbedarf (insbesondere Panzer und LSD-Labor) und weitere Kartentypen.

**Schutz bestehender Systeme:** Funktionsfähige Skripte, Prefabs, Karten und Datenbankdateien nicht ohne Not umbauen; neue Mechaniken möglichst separat ergänzen.

**Fortschrittsschätzung unverändert:** ca. **40 %** funktionale Fassung ohne finales Grafik-/Audio-Polishing, ca. **30 %** endgültiges Spiel. Erfolgreiche Prototyptests entsprechen nicht der Vollimplementierung.
