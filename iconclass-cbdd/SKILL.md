---
name: iconclass-cbdd
description: Schlägt passende Iconclass-Notationen für ein Bild (Foto) und/oder einen kunsthistorischen Beschreibungstext vor, abgestimmt auf die Erschließungspraxis des Corpus der barocken Deckenmalerei in Deutschland (CbDD, deckenmalerei.eu / Deckenmalerei-Lab). Liefert eine nach Präzision und Passgenauigkeit gereihte Liste mit Notation, Bezeichnung und anklickbarem Link auf iconclass.org. Benötigt zwingend den Iconclass-MCP-Server. Verwenden, wenn jemand Iconclass-Codes, Notationen oder eine ikonographische Verschlagwortung für ein Deckenbild, Fresko, eine Kartusche, Personifikation, Allegorie, Heiligen- oder Mythologieszene sucht – auch bei Formulierungen wie "welche Iconclass passt", "verschlagworte dieses Bild", "Iconclass für diesen Abschnitt", "suggest Iconclass codes", "tag this image with Iconclass". Deutsch ist Standard, Englisch auf Wunsch.
---

# Iconclass-Vorschläge für die CbDD

Ziel: Aus einem Bild, einem kunsthistorischen Text oder beidem eine **kleine, gut begründete, gereihte Auswahl** von Iconclass-Notationen erzeugen, wie sie eine CbDD-Redakteurin in das Iconclass-Feld eines Objekts (Typ *Malerei* oder *Malereiteil*) eintragen würde.

## Voraussetzung: Iconclass-MCP

Diese Skill arbeitet **nur** mit dem Iconclass-MCP-Server (Tools `search`, `resolve`, `browse`, `expand_keys`, `search_prefix`).

- Sind die Tools nicht verfügbar oder schlagen alle Aufrufe fehl: abbrechen und der Nutzerin mitteilen, dass der Iconclass-MCP-Server verbunden sein muss. **Keine Notationen aus dem Gedächtnis ausgeben** – Iconclass-Codes sind leicht zu verwechseln, und ein unbelegter Code ist schlimmer als keiner.
- Jede ausgegebene Notation muss vorher per `resolve` bestätigt worden sein (bis zu 25 pro Aufruf; Codes in `notFound` werden verworfen oder ersetzt).

Optional: Ist der Deckenmalerei-Lab-MCP verfügbar und nennt die Nutzerin eine Lab-Seite, einen Abschnitt oder eine deckenmalerei.eu-ID, darf der Text von dort geholt werden (`get-page` mit `section`). Das ist eine Bequemlichkeit, keine Voraussetzung.

## Sprache

- Antwortsprache = Sprache der Anfrage; ohne klare Anfrage (nur Bild) **Deutsch**.
- Bezeichnungen mit `lang: "de"` bzw. `lang: "en"` abrufen. Wünscht die Nutzerin beide Sprachen, `resolve` zweimal aufrufen und beide Labels zeigen.
- Die Labels exakt so übernehmen, wie Iconclass sie liefert (nicht umformulieren, nicht übersetzen).

## Ablauf

### 1. Eingabe auswerten

Zuerst feststellen, was vorliegt, und intern eine Liste der **ikonographischen Elemente** erstellen:

- **Hauptthema / Bildaussage** (z. B. Triumph der Tugend über die Laster, Himmelfahrt Mariens, Apotheose eines Heiligen, Jahreszeitenzyklus).
- **Identifizierte Figuren**: Personifikationen, Tugenden/Laster, Heilige, biblische Personen, Götter, historische Personen, Putten/Engel.
- **Bedeutungstragende Attribute und Motive**: Stern, Zügel, Kreuz, Schlüssel, Tiara, Lorbeer, Waffen, Tiere, Pflanzen, Triumphwagen, Wappen.
- **Inschriften** (Bibelzitate → Bibelbuch, Devisen, Signaturen).
- **Funktion des Ausschnitts**: ganzes Deckenbild (*Malerei*) oder einzelne Figur/Gruppe (*Malereiteil*).

Wie mit den Quellen umgehen:

- **Text vorhanden** → Die Deutung im Text hat Vorrang vor dem eigenen Seheindruck. CbDD-Texte diskutieren oft konkurrierende Deutungen („bisher als Gnade bzw. Glaube gedeutet … ist als Ratio zu bestimmen“): die vom Text **vertretene** Deutung kodieren, verworfene Deutungen nicht. Bei echter Unentschiedenheit des Texts beide nennen und kennzeichnen.
- **Nur Bild** → Nur kodieren, was sichtbar oder über eindeutige Attribute (Ripa-Tradition) erschließbar ist. Unsichere Identifizierungen ausdrücklich als Vermutung markieren und niedriger reihen. Wenn eine sichere Deutung ohne Kontext unmöglich ist, kurz sagen, welche Information (Ort, Raum, Programm, Inschrift) helfen würde.
- **Bild + Text** → Text liefert die Deutung, Bild bestätigt und ergänzt Attribute. Widersprüche benennen.
- Bezieht sich der Text auf ein größeres Programm, das Bild aber nur auf einen Ausschnitt (Beispiel 2 in [references/beispiele.md](references/beispiele.md)), **nur den Ausschnitt** kodieren.

### 2. Notationen suchen

Für jedes Element gezielt suchen; erst breit orientieren, dann in die Tiefe:

