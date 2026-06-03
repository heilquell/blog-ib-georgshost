---
title: 'Forex bei IBKR in Österreich — § 27 oder § 31 EStG? (2026)'
date: 2026-06-03
lastmod: 2026-06-03
description: 'Spot-Forex bei IBKR ist in Österreich eine steuerliche Grauzone: Lager 1 sieht es als Termingeschäft (§ 27 Abs 4, 27,5 % Sondersatz, KZ 995/896), Lager 2 als privates Veräußerungsgeschäft (§ 31, 1-Jahres-Spekulationsfrist, Tarif). Was bedeutet das praktisch, wann brauchst Du den Steuerberater, und was passiert mit USD-Cash-Bestand?'
keywords: ['Forex Steuer Österreich', 'IBKR Forex AT Steuer', 'Spot-Forex § 27 § 31 EStG', 'USD-Cash Fremdwährung Österreich', 'KZ 995 896 Forex', 'EUR.USD Steuer Privatperson', 'Termingeschäft Spekulationsgeschäft']
tags: ['Forex', 'IBKR', 'E1kv', 'Österreich']
---

# Forex bei IBKR in Österreich — § 27 oder § 31 EStG?

> **Stand:** 2026-06-03 · **Lesezeit:** ~7 Minuten · **Gilt für:** AT-Privatpersonen mit IBKR (oder CapTrader / LYNX), die Spot-Forex handeln oder USD-Cash am Broker halten

Du hast bei IBKR 8 Forex-Trades gemacht, Saldo am Jahresende +1,16 €. Klingt nach „kann ich ignorieren". Oder Du hast in Wirklichkeit aktiv EUR.USD geskalpt, Gewinn 3.000 €. Jetzt schaust Du in die FlexQuery und siehst die Forex-Buchungen — und findest in der E1kv kein Feld dafür.

Willkommen in einer der **grauen Zonen** des österreichischen Steuerrechts. Es gibt zwei Auslegungen, beide werden in der Praxis vertreten, und beide haben sehr unterschiedliche Folgen für Dein Netto.

## Die zwei Lager in einem Satz

| Lager | Rechtsnorm | Steuersatz | Wo eintragen | Verlust-Verrechnung |
|---|---|---|---|---|
| **1** | § 27 Abs 4 EStG (Termingeschäft) | 27,5 % Sondersatz | KZ 995 (+) / KZ 896 (−) | im Wertpapier-Topf mit Aktien |
| **2** | § 31 EStG (privates Veräußerungsgeschäft) | Tarif bis 55 % | KZ 803 (+) / KZ 804 (−) | nur mit gleichartigen § 31-Gewinnen |

Praktischer Unterschied: **Bei Verlusten ist Lager 1 deutlich vorteilhafter**, weil die Forex-Verluste mit Aktien-Gewinnen im selben KESt-Topf gegenrechenbar sind. **Bei Gewinnen** kommt es darauf an, ob die Tarif-Belastung (Lager 2) niedriger ausfällt als 27,5 % — bei moderaten Einkommen unwahrscheinlich.

## Lager 1: § 27 Abs 4 EStG — „Termingeschäft"

Das gängige Modell in der Praxis. Logik:

- IBKR liefert Spot-Forex-Trades in der FlexQuery als reguläre Trade-Buchungen mit Buy/Sell, Mengenangaben, Kostenbasis und Erlös.
- Die typische Auslegung von IBKR-Resellern (CapTrader, LYNX) und vielen Steuerberatern: das ist wirtschaftlich ein **Termingeschäft auf Währungen** und fällt damit unter § 27 Abs 4 EStG.
- Konsequenz: 27,5 % Sondersteuersatz, Eintragung in KZ 995 (Überschüsse) und KZ 896 (Verluste).

**Stärken:**
- Verluste **voll verrechenbar** mit Aktien-Gewinnen im selben Wertpapier-Topf
- KESt-pauschal, kein Tarif-Bezug zum Gesamteinkommen
- Einfache Erfassung (1 Saldo-Zeile pro Jahr)

**Schwächen:**
- Vom **BMF nicht ausdrücklich abgesegnet**. Es gibt keine BFH/VwGH-Entscheidung, die explizit Spot-Forex bei Privatpersonen unter § 27 Abs 4 stellt.
- Bei einer strengen Auslegung argumentiert das Finanzamt: Spot-Forex ist **kein** Termingeschäft im engeren Sinn (kein zukünftiger Settlement-Termin).

## Lager 2: § 31 EStG — „Privates Veräußerungsgeschäft"

Die juristisch konservativere Variante. Logik:

- Spot-Forex ist im technischen Sinn **kein** Termingeschäft, weil Settlement T+2 (also faktisch sofort).
- Fremdwährung wird in AT als „**anderes Wirtschaftsgut**" behandelt — wenn Du sie innerhalb von **1 Jahr** nach Anschaffung wieder veräußerst, ist der Gewinn nach § 31 EStG (Spekulationsgeschäft) Tarifsteuer­pflichtig. Über 1 Jahr Haltedauer → steuerfrei.

**Stärken:**
- Rechtssicherer Pfad (BMF-konform)
- Bei langer Haltedauer (> 1 Jahr) **steuerfrei**

