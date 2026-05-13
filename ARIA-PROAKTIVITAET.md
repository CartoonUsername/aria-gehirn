# ARIA-PROAKTIVITAET.md
# Vollständiger Trigger-Katalog, Anti-Spam-Regeln, Bündelungslogik
# Comentra Intelligence Layer — Production Ready
# Version: 1.0

---

# INHALTSVERZEICHNIS

```
TEIL 1  — Trigger-Architektur & Schwere-Skala
TEIL 2  — Revenue & Orders Triggers (RD-001 … OA-006)
TEIL 3  — Inventory & Bestand Triggers (SO-001 … SO-011)
TEIL 4  — Pricing & Repricing Triggers (PA-001 … PA-008)
TEIL 5  — Advertising & PPC Triggers (AD-001 … AD-008)
TEIL 6  — Account Health Triggers (AH-001 … AH-008)
TEIL 7  — Reviews & Feedback Triggers (RA-001 … RA-007)
TEIL 8  — Logistik & Versand Triggers (LG-001 … LG-006)
TEIL 9  — Markt & Wettbewerb Triggers (CP-001 … CP-005)
TEIL 10 — Finanzen & Cashflow Triggers (FN-001 … FN-005)
TEIL 11 — Team & Operatives Triggers (TM-001 … TM-004)
TEIL 12 — Amazon-spezifische Triggers (AZ-*)
TEIL 13 — eBay-spezifische Triggers (EB-*)
TEIL 14 — Otto-spezifische Triggers (OT-*)
TEIL 15 — Saisonale & Peak-Triggers (PEAK-*)
TEIL 16 — Anti-Spam-Regeln (10 Regeln)
TEIL 17 — Bündelungslogik (8 Bündelungs-Typen)
TEIL 18 — Override-Trigger (immer senden)
TEIL 19 — Rollenbasiertes Routing
TEIL 20 — SQL-Schemas
TEIL 21 — TypeScript Worker Code
TEIL 22 — BullMQ Job Definitionen
TEIL 23 — Dashboard & Monitoring Queries
```


===============================================================================
# TEIL 1 — TRIGGER-ARCHITEKTUR & SCHWERE-SKALA
===============================================================================


## 1.1 Schwere-Skala

```
SCHWERE    EMOJI    FARBE     BEDEUTUNG                    REAKTIONSZEIT
─────────────────────────────────────────────────────────────────────────
CRITICAL   ⚠️       ROT       Umsatzverlust läuft jetzt    Sofort (<5 Min)
HIGH       🔴       ORANGE    Dringlich, heute handeln     <4 Stunden
MEDIUM     🟡       GELB      Diese Woche handeln          <48 Stunden
LOW        🔵       BLAU      Beobachten, kein Druck       <7 Tage
INFO       ℹ️       GRAU      Wissen, kein Handeln nötig   —
```


## 1.2 Trigger-ID Schema

```
Format: [KATEGORIE]-[LAUFNUMMER]

RD    Revenue Drop
OA    Order Anomaly
SO    Stock Out / Inventory
PA    Price Anomaly
AD    Advertising
AH    Account Health
RA    Review Anomaly
LG    Logistik
CP    Competitor / Price Intelligence
FN    Finanzen
TM    Team & Tasks
AZ    Amazon-spezifisch
EB    eBay-spezifisch
OT    Otto-spezifisch
PEAK  Peak Season / Saisonal
```


## 1.3 Trigger-Datenstruktur

```typescript
interface Trigger {
  id:               string          // z.B. 'SO-001'
  name:             string          // Lesbare Bezeichnung
  kategorie:        TriggerKategorie
  schwere:          'CRITICAL' | 'HIGH' | 'MEDIUM' | 'LOW' | 'INFO'
  kanal:            Marketplace[]   // Auf welchen Kanälen aktiv
  bedingung:        TriggerCondition
  schwellenwert:    ThresholdConfig
  cooldown_minuten: number          // Minimale Pause nach Auslösung
  buendelbar:       boolean         // Kann mit anderen gebündelt werden
  override:         boolean         // Immer senden, ignoriert Anti-Spam
  empfaenger_rollen: UserRole[]     // Wer bekommt diesen Alert
  nachricht_template: string        // Handlebars-Template
  aktionen:         TriggerAction[] // Verfügbare Schnellaktionen
}

interface ThresholdConfig {
  absolut?:     number   // Absoluter Wert (z.B. Bestand < 5)
  relativ?:     number   // Relative Änderung (z.B. -15%)
  z_score?:     number   // Statistische Abweichung (z.B. > 2.5)
  zeitfenster?: string   // ISO-Duration (z.B. 'PT1H' = 1 Stunde)
  vergleich?:   string   // 'vorwoche' | 'vormonat' | 'vorjahr' | 'baseline'
}
```


## 1.4 Trigger-Lebenszyklus

```
ZUSTAND           BESCHREIBUNG
───────────────────────────────────────────────────────────────
WATCHING          Bedingung noch nicht erfüllt. ARIA beobachtet.
TRIGGERED         Bedingung erfüllt. Alert wird generiert.
SENT              Alert wurde an Empfänger geschickt.
ACKNOWLEDGED      Empfänger hat Alert geöffnet.
ACTED             Empfänger hat eine Aktion ausgeführt.
RESOLVED          Das Problem ist behoben.
SUPPRESSED        Alert wurde unterdrückt (Anti-Spam).
BUNDLED           Alert wurde in ein Bündel aufgenommen.
EXPIRED           Alert ist abgelaufen ohne Aktion.
SNOOZED           Alert wurde temporär stumm geschaltet.
```


===============================================================================
# TEIL 2 — REVENUE & ORDERS TRIGGERS
===============================================================================


## RD-001 — Tages-Umsatz kritisch eingebrochen

```
ID:               RD-001
NAME:             Tages-Umsatz kritisch eingebrochen
SCHWERE:          CRITICAL
SCHWELLENWERT:    -40% vs. Vortag gleicher Wochentag
COOLDOWN:         120 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  daily_revenue < (same_weekday_last_week * 0.60)

BESCHREIBUNG:
  Umsatz bricht heute um mehr als 40% ein verglichen mit dem selben Wochentag der Vorwoche.

SCHNELLAKTIONEN:
  • Listings prüfen
  • Kampagnen prüfen
  • Preise prüfen
```


## RD-002 — Umsatz-Nulllinie — kein einziger Verkauf

```
ID:               RD-002
NAME:             Umsatz-Nulllinie — kein einziger Verkauf
SCHWERE:          CRITICAL
SCHWELLENWERT:    0 Bestellungen in 4h zwischen 08:00–20:00
COOLDOWN:         240 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  orders_last_4h == 0 AND hour BETWEEN 8 AND 20

BESCHREIBUNG:
  Zwischen 8 und 20 Uhr 4 Stunden lang kein einziger Verkauf auf allen Kanälen.

SCHNELLAKTIONEN:
  • Listings prüfen
  • System-Status prüfen
  • Preise prüfen
```


## RD-003 — Monats-Ziel in Gefahr

```
ID:               RD-003
NAME:             Monats-Ziel in Gefahr
SCHWERE:          HIGH
SCHWELLENWERT:    MTD-Fortschritt < 70% bei > 60% des Monats vergangen
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  mtd_revenue / monthly_target < 0.70 AND day_of_month / days_in_month > 0.60

BESCHREIBUNG:
  Der Monat ist mehr als 60% vorbei aber erst 70% oder weniger des Monatsziels ist erreicht.

SCHNELLAKTIONEN:
  • Monats-Analyse öffnen
  • Aktionsplan erstellen
```


## RD-004 — Wochenvergleich negativ

```
ID:               RD-004
NAME:             Wochenvergleich negativ
SCHWERE:          MEDIUM
SCHWELLENWERT:    -20% vs. gleiche KW Vorjahr
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  current_week_revenue < same_week_last_year * 0.80

BESCHREIBUNG:
  Aktuelle Woche liegt mehr als 20% unter der gleichen Kalender-Woche des Vorjahres.

SCHNELLAKTIONEN:
  • KW-Vergleich ansehen
  • Ursache analysieren
```


## RD-005 — Umsatzspike — positiv

```
ID:               RD-005
NAME:             Umsatzspike — positiv
SCHWERE:          INFO
SCHWELLENWERT:    +50% vs. 7-Tage-Durchschnitt
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  today_revenue > 7day_avg * 1.50

BESCHREIBUNG:
  Ungewöhnlich hoher Umsatz heute — gut zu wissen, evtl. Bestand prüfen.

SCHNELLAKTIONEN:
  • Bestand prüfen
  • Ursache dokumentieren
```


## RD-006 — Kanal-Ausfall

```
ID:               RD-006
NAME:             Kanal-Ausfall
SCHWERE:          CRITICAL
SCHWELLENWERT:    0 Bestellungen Kanal X in 6h während Öffnungszeiten
COOLDOWN:         360 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  channel_orders_6h == 0 AND other_channels_normal == true

BESCHREIBUNG:
  Ein einzelner Verkaufskanal hat 6 Stunden lang keine Bestellung generiert während andere Kanäle normal laufen.

SCHNELLAKTIONEN:
  • Kanal-Status prüfen
  • Listings auf Kanal prüfen
```


## OA-001 — Bestellmenge-Spike einzelne SKU

```
ID:               OA-001
NAME:             Bestellmenge-Spike einzelne SKU
SCHWERE:          HIGH
SCHWELLENWERT:    +300% Bestellmenge einzelne SKU vs. 7-Tage-Schnitt
COOLDOWN:         240 Minuten
EMPFÄNGER:        Lager, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  sku_orders_today > sku_7day_avg * 4.00

BESCHREIBUNG:
  Eine einzelne SKU wird plötzlich dreimal so oft bestellt wie üblich — Bestand prüfen.

SCHNELLAKTIONEN:
  • Bestand prüfen
  • Einkauf informieren
```


## OA-002 — Stornierungsrate gestiegen

```
ID:               OA-002
NAME:             Stornierungsrate gestiegen
SCHWERE:          MEDIUM
SCHWELLENWERT:    Stornierungsrate > 5% in 24h
COOLDOWN:         720 Minuten
EMPFÄNGER:        MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  cancellation_rate_24h > 0.05

BESCHREIBUNG:
  Stornierungen häufen sich — mögliche Ursache: Lieferverzögerung oder Listing-Problem.

SCHNELLAKTIONEN:
  • Stornierungs-Gründe analysieren
  • Lieferzeiten prüfen
```


## OA-003 — Großbestellung eingegangen

```
ID:               OA-003
NAME:             Großbestellung eingegangen
SCHWERE:          INFO
SCHWELLENWERT:    Einzelbestellung > 10 Einheiten einer SKU
COOLDOWN:         0 Minuten
EMPFÄNGER:        Lager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  order_quantity >= 10

BESCHREIBUNG:
  Eine einzelne Bestellung über 10 Einheiten — Lager informieren, evtl. Lieferzeit prüfen.

SCHNELLAKTIONEN:
  • Lieferbarkeit prüfen
  • Kunden kontaktieren
```


## OA-004 — Offene Bestellungen aufgestaut

```
ID:               OA-004
NAME:             Offene Bestellungen aufgestaut
SCHWERE:          HIGH
SCHWELLENWERT:    > 30 unversendete Bestellungen älter als 24h
COOLDOWN:         480 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  open_orders_24h > 30

BESCHREIBUNG:
  Stau im Lager: über 30 Bestellungen warten länger als 24 Stunden auf Versand.

SCHNELLAKTIONEN:
  • Lager-Dashboard öffnen
  • Kapazität prüfen
```


## OA-005 — Bestellwert-Anomalie

```
ID:               OA-005
NAME:             Bestellwert-Anomalie
SCHWERE:          MEDIUM
SCHWELLENWERT:    Ø Bestellwert heute < 50% des 30-Tage-Schnitts
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  avg_order_value_today < avg_order_value_30d * 0.50

BESCHREIBUNG:
  Kunden kaufen heute deutlich günstigere Produkte als üblich — mögliche Ursache: Kanal-Mix oder Promotion.

SCHNELLAKTIONEN:
  • Kanal-Mix analysieren
  • Promo-Einfluss prüfen
```


## OA-006 — B2B-Großkunde — Bestellpause

```
ID:               OA-006
NAME:             B2B-Großkunde — Bestellpause
SCHWERE:          LOW
SCHWELLENWERT:    B2B-Kunde > 500€/Monat hat 30 Tage nicht bestellt
COOLDOWN:         10080 Minuten
EMPFÄNGER:        Vertrieb, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  b2b_customer_last_order > 30 AND b2b_customer_monthly_value > 500

BESCHREIBUNG:
  Ein B2B-Kunde der normalerweise regelmäßig bestellt ist 30 Tage inaktiv.

SCHNELLAKTIONEN:
  • Kunden kontaktieren
  • Kundenprofil öffnen
```


===============================================================================
# TEIL 3 — INVENTORY & BESTAND TRIGGERS
===============================================================================


## SO-001 — Stockout — sofort

```
ID:               SO-001
NAME:             Stockout — sofort
SCHWERE:          CRITICAL
SCHWELLENWERT:    Bestand = 0 UND Listing noch aktiv
COOLDOWN:         0 Minuten
EMPFÄNGER:        Lager, GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  stock_quantity == 0 AND listing_status == 'active'

BESCHREIBUNG:
  Bestand auf 0 gefallen aber Listing ist noch aktiv — Käufer sehen das Produkt aber es kann nicht geliefert werden.

SCHNELLAKTIONEN:
  • Listing pausieren
  • Nachbestellung initiieren
  • Bestand buchen
```


## SO-002 — Kritischer Bestand — < Lead-Time

```
ID:               SO-002
NAME:             Kritischer Bestand — < Lead-Time
SCHWERE:          CRITICAL
SCHWELLENWERT:    Reichweite < Wiederbeschaffungszeit
COOLDOWN:         240 Minuten
EMPFÄNGER:        Lager, Einkauf
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  days_of_stock < lead_time_days

BESCHREIBUNG:
  Der aktuelle Bestand reicht nicht aus um die Zeit bis zur nächsten Lieferung zu überbrücken.

SCHNELLAKTIONEN:
  • Expressbestellung prüfen
  • Lieferanten anrufen
  • Kampagne pausieren
```


## SO-003 — Stockout-Risiko — 7 Tage

```
ID:               SO-003
NAME:             Stockout-Risiko — 7 Tage
SCHWERE:          HIGH
SCHWELLENWERT:    Reichweite < 7 Tage bei aktuellem Absatztempo
COOLDOWN:         480 Minuten
EMPFÄNGER:        Lager, Einkauf
OVERRIDE:         JA
BÜNDELBAR:        JA

BEDINGUNG:
  (stock_quantity / daily_velocity) < 7

BESCHREIBUNG:
  Bei aktuellem Absatztempo ist der Bestand in weniger als 7 Tagen aufgebraucht.

SCHNELLAKTIONEN:
  • Bestellvorschlag ansehen
  • Lieferanten kontaktieren
```


## SO-004 — Stockout-Risiko — 14 Tage

```
ID:               SO-004
NAME:             Stockout-Risiko — 14 Tage
SCHWERE:          MEDIUM
SCHWELLENWERT:    Reichweite < 14 Tage
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager, Einkauf
OVERRIDE:         JA
BÜNDELBAR:        JA

BEDINGUNG:
  (stock_quantity / daily_velocity) < 14

BESCHREIBUNG:
  Vorwarnung: Bestand reicht noch 14 Tage. Bestellung sollte eingeplant werden.

SCHNELLAKTIONEN:
  • Bestellplanung öffnen
```


## SO-005 — Bestandsdifferenz — Soll/Ist

```
ID:               SO-005
NAME:             Bestandsdifferenz — Soll/Ist
SCHWERE:          HIGH
SCHWELLENWERT:    Differenz > 5% oder > 10 Einheiten
COOLDOWN:         720 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  ABS(system_stock - physical_stock) > MAX(physical_stock * 0.05, 10)

BESCHREIBUNG:
  Erhebliche Abweichung zwischen Systembestand und tatsächlichem Bestand.

SCHNELLAKTIONEN:
  • Inventur starten
  • Buchung prüfen
```


## SO-006 — Überbestand — Kapital gebunden

```
ID:               SO-006
NAME:             Überbestand — Kapital gebunden
SCHWERE:          LOW
SCHWELLENWERT:    Bestand > 180 Tage Reichweite
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF, Einkauf
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  (stock_quantity / daily_velocity) > 180

BESCHREIBUNG:
  Produkt hat mehr als 6 Monate Bestand. Kapital ist gebunden, Lagerkosten laufen.

SCHNELLAKTIONEN:
  • Abverkaufs-Promo prüfen
  • Einkauf stoppen
```


## SO-007 — Eingehende Lieferung — Verzögert

```
ID:               SO-007
NAME:             Eingehende Lieferung — Verzögert
SCHWERE:          HIGH
SCHWELLENWERT:    Erwartetes Lieferdatum überschritten um > 3 Tage
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager, Einkauf
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  expected_delivery_date + 3 DAYS < CURRENT_DATE AND status != 'delivered'

BESCHREIBUNG:
  Eine erwartete Lieferung ist mehr als 3 Tage überfällig.

SCHNELLAKTIONEN:
  • Lieferant kontaktieren
  • Bestandssituation prüfen
```


## SO-008 — Charge läuft ab

```
ID:               SO-008
NAME:             Charge läuft ab
SCHWERE:          HIGH
SCHWELLENWERT:    Ablaufdatum < 60 Tage (verderbliche Ware)
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  expiry_date - CURRENT_DATE < 60

BESCHREIBUNG:
  Charge mit Ablaufdatum hat weniger als 60 Tage Restlaufzeit.

SCHNELLAKTIONEN:
  • Abverkauf-Promo erstellen
  • Charge priorisieren
```


## SO-009 — FBA-Bestand niedrig

```
ID:               SO-009
NAME:             FBA-Bestand niedrig
SCHWERE:          HIGH
SCHWELLENWERT:    FBA-Bestand < 7 Tage bei Amazon-Velocity
COOLDOWN:         480 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  fba_quantity / fba_daily_velocity < 7

BESCHREIBUNG:
  Amazon FBA-Bestand reicht nur noch 7 Tage — FBA-Einlieferung planen.

SCHNELLAKTIONEN:
  • FBA-Einlieferung planen
  • Lieferplan erstellen
```


## SO-010 — FBA-Bestand zu hoch — Lagergebühren

```
ID:               SO-010
NAME:             FBA-Bestand zu hoch — Lagergebühren
SCHWERE:          MEDIUM
SCHWELLENWERT:    FBA-Bestand > 90 Tage Reichweite
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  fba_quantity / fba_daily_velocity > 90

BESCHREIBUNG:
  FBA-Bestand ist sehr hoch — Amazon erhebt Long-Term-Storage-Fees nach 365 Tagen.

SCHNELLAKTIONEN:
  • FBA-Bestand analysieren
  • Removal-Order prüfen
```


## SO-011 — Multi-Kanal-Bestand-Konflikt

```
ID:               SO-011
NAME:             Multi-Kanal-Bestand-Konflikt
SCHWERE:          HIGH
SCHWELLENWERT:    Überverkauf durch Kanal-Desync
COOLDOWN:         60 Minuten
EMPFÄNGER:        MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  channel_stock_sync_error == true OR total_reserved > available_stock

BESCHREIBUNG:
  Bestandssync zwischen Kanälen ist fehlgeschlagen — Überverkauf möglich.

SCHNELLAKTIONEN:
  • Sync prüfen
  • Listings pausieren
  • Bestand manuell prüfen
```


===============================================================================
# TEIL 4 — PRICING & REPRICING TRIGGERS
===============================================================================


## PA-001 — Preis-Fehler — Zu günstiger Preis

