# Entwicklungsstand

**Stand:** 01.10.2026

## Aktuelle Entwicklungsphase

Der Schwerpunkt liegt auf den Kernsystemen für Inventar, Container und Basis. Ressourcen-Grundkonfiguration und grundlegende Gebäudetests sind abgeschlossen. Finale Grafik, hochwertige Assets und Endstufen-Systeme kommen später.

## Aktuelle Designplanung

Parallel zur technischen Entwicklung wird derzeit das Werkbank-/Produktionssystem vollständig festgelegt.

Bereits festgelegt bzw. vorgemerkt:
- einfache Gegenstände dürfen teilweise direkt hergestellt werden; Werkbänke sind vor allem für komplexe oder spezialisierte Herstellung vorgesehen
- Produktionsketten sollen höchstens etwa 5 Verarbeitungsschritte besitzen
- schwere Maschinen benötigen geeigneten/festen Boden und Strom
- Kreissäge gestrichen; das Sägewerk übernimmt die komplette Holzverarbeitung
- Sägewerk vorläufig 3 Stufen und für größere Produktionsmengen vorgesehen
- Steinbearbeitungsstation 3 Stufen
- Metallwerkbank 4 Stufen
- Schmelzofen 4 Stufen
- Schmiede 4 Stufen
- Bauwerkbank 4 Stufen
- Betonmischer 4 Stufen
- Glaswerkbank 3 Stufen
- Werkzeugwerkbank 4 Stufen
- Waffenwerkbank 5 Stufen
- Rüstungswerkbank 4 Stufen
- Schneiderei/Gerberei werden unter **Schneider** zusammengeführt
- **Webstuhl** bleibt als eigene Spezialstation und dient später zum Übertragen besonderer Effekte auf Kleidung/Rüstung
- allgemeine Reparaturstation statt separater Schweißstation
- Elektronikwerkbank 5 Stufen
- Batteriewerkbank 4 Stufen
- Elektrostation 4 Stufen
- Generatorwerkstatt 4 Stufen
- Kochstation 4 Stufen
- Fleisch-/Tierverarbeitung wird unter **Metzger** zusammengeführt; der Metzger übernimmt grundsätzlich alles, was mit tierischen Rohstoffen zu tun hat
- Landwirtschaftsstation 4 Stufen
- Wasseraufbereitung 4 Stufen
- Medizinische Station 4 Stufen
- **Klinik** als späteres Siedlungsgebäude zur Behandlung vorgesehen
- Chemielabor 4 Stufen
- Pharmazeutische Station wird zur **Apotheke**

Weitere neue Designpunkte:
- spezielle verschlossene Lootkisten sollen bestimmte Skills bzw. Skillstufen voraussetzen
- Tageslänge soll voraussichtlich vom Spieler wählbar sein, bis hin zu **1 Ingame-Tag = 24 Stunden Echtzeit**
- starke Elektrowaffe mit wiederaufladbaren Akkus ist vorgesehen
- leere Waffenakkus behalten eine kleine Notreserve, damit die Waffe nach einer Wartezeit noch einmal genutzt werden kann
- Basis-PC soll später GEAM OS als spielinternes Computersystem verwenden
- Datenwiederherstellung, Entschlüsselung und ähnliche Story-Minispiele sollen unter anderem am Basis-PC stattfinden
- Storyidee um Sarah: zunächst freundliche und hilfreiche Figur, deren Verhalten später als Fassade entlarvt werden kann
- mögliche Storyspur um eine fiktive amerikanische Forschungs-/Militärorganisation und deren Verbindung zum Ausbruch
- klare Sprachregel für alle Spieltexte: verständliches Standarddeutsch, keine vulgären Beleidigungen, keine unnötig derbe Sprache

## Aktueller Teststand

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
- Lootkiste als physisches Hindernis, aktuelle Testgröße 1.2 / 1.5 / 0.8
- eigenes Kisten-Mini-Inventar
- einzelne Items nehmen
- Alles nehmen
- Spieler -> Kiste: Mengenübertragung
- Spieler -> Kiste: kompletter ausgewählter Stack mit Alles einlagern
- Stack- und Kapazitätsgrenzen
- geschlossene Kiste blockiert Einlagerung
- geöffnete Kiste erlaubt Einlagerung

Die aktuelle Container-GUI ist noch eine technische Demo und wird später ersetzt.

## Container-/Inventarsystem

Zielaufbau der finalen Oberfläche:
- links: Spielerinventar
- oben links: INVENTORY
- Tasche und Rucksack
- unten links: NUTZEN und AUFTEILEN sowie weitere Spieleraktionen
- rechts: aktuell geöffneter Container, z. B. Lootkiste, Gegner oder später andere Container
- Transfer über Mengen-Slider
- ALLE NEHMEN
- ALLES EINLAGERN

