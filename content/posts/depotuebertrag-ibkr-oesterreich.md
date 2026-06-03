---
title: 'Depot-Übertrag bei IBKR — muss ich das in Österreich erklären? (2026)'
date: 2026-06-03
lastmod: 2026-06-03
description: 'Übertrag zwischen eigenen IBKR-Konten oder die IBKR-LLC-zu-Ireland-Migration: in Österreich grundsätzlich steuerneutral und nicht meldepflichtig — wenn die Anschaffungskosten korrekt mitwandern. Worauf Du achten musst, damit später keine Phantom-Gewinne realisiert werden.'
keywords: ['Depotübertrag IBKR Österreich', 'IBKR LLC Ireland Migration Steuer', 'Depotübertrag steuerneutral', 'Depotübertrag Meldepflicht', '§ 27 Abs 6 Z 2 EStG', 'IBKR Subaccount Übertrag', 'Anschaffungskosten Depotübertrag']
tags: ['IBKR', 'Depotübertrag', 'E1kv', 'Österreich', 'ATAD']
---

# Depot-Übertrag bei IBKR — muss ich das in Österreich erklären?

> **Stand:** 2026-06-03 · **Lesezeit:** ~6 Minuten · **Gilt für:** AT-Privatpersonen, die zwischen eigenen IBKR-Konten umgebucht haben oder von der IBKR-LLC-zu-Ireland-Migration betroffen waren

Vielleicht kennst Du das: Anfang 2022 kam plötzlich ein neuer Konto-Code in Deinen IBKR-Statements (U24…), Deine ganze Position wurde von Deinem alten Konto (U7…) auf das neue umgebucht — ohne dass Du irgendwas verkauft hättest. Das war die Brexit-/ATAD-bedingte Migration von **Interactive Brokers LLC** (US-Entity) zu **Interactive Brokers Ireland Limited**.

Oder Du hast aktiv selbst umgeschichtet — eine Position von einem Sub-Account auf einen anderen, weil Du verschiedene Strategien trennen wolltest.

In beiden Fällen taucht in der FlexQuery der nächsten Monate alles „neu" auf. Logische Frage: **muss ich da was erklären? Gilt das als Verkauf?**

Antwort vorweg: **Nein**, nicht in Österreich. Aber Du musst eine Sache prüfen, sonst zahlst Du bei den nächsten Verkäufen zu viel KESt.

## Die gesetzliche Lage in einer Minute

**§ 27 Abs 6 Z 2 EStG** regelt: ein Depotübertrag zwischen Konten **derselben Person bei derselben Bank** löst **keine Steuer aus** und ist **nicht meldepflichtig**.

