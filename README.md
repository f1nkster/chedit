# ⚗️ Chemie-Formeleditor

Ein Web-Tool für den Chemieunterricht: Reaktionsgleichungen, Stöchiometrie,
Oxidationszahlen & Redox, pH-Werte & Titration, Atombau, Elektrochemie,
Strukturformeln, Kristallgitter und Reaktionsmechanismen – mit Export und
Arbeitsblatt-Generator. Kernstück ist [index.html](index.html) plus der Ordner
`assets/` (Logo und Schrift) – keine Installation, keine Abhängigkeiten,
kein Server nötig.

![ChEdit – eine Reaktionsgleichung wird automatisch ausgeglichen; darüber die 13 Modi in fünf Gruppen von Atombau bis Mechanismen](docs/screenshot.png)

Das Design folgt dem **FAU-Corporate-Design** (FAU-Blau `#04316a`, Phil-Fak-Gelb `#fdb735`)
und passt damit optisch zu https://www.chemiedidaktik.phil.fau.de/. Im Header steht links
das **ChEdit-Logo** (Variante 1e „Editor-Caret“: der Schriftzug tippt sich beim Laden
selbst ein, der gelbe Cursor blinkt; bei `prefers-reduced-motion` statisch) und rechts
das Lehrstuhl-Logo, verlinkt auf die Lehrstuhl-Website. Eine statische SVG-Fassung des
ChEdit-Logos liegt unter `assets/logo-chedit.svg` (z. B. für Favicon oder Druck).

**DSGVO:** Das Tool lädt zur Laufzeit **keine externen Ressourcen**. Die Schrift
„Source Sans 3“ (freie Schrift, SIL Open Font License) und das Logo liegen lokal in
`assets/` – kein Google-Fonts-CDN, keine Tracker, keine Cookies. Beim Hochladen den
`assets/`-Ordner mitkopieren.

> **Hinweis zu diesem Repository:** Nicht enthalten sind das geschützte
> **FAU-/Lehrstuhl-Logo** (`assets/logo-chemiedidaktik.svg`), die lokale Hilfsdatei
> `start-lokal.bat` und die server-spezifischen `oembed.*`-Dateien. Schrift und
> ChEdit-Logo (im Ordner `assets/`) sind dabei, das Tool läuft also direkt. Für die
> FAU-Version einfach ein eigenes `assets/logo-chemiedidaktik.svg` ergänzen – fehlt die
> Datei, blendet der Header diesen Logo-Platz automatisch aus (kein kaputtes Bild).

## Funktionen

- **Automatisch ausgleichen**: Edukte und Produkte eingeben (`CH4 + O2 -> CO2 + H2O`),
  das Tool berechnet die kleinsten ganzzahligen Koeffizienten (exakte Bruchrechnung, Gauß-Verfahren).
- **Selbst ausgleichen & prüfen**: Gleichung mit eigenen Koeffizienten eingeben
  (`2 H2 + O2 -> 2 H2O`), das Tool zeigt pro Element die Atomanzahlen links/rechts – gut als Übung.
- **Stöchiometrie-Rechner**: ausgeglichene Gleichung → interaktive Tabelle mit molaren
  Massen; bei einem Stoff n (mol) oder m (g) eintragen, alle übrigen Werte werden über
  das Stoffmengenverhältnis berechnet (auch Hydrate und Elektronen/Faraday).
- **Oxidationszahlen & Redox**: OZ je Element aus der Summenformel (inkl. Sonderfällen
  wie Peroxiden und Hydriden) oder **je Atom** aus der Struktur organischer Moleküle.
  Redoxgleichungen werden erkannt und die **Teilgleichungen automatisch aufgestellt** –
  Elektronen-, H⁺/OH⁻- und H₂O-Ausgleich je Milieu (sauer/basisch umschaltbar),
  Gesamtgleichung mit Selbstprüfung, römische OZ über den Atomen.
- **Säuren & Basen (pH)**: pH, pOH und Ionenkonzentrationen für starke und schwache
  Säuren/Basen (pKs/pKb, H₂SO₄, Autoprotolyse, quadratisch genau) mit Rechenweg und
  exportierbarer **pH-Skala** mit wählbaren Indikatoren (Universalindikator bis Rotkohlsaft).
