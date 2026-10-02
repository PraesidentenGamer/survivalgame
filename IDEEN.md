# Ideenliste

Diese Datei sammelt Ideen und spätere Designrichtungen für das Survival-Game-Projekt.

Wichtig: Eine Idee auf dieser Liste bedeutet **nicht**, dass sie sofort umgesetzt wird. Neue Vorschläge werden gesammelt, damit der aktuelle Entwicklungsblock nicht ständig unterbrochen wird.

## Ideen-Parkplatz und Arbeitsregel

- neue Vorschläge von Freunden/Mitarbeitern werden hier bzw. im vorgesehenen GitHub-Ideenbereich gesammelt
- aktuelle Pflichtsysteme werden zuerst fertig geplant und umgesetzt
- Ideen werden später gesammelt geprüft: übernehmen, verändern, verschieben oder ablehnen
- vorbereitete Funktionen dürfen bereits technisch vorgesehen sein, ohne sofort aktiv zu werden
- mögliche spätere Inhalte können im Spiel als **„Kommt bald“** oder **„geplant“** erscheinen, ohne als festes Versprechen zu gelten

## Vorgemerkte spätere Inhalte

### Y-Haus-Gebiet
- besonderer Wohnkomplex nach persönlicher Inspiration
- Grundlage: historisches Y-Haus in Hoyerswerda sowie ähnliche Y-Haus-Komplexe als zusätzliche Orientierung
- kein 1:1-Nachbau nötig
- mögliche feste Karte oder späterer Event-/Storyort
- Innenhof, Treppenhäuser, Keller, Dächer und Wohnbereiche frei gestaltbar
- Wintervariante besonders passend

### Fahrzeugidee: Trabant 601
- als spätere Fahrzeugidee vorgemerkt
- frühes bis mittleres Fahrzeug
- eher einfach zu reparieren
- konkrete Werte und rechtliche/gestalterische Umsetzung später prüfen
- alternativ eigenständiges, klar inspiriertes Fahrzeugdesign

### Schwierigkeit
- erste Veröffentlichung nur **Normal / Ausgeglichen**
- später eventuell **Leicht**
- später eventuell **Hardcore**
- Schwierigkeitsprofile sollen über eigene .db-Dateien steuerbar sein
- neue Modi erst nach echtem Spielerfeedback aktivieren

### Multiplayer
- späteres Multiplayer-System nach dem Grundprinzip einer hostbaren gemeinsamen Welt
- Singleplayer bleibt vollständig unabhängig
- Freunde können später beitreten
- optional dedizierter Server
- Architektur wird früh so vorbereitet, dass Multiplayer nicht komplett neu aufgebaut werden muss

### Update-System
- ZIP-basierte Updates
- separater Updater
- Backup/Restore der zu ersetzenden Dateien
- Rollback bei Fehler
- SHA-256-Prüfung möglich
- neue Funktionen können über Feature-Flags und Abhängigkeiten vorbereitet werden
- Spielgröße ist noch völlig offen; Update-System darf keine festen Größenannahmen treffen

### Ressourcen und Überleben
- Moos als vielseitige Ressource
- Sand und Kies als alternative Filtermaterialien
- Sand + Kies zusammen erhöhen das Filtertempo
- Natur-Wasserfilter reicht vorläufig für 6 Flaschen Wasser
- Salz bei Küstengebieten insbesondere im Hafen
- Schrott als allgemeine Recycling-Ressource

### Chemie und Dekontamination
- Allgemeine Chemikalien als universeller Chemie-Grundstoff
- Chlor als konkreter Spezialstoff
- Salpetersäure für besondere Reinigungs-/Dekontaminationsrezepte
- Industriereiniger
- Dekontaminationsmittel
- Dekontaminationsdusche entfernt vorgesehene negative Umwelt-/Kontaminationseffekte
- Chemisches Reinigungsbecken für verseuchte Kisten
- gereinigte verseuchte Kiste verschwindet, sobald sie vollständig geleert wurde

### Materialvarianten
Grundregel:
- Materialien bleiben grundsätzlich in einer einfachen Grundform
- zusätzliche Varianten nur bei echtem spielmechanischem Zweck
- keine unnötigen Varianten nur wegen Optik oder Herkunft
- Stahl bleibt ein einziges normales Material
- Panzerglas ist höchste Glasstufe und extrem stabil; genaue Werte später