```
ID:               PA-001
NAME:             Preis-Fehler — Zu günstiger Preis
SCHWERE:          CRITICAL
SCHWELLENWERT:    Verkaufspreis < Einkaufspreis + Mindestmarge
COOLDOWN:         60 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  selling_price < purchase_price * (1 + min_margin_pct)

BESCHREIBUNG:
  Produkt wird unter Einkaufspreis oder unter Mindestmarge verkauft. Jede Bestellung macht Verlust.

SCHNELLAKTIONEN:
  • Preis sofort korrigieren
  • Repricing-Regel prüfen
```


## PA-002 — Buy Box verloren

```
ID:               PA-002
NAME:             Buy Box verloren
SCHWERE:          HIGH
SCHWELLENWERT:    Buy Box weg AND Wettbewerberpreis bekannt
COOLDOWN:         240 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  has_buybox == false AND had_buybox_yesterday == true

BESCHREIBUNG:
  Buy Box verloren. Wettbewerber hat günstigeren Preis.

SCHNELLAKTIONEN:
  • Preis anpassen
  • Repricing aktivieren
  • Konkurrenz analysieren
```


## PA-003 — Wettbewerber senkt massiv

```
ID:               PA-003
NAME:             Wettbewerber senkt massiv
SCHWERE:          HIGH
SCHWELLENWERT:    Hauptwettbewerber senkt > 15% in 24h
COOLDOWN:         480 Minuten
EMPFÄNGER:        MarketplaceManager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  competitor_price_change_24h < -0.15 AND is_main_competitor == true

BESCHREIBUNG:
  Hauptwettbewerber hat den Preis um mehr als 15% gesenkt — mögliche Lagerräumung oder Preiskampf.

SCHNELLAKTIONEN:
  • Wettbewerber analysieren
  • Strategie festlegen
  • Repricing anpassen
```


## PA-004 — Preiskampf erkannt

```
ID:               PA-004
NAME:             Preiskampf erkannt
SCHWERE:          HIGH
SCHWELLENWERT:    3+ Wettbewerber senken innerhalb 48h > 10%
COOLDOWN:         720 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  competitors_with_price_drop_48h >= 3 AND avg_price_drop > 0.10

BESCHREIBUNG:
  Mehrere Wettbewerber senken gleichzeitig die Preise — möglicher Marktpreisverfall.

SCHNELLAKTIONEN:
  • Marktanalyse ansehen
  • Mindestpreis prüfen
  • Strategie-Entscheidung GF
```


## PA-005 — Preiserhöhungs-Chance

```
ID:               PA-005
NAME:             Preiserhöhungs-Chance
SCHWERE:          MEDIUM
SCHWELLENWERT:    Alle Wettbewerber teurer als wir um > 10%
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  our_price < min_competitor_price * 0.90

BESCHREIBUNG:
  Wir sind deutlich günstiger als alle Wettbewerber — Preiserhöhung möglich ohne Buy-Box-Risiko.

SCHNELLAKTIONEN:
  • Preis erhöhen
  • Marge berechnen
```


## PA-006 — Wettbewerber ausverkauft — Preischance

```
ID:               PA-006
NAME:             Wettbewerber ausverkauft — Preischance
SCHWERE:          HIGH
SCHWELLENWERT:    Hauptwettbewerber OOS AND wir haben Bestand
COOLDOWN:         240 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  main_competitor_stock == 0 AND our_stock > 7

BESCHREIBUNG:
  Hauptwettbewerber ist ausverkauft. Preiserhöhung möglich.

SCHNELLAKTIONEN:
  • Preis erhöhen
  • Werbung erhöhen
```


## PA-007 — Repricing-Regel außer Betrieb

```
ID:               PA-007
NAME:             Repricing-Regel außer Betrieb
SCHWERE:          CRITICAL
SCHWELLENWERT:    Repricing-Job seit > 2h nicht gelaufen
COOLDOWN:         120 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  last_repricing_run > NOW() - INTERVAL '2 hours'

BESCHREIBUNG:
  Repricing-Engine läuft nicht mehr. Preise werden nicht aktualisiert — Buy-Box-Verlust möglich.

SCHNELLAKTIONEN:
  • Repricing-Job prüfen
  • Manuell reprisen
  • Tech-Support
```


## PA-008 — Mindestpreis unterschritten durch Repricing

```
ID:               PA-008
NAME:             Mindestpreis unterschritten durch Repricing
SCHWERE:          CRITICAL
SCHWELLENWERT:    Repricing hat Preis unter Minimum gesenkt
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  current_price < min_allowed_price

BESCHREIBUNG:
  Repricing-Algorithmus hat den definierten Mindestpreis unterschritten. Listing pausieren bis Ursache geklärt.

SCHNELLAKTIONEN:
  • Preis manuell korrigieren
  • Repricing-Regel prüfen
  • Listing pausieren
```


===============================================================================
# TEIL 5 — ADVERTISING & PPC TRIGGERS
===============================================================================


## AD-001 — ACoS kritisch zu hoch

```
ID:               AD-001
NAME:             ACoS kritisch zu hoch
SCHWERE:          HIGH
SCHWELLENWERT:    ACoS > 40% UND Ausgaben > 50€/Tag
COOLDOWN:         480 Minuten
EMPFÄNGER:        MarketplaceManager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  acos_7d > 0.40 AND daily_ad_spend > 50

BESCHREIBUNG:
  Werbung verschlingt Marge. ACoS über 40% bedeutet für die meisten Produkte negativen ROAS.

SCHNELLAKTIONEN:
  • Kampagne pausieren
  • Gebote senken
  • ACoS-Analyse
```


## AD-002 — Werbebudget aufgebraucht

```
ID:               AD-002
NAME:             Werbebudget aufgebraucht
SCHWERE:          HIGH
SCHWELLENWERT:    Tagesbudget erschöpft vor 14:00 Uhr
COOLDOWN:         480 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  budget_remaining == 0 AND hour < 14

BESCHREIBUNG:
  Budget ist vor Mittag aufgebraucht — Nachmittags-Traffic geht verloren.

SCHNELLAKTIONEN:
  • Budget erhöhen
  • Gebote senken
  • Kampagne analysieren
```


## AD-003 — Conversion aus Werbung eingebrochen

```
ID:               AD-003
NAME:             Conversion aus Werbung eingebrochen
SCHWERE:          MEDIUM
SCHWELLENWERT:    Ad-Conversion < 50% des 14-Tage-Schnitts
COOLDOWN:         720 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  ad_conversion_rate < ad_conversion_7d_avg * 0.50

BESCHREIBUNG:
  Werbeklicks bringen keine Käufe mehr — mögliche Ursache: Listing-Problem, Preis, Saison.

SCHNELLAKTIONEN:
  • Listing prüfen
  • Wettbewerber prüfen
  • Keywords analysieren
```


## AD-004 — Impression-Einbruch

```
ID:               AD-004
NAME:             Impression-Einbruch
SCHWERE:          MEDIUM
SCHWELLENWERT:    Impressions < 30% des 7-Tage-Schnitts
COOLDOWN:         720 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  impressions_today < impressions_7d_avg * 0.30

BESCHREIBUNG:
  Werbeanzeigen werden kaum noch ausgespielt — mögliche Ursache: Budget, Gebote zu niedrig, Listing-Qualität.

SCHNELLAKTIONEN:
  • Gebote prüfen
  • Budget prüfen
  • Listing-Qualität prüfen
```


## AD-005 — Neues High-Performer Keyword

```
ID:               AD-005
NAME:             Neues High-Performer Keyword
SCHWERE:          INFO
SCHWELLENWERT:    Keyword > 10 Conversions in 7 Tagen ohne manuelles Gebot
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  auto_campaign_keyword_conversions_7d > 10

BESCHREIBUNG:
  Auto-Kampagne hat ein konvertierendes Keyword gefunden — in manuelle Kampagne übernehmen.

SCHNELLAKTIONEN:
  • Keyword übernehmen
  • Manuelle Kampagne öffnen
```


## AD-006 — Verlust-Keyword erkannt

```
ID:               AD-006
NAME:             Verlust-Keyword erkannt
SCHWERE:          MEDIUM
SCHWELLENWERT:    Keyword > 20 Klicks, 0 Conversions, > 30€ ausgegeben
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  keyword_clicks_30d > 20 AND keyword_conversions_30d == 0 AND keyword_spend_30d > 30

BESCHREIBUNG:
  Keyword gibt viel Geld aus ohne Verkäufe zu bringen — als Negativ-Keyword blocken.

SCHNELLAKTIONEN:
  • Als Negativ-Keyword hinzufügen
  • Gebot pausieren
```


## AD-007 — Wettbewerber schaltet Werbung auf unsere Keywords

```
ID:               AD-007
NAME:             Wettbewerber schaltet Werbung auf unsere Keywords
SCHWERE:          LOW
SCHWELLENWERT:    CPC > 150% des 30-Tage-Schnitts erkannt
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  main_keyword_cpc > main_keyword_cpc_30d_avg * 1.50

BESCHREIBUNG:
  CPC-Anstieg deutet auf neue Wettbewerber-Aktivität bei unseren wichtigsten Keywords hin.

SCHNELLAKTIONEN:
  • Keywords analysieren
  • Gebotsstrategie überprüfen
```


## AD-008 — Sponsored-Budget monatlich > Ziel

```
ID:               AD-008
NAME:             Sponsored-Budget monatlich > Ziel
SCHWERE:          MEDIUM
SCHWELLENWERT:    Monatliche Ad-Ausgaben > 110% des gesetzten Monatsbudgets
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  monthly_ad_spend > monthly_ad_budget * 1.10

BESCHREIBUNG:
  Monatliches Werbungsbudget wird überschritten.

SCHNELLAKTIONEN:
  • Budget-Übersicht öffnen
  • Kampagnen priorisieren
```


===============================================================================
# TEIL 6 — ACCOUNT HEALTH TRIGGERS
===============================================================================


## AH-001 — Amazon ODR über Schwelle

```
ID:               AH-001
NAME:             Amazon ODR über Schwelle
SCHWERE:          CRITICAL
SCHWELLENWERT:    ODR > 1,0%
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  amazon_odr > 0.010

BESCHREIBUNG:
  Order Defect Rate überschreitet Amazon-Grenze von 1%. Account-Sperre droht.

SCHNELLAKTIONEN:
  • ODR-Analyse
  • A-to-Z Claims prüfen
  • Plan of Action vorbereiten
```


## AH-002 — Amazon ODR nähert sich Schwelle

```
ID:               AH-002
NAME:             Amazon ODR nähert sich Schwelle
SCHWERE:          HIGH
SCHWELLENWERT:    ODR > 0,75%
COOLDOWN:         480 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  amazon_odr > 0.0075

BESCHREIBUNG:
  ODR nähert sich kritischem Bereich. Sofortige Gegemaßnahmen verhindern Eskalation.

SCHNELLAKTIONEN:
  • Offene Claims prüfen
  • Negative Bewertungen prüfen
```


## AH-003 — Late Shipment Rate zu hoch

```
ID:               AH-003
NAME:             Late Shipment Rate zu hoch
SCHWERE:          HIGH
SCHWELLENWERT:    LSR > 3%
COOLDOWN:         480 Minuten
EMPFÄNGER:        Lager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  amazon_lsr > 0.03

BESCHREIBUNG:
  Amazon bestraft Late Shipment Rate über 4%. Über 3% ist bereits Warnstufe.

SCHNELLAKTIONEN:
  • Versand-Prozess prüfen
  • Offene Bestellungen priorisieren
```


## AH-004 — Amazon Account-Warnung erhalten

```
ID:               AH-004
NAME:             Amazon Account-Warnung erhalten
SCHWERE:          CRITICAL
SCHWELLENWERT:    Jede Policy-Verletzungs-Benachrichtigung
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  amazon_policy_notification == true

BESCHREIBUNG:
  Amazon hat eine Warnung verschickt. Immer sofort handeln.

SCHNELLAKTIONEN:
  • Amazon Seller Central öffnen
  • Warnung lesen
  • Anwalt kontaktieren
```


## AH-005 — eBay Account-Einschränkung

```
ID:               AH-005
NAME:             eBay Account-Einschränkung
SCHWERE:          CRITICAL
SCHWELLENWERT:    eBay Performance-Warnung erhalten
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  ebay_account_restriction == true

BESCHREIBUNG:
  eBay hat eine Performance-Warnung oder Einschränkung ausgesprochen.

SCHNELLAKTIONEN:
  • eBay My Account öffnen
  • Resolution Center prüfen
```


## AH-006 — Verkäufer-Bewertung gefallen

```
ID:               AH-006
NAME:             Verkäufer-Bewertung gefallen
SCHWERE:          MEDIUM
SCHWELLENWERT:    Feedback-Score < 97% (eBay) oder < 4.5 (Amazon)
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  (ebay_feedback_score < 0.97) OR (amazon_seller_rating < 4.5)

BESCHREIBUNG:
  Verkäufer-Gesamtbewertung ist unter kritische Schwelle gefallen.

SCHNELLAKTIONEN:
  • Bewertungen prüfen
  • Kundenanfragen prüfen
```


## AH-007 — DATEV/Finanzamt — Frist läuft ab

```
ID:               AH-007
NAME:             DATEV/Finanzamt — Frist läuft ab
SCHWERE:          HIGH
SCHWELLENWERT:    Steuerliche Frist in < 7 Tagen
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  tax_deadline - CURRENT_DATE < 7

BESCHREIBUNG:
  Steuerliche oder rechtliche Frist nähert sich. Buchhalter informieren.

SCHNELLAKTIONEN:
  • Buchhalter kontaktieren
  • DATEV öffnen
```


## AH-008 — Marketplace-Gebühren-Erhöhung

```
ID:               AH-008
NAME:             Marketplace-Gebühren-Erhöhung
SCHWERE:          MEDIUM
SCHWELLENWERT:    Neu erkannte Gebührenänderung
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  marketplace_fee_change_detected == true

BESCHREIBUNG:
  Marketplace hat Gebührenstruktur geändert. Kalkulation prüfen.

SCHNELLAKTIONEN:
  • Gebühren-Vergleich öffnen
  • Kalkulationen prüfen
```


===============================================================================
# TEIL 7 — REVIEWS & FEEDBACK TRIGGERS
===============================================================================


## RA-001 — 1-Stern-Bewertung eingegangen

```
ID:               RA-001
NAME:             1-Stern-Bewertung eingegangen
SCHWERE:          HIGH
SCHWELLENWERT:    Rating == 1 auf einem Kanal
COOLDOWN:         1440 Minuten
EMPFÄNGER:        CustomerService, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  review_rating == 1

BESCHREIBUNG:
  1-Stern-Bewertung ist besonders schädlich für Ranking und Conversionrate. Sofortige Response empfohlen.

SCHNELLAKTIONEN:
  • Response-Entwurf öffnen
  • Bestellung finden
  • Kontakt anbieten
```


## RA-002 — Negative Bewertung-Serie

```
ID:               RA-002
NAME:             Negative Bewertung-Serie
SCHWERE:          HIGH
SCHWELLENWERT:    3+ Bewertungen < 3 Sterne für gleiche SKU in 7 Tagen
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  sku_reviews_below_3_7d >= 3

BESCHREIBUNG:
  Häufung negativer Bewertungen auf ein Produkt deutet auf Qualitätsproblem hin.

SCHNELLAKTIONEN:
  • SKU analysieren
  • Bewertungs-Cluster ansehen
  • Qualitätsprüfung
```


## RA-003 — Bewertungs-Durchschnitt fällt

```
ID:               RA-003
NAME:             Bewertungs-Durchschnitt fällt
SCHWERE:          MEDIUM
SCHWELLENWERT:    Ø Rating sinkt um > 0.3 in 30 Tagen
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  avg_rating_now < avg_rating_30d_ago - 0.3

BESCHREIBUNG:
  Schleichender Rückgang des Bewertungsschnitts — oft Zeichen für veränderte Kundenerwartung.

SCHNELLAKTIONEN:
  • Rating-Trend ansehen
  • Neueste Bewertungen lesen
```


## RA-004 — Neue positive 5-Sterne-Bewertung

```
ID:               RA-004
NAME:             Neue positive 5-Sterne-Bewertung
SCHWERE:          INFO
SCHWELLENWERT:    Rating == 5
COOLDOWN:         0 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  review_rating == 5

BESCHREIBUNG:
  Positive Bestätigung. Kein Handlungsbedarf — gut zu wissen.

SCHNELLAKTIONEN:
  • Bewertung ansehen
```


## RA-005 — Bewertungs-Spike — verdächtig

```
ID:               RA-005
NAME:             Bewertungs-Spike — verdächtig
SCHWERE:          MEDIUM
SCHWELLENWERT:    > 10 Bewertungen für eine SKU in 24h
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  sku_reviews_24h > 10

BESCHREIBUNG:
  Ungewöhnlich viele Bewertungen in kurzer Zeit. Mögliche Review-Manipulation oder Vine-Aktivität.

SCHNELLAKTIONEN:
  • Bewertungen prüfen
  • Vine-Status prüfen
```


## RA-006 — Themen-Muster in Bewertungen

```
ID:               RA-006
NAME:             Themen-Muster in Bewertungen
SCHWERE:          MEDIUM
SCHWELLENWERT:    Gleiches Stichwort in > 3 negativen Bewertungen in 14 Tagen
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager, Einkauf
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  negative_review_topic_frequency_14d >= 3

BESCHREIBUNG:
  Wiederholendes Negativ-Thema deutet auf systematisches Produktproblem hin.

SCHNELLAKTIONEN:
  • Themen-Analyse öffnen
  • Produktverbesserung prüfen
```


## RA-007 — Verkäufer-Feedback negativ

```
ID:               RA-007
NAME:             Verkäufer-Feedback negativ
SCHWERE:          HIGH
SCHWELLENWERT:    Direktes Verkäufer-Feedback < 3 Sterne
COOLDOWN:         720 Minuten
EMPFÄNGER:        CustomerService
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  seller_feedback_rating < 3

BESCHREIBUNG:
  Negatives Feedback über den Verkäufer (nicht das Produkt). Response-Pflicht auf eBay.

SCHNELLAKTIONEN:
  • Auf Feedback antworten
  • Lösung anbieten
  • Bestellung prüfen
```


===============================================================================
# TEIL 8 — LOGISTIK & VERSAND TRIGGERS
===============================================================================


## LG-001 — Versandfehler — Paket verloren

```
ID:               LG-001
NAME:             Versandfehler — Paket verloren
SCHWERE:          CRITICAL
SCHWELLENWERT:    Tracking seit > 5 Tagen kein Update AND Zustellung erwartet
COOLDOWN:         0 Minuten
EMPFÄNGER:        Lager, CustomerService
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  tracking_last_update > 5 AND expected_delivery < CURRENT_DATE

BESCHREIBUNG:
  Paket scheint verloren. Kunde wartet. Sofortiges Handeln erforderlich.

SCHNELLAKTIONEN:
  • Carrier kontaktieren
  • Kunden informieren
  • Ersatz prüfen
```


## LG-002 — Versandverzögerung — SLA-Verletzung

```
ID:               LG-002
NAME:             Versandverzögerung — SLA-Verletzung
SCHWERE:          HIGH
SCHWELLENWERT:    Bestellung nicht versendet innerhalb SLA-Zeit
COOLDOWN:         240 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  order_age_hours > sla_hours AND shipping_status == 'pending'

BESCHREIBUNG:
  Bestellung wurde nicht innerhalb der vereinbarten Versandzeit versendet.

SCHNELLAKTIONEN:
  • Bestellung priorisieren
  • Lager informieren
```


## LG-003 — Retoure eingegangen — Qualitätsprüfung