- **Titration (interaktiv)**: Probe, Maßlösung und Indikator wählen, mit dem
  Bürette-Regler titrieren – Kurve, pH-Wert und Lösungsfarbe reagieren live.
  Äquivalenz- und Halbäquivalenzpunkt, Pufferbereich und pH-Sprung werden markiert,
  die Indikator-Eignung wird bewertet (exakte Ladungsbilanz-Rechnung inkl. Verdünnung).
- **Atombau**: Elektronenkonfiguration für H bis Kr (auch Ionen) als
  **Energiestufenmodell** oder **Orbitalmodell** (Kästchenschreibweise mit Spin-Pfeilen;
  Pauli, Hund, 4s-vor-3d, Cr/Cu-Ausnahmen), Edelgas-Kurzform und **Herleitung der
  PSE-Position** aus der Konfiguration samt klickbarem Mini-Periodensystem.
- **Galvanik & Elektrolyse**: Galvanische Zellen aus zwei Halbzellen frei
  zusammenbauen (10 Metalle; Nernst-Gleichung bei c ≠ 1 mol/L, auch
  Konzentrationszellen) – Zellen-Schema mit Salzbrücke, Elektronenfluss und Voltmeter,
  Zellendiagramm und Rechenweg. Umschaltbar auf **Elektrolyse**: Pole wechseln,
  Zersetzungsspannung, **Faraday-Rechner** für abgeschiedene Massen.
- **Spannungsreihe**: Metall und Salzlösung wählen → läuft die Redoxreaktion
  freiwillig? E°-Skala mit Markierung, Begründung und Reaktionsgleichung.
- **Kristallgitter (3D)**: NaCl, CsCl, kubisch/hexagonal dichteste Packung und
  kubisch-raumzentriert als drehbares Kugelmodell in JSmol – mit
  **Elementarzellen-Box**, Koordinationszahlen, Raumausfüllung und messbaren Abständen.
- **EPA-Modell (3D)**: im 3D-Viewer zuschaltbar – Bindungswinkel und freie
  Elektronenpaare am kraftfeld-optimierten Molekül.
- **Strukturformeln (OC)**: Einfache organische Moleküle als **Skelettformel** oder mit
  **ausgeschriebenen C und H** zeichnen lassen. Eingabe als Halbstrukturformel
  (`CH3-CH(OH)-COOH`), SMILES (`CCO`, `c1ccccc1`) **oder deutscher Name**
  (`Ethanol`, `2-Methylbutan`, `But-2-en`, `Propan-2-ol`, `Essigsäure`, `Cyclohexan` –
  systematische Nomenklatur mit Substituenten, Mehrfachbindungen, -ol/-al/-on/-säure/-amin
  sowie gängige Trivialnamen). Das Tool zeigt die Summenformel an
  und warnt didaktisch, wenn geschriebene H-Zahlen nicht zur Valenz passen
  (z. B. `CH2-CH3`). Bei ausgeschriebenen Strukturen ist die Geometrie umschaltbar:
  **Gewinkelt (120°)** wie in realistischen Darstellungen oder **Linear (90°)** wie in
  klassischen Schulbuch-Valenzstrichformeln (gerade Kette, H senkrecht).
- **Freie Elektronenpaare**: Bei ausgeschriebenen Strukturformeln optional zuschaltbar –
  Striche an O, N, S und Halogenen wie in der Valenzstrichformel üblich.
- **PNG- und SVG-Export**: Gleichung oder Strukturformel als hochauflösendes PNG in die
  Zwischenablage kopieren oder herunterladen – direkt in Word/Docs einfügbar. Zusätzlich
  SVG-Download (Vektorgrafik, verlustfrei skalierbar). Schriftart, Größe und transparenter
  Hintergrund einstellbar.
- **Arbeitsblatt-Modus**: Einträge aus fast allen Modi mit „➕ Zur Liste“ sammeln
  (Gleichungen, Strukturen, Mechanismen, OZ/Redox-Schemata, pH-Skalen, Titrationskurven,
  Atombau-Diagramme, Zellen-Schemata, Spannungsreihen; bleibt lokal im Browser
  gespeichert), sortieren, mit Titel versehen und als Druckseite/PDF ausgeben – mit
  Name/Klasse/Datum-Kopfzeile. Wählbarer **Aufgabentyp**: Lösung anzeigen · **Lücken**
  (Koeffizienten, OZ, pH-Marker, Kurven-Beschriftungen frei) · **Fehlersuche** (das Tool
  baut gezielt typische Fehlvorstellungen ein – z. B. „ÄP = neutral“, O pauschal als −II,
  Hund verletzt, Anode/Kathode vertauscht – und das Lösungsblatt erklärt den Fehler) ·
  **Skizzieren** (leere Diagramme zum Selbstzeichnen). Lösungsblatt auf eigener
  Seite anhängbar.
