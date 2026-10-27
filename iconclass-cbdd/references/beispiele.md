# Beispiele aus der CbDD

Zwei echte CbDD-Datensätze aus Lindau, Damenstift, Festsaal (Franz Joseph Spiegler, 1736). Sie zeigen die Bandbreite: Beispiel 2 ist der Normalfall, Beispiel 1 die erschöpfende Maximalvariante.

## Beispiel 2 – Normalfall (Malereiteil)

- **Objekt:** „Die Vernunft als Wagenlenkerin“ (alternativ: Ratio), Typ *Malereiteil*
- **https://deckenmalerei.eu/85eef01b-bda5-4b14-b01b-f088f2cd67b6**
- **Bild:** schwebende Frau in blauem Kleid mit grünem Mantel, hält Zügel hoch, Stern über dem Kopf; Zügel führen zum Wagen, weitere Figuren angeschnitten.
- **Text (Auszug, Lab-Abschnitt „Die Ratio: Vernunft als unsterbliche Seele und Adel der Tugend“):** „… ist als Allegorie der *Ratio* zu bestimmen … Ripa beschreibt sie als himmelblau gekleidete Frau … auch die Zügel als ihr Attribut … der Stern über dem Haupt der Vernunft … als unsterbliche Seele … Hinweis auf den Adel.“
- **CbDD-Iconclass:** `52B5(+2) 24D`

Erwartete Ausgabe der Skill (gekürzt):

| # | Notation | Bezeichnung | Begründung | Sicherheit |
|---|----------|-------------|------------|------------|
| 1 | [52B5(+2)](https://iconclass.org/de/52B5%28%2B2%29) | Rationalität, Vernunft, Verstand; Ripa: Ratiocinatione o Discorso (+ allegorische Szene …) | im Text als Ratio bestimmt (Ripa: blaues Kleid, Zügel); lenkt den Tugendwagen, also Teil einer Gruppenhandlung → (+2) | hoch |
| 2 | [24D](https://iconclass.org/de/24D) | Sterne | Stern über dem Haupt, nach Ripa unsterbliche Seele / Adel | hoch |

**Zum Kopieren:** `52B5(+2) 24D`

Lehre: Nur die Figur des Ausschnitts kodieren, nicht das ganze Programm (Virtus, Laster, Ecclesia …). Ältere, im Text verworfene Deutungen („Gnade“, „Glaube“) werden **nicht** vorgeschlagen.

## Beispiel 1 – Maximalvariante (Malerei, ganzes Deckenbild)

- **Objekt:** „Die Christliche Tugend triumphiert über die Laster“, Typ *Malerei*, Freskomalerei, Decke, 1736
- **https://deckenmalerei.eu/81af98ae-93b5-45c8-be2e-8964bbcba29b**
- **Inschriften:** „POST CONCUPISCENTIAS TUAS NON EAS Eccl. 18, 30 …“, „SEMPER HONOS NOMENQUE TUUM LAUDESQUE MANEBUNT“, „DAS ALTER VON DER JUGENT / DER ADEL VON DER TUGENT“, Signatur Spiegler 1736
- **CbDD-Iconclass (vollständige Erschließung, über 90 Codes):**

```
11D121 11F2 11M31 11M32 11MM41 11MM42 11MM43 11MM44 11NN32 11NN33 11NN35 11NN36 11P11 11P31111 11P31131 22C31 23D4 23R11 23R113 23R13 23R14 24 24A6 24D 25F24(STAG) 25F28(BAT) 25F33(EAGLE) 25F33(FALCON)(+13) 25F34 25F35(PARROT) 25F42 25G3(LAUREL)(+221) 25G3(OLIVE-TREE)(+221) 25G41(POPPY) 25G41(ROSE) 25H216 26A 31A22210 31A511 31AA3191 33C91 34B11 34B12 41A3281 41A422 41A541 41B121 41B32 41C321 41C711 41D2632 43A421 43C1147 44A1(+6) 44B191 44B192 44BB191 44G3129 45A232 45C11(SPEAR) 45C13(SWORD) 45C14(PIKE) 45C15(BOW AND ARROW) 45C22 45C221 46B3311 46C13142 46C215(ANCHOR) 47D8(CHAIN) 47G52 47I21211 47I2133 48C161 48C7352 48CC7352 52A51(+2) 52AA1(+2) 52B5(+2) 53A1(+2) 54A44(+1) 57A6(+2) 59B32(+2) 59CC2(+2) 71Y4 92B11221 92B37 92C37 92C38 92D191 92D1916 92M27 96A237
```

Das ist **nicht** der Standard. Ohne ausdrückliche Bitte um Vollständigkeit wäre für dieses Bild eine Auswahl wie diese angemessen (Reihenfolge = Rang):

1. `11MM4` bzw. die vier `11MM41`–`11MM44` – Triumph der Kardinaltugenden (Hauptthema)
2. `57A6(+2)` – Tugendhaftigkeit / Virtù im Triumphwagen
3. `43A421` – Triumphwagen
4. `11NN3…` – unterlegene Laster (Neid etc.), soweit im Text benannt
5. `52B5(+2)` – Ratio als Wagenlenkerin
6. `59B32(+2)` – Fama mit Posaune
7. `11P11` – Ecclesia mit Tiara, Kreuz und Schlüssel
8. `71Y4` – Inschrift aus Jesus Sirach

Lehre: Bei großen Programmbildern zuerst Hauptthema und Hauptfiguren; Tiere, Pflanzen, Waffen, Kleidung, Ornament nur in der ausführlichen Variante.
