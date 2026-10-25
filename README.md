# Hollywood Terminal Desktop (HTD)

Version **1.1.0** · 25.10.2026

Ein filmischer Kontrollraum für den Browser: 14 verschiebbare und skalierbare Fenster mit frei erfundenen Terminal-, Traffic- und Monitoringdaten. Keine Installation, keine Bibliotheken, kein Build, keine externen Ressourcen oder Netzwerkabfragen. Die App funktioniert auch offline.

## Starten

ZIP entpacken und `index.html` in einem aktuellen Chrome, Edge, Firefox oder Safari öffnen. Für verlässliche lokale Speicherung empfiehlt sich eine feste Webadresse (zum Beispiel GitHub Pages). Bei `file://` hängt das Speicherverhalten vom Browser ab.

## GitHub Pages

1. Auf GitHub ein neues Repository erstellen, zum Beispiel `hollywood-terminal-desktop`.
2. `index.html`, `style.css`, `app.js`, `.nojekyll`, `README.md` und `CHANGELOG.md` direkt in das Hauptverzeichnis hochladen. Bei versteckten Dateien gegebenenfalls `.nojekyll` überspringen; für diese App ist die Datei optional.
3. Unter **Settings → Pages → Build and deployment** die Quelle **Deploy from a branch** wählen.
4. Branch **main** und Ordner **/ (root)** wählen und speichern.
5. Nach Abschluss der Bereitstellung die angezeigte Pages-Adresse öffnen: `https://DEIN-NAME.github.io/hollywood-terminal-desktop/`.

Die Dateien brauchen keine Pfadanpassung. Produktives Repository: https://github.com/vorzueglich/htd · GitHub Pages: https://vorzueglich.github.io/htd/

## Bedienung

| Taste | Funktion |
| --- | --- |
| Leertaste | Pause / weiter |
| A | Fenster nach dem gewählten Layout neu anordnen |
| R | Simulierte Sitzung neu starten, Anordnung beibehalten |
| H | Hilfe öffnen / schliessen |
| S | Settings öffnen / schliessen |
| Esc | Dialog beziehungsweise Browser-Vollbild verlassen |

Fenster an ihrer Titelleiste ziehen. Unten rechts über den nativen Browser-Griff skalieren (am zuverlässigsten mit Maus/Trackpad). Doppelklick auf eine Titelleiste maximiert das Fenster; erneuter Doppelklick stellt es wieder her. Anklicken bringt ein Fenster nach vorne. Auf kleinen Displays kann der Desktop gescrollt werden. Vollbild muss durch einen Klick ausgelöst werden und setzt Unterstützung durch den Browser voraus.

## Live-Settings

Das Settings-Menü ist jederzeit über **⚙ Settings** oder **S** erreichbar. Änderungen gelten sofort, während die Simulation weiterläuft:

- Geschwindigkeit: 5–100 %, Standard 65 %.
- Fensterzahl: 4–20, Standard 14. Eine Änderung ordnet die Fenster neu an.
- Layout: Busy (Standard), Grid oder Cascade. Layoutwechsel ersetzt die bisherige Anordnung.
- Farbstil: Green (Standard), Cyan, Amber oder Violet.
- Modus: Normal (Standard), Alarm mit häufigeren Ereignissen und Warnfarben oder Quiet mit langsamerem Takt.
- Schriftgrösse: klein, mittel (Standard), gross.
- Scanlines und Phosphor-Leuchten separat ein-/ausschalten.
- Animationen deaktivieren: Anzeigen bleiben statisch. Die Systemuhr läuft weiter.
- Defaults wiederherstellen: setzt Einstellungen und Fensteranordnung zurück.

Einstellungen und Fensterpositionen werden unter `htd-v1` im lokalen Browserspeicher gespeichert. Ohne Speicherberechtigung bleibt die App nutzbar, speichert jedoch nur für die laufende Sitzung. Ein anderer Browser oder eine andere URL hat einen eigenen Speicher. Reduzierte Bewegung im Betriebssystem wird beim ersten Start berücksichtigt. Hintergrundtabs pausieren die Datenaktualisierung automatisch.

## Simulation und Performance

Alle Werte, Services, IDs und Verbindungen sind erfunden. Es werden keine realen Systeme überwacht oder kontaktiert. Kein Audio, keine Kamera, kein Mikrofon, kein Tracking. Für Filmaufnahmen empfiehlt sich ein Desktop-Display mit mindestens 1280 × 800 Pixeln. Viele Fenster, grosse Vollbildauflösungen und hohe Geschwindigkeit beanspruchen mehr Rechenleistung; bei Bedarf Geschwindigkeit senken oder Effekte abschalten.

## Dateien und Versionierung

- `index.html`: Oberfläche und Dialoge
- `style.css`: Design, Farben und responsive Darstellung
- `app.js`: Simulation, Fenstersteuerung und Speicherung
- `CHANGELOG.md`: Änderungen je Version

Versionsschema: MAJOR.MINOR.PATCH. Für eine Veröffentlichung auf GitHub kann ein Tag `v1.1.0` samt Release und ZIP angelegt werden. Bei Updates die drei App-Dateien zusammen ersetzen und Browser neu laden. Kein Service Worker: dadurch werden keine alten App-Versionen absichtlich offline zwischengespeichert.

## Neu in 1.1.0: organische Abläufe und Grafikfenster

Jedes Fenster hat eine eigene Datenrate mit zufälligen Schwankungen, kurzen Ereignisschüben und gelegentlichen Wartezeiten. Schnelle Paketlogs, langsame Journale und mehrere Sekunden ruhende Telemetrie laufen nebeneinander. Radar, Kartenverbindungen und Kurven werden unabhängig davon mit bis zu 30 Bildern pro Sekunde gezeichnet. Geschwindigkeit und Modus skalieren die Simulationszeit gemeinsam, ohne die unterschiedlichen Rhythmen zu vereinheitlichen. Pause hält auch Radar und Karten an.

Die 14 Standardfenster enthalten Weltkarte, Europakarte, Radar, Spektrumanalyse, zwei zweifarbige Traffic-Kurven und einen verpixelten synthetischen Korridor-Feed. Die Karten sind bewusst vereinfachte, selbst gezeichnete Umrisse ohne Anspruch auf geografische Präzision. Der Pixelfeed läuft absichtlich mit niedriger, schwankender Bildrate. Er verwendet weder Kamera noch Videodateien.

Statuspunkte erscheinen unabhängig vom Farbstil grün, gelb und rot. Warnmeldungen und hohe Spektralpegel erhalten zusätzliche Farbakzente. Die gesamte Darstellung bleibt simuliert.

### Prüfstand

JavaScript-Syntax sowie App-Start, alle Grafikpfade, 14/20/4 Fenster, Farbwechsel und Pause wurden in einer isolierten DOM-/Canvas-Testumgebung geprüft. Bei 16,5 Sekunden simulierter Laufzeit zeigten die Fenster deutlich unterschiedliche Updatezahlen. Die Browserprüfung der veröffentlichten Seite erfolgt zusätzlich über GitHub Pages.