- **Reaktionsmechanismen**: Eigener Modus mit kuratierten, lehrplanrelevanten
  Mechanismen: **SN1**, **SN2** und **radikalische Substitution (SR)** (Photochlorierung
  von Methan). Bei den nukleophilen Substitutionen sind Substrat (Methyl/primär/sekundär/
  tertiär) und Nucleophil (OH⁻, H₂O, I⁻) wählbar. Die Schritte werden mit
  **Elektronenverschiebungspfeilen** gezeichnet – volle Pfeilspitze für Elektronen**paare**,
  **Fischhaken (halbe Spitze)** für die Bewegung **einzelner** Elektronen inkl.
  **Radikal-Punkten** –, dazu δ-Partialladungen und Übergangszustand (Klammern + ‡). Alles
  lässt sich durchblättern, exportieren und ins Arbeitsblatt übernehmen. Eine **begründete
  SN1/SN2-Abwägung** erklärt, welcher Mechanismus für die Kombination zu erwarten ist.
  Dazu 3D: schematische **JSmol-Animationen** (Rückseitenangriff an CH₃Br, Cl₂-Homolyse)
  und das **planare tert-Butyl-Kation**. Teilbare Links: `?mode=mech&m=sn2&sub=mebr&nu=oh&schritt=2`.
- **3D-Viewer-Bedienung**: Umschaltbare **Darstellungsformen** – Kugel-Stab, Stäbchen,
  Kalotten (CPK), Drahtmodell und **ESP-Oberfläche** (elektrostatisches Potential:
  rot = negativ/elektronenreich, blau = positiv; aus Gasteiger-Partialladungen) –,
  optionale **Atom-Beschriftung** und ein **Messmodus** (Abstände durch Anklicken zweier
  Atome). Hinweis: Keil-Strich-Formeln sind eine **2D**-Stereo-Konvention; die räumliche
  Anordnung zeigt hier direkt das 3D-Modell.
- **3D-Modelle (JSmol)**: Im Strukturmodus öffnet „🧊 3D-Modell“ die mitgelieferte
  Viewer-Seite `3d.html` in einem **Popup-Fenster** (MOL-Datei wird per URL übergeben;
  erneute Klicks nutzen dasselbe Fenster). Die Geometrie wird von JSmol per Kraftfeld
  optimiert – ein Overlay verdeckt die Ansicht währenddessen, sodass direkt das
  **fertige Modell** erscheint. Exporte im Popup: **PNG** (Bild), **SVG** (Bild in
  SVG-Hülle, kein echter Vektor) und **MOL (3D)** – die optimierten 3D-Koordinaten
  für Avogadro, Chimera & Co. JSmol wird **erst beim Klick** geladen: bevorzugt aus dem
  lokalen Ordner `jsmol/` neben dem Tool, sonst von
  `https://intern.chemiedidaktik.fau.de/jsmol` (per `?jsmol=…` übersteuerbar) –
  DSGVO-konform, keine Drittanbieter.
  **Wichtig:** `3d.html` mit hochladen; Tool und JSmol sollten auf derselben Domain
  liegen. Technischer Hinweis im Code: `set minimizationRefresh false` darf nicht
  verwendet werden – es hält die Minimierung in JSmol komplett an.
- **Barrierefreiheit**: Die Vorschau trägt eine textliche Beschreibung (`aria-label`,
  z. B. „CH4 + 2 O2 → CO2 + 2 H2O“) für Screenreader, Statusmeldungen sind `aria-live`,
  Umschalter melden ihren Zustand (`aria-pressed`), sichtbarer Tastatur-Fokus.

### Eingabe-Syntax

