# Entwicklungsstand

**Stand:** 30.09.2026

## Aktuelle Entwicklungsphase

Der Schwerpunkt liegt nach der Ressourcen-Grundkonfiguration nun auf **Gebäuden und festen Kartenobjekten**. Finale Grafik, Vertonung und weitere Endstufen-Systeme kommen bewusst später.

## Gebietsfortschritt

Geplante feste Gebiete: **30**

### Ressourcen-Grundkonfiguration fertig
- Kiefergestruepp
- Kiefernhain
- Test_Kiefernwald
- Steinfeld
- Steinbruch
- Felsklippen
- Kohlemine
- Eisenmine
- Feuchtwiese
- Moorgebiet
- Sumpfgebiet
- Kalter_Waldrand
- Schneefeld
- Frostgebiet
- Kuestengebiet
- Hafen
- Verlassene_Stadt
- Stadtruinen
- Verlassene_Einrichtung
- Forschungsanlage
- Militaerstuetzpunkt
- Insel
- Siedlung
- Zweite_Basis
- Test_Basis
- Bunker_A
- Bunker_B
- Bunker_C
- Bunker_D
- Tschernobyl

Damit sind aktuell **30 von 30** festen Gebieten bei der Ressourcen-Grundkonfiguration beziehungsweise beim vorgesehenen Spawn-Grundzustand eingerichtet.

### Nächster Entwicklungsblock
- Gebäude und feste Kartenobjekte
- danach weitere repräsentative Tests
- später automatischer Gebiets-/Spawn-Validator

## Aktueller Teststand

Bereits technisch geprüft:
- Spielerbewegung
- einfache Interaktion mit E
- Ressourcen sammeln und abbauen
- Inventar-Grundfunktion mit Stacks
- Gesundheit und einfacher Faustkampf
- Weltkarten-Ausgänge und Szenenwechsel
- zufälliges Ressourcen-Spawning mit Mindestabstand
- kleine und große Gebäudehüllen
- Eltern-/Kind-Struktur für Gebäude
- normale Tür mit Scharnier, Öffnen/Schließen mit E und Öffnung in beide Richtungen
- Lootkiste mit mehreren möglichen Loot-Einträgen
- zufällige Lootmengen
- prozentuale Lootchancen
- mehrere Loot-Treffer in einer Kiste
- Kiste kann nur einmal geleert werden
- Testgröße der Lootkiste als sinnvolles Hindernis: Scale 1.2 / 1.5 / 0.8

Noch technisch zu prüfen bzw. als nächster Funktionsblock:
- Kisten mit eigenem Mini-Inventar statt automatischer Übergabe
- echtes Container-/Stack-Verschieben zwischen Kiste und Spieler
- Gegner-Spawning pro Gebiet
- mehrere Gegnertypen und besondere Angriffe
- echtes Crafting mit Werkbank
- Produktionszeiten
- Recycler
- Schmelzer
- Hunger, Wasser und weitere Überlebenswerte
- Strahlung, Infektion und Temperatur
- Bausystem und Abriss
- Basis-Ressourcenreset auf freien Flächen
- Events und Eventphasen
- Quest-/Storyfortschritt
- Skill-/Fortschrittssystem
- Fahrzeuge
- Begleiter
- Siedlungsmechaniken
- lesbare Dokumente / Fundstücke
- Speichern/Laden aller späteren persistenten Systeme
- später: datengetriebener Zugriff auf .db-Dateien

## Bereits vorhandene Grundsysteme

- Spielerbewegung
- einfache Interaktion mit E
- Test-Inventar mit 10 Grundslots und Stacks
- Gesundheit
- einfacher Faustkampf
- Koordinatenanzeige
- Speichern und Laden als technischer Test
- Weltkarten-Ausgänge an allen vier Kartenrändern
- Weltkarten-Reise
- zentrales Gebietssystem über AreaData
- wiederverwendbares Prefab_AreaSystem_Standard
- AreaSpawnZone für zufällige Positionen
- AreaSpawnManager für zufälliges Ressourcen-Spawning
- Mindestabstand zwischen gespawnten Ressourcen
- GameManager mit DontDestroyOnLoad
- funktionierender Demo-Türmechanismus:
  - Tür mit Scharnier-/Drehpunkt
  - Öffnen/Schließen mit E
  - Öffnung je nach Spielerseite in beide Richtungen