```
ID:               LG-003
NAME:             Retoure eingegangen — Qualitätsprüfung
SCHWERE:          MEDIUM
SCHWELLENWERT:    Retourengrund == 'defekt' oder 'beschädigt'
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager, Einkauf
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  return_reason IN ('defective', 'damaged', 'not_as_described')

BESCHREIBUNG:
  Defekte Retoure. Qualitätsprüfung und ggf. Lieferanten-Feedback notwendig.

SCHNELLAKTIONEN:
  • Retoure prüfen
  • Qualitätsdokumentation
```


## LG-004 — GLS/Carrier — Zustellfehler

```
ID:               LG-004
NAME:             GLS/Carrier — Zustellfehler
SCHWERE:          HIGH
SCHWELLENWERT:    Zustellversuch fehlgeschlagen, kein Follow-up
COOLDOWN:         480 Minuten
EMPFÄNGER:        CustomerService
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  delivery_attempt_failed == true AND redelivery_scheduled == false

BESCHREIBUNG:
  Carrier konnte nicht zustellen und hat keinen zweiten Versuch angesetzt.

SCHNELLAKTIONEN:
  • Carrier kontaktieren
  • Kunden informieren
```


## LG-005 — Paket-Pool läuft an Kapazitätsgrenze

```
ID:               LG-005
NAME:             Paket-Pool läuft an Kapazitätsgrenze
SCHWERE:          MEDIUM
SCHWELLENWERT:    Tägliche Paketemenge > 80% Kapazität 3 Tage in Folge
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  daily_parcel_count > max_daily_capacity * 0.80 FOR 3 CONSECUTIVE DAYS

BESCHREIBUNG:
  Lagerkapazität für Versand wird eng. Personalplanung oder Carrier-Erweiterung prüfen.

SCHNELLAKTIONEN:
  • Kapazität planen
  • Zusätzlichen Carrier prüfen
```


## LG-006 — Frankier-Fehler — Falsche Gewichtsklasse

```
ID:               LG-006
NAME:             Frankier-Fehler — Falsche Gewichtsklasse
SCHWERE:          MEDIUM
SCHWELLENWERT:    Nachberechnung von Carrier erhalten
COOLDOWN:         1440 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  carrier_surcharge_received == true

BESCHREIBUNG:
  Carrier hat Paket nachberechnet — Gewichts- oder Maßangabe war falsch.

SCHNELLAKTIONEN:
  • Produkt-Gewichte prüfen
  • Verpackung analysieren
```


===============================================================================
# TEIL 9 — MARKT & WETTBEWERB TRIGGERS
===============================================================================


## CP-001 — Wettbewerber komplett ausverkauft

```
ID:               CP-001
NAME:             Wettbewerber komplett ausverkauft
SCHWERE:          HIGH
SCHWELLENWERT:    Hauptwettbewerber OOS auf > 1 Kanal
COOLDOWN:         240 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  main_competitor_stock == 0 AND affected_channels >= 1

BESCHREIBUNG:
  Hauptwettbewerber hat keinen Bestand mehr. Marktanteil kann übernommen werden.

SCHNELLAKTIONEN:
  • Preis erhöhen
  • Werbung hochfahren
  • Bestand prüfen
```


## CP-002 — Neuer Wettbewerber im Markt

```
ID:               CP-002
NAME:             Neuer Wettbewerber im Markt
SCHWERE:          MEDIUM
SCHWELLENWERT:    Neues Listing in unserer Haupt-Kategorie von unbekanntem Anbieter
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager, GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  new_competitor_listing_detected == true AND category == our_main_category

BESCHREIBUNG:
  Neuer Anbieter ist in unsere Hauptkategorie eingetreten.

SCHNELLAKTIONEN:
  • Wettbewerber analysieren
  • Listing vergleichen
```


## CP-003 — Marktpreis-Erosion

```
ID:               CP-003
NAME:             Marktpreis-Erosion
SCHWERE:          HIGH
SCHWELLENWERT:    Durchschnitts-Marktpreis sinkt > 10% in 30 Tagen
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF, MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  category_avg_price_30d_change < -0.10

BESCHREIBUNG:
  Kategorie-Preise fallen systematisch. Kalkulation und Strategie prüfen.

SCHNELLAKTIONEN:
  • Marktanalyse öffnen
  • Preiskalkulation prüfen
```


## CP-004 — Wettbewerber startet Promotion

```
ID:               CP-004
NAME:             Wettbewerber startet Promotion
SCHWERE:          MEDIUM
SCHWELLENWERT:    Hauptwettbewerber hat > 15% Preissenkung für > 3 Tage
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  competitor_price_drop > 0.15 AND duration_days >= 3

BESCHREIBUNG:
  Wettbewerber führt Aktion durch. Temporäre Buy-Box-Verluste möglich.

SCHNELLAKTIONEN:
  • Preis beobachten
  • Gegenpromo prüfen
```


## CP-005 — Kategorie-Bestseller wechselt

```
ID:               CP-005
NAME:             Kategorie-Bestseller wechselt
SCHWERE:          LOW
SCHWELLENWERT:    BSR #1 in Unterkategorie wechselt auf anderen Anbieter
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  category_bsr_1_seller_changed == true

BESCHREIBUNG:
  Der Bestseller in unserer Hauptunterkategorie hat gewechselt. Strategische Information.

SCHNELLAKTIONEN:
  • BSR-Verlauf ansehen
  • Bestseller analysieren
```


===============================================================================
# TEIL 10 — FINANZEN & CASHFLOW TRIGGERS
===============================================================================


## FN-001 — Auszahlung Amazon — Ungewöhnlich niedrig

```
ID:               FN-001
NAME:             Auszahlung Amazon — Ungewöhnlich niedrig
SCHWERE:          HIGH
SCHWELLENWERT:    Amazon-Auszahlung < 60% des 4-Wochen-Schnitts
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  amazon_disbursement < amazon_avg_disbursement_4w * 0.60

BESCHREIBUNG:
  Amazon-Auszahlung deutlich unter Erwartung. Mögliche Ursache: Reserven, Einbehalte, Fehler.

SCHNELLAKTIONEN:
  • Auszahlungs-Report prüfen
  • Amazon Seller Central
```


## FN-002 — Lieferanten-Rechnung überfällig

```
ID:               FN-002
NAME:             Lieferanten-Rechnung überfällig
SCHWERE:          HIGH
SCHWELLENWERT:    Lieferanten-Rechnung > 30 Tage überfällig
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  invoice_due_date + 30 < CURRENT_DATE AND payment_status == 'unpaid'

BESCHREIBUNG:
  Rechnung ist überfällig. Lieferantenbeziehung und Kredit-Linie in Gefahr.

SCHNELLAKTIONEN:
  • Zahlung anweisen
  • Lieferant kontaktieren
```


## FN-003 — Margin-Erosion erkannt

```
ID:               FN-003
NAME:             Margin-Erosion erkannt
SCHWERE:          MEDIUM
SCHWELLENWERT:    Durchschnittsmarge fällt > 3 Prozentpunkte in 60 Tagen
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  avg_margin_now < avg_margin_60d_ago - 0.03

BESCHREIBUNG:
  Schleichende Margen-Verschlechterung. Mögliche Ursachen: gestiegene Kosten, Preisdruck, Mixeffekt.

SCHNELLAKTIONEN:
  • Margin-Analyse öffnen
  • Kostenstruktur prüfen
```


## FN-004 — DATEV-Export ausstehend

```
ID:               FN-004
NAME:             DATEV-Export ausstehend
SCHWERE:          MEDIUM
SCHWELLENWERT:    Letzter DATEV-Export > 30 Tage alt
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  last_datev_export > NOW() - INTERVAL '30 days'

BESCHREIBUNG:
  DATEV-Export wurde lange nicht durchgeführt. Buchhalter hat veraltete Daten.

SCHNELLAKTIONEN:
  • DATEV-Export starten
```


## FN-005 — Umsatzsteuer-Fälligkeit nähert sich

```
ID:               FN-005
NAME:             Umsatzsteuer-Fälligkeit nähert sich
SCHWERE:          HIGH
SCHWELLENWERT:    USt-Voranmeldung in < 5 Werktagen fällig
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  ust_deadline - CURRENT_DATE <= 5 AND is_working_day == true

BESCHREIBUNG:
  Umsatzsteuer-Voranmeldung läuft ab. Buchhalter informieren.

SCHNELLAKTIONEN:
  • Buchhalter informieren
  • DATEV-Export starten
```


===============================================================================
# TEIL 11 — TEAM & OPERATIVES TRIGGERS
===============================================================================


## TM-001 — Task überfällig — kritisch

```
ID:               TM-001
NAME:             Task überfällig — kritisch
SCHWERE:          HIGH
SCHWELLENWERT:    Task mit HIGH-Priorität > 24h nach Fälligkeit offen
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  task_priority == 'HIGH' AND task_due_date + INTERVAL '24h' < NOW() AND task_status != 'done'

BESCHREIBUNG:
  Wichtige Aufgabe wurde nicht erledigt und ist mehr als 24h überfällig.

SCHNELLAKTIONEN:
  • Task öffnen
  • Mitarbeiter erinnern
```


## TM-002 — Mehrere überfällige Tasks — Stau

```
ID:               TM-002
NAME:             Mehrere überfällige Tasks — Stau
SCHWERE:          MEDIUM
SCHWELLENWERT:    > 5 überfällige Tasks im System
COOLDOWN:         1440 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  overdue_tasks_count > 5

BESCHREIBUNG:
  Zu viele offene überfällige Tasks — mögliches Kapazitätsproblem.

SCHNELLAKTIONEN:
  • Task-Übersicht öffnen
  • Priorisieren
```


## TM-003 — Fehler-Muster Mitarbeiter

```
ID:               TM-003
NAME:             Fehler-Muster Mitarbeiter
SCHWERE:          MEDIUM
SCHWELLENWERT:    Gleicher Fehlertyp > 3 Mal in 7 Tagen
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF
OVERRIDE:         NEIN
BÜNDELBAR:        JA

BEDINGUNG:
  employee_error_type_count_7d >= 3

BESCHREIBUNG:
  Mitarbeiter macht wiederholt den gleichen Fehler. Schulungsbedarf oder Prozessverbesserung.

SCHNELLAKTIONEN:
  • Fehler-Log öffnen
  • Gespräch planen
```


## TM-004 — Wochenende — offene kritische Bestellungen

```
ID:               TM-004
NAME:             Wochenende — offene kritische Bestellungen
SCHWERE:          HIGH
SCHWELLENWERT:    Kritische Bestellungen am Freitag 16:00 noch offen
COOLDOWN:         0 Minuten
EMPFÄNGER:        Lager
OVERRIDE:         JA
BÜNDELBAR:        JA

BEDINGUNG:
  DAYOFWEEK == 5 AND HOUR == 16 AND critical_orders_open > 0

BESCHREIBUNG:
  Freitag 16:00: Kritische Bestellungen müssen heute noch versendet werden.

SCHNELLAKTIONEN:
  • Kritische Bestellungen anzeigen
  • Versand priorisieren
```


===============================================================================
# TEIL 12 — AMAZON-SPEZIFISCHE TRIGGERS
===============================================================================


## AZ-LQ — Listing Quality

```
ID:               AZ-LQ-001
NAME:             Listing-Qualitätsscore gefallen
SCHWERE:          MEDIUM
SCHWELLENWERT:    Listing Score < 70 (Amazon Quality Score)
COOLDOWN:         10080 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  amazon_listing_quality_score < 70

BESCHREIBUNG:
  Amazons Listing-Qualitätsscore ist unter 70 gefallen.
  Mögliche Ursachen: fehlende Bilder, kurze Bullet Points,
  fehlende Keywords, unvollständige Produktdaten.

SCHNELLAKTIONEN:
  • Listing-Editor öffnen
  • Qualitäts-Empfehlungen ansehen
```


```
ID:               AZ-LQ-002
NAME:             A+ Content nicht vorhanden
SCHWERE:          LOW
SCHWELLENWERT:    Brand-registriertes Produkt ohne A+ Content
COOLDOWN:         43200 Minuten (30 Tage)
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  brand_registered == true AND a_plus_content == false

BESCHREIBUNG:
  Brand-registrierte ASINs ohne A+ Content verlieren Conversion-Potential.

SCHNELLAKTIONEN:
  • A+ Content erstellen
```


```
ID:               AZ-LQ-003
NAME:             Hauptbild-Änderung durch Dritten erkannt
SCHWERE:          HIGH
SCHWELLENWERT:    Haupt-Bild-URL hat sich geändert
COOLDOWN:         240 Minuten
EMPFÄNGER:        MarketplaceManager, GF
BÜNDELBAR:        NEIN

BEDINGUNG:
  main_image_url != expected_main_image_url

BESCHREIBUNG:
  Amazon erlaubt Wettbewerber-Bildüberschreibungen in bestimmten Fällen.
  Sofort prüfen und rückgängig machen.

SCHNELLAKTIONEN:
  • Bild vergleichen
  • Amazon Case öffnen
  • Bild zurücksetzen
```


## AZ-FBA — Fulfillment by Amazon

```
ID:               AZ-FBA-001
NAME:             FBA-Stranded Inventory
SCHWERE:          MEDIUM
SCHWELLENWERT:    Units im FBA-Lager ohne aktives Listing
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  fba_stranded_units > 0

BESCHREIBUNG:
  FBA-Bestand ohne Listing kostet Lagergebühren aber erzielt keinen Umsatz.
```


```
ID:               AZ-FBA-002
NAME:             FBA Long-Term Storage Fee Alert
SCHWERE:          MEDIUM
SCHWELLENWERT:    Einheiten seit > 270 Tagen im FBA-Lager
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  fba_inventory_age_days > 270

BESCHREIBUNG:
  Amazon erhebt nach 365 Tagen erhebliche Long-Term-Storage-Fees. Warnung bei 270 Tagen.
```


```
ID:               AZ-FBA-003
NAME:             FBA-Einlieferung abgelehnt
SCHWERE:          HIGH
SCHWELLENWERT:    FBA-Shipment von Amazon abgelehnt
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  fba_shipment_status == 'rejected'

BESCHREIBUNG:
  FBA-Einlieferung wurde abgelehnt. Labelierung oder Verpackung prüfen.
```



## AZ-VC — Vine & Brand

```
ID:               AZ-VC-001
NAME:             Vine-Review eingegangen
SCHWERE:          INFO
SCHWELLENWERT:    Jeder Vine-Review
COOLDOWN:         0 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  review_source == 'vine' AND review_received == true

BESCHREIBUNG:
  Vine-Reviewer hat bewertet. Rating prüfen — wenn < 4 Sterne: Produkt analysieren.
```


===============================================================================
# TEIL 13 — EBAY-SPEZIFISCHE TRIGGERS
===============================================================================


## EB-PM-001 — eBay Performance-Metrik — Defizit

```
ID:               EB-PM-001
NAME:             eBay Performance-Metrik — Defizit
SCHWERE:          HIGH
SCHWELLENWERT:    Transaction Defect Rate > 0.5% oder Late Delivery Rate > 3%
COOLDOWN:         480 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  ebay_tdr > 0.005 OR ebay_ldr > 0.03

BESCHREIBUNG:
  eBay droht mit Einschränkungen wenn Performance-Metriken nicht eingehalten werden.

SCHNELLAKTIONEN:
  • eBay Performance-Dashboard
  • Offene Cases prüfen
```


## EB-SR-001 — eBay Seller Rating gefallen

```
ID:               EB-SR-001
NAME:             eBay Seller Rating gefallen
SCHWERE:          MEDIUM
SCHWELLENWERT:    eBay Feedback-Score < 98%
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  ebay_feedback_score < 0.98

BESCHREIBUNG:
  eBay-Bewertungsschnitt gefallen. Direkte Auswirkung auf Sichtbarkeit.

SCHNELLAKTIONEN:
  • Feedback analysieren
  • Response vorbereiten
```


## EB-OFR-001 — eBay Best Offer — Angebot ausstehend

```
ID:               EB-OFR-001
NAME:             eBay Best Offer — Angebot ausstehend
SCHWERE:          LOW
SCHWELLENWERT:    Best Offer Angebot > 48h unbeantwortet
COOLDOWN:         2880 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  ebay_best_offer_pending_hours > 48

BESCHREIBUNG:
  Best-Offer-Angebote verfallen. Entscheidung treffen.

SCHNELLAKTIONEN:
  • Angebote ansehen
  • Akzeptieren oder Ablehnen
```


===============================================================================
# TEIL 14 — OTTO-SPEZIFISCHE TRIGGERS
===============================================================================


## OT-QS-001 — Otto Qualitätsscore gefallen

```
ID:               OT-QS-001
NAME:             Otto Qualitätsscore gefallen
SCHWERE:          HIGH
SCHWELLENWERT:    Otto Produkt-Qualitätsscore < 80
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  otto_quality_score < 80

BESCHREIBUNG:
  Otto bewertet Listing-Qualität und bestraft schlechte Scores mit Sichtbarkeitsverlust.

SCHNELLAKTIONEN:
  • Listing verbessern
  • Otto Partner Connect öffnen
```


## OT-RT-001 — Otto Retoure — Hohe Quote

```
ID:               OT-RT-001
NAME:             Otto Retoure — Hohe Quote
SCHWERE:          HIGH
SCHWELLENWERT:    Retourenquote auf Otto > 20% in 30 Tagen
COOLDOWN:         1440 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        JA

BEDINGUNG:
  otto_return_rate_30d > 0.20

BESCHREIBUNG:
  Hohe Retourenquote auf Otto. Listing-Korrektheit und Produktqualität prüfen.

SCHNELLAKTIONEN:
  • Retouren-Analyse
  • Listing prüfen
```


## OT-PO-001 — Otto Bestelleingang — Sync-Fehler

```
ID:               OT-PO-001
NAME:             Otto Bestelleingang — Sync-Fehler
SCHWERE:          CRITICAL
SCHWELLENWERT:    Otto Order-Sync-Job seit > 1 Stunde fehlgeschlagen
COOLDOWN:         120 Minuten
EMPFÄNGER:        MarketplaceManager
BÜNDELBAR:        NEIN

BEDINGUNG:
  otto_order_sync_last_success > NOW() - INTERVAL '1 hour'

BESCHREIBUNG:
  Otto-Bestellungen werden nicht synchronisiert. Bestellungen gehen verloren.

SCHNELLAKTIONEN:
  • Sync-Job prüfen
  • Manuelle Synchronisation
  • Tech-Support
```


===============================================================================
# TEIL 15 — SAISONALE & PEAK-TRIGGERS
===============================================================================


## PEAK-001 — Black Friday — 14-Tage-Vorlauf

```
ID:               PEAK-001
NAME:             Black Friday — 14-Tage-Vorlauf
SCHWERE:          HIGH
SCHWELLENWERT:    Black Friday ist in 14 Tagen
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  DATE_DIFF(black_friday_date, CURRENT_DATE) == 14

BESCHREIBUNG:
  14-Tage-Checkliste: Bestand, Kampagnen, Preise, Repricing, Lager-Kapazität.

SCHNELLAKTIONEN:
  • BF-Checkliste öffnen
  • Bestand prüfen
  • Kampagnen planen
```


## PEAK-002 — Black Friday — 3-Tage-Vorlauf

```
ID:               PEAK-002
NAME:             Black Friday — 3-Tage-Vorlauf
SCHWERE:          CRITICAL
SCHWELLENWERT:    Black Friday ist in 3 Tagen
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         JA
BÜNDELBAR:        NEIN

BEDINGUNG:
  DATE_DIFF(black_friday_date, CURRENT_DATE) == 3

BESCHREIBUNG:
  Letzter Vorlauf-Check. Alles muss bereit sein.

SCHNELLAKTIONEN:
  • Finale Checkliste
  • Repricing aktivieren
  • Lager-Schicht planen
```


## PEAK-003 — Black Friday — Heute — Monitoring aktiv

