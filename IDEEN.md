# Ideenliste

Diese Datei sammelt Ideen und bereits festgelegte spätere Designrichtungen für das Survival-Game-Projekt.

Wichtig: Eine Idee auf dieser Liste bedeutet **nicht**, dass sie sofort umgesetzt wird. Der aktuelle Entwicklungsabschnitt hat Vorrang.

## Vorgemerkt

### Ressourcen und Überleben
- Moos als vielseitige Ressource
  - Natur-Wasserfilter
  - Gebäudetarnung
  - Dämmmaterial
  - Zunder
  - Notnahrung
  - einfache medizinische Nutzung
  - Kompost / Pflanzenbau
  - Fallentarnung
  - Wasseraufnahme
  - Schlaf- und Füllmaterial
  - Geräuschdämmung
  - Pilzzucht
  - mögliche Torf-Verarbeitung
- Sand und Kies als alternative Filtermaterialien
- Sand + Kies zusammen erhöhen das Filtertempo
- Natur-Wasserfilter reicht vorläufig für 6 Flaschen Wasser
- Salz soll bei den aktuellen Küstengebieten nur im roten Gebiet Hafen vorkommen
- Schrott als allgemeine Recycling-Ressource

### Materialvarianten
Grundregel:
- Materialien bleiben grundsätzlich in einer einfachen Grundform
- zusätzliche Varianten nur dann, wenn sie spielmechanisch wirklich einen eigenen Zweck haben
- keine zusätzlichen Varianten nur wegen Optik, Herkunft oder Gebiet

Beispiele für sinnvolle Varianten:
- Glas -> kugelsicheres Glas
- Reifen -> kugelsichere Reifen

Beispiele für bewusst einfache Grundformen:
- Holz bleibt Holz
- Stein bleibt Stein
- Sand bleibt Sand
- Schrott bleibt Schrott, solange verschiedene Schrottarten keinen eigenen spielmechanischen Zweck haben

### Kältegebiete
Typische natürliche Ressourcen:
- Schnee
- Eis
- Harz
- Beeren
- Tannenzapfen
- Tannennadeln
- Winterkraut

Grundressourcen wie Holz und Stein bleiben normale Items. Für kalte Gebiete reichen später passende Modelle, Materialien und Texturen; eigene Varianten wie Frostholz oder Froststein sind nicht nötig.

### Beeren und Wintertee
- Beeren können direkt gegessen werden
- Beeren können später zu Lebensmitteln weiterverarbeitet werden
- Beeren können für Tee verwendet werden
- Wintertee kann aus passenden Zutaten wie Beeren, Tannennadeln und Wasser entstehen
- Wintertee soll zeitlich begrenzten Kälteschutz geben
- Getränke ersetzen passende Winterkleidung nicht vollständig, sondern dienen als Zusatz- oder Notlösung

### Crafting und Produktionsketten
- Zwei Rezept-Anzeigemodi:
  - Direkt: Materialien, Mengen und Station werden vollständig angezeigt
  - Indirekt: Spieler muss benötigte Materialien selbst herausfinden
- Freigeschaltete Rezepte sollen in einem Rezept- oder Wissensbuch nachsehbar sein
- Story-Schlüsselrezepte sollen auch im indirekten Modus genügend Hinweise erhalten
- ein fertiges Produkt soll maximal **5 Abhängigkeiten / Verarbeitungsschritte** haben
- normale Produkte sollen meist deutlich unter dieser Grenze bleiben
- unnötige Zwischenprodukte vermeiden
- Beispiel für kurze Kette: Sand -> Glas -> Fenster
- Beispiel für komplexere Kette: Schrott -> Metallreste -> Barren -> Metallplatte -> Fahrzeugteil

### Recycler und Schmelzer
- Recycler als wichtige Werkbank / Produktionsstation
- Schrott wird dort zerlegt
- Ergebnisse können über Wahrscheinlichkeiten und Mengenbereiche bestimmt werden
- mehrere Ergebnisse können gleichzeitig entstehen
- mögliche Kernmaterialien:
  - Eisenreste
  - Kupferreste
  - Aluminiumreste
  - Elektronikteile
- Metallreste werden bei Bedarf im Schmelzer zu verwendbaren Metallen oder Barren verarbeitet
- Recycler und Schmelzer bleiben getrennte Systeme
- spätere Recycler-Upgrades können Ausbeute oder seltene Rückgewinnungen beeinflussen

### Datenbank-Architektur
Langfristiges Leitprinzip:

**C# enthält die Mechanik. Datenbanken enthalten Spielinhalte, Werte und Abläufe.**

Daten, die möglichst in .db-Dateien ausgelagert werden sollen:
- Items
- Ressourcen
- Rezepte
- Zutaten
- Werkbänke
- Produktionszeiten
- Recycler-Ausbeuten
- Wahrscheinlichkeiten
- Lootpools
- Gebietsressourcen
- Gegnerwerte
- Händler
- Fahrzeuge
- Freischaltungen
- Quests
- Storydaten
- Dialoge
- Balancewerte
- Events

Geplante Ordneridee:

```text
Datenbanken
├── Items
├── Crafting
├── Ressourcen
├── Loot
├── Gebiete
├── Events
├── Quests
├── Gegner
├── Haendler
├── Fahrzeuge
├── Dialoge
└── Balance
```