## Bereits eingeführte Ressourcen

- Holz / Bäume
- harte Bäume
- Stein
- loses Holz
- loser Stein
- Hanf
- Kohle
- Eisen
- Moos
- Beeren
- Schnee
- Eis
- Harz
- Tannenzapfen
- Tannennadeln
- Winterkraut
- Sand
- Salz
- Schrott

## Aktuelle Gebiets-Balance

### Wälder
- Kiefergestruepp: leichter Wald
- Kiefernhain: mittlerer Wald mit harten Bäumen
- Test_Kiefernwald: schwerer Wald mit höherem Anteil harter Bäume

### Felsgebiete
- Steinfeld: leicht
- Steinbruch: mittel
- Felsklippen: schwer

### Minen
- Kohlemine: Kohle als Hauptressource
- Eisenmine: Eisen als Hauptressource

### Feuchtgebiete
- Feuchtwiese: pflanzenreich, Moos 15-25
- Moorgebiet: deutlich moosreicher, Moos 25-35
- Sumpfgebiet: stärkster Moosanteil, Moos 35-50

### Kältegebiete
- Kalter_Waldrand: viel Holz, Beeren, Harz, Tannenzapfen und Tannennadeln; wenig Schnee und Eis
- Schneefeld: Schnee 20-30, Eis 8-15; deutlich weniger Holz und Pflanzen
- Frostgebiet: Schnee 30-40, Eis 15-25; nur sehr wenig Holz und Pflanzen

### Küstengebiete
- Kuestengebiet: Sand als Hauptressource, kein Salz
- Hafen: weniger Vegetation, mehr loses Material und Stein; Salz kommt nur im roten Gebiet Hafen vor
- Insel: Mischung aus Wald- und Küstenressourcen

### Stadt-, Technik- und Militärgebiete
- Verlassene_Stadt: Schrott 10-20
- Stadtruinen: Schrott 20-30
- Verlassene_Einrichtung: Schrott 15-25
- Forschungsanlage: Schrott 20-30
- Militaerstuetzpunkt: Schrott 25-35

### Bunker
- Bunker_A bis Bunker_D sind mit knappen Außenressourcen und zunehmendem Schrottanteil grundkonfiguriert
- natürliche Ressourcen sollen später nur im Außen-/Eingangsbereich erscheinen
- Innenebenen erhalten stattdessen Gegner, Kisten, Storyobjekte und eigene Lootpools

### Tschernobyl
- natürliche Grundressourcen bleiben vorhanden
- Schrott ist stark vertreten
- Strahlung und andere Gefahren werden später als Gebietseffekte umgesetzt

### Basis und Siedlung
- Siedlung ist eine bewusste Ausnahme und besitzt keine normalen zufälligen Grundressourcen
- Test_Basis besitzt als Prototyp:
  - Baum 15-25
  - Stein 10-20
  - loses Holz 8-15
  - loser Stein 8-15
  - Hanf 5-10
- Zweite_Basis soll ebenfalls natürliche Basisressourcen erhalten
- späterer Basis-Ressourcenreset:
  - natürliche Ressourcen können nach definierter Zeit neu erscheinen
  - nur auf freien Flächen
  - gebaute Objekte bleiben unangetastet

## Gebäude-Prototyp

In `Verlassene_Stadt` wurde `Gebaeude_Test_01` aufgebaut.

Enthalten:
- Boden
- vier Außenwände
- Türöffnung
- `Tuer_Drehpunkt` als Empty GameObject
- `Tuer` als Cube und Kindobjekt des Drehpunkts
- funktionierende Türinteraktion über `DemoDoor.cs`
- Innenwand als einfacher Raumtrenner
- vorgesehener Prefab-Name: `Prefab_Gebaeude_Test_01`

