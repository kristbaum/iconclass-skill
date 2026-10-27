# iconclass-cbdd

Skill für Claude, die Iconclass-Notationen für Bilder und/oder kunsthistorische Texte vorschlägt, abgestimmt auf das *Corpus der barocken Deckenmalerei in Deutschland* (CbDD, [deckenmalerei.eu](https://deckenmalerei.eu), [Deckenmalerei-Lab](https://deckenmalerei-lab.badw.de)).

- Eingabe: Foto, Beschreibungstext (z. B. ein Abschnitt aus dem Deckenmalerei-Lab) oder beides
- Ausgabe: gereihte Tabelle mit Notation (Link auf iconclass.org), Bezeichnung, Begründung, Sicherheit, plus eine kopierfertige Codezeile im Format des CbDD-Iconclass-Felds
- Sprache: Deutsch als Standard, Englisch auf Wunsch
- **Voraussetzung:** verbundener Iconclass-MCP-Server. Der Deckenmalerei-Lab-MCP ist optional (zum Holen von Texten).

## Aufbau

- [iconclass-cbdd/SKILL.md](iconclass-cbdd/SKILL.md) – Arbeitsablauf und Ausgabeformat
- [iconclass-cbdd/references/cbdd-konventionen.md](iconclass-cbdd/references/cbdd-konventionen.md) – CbDD-typische Äste, Schlüssel (+1)/(+2), Attribute
- [iconclass-cbdd/references/beispiele.md](iconclass-cbdd/references/beispiele.md) – die beiden Lindauer Beispiele unten, mit erwarteter Ausgabe

## Installation

- Claude Code: Ordner `iconclass-cbdd/` nach `~/.claude/skills/` (oder `.claude/skills/` im Projekt) kopieren.
- claude.ai: die fertige Datei [iconclass-cbdd.skill](iconclass-cbdd.skill) unter *Einstellungen → Skills* hochladen.

## Paket neu bauen

Die `.skill`-Datei ist ein ZIP-Archiv, das den Ordner `iconclass-cbdd/` (mit `SKILL.md` darin) als oberste Ebene enthält. Nach jeder Änderung an der Skill im Repo-Wurzelverzeichnis neu bauen:

```bash
rm -f iconclass-cbdd.skill
zip -r iconclass-cbdd.skill iconclass-cbdd -x '*.DS_Store' '*/__pycache__/*'
unzip -l iconclass-cbdd.skill   # Kontrolle: Pfade beginnen mit iconclass-cbdd/
```

Danach die neue `iconclass-cbdd.skill` mit committen.

## Testbilder

Example 1 fmd10021481a.jpg:
https://deckenmalerei.eu/81af98ae-93b5-45c8-be2e-8964bbcba29b
Name:
Die Christliche Tugend triumphiert über die Laster
ID:
81af98ae-93b5-45c8-be2e-8964bbcba29b
Typ:
Malerei
Iconclass:
11D121 11F2 11M31 11M32 11MM41 11MM42 11MM43 11MM44 11NN32 11NN33 11NN35 11NN36 11P11 11P31111 11P31131 22C31 23D4 23R11 23R113 23R13 23R14 24 24A6 24D 25F24(STAG) 25F28(BAT) 25F33(EAGLE) 25F33(FALCON)(+13) 25F34 25F35(PARROT) 25F42 25G3(LAUREL)(+221) 25G3(OLIVE-TREE)(+221) 25G41(POPPY) 25G41(ROSE) 25H216 26A 31A22210 31A511 31AA3191 33C91 34B11 34B12 41A3281 41A422 41A541 41B121 41B32 41C321 41C711 41D2632 43A421 43C1147 44A1(+6) 44B191 44B192 44BB191 44G3129 45A232 45C11(SPEAR) 45C13(SWORD) 45C14(PIKE) 45C15(BOW AND ARROW) 45C22 45C221 46B3311 46C13142 46C215(ANCHOR) 47D8(CHAIN) 47G52 47I21211 47I2133 48C161 48C7352 48CC7352 52A51(+2) 52AA1(+2) 52B5(+2) 53A1(+2) 54A44(+1) 57A6(+2) 59B32(+2) 59CC2(+2) 71Y4 92B11221 92B37 92C37 92C38 92D191 92D1916 92M27 96A237
Technik:
Freskomalerei
Material:
Putz
Position:
Decke
Inschrift:
„POST CONCUPISCENTIAS TUAS NON EAS Eccl. 18, 30 / deinen bösen Begierden gehe nicht nach.“, „SEMPER HONOS NOMENQUE TUUM LAUDESQUE MANEBUNT“, „DAS ALTER VON DER JUGENT / DER ADEL VON DER TUGENT“, „F:Jos:SPiegler Invenit et Pinxit 1736.“
Datierung [Malerei]:
1736


Example 2 P1010344.jpg:
https://deckenmalerei.eu/85eef01b-bda5-4b14-b01b-f088f2cd67b6
Name:
Die Vernunft als Wagenlenkerin
ID:
85eef01b-bda5-4b14-b01b-f088f2cd67b6
Typ:
Malereiteil
alternative Namen:
Ratio
Iconclass:
52B5(+2) 24D 