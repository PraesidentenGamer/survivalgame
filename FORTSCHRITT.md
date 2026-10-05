# Projektfortschritt

**Stand:** 05.10.2026

Diese Datei ist die kompakte Arbeitsübersicht für den aktuellen Projektstand. Sie trennt bestätigte/fertige Datenbankblöcke von noch offenen Werten und späterer Code-Umsetzung.

## Aktueller Schwerpunkt

**Zuerst alle offenen Datenbankwerte und Regeln sauber festlegen, danach Loader/Code weiterbauen.**

Grundregel:
- bestehende Werte erhalten
- spätere ausdrücklich bestätigte Entscheidungen ersetzen ältere Vorschläge
- unbekannte Werte nicht erfinden
- Datenbanken einzeln bearbeiten und validieren
- C# führt die Regeln aus; Verhalten und Balance werden möglichst datengetrieben

## Datenbankstatus

| Bereich | Stand | Offene Punkte |
|---|---|---:|
| Gegner | fertig, 53 Gegner | 0 |
| Gebiete | fertig, 30 dauerhafte Gebiete | 0 |
| Rezepte | fertig | 0 |
| Welt/Reise | fertig | 0 |
| Skills Spieler | fertig, 75 normale Skills + SECRET-System | 0 |
| Forschung | fertig, 133 Knoten | 0 |
| Items | integriert, 326 historische Slots + Systemitems | noch offen |
| Ressourcen | strukturell fertig | 48 |
| Loot | strukturell fertig | 31 |
| Fahrzeuge | strukturell fertig | 111 |
| Events | strukturell fertig | 19 |
| Einstellungen | strukturell fertig | 21 |
| Progression/XP | vollständig erzeugt | Qualitäts-/Referenzprüfung offen |
| Pakete/Belohnungen | vollständig erzeugt | Item-Referenz-/Stackprüfung offen |
| Quests/Story | aktive Planungsphase | noch offen |
| Shop | noch nicht gebaut | offen |
| Händler | noch nicht gebaut | offen |
| Economy | noch nicht gebaut | offen |
| Begleiter/NPC-KI | Regeln werden gerade finalisiert | DBs noch nicht gebaut |

### Wichtige Item-Korrektur
- Item 053 wird von **Infektionsmittel** zu **Infektionshemmer**
- ID wird von `infektionsmittel` zu `infektionshemmer`
- Zweck: bestehende Infektion reduzieren bzw. Fortschreiten bremsen
- Kategorie Medizin
- Stack 10
- spezialisierte Seltenheit: Gelb/Episch
- nicht in normalen Versorgungs-/Loginpaketen

Zusätzlich vorgesehen:
- neues Item **Fähigkeits-Neukalibrierung**
- wird für das Zurücksetzen normaler Spieler-Skills verwendet

## Spieler-Progression

Bestätigt:
- Level 1–100
- ganze XP-Werte
- Level 100 = Maximum
- pro Level-Up 1 Skillpunkt
- Level 100 ergibt insgesamt 99 reguläre Skillpunkte
- alle 5 Level zusätzliche Forschungspunkte
- alle 10 Level größere Belohnung und permanenter Sammel-XP-Bonus
- Story-Freischaltungen bleiben getrennt
- Skills dürfen Storyvoraussetzungen nicht umgehen

### Skill-Reset
- ab Level 20
- kostet 1× Fähigkeits-Neukalibrierung
- 100 % der regulären Skillpunkte werden zurückgegeben
- SECRET-, Story-, Forschungs-, Gebiets- und Fahrzeugfreischaltungen bleiben erhalten
- Reset muss immer bestätigt werden

## Login-System

Bestätigt:
- fester 30-Tage-Kalender
- verpasste Tage setzen den Fortschritt nicht zurück
- 4 vorbereitete Kalender A → B → C → D → A
- insgesamt 120 Login-Tage pro Rotation
- unabhängig vom realen Kalendermonat
- keine Echtgeld-, Story-, SECRET- oder einzigartigen Questgegenstände
- Tag 30 ist jeweils die größte Belohnung

