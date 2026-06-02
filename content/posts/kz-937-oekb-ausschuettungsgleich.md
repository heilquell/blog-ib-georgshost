---
title: 'KZ 937 / ausschüttungsgleiche Erträge richtig melden — OeKB, Anschaffungswerts-Korrektur und der Schwarzfonds-Strafzuschlag (Österreich 2026)'
date: 2026-06-02
lastmod: 2026-06-02
description: 'Praktischer Leitfaden für KZ 937 in der E1kv: ausschüttungsgleiche Erträge aus thesaurierenden Fonds und ETFs. Mit Beispiel, OeKB-Profitlist-Lookup pro ISIN, der oft übersehenen Anschaffungswerts-Korrektur und der 90%-Pauschale für nicht-gemeldete Fonds.'
keywords: ['KZ 937', 'ausschüttungsgleiche Erträge', 'OeKB Profitlist', 'thesaurierender ETF Steuer', 'Schwarzfondsbesteuerung', 'Investmentfondsgesetz', 'Anschaffungswerts-Korrektur', 'E1kv KZ 937', 'IBKR Österreich Steuer', 'meldepflichtiger Fonds']
tags: ['E1kv', 'Kennzahlen', 'OeKB', 'Thesaurierer', 'Investmentfonds', 'Österreich']
---

# KZ 937 / ausschüttungsgleiche Erträge — die häufigste Stolperfalle bei thesaurierenden ETFs

> **Stand:** 2026-06-02 · **Lesezeit:** ~9 Minuten · **Gilt für:** AT-Privatpersonen, Beilage E1kv „ohne KESt-Abzug", Steuerjahr 2025

Wenn Du **thesaurierende Fonds oder ETFs** hältst, hast Du in der E1kv eine eigene Kennzahl: **KZ 937** für ausschüttungsgleiche Erträge. Das ist nicht das Gleiche wie KZ 863 (echte Ausschüttungen) — und es ist die Stelle, an der **die meisten Selbst-Erklärer Fehler machen**, weil drei Dinge gleichzeitig passieren müssen:

1. Den richtigen Betrag bei der **OeKB** abrufen — pro ISIN, pro Geschäftsjahr.
2. In **KZ 937** eintragen (und nicht versehentlich in 863 mit den echten Dividenden vermengen).
3. Den **Anschaffungswert anheben** (AW-Korrektur), damit der spätere Verkaufsgewinn nicht doppelt besteuert wird.

Punkt 3 wird fast immer vergessen. Wer einen Avg-Cost-Tracker selbst pflegt und das nicht macht, **zahlt beim späteren Verkauf KESt auf Beträge, die bereits jährlich versteuert wurden**.