**Schwächen:**
- **Verluste nur mit gleichartigen § 31-Gewinnen verrechenbar**, nicht mit Aktien-Gewinnen. Praktisch oft tot.
- **Pro-Lot-Buchführung erforderlich** — jeder USD-Kauf hat eine eigene Anschaffungs-Zeile, jeder Verkauf muss gegen das richtige Lot zugeordnet werden. Das macht weder IBKR noch ein normaler Tax-Tool automatisch.
- Tarif bis 55 % — bei höherem Einkommen schlechter als 27,5 %.

## Was IBKR an der Quelle macht

IBKR (bzw. CapTrader / LYNX als Reseller) wendet **keine österreichische Steuersicht** an. Die FlexQuery liefert die Trades neutral, mit:

| Feld | Bedeutung |
|---|---|
| `asset_category` | `CASH` (Spot-Forex), `FUT` (FX-Future), `FOP` (FX-Option) |
| `realized_pnl` | EUR-Gewinn/Verlust nach IBKRs Avg-Cost-Methode |
| `commission` | Trade-Kommission |

Die Klassifikation in § 27 oder § 31 ist Dein Problem — IBKR weiß nicht, in welchem Steuersystem Du veranlagt wirst.

## Sonderfall: USD-Cash-Bestand ohne aktiven FX-Trade

Wenn Du eine US-Aktie verkaufst und das resultierende USD am Konto liegen lässt (z. B. mehrere Monate, ohne Reinvestition), entstehen durch EUR/USD-Kurs­schwankungen rechnerische Gewinne oder Verluste. **Was musst Du damit machen?**

- **In Deutschland**: § 23 EStG. USD-Cash gilt als eigenes Wirtschaftsgut, FIFO-Bewertung, FX-Differenz zwischen USD-Zufluss (Verkauf, Dividende) und USD-Abfluss (Wiederanlage) ist steuerpflichtig bei Spekulationsfrist unter 1 Jahr. [BFH VIII R 5/19, herrschende Auffassung.](https://www.bundesfinanzhof.de/de/entscheidung/entscheidungen-online/detail/STRE202210019/)
- **In Österreich**: **nicht relevant**. § 27 Abs 3 EStG greift bei „Einkünften aus der Überlassung von Kapital", und das setzt **Verzinslichkeit** voraus. Reine FX-Wertänderung auf einem nicht verzinsten USD-Cash-Bestand fällt durch das Raster.
- **Wenn das IBKR-USD-Cash Zinsen abwirft** (was es bei höheren Salden tut): das ist **strittig**, ob die FX-Komponente dann doch § 27 Abs 3 EStG-relevant wird. Praxis: viele AT-Anleger machen es nicht, das FA hat das bei reinen Privatpersonen bisher nicht aufgegriffen.

## Praktische Empfehlung

**Mini-Volumen** (Saldo < 100 €/Jahr, wenige Trades):
Nicht eintragen. Bei einer FA-Prüfung im Vermerk dokumentieren („Forex-Saldo wirtschaftlich unbedeutend, < Bagatellgrenze"). Belege aufbewahren.

**Moderates Volumen** (Saldo 100–2.000 €/Jahr, gelegentliches FX-Trading):
- Erstmal Lager 1 (KZ 995/896) ansetzen.
- Im Vermerk auf die strittige Klassifikation hinweisen.
- Bei Verlusten: voll verrechnen mit Aktien-Gewinnen.

**Aktiver Forex-Trader** (Gewinne > 2.000 €/Jahr, hunderte Trades):
- **Steuerberater konsultieren**, einmalig. Ein 1-Stunden-Termin klärt Deine konkrete Konstellation.
- Frage: Tariflage prüfen (passt § 31 mit Tarif vielleicht besser bei niedrigem Einkommen?), Pro-Lot-Buchführung machbar?
- Bei großen Volumina und Lager 1 droht im Streitfall eine Nachverhandlung — die Kostenfrage des Steuerberaters ist gegen die Nachzahlungs­risikoabwägung billig.

## Wo DepotTax Dich entlastet

DepotTax weist deine Forex-Trades **separat** im PDF aus (Sektion „Forex-Termingeschäfte" im Wertpapier-Detail) — bewusst **nicht** automatisch in KZ 995/896 eingerechnet, damit Du selbst entscheiden kannst, welcher Pfad zu deiner Konstellation passt:

- Saldo pro Jahr
- Σ positive / Σ negative
- Anzahl Closes
- Symbol-Detail über die /pivot-Auswertung (siehst Du, ob Du wirklich aktiv EUR.USD handelst oder nur Cash-Konversion machst)

Die [Trade-Kosten-Auswertung](https://depottax.at/) zeigt Dir zusätzlich, ob Forex-Spreads bei deiner Strategie überhaupt eine relevante Kostenposition sind — IBKR-Spreads liegen bei Major-Pairs typisch 0,2–0,5 Pips, bei kleineren Volumina sind das die echten Friktionskosten.

[DepotTax → kostenlos testen](https://depottax.at/)

> 💬 Hast Du eine konkrete Konstellation (großer USD-Cash-Bestand über Jahre, aktives Forex-Trading, FX-Termingeschäfte über Futures)? Schreib uns an [team@depottax.at](mailto:team@depottax.at) — bei größeren Beträgen vermitteln wir gerne an AT-Steuerberater mit Broker-Spezialisierung.
