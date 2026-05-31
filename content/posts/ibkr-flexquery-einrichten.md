---
title: 'IBKR FlexQuery für die AT-Steuererklärung einrichten — Schritt für Schritt'
date: 2026-05-31
lastmod: 2026-05-31
description: 'Wie Du in Interactive Brokers eine Activity Flex Query erstellst, die alle für die österreichische E1kv nötigen Daten enthält — Trades, Dividenden, Quellensteuer, Cash Transactions. Mit der Section-Checkliste, die wirklich passt.'
keywords: ['IBKR FlexQuery', 'IBKR FlexQuery erstellen', 'Activity Flex Query', 'IBKR Steuer Österreich', 'Interactive Brokers Steuererklärung', 'IBKR XML Export', 'IBKR Activity Statement Steuer']
tags: ['FlexQuery', 'IBKR', 'Steuererklärung', 'Österreich']
---

# IBKR FlexQuery für die AT-Steuererklärung einrichten

> **Stand:** 2026-05-31 · **Lesezeit:** ~8 Minuten · **Gilt für:** AT-Privatpersonen, IBKR Client Portal 2026

Für die österreichische Steuererklärung („E1kv ohne KESt-Abzug") brauchst Du aus Interactive Brokers **alle** Trades, Dividenden, Quellensteuer-Abzüge und Cash-Bewegungen eines Kalenderjahres — in einem Format, das maschinenlesbar ist. Das **Activity Statement** im PDF reicht dafür nicht. Du brauchst eine **Activity Flex Query** als XML.

Diese Anleitung zeigt **welche Sections genau anhaken sind**, damit nichts fehlt — und welche oft vergessen werden.

> 💡 **Quick-Win:** Wenn Du den Export samt KZ-Zuordnung automatisieren willst — am Ende des Artikels gibt es einen Link zu einem [Tool](#tool), das die FlexQuery direkt einliest und die E1kv-Beilage erzeugt.

## Inhaltsverzeichnis

1. Warum FlexQuery (und nicht das normale Activity Statement)?
2. Wo findest Du FlexQueries im IBKR Client Portal?
3. Die Pflicht-Sections für die AT-Steuererklärung
4. Format, Zeitraum, Optionen
5. Speichern, Ausführen, Download
6. Häufige Fehler
7. Tool spart Dir die FlexQuery-Konfiguration

---

## 1. Warum FlexQuery — reicht das Activity Statement nicht?

Kurze Antwort: **Nein, für die E1kv nicht.**

| Format | Was Du bekommst | Steuer-tauglich? |
|--------|----------------|------------------|
| **Activity Statement (PDF)** | Hübsche Übersicht, aber Spalten-Aggregation, keine Roh-Trades | ❌ — keine maschinelle Avg-Cost-Berechnung möglich |
| **Activity Statement (CSV)** | Trades je Zeile, aber CSV-Struktur ist instabil und mischt Sections | ❌ — Header ändern sich, FX-Kurse fehlen oft |
| **Activity Flex Query (XML)** | Ein Block pro Section, stabile Tags, FX-Kurse zum Buchungstag | ✅ — die einzige zuverlässige Quelle |
| **Tax Forms (1099 / 1042-S)** | US-Steuerunterlagen | ❌ — irrelevant für AT, gilt nur für US-Resident-Steuer |

Die FlexQuery ist also nicht „die luxuriöse Variante", sondern für AT-Steuerzwecke **die einzige korrekte**.

---

## 2. Wo findest Du FlexQueries im IBKR Client Portal?

1. Login im Client Portal (https://www.interactivebrokers.com → „Login" oben rechts).
2. Im Menü oben rechts auf das **Personen-Icon** klicken → **Settings**.
3. In der linken Spalte: **Account Settings**.
4. Im Block **Reporting** den Eintrag **Flex Queries** öffnen.

Du landest auf einer Seite mit zwei Tabellen:
- **Activity Flex Query** ← das willst Du
- **Trade Confirmation Flex Query** ← brauchst Du **nicht**

Klicke unter „Activity Flex Query" auf **Create** (das `+`-Symbol).

> 🇬🇧 Falls die Oberfläche bei Dir auf Englisch ist — die Menüpunkte heißen identisch. IBKR übersetzt diese Section schon Jahre nicht.

---

## 3. Die Pflicht-Sections für die AT-Steuererklärung

Im Create-Dialog gibst Du der Query zuerst einen **Query Name** (z.B. `AT_Steuer_2025`). Dann scrollst Du zur Liste **Sections**. Hier kommt die kritische Entscheidung — welche Sections Du anhakst.

### ✅ Pflicht-Sections (anhaken)

| Section | Warum Du das brauchst |
|---------|----------------------|
| **Trades** | Jeder Aktien-/Options-/Forex-Trade. Basis für Avg-Cost-Berechnung der realisierten Gewinne (KZ 994/892, 995/896). |
| **Cash Transactions** | Dividenden, Payment In Lieu, Quellensteuer, Broker-Zinsen, Gebühren. Basis für KZ 863, 861, 998. |
| **Open Positions** | Wertpapierbestand zum Stichtag — Basis für offene Positionen + Avg-Cost-Übertrag ins Folgejahr. |
| **Statement of Funds** | Cash-Flow-Bewegungen je Währung. Cross-Check, ob die Summen mit den Cash Transactions zusammenpassen. |
| **Conversion Rates** | EUR-Wechselkurse zum jeweiligen Buchungstag. **Pflicht** — ohne diese kannst Du USD-Dividenden nicht korrekt in EUR umrechnen. |

### 🔲 Optionale, aber empfohlene Sections

| Section | Warum trotzdem nützlich |
|---------|------------------------|
| **Corporate Actions** | Splits, Spin-Offs, Ticker-Wechsel. Sonst zerschießt Dir ein Apple-1:4-Split die Avg-Cost-Berechnung. |
| **Transfers** | Wenn Du Wertpapiere zu/von einem anderen Broker übertragen hast — die Avg-Cost-Basis muss mit übertragen werden. |
| **Securities Info** | ISIN, Issuer-Country-Code (wichtig für Quellensteuer-DBA-Zuordnung pro Land). |

### ❌ Nicht relevant für die AT-Steuererklärung

- Net Stock Position Summary
- Net Asset Value
- Tier Interest Details
- SLB Activity
- Salesforce Notes

Diese Sections kannst Du weglassen — sie blähen nur die XML auf und tragen nichts zur E1kv bei.

---

## 4. Format, Zeitraum, Optionen

Im selben Create-Dialog, unter den Sections:

### Format
- **XML** wählen. **Nicht CSV.**
- Begründung: XML hat strikte Tags (`<Trade>`, `<CashTransaction>`), CSV mischt Sections und ändert Header je Version.

### Period
- **Last Year** wenn Du das gesamte Vorjahr willst (typisch für die Steuererklärung im April).
- **Year to Date** wenn Du laufende Werte fürs aktuelle Jahr willst (für unterjährige Kontrollen).
- **Custom Date Range** wenn Du z.B. nur ein Quartal brauchst.

> ⚠️ **Achtung Zeitzone:** IBKR liefert Timestamps in **EST (New York)**. Ein Trade am 1. Jänner 02:00 EST = noch 31. Dezember Vorjahres-Wien. Das Avg-Cost-Tool muss das berücksichtigen, sonst landet ein Trade im falschen Steuerjahr.

### Wichtige Optionen anhaken

| Option | Wert |
|--------|------|
| **Include Canceled Trades?** | **No** — sonst zählen stornierte Trades doppelt |
| **Display Header/Trailer Records?** | **Yes** — Hash-Summen zur Integritätsprüfung |
| **Profit and Loss** | **Default** lassen — das Tool rechnet ohnehin Avg-Cost neu |
| **Date Format** | `yyyy-MM-dd` (ISO) — sonst MM/DD/YYYY und das ist Sprachen-abhängig |
| **Time Format** | `HHmmss` (24h) |
| **Date/Time Separator** | `;` (Semikolon — sonst kollidiert mit Komma in CSV-Importen) |

---

## 5. Speichern, Ausführen, Download

1. Unten rechts **Save** klicken. Die Query erscheint jetzt in der Liste „Activity Flex Query".
2. Neben dem Namen siehst Du ein **Play-Icon** (▶). Klicken.
3. Im Popup den **Zeitraum bestätigen** und auf **Run** klicken.
4. IBKR generiert die XML. **Erste Generierung dauert je nach Account-Volumen 30 Sekunden bis 5 Minuten.**
5. Im selben Popup auf **Download** klicken — die XML liegt jetzt auf Deinem Rechner.

**Datei-Größe:** Bei 200–500 Trades/Jahr typischerweise 0,5–3 MB.

### Automatisierung über die Flex Web Service API

Wenn Du das Tool [IB-Abrechnung](#tool) verwendest, brauchst Du keinen manuellen Download. Du legst die FlexQuery einmal an und erzeugst einen **Token** (Settings → Reporting → Flex Web Service → Configure). Das Tool zieht sich die XML dann jeden Nacht automatisch.

---

## 6. Häufige Fehler

### „Bei meiner FlexQuery fehlen die Quellensteuer-Buchungen"
Section **Cash Transactions** vergessen. Reine `Trades`-Section enthält keine Dividenden/Quellensteuer — das sind technisch keine Trades.

### „USD-Beträge sind ohne EUR-Umrechnung"
Section **Conversion Rates** vergessen. Ohne FX-Kurse zum Buchungstag musst Du sonst pro Buchung den EZB-Tageskurs manuell ergänzen — bei 200 Dividenden ein Vormittag im Excel.

### „Mein Avg-Cost stimmt nicht — IBKR sagt was anderes"
Das ist **normal und erwartet**. IBKR rechnet `Maximizing Profits` oder `LIFO` oder `Specific Lots` — je nach Konto-Setting. AT verlangt **Avg-Cost (§ 27a Abs 4 EStG)**. Das Steuer-Tool muss Avg-Cost selbst nachrechnen aus den Roh-Trades. Die IBKR-PnL-Spalte ist für die AT-Steuererklärung **nicht** maßgeblich.

### „Corporate Action hat mein Avg-Cost zerstört"
Section **Corporate Actions** war nicht angehakt. Bei einem Apple-1:4-Split steht in Trades ein „Split-Trade" ohne Cashflow — ohne die Corporate-Actions-Section sieht das Tool die Stückzahlen-Anpassung nicht und rechnet die Avg-Cost-Basis falsch.

### „Ich habe vor 2 Jahren von Lynx zu IBKR übertragen — die Avg-Cost-Basis ist 0"
Section **Transfers** anhaken. Aber: bei Transfers von **vor** dem ersten IBKR-Trade muss die historische Basis manuell aus dem alten Broker-Statement rekonstruiert werden — keine FlexQuery der Welt kann Daten liefern, die der Broker nicht hat.

### „Period: Last Year — aber ich kriege nur 11 Monate"
Du hast die Query vor Jahresende erstellt und IBKR interpretiert „Last Year" relativ. Lösung: **Custom Date Range** mit explizitem `2025-01-01` bis `2025-12-31`.

---

## 7. <a id="tool"></a>Tool spart Dir die FlexQuery-Konfiguration

Wenn Du nicht jedes Jahr durch diese Section-Checkliste musst:

> 🛠 **[IB-Abrechnung](https://ib.georgshost.eu)** liest Deine Activity Flex Query ein und erzeugt die E1kv-Beilage direkt — inkl. AT-konformer Avg-Cost-Berechnung, DBA-Quellensteuer-Cap pro Land und PDF für den Steuerberater. Du kannst entweder die XML manuell hochladen oder über den **Flex Web Service Token** automatisch synchronisieren lassen.

Aktuell in geschlossener Beta. Melde Dich falls Du dabei sein willst.

---

**Disclaimer:** Keine Steuerberatung. Bei komplexen Situationen (Vorjahres-Übertrag von einem anderen Broker, internationale Wegzugsbesteuerung, Betriebsvermögen) → Steuerberater.

### Verwandte Guides

- [E1kv ausfüllen für IBKR-User (Österreich 2026)](./e1kv-ausfuellen-ibkr/) — der nächste Schritt nach dem FlexQuery-Setup
- [KZ 863 vs KZ 994 — wo trage ich was ein?](./kz-863-vs-kz-994/) — Zuordnungstabelle pro Buchungstyp

### Quellen

- IBKR Knowledge Base: „Activity Flex Query — Sections Reference"
- IBKR Help Center: „Flex Web Service Configuration"
- BMF-Formularhilfe E1kv 2025 (zur Sections-Anforderung)
- EStG § 27a Abs 4 (Avg-Cost-Pflicht)