> 💡 Am Ende dieses Beitrags zeigen wir, wie unser [DepotTax-Tool](#tool) das automatisch macht — inklusive OeKB-Pull, AW-Korrektur in FIFO und gleitendem Durchschnitt parallel.

## Was sind „ausschüttungsgleiche Erträge"?

Bei einem **thesaurierenden Fonds** werden Dividenden, Zinsen und sonstige Erträge nicht ausgeschüttet, sondern im Fonds reinvestiert. Aus Anlegersicht erhältst Du **kein Geld** — der Fondswert wird nur etwas höher. Steuerlich tut das Finanzamt aber so, als hätte der Fonds die Erträge an Dich verteilt:

- **Was Du tatsächlich bekommst:** nichts (außer im Wert gestiegene Fondsanteile).
- **Was Du versteuern musst:** den jährlichen „ausschüttungsgleichen" Anteil — also den thesaurierten Ertrag pro Anteil × Deine Stückzahl zum Stichtag.

Das ist die berühmte „**Vorab-Besteuerung**" thesaurierender Fonds in Österreich — quasi der Preis für den Steuerstundungs-Vorteil, den ein ausschüttender Fonds nicht hätte. Geregelt im **Investmentfondsgesetz (InvFG) § 186**, im Detail erklärt in der **BMF-Information GZ 2017-0.586.402**.

## KZ 937 vs. KZ 863 — Wo ist die Trennlinie?

| Was Du hast | Wo eintragen |
|---|---|
| **Ausschüttung** eines ausschüttenden Fonds (Cash kommt auf's Konto) | **KZ 863** (siehe auch [KZ 863 vs KZ 994](/posts/kz-863-vs-kz-994/)) |
| **Ausschüttungsgleicher Ertrag** eines thesaurierenden Fonds (kein Cash) | **KZ 937** |
| **Realisierter Verkaufsgewinn** eines Fonds | **KZ 994** (oder Verlust in 892) |

Wichtig: **KZ 937 ist KESt-pflichtig zu 27,5 %**, wie KZ 863 — aber er steht extra, weil das Finanzamt prüfen können muss, ob Du Deine Vorab-Steuer pro Jahr abgegolten hast.

## OeKB-Profitlist: die einzige verlässliche Datenquelle

Den Betrag pro Fondsanteil **berechnest Du nicht selbst** — er wird von der **OeKB (Oesterreichische Kontrollbank) als steuerlicher Vertreter** veröffentlicht. Dort steht für jeden in Österreich meldepflichtigen Fonds ein „Steuerlicher Bericht" mit allen Kennzahlen:

- **Ausschüttungsgleicher Ertrag pro Anteil** (in der Fondswährung)
- **Zur Korrektur des Anschaffungswertes anwendbarer Betrag pro Anteil** (das ist die KZ-188-Zahl)
- **Anrechenbare ausländische Quellensteuer pro Anteil** (KZ 384 / 757)
- **Datum des Geschäftsjahres-Endes**

Anlaufstelle: **profitweb.at** (alte Bezeichnung „MyESt"). Du gibst die **ISIN** ein, wählst das Geschäftsjahr, und bekommst die Werte pro Anteil. Multiplikation mit Deiner Stückzahl zum Stichtag → KZ-937-Betrag.

> ⚠️ **Fonds-Geschäftsjahr ≠ Kalenderjahr.** Ein iShares-ETF kann sein Geschäftsjahr z.B. zum 30. November enden. Der ausschüttungsgleiche Ertrag wird dann **vier Monate nach Geschäftsjahresende** veröffentlicht (= bis Ende März im Folgejahr). Im Steuerjahr 2025 erfasst Du also Geschäftsjahre, die **2025 geendet haben** — z.B. Periode 01.12.2024–30.11.2025.

## Die unterschätzte Falle: Anschaffungswerts-Korrektur

Hier verlieren die meisten Selbst-Erklärer mehrere hundert bis tausend Euro:

Wenn Du auf einen thesaurierenden Fonds jährlich ausschüttungsgleiche Erträge versteuerst, **steigt Dein steuerlicher Anschaffungswert** um genau diesen Betrag (genauer: um den Wert in **KZ 188** der OeKB-Meldung, der oft mit dem ausschüttungsgleichen Ertrag identisch ist). Beim späteren **Verkauf** ziehst Du diesen erhöhten Anschaffungswert vom Verkaufserlös ab — sonst zahlst Du **doppelt KESt** auf die thesaurierten Erträge.

### Beispiel: 100 Anteile iShares Core MSCI World UCITS ETF (thesaurierend)

| Jahr | Aktion | Beschreibung |
|---|---|---|
| 2022 | Kauf 100 Anteile à 80 € | AW gesamt: **8.000 €** |
| 2023 | Vorabbesteuerung | OeKB-Wert: 2,10 €/Anteil → KZ 937 = **210 €** versteuert. **AW steigt auf 8.210 €.** |
| 2024 | Vorabbesteuerung | OeKB-Wert: 2,35 €/Anteil → KZ 937 = **235 €** versteuert. **AW steigt auf 8.445 €.** |
| 2025 | Verkauf zu 110 €/Anteil | Erlös: **11.000 €** |

**Ohne AW-Korrektur** (Standard-Avg-Cost-Tracker):
Verkaufsgewinn = 11.000 − 8.000 = **3.000 €** → KZ 994 → 825 € KESt fällig.
Aber auf 445 € der 3.000 € hast Du in 2023 und 2024 schon je 27,5 % gezahlt → **122,38 € Doppel-KESt**.

**Mit korrekter AW-Korrektur**:
Verkaufsgewinn = 11.000 − 8.445 = **2.555 €** → KZ 994 → 702,63 € KESt.

Der korrekte Weg spart Dir hier **122 € exakt für diese eine Position**. Bei einem realen Depot mit mehreren Thesaurierern über zehn Jahre summiert sich das in den vierstelligen Bereich.

## Schwarzfonds: Die 90%-Pauschalbesteuerung

Wenn Dein Fonds **nicht meldepflichtig** ist (keine OeKB-Daten verfügbar), gilt die Schwarzfondsbesteuerung nach **InvFG § 186 Abs. 2 Z 3**:

- **Mindestens 90 % der Wertsteigerung pro Kalenderjahr** gelten als ausschüttungsgleich
- **mindestens aber 10 % des Rücknahmepreises** zum Jahresende

Das ist **deutlich härter** als bei meldepflichtigen Fonds. Konkret: Wenn Dein Schwarzfonds sich im Jahr um 5 % gesteigert hat, versteuerst Du `max(0,9 × 5%, 10% × Rücknahmepreis)` — also bei einem Rücknahmepreis von 100 € praktisch **10 € pro Anteil** (statt der vermutlich realen ~3 € thesaurierten Erträge).

> ⚠️ **Faustregel:** Bei US-domizilierten ETFs (Sitz USA, nicht Irland/Luxemburg) ist die Meldepflicht **meistens nicht** erfüllt. Vor dem Kauf prüfen: ISIN bei profitweb.at suchen — wenn nicht gelistet, im Hinterkopf den Schwarzfonds-Strafzuschlag haben.

## Anrechenbare ausländische Quellensteuer (KZ 384)

Bei meldepflichtigen Fonds liefert die OeKB **auch die anrechenbare Quellensteuer pro Anteil** (KZ 384 in der Meldung, bzw. KZ 757 wenn Du als beschränkt Steuerpflichtiger hier sitzt). Diese trägst Du **gesondert** in der E1kv ein, sie reduziert Deine KESt-Schuld direkt.

Beispiel: Dein US-Aktien-thesaurierender Fonds enthält 8 € pro Anteil ausschüttungsgleiche Erträge, davon 1,20 € US-Quellensteuer-Anrechnung. Du trägst ein:

- **KZ 937**: 8,00 € × Stückzahl
- **KZ 384**: 1,20 € × Stückzahl (DBA-Cap USA 15 % wird automatisch gewahrt, weil die OeKB schon vorab gekappt liefert)

## Häufige Fehler — Quick-Check

- ❌ **Ausschüttungsgleiche Erträge in KZ 863 statt 937** — wird vom Finanzamt nicht zwingend bemerkt, aber bei einer späteren Prüfung problematisch.
- ❌ **AW-Korrektur vergessen** — Du zahlst beim Verkauf doppelt.
- ❌ **Falsches Geschäftsjahr** — z.B. Geschäftsjahr endet 30.06.2024, Du trägst es im Steuerjahr 2024 ein statt 2025 (wenn der Stichtag VOR Deinem Kauf liegt, gar nicht).
- ❌ **Stückzahl zum falschen Stichtag** — entscheidend ist die Stückzahl **am Tag des Fonds-Geschäftsjahres-Endes**, nicht am Kalenderjahres-Ende.
- ❌ **Schwarzfonds-Pauschale übersehen** — ein einziger US-domizilierter ETF kann Deine Steuerlast verdreifachen.

## <a name="tool"></a>Das automatisch lösen

Manuell ist KZ 937 für ein Depot mit fünf Thesaurierern und Käufen über mehrere Jahre **mehrere Stunden Arbeit pro Steuererklärung** — OeKB-Lookup, Stückzahlen pro Stichtag, AW-Korrektur in einem Excel-Sheet, Quellensteuer separat erfassen.

Unser Tool **[DepotTax](https://depottax.at)** macht das automatisch:

- **OeKB-Pull pro Nacht** für alle ISINs in Deinem Depot — Werte werden gecacht, sobald sie veröffentlicht sind.
- **AW-Korrektur in FIFO + gleitendem Durchschnitt parallel** — Du siehst beide Methoden und Österreich-konform den Avg-Cost-Wert.
- **KZ 937, KZ 994 und KZ 384 fertig vorberechnet** in der Steuerberater-Excel.
- **Schwarzfonds-Warnung** wenn eine ISIN nicht in der OeKB-Profitlist auftaucht.
- **Auch ohne IBKR-FlexQuery nutzbar** — manuelle ETF-Erfassung für **FFB-Sparpläne** und ähnliche thesaurierende Positionen ohne automatisierten Broker-Feed.

Aktuell **Beta-Phase**, Zugang auf Anfrage. Funktioniert mit IBKR, CapTrader, LYNX, BANX, Brokerport — sowie FFB-Konten und sonstigen manuell zu erfassenden Depots.

---

**Du hast Korrekturen, Fragen oder einen Edge-Case, der nicht abgedeckt ist?** Schreib uns: [milosiland@gmail.com](mailto:milosiland@gmail.com)

*Keine steuerliche Beratung — dieser Beitrag dient zur Selbst-Information. Bei komplexen Konstellationen Steuerberater hinzuziehen.*
