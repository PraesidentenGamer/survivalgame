# Ideenliste

Diese Datei sammelt Ideen und bereits festgelegte spätere Designrichtungen für das Survival-Game-Projekt.

Wichtig: Eine Idee auf dieser Liste bedeutet **nicht**, dass sie sofort umgesetzt wird. Der aktuelle Entwicklungsabschnitt hat Vorrang.

## Vorgemerkt

### Ressourcen und Überleben
- Moos als vielseitige Ressource
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

Beispiele:
- Glas -> kugelsicheres Glas
- Reifen -> kugelsichere Reifen

### Crafting und Produktionsketten
- zwei Rezept-Anzeigemodi: direkt und indirekt
- maximal **5 Abhängigkeiten / Verarbeitungsschritte** pro fertigem Produkt
- unnötige Zwischenprodukte vermeiden
- normale Produkte sollen meist deutlich kürzere Ketten haben

### Recycler und Schmelzer
- Schrott wird im Recycler zerlegt
- Ergebnisse über Wahrscheinlichkeiten und Mengenbereiche
- mögliche Kernmaterialien: Eisenreste, Kupferreste, Aluminiumreste, Elektronikteile
- Metallreste können anschließend im Schmelzer weiterverarbeitet werden

### Datenbank-Architektur
**C# enthält die Mechanik. Datenbanken enthalten Spielinhalte, Werte und Abläufe.**

Geplante Datenbereiche:
- Items
- Ressourcen
- Rezepte
- Werkbänke
- Produktionszeiten
- Recycler-Ausbeuten
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

Größere Events sollen möglichst eigene .db-Dateien erhalten, z. B.:
`Datenbanken/Events/Gleich_eins_aufs_Maul_Event.db`

Updates sollen einzelne Datenbanken gezielt ersetzen können. Spielstände bleiben strikt getrennt.

### Gegner-Idee: Maunzi
- Typ: Gegner
- Name: Maunzi
- Spezialangriff / Spruch: **„Ich bin Maunzi“**
- Vorkommen: noch offen; Gebiete und/oder Event
- Spruchschaden: zufällig **0 bis 35** Lebenspunkte
- Schwäche: besonderer Gegenstand / besondere Waffe **Busfahrer „Kalle“**
- Schaden durch Kalle: zufällig **0 bis 50** Lebenspunkte pro Treffer
- Kalle kann über Loot, Events oder andere Fundmöglichkeiten erhalten werden
- Schaden und Effektwerte grundsätzlich nur als ganze Zahlen

### Skill-Idee: Gutes Auge
Mehrstufige Fähigkeit zum leichteren Auffinden von Ressourcen.

Grundidee:
- Stufe 1: Ressourcen in kleinem Umkreis werden sichtbar / hervorgehoben
- Stufe 2: größerer Erkennungsradius
- Stufe 3: nochmals größerer Erkennungsradius
- genaue Radien werden später balanciert
- optional können höhere Stufen seltene oder versteckte Ressourcen besser erkennen
- Ressourcen sollen nicht automatisch durch jede Wand permanent sichtbar werden
- Umsetzung später über das Skill-System und idealerweise datengetrieben

### Story, Sprecher und Hinweise
- Story soll nicht ausschließlich über lange Lesetexte vermittelt werden
- Erzähler / Sprecher für wichtige Storyabschnitte
- Untertitel parallel zur Sprachausgabe
- adaptive gesprochene Hinweise, wenn ein Spieler bei Suchaufgaben lange nicht weiterkommt
- alternative Hinweisfunktion auf Anfrage
- Sprecherstimmen erst sehr spät endgültig erzeugen oder aufnehmen

### Lesbare Dokumente und Umwelt-Storytelling
- gefundene Dokumente sollen teilweise vollständig lesbar sein
- mögliche Typen:
  - interne Berichte
  - E-Mails
  - Versuchsprotokolle
  - Einsatzbefehle
  - Wartungsberichte
  - handschriftliche Notizen
  - Lieferscheine
  - Sicherheitsmeldungen
  - Evakuierungsbefehle
  - geschwärzte oder beschädigte Dokumente