| Eingabe | Bedeutung |
|---|---|
| `->` oder `=` | Reaktionspfeil → |
| `<->` oder `<=>` | Gleichgewichtspfeil ⇌ |
| `Ca(OH)2`, `Fe2O3` | Formeln wie gewohnt, Klammern erlaubt |
| `(s)`, `(l)`, `(g)`, `(aq)` | Aggregatzustände (optional, nach der Formel) |
| `CuSO4*5H2O` | Hydrate mit `*` |
| `H+`, `NO3-`, `e-` | einfach geladene Ionen und Elektronen: Ladung direkt anhängen |
| `Fe^3+`, `SO4^2-` | mehrfach geladene Ionen: Ladung mit `^` |

**Redox:** Ionengleichungen werden inklusive **Ladungsbilanz** ausgeglichen und geprüft,
z. B. `MnO4^- + Fe^2+ + H+ -> Mn^2+ + Fe^3+ + H2O`. Auch Teilgleichungen mit Elektronen
funktionieren: `Cr2O7^2- + H+ + e- -> Cr^3+ + H2O`. Im Prüfmodus erscheint die Ladung
als eigene Zeile in der Vergleichstabelle.

**Hinweis zur Schreibweise:** Mehrfachladungen immer mit `^` schreiben – `Fe3+` würde
als 3 Fe-Atome mit Ladung 1+ gelesen (das Tool zeigt dann einen Tipp an).

### Eingabe-Syntax Strukturformeln

| Eingabe | Bedeutung |
|---|---|
| `CH3-CH2-OH` oder `CCO` | Ketten als Halbstrukturformel oder SMILES |
| `CH3-CH(CH3)-CH3`, `C(CH3)4` | Zweige in Klammern, optional mit Anzahl |
| `CH2=CH2`, `HC#CH` | Doppel-/Dreifachbindung mit `=` / `#` |
| `C1CCCCC1`, `c1ccccc1` | Ringe über Ringziffern (auch `%nn`), Benzol klein geschrieben |
| `c1ccncc1`, `c1ccoc1`, `c1cc[nH]c1` | Heteroaromaten: Pyridin, Furan, Pyrrol, Thiophen |
| `[NH4+]`, `[O-]`, `CC(=O)[O-]` | Ionen/Ladungen und explizite H in eckigen Klammern |
| `[Na+].[Cl-]` | getrennte Teilchen mit `.` |
| `COOH`, `CHO`, `CO`, `NH2`, `OH`, `CN` | erkannte funktionelle Gruppen |

Die Summenformel zeigt bei Ionen die **Netto-Ladung** an; in der Skelettformel werden
Ladungen hochgestellt am Atom dargestellt.

**Grenzen der 2D-Zeichnung:** ein Ring pro Molekül und keine getrennten Fragmente – solche
Strukturen (z. B. Naphthalin, Salze) werden **nicht** als 2D-Skelettformel gezeichnet, sind
aber als **Summenformel** und **3D-Modell** verfügbar. Keine Stereochemie. Unterstützte
Elemente in der 2D-Darstellung: C, H, N, O, S, P und Halogene (weitere via `[…]` für Formel/3D).

## Nutzung

Datei einfach im Browser öffnen (Doppelklick auf `index.html`) – funktioniert auch offline.

**Ausnahme 3D-Ansicht:** JSmol kann unter `file://` (Doppelklick) aus Browser-Sicherheitsgründen
nicht laden. Zum lokalen Testen deshalb **`start-lokal.bat`** doppelklicken – sie startet einen
Mini-Webserver (Python) und öffnet das Tool unter `http://localhost:8124`. Auf dem Webserver
läuft die 3D-Ansicht ohne Weiteres.

## In eine Website einbinden

**Variante 1 – iframe** (empfohlen): `index.html` auf den Webspace hochladen und einbetten:

```html
<iframe src="/pfad/zu/index.html" width="100%" height="560"
        style="border:none; border-radius:12px;"></iframe>
```

**Variante 2 – direkt integrieren**: Den Inhalt von `<style>`, dem `<div class="app">`
und `<script>` in die eigene Seite kopieren.

> Hinweis: Das Kopieren in die Zwischenablage (Clipboard API) funktioniert nur über
> **HTTPS** oder `localhost`. Der Download-Button funktioniert immer.

## URL-Parameter & Link teilen

Das Tool lässt sich mit einer vorbelegten Gleichung öffnen:

```
index.html?eq=CH4%20%2B%20O2%20-%3E%20CO2%20%2B%20H2O&mode=check
```

- `eq` – die Gleichung bzw. Strukturformel (URL-kodiert; der Button **„🔗 Link kopieren“**
  im Tool erzeugt solche Links automatisch)
