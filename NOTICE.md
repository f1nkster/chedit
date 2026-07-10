# Rechtliche Hinweise & Danksagungen

Der **Quellcode** von ChEdit steht unter der [MIT-Lizenz](LICENSE). Für die
folgenden mitgelieferten oder eingebundenen Bestandteile gelten davon abweichende
Bedingungen:

## Logos (nicht von der MIT-Lizenz abgedeckt)

- **FAU-/Lehrstuhl-Logo** (`assets/logo-chemiedidaktik.svg`) – geschützte Wort-/Bildmarke
  der FAU Erlangen-Nürnberg. **Nicht in diesem Repository enthalten** und nicht frei
  weiterverwendbar. Der Header blendet den Logo-Platz aus, wenn die Datei fehlt.
- `assets/logo-chedit.svg` – ChEdit-Wortmarke, für dieses Projekt gestaltet (im Repo enthalten).

Wer ChEdit forkt oder für eine andere Einrichtung einsetzt, sollte diese Logos
durch eigene ersetzen.

## Schriftart

- `assets/source-sans-3.woff2` – **Source Sans 3**, © 2010–2020 Adobe, lizenziert
  unter der [SIL Open Font License 1.1](https://openfontlicense.org/). Freie
  Nutzung und Weitergabe erlaubt.

## Extern eingebundene Software

- **JSmol / Jmol** – wird für die 3D-Modelle genutzt, aber **nicht** in diesem Repo
  mitgeliefert (siehe `.gitignore`). ChEdit lädt JSmol zur Laufzeit vom Server bzw.
  aus einem separat abgelegten `jsmol/`-Ordner. JSmol steht unter der
  [LGPL 2.1](https://www.gnu.org/licenses/lgpl-2.1.html).
  Projektseite: https://jsmol.sourceforge.net/

Um die 3D-Ansicht lokal zu testen, JSmol von der Projektseite herunterladen und den
Ordner als `jsmol/` neben `index.html` legen (oder eine vorhandene Server-Installation
über den Parameter `?jsmol=…` einbinden – siehe README).
