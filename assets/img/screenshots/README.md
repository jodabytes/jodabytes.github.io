# Screenshots für die Potte-Produktseite

Die Galerie auf `potte/index.html` zeigt die Play-Store-Screenshots
(Quelle im App-Repo: `Screenshots/Store/angepasst/`).

## Aktuelle Dateien

| Datei | Motiv | Quelle |
|---|---|---|
| `potte-01-posten.png` | Einzelposten-Liste mit Bilanz | `Screenshot_20260526-165006.png` |
| `potte-02-kategorien.png` | Kategorienmanager (Baum) | `Screenshot_20260526-165054.png` |
| `potte-03-donut.png` | Auswertung, Donut-Diagramm mit Prozent-Tabelle | `Screenshot_20260713-155847.png` |
| `potte-04-verlauf.png` | Auswertung, Verlaufs-Liniendiagramm | `Screenshot_20260526-165129.png` |
| `potte-05-dauerposten.png` | Dauerposten-Liste | `Screenshot_20260526-165145.png` |
| `potte-06-darkmode.png` | Einzelposten im Dark Mode | `Screenshot_20260526-165621.png` |

**Format:** 1080 × 2160 px, PNG. Das Seitenverhältnis steckt in
`assets/css/site.css` (`.phone img { aspect-ratio: 1080 / 2160 }`) und in den
`width`/`height`-Attributen der `<img>`-Tags — bei einem Formatwechsel beides
anpassen.

## Screenshot austauschen / ergänzen

1. Neues PNG mit sprechendem Namen (`potte-NN-motiv.png`) hier ablegen.
2. In `potte/index.html` das betroffene `<figure class="phone">` anpassen
   (Dateiname, `alt`-Text, `<figcaption>`) **und** die `screenshot`-URL im
   JSON-LD-Block im `<head>` aktualisieren.
3. Lokal prüfen (Seite öffnen, Galerie ansehen).

Noch offen: Es gibt bisher keinen Screenshot der Pots/Gemeinschaftsausgaben
oder der Endabrechnung — wäre eine sinnvolle Ergänzung (Slot 07), da die
Seite dieses Feature prominent bewirbt.