Das aktuelle Gebäude ist bewusst nur ein kleines technisches Testmodell. Echte Gebäude werden später deutlich größer und detaillierter.

## Noch nicht vollständig umgesetzt

- Lootkisten mit Datenbank-Lootpools und eigenem Mini-Inventar
- Gegner-Spawning pro Gebiet
- größere Gebäude, Ruinen und feste Kartenstrukturen
- endgültige Grafik und Assets
- finales Inventar-UI
- Storysystem
- Sprecher-/Vertonungssystem
- dynamische Musik
- Fahrzeuge
- Begleiter
- Siedlungs-Systeme
- Bunker-Inhalte
- Events
- vollständiges Crafting
- Recycler und Schmelzer
- Nahrungs- und Getränkesystem
- Skill- und Fortschrittssysteme
- datengetriebene Spielinhalte über .db-Dateien
- zeitgesteuerter Basis-Ressourcenreset
- späterer Hardware-Kompatibilitätsprüfer

## Wichtige Designentscheidungen

- 30 dauerhaft vorhandene Hauptgebiete
- temporäre Eventgebiete zählen nicht zu den 30 Hauptgebieten
- neue Gebiete werden über Story und Fortschritt freigeschaltet
- Ressourcen und andere platzierbare Inhalte können beim erneuten Betreten neu verteilt werden
- normale Standardgebiete sind ungefähr 200 x 200 Unity-Einheiten groß
- Schwierigkeitssystem für normale Gebiete: Grün, Gelb, Rot und Dunkelrot
- Eventgebiete verwenden eine eigene Kennzeichnung
- Spieleransprache erfolgt in der Du-Form
- zwei Rezept-Anzeigemodi sind geplant: direkt und indirekt
- Materialvarianten werden nur eingeführt, wenn sie spielmechanisch einen echten eigenen Zweck haben
- pro fertigem Produkt sind maximal **5 Abhängigkeiten / Verarbeitungsschritte** vorgesehen
- Schaden und Effektstärken werden grundsätzlich als **ganze Zahlen** behandelt
- Schrott wird später im Recycler in Kernmaterialien zerlegt; Metallreste können anschließend im Schmelzer weiterverarbeitet werden
- C# soll langfristig primär die Spielmechanik enthalten; veränderliche Spieldaten sollen möglichst in modularen .db-Dateien liegen
- größere Events sollen jeweils eigene, leicht austauschbare Event-Datenbanken erhalten
- Spieldatenbanken und Spielstände werden strikt getrennt
- Storytexte sollen später optional vertont werden; adaptive Hinweise können gesprochen werden
- finale Musik und Sprecherstimmen kommen erst in einer späten Entwicklungsphase
- der aktuelle Build-Charakter entspricht eher einem Prototyp / einer Pre-Demo als einer Beta
- alte Demo-/Testobjekte müssen nicht zwingend entfernt werden; sie können später bewusst als Storyelemente weiterverwendet werden

## Geplante Datenarchitektur

Langfristig gilt als Leitprinzip:

**C# = Logik und Systeme**  
**.db = Inhalte, Werte, Zuordnungen und Abläufe**

Beispiele:
- Items und Ressourcen
- Rezepte und Zutaten
- Werkbänke und Produktionszeiten
- Lootpools und Wahrscheinlichkeiten
- Gebietsressourcen und Spawnwerte
- Gegnerwerte
- Händler
- Fahrzeuge
- Freischaltungen
- Quests und Storydaten
- Events und Eventphasen
- Dialoge und Sprecherzuordnungen
- Balancewerte

## Aktueller Fokus

**Die Ressourcen-Grundkonfiguration und die grundlegenden Gebäudetests sind erledigt. Als nächstes werden die noch fehlenden Kernmechaniken technisch einzeln geprüft. Der Lootkisten-Grundtest ist bestanden; als nächstes soll die Kiste ein eigenes Mini-Inventar erhalten.**

Große Inhaltsmengen wie Lootpools, Items, Events und Rezepte sollen später nicht im C#-Code gepflegt werden, sondern aus modularen .db-Dateien kommen. C# bleibt dabei die Logik- und Vermittlungsschicht.