Für größere Events:
- möglichst eigene Datenbank pro Event
- Beispiel: `Datenbanken/Events/Gleich_eins_aufs_Maul_Event.db`
- weitere Events erhalten jeweils eigene .db-Dateien
- Eventdaten können Bedingungen, Phasen, Ziele, Gegner, Loot, Timer, Dialoge und Belohnungen enthalten
- C# stellt nur die allgemeine Event-Engine bereit
- Updates sollen einzelne Datenbanken gezielt ersetzen können
- Spielstände werden strikt von Spieldatenbanken getrennt
- feste IDs statt sichtbarer Namen als technische Referenzen verwenden
- Datenbanken sollen später Versionsinformationen erhalten, z. B. SchemaVersion, ContentVersion und MinimumGameVersion

### Gegner-Idee: Maunzi
- Typ: Gegner
- Name: Maunzi
- charakteristischer Spruch / Spezialangriff: **„Ich bin Maunzi“**
- Vorkommen: noch offen; normale Gebiete und/oder Events möglich
- Spruchschaden: zufällig **0 bis 35** Lebenspunkte
- Schwäche: Angriff mit dem besonderen Gegenstand / der besonderen Waffe **Busfahrer „Kalle“**
- Schaden durch Kalle: zufällig **0 bis 50** Lebenspunkte pro Treffer
- Busfahrer „Kalle“ soll über Loot, Events oder andere Fundmöglichkeiten erhältlich sein
- Lebenspunkte, Reichweite, Abklingzeit, Spawnrate und eigener Loot werden später festgelegt
- Schaden und Effektwerte werden grundsätzlich nur als ganze Zahlen gespeichert und berechnet

### Story, Sprecher und Hinweise
- Story soll nicht ausschließlich über lange Lesetexte vermittelt werden
- Erzähler / Sprecher für wichtige Storyabschnitte
- Untertitel parallel zur Sprachausgabe
- Sprache und Untertitel getrennt ein-/ausschaltbar
- eigener Lautstärkeregler für Sprache
- Story-Sprachausgabe soll überspringbar sein
- mögliche Kategorien:
  - Erzähler
  - NPC-Stimmen
  - Funkdurchsagen
  - Tonaufzeichnungen
  - Hinweise
- adaptive Hinweise, wenn ein Spieler bei einer Suche längere Zeit nicht weiterkommt
- Hinweise können gestuft werden: leicht -> konkreter -> deutlich
- alternativ Hinweis auf Anfrage über Questbuch / Hinweisfunktion
- Sprecherstimmen werden erst sehr spät endgültig erzeugt oder aufgenommen

### Musik
- Musiksystem erst gegen Ende
- instrumentale Stücke
- situationsabhängige Musik, z. B. Erkundung, Kampf, Gefahr, Boss, Horde, Story
- weiche Übergänge / Crossfades
- Kampfmusik soll nicht sofort beim kleinsten Kontakt hektisch wechseln
- finale Musikproduktion erst nach stabiler Spielmechanik und Storystruktur

### Basis, Siedlung und Ressourcen-Reset
- Moos-Tarnung für Wände und andere Bauteile
- getarnte Gebäude sollen von Gegnern erst aus geringerer Entfernung erkannt werden
- Tarnung darf Hordenangriffe nicht vollständig verhindern
- Moos kann eventuell Fallen und kleine Lager tarnen
- Siedlung soll als eigener aufbaubarer Bereich funktionieren
- Test_Basis besitzt bereits als Prototyp natürliche Ressourcen über den AreaSpawnManager
- spätere Basis-Regel:
  - abgebaute natürliche Ressourcen bleiben zunächst weg
  - nach einer festgelegten Zeit kann ein Basis-Ressourcenreset stattfinden
  - nur natürliche Ressourcen werden neu erzeugt
  - Gebäude, Wände, Werkbänke, Lager, Fahrzeuge und andere Spielerobjekte bleiben unverändert
  - Ressourcen dürfen nur auf freien Flächen neu spawnen
- ob der Reset-Timer auf Echtzeit oder aktiver Spielzeit basiert, wird später entschieden
- Basisressourcen sollen normale Ressourcengebiete nicht überflüssig machen

### Fortschritt und Story
- Zweite Basis über Story freischalten
- Siedlung als eigener großer Mechanikbereich
- Hunde als erste Tierbegleiter
- Fahrzeuge und weitere große Systeme erst in späteren Entwicklungsphasen

### Entwicklungs- und Build-Bezeichnung
- aktueller Zustand entspricht eher Prototyp / Pre-Demo als Beta
- mögliche spätere Build-Bezeichnung: `SurvivalGame_Pre-Demo_v0.0.001_Build00025.exe`
- Alpha erst, wenn die Kernmechaniken weitgehend vollständig und grundsätzlich durchspielbar sind
- Beta erst deutlich später mit weitgehend vollständigen Systemen und Fokus auf Fehlerbehebung, Balancing und Feinschliff

### Späte Entwicklungsphase
- finale Modelle, Texturen, Effekte und UI erst nach funktionaler Fertigstellung der Systeme
- Musik und Sprecherstimmen ebenfalls spät
- Hardware-Kompatibilitätsprüfer erst gegen Ende
- geplanter Hardware-Prüfer soll spätere, separat definierte Hardware-Einschränkungen kontrollieren, ohne die aktuelle Kernentwicklung zu blockieren

## Ideen-Parkplatz

Neue Vorschläge können hier gesammelt werden, auch wenn sie erst viel später geprüft oder umgesetzt werden.

So bleibt die aktuelle Entwicklung fokussiert, ohne dass Ideen verloren gehen.