Die erzeugten Detailtabellen werden vor dem endgültigen Produktionsstatus noch einmal gegen die bestätigten Planungsstände geprüft.

## Quest- und Storyfortschritt

### Hauptstory
Aktuell ist ein konkreter Grundbogen mit **25 Hauptmissionen** definiert.

Wichtige Stationen:
- Start auf dem eigenen Grundstück
- erstes Waldgebiet
- Signal/Testsektoren
- Beweisvernichtung und verschlossene Zugänge
- Bunker A
- zweite Basis
- Forschungsanlage
- Versuchsperson/Widersprüche
- militärische Spuren
- gescheiterte Evakuierung
- Siedlung
- Verbündete
- Helikopter/Freies Fliegen als getrennte Systeme
- Vorbereitung auf die Sperrzone
- Tschernobyl
- scheinbarer Ursprung
- Cliffhanger und anschließendes freies Spiel

### SECRET-Missionen
12 SECRET-Missionen mit jeweils 3 Stufen sind konzeptionell festgelegt. Sie schalten geheime Fähigkeiten frei, kosten keine Skillpunkte und bleiben bis zur Entdeckung verborgen.

## Sarah – Storyfigur und Karma

Sarah ist als wichtige wiederkehrende Figur vorgesehen.

Bestätigte Richtung:
- anfangs freundlich und hilfsbereit
- der Spieler beeinflusst ihre Entwicklung über ein Karma-/Vertrauenssystem
- Startwert: 50 %
- **50–100 %:** Sarah bleibt Begleiterin
- **unter 50 %:** neutraler/negativer Pfad
- sehr niedriger Wert kann zur Trennung und späteren Konfrontation in Tschernobyl führen
- kein zwingender Kampf gegen Sarah
- Akten dürfen bewusst offenlassen, ob Sarah hinter den Vorgängen steckt oder selbst als Marionette benutzt wurde
- die endgültige Bewertung bleibt beim Spieler
- auf Leicht ist die Karmaanzeige sichtbar; negative Entscheidungen wirken abgeschwächt
- auf höheren Schwierigkeitsstufen wird die Entwicklung vor allem über Dialoge, Körpersprache und Verhalten vermittelt

### Negativer Sarah-Ausgang
Status-Effekt **Gebrochen**:
- zeitlich begrenzt
- -20 % effektive maximale Haltbarkeit für Gegenstände mit Haltbarkeit
- Gegenstände werden nicht dauerhaft beschädigt
- aktueller Plan: 6 Ingame-Stunden = 90 Minuten aktive Spielzeit

## Allgemeines Begleitersystem

### Grundregel
**Der Spieler bleibt immer die Hauptfigur. Begleiter unterstützen, ersetzen ihn aber nicht.**

### Menschliche Begleiter
- keine normalen Lebenspunkte
- nicht dauerhaft tötbar
- eigene Skillverwaltung
- jeder Skill kann grundsätzlich bis Maximalstufe ausgebaut werden
- aktuell 5 Skillstufen vorgesehen
- aktive Begleiter benutzen die vom Spieler vergebenen Skills
- aktive Begleiter: maximal **75 % effektive Skillwirkung**
- nicht aktive Begleiter in der Siedlung: autonom und **100 % / Maximal-Skills**
- maximaler späterer Squad-Rahmen: Spieler + bis zu 3 eigene Begleiter
- im späteren Multiplayer besitzt jeder Spieler seine eigenen Begleiter
- jeder Begleiter hört ausschließlich auf seinen Besitzer

### Passive Hilfe
Jeder Begleiter besitzt das 3-stufige Hilfesystem **Passive Hilfe**:
1. subtiler Hinweis
2. deutlicherer Hinweis
3. starker Hinweis

Der Begleiter löst die Aufgabe nie vollständig selbst.

