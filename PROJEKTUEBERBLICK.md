# Remnants of Tomorrow (RoT) – kompakter Projektüberblick
**Stand: 02.11.2026 · Spoilerarme öffentliche Zusammenfassung · In Entwicklung**

## 1. Spielidee und Umfang
RoT ist ein eigenständiges postapokalyptisches Survival-Spiel mit Erkundung, Sammeln, Kampf, Basisbau, Werkbank-Crafting, Fahrzeugen, Begleitern, Siedlungsausbau und langfristigem Fortschritt. Das grundlegende Survival-Prinzip orientiert sich an Genrevorbildern, während Spielwelt, Balancing, Grafik und Systeme eigenständig geplant werden.

Vorgesehen sind unterschiedliche Ressourcen-, Stadt-, Industrie-, Kälte- und Sondergebiete. Die Weltkarte verwaltet Reisen, Schwierigkeiten und separate Eventmarker. Haupt- und Nebenmissionen, zufällige Begegnungen und optionale größere Ereignisse sollen den Spielfortschritt ergänzen. **Story, Spezialfiguren, versteckte Inhalte und Bossdetails werden hier bewusst nicht offengelegt.**

## 2. Technische Grundlage und tatsächlicher Projektstand
- **Engine:** Unity **2017.2.5f1**, Built-in Render Pipeline; **Sprache:** C#; **Modellierung:** Blender.
- **Daten:** JSON-basierte Dateien mit Endung `.json.db`; maßgeblicher aktiver Datenbankpfad im lokalen Spiel: `Assets/StreamingAssets/database/`. Definitionsdaten und veränderliche Spielstände bleiben getrennt.
- **Spielstand:** Verschlüsseltes `.rotsave` als Hauptformat, `.sgsave` als Reserve; fünf manuelle Slots sowie zusätzliche Sicherungs- und Wiederherstellungsmechanismen sind vorgesehen bzw. teilweise vorbereitet.
- **Zuletzt dokumentierte Projektkopie (01.11.):** 36 Unity-Szenen (davon 34 im bisherigen Build-Abgleich aktiv), 213 C#-Dateien, 32 Prefabs, zwei separate Materialdateien. Die Zahlen beziehen sich auf das lokal geprüfte Archiv, **nicht auf hier veröffentlichte Projektdateien**.
- **Vorhandene Prototypen/Grundlagen:** Spieler und Kamera, Hauptmenü, Weltkarte und Gebietswechsel, Ressourcenabbau, Inventar/Lager, Ausrüstung, Kampf/Gegner, Crafting, Fahrzeug-/Tankstellenfunktionen sowie Basis-Horden. Einzelne Funktionen wurden in Unity getestet; daraus folgt **kein vollständig spielbares Gesamtspiel**.
- **Bestätigte Teiltests:** unter anderem Weltkarten-/Fahrzeugprototypen sowie Horden- und Save/Load-Tests. Der Produktionssystem-Zwischenstand lief am 27.10. in einem kurzen Unity-Play-Modus-Test ohne Konsolenfehler oder -warnungen; ein vollständiger Herstellungsablauf wurde dadurch nicht bestätigt.
- **Offene Integration:** Neuere C#-Arbeitsfassungen für Produktionslogik, Menüs, Benachrichtigungen und Save-Recovery müssen noch zusammen kompiliert und praktisch getestet werden. Die Korrektur eines am 30.10. gemeldeten Compilerfehlers wurde noch nicht durch eine erneute vollständige Unity-Prüfung bestätigt.