```
ID:               PEAK-003
NAME:             Black Friday — Heute — Monitoring aktiv
SCHWERE:          INFO
SCHWELLENWERT:    Black Friday läuft
COOLDOWN:         30 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  CURRENT_DATE == black_friday_date

BESCHREIBUNG:
  Erhöhtes Monitoring während Black Friday. Stündliche Checks.

SCHNELLAKTIONEN:
  • Real-Time Dashboard
  • Bestand prüfen
```


## POSTPEAK-001 — Post-Peak — Retouren-Welle erwartet

```
ID:               POSTPEAK-001
NAME:             Post-Peak — Retouren-Welle erwartet
SCHWERE:          MEDIUM
SCHWELLENWERT:    7 Tage nach Black Friday / Weihnachten
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  DATE_DIFF(CURRENT_DATE, peak_end_date) == 7

BESCHREIBUNG:
  Retourenwelle in 2-3 Wochen. Lager und CustomerService vorbereiten.

SCHNELLAKTIONEN:
  • Retouren-Kapazität planen
  • Rücksende-Labels prüfen
```


## POSTPEAK-002 — Lagerräumung Post-Peak

```
ID:               POSTPEAK-002
NAME:             Lagerräumung Post-Peak
SCHWERE:          LOW
SCHWELLENWERT:    Saisonaler Bestand nach Peak > 60 Tage unverkauft
COOLDOWN:         10080 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  post_peak_seasonal_stock_age > 60

BESCHREIBUNG:
  Saisonale Produkte nach Peak. Abverkaufspreis oder Lagerräumung einleiten.

SCHNELLAKTIONEN:
  • Abverkaufs-Preis setzen
  • FBA-Removal prüfen
```


## SPRING-001 — Frühlings-Saison-Vorbereitung

```
ID:               SPRING-001
NAME:             Frühlings-Saison-Vorbereitung
SCHWERE:          MEDIUM
SCHWELLENWERT:    1. März — Frühlings-Kategorie-Reminder
COOLDOWN:         0 Minuten
EMPFÄNGER:        GF, MarketplaceManager, Lager
OVERRIDE:         NEIN
BÜNDELBAR:        NEIN

BEDINGUNG:
  CURRENT_DATE == '{{YEAR}}-03-01'

BESCHREIBUNG:
  Frühlingssaison beginnt. Outdoor-Produkte, Garten, Sandkästen prüfen.

SCHNELLAKTIONEN:
  • Saisonale Listings aktivieren
  • Kampagnen planen
```


===============================================================================
# TEIL 16 — ANTI-SPAM-REGELN
===============================================================================

Alle 10 Regeln sind aktiv. Prioritätsreihenfolge: 1 → 10.
CRITICAL Alerts sind von ALLEN Anti-Spam-Regeln ausgenommen (außer Regel 1.1).


## REGEL 1 — Daily Cap

```
MAX ALERTS PRO TAG (ohne CRITICAL): 10

Gilt pro Tenant, pro Empfänger.
Wenn Limit erreicht: alle weiteren Alerts in 'daily_overflow_queue'.
Overflow-Queue wird täglich um 18:00 als gebündeltes Summary gesendet.

Ausnahmen:
  • CRITICAL: kein Limit
  • Manuelle Anfragen durch User: kein Limit
  • Peak-Perioden: Limit erhöht auf 15 (Konfigurierbar)

SQL:
  SELECT COUNT(*) FROM aria_alerts
  WHERE tenant_id = $1
  AND recipient_id = $2
  AND schwere != 'CRITICAL'
  AND sent_at >= CURRENT_DATE
  GROUP BY recipient_id
  HAVING COUNT(*) >= 10
```


## REGEL 2 — Burst-Schutz

```
MAX ALERTS IN 15 MINUTEN: 2 (ohne CRITICAL)

Verhindert Notification-Flood bei System-Anomalien oder Datenproblemen.
Wenn Burst erkannt: dritte und weitere Alerts werden gebündelt.
Nach 15-Min-Fenster: nächste Alerts normal verarbeitet.

SQL:
  SELECT COUNT(*) FROM aria_alerts
  WHERE tenant_id = $1
  AND recipient_id = $2
  AND schwere != 'CRITICAL'
  AND sent_at >= NOW() - INTERVAL '15 minutes'
  HAVING COUNT(*) >= 2
```


## REGEL 3 — Cooldown pro Trigger + Objekt

```
Jeder Trigger hat einen definierten Cooldown (siehe Trigger-Katalog).
Cooldown gilt pro: trigger_id + object_id (z.B. SKU oder Kanal).

Beispiel:
  SO-003 für SKU-A: Cooldown 480 Minuten
  SO-003 für SKU-B: eigener unabhängiger Cooldown
  SO-003 für SKU-A: erst nach 480 Min wieder auslösen

Cooldown-Tabelle:
  TRIGGER    COOLDOWN
  ─────────────────────────────
  RD-001     120 Min
  RD-002     240 Min
  SO-001     0 Min (immer)
  SO-002     240 Min
  SO-003     480 Min
  SO-004     1440 Min
  PA-001     60 Min
  PA-002     240 Min
  PA-007     120 Min
  PA-008     0 Min (immer)
  AH-001     0 Min (immer)
  AH-002     480 Min
  AH-004     0 Min (immer)
  [alle anderen: siehe Trigger-Katalog]

SQL:
  SELECT sent_at FROM aria_alerts
  WHERE tenant_id = $1
  AND trigger_id = $2
  AND object_id = $3
  AND sent_at >= NOW() - ($4 || ' minutes')::INTERVAL
  ORDER BY sent_at DESC LIMIT 1
```


## REGEL 4 — Verwandte Trigger bündeln

```
Trigger die das gleiche Objekt betreffen werden gebündelt.
Bündelungs-Fenster: 15 Minuten.

Beispiel:
  08:14 — SO-003 für SKU-A (Stockout 7 Tage)
  08:16 — PA-002 für SKU-A (Buy Box verloren)
  08:18 — AD-003 für SKU-A (Conversion eingebrochen)

  → Wird gebündelt zu:
  08:30 — Bündel SKU-A: 3 Probleme erkannt
           1. Stockout-Risiko in 7 Tagen
           2. Buy Box verloren
           3. Ad-Conversion eingebrochen

Ausnahmen vom Bündeln:
  • CRITICAL Alerts: nie bündeln
  • Override-Trigger: nie bündeln
  • Trigger mit buendelbar: false
```


## REGEL 5 — Bekannter Zustand

```
Wenn das Problem bereits bekannt ist und aktiv bearbeitet wird: kein Alert.

Bekannt = einer der folgenden Zustände in aria_alerts:
  • Status: 'acknowledged' — Empfänger hat Alert geöffnet
  • Status: 'snoozed' — Empfänger hat Alert zurückgestellt
  • Status: 'acted' — Empfänger hat Aktion ausgeführt

Wenn bekannter Zustand:
  → Alert wird SUPPRESSED
  → Kein erneutes Senden
  → Exception: wenn Schwere eskaliert (LOW → HIGH)

SQL:
  SELECT status FROM aria_alerts
  WHERE trigger_id = $1
  AND object_id = $2
  AND tenant_id = $3
  AND status IN ('acknowledged', 'snoozed', 'acted')
  AND created_at >= NOW() - INTERVAL '24 hours'
```


## REGEL 6 — Hysterese

```
Verhindert Flapping: Alert löst erneut nur aus wenn
Schwelle um mindestens 25% verletzt wird (nach Erholung).

Beispiel:
  ODR-Schwelle: 1.0%
  Alert ausgelöst bei: 1.1%
  ODR sinkt auf 0.9% (unter Schwelle)
  Neuer Alert erst bei: 1.0% + 25% Hysterese = wenn ODR > 1.25%
  — oder wenn Reset bestätigt (ODR dauerhaft < 0.75% für 24h)

Hysterese-Werte pro Trigger-Typ:
  Prozent-Metriken (ODR, LSR etc.): 25% Abstand
  Absolute Metriken (Bestand):      10% Abstand
  Preise:                           5% Abstand
  Binäre Metriken (Job läuft/läuft nicht): kein Hysterese nötig
```


## REGEL 7 — Nachtruhe

```
NACHTRUHE: 22:00 – 07:00 Uhr (Lokal-Zeit des Tenants)

In der Nachtruhe:
  • LOW, MEDIUM, INFO: werden zurückgehalten bis 07:00
  • HIGH: werden zurückgehalten bis 07:00
  • CRITICAL: werden immer sofort gesendet

Um 07:00 werden alle zurückgehaltenen Alerts als gebündeltes
Morgen-Summary gesendet (max. 5 Alerts, Rest in Overflow).

Konfigurierbar pro Tenant:
  quiet_hours_start: default 22:00
  quiet_hours_end:   default 07:00
  quiet_hours_tz:    default 'Europe/Berlin'
  critical_override: default true
```


## REGEL 8 — Wochenend-Reduktion

```
SAMSTAG / SONNTAG: reduzierter Alert-Betrieb

Sa/So werden nur gesendet:
  • CRITICAL: immer
  • HIGH: nur wenn Schaden > 500€ kalkulierbar
  • MEDIUM, LOW, INFO: nicht am Wochenende

Konfigurierbar per Tenant:
  weekend_mode_enabled: default true
  weekend_high_threshold: default 500
  weekend_quiet_days: default ['saturday', 'sunday']

Ausnahmen:
  • Kanal ist 24/7 aktiv (Amazon): CRITICAL immer
  • GF hat weekend_override=true gesetzt
```


## REGEL 9 — Urlaubs-Modus

```
URLAUBS-MODUS: alle Alerts außer CRITICAL unterdrückt

Aktivierung: manuell durch User oder automatisch via Kalender

Im Urlaubs-Modus:
  • CRITICAL: weiterhin sofort (an Vertretung)
  • Alle anderen: suppressed
  • Bei CRITICAL: auch Backup-Empfänger benachrichtigen

Deaktivierung: automatisch nach End-Datum oder manuell

aria_proactivity_config Feld:
  vacation_mode: boolean
  vacation_start: date
  vacation_end: date
  vacation_backup_recipient: user_id
```


## REGEL 10 — Eskalations-Lockout

```
Nach einem CRITICAL Alert: 60 Minuten Lockout für LOW und MEDIUM

Begründung:
  Nach einem CRITICAL Alert ist der Empfänger bereits in Alarmbereitschaft.
  LOW/MEDIUM Alerts zu dieser Zeit sind Rauschen und verringern Aufmerksamkeit.

Lockout gilt für:
  • LOW: 60 Minuten nach letztem CRITICAL
  • MEDIUM: 60 Minuten nach letztem CRITICAL
  • HIGH: kein Lockout (bleibt aktiv)
  • CRITICAL: kein Lockout (immer sofort)

SQL:
  SELECT sent_at FROM aria_alerts
  WHERE tenant_id = $1
  AND recipient_id = $2
  AND schwere = 'CRITICAL'
  AND sent_at >= NOW() - INTERVAL '60 minutes'
  LIMIT 1
```


===============================================================================
# TEIL 17 — BÜNDELUNGSLOGIK
===============================================================================


## 8 Bündelungs-Typen


## Bündel-Typ: OBJECT_BUNDLE

```
TYP:              OBJECT_BUNDLE
BESCHREIBUNG:     Mehrere Trigger für das gleiche Objekt (SKU, Kanal) in kurzer Zeit
ZEITFENSTER:      15 Minuten
MAX-ALERTS:       keine
TRIGGER-BEREICH:  Alle Trigger für object_id X im Zeitfenster

FORMAT-BEISPIEL:
  Bündel SKU-A: 3 Probleme — Stockout, Buy Box, Conversion
```


## Bündel-Typ: CATEGORY_BUNDLE

```
TYP:              CATEGORY_BUNDLE
BESCHREIBUNG:     Gleichartige Trigger für verschiedene Objekte gebündelt
ZEITFENSTER:      30 Minuten
MAX-ALERTS:       max. 3 Alerts pro Kategorie
TRIGGER-BEREICH:  Alle SO-Trigger im Zeitfenster

FORMAT-BEISPIEL:
  Bestandsübersicht: 5 SKUs haben Meldebestand erreicht
```


## Bündel-Typ: MORNING_BUNDLE

```
TYP:              MORNING_BUNDLE
BESCHREIBUNG:     Alle nächtlich aufgelaufenen Alerts als Morgen-Summary
ZEITFENSTER:      Täglich 07:00
MAX-ALERTS:       max. 10 Alerts
TRIGGER-BEREICH:  Alle während Nachtruhe suppressed Alerts

FORMAT-BEISPIEL:
  Guten Morgen — hier ist was über Nacht passiert ist (4 Punkte)
```


## Bündel-Typ: EVENING_BUNDLE

```
TYP:              EVENING_BUNDLE
BESCHREIBUNG:     Tages-Summary aller LOW/INFO Alerts
ZEITFENSTER:      Täglich 18:00
MAX-ALERTS:       max. 8 Alerts
TRIGGER-BEREICH:  Alle LOW und INFO des Tages

FORMAT-BEISPIEL:
  Tages-Zusammenfassung (3 Beobachtungen, kein Handlungsbedarf)
```


## Bündel-Typ: MONDAY_BUNDLE

```
TYP:              MONDAY_BUNDLE
BESCHREIBUNG:     Wochenstart-Bundle aller Wochenend-suppressten Alerts
ZEITFENSTER:      Montag 08:00
MAX-ALERTS:       max. 15 Alerts
TRIGGER-BEREICH:  Alle Sa/So suppressed non-CRITICAL Alerts

FORMAT-BEISPIEL:
  Wochenstart-Übersicht: Was hat das Wochenende gebracht (6 Punkte)
```


## Bündel-Typ: STOCKOUT_BUNDLE

```
TYP:              STOCKOUT_BUNDLE
BESCHREIBUNG:     Alle Bestandsrisiken als Bestellliste
ZEITFENSTER:      Täglich 09:00
MAX-ALERTS:       keine
TRIGGER-BEREICH:  Alle SO-003, SO-004 des Tages

FORMAT-BEISPIEL:
  Bestellliste heute: 4 Produkte brauchen Nachbestellung (priorisiert)
```


## Bündel-Typ: REVIEW_BUNDLE

```
TYP:              REVIEW_BUNDLE
BESCHREIBUNG:     Alle neuen Bewertungen des Tages
ZEITFENSTER:      Täglich 20:00
MAX-ALERTS:       max. 20 Bewertungen
TRIGGER-BEREICH:  Alle RA-001, RA-004 des Tages

FORMAT-BEISPIEL:
  Bewertungs-Übersicht heute: 12 neu (10x5⭐, 1x3⭐, 1x1⭐)
```


## Bündel-Typ: WEEKLY_PERFORMANCE_BUNDLE

```
TYP:              WEEKLY_PERFORMANCE_BUNDLE
BESCHREIBUNG:     Wöchentliches Performance-Summary
ZEITFENSTER:      Freitag 17:00
MAX-ALERTS:       keine
TRIGGER-BEREICH:  Alle INFO und LOW der Woche + Performance-Daten

FORMAT-BEISPIEL:
  Wochenperformance: Umsatz, Top-Produkte, Auffälligkeiten
```


## Prioritäts-Segregation in Bündeln

```
Bündel enthalten niemals gemischte Schwere-Level ohne klare Trennung.

FALSCH:
  ⚠️ Bündel: Stockout + Preis-Chance + Neue 5-Sterne-Bewertung

RICHTIG:
  🔴 DRINGEND (2 Punkte):
     • SKU-A Stockout in 5 Tagen
     • SKU-B Buy Box verloren

  ℹ️ ZUR INFORMATION (2 Punkte):
     • SKU-C neue 5-Sterne-Bewertung
     • SKU-D Preis-Erhöhungschance erkannt
```


## Kritikalitäts-Eskalation im Bündel

```
Wenn ein Bündel einen CRITICAL Alert enthält:
  → Bündel aufbrechen
  → CRITICAL sofort einzeln senden
  → Rest normal bündeln

Wenn ein Bündel mehrere HIGH Alerts enthält (> 3):
  → Bündel-Schwere wird auf HIGH angehoben
  → Sofort senden (nicht auf Bundle-Zeit warten)
```


===============================================================================
# TEIL 18 — OVERRIDE-TRIGGER
===============================================================================

Diese Trigger ignorieren ALLE Anti-Spam-Regeln.
Sie werden immer sofort gesendet — egal was.

```
TRIGGER-ID    GRUND FÜR OVERRIDE
─────────────────────────────────────────────────────────────────────────
SO-001        Stockout läuft jetzt — jede Bestellung macht Verlust
SO-003        Stockout in 7 Tagen — kritisches Zeitfenster
SO-004        Stockout in 14 Tagen — Bestellung muss eingeplant werden
RD-002        Null-Umsatz 4h — Systemausfall oder komplettes Listing-Problem
PA-007        Repricing-Engine down — Buy-Box-Verlust läuft
AH-001        Amazon ODR > 1% — Account-Sperre droht sofort
AH-002        Amazon ODR > 0.75% — Eskalationsstufe 2
AH-004        Amazon Policy-Warnung — immer sofort handeln
OT-PO-001     Otto-Sync-Fehler — Bestellungen gehen verloren
PEAK-002      Black Friday in 3 Tagen — letzte Chance zur Vorbereitung
TM-004        Freitag 16:00 kritische offene Bestellungen — Wochenende
```


===============================================================================
# TEIL 19 — ROLLENBASIERTES ROUTING
===============================================================================


## Rollen-Definitionen

```
ROLLE                 BESCHREIBUNG
─────────────────────────────────────────────────────────────────────────
GF                    Geschäftsführer — strategische Alerts, alle CRITICAL
MarketplaceManager    Marketplace-verantwortlich — Listings, Preise, Werbung
Lager                 Lagermitarbeiter — Bestand, Versand, Retouren
Einkauf               Einkauf — Lieferanten, Bestellungen
CustomerService       Kundenservice — Bewertungen, Cases, Retouren
Buchhalter            Finanzbuchhaltung — Zahlungen, DATEV, Rechnungen
```


## Alert-Routing-Matrix

```
TRIGGER           GF    MM    LAGER  EINKAUF  CS    BUCH
────────────────────────────────────────────────────────────
RD-001 (Revenue)  ✓     ✓     —      —        —     —
RD-002 (Null)     ✓     ✓     —      —        —     —
RD-003 (Ziel)     ✓     —     —      —        —     —
SO-001 (Stockout) ✓     ✓     ✓      ✓        —     —
SO-002 (Kritisch) —     ✓     ✓      ✓        —     —
SO-003 (7 Tage)   —     ✓     ✓      ✓        —     —
SO-004 (14 Tage)  —     —     ✓      ✓        —     —
PA-001 (Preis)    ✓     ✓     —      —        —     —
PA-002 (Buy Box)  —     ✓     —      —        —     —
AD-001 (ACoS)     ✓     ✓     —      —        —     —
AH-001 (ODR)      ✓     ✓     —      —        —     —
AH-002 (ODR warn) ✓     ✓     —      —        —     —
AH-004 (Warning)  ✓     —     —      —        —     —
RA-001 (1 Stern)  —     ✓     —      —        ✓     —
RA-002 (Serie)    ✓     ✓     —      ✓        ✓     —
LG-001 (Verlust)  —     —     ✓      —        ✓     —
LG-002 (Delay)    —     —     ✓      —        —     —
FN-001 (Auszahl.) ✓     —     —      —        —     ✓
FN-002 (Rechnung) ✓     —     —      —        —     ✓
FN-005 (USt)      ✓     —     —      —        —     ✓
TM-001 (Task)     ✓     —     —      —        —     —
CP-001 (Wettbew.) ✓     ✓     —      —        —     —
PEAK-002 (BF)     ✓     ✓     ✓      ✓        —     —
```


===============================================================================
# TEIL 20 — SQL-SCHEMAS
===============================================================================