- Dokumente können Zugangscodes, Koordinaten, Hinweise und zusätzliche Story enthalten
- storykritische Informationen sollen nicht ausschließlich vom Lesen optionaler Dokumente abhängen
- Dokumente sollen später ebenfalls datengetrieben verwaltet werden können

### Alte Demo- und Testobjekte als Storyelement
- frühe Platzhalterobjekte müssen nicht vollständig entfernt werden
- ausgewählte Demo-Objekte können bewusst im fertigen Spiel erhalten bleiben
- mögliche Story-Erklärung:
  - alte Testsektoren
  - Trainings- oder Versuchsanlagen
  - frühe Prototypen
  - beschädigte Gebäude
  - vernichtete oder teilweise vernichtete Beweise
- Vertuschungs-Idee:
  - Einrichtungen wurden absichtlich beschädigt oder geräumt
  - verbrannte Akten
  - zerstörte Terminals
  - zugemauerte / gesprengte Zugänge
  - zurückgelassene Versuchstechnik
- Spieler kann nach und nach erkennen, dass bestimmte Schäden nicht nur vom Ausbruch stammen
- Verbindung zu Forschungsanlage, Bunkern und der größeren Ursprungsgeschichte möglich

### Genre-Mischung
Das Spiel soll bewusst mehrere Bereiche verbinden:
- Survival
- Erkunden
- Bauen
- Crafting
- Looting
- Story
- Progression
- Events
- Horror / Bedrohungsatmosphäre

Horror soll eher über Atmosphäre, Unsicherheit, verlassene Anlagen, Dokumente, Spuren und unbekannte Hintergründe entstehen und nicht ausschließlich über Jumpscares.

### Gebäude
- aktuelle Demo-Gebäude dienen nur technischen Tests
- echte Gebäude sollen deutlich größer werden
- Eltern-/Kindobjekte werden genutzt, um Gebäude sauber zu strukturieren
- normale Türen sollen grundsätzlich in beide Richtungen geöffnet werden können
- besondere Türtypen wie Schiebe-, Garagen-, Bunker- oder Sicherheitstüren erhalten eigene Mechaniken
- `Prefab_Gebaeude_Test_01` soll als technisches Relikt aufgehoben werden und kann später Storyzweck bekommen

### Firmen, Marken und Namen
- allgemeine Begriffe können normal verwendet werden
- für klar geschützte oder eindeutig zuordenbare reale Firmen-/Markennamen sollen eigene fiktive Namen entwickelt werden
- eigene Firmen erhalten nach Möglichkeit eigene Logos, Farben, Produkte und Hintergrundgeschichten
- konkrete fiktive Namen werden vor finaler Verwendung noch geprüft

### Musik
- instrumentale Stücke
- situationsabhängig, z. B. Erkundung, Kampf, Gefahr, Boss, Horde, Story
- weiche Übergänge
- finale Musikproduktion erst spät

### Basis, Siedlung und Ressourcen-Reset
- Siedlung ist eine Ausnahme und erhält keine normalen zufälligen Grundressourcen
- Test_Basis und Zweite_Basis besitzen natürliche Grundressourcen
- späterer Ressourcenreset nur auf freien Flächen
- gebaute Objekte bleiben unverändert
- genaue Reset-Zeit später festlegen

### Entwicklungs- und Build-Bezeichnung
- aktueller Zustand entspricht eher Prototyp / Pre-Demo als Beta
- mögliche spätere Build-Bezeichnung: `SurvivalGame_Pre-Demo_v0.0.001_Build00025.exe`

### Späte Entwicklungsphase
- finale Modelle, Texturen, Effekte und UI erst nach funktionaler Fertigstellung
- Musik und Sprecherstimmen ebenfalls spät
- Hardware-Kompatibilitätsprüfer erst gegen Ende

## Ideen-Parkplatz

Neue Vorschläge können hier gesammelt werden, auch wenn sie erst viel später geprüft oder umgesetzt werden.

So bleibt die aktuelle Entwicklung fokussiert, ohne dass Ideen verloren gehen.