Die Transferlogik soll für alle Container gemeinsam verwendet werden.

## Lootkisten

- Loot wird einmal erzeugt und bleibt in der Kiste.
- Kein erneutes Würfeln beim späteren Öffnen.
- Einzelne Mengen können entnommen werden.
- Ein kompletter ausgewählter Stack kann mit Alles nehmen entnommen werden.
- Normale Kisten dürfen grundsätzlich auch als Lager für eigene Gegenstände verwendet werden.
- Eine spätere Option soll festlegen können, ob leere gelootete Kisten automatisch gesperrt werden.
- Große Lootpools werden später datengetrieben über .db-Dateien verwaltet.
- C# kennt langfristig nur die Logik bzw. Pool-ID; Inhalte, Mengen und Chancen liegen in den Datenbanken.

## Startbasis

Die gezeigte Grundbase ist nur der Startzustand und kann vollständig umgebaut werden.

### Abreißbar
- Boden
- Wände
- Türen
- Fenster
- sonstige normale Bauteile

### Grundobjekte
Grundobjekte innerhalb der Basis sind nicht zerstörbar. Sie können aufgenommen/eingelagert und später wieder herausgenommen und neu platziert werden. Beispiel: Spind.

### Defekter Pickup
- dauerhaft vorhanden
- nicht abreißbar
- nicht verschiebbar
- nicht einlagerbar
- dauerhaft als kleines erstes Lager nutzbar

### Abriss
Beim Abriss werden **25 % der Ressourcen der aktuell verbauten Ausbaustufe** zurückgegeben. Das gilt für alle Ausbaustufen und abreißbaren Bauteile.

Bei einer Ressourcenberechnung wird auf die nächste ganze Ressource aufgerundet. Teilressourcen existieren im Inventar nicht.

### Erste Holzstufe
Aktuelle Referenz:
- Holzboden: Haltbarkeit 6, Kosten 1 Holz
- Holzwand: Haltbarkeit 6, Kosten 1 Holz
- Holztür: Haltbarkeit 6, Kosten 1 Holz
- Holzfenster: Haltbarkeit 6, Kosten 1 Holz

## Zahlenregeln

Grundsätzlich werden Spielwerte bewusst einfach gehalten.

### Standard
Nur ganze Zahlen bei:
- Ressourcen
- Inventarmengen
- Baukosten
- Händlerpreisen
- Käufen
- Tauschmengen
- XP
- Haltbarkeit
- Schaden
- Kapazitäten
- Belohnungen

### Ausnahme
Leben, Hunger und Durst/Wasser dürfen ganze Zahlen oder 0,5er-Schritte verwenden.

### Negative Werte
Negative Werte sind nur bei ausdrücklich vorgesehenen negativen Effekten erlaubt, z. B. Kältegebiet mit falscher Kleidung.

Die Spielregeln stehen über mathematischen Rundungsregeln.

## Nächste Programmier-Schritte

1. Gemeinsames zweigeteiltes Inventar-/Container-UI bauen.
2. Spielerinventar links mit Tasche/Rucksack und den Aktionen NUTZEN/AUFTEILEN.
3. Rechten Containerbereich verallgemeinern, damit Kiste, Gegner usw. dasselbe System verwenden.
4. Mengen-Slider für beide Transferrichtungen endgültig einbauen.
5. ALLE NEHMEN und ALLES EINLAGERN finalisieren.
6. Pickup als stationäres Mini-Lager anbinden.
7. Grundobjekte der Basis einlagerbar und wieder platzierbar machen.
8. Bausystem für Boden, Wände, Türen, Fenster und weitere Bauteile.
9. Abrisssystem mit 25-%-Rückerstattung der aktuellen Ausbaustufe.
10. Danach Gegner-Spawning, Crafting/Werkbänke, Hunger/Wasser, Temperatur, Strahlung/Infektion und weitere Kernsysteme einzeln umsetzen und testen.

## Datenarchitektur

**C# = Logik und Systeme**  
**.db = Inhalte, Werte, Zuordnungen und Abläufe**

Geplante Datenbereiche:
- Items/Ressourcen
- Rezepte
- Werkbänke/Produktionszeiten
- Lootpools
- Gebietsressourcen
- Gegner
- Händler
- Fahrzeuge
- Freischaltungen
- Quests/Story
- Events
- Dialoge
- Balancewerte

Spieldatenbanken und Spielstände bleiben getrennt.

## Gebietsstand

Geplant und grundkonfiguriert: **30 dauerhaft vorhandene Hauptgebiete**. Temporäre Eventgebiete zählen nicht dazu.

Die bisher festgelegten Gebiets-, Ressourcen-, Story-, Fahrzeug-, Siedlungs- und weiteren Langzeitideen bleiben Bestandteil der Roadmap und werden schrittweise umgesetzt.