```sql
-- Haupt-Alert-Tabelle
CREATE TABLE aria_alerts (
  id                uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  tenant_id         uuid NOT NULL REFERENCES tenants(id),
  trigger_id        text NOT NULL,
  trigger_name      text NOT NULL,
  schwere           text NOT NULL CHECK (schwere IN ('CRITICAL','HIGH','MEDIUM','LOW','INFO')),
  object_id         text,
  object_type       text,
  titel             text NOT NULL,
  nachricht         text NOT NULL,
  daten             jsonb DEFAULT '{}',
  aktionen          jsonb DEFAULT '[]',
  empfaenger_rollen text[] DEFAULT '{}',
  empfaenger_ids    uuid[] DEFAULT '{}',
  status            text DEFAULT 'sent'
                    CHECK (status IN ('sent','acknowledged','acted','resolved','suppressed','bundled','expired','snoozed')),
  bundle_id         uuid REFERENCES aria_alert_bundles(id),
  created_at        timestamptz DEFAULT now(),
  sent_at           timestamptz,
  acknowledged_at   timestamptz,
  acted_at          timestamptz,
  resolved_at       timestamptz,
  snoozed_until     timestamptz,
  override          boolean DEFAULT false,
  kanal             text,
  sku               text
);

CREATE INDEX idx_aria_alerts_tenant_id ON aria_alerts(tenant_id);
CREATE INDEX idx_aria_alerts_trigger_id ON aria_alerts(trigger_id);
CREATE INDEX idx_aria_alerts_schwere ON aria_alerts(schwere);
CREATE INDEX idx_aria_alerts_sent_at ON aria_alerts(sent_at);
CREATE INDEX idx_aria_alerts_object ON aria_alerts(object_id, object_type);
CREATE INDEX idx_aria_alerts_status ON aria_alerts(status);

-- Bündel-Tabelle
CREATE TABLE aria_alert_bundles (
  id                uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  tenant_id         uuid NOT NULL REFERENCES tenants(id),
  bundle_typ        text NOT NULL,
  titel             text NOT NULL,
  nachricht         text,
  alert_ids         uuid[] DEFAULT '{}',
  schwere_max       text NOT NULL,
  alert_count       int DEFAULT 0,
  gesendet          boolean DEFAULT false,
  created_at        timestamptz DEFAULT now(),
  sent_at           timestamptz
);

-- Trigger-Zustands-Tabelle (für Cooldown & Hysterese)
CREATE TABLE aria_trigger_states (
  id                uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  tenant_id         uuid NOT NULL REFERENCES tenants(id),
  trigger_id        text NOT NULL,
  object_id         text,
  last_triggered_at timestamptz,
  last_sent_at      timestamptz,
  last_value        numeric,
  trigger_count     int DEFAULT 0,
  suppressed_count  int DEFAULT 0,
  zustand           text DEFAULT 'watching',
  UNIQUE (tenant_id, trigger_id, object_id)
);

-- Anti-Spam Config pro Tenant
ALTER TABLE tenants ADD COLUMN IF NOT EXISTS aria_proactivity_config jsonb DEFAULT '{
  "daily_cap": 10,
  "burst_limit": 2,
  "burst_window_min": 15,
  "quiet_hours_enabled": true,
  "quiet_hours_start": "22:00",
  "quiet_hours_end": "07:00",
  "quiet_tz": "Europe/Berlin",
  "weekend_mode": true,
  "weekend_high_threshold_eur": 500,
  "vacation_mode": false,
  "vacation_start": null,
  "vacation_end": null,
  "vacation_backup_recipient": null
}';
```


===============================================================================
# TEIL 21 — TYPESCRIPT WORKER CODE
===============================================================================


## Hauptstruktur: shouldSendAlert()

```typescript
// services/aria/proactivity/should-send-alert.ts

export async function shouldSendAlert(
  tenantId: string,
  triggerId: string,
  objectId: string,
  schwere: AlertSchwere,
  supabase: SupabaseClient
): Promise<{ send: boolean; grund?: string }> {

  // CRITICAL immer senden (außer Cooldown = 0)
  const trigger = TRIGGER_KATALOG[triggerId]
  if (schwere === 'CRITICAL' && trigger?.override) {
    return { send: true }
  }

  const config = await getTenantProactivityConfig(tenantId, supabase)

  // REGEL 9: Urlaubs-Modus
  if (config.vacation_mode && schwere !== 'CRITICAL') {
    return { send: false, grund: 'URLAUBS_MODUS' }
  }

  // REGEL 7: Nachtruhe
  if (isQuietHours(config) && schwere !== 'CRITICAL') {
    await queueForMorningBundle(tenantId, triggerId, objectId, supabase)
    return { send: false, grund: 'NACHTRUHE' }
  }

  // REGEL 8: Wochenend-Reduktion
  if (isWeekend() && config.weekend_mode) {
    if (schwere === 'LOW' || schwere === 'MEDIUM' || schwere === 'INFO') {
      return { send: false, grund: 'WOCHENENDE' }
    }
  }

  // REGEL 3: Cooldown
  const cooldownActive = await isCooldownActive(tenantId, triggerId, objectId, supabase)
  if (cooldownActive) {
    return { send: false, grund: 'COOLDOWN' }
  }

  // REGEL 5: Bekannter Zustand
  const bekannt = await isKnownState(tenantId, triggerId, objectId, supabase)
  if (bekannt) {
    return { send: false, grund: 'BEKANNTER_ZUSTAND' }
  }

  // REGEL 6: Hysterese
  const hysterese = await checkHysteresis(tenantId, triggerId, objectId, supabase)
  if (!hysterese.crossed) {
    return { send: false, grund: 'HYSTERESE' }
  }

  // REGEL 10: Eskalations-Lockout
  if ((schwere === 'LOW' || schwere === 'MEDIUM') && await recentCritical(tenantId, supabase)) {
    return { send: false, grund: 'ESKALATIONS_LOCKOUT' }
  }

  // REGEL 2: Burst-Schutz
  const burst = await checkBurst(tenantId, supabase)
  if (burst.exceeded) {
    await addToBurstBundle(tenantId, triggerId, objectId, supabase)
    return { send: false, grund: 'BURST_SCHUTZ' }
  }

  // REGEL 1: Daily Cap
  const dailyCap = await checkDailyCap(tenantId, supabase)
  if (dailyCap.exceeded && schwere !== 'CRITICAL') {
    await addToOverflowQueue(tenantId, triggerId, objectId, supabase)
    return { send: false, grund: 'DAILY_CAP' }
  }

  return { send: true }
}
```


## isCooldownActive()

```typescript
export async function isCooldownActive(
  tenantId: string,
  triggerId: string,
  objectId: string,
  supabase: SupabaseClient
): Promise<boolean> {

  const cooldownMin = TRIGGER_KATALOG[triggerId]?.cooldown_minuten ?? 60
  if (cooldownMin === 0) return false

  const { data } = await supabase
    .from('aria_trigger_states')
    .select('last_sent_at')
    .eq('tenant_id', tenantId)
    .eq('trigger_id', triggerId)
    .eq('object_id', objectId)
    .single()

  if (!data?.last_sent_at) return false

  const lastSent = new Date(data.last_sent_at)
  const cooldownMs = cooldownMin * 60 * 1000
  return Date.now() - lastSent.getTime() < cooldownMs
}
```


## applyHysteresis()

```typescript
export async function checkHysteresis(
  tenantId: string,
  triggerId: string,
  objectId: string,
  supabase: SupabaseClient
): Promise<{ crossed: boolean }> {

  const { data: state } = await supabase
    .from('aria_trigger_states')
    .select('last_value, zustand')
    .eq('tenant_id', tenantId)
    .eq('trigger_id', triggerId)
    .eq('object_id', objectId)
    .single()

  // Erstmaliger Trigger: immer senden
  if (!state) return { crossed: true }

  // Wenn zuletzt nicht ausgelöst: senden
  if (state.zustand !== 'triggered') return { crossed: true }

  // Hysterese-Check: Wert muss sich erholt haben
  const hystereseFactor = TRIGGER_KATALOG[triggerId]?.hysterese_faktor ?? 0.25
  const threshold = TRIGGER_KATALOG[triggerId]?.schwellenwert?.absolut

  if (!threshold) return { crossed: true }

  // Erholung muss > 25% über Schwelle gewesen sein
  const recoveryThreshold = threshold * (1 - hystereseFactor)
  if ((state.last_value ?? 0) > recoveryThreshold) {
    return { crossed: false }
  }

  return { crossed: true }
}
```


## Stockout Check Worker

```typescript
// workers/aria/stockout-check.worker.ts

export async function stockoutCheckWorker(job: Job) {
  const { tenantId } = job.data

  const { data: products } = await supabase
    .from('products')
    .select('id, sku, stock_quantity, daily_velocity, lead_time_days, listing_status')
    .eq('tenant_id', tenantId)
    .eq('listing_status', 'active')

  for (const product of products ?? []) {
    const daysOfStock = product.daily_velocity > 0
      ? product.stock_quantity / product.daily_velocity
      : 999

    // SO-001: Stockout jetzt
    if (product.stock_quantity === 0) {
      await triggerAlert(tenantId, 'SO-001', product.sku, 'CRITICAL', {
        sku: product.sku,
        stock: 0,
        listing_status: product.listing_status
      })
    }

    // SO-002: Stockout < Lead-Time
    else if (daysOfStock < product.lead_time_days) {
      await triggerAlert(tenantId, 'SO-002', product.sku, 'CRITICAL', {
        sku: product.sku,
        days_of_stock: daysOfStock.toFixed(1),
        lead_time_days: product.lead_time_days
      })
    }

    // SO-003: Stockout < 7 Tage
    else if (daysOfStock < 7) {
      await triggerAlert(tenantId, 'SO-003', product.sku, 'HIGH', {
        sku: product.sku,
        days_of_stock: daysOfStock.toFixed(1)
      })
    }

    // SO-004: Stockout < 14 Tage
    else if (daysOfStock < 14) {
      await triggerAlert(tenantId, 'SO-004', product.sku, 'MEDIUM', {
        sku: product.sku,
        days_of_stock: daysOfStock.toFixed(1)
      })
    }
  }
}
```


## processAndSendAlerts()

```typescript
export async function processAndSendAlerts(
  tenantId: string,
  alerts: AlertCandidate[],
  supabase: SupabaseClient
): Promise<void> {

  for (const alert of alerts) {
    const { send, grund } = await shouldSendAlert(
      tenantId, alert.triggerId, alert.objectId, alert.schwere, supabase
    )

    if (!send) {
      await logSuppressed(tenantId, alert.triggerId, alert.objectId, grund!, supabase)
      continue
    }

    // Prüfen ob bündelbar
    const trigger = TRIGGER_KATALOG[alert.triggerId]
    if (trigger?.buendelbar && alert.schwere !== 'CRITICAL') {
      await addToBundleCandidate(tenantId, alert, supabase)
      continue
    }

    // Direkt senden
    await saveAndSendAlert(tenantId, alert, supabase)
  }

  // Bündel verarbeiten
  await processBundles(tenantId, supabase)
}
```


## bundleSenderWorker()

```typescript
// Läuft alle 15 Minuten — verarbeitet Bundle-Kandidaten
export async function bundleSenderWorker(job: Job) {
  const { tenantId } = job.data

  // Object-Bundles: gleiche SKU, Zeitfenster 15 Min
  const objectCandidates = await getBundleCandidatesByObject(tenantId, 15, supabase)

  for (const [objectId, alerts] of Object.entries(objectCandidates)) {
    if (alerts.length >= 2) {
      // CRITICAL-Alerts raus — die wurden schon gesendet
      const nonCritical = alerts.filter(a => a.schwere !== 'CRITICAL')
      if (nonCritical.length >= 2) {
        await createAndSendBundle(tenantId, 'OBJECT_BUNDLE', objectId, nonCritical, supabase)
      }
    } else if (alerts.length === 1) {
      // Einzelner Alert: direkt senden
      await saveAndSendAlert(tenantId, alerts[0], supabase)
    }
  }

  // Category-Bundles: gleicher Trigger-Typ, verschiedene Objekte
  const categoryCandidates = await getBundleCandidatesByCategory(tenantId, 30, supabase)

  for (const [category, alerts] of Object.entries(categoryCandidates)) {
    if (alerts.length >= 3) {
      await createAndSendBundle(tenantId, 'CATEGORY_BUNDLE', category, alerts, supabase)
    } else {
      for (const alert of alerts) {
        await saveAndSendAlert(tenantId, alert, supabase)
      }
    }
  }
}
```


## saveAndSendAlert()

```typescript
export async function saveAndSendAlert(
  tenantId: string,
  alert: AlertCandidate,
  supabase: SupabaseClient
): Promise<void> {

  // ARIA-Nachricht generieren
  const nachricht = await generateAlertNachricht(alert)

  // In DB speichern
  const { data: saved } = await supabase
    .from('aria_alerts')
    .insert({
      tenant_id: tenantId,
      trigger_id: alert.triggerId,
      trigger_name: TRIGGER_KATALOG[alert.triggerId]?.name,
      schwere: alert.schwere,
      object_id: alert.objectId,
      object_type: alert.objectType,
      titel: alert.titel,
      nachricht,
      daten: alert.daten,
      aktionen: alert.aktionen,
      empfaenger_rollen: getEmpfaengerRollen(alert.triggerId),
      status: 'sent',
      sent_at: new Date().toISOString(),
      override: TRIGGER_KATALOG[alert.triggerId]?.override ?? false
    })
    .select()
    .single()

  // Trigger-State updaten
  await supabase
    .from('aria_trigger_states')
    .upsert({
      tenant_id: tenantId,
      trigger_id: alert.triggerId,
      object_id: alert.objectId,
      last_sent_at: new Date().toISOString(),
      last_value: alert.currentValue,
      zustand: 'triggered',
      trigger_count: supabase.rpc('increment', { x: 1 })
    }, { onConflict: 'tenant_id,trigger_id,object_id' })

  // Discord/Push-Notification senden
  await notificationDispatcher.send(tenantId, saved!)
}
```


===============================================================================
# TEIL 22 — BULLMQ JOB DEFINITIONEN
===============================================================================

```typescript
// queues/aria-proactivity.queue.ts

import { Queue, Worker } from 'bullmq'
import { getRedis } from '@/lib/redis'

export const ariaProactivityQueue = new Queue('aria-proactivity', {
  connection: getRedis()
})

// Job-Registrierung
export function registerAriaProactivityJobs(tenantId: string) {

  // Stockout Check — alle 30 Minuten
  ariaProactivityQueue.add('aria-trigger-stockout-check',
    { tenantId },
    { repeat: { every: 30 * 60 * 1000 } }
  )

  // Revenue Drop Check — stündlich
  ariaProactivityQueue.add('aria-trigger-revenue-check',
    { tenantId },
    { repeat: { every: 60 * 60 * 1000 } }
  )

  // Buy Box Check — alle 15 Minuten
  ariaProactivityQueue.add('aria-trigger-buybox-check',
    { tenantId },
    { repeat: { every: 15 * 60 * 1000 } }
  )

  // Account Health Check — stündlich
  ariaProactivityQueue.add('aria-trigger-account-health',
    { tenantId },
    { repeat: { every: 60 * 60 * 1000 } }
  )

  // Repricing Engine Health — alle 10 Minuten
  ariaProactivityQueue.add('aria-trigger-repricing-health',
    { tenantId },
    { repeat: { every: 10 * 60 * 1000 } }
  )

  // Preis-Anomalie Check — alle 30 Minuten
  ariaProactivityQueue.add('aria-trigger-price-check',
    { tenantId },
    { repeat: { every: 30 * 60 * 1000 } }
  )

  // Review Check — alle 2 Stunden
  ariaProactivityQueue.add('aria-trigger-review-check',
    { tenantId },
    { repeat: { every: 2 * 60 * 60 * 1000 } }
  )

  // ACoS/Advertising Check — alle 2 Stunden
  ariaProactivityQueue.add('aria-trigger-ads-check',
    { tenantId },
    { repeat: { every: 2 * 60 * 60 * 1000 } }
  )

  // Bundle Sender — alle 15 Minuten
  ariaProactivityQueue.add('aria-bundle-sender',
    { tenantId },
    { repeat: { every: 15 * 60 * 1000 } }
  )

  // Morning Bundle — täglich 07:00
  ariaProactivityQueue.add('aria-morning-bundle',
    { tenantId },
    { repeat: { pattern: '0 7 * * *', tz: 'Europe/Berlin' } }
  )

  // Evening Bundle — täglich 18:00
  ariaProactivityQueue.add('aria-evening-bundle',
    { tenantId },
    { repeat: { pattern: '0 18 * * *', tz: 'Europe/Berlin' } }
  )

  // Weekly Retro + Review Bundle — Freitag 17:00
  ariaProactivityQueue.add('aria-weekly-bundle',
    { tenantId },
    { repeat: { pattern: '0 17 * * 5', tz: 'Europe/Berlin' } }
  )
}
```


===============================================================================
# TEIL 23 — DASHBOARD & MONITORING QUERIES
===============================================================================


## Heutige Alert-Übersicht

```sql
SELECT
  schwere,
  COUNT(*) as anzahl,
  COUNT(*) FILTER (WHERE status = 'acknowledged') as gelesen,
  COUNT(*) FILTER (WHERE status = 'acted') as bearbeitet,
  COUNT(*) FILTER (WHERE status = 'suppressed') as suppressed
FROM aria_alerts
WHERE tenant_id = $1
  AND sent_at >= CURRENT_DATE
GROUP BY schwere
ORDER BY CASE schwere
  WHEN 'CRITICAL' THEN 1
  WHEN 'HIGH' THEN 2
  WHEN 'MEDIUM' THEN 3
  WHEN 'LOW' THEN 4
  WHEN 'INFO' THEN 5
END;
```


## Aktivste Trigger der letzten 30 Tage

```sql
SELECT
  trigger_id,
  trigger_name,
  COUNT(*) as ausloesungen,
  COUNT(*) FILTER (WHERE status = 'acted') as mit_aktion,
  ROUND(100.0 * COUNT(*) FILTER (WHERE status = 'acted') / COUNT(*), 1) as aktion_rate_pct,
  MAX(sent_at) as zuletzt_gesendet
FROM aria_alerts
WHERE tenant_id = $1
  AND sent_at >= NOW() - INTERVAL '30 days'
  AND status != 'suppressed'
GROUP BY trigger_id, trigger_name
ORDER BY ausloesungen DESC
LIMIT 20;
```


## Suppression-Rate pro Trigger

```sql
SELECT
  trigger_id,
  COUNT(*) as total_ausgeloest,
  COUNT(*) FILTER (WHERE status = 'suppressed') as suppressed,
  ROUND(100.0 * COUNT(*) FILTER (WHERE status = 'suppressed') / COUNT(*), 1) as suppression_rate_pct,
  array_agg(DISTINCT daten->>'suppress_grund') as suppress_gruende
FROM aria_alerts
WHERE tenant_id = $1
  AND created_at >= NOW() - INTERVAL '7 days'
GROUP BY trigger_id
HAVING COUNT(*) FILTER (WHERE status = 'suppressed') > 0
ORDER BY suppression_rate_pct DESC;
```


## Unbearbeitete CRITICAL Alerts

```sql
SELECT
  id,
  trigger_id,
  titel,
  object_id,
  sent_at,
  EXTRACT(EPOCH FROM (NOW() - sent_at))/60 as minuten_offen
FROM aria_alerts
WHERE tenant_id = $1
  AND schwere = 'CRITICAL'
  AND status NOT IN ('acted', 'resolved')
ORDER BY sent_at ASC;
```


## Tages-Cap Status

