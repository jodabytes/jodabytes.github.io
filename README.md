# jodabytes-Webseite

Statische Webseite für den Entwickler-Account **jodabytes**: Portfolio-Startseite,
Produktseite für **Potte**, Anleitung, Datenschutzerklärung und Impressum.
Reines HTML/CSS — kein Build-Tool, keine externen Abhängigkeiten, kein
erforderliches JavaScript.

## Struktur

```
index.html               jodabytes-Startseite (App-Portfolio)
impressum.html           Impressum — PLATZHALTER VOR VERÖFFENTLICHUNG AUSFÜLLEN!
404.html                 Fehlerseite (GitHub Pages nutzt sie automatisch)
potte/index.html         Potte-Produktseite
potte/anleitung.html     Erste Schritte + FAQ (stabile Anker, siehe unten)
potte/datenschutz.html   Datenschutzerklärung (wird in App + Play Console verlinkt)
assets/css/site.css      einziges Stylesheet (Farb-Tokens aus docs/design-tokens.md)
assets/img/              Icon + Screenshots (siehe assets/img/screenshots/README.md)
robots.txt, sitemap.xml, llms.txt
```

> **Hinweis CNAME:** Es gibt bewusst noch keine `CNAME`-Datei. Sie wird erst
> angelegt, wenn die eigene Domain gekauft und das DNS eingerichtet ist —
> vorher würde sie die GitHub-Pages-URLs (auch die alte Datenschutz-URL
> `/ExpenseMonitor/`) auf die nicht erreichbare Domain umleiten und damit
> kaputt machen.

## ✅ Vor der Veröffentlichung

1. **Impressum:** Name und Ort sind eingetragen (bewusst ohne vollständige
   Anschrift). Bei späterer Monetarisierung eine ladungsfähige Anschrift
   ergänzen — z. B. über einen Impressum-Dienst — und den „Hinweis“-Absatz
   („derzeit kostenlos“) aktualisieren.
2. **Screenshots:** Die Play-Store-Screenshots sind eingesetzt. Austausch
   oder Ergänzung (z. B. Pots-Motiv): siehe `assets/img/screenshots/README.md`.
3. **Domain prüfen:** Die Seite ist auf `jodabytes.de` ausgelegt — siehe
   „Domain ändern“, falls es eine andere Domain wird.

## Phase 1: Übergangsbetrieb auf GitHub Pages (ohne eigene Domain)

Die alte Datenschutz-URL `https://joda-bln.github.io/ExpenseMonitor/` wird vom
Repo `joda-bln/ExpenseMonitor` (Projekt-Page) ausgeliefert. Die neue Webseite
liegt in der GitHub-**Organisation `jodabytes`** im Site-Repo
`jodabytes/jodabytes.github.io` und läuft unter `https://jodabytes.github.io/`
— ein anderer Account-Namespace als die alte Seite, beide koexistieren,
der alte Link bleibt intakt.

1. Kostenlose GitHub-Organisation `jodabytes` anlegen, darin ein neues
   **öffentliches** Repo `jodabytes.github.io` (der Name muss exakt so lauten).
2. Den **Inhalt** dieses Ordners (nicht den Ordner selbst) in die Repo-Wurzel
   kopieren, committen, auf `main` pushen. User-Site-Repos veröffentlicht
   GitHub Pages automatisch aus der Wurzel von `main`
   (kontrollieren unter Settings → Pages).
3. **Keine Custom Domain eintragen und keine `CNAME`-Datei anlegen**, solange
   die Domain nicht existiert — die Seite wäre sonst nicht erreichbar.
4. Prüfen (beide müssen funktionieren):
   - neu: `https://jodabytes.github.io/` und `/potte/datenschutz.html`
   - alt: `https://joda-bln.github.io/ExpenseMonitor/` (unverändert)
5. Das alte Repo `joda-bln/ExpenseMonitor` unverändert lassen (nicht löschen,
   nicht auf privat stellen, Pages nicht deaktivieren), solange App-Version
   1.5.2 im Umlauf ist und die Play Console darauf zeigt.

Hinweis: `sitemap.xml`, `robots.txt`, `llms.txt` und die canonical-/OG-Tags
verweisen bereits auf `https://jodabytes.de` — für den Übergangsbetrieb ist
das unschädlich, die Seite funktioniert trotzdem. Sitemap erst bei Google
einreichen, wenn die Domain live ist.

## Phase 2: Eigene Domain aufschalten (später)