- `search` mit `query` (Stichwort, `lang: "de"`): funktioniert gut mit deutschen **und** Ripa-Begriffen (z. B. „Vernunft“, „Fama“, „Temperanza“, „Triumphwagen“, „Putto“).
- `search` mit `semanticQuery`: für Konzepte und Szenen; am besten **auf Englisch** formulieren (deutsche semantische Anfragen liefern schwächere Treffer).
- `parentNotation` einsetzen, um im richtigen Ast zu bleiben (z. B. `11M` für Tugenden, `11N` für Laster, `5` für abstrakte Begriffe, `73` für Neues Testament).
- `browse` (depth 1–2), um vom gefundenen Begriff zum **spezifischsten passenden** Kind zu kommen.
- `expand_keys` bzw. `browse` mit `includeKeys`, um den richtigen Schlüssel-Zusatz zu finden – **die Bedeutung von (+1), (+2) … ist astabhängig**, immer das zurückgegebene Label lesen.

Die CbDD-typischen Äste, Schlüssel und Muster stehen in [references/cbdd-konventionen.md](references/cbdd-konventionen.md). Diese Datei vor der Suche lesen, wenn das Bild Personifikationen, Tugenden/Laster, Putten, Tiere, Pflanzen oder Attribute enthält.

### 3. Prüfen

Alle Kandidaten in **einem** `resolve`-Aufruf bestätigen (max. 25). Dabei prüfen:

- Existiert der Code? (`notFound` → verwerfen oder Alternative suchen)
- Passt der **Pfad** (Hierarchie) zum Gemeinten? Gleichlautende Begriffe in falschen Ästen sind die häufigste Fehlerquelle (z. B. „Esel“ als Lasttier 46C13142 vs. als Symboltier 25F…).
- Ist es die **spezifischste belegte** Ebene – aber nicht spezifischer, als Bild/Text hergeben?
- Doppelungen vermeiden: Ein spezifischer Code macht seinen Elternknoten überflüssig.

### 4. Reihen und auswählen

Reihenfolge nach **Präzision und Passgenauigkeit**:

1. **Hauptthema** – die Notation, die das Bild als Ganzes am genauesten trifft.
2. **Zentrale Figuren** – sicher identifizierte Personifikationen, Heilige, Götter mit passendem Schlüssel.
3. **Ikonographisch tragende Attribute/Motive** – nur, wenn sie für die Deutung wichtig sind (der Stern über der Ratio, der Triumphwagen der Virtus).
4. **Ergänzend / unsicher** – plausibel, aber weniger belegt oder nebensächlich.

Umfang: **Standard 3–8 Notationen.** Lieber wenige, sicher passende als viele mittelmäßige. Eine erschöpfende Erschließung jeder Figur und jedes Attributs (wie Beispiel 1 mit über 90 Codes) **nur auf ausdrückliche Bitte** („vollständig“, „alle Details“, „ausführlich“). Dekoratives Allgemeingut (Wolken, Draperie) nur in der ausführlichen Variante.

### 5. Ausgabe

Format (auf Deutsch; auf Englisch Spalten entsprechend übersetzen):

```markdown
**Vorschläge für: <kurzer Titel oder Bildbeschreibung>**

| # | Notation | Bezeichnung | Begründung | Sicherheit |
|---|----------|-------------|------------|------------|
| 1 | [52B5(+2)](https://iconclass.org/de/52B5%28%2B2%29) | Rationalität, Vernunft, Verstand; Ripa: Ratiocinatione o Discorso (+ allegorische Szene …) | Wagenlenkerin mit Zügeln, im Text als *Ratio* bestimmt; Teil einer Gruppenhandlung → (+2) | hoch |
| 2 | [24D](https://iconclass.org/de/24D) | Sterne | Stern über dem Haupt als Attribut (unsterbliche Seele / Adel nach Ripa) | hoch |

**Zum Kopieren:** `52B5(+2) 24D`
```

Regeln:

- **Link**: `https://iconclass.org/de/<Notation>` (bzw. `/en/` bei englischer Ausgabe). In der URL `(` → `%28`, `)` → `%29`, `+` → `%2B`, Leerzeichen → `%20`. Der sichtbare Linktext bleibt die unkodierte Notation. Beispiel: `[45C15(BOW AND ARROW)](https://iconclass.org/de/45C15%28BOW%20AND%20ARROW%29)`.
- **Bezeichnung**: das Label aus `resolve`, bei sehr langen Labels sinnvoll mit „…“ kürzen.
- **Begründung**: ein Satz, der auf das konkrete Indiz verweist (Attribut im Bild, Textstelle, Inschrift).
- **Sicherheit**: hoch / mittel / niedrig (en: high / medium / low).
- **Zum Kopieren**: alle Notationen der Tabelle, durch Leerzeichen getrennt, in Tabellenreihenfolge – das entspricht dem Format des CbDD-Iconclass-Felds.
- Danach optional **1–3 Zeilen** zu Unsicherheiten, verworfenen Alternativen oder was die Zuordnung verbessern würde. Kein langer Fließtext.

## Grenzen

- Keine Notationen erfinden oder „konstruieren“ (z. B. eigene Klammer-Namen wie `25F33(KRANICH)`), ohne sie per `resolve` zu bestätigen. Wenn ein benanntes Tier/Pflanze/Objekt nicht existiert, die nächsthöhere Ebene ohne Namen nehmen und das vermerken.
- Bei Bildern ohne erkennbares ikonographisches Thema (reine Ornamentik, Stuck, Architekturmalerei) das sagen und nur die passenden Ornament-/Architektur-Notationen vorschlagen.
