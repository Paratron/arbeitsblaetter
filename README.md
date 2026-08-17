# Arbeitsblätter – PWA für das iPad

Foto vom Arbeitsblatt aufnehmen, Textfelder darauf setzen, Antworten mit der Tastatur
(Bildschirm- oder Bluetooth-Tastatur) eintippen. Mehrere Blätter werden mit Titel und
Datum auf dem iPad gespeichert.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | die komplette App (HTML, CSS, JavaScript in einer Datei) |
| `manifest.webmanifest` | macht die Installation als App möglich |
| `sw.js` | Service Worker, damit die App ohne Internet startet |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | App-Symbol |

Alle Dateien müssen im **selben Ordner** liegen.

## Ins Netz stellen

Die App muss über **HTTPS** ausgeliefert werden – nur dann lässt sie sich installieren
und nur dann funktioniert der Service Worker. Direktes Öffnen einer lokalen Datei
(`file://`) genügt nicht.

Einfachster Weg – GitHub Pages, kostenlos:

1. Auf github.com ein neues, öffentliches Repository anlegen.
2. Alle Dateien aus diesem Ordner per „Add file → Upload files" hochladen, „Commit changes".
3. Im Repository: **Settings → Pages**, unter „Branch" `main` und `/ (root)` wählen, „Save".
4. Nach ein bis zwei Minuten ist die Adresse erreichbar:
   `https://DEINNAME.github.io/REPOSITORYNAME/`

Jeder andere Static-Host (Netlify, Cloudflare Pages, ein eigener Webspace) geht genauso.

## Auf dem iPad installieren

1. Adresse in **Safari** öffnen (nicht in Chrome – nur Safari kann installieren).
2. Teilen-Symbol → **Zum Home-Bildschirm**.
3. Ab jetzt die App **immer über das Symbol auf dem Home-Bildschirm** starten.

Das ist nicht bloß bequemer: Nur bei installierten Web-Apps schützt iPadOS die
gespeicherten Daten. Wird die App dagegen als Safari-Tab benutzt, löscht Safari die
Daten nach sieben Tagen ohne Benutzung.

## Bedienung

**Liste**
- `+ Neues Foto` → iPad fragt „Foto aufnehmen" oder „Fotos". Das Blatt öffnet sich sofort.
- Karte antippen öffnet das Blatt, 🗑 löscht es nach Rückfrage.
- Unten steht, wie viel Speicher belegt ist.

**Blatt**
- Titel oben eintippen (freiwillig). Datum wird automatisch gesetzt.
- `+ Textfeld` drücken, dann auf die Stelle tippen, an der der Text beginnen soll.
  Die Tastatur öffnet sich, das Blatt schiebt sich so, dass das Feld sichtbar bleibt.
- Mit einem Finger schieben = Blatt verschieben. Zwei Finger = zoomen.
  Zum genauen Setzen vorher hineinzoomen.
- Ausgewähltes Feld: `A− / A+` Schriftgröße, `enger / breiter` Feldbreite,
  blauer Griff ✥ links zum Verschieben, ↔ rechts zum Ziehen der Breite,
  `Feld löschen`, `Fertig` schließt die Tastatur.
- Bluetooth-Tastatur: Pfeiltasten verschieben das ausgewählte Feld
  (mit Umschalt in größeren Schritten), Esc schließt das Feld.
- Diktieren: das Mikrofon auf der iPad-Tastatur funktioniert in jedem Textfeld.

Gespeichert wird automatisch, es gibt keinen Speichern-Knopf.

## Wie der Text sich verhält

Ein Textfeld hat eine feste Breite und bricht dort um. Wird der Text länger als der
Platz auf dem Blatt, **wächst das Feld nach unten** und verdeckt, was darunter gedruckt
ist. Gegenmittel: Schrift kleiner stellen oder das Feld schmaler und dafür in eine
freie Fläche verschieben.

## Grenzen, die man kennen sollte

- **Kein Export.** Das fertige Blatt lebt in der App, gedacht zum Herzeigen auf dem iPad.
- Wird das App-Symbol vom Home-Bildschirm gelöscht, sind **alle Blätter weg**.
  Dasselbe gilt für „Website-Daten löschen" in den iPad-Einstellungen.
  Als Langzeitarchiv taugt die App deshalb nicht.
- Der Speicherplatz richtet sich nach dem freien Platz des iPads (bei installierten
  Web-Apps bis zu 20 Prozent davon). Ein Foto wird auf 1800 Pixel verkleinert und
  wiegt rund 300 KB – das reicht für hunderte Blätter.
- Änderungen an `index.html` später hochladen? Dann in `sw.js` die Zeile
  `const CACHE = "arbeitsblaetter-v1"` auf `-v2` ändern, sonst zeigt das iPad
  weiter die alte Version aus dem Cache.
