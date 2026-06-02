---
title: 'FFB-Konto neben IBKR — Steuererklärung in Österreich richtig erfassen (2026)'
date: 2026-06-02
lastmod: 2026-06-02
description: 'Praktischer Leitfaden für FFB-Konten (FIL Fondsbank) in der österreichischen E1kv: Warum keine KESt automatisch abgezogen wird, was die deutsche Jahresbescheinigung NICHT abdeckt, FIFO vs. gleitender Durchschnitt bei Sparplänen, KZ 937 bei thesaurierenden Fonds.'
keywords: ['FFB Steuererklärung Österreich', 'FIL Fondsbank E1kv', 'FFB Sparplan KESt Österreich', 'FFB Fonds Avg-Cost', 'FFB IBKR Steuer', 'FFB Jahresbescheinigung Österreich', 'thesaurierender Fonds FFB', 'FFB FinanzOnline']
tags: ['FFB', 'E1kv', 'Investmentfonds', 'Sparplan', 'Österreich']
---

# FFB-Konto neben IBKR — Steuererklärung in Österreich richtig erfassen

> **Stand:** 2026-06-02 · **Lesezeit:** ~8 Minuten · **Gilt für:** AT-Privatpersonen mit FFB-Sparplan oder Einmal­anlagen, Steuerjahr 2025

Viele österreichische Privatanleger haben **eine Mischsituation**: Aktien und ETFs bei IBKR (oder CapTrader / LYNX), und nebenbei einen **FFB-Sparplan** (FIL Fondsbank Deutschland) mit aktiv gemanagten Fonds — typischerweise DWS, Carmignac, Comgest, Pictet. Bei der Steuererklärung kommen dann zwei Welten zusammen:

- **IBKR** liefert Dir alles in einer FlexQuery — die App rechnet automatisch.
- **FFB** liefert eine deutsche **Jahressteuerbescheinigung**, die in Österreich **nicht 1:1 verwendbar** ist und keine FlexQuery-Export-Schnittstelle hat.

Konsequenz: Dein FFB-Teil **musst Du selbst erklären**, von Hand. Diese Seite erklärt **warum** (die KESt-Sondersituation), **was Du brauchst**, und wo die häufigsten Fehler liegen.

> 💡 Am Ende zeigen wir, wie Du FFB und IBKR **in einer einzigen Excel-Steuerberater-Mappe** zusammenführst — auch ohne Export.

## 1. Warum FFB-Konten in Deiner E1kv landen — die KESt-Falle

In Österreich gibt es zwei Wege, wie Kapital­einkünfte versteuert werden:

| Konstellation | Ergebnis |
|---|---|
| **Inländische depotführende Stelle** (Erste Bank, Raiffeisen, FFB **Österreich-Niederlassung*** o. Ä.) → KESt wird **automatisch abgezogen** | „Endbesteuerung", keine eigene Erklärung nötig |
| **Ausländische depotführende Stelle** (IBKR Irland, FFB Deutschland, CapTrader, LYNX) | **Du selbst in der E1kv erklären** und 27,5 % KESt vom Finanzamt einfordern |

> *Stand 2026 betreibt FFB (FIL Fondsbank GmbH) kein österreichisches steuerliches Vertretungsmodell mit automatischer KESt-Abfuhr für österreichische Privatkunden. Wenn sich das geändert hat, bitte vor Abgabe der Steuererklärung beim eigenen FFB-Berater oder direkt bei der FFB nachfragen.

**Praktische Konsequenz**: Auch wenn Dein FFB-Sparplan exakt 80 €/Monat in einen DWS-Fonds zahlt und „still vor sich hin läuft" — Du musst **jedes Jahr** in der E1kv:

- Realisierte Verkaufsgewinne erklären (KZ 994 / 892)
- Ausschüttungen erklären (KZ 863)
- Ausschüttungsgleiche Erträge erklären (KZ 937)
- Anrechenbare ausländische Quellensteuer ansetzen (KZ 384)

## 2. Was FFB Dir gibt — und was fehlt

FFB stellt typischerweise zur Verfügung:

- **Depotauszug** (Bestand zum Jahresende, pro Fonds und ISIN)
- **Steuerbescheinigung für Privatanleger** nach **deutschem** Steuerrecht — also mit Vorabpauschale, Teilfreistellungs-Quoten, deutscher Abgeltungsteuer-Logik
- **Transaktionsverlauf** (alle Käufe / Verkäufe des Jahres, meist als PDF)

Was **fehlt** für die österreichische E1kv:

