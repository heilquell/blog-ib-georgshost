---
title: 'E1kv ausfüllen für IBKR-User (Österreich 2026) — vollständige Anleitung'
date: 2026-05-31
lastmod: 2026-05-31
description: 'Schritt-für-Schritt-Anleitung zum Ausfüllen der Beilage E1kv „ohne KESt-Abzug" für österreichische Privatpersonen mit Interactive-Brokers-Konto. Inkl. KZ 863, 994, 892, 995, 896, 861, 998.'
keywords: ['E1kv', 'E1kv ausfüllen', 'IBKR Steuer Österreich', 'Interactive Brokers KESt', 'Beilage Kapitalvermögen', 'ohne KESt-Abzug', 'KZ 863', 'KZ 994', 'FinanzOnline E1kv']
tags: ['E1kv', 'IBKR', 'Steuererklärung', 'Österreich']
---

# E1kv ausfüllen für IBKR-User (Österreich 2026) — vollständige Anleitung

> **Stand:** 2026-05-31 · **Lesezeit:** ~15 Minuten · **Gilt für:** Steuerjahr 2025 (Erklärung 2026)

Du hast ein Interactive-Brokers-Konto, bist in Österreich steuerpflichtig — und stehst jetzt vor der **Beilage E1kv „ohne KESt-Abzug"** in FinanzOnline. Diese Anleitung erklärt **jede relevante Kennzahl**, wie Du sie aus Deinen IBKR-Daten bekommst, und wo die häufigsten Fehler liegen.

> 💡 **Quick-Win:** Wenn Du Dir das jährliche Excel-Gebastel sparen willst — am Ende des Artikels gibt es einen Link zu einem **automatisierten Tool**, das die Beilage direkt aus Deiner FlexQuery erstellt.

## Inhaltsverzeichnis

1. Wer braucht die E1kv „ohne KESt-Abzug"?
2. Was Du vorher brauchst (FlexQuery-Setup)
3. Die wichtigsten Kennzahlen — Übersicht
4. Schritt 1: Dividenden + PiL → KZ 863
5. Schritt 2: Aktien-Gewinne/Verluste → KZ 994 / 892
6. Schritt 3: Optionen → KZ 995 / 896 (oder KZ 857?)
7. Schritt 4: Broker-Zinsen → KZ 861 oder 863?
8. Schritt 5: Anrechenbare Quellensteuer → KZ 998
9. Häufige Fehler + Edge-Cases
10. Wo Du Dir die Stunden sparst

---

## 1. Wer braucht die E1kv „ohne KESt-Abzug"?

Kurz: **Jede AT-Privatperson mit Konto bei einer ausländischen Bank oder Wertpapierfirma**, die keinen automatischen KESt-Abzug in Österreich macht. Das betrifft:

- Interactive Brokers (IBKR Ireland, IBKR LLC)
- CapTrader, Lynx (IBKR-Reseller)
- Degiro
- Trade Republic? **Nein** — seit 2024 in AT steuereinfach
- Scalable Capital? **Nein** — vermutlich ebenfalls steuereinfach (vor Abgabe prüfen)

> Wenn Dein Broker bereits AT-KESt einbehält (Erste, BAWAG, Flatex AT u.ä.), brauchst Du diese Beilage **nicht** — dort kommt höchstens die Beilage **„mit KESt-Abzug"** zum Einsatz.

## 2. Was Du vorher brauchst — IBKR FlexQuery-Setup

[Detail-Anleitung im separaten Guide → "IBKR FlexQuery für die AT-Steuererklärung einrichten"]

Kurzfassung:
- IBKR Kontoverwaltung → Performance & Reports → FlexQuery
- Neue Query anlegen: Period = letztes Steuerjahr (z.B. 2025-01-01 bis 2025-12-31)
- Aktiviere mindestens: Trades, CashTransactions, OpenPositions, ChangeInNAV, StatementOfFunds
- Format: XML

→ Daraus brauchst Du folgende Daten als Aggregate (manuell aus XML ziehen oder Excel-Pivot):

## 3. Die wichtigsten Kennzahlen — Übersicht