### Tierbegleiter / Hunde
- eigenes System, getrennt von menschlichen Skillleisten
- keine Lebenspunkte
- keine Skillleiste
- Fähigkeiten werden zufällig bestimmt
- ein neuer Hund darf anfangs maximal 2 Fähigkeiten besitzen
- erster Hund wird über Story freigeschaltet
- späteres Zucht-/Kreuzungssystem vorgesehen
- Passive Hilfe funktioniert nonverbal, z. B. Blick in die Richtung eines gesuchten Objekts

**Noch offen:** genaue Squad-Zählung von Tierbegleitern gegenüber den 3 normalen Begleiterplätzen.

## Datengetriebene Begleiter-KI

Die Begleiter-KI soll nicht frei improvisieren, sondern innerhalb fester Datenbankregeln handeln.

### Aktiver Begleiter
Wenn kein expliziter Befehl vorliegt, darf die KI begrenzt eigenständig:
- Besitzer folgen
- Abstand halten und Kollisionen vermeiden
- auf unmittelbare Gefahren reagieren
- geeignete Gegner angreifen
- Deckung/Position verbessern
- warnen
- Passive Hilfe geben
- rollenbezogene kleine Unterstützungsaktionen ausführen

Nicht erlaubt:
- eigenmächtige Storyentscheidungen
- geschützte Questgegenstände verwenden
- wichtige Systeme ohne Freigabe aktivieren
- große Ressourcenmengen ohne Erlaubnis verbrauchen
- den Besitzer durch eine eigene Mission verlassen

### Nicht aktiver menschlicher Begleiter
In der Siedlung darf er innerhalb seiner Vorgaben autonom arbeiten:
- Arbeitsstationen nutzen
- fehlende Ressourcen erkennen
- erlaubte Siedlungslager prüfen
- benötigte Ressourcen selbst beschaffen
- anschließend zur Aufgabe zurückkehren

### Lagerberechtigungen
Grundregel:
- sämtliche privaten Lager des Spielers sind **verboten**
- Siedlungslager sind standardmäßig nicht automatisch freigegeben
- ein Siedlungslager kann ausdrücklich für NPCs freigegeben werden
- Story-/Quest-/Geheimgegenstände bleiben geschützt

Mögliche Lagerzustände:
- Privat
- Siedlung – gesperrt
- Siedlung – für NPCs freigegeben

### Arbeitsstatus und Rückkehrzeit
Stationen/Begleiterverwaltung sollen den aktuellen autonomen Status zeigen, z. B.:

> Bin unterwegs – Ressource X ist ausgegangen. Geschätzte Rückkehr: 00:07:45

Die Rückkehrzeit soll dynamisch aus Weg, Gebiet, Bewegung und benötigter Sammelmenge berechnet werden.

### KI-Fallback
Die KI darf kleine Probleme selbst behandeln, z. B. Route neu berechnen oder eine erlaubte alternative Ressource suchen.

Bei einem echten Hänger gilt jedoch:
- Aufgabe einfrieren
- keine Ressourcen weiter verbrauchen
- Status **Fehler / hängt**
- Spieler informieren
- **kein automatischer harter Neustart**
- nur der Spieler darf KI neu starten, Aufgabe abbrechen, zurückrufen oder erneut versuchen

Damit bleibt die letztendliche Kontrolle beim Spieler.

## Spätere Begleiter-DBs

Vorgesehene Trennung:
- `companions.json.db`
- `companion_skills.json.db`
- `companion_ai.json.db`
- `companion_help.json.db`

Die endgültige Aufteilung wird erst festgeschrieben, wenn alle offenen Begleiterregeln geklärt sind.

## Nächste Arbeitsschritte

1. Begleiter-/NPC-KI-Regeln vollständig abschließen.
2. Quest-/Story-DB weiter finalisieren.
3. offene Werte in Items, Ressourcen, Loot, Settings, Fahrzeuge und Events schließen.
4. Progression- und Paketdaten gegen bestätigte Referenzen prüfen.
5. Shop/Händler/Economy planen und als DBs aufbauen.
6. vollständige Referenz- und Integritätsprüfung aller Datenbanken.
7. erst danach Loader/Manager und weitere C#-Umsetzung fortsetzen.