### Händler
- neutraler/friedlicher Sonder-NPC
- pro Erscheinen immer genau 3 verschiedene gesuchte Ressourcen
- Anforderungen bleiben bis zum nächsten Erscheinen gleich
- vollständige Lieferung gibt normale Belohnung plus mögliche Bonusbelohnung
- eigener Händler-Loot-/Bonuspool
- Händlerposition kann zwischen vorbereiteten Punkten rotieren
- Händlergebiet ohne normale Zombie-/Feindspawns
- einige normale Ressourcen dürfen dort vorkommen
- bei Angriff verteidigt sich der Händler nur in seiner Reichweite
- Händler stoppt spätestens bei 10 Restleben des Spielers
- Handel bleibt bis zum erneuten Betreten des Gebiets gesperrt

### Eventgebiete
- Spieler bleibt bei Offlinegehen im Eventgebiet gespeichert
- Eventgebiet bleibt bestehen, solange der Spieler noch darin ist, auch wenn der Timer abläuft
- Gegner bleiben aktiv
- erst nach Verlassen wird ein abgelaufenes Eventgebiet entfernt
- stirbt der Spieler danach in einem nicht mehr erneut erreichbaren Eventgebiet, behält er sein Inventar
- unfairer unerreichbarer Inventarverlust soll notfalls vollständig erstattet und zusätzlich entschädigt werden

### Eventideen
- 1.-April-Event
- Sommer-Event
- Herbst/Halloween
- Weihnachten
- Flugzeugabsturz als kleines temporäres Mini-Event
- „Gleich eins aufs Maul“ als kampforientiertes Event
- Bossidee „Gleich eins aufs Maul“ mit Spezialangriff „Superschlag“

### Weltkarte
- Hauptressourcen und mögliche Beute beim Gebiet anzeigen
- nicht den kompletten Lootpool offenlegen
- Schwierigkeiten Grün/Gelb/Rot/Dunkelrot
- Eventgebiete mit eigener Kennfarbe
- temporäre Eventmarker mit Timer
- gesperrte und versteckte Gebiete
- ungefähr 30 dauerhafte Hauptgebiete langfristig vorgesehen

### Siedlung
- eigener großer Mechanikbereich
- eigene Ressourcen, Lager, Strom, Wasser, Produktion und Gebäude
- Spezialgebäude maximal einmal pro Typ
- Gebäude bis Level 3
- NPC-Kapazität pro Gebäude direkt an Gebäudestufe gekoppelt
- eigene Expeditionen
- Verteidigung und Sicherheitszentrum
- große Kraftwerke als spätere Siedlungs-/Endgame-Systeme

### KI und NPC
- gemeinsame KI-Basis für Gegner, Tiere, NPCs und Begleiter
- Dialoge und Sprachausgabe später
- NPCs können später folgen, warten, arbeiten, sammeln, transportieren und bewachen
- wichtige NPCs dauerhaft/unverwundbar, sofern für ihre Rolle nötig

### Story und Hinweise
- Hauptstory und Nebenstory getrennt
- Story soll großen Anteil am Spiel haben
- Tschernobyl zunächst scheinbarer Ursprung; spätere größere Ursache bleibt offen
- Hinweise über Dokumente, Funk, Datenträger, Computer, Storyorte und Prototypen
- Sarah zunächst freundlich/vertrauenswürdig, spätere Fassade möglich
- fiktive Forschungs-/Militärorganisation als mögliche Hintergrundspur

### Forschung und Prototypen
- Forschungsstation
- High-End-Forschungsstation
- Forschungs-/Prototypenstation
- Prototypenmodul als experimenteller Forschungsgegenstand
- Prototypenwaffen und Spezialtechnik später
- Besitzlimits dürfen bei Belohnungen überschritten werden

### Fahrzeuge
- Motorrad
- Jeep
- gepanzertes Fahrzeug
- Hovercraft
- Speedboot
- Helikopter
- Panzer als spätere schwere Stufe
- mobiles Endstufen-Labor/Fahrzeug mit eigenem Design
- Trabant 601 als zusätzliche Fahrzeugidee

### Musik und Grafik
- realistische/glaubwürdige Optik
- Musik, Umgebungsgeräusche und Texturen sind für die erste vollständig spielbare Version Pflicht
- finale hochwertige Assets dürfen trotzdem später weiter verbessert werden
- klare Asset- und Dateistruktur
- Platzhalter und finale Assets getrennt verwalten

## Grundregel

Das Spiel soll schwierig sein dürfen, aber nicht unfair. Verluste sollen nur dann hart sein, wenn der Spieler grundsätzlich eine reale Chance hat, sie wieder auszugleichen oder zurückzuholen.