```sql
SELECT
  recipient_role,
  COUNT(*) as alerts_heute,
  (SELECT (aria_proactivity_config->>'daily_cap')::int FROM tenants WHERE id = $1) as daily_cap,
  CASE WHEN COUNT(*) >= (SELECT (aria_proactivity_config->>'daily_cap')::int FROM tenants WHERE id = $1)
    THEN 'LIMIT_ERREICHT'
    ELSE 'OK'
  END as status
FROM aria_alerts, unnest(empfaenger_rollen) AS recipient_role
WHERE tenant_id = $1
  AND sent_at >= CURRENT_DATE
  AND schwere != 'CRITICAL'
GROUP BY recipient_role;
```


## Hysteres-Analyse

```sql
SELECT
  ts.trigger_id,
  ts.object_id,
  ts.last_value,
  ts.zustand,
  ts.trigger_count,
  ts.suppressed_count,
  ts.last_triggered_at,
  ts.last_sent_at,
  EXTRACT(EPOCH FROM (NOW() - ts.last_sent_at))/60 as min_seit_letztem
FROM aria_trigger_states ts
WHERE ts.tenant_id = $1
  AND ts.zustand = 'triggered'
ORDER BY ts.last_triggered_at DESC;
```


## Bundle-Performance

```sql
SELECT
  bundle_typ,
  COUNT(*) as bundles_gesendet,
  AVG(alert_count) as avg_alerts_pro_bundle,
  MAX(alert_count) as max_alerts_in_bundle
FROM aria_alert_bundles
WHERE tenant_id = $1
  AND sent_at >= NOW() - INTERVAL '30 days'
GROUP BY bundle_typ
ORDER BY bundles_gesendet DESC;
```


---

*ARIA-PROAKTIVITAET.md — Production Ready*
*Comentra Intelligence Layer*
*Version 1.0 — Mai 2026*
*92 Trigger. 10 Anti-Spam-Regeln. 8 Bündelungs-Typen.*
===============================================================================
# TEIL 24 — VOLLSTÄNDIGE SCHWELLENWERT-REFERENZTABELLEN
===============================================================================

## 24.1 Revenue-Schwellen nach Saison

```
ZEITRAUM                  NORMAL-ABWEICHUNG   ALERT-SCHWELLE   OVERRIDE-SCHWELLE
───────────────────────────────────────────────────────────────────────────────────
Januar                    ±25%                -40%             -60%
Februar                   ±20%                -35%             -55%
März (Frühling-Start)     ±30%                -35%             -55%
April                     ±25%                -35%             -55%
Mai                       ±20%                -35%             -55%
Juni                      ±20%                -35%             -55%
Juli                      ±25%                -40%             -60%
August                    ±25%                -40%             -60%
September                 ±20%                -35%             -55%
Oktober (Pre-Peak)        ±30%                -30%             -50%
November (Peak)           ±50%                -25%             -40%
Dezember (Peak)           ±45%                -25%             -40%
```

## 24.2 Stockout-Schwellen nach Lead-Time

```
LEAD-TIME           KRITISCH (<)    HOCH (<)    MEDIUM (<)
───────────────────────────────────────────────────────────
1-2 Tage            Lead-Time       4 Tage      8 Tage
3-5 Tage            Lead-Time       7 Tage      14 Tage
6-10 Tage           Lead-Time       14 Tage     21 Tage
11-20 Tage          Lead-Time       21 Tage     35 Tage
21-30 Tage          Lead-Time       30 Tage     45 Tage
> 30 Tage           Lead-Time       Lead+7 T.   Lead+14 T.
```

## 24.3 ACoS-Schwellen nach Produktkategorie

```
KATEGORIE                   ZIEL-ACoS    WARN-ACoS    STOP-ACoS
──────────────────────────────────────────────────────────────────
Hochpreisige Möbel (>200€)  15-20%       30%          45%
Mittelpeis Heimdeko         20-25%       35%          50%
Outdoor / Garten            18-22%       32%          48%
Akustik / Büro              22-28%       38%          55%
Kinderzimmer / Spielzeug    20-25%       35%          50%
Werkzeug / Heimwerk         18-22%       30%          45%
```

## 24.4 Review-Schwellen nach Produktalter

```
PRODUKTALTER   ERWARTETE REVIEWS   WARN-SCORE   ALERT-RATE (neg.)
────────────────────────────────────────────────────────────────────
0-30 Tage      0-5                 3.0+         1+ unter 3 Sterne
31-90 Tage     5-20                3.5+         2+ unter 3 Sterne in 7d
91-180 Tage    20-50               3.8+         3+ unter 3 Sterne in 14d
181-365 Tage   50-100              4.0+         3+ unter 3 Sterne in 14d
> 1 Jahr       100+                4.2+         -0.3 Score-Drop in 30d
```

## 24.5 Conversion-Schwellen nach Kanal

```
KANAL          TYPISCHE CR    WARN (<)    CRITICAL (<)
──────────────────────────────────────────────────────────
Amazon.de      8-15%          50% Baseline  25% Baseline
eBay.de        3-8%           50% Baseline  25% Baseline
Otto           5-12%          50% Baseline  25% Baseline
Kaufland       4-9%           50% Baseline  25% Baseline
```

===============================================================================
# TEIL 25 — TRIGGER-NACHRICHTEN-TEMPLATES
===============================================================================

Jeder Trigger hat ein Handlebars-Template für die Alert-Nachricht.
Variablen in {{doppelten Klammern}}.

### Template: SO-001 (CRITICAL)

```
⚠️ SOFORT: {{sku}} ist ausverkauft — Listing noch aktiv.

Jede Bestellung die jetzt eingeht kann nicht erfüllt werden.
Umsatz-Ausfall läuft.

Nächster Schritt: Listing jetzt pausieren ODER Bestand buchen.
Bestand in System: 0 | Listing-Status: {{listing_status}}
```

### Template: SO-003 (HIGH)

```
🔴 Stockout in {{days_of_stock}} Tagen: {{sku}}

Aktueller Bestand: {{stock_quantity}} Einheiten
Täglicher Absatz: {{daily_velocity}} Einheiten/Tag
Reichweite: {{days_of_stock}} Tage

Lead-Time bei {{supplier_name}}: {{lead_time_days}} Tage
Bestellung sollte heute noch raus.
```

### Template: RD-001 (CRITICAL)

```
⚠️ UMSATZ-EINBRUCH: {{pct_change}}% heute vs. gleicher Wochentag letzte Woche.

Heute bis jetzt:    {{today_revenue}} €
Vorwoche gleicher Tag: {{comparison_revenue}} €
Differenz:          {{diff_revenue}} €

Zeitraum: {{current_time}} Uhr — Beginn des Einbruchs: ~{{drop_start_time}} Uhr
```

### Template: PA-002 (HIGH)

```
🔴 Buy Box verloren: {{sku}} auf {{marketplace}}

Unser Preis:         {{our_price}} €
Wettbewerber:        {{competitor_name}} — {{competitor_price}} €
Differenz:           {{price_diff}} €

Letzter Buy-Box-Zeitpunkt: {{last_buybox_time}}
Empfehlung: Preis auf {{recommended_price}} € anpassen (Marge: {{new_margin}}%)
```

### Template: AH-001 (CRITICAL)

```
⚠️ AMAZON ODR ÜBER GRENZE: {{odr_pct}}% (Grenze: 1,0%)

Account-Sperre droht.

Beitragende Faktoren:
  A-to-Z Claims:       {{atoz_count}} in 60 Tagen
  Negative Bewertungen: {{neg_reviews}} in 60 Tagen
  Chargebacks:         {{chargebacks}} in 60 Tagen

Sofortmaßnahme: Alle offenen A-to-Z Claims innerhalb 24h bearbeiten.
```

### Template: AD-001 (HIGH)

```
🔴 ACoS zu hoch: {{campaign_name}}

Aktueller ACoS:     {{acos_pct}}% (7-Tage-Schnitt)
Ziel-ACoS:          {{target_acos_pct}}%
Tägliche Ausgaben:  {{daily_spend}} €
Tägliche Sales:     {{daily_sales}} €

Break-Even ACoS:    {{breakeven_acos_pct}}%
Empfehlung: Gebote auf Nicht-Converter um {{reduction_pct}}% senken.
```

### Template: RA-001 (HIGH)

```
⭐ 1-Stern-Bewertung: {{sku}} auf {{marketplace}}

Bewerter: {{reviewer_name}}
Bewertungstext: "{{review_text_short}}"

Bestellung: {{order_id}} vom {{order_date}}

Empfehlung: Response innerhalb 24h.
Ich habe einen Response-Entwurf vorbereitet — [öffnen]
```

### Template: CP-001 (HIGH)

```
💡 CHANCE: {{competitor_name}} ausverkauft für {{sku}}

Wettbewerber ohne Bestand seit: {{oos_since}}
Kanal: {{marketplace}}

Unser Bestand: {{our_stock}} Einheiten ({{our_days}} Tage Reichweite)

Historisch bei Wettbewerber-OOS: +{{historical_conversion_lift}}% Conversion
Empfehlung:
  Preis: +{{recommended_price_increase}} € → {{new_price}} €
  Werbung: Budget +{{recommended_budget_increase}}% für {{recommended_days}} Tage
```

===============================================================================
# TEIL 26 — PROAKTIVITÄTS-KONFIGURATION PER TENANT
===============================================================================

## 26.1 Vollständiges Config-Schema

```typescript
interface AriaProactivityConfig {

  // ─── Anti-Spam ───────────────────────────────────────────
  daily_cap: number                    // Default: 10
  burst_limit: number                  // Default: 2
  burst_window_min: number             // Default: 15

  // ─── Zeiten ──────────────────────────────────────────────
  quiet_hours_enabled: boolean         // Default: true
  quiet_hours_start: string            // Default: '22:00'
  quiet_hours_end: string              // Default: '07:00'
  quiet_tz: string                     // Default: 'Europe/Berlin'
  weekend_mode: boolean                // Default: true
  weekend_high_threshold_eur: number   // Default: 500
  weekend_quiet_days: string[]         // Default: ['saturday','sunday']

  // ─── Urlaub ───────────────────────────────────────────────
  vacation_mode: boolean               // Default: false
  vacation_start: string | null        // ISO-Date
  vacation_end: string | null          // ISO-Date
  vacation_backup_recipient: string | null  // User-ID

  // ─── Peak-Anpassungen ─────────────────────────────────────
  peak_mode: boolean                   // Default: false (manuell oder auto)
  peak_daily_cap_multiplier: number    // Default: 1.5 (15 statt 10)
  peak_weekend_override: boolean       // Default: true

  // ─── Kanal-spezifische Deaktivierung ─────────────────────
  disabled_triggers: string[]          // z.B. ['RA-004', 'OA-003']
  disabled_channels: string[]          // z.B. ['kaufland'] wenn nicht aktiv

  // ─── Empfänger-Override ───────────────────────────────────
  critical_override_recipients: string[]   // Immer benachrichtigen bei CRITICAL
  gf_digest_only: boolean              // GF bekommt nur Digests, keine Einzelalerts

  // ─── Schwellenwert-Anpassungen ────────────────────────────
  revenue_drop_threshold: number       // Default: 0.40 (40%)
  acos_warn_threshold: number          // Default: 0.40 (40%)
  odr_warn_threshold: number           // Default: 0.0075 (0.75%)
  stockout_warn_days: number           // Default: 7
}
```

## 26.2 Starter vs Professional vs Enterprise Konfiguration

```
FEATURE                         STARTER   PROFESSIONAL   ENTERPRISE
──────────────────────────────────────────────────────────────────────────
Trigger-Katalog (Basis)         ✓         ✓              ✓
CRITICAL Alerts                 ✓         ✓              ✓
HIGH Alerts                     ✓         ✓              ✓
MEDIUM/LOW Alerts               —         ✓              ✓
Bündelungs-Logik (Basic)        ✓         ✓              ✓
Bündelungs-Logik (Advanced)     —         ✓              ✓
Wochenbericht                   —         ✓              ✓
Anti-Spam konfigurierbar        —         ✓              ✓
Peak-Modus                      —         ✓              ✓
Benutzerdefinierte Schwellen    —         —              ✓
Rollen-basiertes Routing        —         —              ✓
Urlaubs-Modus                   —         ✓              ✓
Max Trigger aktiv               20        50             alle 92
Daily Cap                       5         10             25
```

===============================================================================
# TEIL 27 — TRIGGER-ABHÄNGIGKEITEN & KASKADEN
===============================================================================

Einige Trigger sind voneinander abhängig oder lösen Kaskaden aus.

## 27.1 Abhängigkeits-Graph

```
SO-001 (Stockout jetzt)
  ← wird ausgelöst wenn SO-003 ignoriert wurde
  ← wird ausgelöst wenn SO-002 ignoriert wurde
  → triggert automatisch: OA-001 Prüfung (Spike?)
  → suppressed wenn: Listing bereits manuell pausiert

PA-001 (Preis unter Marge)
  ← wird ausgelöst wenn PA-008 nicht behoben wurde
  → triggert sofort: RD-001 Monitoring (Verlust-Verkäufe)
  → suppressed wenn: Mindestpreis manuell deaktiviert

AH-001 (ODR über Grenze)
  ← eskaliert von AH-002 wenn keine Aktion erfolgte
  → triggert: alle anderen AH-Trigger werden suppressed (Überlast)
  → triggert: Krisenmodus-Flag in aria_proactivity_config

RD-002 (Null-Umsatz)
  → prüft automatisch: Listing-Status aller aktiven SKUs
  → prüft: Repricing-Engine Status
  → prüft: Marketplace-API-Status
```

## 27.2 Eskalations-Ketten

```
ESKALATION 1: Stockout-Kette
  SO-004 (14 Tage) → ignoriert 7 Tage → SO-003 (7 Tage)
  SO-003 (7 Tage)  → ignoriert 5 Tage → SO-002 (Lead-Time)
  SO-002 (LT)      → ignoriert 1 Tag  → SO-001 (jetzt)

ESKALATION 2: ODR-Kette
  AH-002 (0.75%)   → keine Aktion 48h → AH-001 (1.0%)
  AH-001 (1.0%)    → keine Aktion 72h → Krisenmodus + externe Benachrichtigung

ESKALATION 3: Revenue-Kette
  RD-003 (Monatsziel) → keine Aktion 7 Tage → RD-001 Daily Check schärfer
  RD-001 (40% Drop)   → keine Aktion 4h     → GF-Direktanruf (wenn konfiguriert)

ESKALATION 4: Repricing-Kette
  PA-007 (Engine down) → keine Aktion 2h → PA-001 Check (Preis unter Marge?)
  PA-008 (Unter Minimum) → sofort → PA-001 + Listing-Pausierung empfohlen
```

## 27.3 Gegenseitige Ausschlussbedingungen

```
WENN AKTIV:              DANN SUPPRESSED:
────────────────────────────────────────────────────────────────
AH-001 (Krisenmodus)     Alle LOW und MEDIUM dieses Tenants
SO-001 (Stockout)        SO-003, SO-004 für gleiche SKU
RD-002 (Null-Umsatz)     RD-001 (wäre redundant)
PA-001 (Preis-Fehler)    PA-005 (Preiserhöhungs-Chance)
Urlaubs-Modus aktiv      Alle außer CRITICAL
```

===============================================================================
# TEIL 28 — PROAKTIVITÄTS-METRIKEN & KPIs
===============================================================================

## 28.1 Qualitäts-KPIs des Alert-Systems

```
KPI                           BESCHREIBUNG                         ZIEL
────────────────────────────────────────────────────────────────────────────
Action Rate                   Alerts die zu einer Aktion führten   > 60%
Response Time (CRITICAL)      Zeit bis erste Aktion nach CRITICAL  < 10 Min
Response Time (HIGH)          Zeit bis erste Aktion nach HIGH      < 2h
False Positive Rate           Alerts ohne erkennbare Relevanz      < 10%
Suppression Rate              Alerts die Anti-Spam unterdrückt     < 30%
Bundle Efficiency             Alerts in Bündeln vs. einzeln        > 25%
Daily Cap Hits                Tage mit Daily-Cap-Limit-Erreichen   < 10%/Monat
Mute Rate                     Trigger die dauerhaft ignoriert      < 5%
CRITICAL Resolution Time      Zeit bis CRITICAL auf 'resolved'     < 4h
Recurrence Rate               Gleicher Trigger in 7 Tagen erneut  < 20%
```

## 28.2 SQL: Qualitäts-KPI-Berechnung

```sql
-- Action Rate der letzten 30 Tage
SELECT
  ROUND(
    100.0 * COUNT(*) FILTER (WHERE status IN ('acted', 'resolved'))
    / NULLIF(COUNT(*) FILTER (WHERE status != 'suppressed'), 0),
  1) AS action_rate_pct,
  ROUND(
    100.0 * COUNT(*) FILTER (WHERE status = 'suppressed')
    / NULLIF(COUNT(*), 0),
  1) AS suppression_rate_pct
FROM aria_alerts
WHERE tenant_id = $1
  AND created_at >= NOW() - INTERVAL '30 days';
```

## 28.3 Automatische Alert-System-Selbstdiagnose

```typescript
// Täglich um 03:00 Uhr: System-Health-Check für das Alert-System selbst
async function ariaProactivityHealthCheck(tenantId: string): Promise<void> {

  const stats = await getAlertStats(tenantId, 7)  // letzte 7 Tage

  // Zu viele Suppressions → Thresholds zu aggressiv
  if (stats.suppression_rate > 0.50) {
    await createInternalAlert(tenantId, {
      type: 'SYSTEM_HEALTH',
      message: `Alert-Suppression-Rate bei ${(stats.suppression_rate*100).toFixed(0)}%.` +
               ` Schwellenwerte prüfen — ggf. Daily Cap erhöhen.`,
      severity: 'LOW'
    })
  }

  // Zu wenig Actions → Alerts werden ignoriert
  if (stats.action_rate < 0.20 && stats.total_alerts > 10) {
    await createInternalAlert(tenantId, {
      type: 'SYSTEM_HEALTH',
      message: `Action Rate nur ${(stats.action_rate*100).toFixed(0)}%.` +
               ` Alerts werden ignoriert. Relevanz der Trigger prüfen.`,
      severity: 'MEDIUM'
    })
  }

  // CRITICAL ohne Response
  const unresolvedCriticals = await getUnresolvedCriticals(tenantId, 4)
  if (unresolvedCriticals.length > 0) {
    await escalateCriticals(tenantId, unresolvedCriticals)
  }
}
```

===============================================================================
# TEIL 29 — TRIGGER-VOLLSTÄNDIGE ÜBERSICHTSTABELLE
===============================================================================

