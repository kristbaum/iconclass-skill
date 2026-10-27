# CbDD-Konventionen für Iconclass

Abgeleitet aus vorhandenen CbDD-Datensätzen (u. a. Lindau, Damenstift, Festsaal, Spiegler 1736). Alle hier genannten Codes wurden über den Iconclass-MCP geprüft – trotzdem vor der Ausgabe erneut per `resolve` bestätigen.

## Inhalt

1. Allgemeine Muster
2. Personifikationen und Schlüssel (+1)/(+2)
3. Tugenden und Laster: 11M/11N und 5er-Äste
4. Häufige Äste in barocker Deckenmalerei
5. Benannte Notationen (NAME) und Tier-/Pflanzen-Schlüssel
6. Inschriften, Wappen, Signaturen

---

## 1. Allgemeine Muster

- **Die CbDD kodiert die Deutung, nicht nur den Seheindruck.** Wenn der Text eine Figur als *Ratio* bestimmt, wird Vernunft kodiert, auch wenn die Figur allein aus dem Bild als „Frau mit Zügeln“ erscheinen würde.
- **Ripa ist der Referenzrahmen.** Viele Iconclass-Labels im Ast 5 nennen die Ripa-Begriffe („Ripa: Fama, Fama buona …“). Nennt der CbDD-Text eine Ripa-Personifikation, zuerst im Ast 5 suchen, ggf. mit dem italienischen Ripa-Begriff als `query`.
- **Malerei vs. Malereiteil.** Das Gesamtbild (*Malerei*) bekommt Hauptthema plus alle wichtigen Figuren; ein *Malereiteil* (eine Figur/Gruppe) nur die Notationen dieser Figur und ihrer Attribute. Beispiel: Malereiteil „Die Vernunft als Wagenlenkerin“ → nur `52B5(+2) 24D`.
- **Attribute separat.** Bedeutungstragende Attribute werden als eigene Notationen erfasst (Stern → `24D`, Schlüssel → `41A3281`, Tiara → `11P31111`, Trompete → `48C7352`, Triumphwagen → `43A421`).
- **Christlich und allgemein-allegorisch nebeneinander.** Bei Tugendprogrammen kodiert die CbDD häufig sowohl die christliche Tugend (11M…) als auch den abstrakten Begriff (5…), wenn beide Lesarten im Text angelegt sind.

## 2. Personifikationen und Schlüssel (+1)/(+2)

Im Ast **5 (abstrakte Ideen)** und einigen anderen Ästen gelten diese Schlüssel (Label immer prüfen):

| Schlüssel | Bedeutung | CbDD-Einsatz |
|---|---|---|
| `(+1)` | Personifikation | Einzelfigur, z. B. Tugend allein in einer Kartusche → `54A44(+1)` Geduld |
| `(+2)` | allegorische Szene (zwei oder mehr Personifikationen in einer Handlung) | Figur als Teil einer Gruppenhandlung, z. B. Ratio lenkt den Tugendwagen → `52B5(+2)` |
| `(+3)` | symbolische Darstellung einer Konzeption | Begriff ohne Personifikation, nur durch Symbole |
| `(+21)`, `(+22)` | Unterformen von (+2) | nur, wenn Text/Bild das ausdrücklich tragen |

Faustregel: **Einzelfigur → (+1), Teil eines allegorischen Geschehens → (+2).** Im großen Lindauer Mittelbild sind deshalb fast alle Personifikationen mit `(+2)` kodiert (`52A51(+2)` Weisheit, `57A6(+2)` Tugendhaftigkeit, `59B32(+2)` Fama, `59CC2(+2)` Ungerechtigkeit, `52AA1(+2)` Dummheit), die Eckkartusche mit Geduld dagegen mit `(+1)`.

Die Bedeutung der Schlüssel ist astabhängig: Bei `92D1916` (Putten) heißt `(+2)` z. B. „Liebesaffären“. Daher Schlüssel nie übertragen, sondern per `expand_keys` nachsehen.

## 3. Tugenden und Laster