| Kennzahl | Inhalt | Wo in der E1kv? |
|----------|--------|-----------------|
| **KZ 863** | Dividenden + PiL brutto, Zinsen aus Wertpapieren | Spalte „Überlassung von Kapital" |
| **KZ 994** | Realisierte Wertsteigerungen Aktien (Überschüsse) | Spalte „Wertsteigerungen" |
| **KZ 892** | Realisierte Wertsteigerungen Aktien (Verluste, mit Minus) | Spalte „Wertsteigerungen" |
| **KZ 995** | Verbriefte Derivate (Optionen-Überschüsse)¹ | Spalte „Derivate" |
| **KZ 896** | Verbriefte Derivate (Optionen-Verluste, mit Minus)¹ | Spalte „Derivate" |
| **KZ 861** | Zinsen aus Geldeinlagen bei Kreditinstituten (25 %) | Spalte „Sondersteuersatz 25 %" |
| **KZ 998** | Anrechenbare ausländische Quellensteuer | Anrechnung |

¹ Optionen-Klassifizierung in AT ist strittig — siehe Abschnitt 6.

[→ Detail-Guide: "KZ 863 vs KZ 994 — wo trage ich was ein?"]

---

## 4. Schritt 1: Dividenden + PiL → KZ 863

Aus IBKR brauchst Du:
- **CashTransactions Type = "Dividends"** (Σ Brutto in EUR)
- **CashTransactions Type = "Payment In Lieu Of Dividends"** (PiL, Σ Brutto)

Beide werden **gemeinsam** unter KZ 863 eingetragen.

**Wichtig:** Payment In Lieu Of Dividends entstehen bei IBKR, wenn der Broker Deine Aktien verleiht. Steuerlich werden sie wie reguläre Dividenden behandelt — auch wenn IBKR sie separat ausweist.

**Beispiel-Rechnung:**
```
Dividenden brutto:    3.252,70 €
PiL brutto:           3.010,38 €
─────────────────────────────────
Σ in KZ 863:          6.263,08 €
```