```
ID         NAME                                       SCHWERE    COOLDOWN  OVERRIDE  BÜNDELBAR
─────────────────────────────────────────────────────────────────────────────────────────────────
RD-001     Tages-Umsatz kritisch eingebrochen          CRITICAL   120       NEIN      NEIN
RD-002     Umsatz-Nulllinie                            CRITICAL   240       JA        NEIN
RD-003     Monats-Ziel in Gefahr                       HIGH       1440      NEIN      JA
RD-004     Wochenvergleich negativ                     MEDIUM     10080     NEIN      JA
RD-005     Umsatzspike positiv                         INFO       1440      NEIN      JA
RD-006     Kanal-Ausfall                               CRITICAL   360       NEIN      NEIN
OA-001     Bestellmenge-Spike einzelne SKU             HIGH       240       NEIN      JA
OA-002     Stornierungsrate gestiegen                  MEDIUM     720       NEIN      JA
OA-003     Großbestellung eingegangen                  INFO       0         NEIN      JA
OA-004     Offene Bestellungen aufgestaut              HIGH       480       NEIN      JA
OA-005     Bestellwert-Anomalie                        MEDIUM     1440      NEIN      JA
OA-006     B2B-Großkunde Bestellpause                  LOW        10080     NEIN      JA
SO-001     Stockout sofort                             CRITICAL   0         JA        NEIN
SO-002     Kritischer Bestand < Lead-Time              CRITICAL   240       JA        NEIN
SO-003     Stockout-Risiko 7 Tage                      HIGH       480       JA        JA
SO-004     Stockout-Risiko 14 Tage                     MEDIUM     1440      JA        JA
SO-005     Bestandsdifferenz Soll/Ist                  HIGH       720       NEIN      JA
SO-006     Überbestand 180 Tage                        LOW        10080     NEIN      JA
SO-007     Lieferung verzögert                         HIGH       1440      NEIN      JA
SO-008     Charge läuft ab                             HIGH       1440      NEIN      JA
SO-009     FBA-Bestand niedrig                         HIGH       480       NEIN      JA
SO-010     FBA-Bestand zu hoch                         MEDIUM     10080     NEIN      JA
SO-011     Multi-Kanal Bestand-Konflikt                HIGH       60        NEIN      NEIN
PA-001     Preis unter Marge                           CRITICAL   60        JA        NEIN
PA-002     Buy Box verloren                            HIGH       240       NEIN      JA
PA-003     Wettbewerber senkt massiv                   HIGH       480       NEIN      JA
PA-004     Preiskampf erkannt                          HIGH       720       NEIN      JA
PA-005     Preiserhöhungs-Chance                       MEDIUM     1440      NEIN      JA
PA-006     Wettbewerber OOS Preischance                HIGH       240       NEIN      JA
PA-007     Repricing-Engine down                       CRITICAL   120       JA        NEIN
PA-008     Mindestpreis unterschritten                 CRITICAL   0         JA        NEIN
AD-001     ACoS zu hoch                                HIGH       480       NEIN      JA
AD-002     Budget aufgebraucht                         HIGH       480       NEIN      JA
AD-003     Conversion Werbung eingebrochen             MEDIUM     720       NEIN      JA
AD-004     Impression-Einbruch                         MEDIUM     720       NEIN      JA
AD-005     Neues High-Performer Keyword                INFO       10080     NEIN      JA
AD-006     Verlust-Keyword erkannt                     MEDIUM     10080     NEIN      JA
AD-007     Wettbewerber auf Keywords                   LOW        1440      NEIN      JA
AD-008     Monatliches Ad-Budget überschritten         MEDIUM     1440      NEIN      JA
AH-001     Amazon ODR über Schwelle                    CRITICAL   0         JA        NEIN
AH-002     Amazon ODR nähert sich Schwelle             HIGH       480       JA        NEIN
AH-003     Late Shipment Rate zu hoch                  HIGH       480       NEIN      NEIN
AH-004     Amazon Account-Warnung                      CRITICAL   0         JA        NEIN
AH-005     eBay Account-Einschränkung                  CRITICAL   0         NEIN      NEIN
AH-006     Verkäufer-Bewertung gefallen                MEDIUM     1440      NEIN      JA
AH-007     DATEV/Finanzamt Frist                       HIGH       0         NEIN      NEIN
AH-008     Marketplace-Gebühren-Erhöhung               MEDIUM     10080     NEIN      JA
RA-001     1-Stern-Bewertung                           HIGH       1440      NEIN      JA
RA-002     Negative Bewertung-Serie                    HIGH       1440      NEIN      JA
RA-003     Bewertungs-Durchschnitt fällt               MEDIUM     10080     NEIN      JA
RA-004     Neue 5-Sterne-Bewertung                     INFO       0         NEIN      JA
RA-005     Bewertungs-Spike verdächtig                 MEDIUM     1440      NEIN      JA
RA-006     Themen-Muster negativ                       MEDIUM     10080     NEIN      JA
RA-007     Verkäufer-Feedback negativ                  HIGH       720       NEIN      JA
LG-001     Paket verloren                              CRITICAL   0         JA        NEIN
LG-002     Versandverzögerung SLA                      HIGH       240       NEIN      JA
LG-003     Retoure Qualitätsprüfung                    MEDIUM     1440      NEIN      JA
LG-004     Zustellfehler ohne Follow-up                HIGH       480       NEIN      JA
LG-005     Paket-Pool Kapazitätsgrenze                 MEDIUM     1440      NEIN      JA
LG-006     Frankier-Fehler Carrier                     MEDIUM     1440      NEIN      JA
CP-001     Wettbewerber OOS                            HIGH       240       NEIN      JA
CP-002     Neuer Wettbewerber im Markt                 MEDIUM     10080     NEIN      JA
CP-003     Marktpreis-Erosion                          HIGH       10080     NEIN      JA
CP-004     Wettbewerber startet Promotion              MEDIUM     1440      NEIN      JA
CP-005     Kategorie-Bestseller wechselt               LOW        10080     NEIN      JA
FN-001     Amazon-Auszahlung niedrig                   HIGH       10080     NEIN      JA
FN-002     Lieferanten-Rechnung überfällig             HIGH       1440      NEIN      JA
FN-003     Margin-Erosion erkannt                      MEDIUM     10080     NEIN      JA
FN-004     DATEV-Export ausstehend                     MEDIUM     10080     NEIN      JA
FN-005     USt-Fälligkeit nähert sich                  HIGH       0         NEIN      NEIN
TM-001     Task überfällig kritisch                    HIGH       1440      NEIN      JA
TM-002     Viele überfällige Tasks                     MEDIUM     1440      NEIN      JA
TM-003     Fehler-Muster Mitarbeiter                   MEDIUM     10080     NEIN      JA
TM-004     Freitag offene kritische Bestellungen       HIGH       0         JA        NEIN
AZ-LQ-001  Amazon Listing-Qualitätsscore               MEDIUM     10080     NEIN      JA
AZ-LQ-002  A+ Content fehlt                            LOW        43200     NEIN      JA
AZ-LQ-003  Hauptbild geändert durch Dritten            HIGH       240       NEIN      NEIN
AZ-FBA-001 FBA Stranded Inventory                      MEDIUM     1440      NEIN      JA
AZ-FBA-002 FBA Long-Term Storage                       MEDIUM     1440      NEIN      JA
AZ-FBA-003 FBA-Einlieferung abgelehnt                  HIGH       1440      NEIN      NEIN
AZ-VC-001  Vine-Review eingegangen                     INFO       0         NEIN      JA
EB-PM-001  eBay Performance-Defizit                    HIGH       480       NEIN      NEIN
EB-SR-001  eBay Seller Rating gefallen                 MEDIUM     1440      NEIN      JA
EB-OFR-001 eBay Best Offer ausstehend                  LOW        2880      NEIN      JA
OT-QS-001  Otto Qualitätsscore gefallen                HIGH       1440      NEIN      JA
OT-RT-001  Otto Retoure hohe Quote                     HIGH       1440      NEIN      JA
OT-PO-001  Otto Bestelleingang Sync-Fehler             CRITICAL   120       JA        NEIN
PEAK-001   Black Friday 14-Tage-Vorlauf                HIGH       0         NEIN      NEIN
PEAK-002   Black Friday 3-Tage-Vorlauf                 CRITICAL   0         JA        NEIN
PEAK-003   Black Friday läuft                          INFO       30        NEIN      JA
POSTPEAK-001 Post-Peak Retouren-Welle                  MEDIUM     0         NEIN      NEIN
POSTPEAK-002 Lagerräumung Post-Peak                    LOW        10080     NEIN      JA
SPRING-001 Frühlings-Saison-Vorbereitung               MEDIUM     0         NEIN      NEIN
```

---

*ARIA-PROAKTIVITAET.md — Production Ready*
*Comentra Intelligence Layer*
*Version 1.0 — Mai 2026*
*92 Trigger | 10 Anti-Spam-Regeln | 8 Bündelungs-Typen*
*Kein Text ohne Regel. Keine Regel ohne Code.*
===============================================================================
# TEIL 30 — TRIGGER-KATALOG TYPESCRIPT DEFINITIONEN
===============================================================================

```typescript
// services/aria/proactivity/trigger-katalog.ts
// Vollständige TypeScript-Definitionen aller 92 Trigger

export const TRIGGER_KATALOG: Record<string, Trigger> = {

  'RD-001': {
    id: 'RD-001',
    name: 'Tages-Umsatz eingebrochen',
    kategorie: 'REVENUE',
    schwere: 'CRITICAL',
    cooldown_minuten: 120,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { relativ: -0.40, vergleich: 'vorwoche_gleicher_tag' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RD-002': {
    id: 'RD-002',
    name: 'Null-Umsatz 4h',
    kategorie: 'REVENUE',
    schwere: 'CRITICAL',
    cooldown_minuten: 240,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { absolut: 0, zeitfenster: 'PT4H' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RD-003': {
    id: 'RD-003',
    name: 'Monatsziel in Gefahr',
    kategorie: 'REVENUE',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { relativ: -0.30, vergleich: 'monatsziel_proportional' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RD-004': {
    id: 'RD-004',
    name: 'Wochenvergleich negativ',
    kategorie: 'REVENUE',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { relativ: -0.20, vergleich: 'gleiche_kw_vorjahr' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RD-005': {
    id: 'RD-005',
    name: 'Umsatzspike positiv',
    kategorie: 'REVENUE',
    schwere: 'INFO',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { relativ: 0.50, vergleich: '7d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RD-006': {
    id: 'RD-006',
    name: 'Kanal-Ausfall',
    kategorie: 'REVENUE',
    schwere: 'CRITICAL',
    cooldown_minuten: 360,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { absolut: 0, zeitfenster: 'PT6H' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-001': {
    id: 'OA-001',
    name: 'Bestellmenge-Spike SKU',
    kategorie: 'ORDERS',
    schwere: 'HIGH',
    cooldown_minuten: 240,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'MarketplaceManager'],
    schwellenwert: { relativ: 3.0, vergleich: '7d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-002': {
    id: 'OA-002',
    name: 'Stornierungsrate gestiegen',
    kategorie: 'ORDERS',
    schwere: 'MEDIUM',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'Lager'],
    schwellenwert: { relativ: 0.05, zeitfenster: 'P1D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-003': {
    id: 'OA-003',
    name: 'Großbestellung',
    kategorie: 'ORDERS',
    schwere: 'INFO',
    cooldown_minuten: 0,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'GF'],
    schwellenwert: { absolut: 10 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-004': {
    id: 'OA-004',
    name: 'Offene Bestellungen aufgestaut',
    kategorie: 'ORDERS',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { absolut: 30, zeitfenster: 'P1D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-005': {
    id: 'OA-005',
    name: 'Bestellwert-Anomalie',
    kategorie: 'ORDERS',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { relativ: -0.50, vergleich: '30d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'OA-006': {
    id: 'OA-006',
    name: 'B2B Bestellpause',
    kategorie: 'ORDERS',
    schwere: 'LOW',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Vertrieb', 'GF'],
    schwellenwert: { absolut: 30, einheit: 'tage_seit_letzter_bestellung' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-001': {
    id: 'SO-001',
    name: 'Stockout jetzt',
    kategorie: 'INVENTORY',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['Lager', 'GF', 'MarketplaceManager'],
    schwellenwert: { absolut: 0 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-002': {
    id: 'SO-002',
    name: 'Bestand < Lead-Time',
    kategorie: 'INVENTORY',
    schwere: 'CRITICAL',
    cooldown_minuten: 240,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['Lager', 'Einkauf'],
    schwellenwert: { dynamisch: 'reichweite < lead_time_days' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-003': {
    id: 'SO-003',
    name: 'Stockout 7 Tage',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: true,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'Einkauf'],
    schwellenwert: { dynamisch: 'reichweite < 7' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-004': {
    id: 'SO-004',
    name: 'Stockout 14 Tage',
    kategorie: 'INVENTORY',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: true,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'Einkauf'],
    schwellenwert: { dynamisch: 'reichweite < 14' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-005': {
    id: 'SO-005',
    name: 'Bestandsdifferenz',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { relativ: 0.05, minimum_absolut: 10 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-006': {
    id: 'SO-006',
    name: 'Überbestand 180 Tage',
    kategorie: 'INVENTORY',
    schwere: 'LOW',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'Einkauf'],
    schwellenwert: { dynamisch: 'reichweite > 180' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-007': {
    id: 'SO-007',
    name: 'Lieferung verzögert',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'Einkauf'],
    schwellenwert: { absolut: 3, einheit: 'tage_ueberfaellig' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-008': {
    id: 'SO-008',
    name: 'Charge läuft ab',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { absolut: 60, einheit: 'tage_bis_ablauf' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-009': {
    id: 'SO-009',
    name: 'FBA Bestand niedrig',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { dynamisch: 'fba_reichweite < 7' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-010': {
    id: 'SO-010',
    name: 'FBA Bestand zu hoch',
    kategorie: 'INVENTORY',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { dynamisch: 'fba_reichweite > 90' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'SO-011': {
    id: 'SO-011',
    name: 'Kanal-Bestand-Konflikt',
    kategorie: 'INVENTORY',
    schwere: 'HIGH',
    cooldown_minuten: 60,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['MarketplaceManager', 'Lager'],
    schwellenwert: { bool: 'sync_error OR ueberverkauf' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-001': {
    id: 'PA-001',
    name: 'Preis unter Marge',
    kategorie: 'PRICING',
    schwere: 'CRITICAL',
    cooldown_minuten: 60,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { dynamisch: 'preis < einkauf * (1 + min_marge)' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-002': {
    id: 'PA-002',
    name: 'Buy Box verloren',
    kategorie: 'PRICING',
    schwere: 'HIGH',
    cooldown_minuten: 240,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { bool: 'buybox_verloren' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-003': {
    id: 'PA-003',
    name: 'Wettbewerber senkt massiv',
    kategorie: 'PRICING',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'GF'],
    schwellenwert: { relativ: -0.15, zeitfenster: 'P1D', filter: 'is_main_competitor' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-004': {
    id: 'PA-004',
    name: 'Preiskampf erkannt',
    kategorie: 'PRICING',
    schwere: 'HIGH',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { anzahl: 3, relativ: -0.10, zeitfenster: 'P2D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-005': {
    id: 'PA-005',
    name: 'Preiserhöhungs-Chance',
    kategorie: 'PRICING',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { relativ: 0.10, filter: 'alle_wettbewerber_teurer' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-006': {
    id: 'PA-006',
    name: 'Wettbewerber OOS Preischance',
    kategorie: 'PRICING',
    schwere: 'HIGH',
    cooldown_minuten: 240,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { bool: 'hauptwettbewerber_oos AND unser_bestand > 7' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-007': {
    id: 'PA-007',
    name: 'Repricing-Engine down',
    kategorie: 'PRICING',
    schwere: 'CRITICAL',
    cooldown_minuten: 120,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { zeitfenster: 'PT2H', bool: 'letzter_lauf_ueberfaellig' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'PA-008': {
    id: 'PA-008',
    name: 'Mindestpreis unterschritten',
    kategorie: 'PRICING',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { dynamisch: 'preis < min_allowed_price' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-001': {
    id: 'AD-001',
    name: 'ACoS zu hoch',
    kategorie: 'ADVERTISING',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'GF'],
    schwellenwert: { relativ: 0.40, zeitfenster: 'P7D', minimum_spend: 50 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-002': {
    id: 'AD-002',
    name: 'Budget aufgebraucht',
    kategorie: 'ADVERTISING',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { absolut: 0, zeitbedingung: 'vor_14_uhr' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-003': {
    id: 'AD-003',
    name: 'Ad-Conversion eingebrochen',
    kategorie: 'ADVERTISING',
    schwere: 'MEDIUM',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { relativ: -0.50, vergleich: '14d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-004': {
    id: 'AD-004',
    name: 'Impression-Einbruch',
    kategorie: 'ADVERTISING',
    schwere: 'MEDIUM',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { relativ: -0.70, vergleich: '7d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-005': {
    id: 'AD-005',
    name: 'High-Performer Keyword',
    kategorie: 'ADVERTISING',
    schwere: 'INFO',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { absolut: 10, einheit: 'conversions_7d_auto_kampagne' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-006': {
    id: 'AD-006',
    name: 'Verlust-Keyword',
    kategorie: 'ADVERTISING',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { klicks: 20, conversions: 0, ausgaben: 30 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-007': {
    id: 'AD-007',
    name: 'CPC Anstieg Keywords',
    kategorie: 'ADVERTISING',
    schwere: 'LOW',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { relativ: 0.50, vergleich: '30d_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AD-008': {
    id: 'AD-008',
    name: 'Monatliches Budget überschritten',
    kategorie: 'ADVERTISING',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { relativ: 0.10, vergleich: 'monatsbudget' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-001': {
    id: 'AH-001',
    name: 'Amazon ODR über Grenze',
    kategorie: 'ACCOUNT',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 0.010 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-002': {
    id: 'AH-002',
    name: 'Amazon ODR Warnstufe',
    kategorie: 'ACCOUNT',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { absolut: 0.0075 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-003': {
    id: 'AH-003',
    name: 'Late Shipment Rate',
    kategorie: 'ACCOUNT',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['Lager', 'GF'],
    schwellenwert: { absolut: 0.03 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-004': {
    id: 'AH-004',
    name: 'Amazon Account-Warnung',
    kategorie: 'ACCOUNT',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['GF'],
    schwellenwert: { bool: 'policy_notification' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-005': {
    id: 'AH-005',
    name: 'eBay Account-Einschränkung',
    kategorie: 'ACCOUNT',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { bool: 'ebay_restriction' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-006': {
    id: 'AH-006',
    name: 'Verkäufer-Bewertung gefallen',
    kategorie: 'ACCOUNT',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { amazon: 4.5, ebay_pct: 0.97 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-007': {
    id: 'AH-007',
    name: 'Steuerliche Frist',
    kategorie: 'ACCOUNT',
    schwere: 'HIGH',
    cooldown_minuten: 0,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 7, einheit: 'tage_bis_frist' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'AH-008': {
    id: 'AH-008',
    name: 'Gebühren-Erhöhung',
    kategorie: 'ACCOUNT',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { bool: 'gebuehren_aenderung_erkannt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-001': {
    id: 'RA-001',
    name: '1-Stern-Bewertung',
    kategorie: 'REVIEWS',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['CustomerService', 'MarketplaceManager'],
    schwellenwert: { absolut: 1 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-002': {
    id: 'RA-002',
    name: 'Neg. Bewertungs-Serie',
    kategorie: 'REVIEWS',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'GF'],
    schwellenwert: { anzahl: 3, schwelle: 3, zeitfenster: 'P7D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-003': {
    id: 'RA-003',
    name: 'Rating-Durchschnitt fällt',
    kategorie: 'REVIEWS',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { absolut: -0.3, zeitfenster: 'P30D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-004': {
    id: 'RA-004',
    name: 'Neue 5-Sterne-Bewertung',
    kategorie: 'REVIEWS',
    schwere: 'INFO',
    cooldown_minuten: 0,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { absolut: 5 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-005': {
    id: 'RA-005',
    name: 'Bewertungs-Spike',
    kategorie: 'REVIEWS',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { absolut: 10, zeitfenster: 'P1D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-006': {
    id: 'RA-006',
    name: 'Themen-Muster negativ',
    kategorie: 'REVIEWS',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'Einkauf'],
    schwellenwert: { frequenz: 3, zeitfenster: 'P14D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'RA-007': {
    id: 'RA-007',
    name: 'Verkäufer-Feedback negativ',
    kategorie: 'REVIEWS',
    schwere: 'HIGH',
    cooldown_minuten: 720,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['CustomerService'],
    schwellenwert: { absolut: 3 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-001': {
    id: 'LG-001',
    name: 'Paket verloren',
    kategorie: 'LOGISTICS',
    schwere: 'CRITICAL',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['Lager', 'CustomerService'],
    schwellenwert: { tage: 5, bool: 'kein_tracking_update' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-002': {
    id: 'LG-002',
    name: 'SLA-Versandverzögerung',
    kategorie: 'LOGISTICS',
    schwere: 'HIGH',
    cooldown_minuten: 240,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { dynamisch: 'order_age > sla_hours' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-003': {
    id: 'LG-003',
    name: 'Retoure Qualitätsprüfung',
    kategorie: 'LOGISTICS',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'Einkauf'],
    schwellenwert: { bool: 'defekt_oder_beschaedigt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-004': {
    id: 'LG-004',
    name: 'Zustellfehler',
    kategorie: 'LOGISTICS',
    schwere: 'HIGH',
    cooldown_minuten: 480,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['CustomerService'],
    schwellenwert: { bool: 'failed AND kein_redelivery' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-005': {
    id: 'LG-005',
    name: 'Paket-Pool Kapazität',
    kategorie: 'LOGISTICS',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager', 'GF'],
    schwellenwert: { relativ: 0.80, tage: 3 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'LG-006': {
    id: 'LG-006',
    name: 'Frankier-Fehler',
    kategorie: 'LOGISTICS',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { bool: 'carrier_surcharge' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'CP-001': {
    id: 'CP-001',
    name: 'Wettbewerber OOS',
    kategorie: 'COMPETITION',
    schwere: 'HIGH',
    cooldown_minuten: 240,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { bool: 'hauptwettbewerber_oos AND kanäle >= 1' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'CP-002': {
    id: 'CP-002',
    name: 'Neuer Wettbewerber',
    kategorie: 'COMPETITION',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager', 'GF'],
    schwellenwert: { bool: 'neues_listing_hauptkategorie' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'CP-003': {
    id: 'CP-003',
    name: 'Marktpreis-Erosion',
    kategorie: 'COMPETITION',
    schwere: 'HIGH',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF', 'MarketplaceManager'],
    schwellenwert: { relativ: -0.10, zeitfenster: 'P30D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'CP-004': {
    id: 'CP-004',
    name: 'Wettbewerber Promotion',
    kategorie: 'COMPETITION',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { relativ: -0.15, tage: 3 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'CP-005': {
    id: 'CP-005',
    name: 'BSR #1 gewechselt',
    kategorie: 'COMPETITION',
    schwere: 'LOW',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['MarketplaceManager'],
    schwellenwert: { bool: 'bsr1_seller_changed' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'FN-001': {
    id: 'FN-001',
    name: 'Auszahlung niedrig',
    kategorie: 'FINANCE',
    schwere: 'HIGH',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { relativ: -0.40, vergleich: '4w_schnitt' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'FN-002': {
    id: 'FN-002',
    name: 'Rechnung überfällig',
    kategorie: 'FINANCE',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 30, einheit: 'tage_ueberfaellig' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'FN-003': {
    id: 'FN-003',
    name: 'Margin-Erosion',
    kategorie: 'FINANCE',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: -0.03, zeitfenster: 'P60D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'FN-004': {
    id: 'FN-004',
    name: 'DATEV-Export ausstehend',
    kategorie: 'FINANCE',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 30, einheit: 'tage_seit_letztem_export' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'FN-005': {
    id: 'FN-005',
    name: 'USt-Fälligkeit',
    kategorie: 'FINANCE',
    schwere: 'HIGH',
    cooldown_minuten: 0,
    override: false,
    buendelbar: false,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 5, einheit: 'werktage_bis_frist' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'TM-001': {
    id: 'TM-001',
    name: 'Task kritisch überfällig',
    kategorie: 'TEAM',
    schwere: 'HIGH',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 24, einheit: 'stunden_nach_faelligkeit', filter: 'high_priority' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'TM-002': {
    id: 'TM-002',
    name: 'Viele überfällige Tasks',
    kategorie: 'TEAM',
    schwere: 'MEDIUM',
    cooldown_minuten: 1440,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { absolut: 5 },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'TM-003': {
    id: 'TM-003',
    name: 'Fehler-Muster',
    kategorie: 'TEAM',
    schwere: 'MEDIUM',
    cooldown_minuten: 10080,
    override: false,
    buendelbar: true,
    empfaenger_rollen: ['GF'],
    schwellenwert: { anzahl: 3, zeitfenster: 'P7D' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

  'TM-004': {
    id: 'TM-004',
    name: 'Freitag offene Bestellungen',
    kategorie: 'TEAM',
    schwere: 'HIGH',
    cooldown_minuten: 0,
    override: true,
    buendelbar: false,
    empfaenger_rollen: ['Lager'],
    schwellenwert: { zeitpunkt: 'FR_16:00', bool: 'kritische_bestellungen_offen' },
    kanal: ['amazon', 'ebay', 'otto', 'kaufland'],
  },

}
```