| Bereich | Notation | Hinweis |
|---|---|---|
| Sapientia und die sieben Tugenden | `11M` | christlicher Kontext |
| theologische Tugenden | `11M3` (Glaube `11M31`, …) | |
| Kardinaltugenden | `11M4` (Klugheit `11M41` …) | |
| **Triumph** der Tugenden | `11MM…` (z. B. `11MM41`–`11MM44` Kardinaltugenden, `11MM31`) | Doppelbuchstabe = „Triumph“ bzw. Gegenteil – Label lesen |
| Laster, Todsünden | `11N`, Personifikationen `11N3…` | |
| **Triumph** über/der Laster | `11NN3…` (z. B. `11NN32` Neid) | |
| Tugendhaftigkeit, Virtù (Ripa) | `57A6(+1)` / `57A6(+2)` | allgemeine *Virtus* |
| römische Virtus | `96A5(VIRTUS)` | nur bei explizit antikem Kontext |
| Fama (Ripa: Fama buona) | `59B32(+1)` / `59B32(+2)` | Posaune → zusätzlich `48C7352` |
| Weisheit (Sapienza) | `52A51(+…)` | |
| Vernunft (Ratiocinatione) | `52B5(+…)` | |
| Ecclesia | `11P11` | Tiara `11P31111`, Schlüssel `41A3281` |

Gegenbegriffe stehen im Ast 5 unter doppeltem Buchstaben (`52AA` Unintelligenz, `59CC` Ungerechtigkeit, `57AA` Laster allgemein).

## 4. Häufige Äste in barocker Deckenmalerei

| Thema | Einstieg |
|---|---|
| Christus, Symbole Christi | `11D` (Kreuz als Christussymbol `11D121`) |
| Maria | `11F` (Maria ohne Kind `11F2`) |
| Engel | `11G` (als Kinder dargestellt `11G191`) |
| Heilige | `11H(NAME)` männlich, `11HH(NAME)` weiblich – Namen auf Englisch, z. B. `11H(AUGUSTINE)` |
| Himmel, Paradies | `11S` |
| Kirche als Institution | `11P` |
| Licht, Strahlen | `22C31` |
| Jahreszeiten | `23D4` (Winter `23D41` …) |
| Tageszeiten | `23R1…` (Morgen `23R11`, Mittag `23R113`) |
| Sonne, Sterne | `24A`, `24D` |
| Wolken | `26A` |
| Triumphzug, Triumphwagen | `43A42`, `43A421` |
| Frieden und Wohlstand | `45A232` |
| Putten, Amoretten | `92D1916` (Triumph-Kontext `92D1916(+78)`) |
| Altes / Neues Testament | `71…` / `73…` |
| antike Götter | `92…` (griechisch-römisch), römische Personifikationen `96A5(NAME)` |

Bei Putten unterscheiden: profane/mythologische Putten → `92D1916`; Engelsputten im christlichen Kontext → `11G191`. Im Lindauer Allegorie-Programm hat die CbDD `92D1916` verwendet.

## 5. Benannte Notationen und Schlüssel bei Tieren/Pflanzen/Objekten

- Namen in Klammern sind **englisch und großgeschrieben**: `25F33(EAGLE)`, `25F35(PARROT)`, `25G41(ROSE)`, `45C13(SWORD)`, `45C15(BOW AND ARROW)`, `46C215(ANCHOR)`, `47D8(CHAIN)`.
- Tiere: `25F…`; Schlüssel `(+1)` = als Symbol, `(+12)` = Wappentier, `(+13)` = als Attribut → `25F33(FALCON)(+13)`.
- Pflanzen: `25G…`; `(+221)` = Zweig → `25G3(LAUREL)(+221)` Lorbeerzweig, `25G3(OLIVE-TREE)(+221)` Ölzweig.
- Ob ein Name existiert, immer per `resolve` prüfen; sonst die unbenannte Elternnotation nehmen.
- Vorsicht bei Tieren im Lastenkontext: `46C13142` ist der Esel als Reit-/Lasttier, nicht als Symboltier.

## 6. Inschriften, Wappen, Signaturen

- **Bibelzitate** → das Bibelbuch kodieren, z. B. „Eccl. 18, 30“ (Jesus Sirach) → `71Y4`. Bei Psalmen, Evangelien etc. entsprechend im Ast 71/73 suchen.
- **Wappen** → `46A122` (Wappenschild, heraldisch) oder `44A1(+6)` (Wappen einer kirchlichen Gemeinschaft); im Lindauer Damenstift wurde `44A1(+6)` verwendet.
- **Malersignatur / Künstler im Bild** → nur kodieren, wenn ikonographisch relevant (Selbstbildnis etc.).