- ❌ Kein FlexQuery- oder OFX-Export
- ❌ Kein Lot-Level-Tracking (FIFO / Avg-Cost in EUR mit FX-Kurs zum Tag)
- ❌ Keine **österreich-konforme** Anschaffungswerts-Korrektur für thesaurierte Erträge
- ❌ Keine OeKB-Kennzahlen (KZ 937, KZ 384) — die deutsche Vorabpauschale ist **nicht das gleiche** wie der österreichische ausschüttungsgleiche Ertrag

> ⚠️ **Achtung**: Die deutsche Steuerbescheinigung enthält Werte, die in Österreich **nicht direkt übernommen werden dürfen** — Vorabpauschale ≠ ausschüttungsgleicher Ertrag, deutsche Teilfreistellungen gelten in AT nicht. Wer die deutschen Zahlen 1:1 in KZ 937 einträgt, riskiert eine Berichtigung durch das Finanzamt.

## 3. Was Du tatsächlich brauchst — und wie Du's bekommst

Pro **ISIN** im FFB-Depot brauchst Du:

**Aus FFB selbst**:
- Alle Käufe (Datum, Stückzahl, Preis in EUR, Kosten)
- Alle Verkäufe (Datum, Stückzahl, Preis in EUR)
- Alle Ausschüttungen (Datum, Betrag in EUR — bei ausschüttenden Fonds)
- Stückzahl-Bestand zum Jahresende und zum jeweiligen Fonds-Geschäftsjahres-Ende

**Aus der OeKB** (für thesaurierende Fonds):
- Ausschüttungsgleicher Ertrag pro Anteil zum Geschäftsjahres-Ende
- Anrechenbare ausländische Quellensteuer pro Anteil
- Anschaffungswerts-Korrekturbetrag (KZ 188)

