# Entwicklungsstand

**Stand:** 29.09.2026

## Aktuelle Entwicklungsphase

Der aktuelle Schwerpunkt liegt auf den festen Gebieten: Ressourcen, Spawnregeln und erste Gebiets-Balance.

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

Damit sind aktuell **12 von 30** festen Gebieten bei der Ressourcen-Grundkonfiguration eingerichtet.

### Als Nächstes
- weitere Kältegebiete: Schneefeld und Frostgebiet
- danach Küsten- und Inselgebiete
- anschließend weitere Spezial- und Storygebiete nach Bedarf

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

- Holz
- Stein
- Hanf
- Kohle
- Eisen
- Moos
- Beeren

### Als Nächstes geplant
Für die Kältegebiete sind als typische Ressourcen unter anderem vorgesehen:
- Schnee
- Eis
- Harz
- Tannenzapfen
- Tannennadeln
- Winterkraut

Später zusätzlich:
- Sand
- Kies
- weitere gebietsspezifische Ressourcen

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
- Kalter_Waldrand: Standardressourcen plus Beeren
- Schneefeld: noch offen
- Frostgebiet: noch offen

## Noch nicht vollständig umgesetzt

- Lootkisten mit echten Lootpools
- Gegner-Spawning pro Gebiet
- Gebäude und Ruinen
- endgültige Grafik und Assets
- Storysystem
- Fahrzeuge
- Begleiter
- Siedlungs-Systeme
- Bunker-Inhalte
- Events
- vollständiges Crafting
- Nahrungs- und Getränkesystem
- Skill- und Fortschrittssysteme

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

## Aktueller Fokus

**Zuerst werden die Gebiete technisch und spielerisch aufgebaut. Hochwertige Grafik und finale Assets kommen später.**

Neue Ideen werden gesammelt, aber nicht automatisch sofort umgesetzt, wenn sie nicht zur aktuellen Entwicklungsphase gehören.