> 💡 Diese Aggregation macht das [Tool](#link) automatisch — inklusive korrekter EUR-Umrechnung zum Buchungstag (nicht Jahresende-Kurs!).

---

## 5. Schritt 2: Aktien-Gewinne/Verluste → KZ 994 / 892

AT verlangt **Avg-Cost-Methode** für die Bewertungsmethode (kein FIFO!). Aus IBKR-Trades realisierst Du pro Verkauf:

- Erlös (Net Cash)
- − Anschaffungskosten (Avg-Cost-Basis aus allen Käufen vor dem Verkauf)
- = realisierter Gewinn/Verlust

**Trennung Gewinn vs Verlust:**
- Alle **positiven** Realisierungen aufsummieren → **KZ 994**
- Alle **negativen** Realisierungen aufsummieren → **KZ 892** (eingetragen mit Minus-Vorzeichen)

> ⚠️ **Häufiger Fehler:** Saldieren statt trennen! Das Finanzamt will explizit die **Brutto-Gewinne** in KZ 994 und die **Brutto-Verluste** in KZ 892 sehen, nicht den Saldo.

**Beispiel:**
```
Σ positive Realisierungen:  46.188,83 €   → KZ 994
Σ negative Realisierungen: -26.351,73 €   → KZ 892 (mit Minus)
─────────────────────────────────────────
Netto-Saldo (intern):       19.837,10 €
```

## 6. Schritt 3: Optionen → KZ 995 / 896 (oder KZ 857?)

Hier wird es **rechtlich strittig**:

### Variante A — Praxis (was die meisten machen)
Aktien-Optionen über IBKR werden als **„wie verbriefte Derivate"** behandelt → KZ 995 (Überschüsse) / KZ 896 (Verluste). Begründung: börsennotiert und reguliert (CBOE, NASDAQ-OM, OCC-Clearing). 27,5 % Sondersteuersatz.

### Variante B — strenge gesetzliche Auslegung
§ 27a Abs. 2 Z 7 EStG schließt den 27,5 %-Sondersteuersatz aus, wenn das Derivat **nicht verbrieft** ist UND ohne freiwilligen Steuerabzug. Beides trifft auf IBKR-Aktien-Optionen wörtlich zu → **KZ 857 mit Tarifsteuer (bis 55 %!)**.

**Worst-Case-Differenz:** Bei 43.000 € Options-Saldo wären das **~8.840 € Mehr-KESt**.

NotebookLM gegen das gesamte EStG befragt: „Aktien-Optionen auf regulierten Börsen werden wie verbriefte Derivate behandelt" — bestätigt also Variante A. Aber: Eine **BMF-Vorab-Anfrage** für große Volumina ist defensiv ratsam.

[→ Detail-Diskussion: "Aktien-Optionen bei IBKR — KZ 995 oder KZ 857?"]

## 7. Schritt 4: Broker-Zinsen → KZ 861 oder 863?

Auch hier eine **strittige Klassifikation**:

| Variante | Argument | Steuersatz |
|----------|----------|-----------|
| **KZ 861 (25 %)** | „Zinsen aus Geldeinlagen bei Kreditinstituten" — günstiger | 25 % |
| **KZ 863 (27,5 %)** | IBKR ist **MiFID-Wertpapierfirma**, nicht Kreditinstitut → defensiver | 27,5 % |

**Differenz pro 1.000 € Zinsen: 25 €/Jahr.**

Bei IBKR Ireland ist die Klassifikation als „Überlassung von Kapital an eine Wertpapierfirma" (KZ 863) wahrscheinlich rechtlich korrekter. Wer aggressiv steuerplant: KZ 861. Wer auf der sicheren Seite sein will: KZ 863.

## 8. Schritt 5: Anrechenbare Quellensteuer → KZ 998

US-Dividenden bekommen 15 % US-Quellensteuer abgezogen (mit gültigem W-8BEN), IL-Dividenden 25 % (DBA-Cap nur 15 %), BR-Dividenden 15 %, IE-Zinsen 20 %.

**KZ 998 = nur der DBA-anrechenbare Anteil**, nicht die vollen abgezogenen Quellensteuern. Pro Quellenstaat ist der Cap separat zu beachten:

```
Land | Tatsächlich abgezogen | DBA-Cap | Anrechenbar
US   | -811,38 €             | 15 %    | -811,38 € (= 100 %)
IL   | -114,50 €             | 15 %    |  -68,70 € (= Cap, nicht voll)
BR   |  -32,97 €             | 15 %    |  -32,97 €
IE-Z |  -82,07 €             | 0 %     |    0,00 € (EU-Zinsrichtlinie)
─────────────────────────────────────────────────────
Σ KZ 998:                              -913,05 €
```

> ⚠️ **EU-Zinsrichtlinie:** IE-Quellensteuer auf Broker-Zinsen ist in der Regel nicht anrechenbar (Cap 0 %) — diese 82 € sind **verloren**, nicht in KZ 998!

## 9. Häufige Fehler + Edge-Cases

- **EUR-Umrechnung zum Buchungstag**, nicht zum Jahresende-Kurs (EStR Rz 6121)
- **Bei Aktien-Splits / Spin-Offs:** Anschaffungskosten anteilig aufteilen, nicht ignorieren
- **Verlustausgleich nur INNERHALB des §27-Topfs:** Aktien-Verlust kann Aktien-Gewinn ausgleichen, NICHT Zinsen oder Dividenden
- **Keine Spesen abziehbar** bei AT-Privatpersonen (Unterschied zu Betriebsvermögen)
- **Wegzug aus AT?** Bei Umzug nach DE gilt anderes Recht (§ 23 EStG-Fremdwährungsgewinne) — [→ Separater Guide]

## 10. Wo Du Dir die Stunden sparst

Wenn Du das **jedes Jahr** ausfüllen musst, lohnt sich ein automatisiertes Tool:

> 🛠 **[IB-Abrechnung](https://ib.georgshost.eu)** liest Deine IBKR-FlexQuery automatisch und generiert:
> - Die exakten E1kv-Kennzahlen (KZ 863, 994, 892, 995, 896, 861, 998)
> - PDF-Beilage als Beleg für den Steuerberater
> - Excel-Detail-Auswertung pro Trade
> - Inkl. Avg-Cost-Engine, AT-korrekter §27-Topf-Logik, DBA-Quellensteuer-Cap

Aktuell in geschlossener Beta für Friends-and-Family. Wenn Du Interesse hast — melde Dich.

---

**Disclaimer:** Diese Anleitung ist Hobby-Wissen, **keine Steuerberatung**. Verbindlich ist die Auskunft Deines Steuerberaters bzw. der Finanzbehörde. Bei großen Beträgen oder strittigen Klassifikationen (Optionen / Zinsen) Steuerberater konsultieren.

---

### Verwandte Guides

- [KZ 863 vs KZ 994 — wo trage ich was ein?](/posts/kz-863-vs-kz-994/)
- [IBKR FlexQuery für die AT-Steuererklärung einrichten](#) [in Vorbereitung]

### Quellen

- BMF-Erläuterungen zur E1kv 2025 (FinanzOnline-Formularhilfe)
- EStG § 27, § 27a, § 93–97
- EStR 2000 Rz 6121 (FX-Umrechnung), Rz 6228 ff (Avg-Cost)
- BMF-Info zur Quellensteuer-Anrechnung (DBA-Cap)