→ Diese Werte holst Du bei [profitweb.at](https://profitweb.at) (OeKB-Profitlist) per ISIN-Suche. Details dazu im Beitrag [KZ 937 — ausschüttungsgleiche Erträge richtig melden](/posts/kz-937-oekb-ausschuettungsgleich/).

## 4. Die FIFO/Avg-Cost-Falle bei Sparplänen

Ein FFB-Sparplan mit 80 €/Monat in einen Fonds produziert pro Jahr **ca. 12 kleine Käufe** (oder 24 bei zweimaliger Ausführung). Über fünf Jahre Sparplan-Laufzeit sind das **60–120 Einzelkäufe pro Fonds**. Wenn Du auch nur **einen Teil verkaufst**, müssen die Lots steuerlich zugeordnet werden:

- **Österreich-Pflicht: gleitender Durchschnitt** (Avg-Cost) — Der Verkaufsgewinn berechnet sich aus dem durchschnittlichen Anschaffungspreis aller bis dahin gehaltenen Lots.
- **Deutschland-Pflicht: FIFO** — Erst der ältest Käufer wird verkauft, dann der nächste.

Bei sehr vielen kleinen Käufen mit unterschiedlichen Preisen gibt das **zwei deutlich verschiedene Ergebnisse**. Wer Avg-Cost nicht korrekt rechnet, **kann den Gewinn um mehrere hundert Euro überschätzen** (oder unterschätzen).

### Mini-Beispiel: 3 Sparplan-Käufe + Teilverkauf

| Datum | Aktion | Stk | Preis | Kosten |
|---|---|---|---|---|
| 2024-01-15 | Kauf | 10 | 95 € | 950 € |
| 2024-04-15 | Kauf | 10 | 110 € | 1.100 € |
| 2024-07-15 | Kauf | 10 | 105 € | 1.050 € |
| | **Bestand:** | **30** | **100,00 € Avg** | **3.100 €** |
| 2025-03-01 | Verkauf | 15 | 115 € | Erlös 1.725 € |

**Mit Avg-Cost (AT-Pflicht)**: Kostenbasis 15 × 100 = **1.500 €**, Gewinn **225 €** → KZ 994.

**Mit FIFO (DE)**: Erste 10 × 95 = 950 € + nächste 5 × 110 = 550 € = **1.500 €**, Gewinn **225 €** → in diesem Spezialfall identisch.

Hier zufällig identisch — bei stärker schwankenden Sparplan-Kursen über mehrere Jahre können die beiden Methoden um zweistellige Prozent abweichen. In der österreichischen Erklärung gilt **immer Avg-Cost**, FIFO kannst Du ignorieren (außer Du machst die parallele Berechnung für Cross-Check, was wir im Tool zur Verifikation tun).

## 5. Thesaurierer und KZ 937 — der häufigste Stolperstein

Praktisch **alle aktiv gemanagten DWS-, Carmignac- und Comgest-Fonds**, die typischerweise auf FFB liegen, sind thesaurierend. Das heißt: Du hast nie Cash bekommen, aber **Du musst trotzdem jährlich KZ 937** ausfüllen — pro Jahr, pro ISIN, mit den **OeKB-Werten** (nicht den deutschen Vorabpauschale-Werten!).

Genau diese Konstellation ist im Detail-Beitrag erklärt:

→ **[KZ 937 — ausschüttungsgleiche Erträge richtig melden](/posts/kz-937-oekb-ausschuettungsgleich/)** mit konkretem Rechenbeispiel zur AW-Korrektur, OeKB-Lookup und Schwarzfonds-Falle.

Plus: Bei jedem **Verkauf** musst Du daran denken, dass Dein steuerlicher Anschaffungswert um die kumulierten ausschüttungsgleichen Erträge **gestiegen** ist — sonst zahlst Du beim Verkauf doppelt Steuer. Das war die hauptsächlich verschenkte Steuerersparnis im Rechenbeispiel des verlinkten Beitrags.

## 6. Quellensteuer bei FFB-Fonds

Bei thesaurierenden Fonds wird die im Fonds anfallende ausländische Quellensteuer (z.B. US-Aktien-Dividenden, die der DWS-Fonds intern erhält) **anteilig** auf Deine ausschüttungsgleichen Erträge umgelegt — die OeKB liefert das pro Anteil als anrechenbare Quellensteuer (in **KZ 384** der Meldung).

Diese trägst Du **gesondert** in der E1kv ein. Sie wirkt direkt KESt-mindernd, **bis zum DBA-Cap** (15 % bei US-Erträgen) — die OeKB liefert die Zahl bereits gekappt, Du musst da nichts mehr rechnen.

## 7. Häufige Fehler — Quick-Check

- ❌ **Deutsche Vorabpauschale als ausschüttungsgleicher Ertrag eintragen** — falsche Beträge, falsche steuerliche Logik.
- ❌ **AW-Korrektur bei thesaurierenden FFB-Fonds vergessen** — beim späteren Verkauf doppelt versteuert.
- ❌ **FFB-Konto vergessen** — wenn Du nur deinen IBKR erklärst und FFB "irgendwie nebenbei" hast, weiß das Finanzamt davon erst nichts. Bei Datenmeldung der OeKB ans BMF (jährlich) fliegt es typischerweise auf.
- ❌ **FIFO statt Avg-Cost rechnen** — in Österreich nicht zulässig.
- ❌ **Schwarzfonds-Pauschale übersehen** — selten bei FFB-Bestand, aber prüfen: ISIN bei profitweb.at nicht gelistet = Schwarzfonds mit 90/10-Pauschale.

## <a name="tool"></a>FFB + IBKR auf einem Steuerberater-Blatt

Unser Tool **[DepotTax](https://depottax.at)** löst genau diese Mischsituation:

- **Manuelle ETF-Erfassung** pro FFB-Konto — Du trägst pro Fonds Käufe, Verkäufe und Ausschüttungen einmal ein. Das Tool macht den Rest.
- **OeKB-Pull pro Nacht** für alle ISINs — KZ 937 / 384 / 188-Werte werden gecacht, sobald sie veröffentlicht sind.
- **FIFO + gleitender Durchschnitt parallel** — Du siehst beide Methoden und Österreich-konform die Avg-Cost-Werte. Cross-Check zu Deinen eigenen Berechnungen.
- **Anschaffungswerts-Korrektur automatisch** — kein Doppel-KESt beim späteren Verkauf.
- **IBKR und FFB in einer Excel-Mappe** — eine fertige Steuerberater-Mappe für beide Brokers, keine zwei separaten Excel-Stapel mehr.
- **Schwarzfonds-Warnung** wenn eine ISIN nicht in der OeKB-Profitlist landet.

Aktuell **Beta-Phase**, Zugang auf Anfrage.

---

**Du hast Korrekturen, Erfahrungen mit FFB-Sparplänen in Österreich oder einen Edge-Case der nicht abgedeckt ist?** Schreib uns: [milosiland@gmail.com](mailto:milosiland@gmail.com)

*Keine steuerliche Beratung — dieser Beitrag dient zur Selbst-Information. Bei komplexen Konstellationen Steuerberater hinzuziehen.*
