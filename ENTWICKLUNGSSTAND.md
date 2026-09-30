# Entwicklungsstand

**Stand:** 30.09.2026

## Aktuelle Entwicklungsphase

Der aktuelle Schwerpunkt liegt weiterhin auf den festen Gebieten: Ressourcen, Spawnregeln und erste Gebiets-Balance. Die finale Grafik, Vertonung und weitere Endstufen-Systeme kommen bewusst später.

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

Damit sind aktuell **19 von 30** festen Gebieten bei der Ressourcen-Grundkonfiguration eingerichtet.

### Als Nächstes
- Forschungsanlage
- weitere Spezial-, Story- und Industriegebiete
- Insel und übrige noch offene Gebiete
- anschließend repräsentative Tests und später ein automatischer Gebiets-/Spawn-Validator

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

### Stadt- und Ruinengebiete
- Verlassene_Stadt: Schrott 10-20
- Stadtruinen: Schrott 20-30
- Verlassene_Einrichtung: Schrott 15-25, natürliche Ressourcen knapp

## Noch nicht vollständig umgesetzt

- Lootkisten mit echten Lootpools
- Gegner-Spawning pro Gebiet
- Gebäude und Ruinen
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
- Moos wird als vielseitige Ressource verwendet
- Natur-Wasserfilter: Sand **oder** Kies genügt; beides zusammen erhöht das Filtertempo
- ein Natur-Wasserfilter reicht vorläufig für 6 Flaschen Wasser
- Beeren können direkt gegessen und später weiterverarbeitet werden
- ein geplanter Wintertee kann zeitlich begrenzten Kälteschutz geben
- Holz und Stein bleiben auch in Kältegebieten normale Ressourcen; Unterschiede entstehen später hauptsächlich durch Modelle und Texturen
- Materialvarianten werden nur eingeführt, wenn sie spielmechanisch einen echten eigenen Zweck haben, z. B. Glas und kugelsicheres Glas oder Reifen und kugelsichere Reifen
- pro fertigem Produkt sind maximal **5 Abhängigkeiten / Verarbeitungsschritte** vorgesehen
- Schrott wird später im Recycler in Kernmaterialien zerlegt; Metallreste können anschließend im Schmelzer weiterverarbeitet werden
- C# soll langfristig primär die Spielmechanik enthalten; veränderliche Spieldaten sollen möglichst in modularen .db-Dateien liegen
- größere Events sollen jeweils eigene, leicht austauschbare Event-Datenbanken erhalten
- Spieldatenbanken und Spielstände werden strikt getrennt
- Storytexte sollen später optional vertont werden; adaptive Hinweise können bei festhängenden Spielern ebenfalls gesprochen werden
- finale Musik und Sprecherstimmen kommen erst in einer späten Entwicklungsphase
- der aktuelle Build-Charakter entspricht eher einem Prototyp / einer Pre-Demo als einer Beta

## Geplante Datenarchitektur

Langfristig gilt als Leitprinzip:

**C# = Logik und Systeme**  
**.db = Inhalte, Werte, Zuordnungen und Abläufe**

Beispiele für Datenbank-Inhalte:
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

Die Datenbanken sollen modular aufgebaut sein, damit Updates einzelne .db-Dateien ersetzen können, ohne unnötig die komplette Spiellogik anzufassen.

## Aktueller Fokus

**Zuerst werden die Gebiete und Kernmechaniken funktional aufgebaut. Hochwertige Grafik, finale Assets, Musik, Sprecherstimmen und der Hardware-Kompatibilitätsprüfer kommen später.**

Neue Ideen werden gesammelt und architektonisch berücksichtigt, aber nicht automatisch sofort umgesetzt, wenn sie nicht zur aktuellen Entwicklungsphase gehören.