1. Domain kaufen (geplant: `jodabytes.de`).
2. **DNS beim Registrar:**
   - Apex `jodabytes.de`: vier `A`-Records auf
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www`: `CNAME`-Record auf `jodabytes.github.io`
3. Settings → Pages → Custom domain → `jodabytes.de` eintragen. Dabei legt
   GitHub eine `CNAME`-Datei (Inhalt: eine Zeile `jodabytes.de`) in die
   Repo-Wurzel — alternativ selbst anlegen und pushen.
   Sobald das Zertifikat ausgestellt ist: **Enforce HTTPS** aktivieren.
4. Prüfen: `https://jodabytes.de/potte/datenschutz.html` lädt über HTTPS.
5. App-URLs (`_privacyUrl`, `_manualUrl` in
   `lib/presentation/settings/settings_page.dart`) und die Play-Console-URL
   bei Gelegenheit auf `https://jodabytes.de/…` umstellen. Eilt nicht:
   GitHub Pages leitet `https://jodabytes.github.io/<pfad>` nach der
   Domain-Aufschaltung automatisch pfaderhaltend auf die Domain um, die
   bisherigen Links funktionieren also weiter.

## Status App & Play Console

- Die App verlinkt seit dem Stand nach 1.5.2 auf
  `https://jodabytes.github.io/potte/datenschutz.html` (`_privacyUrl`) und
  `https://jodabytes.github.io/potte/anleitung.html` (`_manualUrl`).
- Die Play Console (App-Inhalte → Datenschutzerklärung) muss auf
  `https://jodabytes.github.io/potte/datenschutz.html` umgestellt werden,
  sobald das App-Update eingereicht ist.
- Die **alte** Datenschutz-URL `https://joda-bln.github.io/ExpenseMonitor/`
  (Repo `joda-bln/ExpenseMonitor`) muss online bleiben, solange Versionen
  ≤ 1.5.2 im Umlauf sind — erst danach kann das alte Repo weg.

## Stabile Anker in der Anleitung

Die App darf direkt auf Abschnitte verlinken. Diese IDs sind **stabil** und
dürfen nie umbenannt werden (neue dürfen dazukommen):

`erste-schritte`, `posten-anlegen`, `kategorien`, `dauerposten`,
`auswertungen`, `pots`, `backup`, `faq`, `faq-kosten`, `faq-daten`,
`faq-geraetewechsel`, `faq-cloud-sync`, `faq-csv`, `faq-ios`,
`faq-loeschen`, `faq-kontakt`

Beispiel: `https://jodabytes.github.io/potte/anleitung.html#faq-geraetewechsel`

## Domain ändern

Die absolute Basis-URL ist derzeit `https://jodabytes.github.io` und steht nur
in Meta-/Crawler-Dateien; interne Links sind relativ. Bei Domainwechsel
(z. B. auf `jodabytes.de`):

1. In allen Dateien `https://jodabytes.github.io` durch die neue Domain
   ersetzen (betrifft: canonical/OG/Twitter-Tags und JSON-LD in den
   HTML-Dateien, `sitemap.xml`, `robots.txt`, `llms.txt`).
2. `CNAME`-Datei anlegen/anpassen.
3. DNS-Records setzen (siehe Phase 2), Pages-Einstellung aktualisieren.
4. In der Google Search Console die neue Domain als Property anlegen und die
   Adressänderung melden (Einstellungen → Adressänderung).

## Neue App ergänzen

1. Ordner `neueapp/` mit eigener `index.html` (Vorlage: `potte/index.html`).
2. App-Karte auf `index.html` unter „Apps“ ergänzen.
3. Einträge in `sitemap.xml` und `llms.txt` hinzufügen.

## Pflege pro Potte-Release

- Versionsnummer auf `potte/index.html` (Hero-Zeile „aktuelle Version“ und
  `softwareVersion` im JSON-LD) aktualisieren.
- Bei inhaltlichen Änderungen: `<lastmod>` in `sitemap.xml` anpassen.
- Bei Änderungen an der Datenschutzerklärung: „Stand:“-Datum in
  `potte/datenschutz.html` aktualisieren und `docs/legal/privacy.md` im
  App-Repo synchron halten.

## Lokal testen

- `index.html` per Doppelklick öffnen — alle Links funktionieren auch via `file://`.
- Oder sauberer: in diesem Ordner `python -m http.server 8000` starten und
  `http://localhost:8000` öffnen.
- JSON-LD prüfen: https://validator.schema.org — nach dem Deploy zusätzlich
  Googles Rich-Results-Test für `/potte/index.html` und `/potte/anleitung.html`.