## 3. Spielsysteme in Entwicklung
| Bereich | Stand und Ziel |
|---|---|
| Survival und Fortschritt | Gesundheit, Hunger, Durst, Temperatur, Ausrüstung, XP, Level, Forschung und Freischaltungen; Zusammenführung noch offen |
| Inventar, Loot und Ressourcen | Gegenstands-IDs, individuelle Stapelgrößen, Container, Abbau und Lootpläne; durchgehende Transaktions- und Gebietstests fehlen |
| Crafting und Produktion | Herstellung über passende Werkbänke mit Rezepten, Materialkosten, Warteschlangen und Ausgaben; Schnittstellen und Fehlerfälle weiter integrieren |
| Basisbau und Siedlung | Rasterbau, Ausbau, Verteidigung, Lager sowie getrennte Siedlungssysteme für Strom, Wasser, Maschinen und Bewohner; noch umfassende Implementierung nötig |
| Gegner, Kampf und Horden | Waffenhaltbarkeit, Gegnerverhalten und Basisangriffe; getestete Teilfunktionen, weitere Balancing- und Persistenztests nötig |
| Fahrzeuge und Reisen | Vorhandene Jeep-/Tankstellenprototypen; weitere Land-, Wasser- und Luftfahrzeuge als Planungsumfang |
| Begleiter, Handel, Computersystem | Eigene KI, Interaktionen, Handels- und spielinterne Computersysteme geplant; noch keine Gesamtfreigabe |
| Missionen und Events | 25 große Eventkonzepte mit lokal vorbereiteten separaten Eventdatenbanken und Index; vollständige Unity-Anbindung steht aus |

Die **25 Eventdatenbanken** sind ein lokaler Planungs-/Datenstand; ältere Repository-Angaben über sieben Einträge in einer früheren `events.json.db` beschreiben einen älteren Prototyp. Für reguläre Gebiete liegen außerdem vorbereitete Lootpläne vor, aber deren vollständige Laufzeitintegration und Abgleich mit tatsächlich geladenen Gebietsdaten sind noch offen. Kleine Zufalls-/Mini-Events und Basis-Horden sind davon unabhängig.

## 4. Grafik, Assets und Produktionsstrategie
Angestrebt wird eine **möglichst hochwertige, realistische Grafik** mit sinnvollen Qualitätsstufen und stabiler Performance. Für Umgebungen, Gebäude, Natur, Werkstätten, Krankenhäuser, Lebensmittel, Waffen, Fahrzeuge, UI und Effekte wurde eine breite **Asset-Vorauswahl** aus geeigneten Quellen zusammengestellt. Einfache kleinere Gegenstände dürfen weniger komplex modelliert sein; charakteristische Gebäude und besondere Figuren erhalten individuelle Blender-Modelle beziehungsweise aufwendige Anpassungen.

Die Vorauswahl ist **keine finale Freigabe**: Lizenz, kommerzielle Nutzbarkeit, Originaldateien, Rigging, Texturen, Animationen und Importfähigkeit in Unity 2017 müssen je Asset kontrolliert werden. Moderne URP-/HDRP-Pakete werden nicht ungeprüft übernommen. Die **vollständige Downloadliste folgt erst nach abgeschlossener Gesamtprüfung**. Bis dahin keine vorzeitige Integration. Endgültige Modelle, UI-Gestaltung, Musik, Geräusche und Effekte folgen nach den vorrangigen Gameplay- und Integrationstests.

## 5. Nächste Meilensteine und Status
1. Vorbereitete C#-Systeme in der vorhandenen Unity-Version gezielt kompilieren und vorhandene funktionsfähige Komponenten schonen.
2. **Durchgehenden Kernablauf nachweisen:** Hauptmenü → Spielstart/Slot → Basis → Gebiet → Sammeln und Kampf → Rückkehr → Crafting/Lager/Bauen → Speichern → Laden.
3. Datenbanken, Story-/Eventzustände, Fahrzeuge, Begleiter, Siedlung, Produktions- und Belohnungssysteme zuverlässig verbinden; Fehlschläge und Wiederherstellung testen.
4. Danach Assets, Weltgestaltung, Animationen, Audio und grafische Qualitätsstufen finalisieren; Windows-Build, Performance und Regression prüfen.

**Status: aktive Entwicklung, kein veröffentlichungsreifer Build.** Als Wunschziele waren der 31.12.2026 beziehungsweise spätestens der 31.01.2027 dokumentiert; diese Termine sind **keine verbindliche Fertigstellungszusage**. Ein vorbereiteter Entwurf, vorhandener C#-Code, erfolgreiche Kompilierung und bestandener Gameplaytest sind ausdrücklich unterschiedliche Fortschrittsstufen.

Weitere Details stehen in den bestehenden Dokumenten [Entwicklungsstand](ENTWICKLUNGSSTAND.md), [Projektfortschritt](FORTSCHRITT.md) und [README](README.md). Diese Kurzfassung veröffentlicht keine Storyspoiler, internen Datenbanken, Verschlüsselungsschlüssel, lokalen Archive oder Unity-Projektdateien.