Das gilt ausdrücklich **auch für ausländische Sachverhalte** — die Regel knüpft an die Identität von Anleger und Bank, nicht an die Geografie an. Quelle: [Enzinger Steuerberatung — Depotübertrag in Österreich, steuerliche Auswirkungen](https://www.enzinger-stb.at/depotuebertrag-in-oesterreich-steuerliche-auswirkungen/).

| Konstellation | Steuerlich |
|---|---|
| Eigener Übertrag zwischen zwei IBKR-Sub-Accounts | **steuerneutral**, keine Meldepflicht |
| IBKR LLC → IBKR Ireland (ATAD-Migration 2021/2022) | **steuerneutral** (s.u.) |
| Übertrag zu einem anderen Broker (z. B. IBKR → CapTrader) | **meldepflichtig**, Anschaffungs­kosten müssen nachgewiesen werden |
| Übertrag an eine andere Person (Schenkung) | **steuerneutral**, aber **meldepflichtig** + ggf. Schenkungs­meldegesetz |

## Graue Zone: IBKR LLC ↔ IBKR Ireland

Die ATAD-bedingte Migration war keine Wahl, sondern eine vom Regulator erzwungene Umstellung. Trotzdem bleibt formal die Frage: **ist IBKR LLC (Greenwich, CT) dieselbe Bank wie IBKR Ireland (Dublin)?**

Streng juristisch: zwei Rechtspersonen. Praktisch:

- Beide gehören zur **Interactive Brokers Group**.
- Die Umstellung war **automatisch** und **ohne Verkaufs­vorgang** auf der Broker-Seite (keine Realisierung der Lots).
- Die ursprünglichen **Anschaffungs­daten und Kostenbasen** wurden 1:1 auf das neue Konto übernommen — sichtbar in der FlexQuery durch unveränderte `OPEN_DATE`-Felder pro Lot.

**Der Praxis-Konsens unter AT-Steuerberatern**: solche konzerninternen Migrationen werden wie „dieselbe Bank" behandelt. Es gibt keine offizielle BMF-Stellungnahme dazu, aber auch keinen bekannten Fall, in dem ein Finanzamt für diese Migration KESt nachgefordert hätte.

> 💡 **Sicherheits-Tipp**: Wenn Du ganz vorsichtig sein willst, ergänze in der E1kv unter „Sonstige Hinweise" einen Satz wie: *„Im Berechnungs­zeitraum erfolgte ein technischer Konten­übertrag innerhalb der Interactive Brokers Group (LLC → Ireland) ohne Realisierung. Anschaffungs­kosten unverändert übernommen."* Das ist freiwillig, schafft aber Transparenz.

## Das eigentliche Risiko: Anschaffungs­kosten

**Steuerneutral** bedeutet nur, dass der Übertrag **selbst** keine Steuer auslöst. Was Du trotzdem korrekt mitführen musst, sind die **Anschaffungs­kosten** und das **Anschaffungs­datum** der übertragenen Lots — denn die brauchst Du beim **späteren Verkauf**.

Schief geht es, wenn der Broker (oder Deine Steuer-Software) die Lots am Übertragsdatum als „neu eingebracht zum Markt-Stichtagskurs" behandelt. Beispiel:

| Position | Wert |
|---|---|
| Kauf VW 2018 (LLC-Konto) | 100 Stk @ 130 € = 13.000 € |
| Migration auf Ireland-Konto 2022 | Markt­wert: 100 Stk @ 175 € = 17.500 € |
| Verkauf 2025 | 100 Stk @ 200 € = 20.000 € |

**Korrekt (Anschaffungs­kosten 2018 mitgenommen):**
Realisierter Gewinn = 20.000 − 13.000 = **7.000 €** → KESt 1.925 €

**Falsch (Migration als Neueinbringung 2022 zum Markt­wert behandelt):**
Realisierter Gewinn = 20.000 − 17.500 = **2.500 €** → KESt 687 €

Bei diesem Fehler **zahlst Du zu wenig KESt** — und riskierst eine Nach­zahlung plus Anspruchszinsen, wenn das Finanzamt das später aufrollt. Andersrum ist der Fehler im IBKR-Standard­fall **nicht der häufige** — IBKR übernimmt die Lots mit Original-Daten. Aber prüfen lohnt sich.

## Was Du konkret prüfen solltest

**1. FlexQuery-Section „Open Position Lots" oder „Closed Lots" für das neue Konto holen.**

Dort steht pro Lot ein `OPEN_DATE` und eine `COST_BASIS`.

**2. Vergleich mit dem alten Konto.**

Wenn Du einen FlexQuery-Export des **alten Kontos vor der Migration** hast (oder im IBKR Activity Statement nachschauen kannst), müssen `OPEN_DATE` und Kosten­basis pro Lot identisch sein.

**3. Sicherung der Belege.**

Speichere die letzte Activity-Statement-PDF des alten Kontos plus das erste neue Statement. Das ist Dein Nachweis im Streitfall — auch in 5 Jahren noch.

**4. Bei Übertrag zwischen eigenen Sub-Accounts** (Du selbst hast initiert):

IBKR-Statements der Quell- und Ziel-Konten miteinander abgleichen. Bei aktiv vom Anleger initiierten Inner-Broker-Übertragen sollte IBKR ebenfalls die Kosten­basis mit­geben, in Einzel­fällen ist hier aber Vorsicht angezeigt.

## Wo DepotTax Dich entlastet

DepotTax verarbeitet **mehrere IBKR-Konten gleichzeitig pro Person** und führt die Anschaffungs­kosten konsistent durch:

- Jeder **Open-Position-Lot** wird mit seinem **historischen `open_date`** und der **ursprünglichen Kosten­basis** importiert — auch wenn dieser Lot über einen Konten­übertrag auf das aktuelle Konto kam.
- Die **Tax-Engine (FIFO / Avg-Cost)** rechnet realisierte Gewinne immer gegen die historische Kosten­basis, nicht gegen einen späteren Markt­wert.
- Über alle Konten einer Person (z. B. U7960159 alt + U24061047 nach Migration) bekommst Du eine konsolidierte **Steuer­erklärungs-Beilage** als PDF — der Steuer­berater sieht beide Konten, die Werte stimmen.
- Im **Dashboard-Hinweis** flaggen wir Konten als „geschätzter Eröffnungs­bestand" auf, wenn die Lot-Historie nicht zurückverfolgbar ist — dann weißt Du, dass Du den Kosten­basis-Check händisch machen solltest.

[DepotTax → kostenlos testen](https://depottax.at/)

> 💬 Bei Unsicherheit über die richtige Behandlung eines konkreten Übertrags: Steuer­berater fragen, nicht raten. Wenn Du keinen hast und es um größere Beträge geht, [team@depottax.at](mailto:team@depottax.at) schreiben — wir vermitteln gerne an AT-Spezialisten mit Broker-Erfahrung.