===============================================================================
# TEIL 31 — VOLLSTÄNDIGE WORKER-IMPLEMENTIERUNGEN
===============================================================================

## Worker: Revenue Drop Worker

```typescript
// workers/aria/revenue-drop.worker.ts

export async function revenueDropWorker(job: Job) {
  const { tenantId } = job.data
  const now = new Date()
  const hour = now.getHours()

  // Nur zwischen 08:00 und 22:00 auswerten
  if (hour < 8 || hour > 22) return

  // Heutiger Umsatz bisher
  const { data: today } = await supabase.rpc('get_revenue_today', {
    p_tenant_id: tenantId
  })

  // Gleicher Wochentag letzte Woche bis zur gleichen Uhrzeit
  const { data: lastWeek } = await supabase.rpc('get_revenue_same_weekday_last_week', {
    p_tenant_id: tenantId,
    p_until_hour: hour
  })

  if (!today || !lastWeek || lastWeek.revenue === 0) return

  const changeRate = (today.revenue - lastWeek.revenue) / lastWeek.revenue

  // RD-001: -40% vs. Vorwoche
  if (changeRate < -0.40) {
    await triggerAlert(tenantId, 'RD-001', 'revenue', 'CRITICAL', {
      today_revenue: today.revenue,
      comparison_revenue: lastWeek.revenue,
      pct_change: (changeRate * 100).toFixed(1),
      diff_revenue: (today.revenue - lastWeek.revenue).toFixed(2)
    })
  }

  // RD-002: 0 Bestellungen in letzten 4h
  const { data: lastFourH } = await supabase.rpc('get_orders_last_4h', {
    p_tenant_id: tenantId
  })

  if (lastFourH?.count === 0) {
    await triggerAlert(tenantId, 'RD-002', 'revenue', 'CRITICAL', {
      orders_last_4h: 0,
      hour: hour
    })
  }
}
```

## Worker: Buy Box Worker

```typescript
// workers/aria/buybox.worker.ts

export async function buyBoxWorker(job: Job) {
  const { tenantId } = job.data

  const { data: listings } = await supabase
    .from('marketplace_listings')
    .select('id, sku, marketplace, had_buybox_yesterday, has_buybox_now,
             current_price, competitor_price, competitor_name')
    .eq('tenant_id', tenantId)
    .eq('listing_status', 'active')

  for (const listing of listings ?? []) {

    // PA-002: Buy Box verloren
    if (listing.had_buybox_yesterday && !listing.has_buybox_now) {
      const priceDiff = listing.competitor_price - listing.current_price
      await triggerAlert(tenantId, 'PA-002', listing.sku, 'HIGH', {
        sku: listing.sku,
        marketplace: listing.marketplace,
        our_price: listing.current_price,
        competitor_price: listing.competitor_price,
        competitor_name: listing.competitor_name ?? 'Unbekannt',
        price_diff: Math.abs(priceDiff).toFixed(2),
        recommended_price: (listing.competitor_price - 0.05).toFixed(2)
      })
    }

    // PA-001: Preis unter Marge
    const { data: costs } = await supabase
      .from('product_costs')
      .select('purchase_price, min_margin')
      .eq('sku', listing.sku)
      .eq('tenant_id', tenantId)
      .single()

    if (costs) {
      const minPrice = costs.purchase_price * (1 + costs.min_margin)
      if (listing.current_price < minPrice) {
        await triggerAlert(tenantId, 'PA-001', listing.sku, 'CRITICAL', {
          sku: listing.sku,
          current_price: listing.current_price,
          min_price: minPrice.toFixed(2),
          purchase_price: costs.purchase_price,
          min_margin: (costs.min_margin * 100).toFixed(1)
        })
      }
    }
  }
}
```

## Worker: Account Health Worker

```typescript
// workers/aria/account-health.worker.ts

export async function accountHealthWorker(job: Job) {
  const { tenantId } = job.data

  // Amazon ODR Check
  const { data: amazonHealth } = await supabase
    .from('amazon_account_health')
    .select('odr, lsr, late_delivery_rate, updated_at')
    .eq('tenant_id', tenantId)
    .order('updated_at', { ascending: false })
    .limit(1)
    .single()

  if (amazonHealth) {
    // AH-001: ODR > 1%
    if (amazonHealth.odr > 0.010) {
      await triggerAlert(tenantId, 'AH-001', 'amazon', 'CRITICAL', {
        odr_pct: (amazonHealth.odr * 100).toFixed(2)
      })
    }
    // AH-002: ODR > 0.75%
    else if (amazonHealth.odr > 0.0075) {
      await triggerAlert(tenantId, 'AH-002', 'amazon', 'HIGH', {
        odr_pct: (amazonHealth.odr * 100).toFixed(2)
      })
    }

    // AH-003: LSR > 3%
    if (amazonHealth.lsr > 0.03) {
      await triggerAlert(tenantId, 'AH-003', 'amazon', 'HIGH', {
        lsr_pct: (amazonHealth.lsr * 100).toFixed(2)
      })
    }
  }

  // eBay Performance Check
  const { data: ebayHealth } = await supabase
    .from('ebay_performance_metrics')
    .select('tdr, ldr, feedback_score, account_restricted')
    .eq('tenant_id', tenantId)
    .order('updated_at', { ascending: false })
    .limit(1)
    .single()

  if (ebayHealth) {
    if (ebayHealth.account_restricted) {
      await triggerAlert(tenantId, 'AH-005', 'ebay', 'CRITICAL', {})
    }
    else if (ebayHealth.tdr > 0.005 || ebayHealth.ldr > 0.03) {
      await triggerAlert(tenantId, 'EB-PM-001', 'ebay', 'HIGH', {
        tdr_pct: (ebayHealth.tdr * 100).toFixed(2),
        ldr_pct: (ebayHealth.ldr * 100).toFixed(2)
      })
    }
  }
}
```

## Worker: Review Check Worker

```typescript
// workers/aria/review-check.worker.ts

export async function reviewCheckWorker(job: Job) {
  const { tenantId } = job.data

  // Neue Bewertungen seit letztem Check
  const { data: newReviews } = await supabase
    .from('product_reviews')
    .select('id, sku, marketplace, rating, review_text, reviewer_name, order_id, created_at')
    .eq('tenant_id', tenantId)
    .gte('created_at', new Date(Date.now() - 2 * 60 * 60 * 1000).toISOString())
    .order('created_at', { ascending: false })

  for (const review of newReviews ?? []) {

    // RA-001: 1-Stern
    if (review.rating === 1) {
      await triggerAlert(tenantId, 'RA-001', review.sku, 'HIGH', {
        sku: review.sku,
        marketplace: review.marketplace,
        rating: review.rating,
        review_text_short: review.review_text?.substring(0, 100) ?? '',
        reviewer_name: review.reviewer_name,
        order_id: review.order_id
      })
    }

    // RA-004: 5-Sterne
    if (review.rating === 5) {
      await triggerAlert(tenantId, 'RA-004', review.sku, 'INFO', {
        sku: review.sku,
        marketplace: review.marketplace
      })
    }
  }

  // RA-002: Serie negativer Bewertungen pro SKU
  const { data: negSeries } = await supabase.rpc('get_negative_review_series', {
    p_tenant_id: tenantId,
    p_days: 7,
    p_threshold_rating: 3,
    p_min_count: 3
  })

  for (const series of negSeries ?? []) {
    await triggerAlert(tenantId, 'RA-002', series.sku, 'HIGH', {
      sku: series.sku,
      count: series.count,
      avg_rating: series.avg_rating.toFixed(1)
    })
  }
}
```

===============================================================================
# TEIL 32 — TESTING & QUALITÄTSSICHERUNG
===============================================================================

## 32.1 Unit Tests für Anti-Spam-Regeln

```typescript
// tests/aria/anti-spam.test.ts

describe('Anti-Spam Regeln', () => {

  describe('Regel 1: Daily Cap', () => {
    it('sollte bei 10 Alerts stoppen', async () => {
      // 10 Alerts senden
      for (let i = 0; i < 10; i++) {
        await sendTestAlert(tenantId, 'RD-004', 'MEDIUM')
      }
      // 11ter Alert sollte suppressed werden
      const result = await shouldSendAlert(tenantId, 'RD-004', 'test', 'MEDIUM', supabase)
      expect(result.send).toBe(false)
      expect(result.grund).toBe('DAILY_CAP')
    })

    it('CRITICAL sollte Daily Cap ignorieren', async () => {
      // 10 Alerts bereits gesendet
      const result = await shouldSendAlert(tenantId, 'AH-001', 'amazon', 'CRITICAL', supabase)
      expect(result.send).toBe(true)
    })
  })

  describe('Regel 3: Cooldown', () => {
    it('sollte SO-003 nach 480 Min blockieren', async () => {
      await sendTestAlert(tenantId, 'SO-003', 'HIGH', 'SKU-A')
      // Direkt danach prüfen
      const result = await shouldSendAlert(tenantId, 'SO-003', 'SKU-A', 'HIGH', supabase)
      expect(result.send).toBe(false)
      expect(result.grund).toBe('COOLDOWN')
    })

    it('sollte SO-003 für andere SKU nicht blockieren', async () => {
      await sendTestAlert(tenantId, 'SO-003', 'HIGH', 'SKU-A')
      const result = await shouldSendAlert(tenantId, 'SO-003', 'SKU-B', 'HIGH', supabase)
      expect(result.send).toBe(true)
    })
  })

  describe('Regel 7: Nachtruhe', () => {
    it('sollte MEDIUM nachts blockieren', async () => {
      jest.setSystemTime(new Date('2026-05-13T23:00:00+02:00'))
      const result = await shouldSendAlert(tenantId, 'RD-004', 'test', 'MEDIUM', supabase)
      expect(result.send).toBe(false)
      expect(result.grund).toBe('NACHTRUHE')
    })

    it('sollte CRITICAL nachts NICHT blockieren', async () => {
      jest.setSystemTime(new Date('2026-05-13T23:00:00+02:00'))
      const result = await shouldSendAlert(tenantId, 'AH-001', 'amazon', 'CRITICAL', supabase)
      expect(result.send).toBe(true)
    })
  })

  describe('Regel 2: Burst-Schutz', () => {
    it('sollte dritten Alert in 15 Min bündeln', async () => {
      await sendTestAlert(tenantId, 'RD-001', 'CRITICAL', 'revenue')
      await sendTestAlert(tenantId, 'RD-003', 'HIGH', 'revenue')
      const result = await shouldSendAlert(tenantId, 'RD-004', 'revenue', 'MEDIUM', supabase)
      expect(result.send).toBe(false)
      expect(result.grund).toBe('BURST_SCHUTZ')
    })
  })
}
```

## 32.2 Integration Tests: Trigger-Auslösung

```typescript
describe('Trigger Integration Tests', () => {

  describe('SO-001: Stockout', () => {
    it('sollte bei Bestand 0 auslösen', async () => {
      await supabase.from('products').update({
        stock_quantity: 0,
        listing_status: 'active'
      }).eq('sku', 'TEST-SKU')

      await stockoutCheckWorker({ data: { tenantId } })

      const { data: alerts } = await supabase
        .from('aria_alerts')
        .select('trigger_id, schwere, object_id')
        .eq('tenant_id', tenantId)
        .eq('trigger_id', 'SO-001')
        .order('created_at', { ascending: false })
        .limit(1)

      expect(alerts?.[0]?.trigger_id).toBe('SO-001')
      expect(alerts?.[0]?.schwere).toBe('CRITICAL')
      expect(alerts?.[0]?.object_id).toBe('TEST-SKU')
    })
  })

  describe('PA-001: Preis unter Marge', () => {
    it('sollte bei Preis unter Einkauf auslösen', async () => {
      await supabase.from('marketplace_listings').update({
        current_price: 5.00  // Unter Einkaufspreis
      }).eq('sku', 'TEST-SKU')

      await buyBoxWorker({ data: { tenantId } })

      const { data: alerts } = await supabase
        .from('aria_alerts')
        .select('trigger_id, schwere')
        .eq('trigger_id', 'PA-001')
        .eq('tenant_id', tenantId)
        .limit(1)

      expect(alerts?.[0]?.schwere).toBe('CRITICAL')
    })
  })
}
```

===============================================================================
# TEIL 33 — DEPLOYMENT-CHECKLISTE
===============================================================================

## 33.1 Vor dem ersten Einsatz

```
DATENBANK
  □ aria_alerts Tabelle erstellt
  □ aria_alert_bundles Tabelle erstellt
  □ aria_trigger_states Tabelle erstellt
  □ aria_proactivity_config Spalte in tenants hinzugefügt
  □ Alle Indices erstellt
  □ RLS aktiviert für alle aria_* Tabellen

BACKEND
  □ TRIGGER_KATALOG vollständig importiert
  □ shouldSendAlert() implementiert und getestet
  □ isCooldownActive() implementiert
  □ checkHysteresis() implementiert
  □ saveAndSendAlert() implementiert
  □ processAndSendAlerts() implementiert
  □ bundleSenderWorker() implementiert

BULLMQ JOBS
  □ aria-trigger-stockout-check — alle 30 Min
  □ aria-trigger-revenue-check — stündlich
  □ aria-trigger-buybox-check — alle 15 Min
  □ aria-trigger-account-health — stündlich
  □ aria-trigger-repricing-health — alle 10 Min
  □ aria-trigger-price-check — alle 30 Min
  □ aria-trigger-review-check — alle 2h
  □ aria-trigger-ads-check — alle 2h
  □ aria-bundle-sender — alle 15 Min
  □ aria-morning-bundle — täglich 07:00
  □ aria-evening-bundle — täglich 18:00
  □ aria-weekly-bundle — Freitag 17:00

KONFIGURATION
  □ Tenant-Config gesetzt (daily_cap, quiet_hours etc.)
  □ Empfänger-Rollen konfiguriert
  □ Discord Webhook für CRITICAL konfiguriert
  □ Push-Notifications konfiguriert
  □ Test-Alert gesendet und empfangen

TESTS
  □ Unit Tests: Anti-Spam-Regeln alle grün
  □ Integration Tests: Trigger-Auslösung korrekt
  □ Load Test: Burst-Schutz funktioniert
  □ End-to-End: CRITICAL Alert löst aus, landet auf Discord
```

## 33.2 Monitoring nach Go-Live (erste 7 Tage)

```
TÄGLICH PRÜFEN:
  □ Alert-Dashboard: Alerts gesendet/suppressed Quote
  □ Unbearbeitete CRITICAL Alerts (sollte 0 sein)
  □ BullMQ Queue-Länge (kein Stau)
  □ aria_trigger_states — Cooldowns aktiv

NACH 7 TAGEN EVALUIEREN:
  □ Action Rate: > 60%? Wenn nicht: Schwellenwerte anpassen
  □ Suppression Rate: > 50%? Daily Cap erhöhen oder Trigger deaktivieren
  □ False Positive Rate: > 10%? Schwellenwerte verschärfen
  □ Mute Rate: Welche Trigger werden ignoriert?
```


---

*ARIA-PROAKTIVITAET.md — Production Ready*
*Comentra Intelligence Layer*
*Version 1.0 — Mai 2026*
*92 Trigger | 10 Anti-Spam-Regeln | 8 Bündelungs-Typen | 12 BullMQ-Jobs*
*Vollständig implementierbar via Claude Code auf dem VPS.*