- `mode` – `check` (Prüfen), `stoich` (Stöchiometrie), `ox` (Oxidationszahlen),
  `ph` (Säuren & Basen), `titr` (Titration), `atom` (Atombau), `galv` (Galvanik &
  Elektrolyse), `reihe` (Spannungsreihe), `struct` (Strukturformeln),
  `lattice` (Kristallgitter), `mech` (Mechanismen) – sonst automatisches Ausgleichen.
  Modusspezifische Zusatzparameter (Stoff, Konzentrationen, Element, Halbzellen …)
  erzeugt „🔗 Link kopieren“ automatisch mit.
- `stil` – `voll` für ausgeschriebene C und H im Strukturmodus (sonst Skelettformel)
- `form` – `linear` für die 90°-Schulbuch-Geometrie (nur zusammen mit `stil=voll`)
- `ep` – `1` blendet freie Elektronenpaare ein (nur zusammen mit `stil=voll`)

## oEmbed-Schnittstelle ([oembed.com](https://oembed.com/))

Damit können oEmbed-fähige Plattformen (WordPress, Moodle mit oEmbed-Filter, …) das Tool
automatisch einbetten, wenn man dort nur den Link einfügt. **Voraussetzung:** Das Tool ist
öffentlich unter einer festen HTTPS-Adresse gehostet – mit `localhost` oder einer lokalen
Datei funktioniert oEmbed nicht.

### Einrichtung

1. Alle Dateien auf den Webspace hochladen, z. B. nach `https://deine-schule.de/chem-tool/`.
2. Den Platzhalter `https://DEINE-DOMAIN.example/chem-tool/` durch die echte Adresse ersetzen, und zwar in:
   - `index.html` (der `<link rel="alternate" …>` Discovery-Tag im `<head>`)
   - `oembed.php` (Variable `$base`) **oder** `oembed.json` (beide URLs)

### Zwei Varianten

| Datei | Voraussetzung | Verhalten |
|---|---|---|
| `oembed.php` (empfohlen) | Hosting mit PHP | Dynamisch: bettet auch Links mit konkreter Gleichung (`?eq=…`) ein, unterstützt `maxwidth`/`maxheight` und `format=json/xml` |
| `oembed.json` | beliebiges statisches Hosting | Fest: liefert immer denselben iframe auf die Startseite |

Bei der statischen Variante im Discovery-Tag in `index.html` einfach `oembed.json` als
`href` eintragen.

### Hinweise zu Plattformen

- **WordPress** nutzt oEmbed-Discovery aus Sicherheitsgründen nur für Autoren mit der
  Berechtigung `unfiltered_html`. Zuverlässiger ist es, den eigenen Endpoint im Theme
  (functions.php) zu registrieren:
  ```php
  wp_oembed_add_provider('https://deine-schule.de/chem-tool/*',
                         'https://deine-schule.de/chem-tool/oembed.php');
  ```
- **Moodle** braucht das oEmbed-Filter-Plugin.
- Plattformen ohne oEmbed: einfach das iframe-Snippet von oben verwenden.

## Repository klonen / Entwicklung

Das Tool besteht im Kern aus statischen Dateien – kein Build-Schritt nötig.

```bash
git clone https://github.com/f1nkster/chedit.git
cd chedit
```

Für die 3D-Ansicht ist zusätzlich **JSmol** nötig. Es ist bewusst **nicht** im Repo
enthalten (Drittsoftware, ~100 MB). Zum lokalen Testen JSmol von
<https://jsmol.sourceforge.net/> herunterladen und den Ordner als `jsmol/` neben
`index.html` legen, dann `start-lokal.bat` doppelklicken (startet einen lokalen
Webserver – nötig, weil Browser JSmol unter `file://` blockieren). Auf einem Webserver
mit vorhandener JSmol-Installation genügt der Fallback bzw. der Parameter `?jsmol=…`.

## Lizenz & Danksagungen

Der Quellcode steht unter der [MIT-Lizenz](LICENSE) – frei nutzbar, anpassbar und
weitergebbar. Für die mitgelieferten Logos (FAU / Lehrstuhl), die Schriftart
(Source Sans 3, SIL OFL) und das extern eingebundene JSmol (LGPL) gelten eigene
Bedingungen; Details in [NOTICE.md](NOTICE.md).
