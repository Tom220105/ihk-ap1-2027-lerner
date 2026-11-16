# IHK AP1 2027 Lerner

Lern-App für **Teil 1 der gestreckten Abschlussprüfung (AP1) der IT-Berufe**, Prüfungsbereich „Einrichten eines IT-gestützten Arbeitsplatzes“ (schriftlich, 90 Minuten, 20 % der Gesamtnote). Aufgebaut entlang der Lernfelder LF01–LF06 für Kaufleute für IT-System-Management, Fachinformatik und verwandte IT-Berufe.

Die App ist eine einzelne HTML-Seite ohne Build-Schritt und ohne Server.

## Funktionen

- **248 Übungsaufgaben** zu LF01–LF06 mit hinterlegter Lösung und Erklärung bzw. Rechenweg
  - Ankreuzen (eine oder mehrere Antworten), Rechenaufgaben, exakte Eingaben (z. B. Subnetzmasken, Binärzahlen) und offene Aufgaben mit Musterlösung
- **Lernen** nach Lernfeld, Thema und Aufgabenart. Unbekannte und unsichere Fragen kommen zuerst.
- **Wiederholen** mit Karteikasten (Spaced Repetition): Richtige Antworten kommen nach 1, 2, 4, 8 und 16 Tagen wieder, falsche noch am selben Tag.
- **Prüfungssimulation**: 25 Aufgaben aus allen Lernfeldern, 90-Minuten-Timer, Auswertung nach IHK-Notenschlüssel
- **Formelsammlung**: Speichereinheiten, Bild- und Videogrößen, Übertragungsdauer, RAID, Energie, Kennzahlen, Handelskalkulation, Verfügbarkeit, Amortisation, Subnetting, Netzplan
- **Countdown** bis zum Prüfungstermin (voreingestellt 24.02.2027, in der App änderbar)

## Nutzung

**Online:** Mit aktivierten GitHub Pages läuft die App unter
<https://tom220105.github.io/ihk-ap1-2027-lerner/>

**Lokal:** Repository klonen oder als ZIP herunterladen und `index.html` im Browser öffnen.

```bash
git clone https://github.com/Tom220105/ihk-ap1-2027-lerner.git
```

Der Lernfortschritt wird im `localStorage` des Browsers gespeichert, also nur auf dem jeweiligen Gerät und im jeweiligen Browser. Wer Browserdaten löscht, löscht auch den Fortschritt.

## Aufbau

| Datei | Inhalt |
| --- | --- |
| `index.html` | App: Oberfläche, Lernlogik, Karteikasten, Prüfungssimulation, Formelsammlung |
| `fragen.js` | Fragenkatalog (`window.FRAGEN`) und Lernfeld-Liste (`window.LERNFELDER`) |

### Eigene Fragen ergänzen

Neue Fragen kommen als Objekt in das Array `window.FRAGEN` in `fragen.js`. Jede `id` muss eindeutig bleiben, weil der Lernfortschritt daran hängt.

```js
{id:"l2-99", lf:2, t:"RAID & Backup", y:"num",
 q:"Wie groß ist die Nettokapazität eines RAID 5 aus 4 Platten à 8 TB?",
 a:24, u:"TB", e:"(n − 1) × C = 3 × 8 TB = 24 TB"}
```

| Feld | Bedeutung |
| --- | --- |
| `y` | Typ: `mc` (eine Antwort), `multi` (mehrere), `num` (Zahl), `text` (exakte Eingabe), `open` (Musterlösung) |
| `o` | Antwortoptionen bei `mc` und `multi` |
| `a` | Lösung: Index (`mc`), Index-Liste (`multi`), Zahl (`num`), Liste erlaubter Antworten (`text`) oder Musterlösung als HTML (`open`) |
| `e` | Erklärung bzw. Rechenweg |
| `u`, `tol`, `h` | Einheit, erlaubte Abweichung (Standard 0,011) und Hinweis bei Rechenaufgaben |

## Hinweise zu den Inhalten

- Alle Aufgaben sind **eigene Übungsaufgaben**. Sie orientieren sich an den Inhalten der Lernfelder, sind aber **keine Original-IHK-Prüfungsaufgaben**.
- Rechtliche Angaben (z. B. GmbHG, HGB, BGB, DSGVO, MoPeG, E-Rechnung) entsprechen dem Stand November 2026.
- Den Prüfungstermin bitte in der Einladung der zuständigen IHK prüfen.
- Ohne Gewähr. Bei Widersprüchen gelten Unterricht, Gesetzestext und IHK.
