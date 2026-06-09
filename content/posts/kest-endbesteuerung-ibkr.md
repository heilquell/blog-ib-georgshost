---
title: '„KESt-endbesteuert" — was das wirklich heißt und warum es bei IBKR nicht greift'
date: 2026-06-09
lastmod: 2026-06-09
description: 'In Österreich ist nicht alles automatisch mit der Kapitalertragsteuer abgegolten. Wer bei IBKR, CapTrader oder LYNX handelt, muss jede Position selbst in die Steuererklärung tragen — Aktien, ETFs, Anleihen, Optionen, FFB-Fonds. Warum das so ist und was daraus folgt.'
keywords: ['KESt-Endbesteuerung', 'KESt-Abzug', 'inländische Depotstelle', 'ausländischer Broker', 'IBKR Steuer Österreich', 'CapTrader Steuer', 'LYNX Steuer', 'E1kv pflicht', '§ 95 EStG', 'KZ 994 KZ 892']
tags: ['E1kv', 'KESt', 'IBKR', 'CapTrader', 'LYNX', 'Steuererklärung', 'Österreich']
---

# „KESt-endbesteuert" — was das wirklich heißt und warum es bei IBKR nicht greift

> **Stand:** 2026-06-09 · **Lesezeit:** ~5 Minuten · **Gilt für:** AT-Privatpersonen, Steuerjahr 2025+

Ein häufiger Satz in IBKR-/CapTrader-Foren: *„Aktiengewinne sind doch endbesteuert, da muss ich nichts angeben."* Falsch — zumindest sobald der Broker im Ausland sitzt. Dieser Artikel räumt das Missverständnis auf, weil daran jedes Jahr Steuererklärungen scheitern.

## Was „endbesteuert" eigentlich heißt

In Österreich gilt für Kapitalerträge der Kapitalertragsteuer-Satz von **27,5 %** (für Aktien, ETFs, Fonds, Dividenden) bzw. **25 %** (für bestimmte Cash-Zinsen). Wenn diese Steuer **direkt an der Quelle einbehalten und ans Finanzamt abgeführt** wird, gilt der Ertrag als **endbesteuert** (§ 97 EStG). Praktisch heißt das:

- Der Ertrag muss **nicht** in der Steuererklärung deklariert werden.
- Es kommt keine Nachforderung, keine Rückzahlung.
- Es zählt auch nicht zur Berechnung anderer Sätze (z. B. SV-Beiträge bei Selbständigen).

Das ist der bequeme Fall, den viele Privatanleger reflexhaft auf alle Wertpapier-Erträge übertragen. Die Voraussetzung steht aber eindeutig im Gesetz.

## Die einzige Voraussetzung für Endbesteuerung: Inländische Depotstelle

Damit ein Wertpapier-Ertrag in Österreich endbesteuert ist, muss die Depotstelle, die ihn auszahlt, **in Österreich ansässig** sein und als **inländischer Abzugsverpflichteter** auftreten (§ 95 EStG). Konkret:

- Erste Bank, Bank Austria, Raiffeisen, BAWAG, Hello Bank, Easybank, Flatex (Wien), DADAT, Bankhaus Schelhammer Capital usw.
- Diese Banken berechnen 27,5 % auf den realisierten Gewinn oder die Ausschüttung, ziehen ihn von der Auszahlung ab und überweisen ihn an die Republik. Du siehst eine fertige Netto-Buchung. Fertig.

**Alles, was im Ausland sitzt, fällt aus diesem Mechanismus raus** — egal ob EU oder Drittland, egal ob der Broker auf Deutsch korrespondiert oder einen österreichischen Steuerreport bietet.

## Warum greift das bei IBKR / CapTrader / LYNX / FFB nicht?

Weil **keiner dieser Anbieter eine inländische Depotstelle ist**:

| Broker | Sitz | Abzugsverpflichteter? |
|---|---|---|
| **Interactive Brokers (IBKR)** | Dublin (IE), US-Mutter | nein |
| **CapTrader** | Düsseldorf (DE), IB-Reseller | nein |
| **LYNX** | Amsterdam (NL), IB-Reseller | nein |
| **Brokerport** | Stuttgart (DE), IB-Reseller | nein |
| **Banx** | Düsseldorf (DE), IB-Reseller | nein |
| **FIL Fondsbank (FFB)** | Kronberg (DE) | nein |

Wenn Du bei einem dieser Anbieter eine Aktie verkaufst oder eine Dividende bekommst, **zieht niemand für die Republik Österreich KESt ab**. Der Bruttobetrag landet auf Deinem Konto. Gut für den Cashflow, schlecht für die Erinnerungsleistung im April: Du musst jeden einzelnen dieser Erträge in der Steuererklärung deklarieren.

## Was das praktisch heißt: Beilage E1kv ist Pflicht

Für jeden Anbieter aus der Tabelle oben gilt am Jahresende ohne Ausnahme:

- **Realisierte Gewinne** auf Aktien, ETFs, Fonds → **KZ 994** (Gewinne) / **KZ 892** (Verluste)
- **Dividenden** brutto → **KZ 863**
- **Anleihen-Kupons** → **KZ 863**
- **Ausschüttungsgleiche Erträge** thesaurierender Meldefonds → **KZ 937** (siehe [KZ 937 — wann OeKB-Daten Pflicht sind](/posts/kz-937-oekb-ausschuettungsgleich/))
- **Anrechenbare ausländische Quellensteuer** → **KZ 998**
- **Forex-Gewinne** in bestimmten Konstellationen → **KZ 994** (mehr dazu in [Forex-Besteuerung bei IBKR](/posts/forex-besteuerung-ibkr-oesterreich/))

Mit anderen Worten: Beilage E1kv komplett ausfüllen. Auch wenn der Broker bequemerweise einen „Steuerreport" generiert — der ersetzt die Eintragung nicht, er liefert nur die Zahlen.

## Häufige Missverständnisse, die Du jetzt loswerden kannst

**„Aktien sind in Österreich endbesteuert."** → Nein, *Erträge inländischer Depotstellen* sind endbesteuert. Die Asset-Klasse spielt keine Rolle.

**„Bei IBKR sind wenigstens die Dividenden endbesteuert, weil die im Statement schon mit Quellensteuer abgerechnet sind."** → Nein. Die im IBKR-Statement abgezogene Steuer ist die **ausländische Quellensteuer des Emissionslandes** (z. B. 15 % US-Withholding bei US-Aktien) — sie hat mit AT-KESt nichts zu tun. Du musst die Dividende trotzdem brutto in KZ 863 melden; die abgezogene Quellensteuer kommt in KZ 998 und wird auf Deine AT-KESt angerechnet (bis maximal 15 % laut DBA).

**„Optionen sind eine Sonderwelt und nicht in der E1kv."** → Doch, Options-Gewinne sind genauso E1kv-pflichtig. Sie folgen aus § 27 Abs 4 EStG (Derivate) und gehören in KZ 994/892. Der Grund warum manche Tools sie separat behandeln ist nicht „endbesteuert vs. nicht endbesteuert" (das wäre die selbe Logik wie bei Aktien — *nichts* bei IBKR ist endbesteuert), sondern dass Optionen eine eigene Handelsstrategie mit Ablaufdatum sind, was z. B. bei Loss-Harvesting anders zu bewerten ist.

**„Mein Steuerberater hat das letzes Jahr alles in einem Topf zusammengefasst, also passt das schon."** → Möglich, aber falsch. Aktien-Gewinne, Anleihen-Kupons und ausschüttungsgleiche Erträge haben *unterschiedliche* Kennzahlen mit unterschiedlichen Verlustausgleichs-Regeln. Wenn alles in einer Zahl landet, wird der Verlustausgleich zwischen den Kategorien falsch gemacht.

## Konsequenz: Tools-Pflicht statt Tabellenkalkulation

Ein normales IBKR-Konto generiert über ein Jahr leicht **mehrere hundert Realisations-Ereignisse**, dazu Dividenden, Quellensteuern in fünf bis zehn Ländern, Cash-Zinsen, Corporate Actions (Splits, Spin-Offs), Forex-Bewegungen. Per Hand in Excel ist das machbar, aber dauert Tage und ist fehleranfällig. Wenn Du Familie und Beruf hast, ist die naheliegende Alternative ein spezialisiertes Tool, das den FlexQuery-Export von IBKR (oder das CSV-Statement von FFB) liest, FIFO oder Durchschnittsmethode rechnet, die OeKB-Meldefonds-Datenbank abfragt und die fertigen Kennzahlen für FinanzOnline ausspuckt.

Genau dafür haben wir [DepotTax](https://depottax.at) gebaut. Du lädst Deinen IBKR-FlexQuery hoch (oder verbindest API-Token für automatischen Nightly-Pull), und am Ende bekommst Du eine PDF/Excel-Aufstellung mit jeder KZ und einer Erklärung pro Position. Auch CapTrader, LYNX, FFB werden unterstützt. <a id="tool"></a>

## Zusammengefasst in einer Zeile

**Endbesteuerung gilt nur bei Erträgen einer inländischen Depotstelle.** IBKR, CapTrader, LYNX, FFB sind keine inländischen Depotstellen — also ist nichts davon endbesteuert. Jedes Jahr Beilage E1kv. Ohne Ausnahme.

---

*Verwandte Posts:*

- [E1kv ausfüllen mit IBKR-Daten](/posts/e1kv-ausfuellen-ibkr/)
- [KZ 863 vs KZ 994 — was wohin gehört](/posts/kz-863-vs-kz-994/)
- [Anrechenbare Quellensteuer bei IBKR (USA, Schweiz, UK)](/posts/quellensteuer-ibkr-usa-schweiz-uk/)
- [FFB-Konto in der Steuererklärung](/posts/ffb-konto-steuererklaerung-oesterreich/)
