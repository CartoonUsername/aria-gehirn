# ARIA-MARKTPLAETZE.md
# Amazon A10 · eBay Cassini · Otto · Kaufland
# Ranking-Faktoren, Gewichtung, Optimierungshebel, Verbotenes
# Comentra Intelligence Layer — Stand: 2025/2026
# Version: 1.0

---

# INHALTSVERZEICHNIS

```
TEIL 1   — Amazon A10 Algorithmus (vollständig)
TEIL 2   — Amazon Listing-Optimierung (pro Element)
TEIL 3   — Amazon PPC & Buy Box
TEIL 4   — Amazon Account Health & Compliance
TEIL 5   — Amazon Verbotenes & Policy
TEIL 6   — eBay Cassini Algorithmus (vollständig)
TEIL 7   — eBay Listing-Optimierung
TEIL 8   — eBay Promoted Listings & Ads
TEIL 9   — eBay Verbotenes & Policy
TEIL 10  — Otto Ranking-System
TEIL 11  — Otto Listing-Optimierung
TEIL 12  — Otto Account & Compliance
TEIL 13  — Kaufland Ranking-System
TEIL 14  — Kaufland Listing-Optimierung
TEIL 15  — Kanal-Vergleich: Ranking-Faktoren im Überblick
TEIL 16  — Kanal-übergreifende Strategien
TEIL 17  — ARIA Optimierungs-Heuristiken
TEIL 18  — Verbotenes Gesamt-Register (alle Kanäle)
```


===============================================================================
# TEIL 1 — AMAZON A10 ALGORITHMUS
===============================================================================


## 1.1 Überblick A10 vs. A9

A10 ist Amazons aktueller Suchalgorithmus (seit ca. 2021, kontinuierliche Updates bis 2026).
Gegenüber dem Vorgänger A9 hat A10 folgende fundamentale Verschiebungen vorgenommen:

| FAKTOR                     | A9 (alt)            | A10 (aktuell)                |
| -------------------------- | ------------------- | ---------------------------- |
| Externe Traffic-Gewichtung | Niedrig             | Sehr hoch                    |
| Verkäufer-Autorität        | Produktbezogen      | Account-global               |
| Organische Sales vs. PPC   | PPC stark gewichtet | Organisch stärker gewichtet  |
| Click-Through-Rate (CTR)   | Mittel              | Hoch                         |
| Off-Amazon Traffic         | Kaum relevant       | Stark positiv gewichtet      |
| Conversionrate             | Sehr hoch           | Sehr hoch (unverändert)      |
| Liefergeschwindigkeit      | Mittel              | Hoch                         |
| Preisrelevanz              | Mittel              | Mittel                       |
| Review-Qualität vs. -Menge | Menge wichtig       | Qualität + Recency wichtiger |
| Keyword-Stuffing           | Noch wirksam        | Negativ bestraft             |


## 1.2 Vollständige Ranking-Faktor-Liste mit Gewichtung

Gewichtungen sind Schätzungen basierend auf öffentlichen Tests, Branchenanalysen 2024–2026.
Amazon veröffentlicht keine offiziellen Gewichtungen.

| FAKTOR                     | GEWICHTUNG | KATEGORIE   | KURZBESCHREIBUNG                              |
| -------------------------- | ---------- | ----------- | --------------------------------------------- |
| Conversion Rate (CVR)      | ~25%       | PERFORMANCE | Käufe / Besucher. Wichtigster Einzelfaktor.   |
| Click-Through Rate (CTR)   | ~15%       | PERFORMANCE | Klicks / Impressionen in Suchergebnissen.     |
| Sales Velocity             | ~15%       | PERFORMANCE | Verkaufsgeschwindigkeit absolut + relativ.    |
| Externe Traffic-Qualität   | ~10%       | TRAFFIC     | Traffic von Google, Social, Brand-Sites.      |
| Seller Authority           | ~8%        | ACCOUNT     | Account-Alter, Verkaufshistorie, Metriken.    |
| Relevanz-Score (Keywords)  | ~8%        | RELEVANZ    | Keyword-Matching in allen Textfeldern.        |
| Preis-Wettbewerbsfähigkeit | ~5%        | PREIS       | Preis relativ zu Kategorie-Median.            |
| Review-Score & Menge       | ~5%        | SOZIAL      | Ø Rating und Anzahl aktueller Bewertungen.    |
| FBA vs. FBM                | ~4%        | LOGISTIK    | FBA hat inhärenten Ranking-Vorteil.           |
| Liefergeschwindigkeit      | ~3%        | LOGISTIK    | Prime, Same-Day, Next-Day.                    |
| Listing-Vollständigkeit    | ~2%        | INHALT      | Bilder, Bullets, A+, Tabellen.                |
| PPC-Aktivität              | ~2%        | ADS         | Indirekter Effekt durch erhöhte Sichtbarkeit. |
| Return Rate                | ~1%        | PERFORMANCE | Niedrige Retouren = positives Signal.         |
| Inventory-Verfügbarkeit    | ~1%        | LOGISTIK    | Stockouts bestrafen Ranking dauerhaft.        |
| Preishistorie              | <1%        | PREIS       | Stabile Preise > volatile Preise.             |


## 1.3 Conversion Rate — Detailanalyse


### Was beeinflusst die CVR direkt


| ELEMENT                | CVR-EINFLUSS   | HEBEL                                                  |
| ---------------------- | -------------- | ------------------------------------------------------ |
| Hauptbild (Hero Image) | Sehr hoch      | Hochauflösend, weißer Hintergrund, Produkt >85% Fläche |
| Preis incl. Versand    | Sehr hoch      | Unter Wettbewerber-Median oder nahe dran               |
| Prime-Badge sichtbar   | Hoch           | FBA oder Seller Fulfilled Prime                        |
| Anzahl Bewertungen     | Hoch           | Erste 15 Bewertungen kritisch für neue Listings        |
| Ø Bewertungsscore      | Hoch           | < 4.0: signifikanter CVR-Verlust                       |
| Bulletpoints Qualität  | Mittel-Hoch    | Top-3 Bullets entscheiden. Benefit-first.              |
| A+ Content vorhanden   | Mittel         | +3–10% CVR laut Amazon-eigenen Studien                 |
| Videocontent           | Mittel         | +5–12% CVR wenn relevant und kurz (<60s)               |
| Anzahl Bilder          | Mittel         | 7 Bilder optimal. < 4: messbar schlechter.             |
| Lieferdatum sichtbar   | Mittel         | Konkrete Datumsangabe > 'in 2-3 Tagen'                 |
| Frage & Antwort (Q&A)  | Niedrig-Mittel | Beantwortet kaufrelevante Fragen proaktiv              |
| Produktbeschreibung    | Niedrig        | Wird wenig gelesen — aber für SEO relevant             |


### CVR-Benchmarks nach Kategorie (DACH 2024/2025)


| KATEGORIE           | SCHLECHTE CVR | DURCHSCHNITT | GUTE CVR | TOP 10% |
| ------------------- | ------------- | ------------ | -------- | ------- |
| Möbel & Wohnen      | < 3%          | 5–8%         | 10–15%   | > 18%   |
| Outdoor & Garten    | < 4%          | 6–10%        | 12–18%   | > 22%   |
| Küche & Haushalt    | < 5%          | 8–12%        | 15–20%   | > 25%   |
| Büro & Schreibwaren | < 5%          | 7–11%        | 13–18%   | > 22%   |
| Spielzeug & Spiele  | < 4%          | 6–10%        | 12–17%   | > 21%   |
| Heimwerken          | < 3%          | 5–8%         | 10–14%   | > 18%   |
| Elektronik-Zubehör  | < 6%          | 10–15%       | 18–25%   | > 30%   |


## 1.4 Sales Velocity — Detailanalyse

Amazon misst Sales Velocity auf mehreren Zeitfenstern gleichzeitig.

| ZEITFENSTER               | GEWICHTUNG | BESCHREIBUNG                        |
| ------------------------- | ---------- | ----------------------------------- |
| Letzte 24 Stunden         | Hoch       | Tages-Momentum. Wichtig bei Events. |
| Letzte 7 Tage             | Sehr hoch  | Haupt-Velocity-Fenster für BSR.     |
| Letzte 30 Tage            | Hoch       | Monatliche Konsistenz.              |
| Letzte 90 Tage            | Mittel     | Saisonale Einordnung.               |
| Letzte 365 Tage           | Niedrig    | Jahres-Baseline.                    |
| Gleicher Zeitraum Vorjahr | Mittel     | Saisonaler Faktor.                  |


**Kritisch:** Velocity-Einbrüche durch Stockouts werden dauerhaft bestraft.
Amazon 'erinnert sich' an Stockout-Perioden. Ranking-Erholung dauert 4–8 Wochen.

```
STOCKOUT-STRAFE (empirisch beobachtet):
  1–2 Tage Stockout:   Ranking-Verlust -20 bis -40 Positionen
  3–7 Tage Stockout:   Ranking-Verlust -50 bis -80 Positionen
  > 7 Tage Stockout:   Ranking-Verlust kann vollständig sein
  Erholungszeit:       Ø 4–8 Wochen bei normalem Absatz
  FBA-Speziell:        FBA-Stockout bestraft stärker als FBM-Stockout
```


## 1.5 Seller Authority

A10 bewertet nicht nur das einzelne Produkt, sondern den gesamten Account.

| AUTHORITY-FAKTOR           | GEWICHTUNG  | ANMERKUNG                                      |
| -------------------------- | ----------- | ---------------------------------------------- |
| Account-Alter              | Mittel      | Accounts > 2 Jahre haben Basis-Vertrauensbonus |
| Verkaufsvolumen historisch | Hoch        | Lifetime Sales im Account                      |
| Account Health Score       | Sehr hoch   | ODR, LSR, Valid Tracking Rate                  |
| Bewertungs-Konsistenz      | Mittel      | Gleichmäßige Bewertungen > Spikes              |
| Policy Violation History   | Kritisch    | Frühere Verstöße wirken langfristig            |
| Brand Registry Mitglied    | Mittel-Hoch | +Trust, Zugang zu A+, Vine, Brand Analytics    |
| Anzahl aktiver ASINs       | Niedrig     | Breites Portfolio minimal positiv              |
| Rücksendungsquote Account  | Mittel      | Account-weite Retourenrate bewertet            |
| Customer Response Time     | Mittel      | < 24h Antwortzeit positiv                      |
| Perfect Order Percentage   | Hoch        | Bestellungen ohne Probleme / Gesamt            |


## 1.6 Externer Traffic — A10-Besonderheit

A10 ist der erste Amazon-Algorithmus der externe Traffic-Qualität stark gewichtet.

```
TRAFFIC-QUELLEN nach positivem Einfluss auf A10-Ranking:

1. SEHR POSITIV
   - Google Organic (SEO) → direkt zur ASIN
   - Pinterest, Instagram → direkte ASIN-Links
   - E-Mail-Kampagnen → ASIN-Links
   - Eigene Website → Amazon-Links

2. POSITIV
   - YouTube (Video mit Link in Beschreibung)
   - Facebook Organic Posts
   - Influencer-Kooperationen mit direktem Link
   - Amazon Posts

3. NEUTRAL bis LEICHT POSITIV
   - Google Shopping Ads → Amazon
   - Facebook Ads → Amazon (bezahlter Traffic weniger gewichtet)

4. NICHT NACHWEISBAR POSITIV
   - Direktaufrufe ohne Referrer
   - VPN/Inkognito-Traffic

WICHTIG: Amazon kann Referrer und Traffic-Qualität messen.
Manipulierter Traffic (Bots, gekaufte Klicks) wird erkannt und bestraft.
```


## 1.7 Keyword-Relevanz im A10


### Keyword-Felder und ihre Gewichtung


| FELD                          | ZEICHENLIMIT        | GEWICHTUNG     | BESONDERHEIT                          |
| ----------------------------- | ------------------- | -------------- | ------------------------------------- |
| Produkttitel                  | 200 Byte            | Sehr hoch      | Erste ~80 Zeichen sichtbar in Suche   |
| Backend Keywords              | 250 Byte            | Hoch           | Nicht öffentlich sichtbar. Kein Spam. |
| Bullet Points (5x)            | 500 Byte/Bullet     | Hoch           | Erste Bullet am wichtigsten           |
| Produktbeschreibung           | 2000 Zeichen        | Mittel         | Wenn kein A+; sonst durch A+ ersetzt  |
| A+ Content                    | Kein direktes Limit | Mittel         | Indirekter SEO-Effekt durch CVR       |
| Markenname                    | —                   | Mittel         | Brand-Keyword immer indexiert         |
| Varianten-Titelfelder         | —                   | Niedrig        | Parent-Listing vererbt etwas Relevanz |
| Subject Matter / Intended Use | 50 Byte/Feld        | Niedrig-Mittel | Flat File Attribute                   |
| Suchbegriffe Felder           | 250 Byte            | Hoch           | = Backend Keywords                    |
| Q&A-Antworten                 | —                   | Niedrig        | Indexiert, aber schwach gewichtet     |



### Keyword-Typen und Strategie


| TYP                  | BESCHREIBUNG                                     | STRATEGIE                               |
| -------------------- | ------------------------------------------------ | --------------------------------------- |
| Head Keywords        | 1–2 Wörter, hohes Volumen, hoher Wettbewerb      | Im Titel, organisch ranken langfristig  |
| Mid-Tail Keywords    | 2–3 Wörter, mittleres Volumen                    | Im Titel + Bullets + Backend            |
| Long-Tail Keywords   | 4+ Wörter, niedriges Volumen, hoch konvertierend | Backend Keywords, Bullets, Beschreibung |
| Competitor Keywords  | Wettbewerber-Marken                              | Backend Keywords (wo erlaubt)           |
| Negative Keywords    | Irrelevante Suchen ausschließen                  | Im PPC, nicht im Listing                |
| Spanish/Multilingual | Andere Sprachen                                  | Backend für DACH mit AT/CH Kunden       |
| Seasonal Keywords    | Weihnachten, Ostern, Sommer                      | Titel für Peak anpassen                 |
| Problem Keywords     | 'Quietschende Treppe verhindern'                 | Beschreibung + A+ Content               |


### Keyword-Verbotenes (wird bestraft)

```
NICHT verwenden im Titel/Bullets/Backend:
  ✗ Preise oder Aktionshinweise ('Jetzt nur 19,99€')
  ✗ Verfügbarkeitsangaben ('Auf Lager')
  ✗ Zeitliche Angaben ('Neu 2025')
  ✗ Subjektive Qualitätsangaben ('Beste Qualität', 'Premium')
  ✗ Wettbewerber-Markennamen im Titel/Bullets (Backend eingeschränkt erlaubt)
  ✗ Amazon eigene Marken ('Amazon', 'Alexa', 'Kindle')
  ✗ Wiederholungen desselben Keywords (kein Vorteil, aber Platzverschwendung)
  ✗ HTML-Zeichen im Backend
  ✗ Offensive oder anstößige Begriffe
  ✗ ASIN-Nummern fremder Produkte
```


## 1.8 BSR (Best Seller Rank) — Mechanik


```
BSR wird berechnet aus:
  • Primär: Verkaufsvolumen der letzten Stunden (stark gewichtet)
  • Sekundär: Verkaufsvolumen der letzten 24h, 7d, 30d

BSR AKTUALISIERUNG:
  • Jede Stunde bei aktiven Verkäufen
  • Alle 12h bei inaktiven Listings

BSR VERERBUNG:
  • Hauptkategorie BSR
  • Unterkategorie BSR (kann mehrere haben)
  • Parent-Listing BSR = kombiniert aus Varianten

BSR BEDEUTUNG (ungefähre Verkaufsmengen Amazon.de):
  BSR  #1        → ~100–500 Verkäufe/Tag (kategoriespezifisch)
  BSR  #100      → ~30–100 Verkäufe/Tag
  BSR  #1.000    → ~10–30 Verkäufe/Tag
  BSR  #10.000   → ~2–10 Verkäufe/Tag
  BSR  #100.000  → ~1 Verkauf alle 2–5 Tage
  BSR  #1.000.000→ Sehr selten, fast kein organisches Ranking
```


===============================================================================
# TEIL 2 — AMAZON LISTING-OPTIMIERUNG PRO ELEMENT
===============================================================================


## 2.1 Produkttitel — Vollständige Regeln


| ASPEKT              | REGEL                                                               | BEISPIEL / ANMERKUNG                           |
| ------------------- | ------------------------------------------------------------------- | ---------------------------------------------- |
| Zeichenlimit        | 200 Byte (nicht Zeichen)                                            | Umlaute = 2 Byte. Praxistipp: max. 150 Zeichen |
| Erste 80 Zeichen    | Wichtigste Keywords + Marke                                         | Sichtbar in Suchergebnissen ohne Abschneiden   |
| Format              | [Marke] + [Hauptkeyword] + [Wichtigstes Feature] + [Größe/Variante] | Standard-Struktur                              |
| Großschreibung      | Jedes Hauptwort groß                                                | Amazon-Standard: 'Holz Sandkasten 150 cm'      |
| Zahlen              | Ziffern statt Wörter                                                | '150 cm' nicht 'einhundertfünfzig Zentimeter'  |
| Trennzeichen        | | oder – oder , erlaubt                                             | Nicht übertreiben (max. 2–3 im Titel)          |
| Maßeinheiten        | Immer angeben bei physischen Produkten                              | cm, kg, Liter, Stück                           |
| Marke immer vorne   | Außer Eigenmarke ohne Recognition                                   | Bei starker Marke: ganz vorne                  |
| Keine Sonderzeichen | !, ?, $, #, @ vermeiden                                             | Kann zur Ablehnung führen                      |
| Keyword-Reihenfolge | Wichtigstes Keyword ganz vorne                                      | Amazon indexiert alle, aber Position zählt     |



### Titel-Formeln nach Produkttyp

```
MÖBEL / HOLZPRODUKTE:
  [Marke] [Produkt] [Hauptkeyword] [Material] [Maß] [Farbe/Finish]
  Beispiel: 'CLAMARO Sandkasten Holz 150x150cm Fichtenholz mit Deckel'

ELEKTRONIK-ZUBEHÖR:
  [Marke] [Produkt] [Kompatibilität] [Hauptfeature] [Specs]
  Beispiel: 'Brand Laptop-Ständer Aluminium verstellbar 10-17 Zoll ergonomisch'

AKUSTIK / SCHALLSCHUTZ:
  [Marke] [Produkt] [Hauptkeyword] [Stückzahl] [Maß] [Material]
  Beispiel: 'Brand Akustikpaneele Schallschutz 12er-Set 30x30cm Filz Büro'

HAUSHALT / KÜCHE:
  [Marke] [Produkt] [Hauptvorteil] [Material] [Größe]
  Beispiel: 'Brand Schneidebrett Bambus antibakteriell 40x25cm mit Saftrille'

KINDERSPIELZEUG:
  [Marke] [Produkt] [Altersangabe] [Hauptkeyword] [Material]
  Beispiel: 'Brand Holzpuzzle ab 3 Jahre Lernspielzeug 100-teilig FSC-Holz'
```


## 2.2 Bullet Points — Vollständige Regeln


| BULLET   | FUNKTION                          | STRUKTUR                    | ZEICHENEMPFEHLUNG |
| -------- | --------------------------------- | --------------------------- | ----------------- |
| Bullet 1 | Hauptvorteil / USP                | FEATURE: Benefit-Erklärung  | 80–120 Zeichen    |
| Bullet 2 | Zweiter USP / Qualität            | MATERIAL/QUALITÄT: Details  | 80–120 Zeichen    |
| Bullet 3 | Anwendungsfall / Zielgruppe       | FÜR: Wer nutzt es, wofür    | 80–120 Zeichen    |
| Bullet 4 | Technische Details / Maße         | MASSE/LIEFERUMFANG: Konkret | 80–120 Zeichen    |
| Bullet 5 | Garantie / Service / Besonderheit | SERVICE: Garantie, Kontakt  | 80–120 Zeichen    |



### Bullet-Formeln

```
FORMEL A — Feature-Benefit:
  [FEATURE IN CAPS]: [Konkreter Nutzen für den Käufer]
  Beispiel: 'STABILES FICHTENHOLZ 26MM: Deutlich robuster als Standard-Sandkästen.
  Widersteht Wind und Wetter ohne zu splittern oder zu verziehen.'

FORMEL B — Problem-Solution:
  [PROBLEM des Käufers]: [Wie dieses Produkt das löst]
  Beispiel: 'KEIN LÄRM MEHR IM BÜRO: Die 50mm dicken Akustikpaneele schlucken
  bis zu 65% der Schallwellen und verwandeln laute Räume in ruhige Arbeitszonen.'

FORMEL C — Spezifikations-Bullet:
  [KATEGORIE]: Maß1 x Maß2 x Maß3 | Material | Gewicht | Lieferinhalt
  Beispiel: 'LIEFERUMFANG & MAßE: 12 Akustikpaneele (je 30x30x5cm) |
  Halterungen | Montageanleitung | Gesamtgewicht ca. 2,4 kg'
```


## 2.3 Produktbilder — Vollständige Regeln


| BILD-SLOT          | INHALT                             | TECHNISCHE ANFORDERUNG               | STRATEGISCHER TIPP                    |
| ------------------ | ---------------------------------- | ------------------------------------ | ------------------------------------- |
| Hauptbild (MAIN)   | Produkt allein, weißer Hintergrund | Min. 1000x1000px, JPEG, >85% Produkt | Zoomfähig: min. 1600x1600px empfohlen |
| Bild 2             | Alle Inhalte/Varianten sichtbar    | Weißer oder neutraler BG erlaubt     | Lieferumfang zeigen                   |
| Bild 3             | Produkt im Einsatz (Lifestyle)     | Echter Einsatz, echte Menschen       | Zielgruppe ansprechend abbilden       |
| Bild 4             | Detail-Shots / Material            | Textur, Verarbeitung, Close-up       | Qualitätssignal                       |
| Bild 5             | Maß-Grafik / Infografik            | Text erlaubt, Maße einzeichnen       | Käufer-Fragen vorab beantworten       |
| Bild 6             | Vergleich / Varianten              | Mehrere Versionen nebeneinander      | Upsell-Potential                      |
| Bild 7             | USP-Grafik / Feature-Highlight     | Icons + Text erlaubt                 | Top-3 Benefits visuell                |
| Bild 8+ (optional) | Zertifikate, Materialtests, Awards | Glaubwürdigkeit                      | Vertrauen aufbauen                    |
| Video (optional)   | Kurzes Produkt-Demo-Video          | Max. 30s–3min, MP4, HD               | +8–15% CVR messbar                    |



### Bild-Verbotenes

```
NICHT erlaubt im Hauptbild:
  ✗ Farbiger Hintergrund
  ✗ Accessoires/Props die nicht im Lieferumfang sind
  ✗ Wasserzeichen oder Logos
  ✗ Text, Grafiken, Pfeile
  ✗ Mehrere Produkte (außer bei Set-ASINs)
  ✗ Menschliche Modelle (außer Bekleidung/Schmuck)

NICHT erlaubt in anderen Bildern:
  ✗ Wettbewerber-Logos oder -Produkte
  ✗ Preise oder Aktionshinweise
  ✗ Claims die nicht verifizierbar sind
  ✗ Falsche Maßstäbe (Produkt größer/kleiner darstellen)
  ✗ Amazon-Logo oder Prime-Logo
  ✗ Prominente Person ohne Freigabe
```


## 2.4 A+ Content (Enhanced Brand Content)


| MODUL-TYP                    | BESCHREIBUNG                     | WANN NUTZEN                 |
| ---------------------------- | -------------------------------- | --------------------------- |
| Standard Headline + Text     | Überschrift + Fließtext          | Produktgeschichte erzählen  |
| Text + Bild links/rechts     | Side-by-side Layout              | Feature-Benefit visuell     |
| Vergleichstabelle            | Bis zu 6 Produkte vergleichen    | Varianten oder Portfolio    |
| 4-Bilder-Grid                | 2x2 Grid mit Text                | Anwendungsfälle             |
| Großes Bild + Text           | Hero-Bild Format                 | Marken-Lifestyle            |
| Bullet-Liste mit Bildern     | Icon + Kurzbeschreibung          | Technische Features         |
| Premium A+ (Brand Exclusive) | Video + interaktiv + mehr Module | Nur große Brands/hohe Sells |


```
A+ CONTENT FAKTEN:
  • Nur für Brand-registrierte Verkäufer verfügbar
  • Ersetzt die Standard-Produktbeschreibung komplett
  • Nicht direkt von Amazon-SEO indexiert (indirekt über CVR-Effekt)
  • Durchschnittliche CVR-Steigerung: +3% bis +10% (Amazon interne Daten)
  • Maximale Modulanzahl Standard A+: 7 Module
  • Video in A+ deutlich höherer Lift als Bild-only
  • Ladezeit von A+ beeinflusst Mobile CVR negativ wenn zu komplex
```


## 2.5 Backend Keywords — Vollständige Regeln

```
REGELN FÜR BACKEND KEYWORDS (Subject Matter / Search Terms):

  LIMIT:         250 Byte total (alle 5 Felder zusammen = 250 Byte)
                 ODER 250 Byte pro Feld (je nach Kategorie, variiert)
                 Praxis: 250 Byte pro Feld ist Standard für DACH

  FORMAT:
    • Keywords durch Leerzeichen trennen (kein Komma, kein Semikolon)
    • Kleinschreibung ist okay (Groß/Klein spielt keine Rolle)
    • Keine Wiederholungen von Keywords die bereits im Titel sind
    • Synonyme, Alternativschreibweisen, Tippfehler eintragen
    • Andere Sprachen für internationale Käufer

  WAS REIN SOLL:
    ✓ Synonyme ('Sandkiste' wenn Titel 'Sandkasten' hat)
    ✓ Alternativschreibweisen ('Schallschutzplatten', 'Schallschutz Platten')
    ✓ Häufige Tippfehler (selten nötig — Amazon toleriert kleine Tippfehler)
    ✓ Englische Keywords bei multinationalem Produkt
    ✓ Regionalbegriffe ('Garten', 'Spielplatz', 'Kinderzimmer')
    ✓ Anwendungskeywords ('für draußen', 'wetterfest', 'FSC zertifiziert')
    ✓ Material-Keywords ('Fichtenholz', 'Massivholz', 'Naturholz')

  WAS NICHT REIN SOLL:
    ✗ Wettbewerber-Markennamen (Policy-Verstoß, kann zu Suspendierung führen)
    ✗ Wiederholungen aus Titel/Bullets (verschwendeter Platz)
    ✗ ASINs oder EANs
    ✗ Falsche Produktkategorien
    ✗ Anstößige Begriffe
    ✗ Irreführende Keywords
```


===============================================================================
# TEIL 3 — AMAZON PPC & BUY BOX
===============================================================================


## 3.1 Sponsored Products — Relevanz-Score & Ad Rank


| FAKTOR          | GEWICHTUNG AD RANK | BESCHREIBUNG                                  |
| --------------- | ------------------ | --------------------------------------------- |
| Gebot (CPC Bid) | ~40%               | Maximales CPC-Gebot des Werbetreibenden       |
| Relevanz-Score  | ~35%               | Keyword-Relevanz des Listings                 |
| Historische CTR | ~15%               | Klickrate bei diesem Keyword in Vergangenheit |
| Historische CVR | ~10%               | Conversionrate bei diesem Keyword             |



### Kampagnen-Typen und wann welcher


| KAMPAGNEN-TYP       | BESTE NUTZUNG                   | VORTEIL                                | NACHTEIL                         |
| ------------------- | ------------------------------- | -------------------------------------- | -------------------------------- |
| Auto-Kampagne       | Keyword-Research, Neuprodukte   | Findet unbekannte Keywords automatisch | Wenig Kontrolle über Ausgaben    |
| Manual Broad Match  | Reichweite, Long-Tail-Discovery | Trifft viele Variationen               | Viele irrelevante Klicks möglich |
| Manual Phrase Match | Balance Reichweite/Kontrolle    | Nur wenn Phrase enthalten              | Mittlere Kontrolle               |
| Manual Exact Match  | Bewährte Keywords skalieren     | Höchste Kontrolle, beste ROAS          | Geringe Reichweite               |
| Product Targeting   | Wettbewerber-ASINs angreifen    | Direkt auf ähnliche Produkte zeigen    | Nur auf Produktseiten            |
| Sponsored Brands    | Markenaufbau, Awareness         | Headline-Platzierung oben              | Höherer CPC                      |
| Sponsored Display   | Retargeting, Off-Amazon         | Verlässt Amazon-Ökosystem              | Niedrigere CVR                   |


## 3.2 Buy Box Algorithmus


| FAKTOR              | GEWICHTUNG | BESCHREIBUNG                                       |
| ------------------- | ---------- | -------------------------------------------------- |
| Fulfillment-Methode | ~30%       | FBA > SFP > FBM. FBA hat starken Vorteil.          |
| Preis (landed)      | ~25%       | Inkl. Versand. Nicht zwingend günstigster gewinnt. |
| Shipping Time       | ~20%       | Schnellere Lieferung = höhere Buy-Box-Chance       |
| Seller Performance  | ~15%       | ODR, LSR, Feedback Score                           |
| Verfügbarkeit       | ~10%       | Bestand > 0, nicht gestaut                         |


```
BUY BOX FAKTEN:
  • ~82% aller Amazon-Verkäufe gehen über die Buy Box
  • FBA-Verkäufer gewinnen Buy Box auch bei 10–15% höherem Preis als FBM
  • Amazon-eigene Produkte haben Buy Box-Vorteil
  • Buy Box-Rotation: mehrere Anbieter teilen sich zeitweise die Box
  • Neuer Seller ohne Feedback: 3–6 Monate braucht es oft für erste Buy Box

BUY BOX VERLUST-GRÜNDE (häufigste):
  1. Preis zu hoch vs. Wettbewerber
  2. ODR-Metrik verschlechtert
  3. Lieferzeit zu lang (FBM ohne SFP)
  4. Negativer Feedback-Spike
  5. Stockout
  6. Repricing-Regel fehlerhaft
```


## 3.3 Repricing-Strategie


| STRATEGIE               | FUNKTIONSWEISE                         | WANN                                | RISIKO             |
| ----------------------- | -------------------------------------- | ----------------------------------- | ------------------ |
| Buy Box Winner          | Geht auf Preis der gerade Buy Box hat  | Wenn Konkurrenz vorhanden           | Preiskampf-Spirale |
| Competitive (Beat by X) | Immer X€/% unter Wettbewerber          | Aggressiver Marktanteil             | Marge gefährdet    |
| Seasonal Boost          | Preiserhöhung in Peak-Zeiten           | Q4, Events, OOS Wettbewerb          | Saisonale Nutzung  |
| Velocity-Based          | Erhöht Preis wenn Sales-Rate hoch      | Eigenmarken ohne starke Konkurrenz  | Komplex            |
| Floor & Ceiling         | Preis bewegt sich nur zwischen Min/Max | Sicherheitsnetz für alle Strategien | Empfohlen immer    |


```
REPRICING-REGELN FÜR COMENTRA:

  PFLICHT-REGELN (immer aktiv):
    1. MIN_PRICE = Einkaufspreis + Mindestmarge (konfigurierbar pro Produkt)
    2. MAX_PRICE = Marktpreis-Cap (z.B. +30% über Wettbewerber-Median)
    3. Keine Preisänderung wenn Stockout < 3 Tage
    4. Keine Preisänderung um > 15% in einer Stunde
    5. Preisänderungen nur während Betriebszeiten (nicht 22:00-07:00)

  EMPFOHLENE KONFIGURATION EmsCraft24:
    Amazon:   Buy Box Winner +0.01€ (unter Wettbewerber), Floor = Marge
    eBay:     Competitive -2% unter Marktpreis, Floor = Marge
    Otto:     Stabiler Preis, manuelle Anpassung quartalsweise
```


===============================================================================
# TEIL 4 — AMAZON ACCOUNT HEALTH & COMPLIANCE
===============================================================================


## 4.1 Performance-Metriken und Schwellen


| METRIK                      | ZIEL   | WARNUNG | KRITISCH (Sperr-Risiko) | MESSZEITRAUM   |
| --------------------------- | ------ | ------- | ----------------------- | -------------- |
| Order Defect Rate (ODR)     | < 1%   | > 0.75% | > 1.0%                  | 60 Tage        |
| Pre-Fulfillment Cancel Rate | < 2.5% | > 2.0%  | > 2.5%                  | 7 Tage         |
| Late Shipment Rate (LSR)    | < 4%   | > 3.0%  | > 4.0%                  | 10/30 Tage     |
| Valid Tracking Rate (VTR)   | > 95%  | < 95%   | < 90%                   | 30 Tage        |
| Negative Feedback           | < 5%   | > 3%    | > 10% in 30 Tagen       | 30/90/365 Tage |
| A-to-Z Claim Rate           | < 1%   | > 0.5%  | > 1%                    | 60 Tage        |
| Chargeback Rate             | < 1%   | > 0.5%  | > 1%                    | 60 Tage        |



## 4.2 ODR-Bestandteile im Detail


| KOMPONENTE                        | BEITRAG ZU ODR            | WIE REDUZIEREN                              |
| --------------------------------- | ------------------------- | ------------------------------------------- |
| Negative Bewertungen (1–2 Sterne) | Anteil an Gesamt-Orders   | CVR hoch halten, Qualität sichern, Response |
| A-to-Z-Garantieansprüche          | Jeder bestätigte Anspruch | Proaktiv mit Kunden lösen bevor Eskalation  |
| Credit Card Chargebacks           | Jeder bestätigte CB       | Käufer-Kommunikation, schnelle Rückgabe     |


## 4.3 Plan of Action (POA) — Struktur

Wenn Amazon den Account sperrt oder eine Aufforderung zum POA kommt:

```
PLAN OF ACTION STRUKTUR (bewährt für Amazon DACH):

1. ROOT CAUSE ANALYSIS
   'Wir haben den Grund für den Verstoß identifiziert als:'
   - Konkret benennen, keine Ausreden
   - Nicht Amazon beschuldigen

2. IMMEDIATE CORRECTIVE ACTIONS
   'Wir haben folgende sofortige Maßnahmen ergriffen:'
   - Was wurde bereits getan (mit Datum)
   - Konkret und messbar

3. PREVENTIVE MEASURES
   'Um dies in Zukunft zu verhindern haben wir:'
   - Prozessänderungen
   - Schulungsmaßnahmen
   - Monitoring-Maßnahmen

4. METRICS/EVIDENCE
   'Als Nachweis fügen wir bei:'
   - Screenshots, Lieferbelege, Kommunikation

WICHTIG:
  - Kurz und sachlich (max. 1 Seite)
  - Keine Emotionen, keine Entschuldigungen
  - Innerhalb von 72h einreichen
  - Bei Ablehnung: verbessert nochmal einreichen (nicht aufgeben)
```


===============================================================================
# TEIL 5 — AMAZON VERBOTENES & POLICY
===============================================================================


## 5.1 Absolute Verbote (sofortige Suspendierung möglich)


```
KRITISCHE VERSTÖSSE — SOFORTIGE SPERRUNG MÖGLICH:

  BEWERTUNGSMANIPULATION:
  ✗ Bewertungen kaufen oder gegen Belohnungen tauschen
  ✗ Negative Bewertungen von Wettbewerbern beauftragen
  ✗ Eigene Bewertungen schreiben oder von Familienmitgliedern
  ✗ Kunden direkt um positive Bewertungen bitten (erlaubt: Neutral bitten)
  ✗ Vine-Reviews manipulieren oder selektieren

  PREIS-VERSTÖSSE:
  ✗ Preisparität mit anderen Plattformen verletzen (Amazon kann günstiger fordern)
  ✗ Konsumenten-freundliche Preisangaben auf Listings falsch darstellen

  LISTING-VERSTÖSSE:
  ✗ ASIN-Missbrauch (Hauptkategorie/Listing für anderes Produkt übernehmen)
  ✗ Counterfeit-Produkte (gefälschte Markenprodukte)
  ✗ Intellectual Property Violations (fremde Markennamen, Logos)
  ✗ Verbotene Produkte listen (je nach Kategorie verschieden)

  ACCOUNT-VERSTÖSSE:
  ✗ Mehrere Seller-Accounts ohne Genehmigung
  ✗ Suspendierter Account durch andere Person weiterführen
  ✗ Falsche Identität im Account
  ✗ Steuer-/Firmenangaben falsch oder veraltet

  KOMMUNIKATIONS-VERSTÖSSE:
  ✗ Käufer außerhalb Amazon-Systems kontaktieren (keine Emails direkt)
  ✗ Off-Amazon-Angebote in Nachrichten erwähnen
  ✗ Rabatte oder Coupons in Buyer-Messages anbieten
```


## 5.2 Graubereiche — erlaubt mit Einschränkungen


| THEMA                         | ERLAUBT                                       | NICHT ERLAUBT                                  |
| ----------------------------- | --------------------------------------------- | ---------------------------------------------- |
| Bewertungen anfragen          | Neutral über Seller Central Anfrage           | Direkte positive Bewertungs-Bitte              |
| Produktbeilagen               | QR-Code zu Website, Anleitung, Garantie-Karte | Direkte Bitte um Bewertung auf Beilage         |
| Käufer-Emails                 | Versandbestätigung, Lieferproblem             | Promotion, Bewertungs-Anfrage per Email        |
| Wettbewerber-Keywords Backend | Generische Synonyme                           | Markennamen der Wettbewerber                   |
| Produktvergleiche             | In A+ Content: Eigenprodukte vergleichen      | Wettbewerber-Produkte namentlich vergleichen   |
| Preisnachlässe                | Coupons, Lightning Deals, Sale-Preise         | Nur für ausgewählte Käufer / VIP-Preise        |
| Bundles                       | FBM-Bundles aus eigenen Produkten             | Fremde Markenprodukte ohne Genehmigung bündeln |


===============================================================================
# TEIL 6 — EBAY CASSINI ALGORITHMUS
===============================================================================


## 6.1 Cassini Grundprinzipien

Cassini ist eBays Suchalgorithmus (seit 2013, kontinuierliche Updates).
Grundprinzip: 'Best Match' — das relevanteste und wahrscheinlichste-zu-kaufen Produkt oben.

| PRINZIP                        | BESCHREIBUNG                                                               |
| ------------------------------ | -------------------------------------------------------------------------- |
| Käufer-zentriert               | Cassini optimiert für Käufer-Zufriedenheit, nicht für Verkäufer-Reichweite |
| Transaktionswahrscheinlichkeit | Welches Listing endet am wahrscheinlichsten in einem Kauf?                 |
| Relevanz + Performance         | Keyword-Match UND historische Performance kombiniert                       |
| Aktualität                     | Neuere Angebote bevorzugt wenn Performance gleich                          |
| Vertrauen                      | Bewerteter, erfahrener Verkäufer bevorzugt                                 |


## 6.2 Vollständige Ranking-Faktoren Cassini


| FAKTOR                    | GEWICHTUNG | KATEGORIE   | BESCHREIBUNG                            |
| ------------------------- | ---------- | ----------- | --------------------------------------- |
| Keyword-Relevanz          | ~25%       | RELEVANZ    | Titelkeywords matchen Suchanfrage exakt |
| Käufer-Zufriedenheit      | ~20%       | PERFORMANCE | Bewertungen, Disputes, Returns          |
| Listing-Qualität          | ~15%       | INHALT      | Bilder, Beschreibung, Vollständigkeit   |
| Preisattraktivität        | ~12%       | PREIS       | Preis vs. Marktmedian in Kategorie      |
| Verkäufer-Performance     | ~10%       | ACCOUNT     | Feedback Score, Response Rate, TRS      |
| Transaktions-Historie     | ~8%        | PERFORMANCE | Historische Verkäufe dieser Kategorie   |
| Listing-Alter/-Aktualität | ~5%        | AKTUALITÄT  | Kürzlich aktualisiert = leichter Boost  |
| Versandbedingungen        | ~5%        | LOGISTIK    | Kostenloser Versand, schnell            |


## 6.3 Top Rated Seller (TRS) — Voraussetzungen und Vorteile


| KRITERIUM          | ANFORDERUNG TRS         | ANFORDERUNG TRS+           |
| ------------------ | ----------------------- | -------------------------- |
| Transaktionen      | ≥ 100 in 12 Monate      | ≥ 100 in 12 Monate         |
| Umsatz             | ≥ 1.000€ in 12 Monate   | ≥ 1.000€ in 12 Monate      |
| Defect Rate        | ≤ 0.5%                  | ≤ 0.5%                     |
| Late Shipment Rate | ≤ 3%                    | ≤ 3%                       |
| Tracking Upload    | ≥ 90%                   | ≥ 95%                      |
| Return Policy      | Keine spezielle Pflicht | 30 Tage Rückgabe + Versand |
| Handling Time      | Keine spezielle Pflicht | 1-Werktag Handling         |


```
TRS VORTEILE:
  • Ranking-Boost: Empirisch 10–30% höhere Sichtbarkeit
  • TRS-Badge auf Listings (Vertrauenssignal für Käufer)
  • Niedrigere eBay-Gebühren (Rabatt auf Endwertgebühr)
  • Top-Platzierung in Best Match wenn Preis wettbewerbsfähig

TRS+ ZUSÄTZLICHE VORTEILE:
  • Noch stärkerer Ranking-Boost
  • TRS+-Badge (Premium-Vertrauenssignal)
  • Deutlich bessere Käufer-Conversion
```


## 6.4 eBay Listing-Spezifika


### Titeloptimierung eBay


| ASPEKT         | EBAY-REGEL                                 | UNTERSCHIED ZU AMAZON                       |
| -------------- | ------------------------------------------ | ------------------------------------------- |
| Zeichenlimit   | 80 Zeichen                                 | Amazon: 200 Byte — eBay viel kürzer!        |
| Format         | Keyword-fokussiert, keine Satzsyntax nötig | eBay: 'Sandkasten Holz 150cm Kinder Garten' |
| Marke          | Kann weggelassen werden                    | Amazon: Marke immer vorne empfohlen         |
| Zustand        | Im Titelfeld erlaubt ('NEU')               | Amazon: Zustand separat im Konditionsfeld   |
| Wiederholungen | Synonyme im Titel erlaubt                  | Amazon: Wiederholungen verschwenderisch     |
| Sonderzeichen  | Kaum Symbole erlaubt                       | Amazon ähnlich                              |



### Item Specifics (Kategorieattribute)

```
ITEM SPECIFICS sind bei eBay KRITISCH für Cassini-Ranking.

REGELN:
  • Alle Pflicht-Attribute vollständig ausfüllen (= Listing wird sonst schlechter gerankbt)
  • Empfohlene Attribute ebenfalls füllen (erhöht Ranking messbar)
  • Exakte Werte statt freie Texte wenn Dropdown verfügbar
  • Maßangaben in den eBay-Standard-Einheiten
  • Marken-Attribut immer ausfüllen

OHNE VOLLSTÄNDIGE ITEM SPECIFICS:
  → Listing erscheint nicht in gefilterten Suchen
  → Kein Ranking in Kategorie-spezifischen Browsing-Seiten
  → Deutlicher Ranking-Nachteil vs. vollständige Listings
```


## 6.5 eBay Defect Rate — Bestandteile


| DEFECT-TYP                             | GEWICHTUNG | WIE VERMEIDEN                                    |
| -------------------------------------- | ---------- | ------------------------------------------------ |
| Transaktions-Defects                   | Hoch       | Auf alle gemeldeten Probleme reagieren           |
| Late Shipment Rate                     | Hoch       | Handling-Time realistisch, Versand am selben Tag |
| Cases Closed Without Seller Resolution | Sehr hoch  | Immer direkt mit Käufer lösen bevor Eskalation   |
| Return Requests                        | Mittel     | Klare Listing-Beschreibung reduziert Rückgaben   |
| Item Not Received Cases                | Sehr hoch  | Tracking immer hochladen                         |


===============================================================================
# TEIL 7 — EBAY LISTING-OPTIMIERUNG
===============================================================================


## 7.1 Optimale eBay-Listing-Struktur

```
CHECKLISTE FÜR EIN TOP-GERANKTES EBAY LISTING:

TITEL (80 Zeichen):
  ✓ Hauptkeyword ganz am Anfang
  ✓ Marke wenn bekannt
  ✓ Synonyme (Sandkasten = Sandkiste)
  ✓ Maße wenn suchrelevant
  ✓ Zustand wenn 'Neu'
  ✓ Keine Füllwörter ('und', 'oder', 'mit')

BILDER:
  ✓ Hauptbild weißer/neutraler Hintergrund
  ✓ Mindestens 6 Bilder
  ✓ Mindestauflösung 1600px (für Zoom)
  ✓ Lifestyle-Bild immer dabei
  ✓ Maß-Infografik

ITEM SPECIFICS:
  ✓ ALLE Pflichtfelder ausgefüllt
  ✓ ALLE empfohlenen Felder ausgefüllt
  ✓ Marke korrekt eingetragen
  ✓ EAN/GTIN hinterlegt

BESCHREIBUNG:
  ✓ Sauberes HTML (kein externer CSS)
  ✓ Mobile-optimiert (kein horizontales Scrollen)
  ✓ Keywords natürlich eingebaut
  ✓ Vollständige Produktdetails
  ✓ Kontaktinfos NUR über eBay-System

VERSANDBEDINGUNGEN:
  ✓ Kostenloser Versand wenn möglich (Ranking-Vorteil)
  ✓ Schnelle Handling-Time (1 Werktag)
  ✓ Tracking immer hochladen

RÜCKGABEPOLITIK:
  ✓ 30 Tage Rückgabe minimum für TRS-Status
  ✓ Klare Bedingungen
```


## 7.2 Beschreibungs-HTML Best Practices

```html
<!-- ERLAUBTE HTML-ELEMENTE IN EBAY-BESCHREIBUNGEN -->

<!-- EMPFOHLEN: Strukturiertes HTML -->
<div style='font-family: Arial, sans-serif; max-width: 800px; margin: 0 auto;'>
  <h2 style='color: #333;'>Produktname — Hauptkeyword</h2>
  <p>Kurze Einleitung mit wichtigstem Benefit. Keyword natürlich eingebaut.</p>

  <h3>Features auf einen Blick</h3>
  <ul>
    <li><strong>Feature 1:</strong> Benefit-Beschreibung</li>
    <li><strong>Feature 2:</strong> Benefit-Beschreibung</li>
    <li><strong>Feature 3:</strong> Benefit-Beschreibung</li>
  </ul>

  <h3>Technische Details</h3>
  <table>
    <tr><td>Maße</td><td>150 x 150 x 25 cm</td></tr>
    <tr><td>Material</td><td>Fichtenholz 26mm</td></tr>
    <tr><td>Gewicht</td><td>18,5 kg</td></tr>
  </table>
</div>

<!-- VERBOTEN IN EBAY BESCHREIBUNGEN: -->
<!-- ✗ Externe Links (zu anderen Shops) -->
<!-- ✗ JavaScript -->
<!-- ✗ Externe CSS-Sheets -->
<!-- ✗ Pop-ups -->
<!-- ✗ Kontaktdaten außerhalb eBay-System -->
<!-- ✗ Preisangaben die nicht dem Listing-Preis entsprechen -->
```


===============================================================================
# TEIL 8 — EBAY PROMOTED LISTINGS & ADS
===============================================================================


## 8.1 Promoted Listings Standard (PLS)


| ASPEKT                | DETAIL                                                             |
| --------------------- | ------------------------------------------------------------------ |
| Gebührenmodell        | CPA (Cost per Action) — nur zahlen wenn Käufer 30 Tage-Attribution |
| Gebühren-Bereich      | 1–20% des Verkaufspreises als Ad Rate                              |
| Empfohlene Rate       | In Kategorie-Vorschlag von eBay oder +1% über Trend                |
| Ranking-Effekt        | Placement in Top-Suchergebnissen und ähnliche Produkte             |
| Auktion vs. Festpreis | Nur für Festpreisangebote verfügbar                                |
| Tracking              | Dashboard mit Impressions, Clicks, Sales                           |


## 8.2 Promoted Listings Advanced (PLA)


| ASPEKT            | DETAIL                                         |
| ----------------- | ---------------------------------------------- |
| Gebührenmodell    | CPC — zahlen pro Klick wie Google Ads          |
| Keyword-Kontrolle | Volle Keyword-Kontrolle (Broad, Phrase, Exact) |
| Budget-Kontrolle  | Tages-Budget einstellbar                       |
| Placement         | Oberste Positionen in Suchergebnissen          |
| Minimum CPC       | Variiert: typisch 0,05–0,30€ in DACH           |
| Ziel-ROAS         | Empfehlung: Ziel-ROAS mindestens 400%          |


===============================================================================
# TEIL 9 — EBAY VERBOTENES & POLICY
===============================================================================


## 9.1 Absolute Verbote eBay

```
SOFORTIGE SUSPENDIERUNG MÖGLICH:

  LISTING-VERBOTE:
  ✗ Produkte listen die noch nicht existieren / nicht auf Lager
     (eBay erlaubt kein Dropshipping aus fremden Marktplätzen)
  ✗ Counterfeit / gefälschte Markenprodukte
  ✗ Listings mit externen Links zu anderen Shops
  ✗ Preis außerhalb des Listings kommunizieren

  BEWERTUNGS-VERBOTE:
  ✗ Negative Bewertungen durch Druck entfernen lassen
  ✗ Bewertungen kaufen oder tauschen
  ✗ Shilling (sich selbst oder Verwandte bieten/kaufen lassen)

  KOMMUNIKATIONS-VERBOTE:
  ✗ Käufer zur Zahlung außerhalb eBay auffordern
  ✗ Kontaktdaten in Listings einbetten
  ✗ Off-eBay-Deals anbieten

  LISTING-MANIPULATION:
  ✗ Keyword Stuffing (gleiches Wort 3+ mal im Titel)
  ✗ Irreführende Kategorisierung
  ✗ False Urgency ('Nur noch 1 Stück!' wenn viele verfügbar)
```


===============================================================================
# TEIL 10 — OTTO RANKING-SYSTEM
===============================================================================


## 10.1 Otto Algorithmus Grundlagen

Otto.de ist Deutschlands zweitgrößter Online-Marktplatz für Non-Food.
Der Algorithmus ist proprietär und nicht offiziell dokumentiert.
Folgende Faktoren sind empirisch von Partner-Händlern bestätigt (Stand 2025):

| FAKTOR                 | GESCHÄTZTE GEWICHTUNG | BESCHREIBUNG                                  |
| ---------------------- | --------------------- | --------------------------------------------- |
| Produktqualitäts-Score | ~25%                  | Otto-internes Listing-Qualitätsrating (0–100) |
| Conversion Rate        | ~20%                  | Käufe / Produktseitenaufrufe                  |
| Retourenquote          | ~15%                  | Niedrige Retouren = starker Ranking-Boost     |
| Keyword-Relevanz       | ~12%                  | Keyword-Match in Titel und Attributen         |
| Preis-Attraktivität    | ~10%                  | Relativer Preis vs. Kategorie                 |
| Verkaufshistorie       | ~8%                   | Absolutvolumen + Wachstumstrend               |
| Händler-Qualitätsscore | ~6%                   | Lieferzeit, Stornos, Beschwerden              |
| Lieferoptionen         | ~4%                   | Expresslieferung verfügbar                    |


## 10.2 Otto Qualitäts-Score (Product Quality Score)


```
DER OTTO PRODUCT QUALITY SCORE (0–100) BERECHNET SICH AUS:

  PFLICHTFELDER (alle müssen ausgefüllt sein für > 60 Score):
  • Produkttitel (min. 40 Zeichen, max. 100 Zeichen)
  • Produktbeschreibung (min. 100 Wörter empfohlen)
  • Mindestens 4 Produktbilder
  • Hauptkategorie korrekt
  • Alle Pflicht-Attribute der Kategorie gefüllt
  • EAN/GTIN vorhanden
  • Versandinformationen vollständig

  QUALITÄTS-FEATURES (erhöhen Score von 60 auf 100):
  • 8+ Bilder (ideal: 10)
  • Beschreibung > 300 Wörter
  • Aufzählungen / strukturierter Text
  • Alle empfohlenen Attribute gefüllt
  • Video vorhanden
  • Mehrfachbilder aus verschiedenen Winkeln

  SCORE-AUSWIRKUNG AUF RANKING:
  < 60:    Listing erscheint kaum in organischen Suchergebnissen
  60-75:   Durchschnittliches Ranking
  75-85:   Überdurchschnittlich, gute Sichtbarkeit
  85-100:  Top-Ranking-Potential, höchste Sichtbarkeit
```


## 10.3 Otto Retourenquote — kritischer Faktor


| RETOURENQUOTE | RANKING-AUSWIRKUNG         | OTTO-MAßNAHMEN                               |
| ------------- | -------------------------- | -------------------------------------------- |
| < 10%         | Positiver Ranking-Boost    | Kein Eingriff                                |
| 10–15%        | Neutral                    | Kein Eingriff                                |
| 15–20%        | Negativer Einfluss         | Mögliche Qualitäts-Nachfrage                 |
| 20–30%        | Deutlicher Ranking-Verlust | Qualitätsgespräch, Verbesserungsaufforderung |
| > 30%         | Starke Ranking-Strafe      | Listing-Deaktivierung möglich                |
| > 40%         | Listing-Deaktivierung      | Zwangsdeaktivierung                          |


```
RETOUREN-MANAGEMENT OTTO:

  HAUPTGRÜNDE FÜR HOHE RETOUREN AUF OTTO:
  1. Falsches Maß / Größenangabe (häufigste Ursache)
  2. Produkterwartung nicht erfüllt (Listing-Qualitätsproblem)
  3. Materialqualität unter Erwartung
  4. Lieferdefekt (Verpackung, Transportschäden)
  5. Doppelkauf (Käufer hat zwei Varianten bestellt, eine zurück)

  HEBEL ZUR RETOUREN-SENKUNG:
  • Maßangaben extrem präzise (cm-Angaben mit Dezimalstelle)
  • Maß-Infografik im Listing (visuelle Größeneinordnung)
  • Ehrliche Produktbeschreibung (keine übertriebenen Claims)
  • Materialfotos in hoher Qualität (Textur, Oberfläche sichtbar)
  • Verpackungsqualität erhöhen (Transportschäden minimieren)
```


## 10.4 Otto Partner Connect — Pflichten


| PFLICHT-METRIK           | ZIEL-WERT             | KONSEQUENZ BEI VERFEHLUNG  |
| ------------------------ | --------------------- | -------------------------- |
| Lieferpünktlichkeit      | > 95%                 | Account-Einschränkung      |
| Stornierungsrate         | < 2%                  | Account-Einschränkung      |
| Antwortzeit Kundenfragen | < 24h Werktage        | Score-Verschlechterung     |
| Produktdaten-Qualität    | Score > 70            | Manuelle Review durch Otto |
| Retouren-Abwicklungszeit | < 7 Tage nach Eingang | Kundenbeschwerden          |


===============================================================================
# TEIL 11 — OTTO LISTING-OPTIMIERUNG
===============================================================================


## 11.1 Otto Produktdaten-Anforderungen

```
PFLICHTFELDER (ohne diese: Listing wird nicht veröffentlicht):
  • Produkttitel: 40–100 Zeichen
  • Kurzbeschreibung: 50–255 Zeichen
  • Beschreibung: keine Mindestlänge aber > 100 Wörter empfohlen
  • Hauptkategorie + Unterkategorie
  • Alle Kategorie-Pflichtattribute (variieren je Kategorie)
  • Mindestens 1 Bild (min. 1200x1200px empfohlen)
  • Preis (ohne MwSt. + mit MwSt. Angabe)
  • Versandinformationen
  • EAN/GTIN (für Markenprodukte Pflicht)

STARK EMPFOHLEN:
  • 6–10 Bilder aus verschiedenen Winkeln
  • Strukturierte Beschreibung mit Bullet Points
  • Video (wo möglich)
  • Alle empfohlenen Attribute
  • Maß-Grafik
```


## 11.2 Otto Kategorie-spezifische Anforderungen


| KATEGORIE      | SPEZIELLE PFLICHT-ATTRIBUTE                                             |
| -------------- | ----------------------------------------------------------------------- |
| Möbel          | Maße (B x H x T), Gewicht, Material, Montagepflicht, Herkunftsland      |
| Spielzeug      | Altersempfehlung, Sicherheitszertifikate, Material, Batterien (ja/nein) |
| Textilien      | Größen-Tabelle, Materialzusammensetzung, Pflegehinweise, Schnittform    |
| Elektro        | Technische Specs, CE-Kennzeichnung, Garantie, Verbrauchswerte           |
| Outdoor/Garten | Maße, Material, Wetterfestigkeit, Gewicht, Aufbauzeit                   |
| Büro/Akustik   | Maße, Material, Dämmwert (wenn vorhanden), Montageart                   |


===============================================================================
# TEIL 12 — OTTO ACCOUNT & COMPLIANCE
===============================================================================


## 12.1 Otto Händler-Qualitätsscore

```
OTTO QUALITÄTSSCORE BESTEHT AUS:

  LIEFERQUALITÄT (40%):
    • Lieferpünktlichkeit
    • Korrekte Sendungsverfolgung hochgeladen
    • Verpackungsqualität (aus Retouren-Feedback)

  KUNDENZUFRIEDENHEIT (35%):
    • Bewertungs-Durchschnitt
    • Retourenquote
    • Kundenbeschwerden

  DATENQUALITÄT (25%):
    • Product Quality Scores aller Listings
    • Aktualität der Produktdaten
    • Vollständigkeit der Attribute

KONSEQUENZEN:
  Score < 60:  Einschränkungen bei neuen Listings
  Score < 40:  Mögliche Kündigung des Partner-Vertrags
  Score > 80:  Premium-Partner-Status möglich
```


## 12.2 Otto verbotene Inhalte

```
ABSOLUT VERBOTEN AUF OTTO:
  ✗ Alkohol, Tabak, Waffen, gefährliche Güter
  ✗ Produkte ohne CE-Kennzeichnung (wenn CE-Pflicht besteht)
  ✗ Spielzeug ohne EN-71-Zertifizierung
  ✗ Counterfeit / Plagiate
  ✗ Externe Links in Produktbeschreibungen
  ✗ Werbung für andere Plattformen
  ✗ Preise die außerhalb des Otto-Systems kommuniziert werden

REGULATORISCHE PFLICHTEN (Deutschland 2025):
  ✓ GPSR (General Product Safety Regulation) — ab Dez. 2024 EU-Pflicht
  ✓ WEEE (Elektroschrott-Richtlinie) wenn relevant
  ✓ Verpackungsgesetz (LUCID-Registrierung)
  ✓ Impressumspflicht und Widerrufsbelehrung
  ✓ Preisangaben klar und vollständig (MwSt., Versand)
```


===============================================================================
# TEIL 13 — KAUFLAND RANKING-SYSTEM
===============================================================================


## 13.1 Kaufland Marketplace Grundlagen

Kaufland.de ist seit 2020 aktiver Marketplace (früher Real.de).
Vergleichsweise weniger Wettbewerb als Amazon/eBay → gute Chance für Nischenseller.
Besondere Stärke: Elektro, Haushalt, Garten, Spielzeug.

| FAKTOR                  | GEWICHTUNG | BESCHREIBUNG                             |
| ----------------------- | ---------- | ---------------------------------------- |
| Keyword-Relevanz        | ~30%       | Titelkeywords + Produktattribute         |
| Preis                   | ~25%       | Stark preis-sensitiver Markt             |
| Listing-Vollständigkeit | ~15%       | Kaufland bewertet Datenqualität explizit |
| Verkäufer-Performance   | ~15%       | Stornoquote, Lieferzeit, Beschwerden     |
| Conversion Rate         | ~10%       | Kaufrate der Produktseite                |
| Bewertungen             | ~5%        | Anzahl und Qualität                      |


## 13.2 Kaufland Seller Scorecard


| METRIK                     | ZIEL         | KRITISCH      |
| -------------------------- | ------------ | ------------- |
| Stornierungsrate           | < 1%         | > 2%          |
| Lieferzuverlässigkeit      | > 97%        | < 93%         |
| Versandzeit (nach Versand) | < 3 Werktage | > 5 Werktage  |
| Kundenbeschwerden-Rate     | < 1%         | > 3%          |
| Retourenbearbeitungszeit   | < 5 Werktage | > 10 Werktage |
| Produktdaten-Qualität      | > 80%        | < 50%         |


## 13.3 Kaufland-spezifische Besonderheiten

```
KAUFLAND BESONDERHEITEN (2025):

  PLATTFORM-CHARAKTER:
  • Stark stationärer-Handel-orientierte Kundschaft
  • Hoher Anteil Lebensmittel-adjacent Kategorie-Traffic
  • Günstigere Produkte performen besser als Premiumpreise
  • Weniger PPC-Möglichkeiten als Amazon

  TECHNICAL INTEGRATION:
  • CSV-Upload oder API (ähnlich Amazon Flat File)
  • EAN ist Pflicht — ohne EAN kein Listing
  • Produktdaten werden mit Kaufland-Stammdaten abgeglichen
  • Bei EAN-Match: Kaufland-Stammdaten überschreiben teils eigene Daten

  STRATEGIE-EMPFEHLUNGEN:
  • Preis wettbewerbsfähig halten (preissensitive Käuferschaft)
  • Versand über DHL/Hermes für schnellste Lieferzeiten
  • Produktdaten perfekt pflegen (wenig Wettbewerb = Datenqualität schlägt durch)
  • Kaufland Fulfillment (KF) nutzen wenn Volumen rechtfertigt
```


===============================================================================
# TEIL 14 — KAUFLAND LISTING-OPTIMIERUNG
===============================================================================


## 14.1 Kaufland Produktdaten-Struktur

```
PFLICHTFELDER KAUFLAND:
  • EAN / GTIN (absolut Pflicht)
  • Produktname: 80–255 Zeichen
  • Produktbeschreibung: mind. 100 Zeichen
  • Hauptbild: min. 600x600px, weißer Hintergrund bevorzugt
  • Preis: inkl. MwSt.
  • Verfügbarkeit
  • Versandinformationen
  • Kategorie-Pflichtattribute

EMPFOHLEN FÜR BESTES RANKING:
  • Produktname: 100–150 Zeichen
  • Beschreibung: 500–1500 Zeichen
  • 5–10 Bilder
  • Alle empfohlenen Kategorie-Attribute
  • Bullet Points in Beschreibung
  • Maß-Angaben präzise

KAUFLAND TITLE-FORMAT:
  [Marke] [Produktname] [Hauptattribut] [Maß/Größe] [Farbe]
  Beispiel: 'Brand Sandkasten Holz wetterfest 150x150 cm Fichtenholz'
```


## 14.2 Kaufland verbotene Inhalte

```
VERBOTEN AUF KAUFLAND:
  ✗ Produkte ohne EAN (Ausnahmen nur nach Antrag)
  ✗ Lebensmittel (separater Prozess, stark eingeschränkt)
  ✗ Gefährliche Güter ohne Sicherheitsdatenblatt
  ✗ Produkte unter Mindestpreis-Bindung ohne Nachweis
  ✗ Externe Links in Produktbeschreibungen
  ✗ Produkte mit fehlender CE-Kennzeichnung (wenn Pflicht)
  ✗ Preiswerbung ('50% OFF', 'Jetzt günstig')
  ✗ Nachahmungen / Plagiate
```


===============================================================================
# TEIL 15 — KANALVERGLEICH: RANKING-FAKTOREN
===============================================================================


## 15.1 Ranking-Faktor-Vergleich alle Kanäle


| RANKING-FAKTOR          | AMAZON A10      | EBAY CASSINI    | OTTO              | KAUFLAND          |
| ----------------------- | --------------- | --------------- | ----------------- | ----------------- |
| Keyword-Titel           | Sehr hoch       | Sehr hoch       | Hoch              | Hoch              |
| Backend Keywords        | Hoch            | Item Specifics  | Attribute         | Attribute         |
| Conversion Rate         | Sehr hoch       | Hoch            | Hoch              | Mittel            |
| Bewertungen/Score       | Hoch            | Sehr hoch       | Mittel            | Niedrig           |
| Preis                   | Mittel          | Hoch            | Hoch              | Sehr hoch         |
| Versandgeschwindigkeit  | Hoch (FBA)      | Hoch (TRS)      | Hoch              | Mittel            |
| Bild-Qualität           | Mittel-Hoch     | Mittel          | Hoch (Score)      | Mittel            |
| Externer Traffic        | Sehr hoch (A10) | Gering          | Gering            | Gering            |
| Account-Autorität       | Hoch            | Sehr hoch       | Mittel            | Mittel            |
| Listing-Vollständigkeit | Mittel          | Sehr hoch       | Sehr hoch         | Hoch              |
| Retourenquote           | Mittel          | Mittel          | Sehr hoch         | Mittel            |
| PPC/Ads                 | Indirekt mittel | Indirekt mittel | Kein direktes PPC | Kein direktes PPC |
| FBA/Fulfillment         | Sehr hoch       | TRS-relevant    | Neutral           | KF optional       |
| Aktualität des Listings | Niedrig         | Mittel          | Mittel            | Mittel            |


## 15.2 Gebühren-Vergleich (2025, DACH)


| GEBÜHREN-TYP       | AMAZON                             | EBAY                                                  | OTTO                     | KAUFLAND           |
| ------------------ | ---------------------------------- | ----------------------------------------------------- | ------------------------ | ------------------ |
| Grundgebühr/Abo    | 39€/Monat (Professional)           | 0€/Monat (Gewerblich möglich)                         | Auf Anfrage              | 0€/Monat           |
| Verkaufsprovision  | 7–15% je Kategorie                 | 5–12% + 0,35€ Grundgebühr                             | 10–20% je Kategorie      | 7–20% je Kategorie |
| FBA/Fulfillment    | 3–10€ je Sendung (volumenabhängig) | Nicht relevant (eBay hat kein FBE)                    | Kein eigenes Fulfillment | KF verfügbar       |
| Listing-Gebühr     | 0€ (Professional)                  | 0,35€ je Angebot (Auktion) / 0€ (Festpreis bis Limit) | 0€                       | 0€                 |
| Werbung            | CPC variabel                       | CPA 1–20%                                             | Keine Standard-PPC       | Keine Standard-PPC |
| Zahlungsabwicklung | Im Provisionssatz enthalten        | Im Provisionssatz enthalten                           | Im Provisionssatz        | Im Provisionssatz  |


===============================================================================
# TEIL 16 — KANALÜBERGREIFENDE STRATEGIEN
===============================================================================


## 16.1 Multi-Kanal-Bestand-Management

```
BESTAND-ALLOKATION NACH KANAL-PRIORITÄT:

  STRATEGIE A — Amazon-First:
    Amazon:   60-70% des Bestands reserviert
    eBay:     15-20%
    Otto:     10-15%
    Kaufland: 5-10%
    Wann:     Amazon ist Hauptkanal, FBA-Einlieferungen geplant

  STRATEGIE B — Balanced:
    Amazon:   40%
    eBay:     30%
    Otto:     20%
    Kaufland: 10%
    Wann:     Ähnliche Performance auf allen Kanälen

  STRATEGIE C — eBay-First:
    eBay:     50%
    Amazon:   30%
    Rest:     20%
    Wann:     Gebrauchtwaren, Auktions-Potential, höhere Margen auf eBay

ÜBERVERKAUFS-SCHUTZ:
  • Bestand in Comentra zentralisiert (Single Source of Truth)
  • Jeder Kanalverkauf zieht sofort vom Zentralbestand ab
  • Buffer: 5-10% Sicherheitspuffer unter echtem Bestand
    (ausgleich für Sync-Delays von 2-15 Minuten)
```


## 16.2 Preisparität zwischen Kanälen

```
AMAZON PREISPARITÄT:
  Amazon erwartet dass ihr Preis nicht dauerhaft höher ist als auf anderen Kanälen.
  Amazon 'scannt' bekannte Konkurrenten (auch eigene Listings auf anderen Plattformen).

  REGEL: Amazon-Preis ≤ eBay-Preis ≤ Otto-Preis ≤ Kaufland-Preis
  (oder gleiche Preise auf allen Kanälen)

  AUSNAHMEN:
    • Temporäre Sales auf Amazon (Lightning Deal, Prime Day)
    • Bundle-Preise (andere Menge/Kombination = anderer Preis zulässig)
    • Kanal-exklusive Bundles

EBAY PREISPARITÄT:
  eBay hat offiziell keine Preisparitätspflicht.
  Praxis: gleicher oder günstigerer Preis erhöht Cassini-Ranking.

OTTO PREISPARITÄT:
  Otto behält sich Preisanpassungen vor wenn günstiger anderswo.
  Monitoring aktiv — zu hohe Preise vs. Markt führen zu Listing-Deprioritisierung.
```


## 16.3 Kanal-spezifische Listing-Variationen

```
GLEICHE PRODUKTE — VERSCHIEDENE LISTINGS:

  AMAZON:
    Titel: Marke + Benefit-Keywords + Maße + Material
    Fokus: CVR, Buy Box, externe Traffic-Optimierung

  EBAY:
    Titel: Top-Keywords + Synonyme (80 Zeichen komprimiert)
    Fokus: Item Specifics vollständig, TRS-Performance

  OTTO:
    Titel: SEO-optimiert für Otto-Suche, kürzerer Stil
    Fokus: Product Quality Score, Retourenminimierung

  KAUFLAND:
    Titel: Keyword-fokussiert, Preis wettbewerbsfähig
    Fokus: Vollständigkeit, EAN korrekt, günstiger Preis

  BILDER:
    Hauptbild: Gleich auf allen Kanälen (weißer Hintergrund, standard)
    Weitere Bilder: Kanal-angepasst (otto: mehr Detail; amazon: lifestyle+infografik)
```


===============================================================================
# TEIL 17 — ARIA OPTIMIERUNGS-HEURISTIKEN
===============================================================================


## 17.1 ARIA Ranking-Analyse-Framework

```typescript
// services/aria/marketplace/ranking-analyzer.ts

interface RankingAnalysis {
  sku: string
  kanal: Marketplace
  currentRank: number
  rankingFaktoren: RankingFaktor[]
  sofortHebel: Optimierung[]
  mittelfristigHebel: Optimierung[]
  score: number  // 0-100
}

interface Optimierung {
  faktor: string
  aufwand: 'niedrig' | 'mittel' | 'hoch'
  wirkung: 'niedrig' | 'mittel' | 'hoch'
  prioritaet: number  // 1 = höchste Priorität
  beschreibung: string
  erwarteterGewinn: string
}

// Amazon Sofort-Hebel nach Aufwand/Wirkung
export const AMAZON_QUICK_WINS: Optimierung[] = [
  {
    faktor: 'Hauptbild',
    aufwand: 'mittel',
    wirkung: 'hoch',
    prioritaet: 1,
    beschreibung: 'Hauptbild auf min. 2000x2000px hochskalieren, Produkt >85% Fläche',
    erwarteterGewinn: '+5-15% CTR, +2-8% CVR'
  },
  {
    faktor: 'Backend Keywords',
    aufwand: 'niedrig',
    wirkung: 'mittel',
    prioritaet: 2,
    beschreibung: 'Backend Keywords auf 250 Byte füllen mit Synonymen und Long-Tail',
    erwarteterGewinn: '+10-20% indexierte Keywords'
  },
  {
    faktor: 'Bullet Point 1',
    aufwand: 'niedrig',
    wirkung: 'mittel-hoch',
    prioritaet: 3,
    beschreibung: 'Ersten Bullet auf Feature-Benefit-Formel umschreiben, CAPS Feature',
    erwarteterGewinn: '+2-5% CVR'
  },
  {
    faktor: 'A+ Content',
    aufwand: 'hoch',
    wirkung: 'hoch',
    prioritaet: 4,
    beschreibung: 'A+ Content mit 5-7 Modulen erstellen (nur Brand Registry)',
    erwarteterGewinn: '+3-10% CVR'
  },
  {
    faktor: 'Produktvideo',
    aufwand: 'hoch',
    wirkung: 'hoch',
    prioritaet: 5,
    beschreibung: 'Kurzes Demo-Video (30-90s) hochladen',
    erwarteterGewinn: '+5-12% CVR auf Mobile'
  },
]
```


## 17.2 ARIA Listing-Score-Berechnung

```typescript
// Simplified Listing Score für ARIA-Dashboard

export function calculateListingScore(listing: Listing, kanal: Marketplace): number {
  let score = 0

  if (kanal === 'amazon') {
    // Titel (20 Punkte)
    if (listing.title.length >= 80 && listing.title.length <= 150) score += 20
    else if (listing.title.length >= 50) score += 10

    // Bilder (20 Punkte)
    if (listing.imageCount >= 7) score += 20
    else if (listing.imageCount >= 5) score += 15
    else if (listing.imageCount >= 3) score += 8

    // Bullets (15 Punkte)
    if (listing.bulletCount === 5 && listing.avgBulletLength >= 80) score += 15
    else if (listing.bulletCount >= 3) score += 8

    // A+ Content (15 Punkte)
    if (listing.hasAPlus) score += 15

    // Backend Keywords (10 Punkte)
    if (listing.backendKeywordsBytes >= 240) score += 10
    else if (listing.backendKeywordsBytes >= 150) score += 6

    // Bewertungen (10 Punkte)
    if (listing.reviewCount >= 50 && listing.avgRating >= 4.2) score += 10
    else if (listing.reviewCount >= 10 && listing.avgRating >= 4.0) score += 6
    else if (listing.reviewCount >= 5) score += 3

    // Preis (10 Punkte)
    if (listing.priceCompetitiveness === 'competitive') score += 10
    else if (listing.priceCompetitiveness === 'above') score += 5

    return Math.min(100, score)
  }

  // eBay Score
  if (kanal === 'ebay') {
    if (listing.title.length >= 60 && listing.title.length <= 80) score += 25
    if (listing.itemSpecificsCompleteness >= 0.9) score += 25
    if (listing.imageCount >= 6) score += 20
    if (listing.hasFreeShipping) score += 15
    if (listing.sellerFeedbackScore >= 0.98) score += 15
    return Math.min(100, score)
  }

  return 0
}
```


## 17.3 ARIA Wettbewerber-Analyse Heuristiken

```
WETTBEWERBER-ANALYSE FRAMEWORK FÜR ARIA:

  SCHRITT 1: TOP-10 WETTBEWERBER IDENTIFIZIEREN
    • Amazon: Top-10 organisch für Haupt-Keyword
    • eBay: Top-10 nach 'Best Match'
    • Kein PPC-Overlay (nur organisch)

  SCHRITT 2: PRO WETTBEWERBER ANALYSIEREN
    • Preis (inkl. Versand)
    • Anzahl Bewertungen + Ø Rating
    • Listing-Qualität (Bilder, Bullets, A+)
    • Lieferoptionen
    • BSR / Kategorie-Rang

  SCHRITT 3: BENCHMARK ERSTELLEN
    • Median-Preis Top-10
    • Median-Reviews Top-10
    • Häufigste Listing-Features
    • Keyword-Überschneidung

  SCHRITT 4: GAP-ANALYSE
    • Wo sind wir besser?
    • Wo sind wir schlechter?
    • Was machen Top-3 anders?

  SCHRITT 5: PRIORISIERTER AKTIONSPLAN
    • Quick Wins (< 1 Stunde Aufwand)
    • Mittelfristig (1 Woche)
    • Langfristig (1 Monat+)
```


===============================================================================
# TEIL 18 — VERBOTENES GESAMT-REGISTER (ALLE KANÄLE)
===============================================================================


## 18.1 Universell verboten — alle Kanäle


| VERSTOSS                           | KONSEQUENZ                            | KANÄLE                 |
| ---------------------------------- | ------------------------------------- | ---------------------- |
| Counterfeit/Plagiate               | Sofortige Sperrung, rechtliche Folgen | Alle                   |
| Bewertungen kaufen                 | Sperrung, Klage möglich               | Alle                   |
| Externe Links in Listings          | Listing-Entfernung                    | Alle                   |
| Preise outside-Plattform anbieten  | Account-Sperrung                      | Alle                   |
| Gefährliche Güter ohne Deklaration | Sperrung + Bußgelder                  | Alle                   |
| Identitätstäuschung                | Sperrung + rechtliche Folgen          | Alle                   |
| Mehrfach-Accounts (ungenehmigt)    | Alle Accounts gesperrt                | Amazon, eBay           |
| Produkte ohne CE (wenn Pflicht)    | Listing-Entfernung + Bußgeld          | Otto, Kaufland, Amazon |


## 18.2 Kanal-spezifisch verboten


| VERSTOSS                                      | KONSEQUENZ                     | NUR BEI        |
| --------------------------------------------- | ------------------------------ | -------------- |
| Preis dauerhaft höher als Wettbewerber-Kanal  | Buy Box-Entzug                 | Amazon         |
| FBA-Bestand erschöpft ohne Nachbestellung     | Ranking-Verlust dauerhaft      | Amazon         |
| Keyword-Stuffing im Titel (gleiche Wörter 3+) | Ranking-Strafe                 | Amazon, eBay   |
| Item Specifics unvollständig                  | Ranking-Verlust                | eBay           |
| Retourenquote > 40%                           | Listing-Deaktivierung          | Otto           |
| Product Quality Score < 60                    | Listing nicht sichtbar         | Otto           |
| EAN fehlt                                     | Listing abgelehnt              | Kaufland, Otto |
| Dropshipping aus anderen Marktplätzen         | Account-Sperrung               | eBay           |
| Wettbewerber-Markennamen im Titel             | Listing-Entfernung + Abmahnung | Amazon, eBay   |


## 18.3 Legale Grauzonen — Vorsicht geboten


| THEMA                                    | STATUS                        | EMPFEHLUNG                                  |
| ---------------------------------------- | ----------------------------- | ------------------------------------------- |
| Bundle-Listing mit Fremdmarke            | Grauzone                      | Nur mit nachweisbarer Herstellererlaubnis   |
| Vine-Bewertungen selektiv einsetzen      | Erlaubt mit Einschränkungen   | Nicht ablehnen oder entfernen               |
| Bewertungs-Erinnerung per Insert         | Grauzone                      | Neutral formulieren, keine Bewertungs-Bitte |
| Preis temporär hoch dann Sale-Preis      | Erlaubt mit Limits            | Referenzpreis darf nicht falsch sein        |
| Cross-Listing gleicher ASIN              | Verboten wenn gleicher Seller | ASIN-Sharing mit anderen Sellern            |
| Influencer-Kooperation ohne Deklaration  | Verboten (EU-Recht)           | Immer als Werbung kennzeichnen              |
| Review-Gating (nur positive beantworten) | Verboten                      | Alle Review-Anfragen gleich behandeln       |


---

*ARIA-MARKTPLAETZE.md — Production Ready*
*Comentra Intelligence Layer*
*Stand: 2025/2026 — Empirisch validiert*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*Alle Gewichtungen sind Schätzungen — Amazon/eBay/Otto/Kaufland veröffentlichen keine offiziellen Werte.*
===============================================================================
# TEIL 19 — AMAZON A10: SAISONALE RANKING-DYNAMIKEN
===============================================================================


## 19.1 Saisonale Ranking-Verschiebungen

Amazon passt intern die Gewichtung saisonaler Signale an.
Wer diese Dynamiken kennt, kann Listing-Optimierungen timen.

| SAISON                    | TIMING          | WAS AMAZON PRIORISIERT               | HEBEL                                |
| ------------------------- | --------------- | ------------------------------------ | ------------------------------------ |
| Valentinstag              | Jan 15 – Feb 14 | Geschenkprodukte, schnelle Lieferung | Titel anpassen, Gift-Keywords        |
| Frühling/Ostern           | Feb – April     | Outdoor, Garten, Kinderspielzeug     | Saisonale Keywords in Backend        |
| Muttertag                 | Apr 15 – Mai 10 | Dekoration, Haushalt, Geschenke      | Geschenk-Keywords                    |
| Prime Day                 | Juli (variabel) | Extreme CVR, Sale-Preise             | Deals einreichen, Bestand voll       |
| Back to School            | Jul – Sep       | Büro, Schulbedarf, Schreibtische     | Büro-Keywords                        |
| Q4 Vorbereitung           | Sep – Okt       | Bestandsaufbau FBA, BSR aufbauen     | FBA einliefern, PPC hochfahren       |
| Black Friday/Cyber Monday | Nov (Woche 47)  | Höchste Traffic-Dichte des Jahres    | Deals, optimale Preise, max. Bestand |
| Weihnachten               | Nov 15 – Dez 24 | Geschenke, Prime, schnelle Lieferung | Gift-Keywords, Bundles               |
| Post-Peak                 | Jan             | Abverkauf, Preissenkungen normal     | Überbestand abbauen                  |


## 19.2 Amazon Keyword-Recherche-Methodik


### Step-by-Step Keyword-Recherche

```
SCHRITT 1: SEED KEYWORDS FINDEN
  • Produktname auf Deutsch (alle Schreibweisen)
  • Produktname auf Englisch (viele DACH-Käufer suchen englisch)
  • Problem-Keywords ('quietschende Treppe sichern')
  • Synonyme (Sandkasten, Sandkiste, Spielsandkasten)
  • Material-Keywords (Fichtenholz, Massivholz, Holz)
  • Zielgruppen-Keywords (Kinder, Kleinkind, ab 2 Jahre)

SCHRITT 2: AUTOCOMPLETE MINING
  • Amazon Suchfeld: Eingabe Seed + Leerzeichen → alle Vorschläge notieren
  • Google Autocomplete für gleiche Seeds
  • eBay Autocomplete (andere Suchmuster als Amazon)

SCHRITT 3: WETTBEWERBER-ANALYSE
  • Top-3 ASINS für Haupt-Keyword
  • Reverse-ASIN-Lookup (Tools: Helium 10, Jungle Scout)
  • Keywords für die sie ranken die wir nicht haben

SCHRITT 4: VOLUMEN-FILTER
  • Search Volume > 300/Monat: in Titel
  • Search Volume 100–300/Monat: in Bullets + Backend
  • Search Volume < 100/Monat: Backend und Beschreibung

SCHRITT 5: RELEVANZ-FILTER
  • Würde jemand der DIESES Keyword sucht unser Produkt kaufen?
  • Wenn nein: weglassen (schlechte CVR schadet Ranking)

SCHRITT 6: PLATZIERUNGS-MATRIX
  TITEL:          Top-3 Head Keywords (höchstes Volumen + Relevanz)
  BULLET 1:       Primär-Keyword + wichtigstes Synonym
  BULLET 2-5:     Mid-Tail Keywords natürlich eingebaut
  BACKEND:        Alles übrige (Synonyme, Long-Tail, andere Sprache)
  BESCHREIBUNG:   Weitere Mid-Tail und Problem-Keywords
```


### Keyword-Volumen-Benchmarks Amazon.de (2025)


| KATEGORIE-BEISPIEL | HAUPT-KEYWORD             | MONATL. VOLUMEN (SCHÄTZUNG) | WETTBEWERB |
| ------------------ | ------------------------- | --------------------------- | ---------- |
| Outdoor/Garten     | Sandkasten Holz           | 8.000–15.000                | Mittel     |
| Outdoor/Garten     | Sandkasten für Kinder     | 3.000–6.000                 | Mittel     |
| Outdoor/Garten     | Sandkiste Holz            | 2.000–4.000                 | Niedrig    |
| Akustik            | Akustikpaneele            | 5.000–10.000                | Hoch       |
| Akustik            | Schallschutz Büro         | 2.000–5.000                 | Mittel     |
| Akustik            | Akustikpaneele Wand       | 1.500–3.000                 | Mittel     |
| Treppen-Zubehör    | Treppenschutzgitter       | 3.000–7.000                 | Hoch       |
| Treppen-Zubehör    | Kinderschutzgitter Treppe | 2.000–5.000                 | Hoch       |
| Lattenrost         | Lattenrost 140x200        | 10.000–20.000               | Sehr hoch  |


## 19.3 Amazon Varianten-Strategie

```
WANN VARIANTEN SINNVOLL SIND:
  ✓ Gleiche Produkt-Basis, nur Größe/Farbe/Menge unterschiedlich
  ✓ Bewertungen sollen gebündelt werden (alle Varianten teilen Reviews)
  ✓ Käufer auf einer Seite alle Optionen sehen sollen

WANN SEPARATE LISTINGS BESSER SIND:
  ✗ Zu viele Varianten (> 20) führen zu schlechter UX
  ✗ Sehr unterschiedliche Keywords pro Variante
  ✗ Unterschiedliche Kategorien für Varianten

VARIANTEN-RANKING-LOGIK:
  • Parent-ASIN: eigenes BSR, eigenes Ranking
  • Child-ASINs: eigene BSR, Rankings werden TEILS auf Parent vererbt
  • Beste-rankte Variante erscheint in Suchergebnissen
  • Clicks auf eine Variante können andere Varianten mitbosten

VARIANTEN-BEST-PRACTICES:
  1. Populärste Variante als Standard-Variante setzen
  2. Alle Varianten gleich vollständig befüllen (Bilder, Bullets)
  3. Variantenspezifische Keywords in Child-Titel integrieren
  4. Bei Bewertungs-Split: Varianten zusammenführen (wenn möglich)
  5. Preis-Differenzierung sinnvoll (Basis vs. Premium-Variante)
```


## 19.4 Amazon Brand Registry — Vollständige Nutzung


| FEATURE                 | VERFÜGBAR     | WERT                                            |
| ----------------------- | ------------- | ----------------------------------------------- |
| A+ Content (EBC)        | Ja            | Direkt messbare CVR-Steigerung                  |
| Sponsored Brands        | Ja            | Headline-Ads, Video-Ads                         |
| Amazon Storefront       | Ja            | Eigene Marken-Seite auf Amazon                  |
| Brand Analytics         | Ja            | Search Query Report, Competitor Intel           |
| Vine Programm           | Ja            | Bis zu 30 kostenlose Bewertungen für neue ASINs |
| Amazon Posts            | Ja            | Instagram-ähnlicher Feed auf Amazon             |
| Virtual Bundles         | Ja            | FBA-Bundles ohne Neu-ASIN                       |
| Manage Your Experiments | Ja            | A/B-Tests für Titel, Bilder, A+                 |
| Transparency Program    | Optional      | Anti-Counterfeit Schutz                         |
| Project Zero            | Auf Einladung | Automatische Counterfeit-Entfernung             |


===============================================================================
# TEIL 20 — AMAZON PERFORMANCE-OPTIMIERUNG FORTGESCHRITTEN
===============================================================================


## 20.1 Launch-Strategie für neue ASINs

```
AMAZON LAUNCH-PHASEN (empirisch bewährt):

PHASE 1 — VORBEREITUNG (vor Go-Live):
  □ Listing 100% vollständig (Bilder, Bullets, A+, Backend)
  □ Bestand ausreichend (min. 60-Tage-Reichweite)
  □ FBA-Bestand eingelagert (wenn FBA geplant)
  □ Keyword-Recherche abgeschlossen
  □ Preisgestaltung: leicht unter Markt-Median für Launch

PHASE 2 — HONEY-MOON PERIOD (Woche 1-2):
  • Amazon gibt neuen ASINs temporären Ranking-Boost
  • CTR und CVR in dieser Phase kritisch für dauerhaftes Ranking
  • PPC sofort starten (Auto-Kampagne + Exact für Top-Keywords)
  • Externes Traffic-Driving aus eigenen Channels
  • Vine-Bewerbung wenn Brand Registry (3-4 Wochen Vorlauf)

PHASE 3 — ORGANISCHES WACHSTUM (Woche 3-8):
  • PPC-Daten auswerten: converting Keywords in Manual umziehen
  • Verlust-Keywords als Negativ-Keywords
  • Preis langsam auf Ziel-Niveau bringen (wenn CVR gut)
  • A/B-Test Hauptbild wenn möglich

PHASE 4 — STABILISIERUNG (Woche 8+):
  • ACoS optimieren, Budget auf Performer konzentrieren
  • Bewertungs-Aufbau (Vine, organisch über Buyer Messages)
  • BSR als Proxy für Ranking-Gesundheit beobachten

TYPISCHE LAUNCH-ZEITLINIE:
  Woche 1:  0 organische Rankings, 100% PPC
  Woche 2:  Erste Long-Tail organische Rankings
  Woche 4:  Mid-Tail Keywords beginnen organisch zu ranken
  Woche 8:  Head Keywords beginnen Page 2-3 zu erscheinen
  Woche 16: Stabile organische Präsenz wenn Velocity gut
```


## 20.2 PPC-Optimierungs-Framework

```
BIDDING-STRATEGIE NACH ZIEL:

  LAUNCH (neue ASIN, kein historisches Ranking):
    Budget: Hoch (Visibility > Profitabilität)
    Ziel-ACoS: Keine Beschränkung in Woche 1-2
    Match-Type: Auto + Broad am Anfang
    Keyword-Set: 10-20 Seeds, breit

  GROWTH (ASIN hat organisches Ranking, skalieren):
    Budget: Mittel-Hoch
    Ziel-ACoS: Break-Even ACoS oder leicht drüber
    Match-Type: Auto (Entdeckung) + Exact (Konversion)
    Keyword-Set: Verfeinert auf Converter

  PROFIT (ASIN etabliert, Marge maximieren):
    Budget: Mittel (nur profitable Keywords)
    Ziel-ACoS: Unter Break-Even, ziel auf positiven ROAS
    Match-Type: Primär Exact, wenig Broad
    Keyword-Set: Top-20 Converter, Rest ausschalten

  DEFENSE (Wettbewerber auf unserem Top-Keyword verdrängen):
    Budget: Variabel
    Strategie: Eigenes Brand-Keyword schützen
    Match-Type: Exact auf eigene Markenbegriffe

WEEKLY PPC REVIEW CHECKLIST:
  □ Keywords mit > 10 Klicks, 0 Conversions → Negativ hinzufügen
  □ Keywords mit gutem ACoS → Gebot erhöhen (+10-20%)
  □ Keywords mit schlechtem ACoS → Gebot senken (-10-20%)
  □ Auto-Kampagne: neue Converting Keywords extrahieren
  □ Budget aufgebraucht vor 14 Uhr → Budget erhöhen oder Gebote senken
  □ Impression Share < 30% bei wichtigen Keywords → Gebote erhöhen
```


## 20.3 Amazon Bewertungs-Aufbau-Strategie (Compliant)

```
LEGALE BEWERTUNGS-AUFBAU-TAKTIKEN:

  1. VINE PROGRAMM (Brand Registry erforderlich):
     • Bis zu 30 Vine-Reviewer erhalten kostenloses Produkt
     • Kosten: 200€ per ASIN (Stand 2024)
     • Zeitraum: ca. 3-4 Wochen
     • Kein Einfluss auf Bewertungs-Inhalt möglich
     • Vine-Badge sichtbar auf Review
     • WANN NUTZEN: Neue ASINs mit 0 Reviews

  2. SELLER CENTRAL REVIEW-ANFRAGE:
     • Über 'Request a Review' Button in Seller Central
     • Nur einmal pro Bestellung nutzbar
     • Kein Custom-Text erlaubt
     • Nur wenn Bestellung abgeschlossen und nicht retourniert
     • AUTOMATISIERT über Seller Central API möglich

  3. FOLLOW-UP EMAIL (nur über Amazon Buyer-Seller Messaging):
     • Darf KEINE Bitte um positive Bewertung enthalten
     • Darf um neutrale Bewertung bitten (wenn Problem: Kontakt zuerst)
     • Empfohlener Timing: 7-10 Tage nach Lieferung
     • Templates müssen Amazon-Policy-konform sein

  4. PRODUKT-INSERT (in Verpackung):
     • Darf auf Kundenservice hinweisen
     • Darf QR-Code zu eigener Website/Support haben
     • NICHT erlaubt: direkte Aufforderung zur positiven Bewertung
     • NICHT erlaubt: Incentive gegen Bewertung

REVIEW-RESPONSE STRATEGIE:
  • Auf ALLE negativen Bewertungen (1-3 Sterne) öffentlich antworten
  • Antwort: professionell, lösungsorientiert, nicht defensiv
  • Keine negativen Bewertungen anfechten außer wenn: Fake/Spam/Falsche ASIN
  • Bei Fake-Reviews: Amazon Case öffnen (Erfolgsrate < 50%)
```


===============================================================================
# TEIL 21 — EBAY CASSINI: DEEP DIVE
===============================================================================


## 21.1 Cassini Best Match Algorithmus — Technische Details

```
CASSINI BEST MATCH — INTERNE SCORING-LOGIK (rekonstruiert):

  RELEVANZ-SCORE:
    Punkte wenn Suchanfrage-Keyword exakt im Titel: +Hoch
    Punkte wenn Suchanfrage-Keyword in Item Specifics: +Mittel
    Punkte wenn Suchanfrage-Keyword in Beschreibung: +Niedrig
    Punkte bei Phrase Match (nicht exact): +Mittel
    Punkte bei Synonym-Match: +Niedrig

  SELLER-PERFORMANCE-SCORE:
    TRS+: Multiplikator auf Gesamt-Score
    TRS:  Basis-Bonus
    Kein TRS: Kein Bonus
    Negative Defects: Abzug proportional zur Defect-Rate

  LISTING-QUALITÄTS-SCORE:
    Bilder > 6: +Punkte
    Kostenloser Versand: +Punkte (starker Faktor)
    1-Tag Handling: +Punkte
    Vollständige Item Specifics: +Punkte
    Aktives Preisangebot (kein Ablauf bald): +Punkte

  TRANSAKTIONS-WAHRSCHEINLICHKEIT:
    Historische CTR auf ähnliche Suchanfragen: +/-
    Historische CVR auf ähnliche Suchanfragen: +/-
    Preis vs. Median-Preis dieser Kategorie: +/-

  AKTUALITÄTSFAKTOR:
    Listing jüngst erstellt/aktualisiert: +Kleiner Boost
    Listing läuft bald ab (Good Till Cancelled): Neutral
    Neugelistet (letzte 7 Tage): +Temporärer Boost
```


## 21.2 eBay Item Specifics — Vollständige Kategorien-Analyse


### Item Specifics für Möbel/Outdoor (eBay.de)


| ATTRIBUT         | WERT-BEISPIEL            | PFLICHT/EMPFOHLEN | RANKING-IMPACT   |
| ---------------- | ------------------------ | ----------------- | ---------------- |
| Marke            | CLAMARO / Eigenmarke     | Pflicht           | Hoch             |
| Material         | Massivholz / Fichtenholz | Pflicht           | Hoch             |
| Breite (cm)      | 150                      | Empfohlen         | Hoch (Filterung) |
| Tiefe (cm)       | 150                      | Empfohlen         | Hoch             |
| Höhe (cm)        | 25                       | Empfohlen         | Mittel           |
| Farbe            | Naturbraun               | Empfohlen         | Mittel           |
| Produktart       | Sandkasten               | Pflicht           | Sehr hoch        |
| Altersempfehlung | Ab 2 Jahren              | Empfohlen         | Mittel           |
| Zertifizierung   | FSC                      | Empfohlen         | Niedrig-Mittel   |
| Herstellernummer | MPN                      | Empfohlen         | Niedrig          |
| EAN              | 4260...                  | Pflicht           | Mittel           |


## 21.3 eBay Good Till Cancelled (GTC) vs. Auktionen


| LISTING-TYP                     | RANKING-EFFEKT                     | WANN NUTZEN                       |
| ------------------------------- | ---------------------------------- | --------------------------------- |
| Good Till Cancelled (Festpreis) | Stabiles Ranking, baut sich auf    | Neu-Produkte, Massenware          |
| Auktion 7 Tage                  | Kurzer Sichtbarkeits-Spike am Ende | Sammlerstücke, Unikate            |
| Auktion 10 Tage                 | Längerer Spike, mehr Exposure      | Hochpreisige Einzelstücke         |
| Best Offer aktiviert            | Neutral/leicht positiv             | Wenn Preisverhandlung akzeptabel  |
| Buy it Now + Auktion            | Kombi-Ranking                      | Selten empfohlen für Standardware |


```
RANKING-TIPP: Listing-RESET-STRATEGIE

  Problem: Alte GTC-Listings verlieren Ranking wenn Sales stocken.
  Cassini 'altert' Listings wenn keine Aktivität.

  LEGAL RESET-METHODE:
    1. Listing beenden (End Item)
    2. Warten: 24-48 Stunden
    3. Listing mit gleichen Daten neu erstellen
    4. Neues Listing bekommt 'Neuheits-Boost'

  WANN SINNVOLL:
    • Ranking dauerhaft schlechter als vor 6 Monaten
    • Keine Sales trotz gutem Preis und guten Listings
    • Saisonaler Neustart nach Sommerpause

  WICHTIG:
    • Bewertungen gehen bei Neulistung nicht verloren (am Account)
    • Product-Level-Bewertungen sind an ASIN/Produkt gebunden
    • Nicht zu häufig (> 1x pro Monat = verdächtig)
```


## 21.4 eBay Promoted Listings Optimierung

```
PROMOTED LISTINGS STANDARD (PLS) — OPTIMIERUNGS-GUIDE:

  WIE AD RATE FESTLEGEN:
    1. eBay zeigt 'Trend Rate' pro Kategorie
    2. Trend Rate + 1-2%: sehr gute Platzierung
    3. Trend Rate: durchschnittliche Platzierung
    4. Unter Trend Rate: kaum Promotion-Effekt

  WANN PLS SINNVOLL:
    ✓ Wenn organisches Ranking < Seite 3
    ✓ Bei neuen Listings (kein organisches Ranking)
    ✓ Bei saisonalen Peaks
    ✓ Wenn Wettbewerber Buy-Box-ähnliche Position dominieren

  WANN PLS WENIG BRINGT:
    ✗ Wenn organisch bereits auf Seite 1 Position 1-5
    ✗ Wenn Preis deutlich über Markt-Median
    ✗ Wenn Item Specifics unvollständig (organische Schwäche bleibt)

  PLA (ADVANCED) — KEYWORD-STRATEGIE:
    Schritt 1: Auto-Kampagne 2 Wochen laufen lassen
    Schritt 2: Daten auswerten: welche Keywords konvertieren?
    Schritt 3: Converter in Manual Exact übertragen
    Schritt 4: Verlierer pausieren
    Schritt 5: Monatlich optimieren
```


===============================================================================
# TEIL 22 — OTTO: FORTGESCHRITTENE STRATEGIEN
===============================================================================


## 22.1 Otto Produktdaten-Upload — Technische Details

```
OTTO PRODUKTDATEN-ÜBERTRAGUNG (2025):

  METHODEN:
    1. Otto Partner Portal (manuell, für kleine Kataloge)
    2. CSV-Upload (für mittlere Kataloge)
    3. REST API (für große Kataloge / Echtzeit-Updates)
    4. SFTP-Upload (Legacy, noch verfügbar)

  API-INTEGRATION:
    • Basis-URL: https://api.otto.market
    • Authentifizierung: OAuth 2.0
    • Rate Limits: 100 Requests/Sekunde
    • Produkt-Upload: POST /v3/products
    • Preis-Update: POST /v3/prices
    • Bestand-Update: POST /v3/quantities
    • Order-Abruf: GET /v4/orders

  DATENFORMAT:
    • JSON (API)
    • CSV mit Otto-spezifischen Spaltenheadern (SFTP/Portal)

  LATENZ BEI ÄNDERUNGEN:
    Preis-Updates:     1-5 Minuten (API)
    Bestand-Updates:   1-5 Minuten (API)
    Produkt-Updates:   1-24 Stunden (je nach Prüfung)
    Neue Listings:     24-72 Stunden (Otto Quality Check)
```


## 22.2 Otto Quality Check — Was passiert bei Ablehnung

```
OTTO LEHNT LISTINGS AB WENN:

  PFLICHTFELDER FEHLEN:
    • EAN nicht vorhanden oder ungültig
    • Hauptkategorie nicht zugeordnet
    • Preis fehlt oder 0
    • Kein Bild hochgeladen

  INHALTLICHE ABLEHNUNGSGRÜNDE:
    • Titel zu kurz (< 20 Zeichen) oder zu lang (> 255 Zeichen)
    • Beschreibung enthält verbotene Inhalte
    • Bild-Qualität zu gering (< 600x600px)
    • Fehlendes Pflichtattribut der Kategorie
    • EAN gehört bereits einem anderen Produkt (Konflikt)
    • Preisangabe nicht MwSt.-konform

  BEI ABLEHNUNG:
    → Otto sendet Fehlermeldung mit Fehlercode
    → Produkt erscheint im Portal mit Status 'Fehler'
    → Korrektur und Re-Upload nötig
    → Bei wiederholten Ablehnungen: manueller Otto-Review

  HÄUFIGE FEHLERCODES:
    OTTO-E-001: EAN ungültig
    OTTO-E-004: Pflichtattribut fehlt
    OTTO-E-007: Bild-URL nicht erreichbar
    OTTO-E-012: Kategorie nicht gefunden
    OTTO-E-015: Preisformat ungültig
```


## 22.3 Otto Search Engine Optimization

```
OTTO SEO — KEYWORD-STRATEGIE:

  OTTO-SPEZIFISCHE SUCHMUSTER:
    • Kürzere, konkreter als Amazon-Suchen
    • Stärker kategorie-navigierend ('Sandkasten Holz kaufen')
    • Qualitätssignale wichtig ('hochwertig', 'robust', 'Made in Germany')

  TITEL-OPTIMIERUNG FÜR OTTO:
    Format: [Hauptkeyword] [Zweitkeyword] [wichtigstes Attribut]
    Länge: 60–100 Zeichen optimal
    Marke: kann weggelassen werden wenn unbekannt

  OTTO SUCHALGORITHMUS — KEYWORD-FELDER (Priorität):
    1. Produktname (Titel): Höchste Gewichtung
    2. Pflichattribute (Kategorie): Hohe Gewichtung
    3. Kurzbeschreibung: Mittlere Gewichtung
    4. Produktbeschreibung: Niedrige Gewichtung
    5. Technische Details: Niedrige Gewichtung

  OTTO KATEGORIE-NAVIGATION:
    • Otto hat starke Kategorie-Filterung durch Käufer
    • Richtige Kategorisierung kritisch für Findbarkeit
    • Falsche Kategorie = kein organisches Ranking in echten Kategorie-Suchen

  OTTO VS. AMAZON KEYWORD-UNTERSCHIEDE:
    Amazon: 'Sandkasten Holz FSC 150cm Kinder Garten ab 2 Jahre'
    Otto:   'Sandkasten Holz 150x150 cm für Kinder'
    → Otto-Käufer suchen direkter, weniger Long-Tail
```


===============================================================================
# TEIL 23 — KAUFLAND: FORTGESCHRITTENE STRATEGIEN
===============================================================================


## 23.1 Kaufland Fulfillment (KF)

```
KAUFLAND FULFILLMENT — FACTS (2025):

  WAS IST KF:
    • Amazons FBA-Äquivalent auf Kaufland
    • Einlagerung im Kaufland-Logistik-Netzwerk
    • Kaufland übernimmt Pick, Pack, Versand

  VORTEILE KF:
    ✓ Schnellere Lieferzeiten (gleich-/nächsttags in vielen Regionen)
    ✓ Ranking-Boost durch bessere Lieferzeit-Metrik
    ✓ Weniger operativer Aufwand für Händler
    ✓ KF-Badge auf Listings (Vertrauenssignal)

  KOSTEN KF (2025, ungefähr):
    Einlagerungs-Grundgebühr: variabel nach Größe
    Versand-Gebühr: 3,50–8,00€ je Sendung
    Lagergebühr: monatlich nach Volumen

  WANN KF RECHNET SICH:
    ✓ Wenn Volumen > 100 Einheiten/Monat auf Kaufland
    ✓ Wenn Eigenversand-Kosten ähnlich wie KF-Kosten
    ✓ Wenn Ranking-Boost durch schnellere Lieferung konvertiert

  WANN KF NICHT RECHNET SICH:
    ✗ Kleine Stückzahlen (< 50/Monat auf Kaufland)
    ✗ Sehr große/schwere Produkte
    ✗ Produkte mit hoher Retourenquote
```


## 23.2 Kaufland EAN-Management

```
EAN (GTIN) MANAGEMENT FÜR KAUFLAND:

  WARUM EAN SO WICHTIG:
    • Kaufland gleicht EAN gegen Katalog-Datenbank ab
    • Bei bekannter EAN: Kaufland füllt Stammdaten automatisch
    • Bei Stammdaten-Konflikt: Kaufland-Daten überschreiben eigene

  WENN KAUFLAND-STAMMDATEN FALSCH SIND:
    → Case beim Kaufland-Support öffnen
    → Nachweis (Bild, technische Specs) einreichen
    → Korrektur dauert 5-15 Werktage

  EIGENMARKEN OHNE STANDARD-EAN:
    → GS1-EAN registrieren lassen (gs1-germany.de)
    → Kosten: ab 150€/Jahr für kleines Portfolio
    → Alternativ: GS1-Präfix kaufen (einmalig ~180€ + Jahresgebühr)

  EAN-KONFLIKTE VERMEIDEN:
    • Nie fremde EANs verwenden
    • Pro Produktvariante eigene EAN
    • EANs zentral in Artikelstamm pflegen
    • Comentra: EAN-Feld als Pflichtfeld für alle Produkte
```


===============================================================================
# TEIL 24 — LISTING-QUALITÄTS-SCORECARD
===============================================================================


## 24.1 Amazon Listing Scorecard (0–100 Punkte)


| ELEMENT          | MAX PUNKTE | KRITERIUM FÜR VOLLE PUNKTE                  | HÄUFIGSTER FEHLER            |
| ---------------- | ---------- | ------------------------------------------- | ---------------------------- |
| Hauptbild        | 15         | ≥ 2000x2000px, >85% Produkt, weißer BG      | Zu klein, BG nicht rein weiß |
| Weitere Bilder   | 10         | ≥ 7 Bilder, Lifestyle + Infografik + Detail | Zu wenige Bilder             |
| Produkttitel     | 15         | 80–150 Zeichen, Keyword vorne, strukturiert | Zu kurz oder zu lang         |
| Bullet Points    | 10         | 5 Bullets, je 80–120 Zeichen, Benefit-first | Zu kurz, kein Benefit        |
| A+ Content       | 10         | A+ aktiv, ≥ 5 Module, strukturiert          | Fehlt komplett               |
| Backend Keywords | 10         | 240+ Byte, Synonyme, keine Wiederholungen   | Nicht ausgefüllt             |
| Bewertungen      | 10         | ≥ 50 Reviews, Ø ≥ 4.2 Sterne                | Zu wenige Reviews            |
| Preis            | 10         | ≤ Markt-Median für Kategorie                | Zu teuer vs. Wettbewerber    |
| FBA / Prime      | 5          | FBA aktiv oder SFP                          | FBM ohne Prime               |
| Video            | 5          | Produktvideo hochgeladen                    | Kein Video                   |


```
SCORE-INTERPRETATION AMAZON:
  90–100: Top-Listing. Fokus auf PPC und externes Traffic.
  75–89:  Gut. 2-3 konkrete Verbesserungen identifizieren.
  60–74:  Mittel. Sofort-Hebel: Bild, Bullets, Backend.
  45–59:  Schwach. Grundlegende Überarbeitung nötig.
  < 45:   Sehr schwach. Komplettes Listing-Rebuild empfohlen.
```


## 24.2 eBay Listing Scorecard (0–100 Punkte)


| ELEMENT           | MAX PUNKTE | KRITERIUM FÜR VOLLE PUNKTE               | HÄUFIGSTER FEHLER        |
| ----------------- | ---------- | ---------------------------------------- | ------------------------ |
| Titel             | 20         | 60–80 Zeichen, Top-Keywords vorne        | Zu lang oder keyword-arm |
| Item Specifics    | 25         | Alle Pflicht- + 90% empfohlen ausgefüllt | Leer gelassen            |
| Bilder            | 15         | ≥ 6 Bilder, ≥ 1600px                     | Zu wenige / zu klein     |
| Beschreibung      | 10         | Strukturiertes HTML, keywords, details   | Copy-paste ohne Struktur |
| Versand kostenlos | 10         | Kostenloser Versand aktiviert            | Versandkosten zu hoch    |
| Handling-Time     | 10         | ≤ 1 Werktag                              | 2+ Werktage              |
| Seller-Feedback   | 10         | ≥ 98% positiv, ≥ 100 Bewertungen         | Zu wenige Bewertungen    |


## 24.3 Otto Listing Scorecard (0–100 Punkte)


| ELEMENT                           | MAX PUNKTE | KRITERIUM FÜR VOLLE PUNKTE           |
| --------------------------------- | ---------- | ------------------------------------ |
| Produktdatenqualität (Otto Score) | 30         | ≥ 85 Otto Product Quality Score      |
| Bilder                            | 20         | ≥ 8 Bilder, 1200x1200px Minimum      |
| Beschreibung                      | 15         | ≥ 200 Wörter, strukturiert, Keywords |
| Attribute vollständig             | 15         | Alle Pflicht + 90% empfohlen         |
| Retourenquote                     | 10         | < 10%                                |
| Lieferzuverlässigkeit             | 10         | > 97% pünktlich                      |


## 24.4 Kaufland Listing Scorecard (0–100 Punkte)


| ELEMENT       | MAX PUNKTE | KRITERIUM FÜR VOLLE PUNKTE        |
| ------------- | ---------- | --------------------------------- |
| EAN korrekt   | 20         | Gültige GS1-EAN, keine Konflikte  |
| Titel         | 15         | 60–150 Zeichen, Keywords, klar    |
| Beschreibung  | 15         | ≥ 150 Zeichen, strukturiert       |
| Bilder        | 15         | ≥ 5 Bilder, min. 800x800px        |
| Attribute     | 15         | Alle Pflichtattribute Kategorie   |
| Preis         | 10         | Wettbewerbsfähig (≤ Markt-Median) |
| Verfügbarkeit | 10         | Immer verfügbar, kein Stockout    |


===============================================================================
# TEIL 25 — ARIA MARKTPLATZ-MONITORING QUERIES
===============================================================================


## 25.1 Listing-Health SQL Queries

```sql
-- Listing-Qualitäts-Übersicht pro Kanal
SELECT
  p.sku,
  p.product_name,
  ml.kanal,
  ml.listing_status,
  ml.listing_quality_score,
  ml.buybox_status,
  ml.current_rank,
  ml.conversion_rate_7d,
  ml.click_through_rate_7d,
  ml.review_count,
  ml.avg_rating,
  ml.last_optimized_at
FROM marketplace_listings ml
JOIN products p ON p.id = ml.product_id
WHERE ml.tenant_id = $1
  AND ml.listing_status = 'active'
ORDER BY ml.listing_quality_score ASC;

-- Listings unter Qualitätsschwelle
SELECT
  p.sku,
  p.product_name,
  ml.kanal,
  ml.listing_quality_score,
  ml.image_count,
  ml.has_a_plus_content,
  ml.backend_keywords_bytes,
  ml.bullet_count
FROM marketplace_listings ml
JOIN products p ON p.id = ml.product_id
WHERE ml.tenant_id = $1
  AND ml.listing_quality_score < 70
ORDER BY ml.listing_quality_score ASC;

-- Keyword-Ranking-Verlauf
SELECT
  kr.keyword,
  kr.kanal,
  kr.rank_today,
  kr.rank_7d_ago,
  kr.rank_30d_ago,
  kr.rank_today - kr.rank_7d_ago AS change_7d,
  p.sku
FROM keyword_rankings kr
JOIN products p ON p.id = kr.product_id
WHERE kr.tenant_id = $1
  AND kr.is_main_keyword = true
ORDER BY ABS(kr.rank_today - kr.rank_7d_ago) DESC;
```


## 25.2 Wettbewerber-Monitoring Queries

```sql
-- Preis-Position vs. Wettbewerber
SELECT
  p.sku,
  ml.kanal,
  ml.current_price,
  ci.competitor_min_price,
  ci.competitor_median_price,
  ci.competitor_count,
  ROUND(100.0 * (ml.current_price - ci.competitor_median_price)
    / ci.competitor_median_price, 1) AS price_vs_median_pct
FROM marketplace_listings ml
JOIN products p ON p.id = ml.product_id
LEFT JOIN competitor_intelligence ci
  ON ci.product_id = ml.product_id AND ci.kanal = ml.kanal
WHERE ml.tenant_id = $1
  AND ci.updated_at >= NOW() - INTERVAL '24 hours'
ORDER BY ABS(ml.current_price - ci.competitor_median_price) DESC;

-- Wettbewerber OOS Tracking
SELECT
  p.sku,
  ml.kanal,
  ci.main_competitor_name,
  ci.main_competitor_stock_status,
  ci.main_competitor_oos_since,
  p.stock_quantity AS our_stock,
  EXTRACT(DAYS FROM (NOW() - ci.main_competitor_oos_since)) AS oos_days
FROM competitor_intelligence ci
JOIN marketplace_listings ml ON ml.id = ci.listing_id
JOIN products p ON p.id = ml.product_id
WHERE ci.tenant_id = $1
  AND ci.main_competitor_stock_status = 'out_of_stock'
ORDER BY oos_days DESC;
```


## 25.3 Performance-Vergleich Kanäle

```sql
-- Umsatz und Marge pro Kanal (Monat)
SELECT
  o.kanal,
  COUNT(DISTINCT o.id) AS bestellungen,
  SUM(oi.quantity) AS einheiten,
  SUM(oi.revenue) AS umsatz_brutto,
  SUM(oi.revenue - oi.platform_fees - oi.cogs) AS deckungsbeitrag,
  ROUND(100.0 * SUM(oi.revenue - oi.platform_fees - oi.cogs)
    / NULLIF(SUM(oi.revenue), 0), 1) AS marge_pct,
  ROUND(SUM(oi.revenue) / COUNT(DISTINCT o.id), 2) AS avg_bestellwert
FROM orders o
JOIN order_items oi ON oi.order_id = o.id
WHERE o.tenant_id = $1
  AND DATE_TRUNC('month', o.ordered_at) = DATE_TRUNC('month', CURRENT_DATE)
GROUP BY o.kanal
ORDER BY umsatz_brutto DESC;
```


===============================================================================
# TEIL 26 — REGULATORISCHES & COMPLIANCE DACH 2025/2026
===============================================================================


## 26.1 EU-Regulierungen die alle Kanäle betreffen


| REGULIERUNG                              | IN KRAFT SEIT          | WAS BETRIFFT ES                  | MASSNAHMEN                                                |
| ---------------------------------------- | ---------------------- | -------------------------------- | --------------------------------------------------------- |
| GPSR (General Product Safety Regulation) | Dez. 2024              | Alle Verbraucherprodukte         | Verantwortliche Person in EU benennen, Rückverfolgbarkeit |
| Verpackungsgesetz (VerpackG)             | 2019 (updates 2024)    | Alle Versandverpackungen         | LUCID-Registrierung, duale Systembeteiligung              |
| Elektrogeräte (WEEE)                     | Laufend                | Elektroprodukte                  | ElektroG-Registrierung                                    |
| CE-Kennzeichnung                         | Laufend                | Viele Produktkategorien          | Konformitätserklärung, technische Dokumentation           |
| Produktinformationsblätter (PIB)         | Produktabhängig        | Energiebezogene Produkte         | EU Energy Label                                           |
| Digital Services Act (DSA)               | Feb. 2024              | Große Plattformen (Amazon, eBay) | Für Verkäufer: Transparenzpflichten                       |
| EU Omnibus-Richtlinie                    | Mai 2022 (D: Jan 2023) | Preisangaben                     | Niedrigster Preis 30 Tage vor Rabatt anzeigen             |


## 26.2 Amazon-spezifische Compliance-Pflichten DACH

```
PFLICHTEN AMAZON.DE (2025):

  GRUNDLEGEND:
    □ Gültige Gewerbeanmeldung (für Pro-Account)
    □ USt-Nummer vorhanden und eingetragen
    □ LUCID-Nummer eingetragen (Verpackungsgesetz)
    □ WEEE-Registrierung wenn Elektroprodukte
    □ Bankverbindung gültig und verifiziert

  PRODUKTBEZOGEN:
    □ CE-Zeichen wenn Produktkategorie CE-pflichtig
    □ GPSR: Responsible Person EU benannt
    □ Sicherheitsdatenblätter wenn Gefahrgut
    □ Altersangaben bei Kinderspielzeug
    □ EN 71 Zertifizierung bei Spielzeug

  LISTING-BEZOGEN:
    □ Widerrufsbelehrung korrekt
    □ Vollständige Lieferantenangaben
    □ Korrekter Steuersatz ausgewiesen
    □ Keine irreführenden Claims
    □ Herkunftsland angegeben wenn pflichtrelevant
```


## 26.3 eBay-spezifische Compliance DACH

```
PFLICHTEN EBAY.DE (2025):

  GRUNDLEGEND:
    □ Gewerbliches Konto wenn > 30 Artikel/Jahr oder gewerbsmäßig
    □ Impressum vollständig (Straße, USt-ID, Handelsregister)
    □ Widerrufsbelehrung in Listings
    □ LUCID-Nummer

  PREISANGABEN:
    □ EU Omnibus: Niedrigster Preis 30 Tage vor Rabatt anzeigen
    □ Grundpreisangabe bei Produkten die nach Gewicht/Menge verkauft werden
    □ MwSt.-Hinweis: 'inkl. MwSt. zzgl. Versandkosten'

  BESONDERHEIT EBAY:
    □ eBay verlangt direkte Widerrufsbelehrung in Listing-Beschreibung
    □ Rückgabepolitik muss eBay-konform sein (14+ Tage für Gewerbliche)
```


===============================================================================
# TEIL 27 — ARIA KANAL-OPTIMIERUNGS-WORKFLOWS
===============================================================================


## 27.1 Monatlicher Listing-Review Workflow

```
MONATLICHER LISTING-HEALTH-REVIEW — ARIA WORKFLOW:

  WOCHE 1 — DATEN SAMMELN:
    □ Keyword-Rankings alle Kanäle exportieren
    □ CVR pro ASIN/Listing vergleichen (aktuell vs. Vormonat)
    □ CTR pro ASIN vergleichen
    □ Wettbewerber-Preis-Snapshot
    □ Neue Wettbewerber in Hauptkategorien identifizieren

  WOCHE 2 — ANALYSIEREN:
    □ Rankings gesunken? Ursache identifizieren
    □ CVR gesunken? Listing-Element-Test
    □ Preis aus dem Markt? Repricing-Strategie prüfen
    □ Neue Keywords aus PPC-Daten identifizieren

  WOCHE 3 — OPTIMIEREN:
    □ Titel für Underperformer überarbeiten
    □ Backend Keywords auffrischen
    □ Bilder tauschen wenn A/B-Test Gewinner bekannt
    □ Item Specifics auf eBay vervollständigen

  WOCHE 4 — MESSEN:
    □ Veränderungen dokumentieren
    □ KPIs vor/nach vergleichen
    □ Nächsten Monat planen
```


## 27.2 Peak-Season Vorbereitung Checkliste


| AUFGABE                                          | TIMING            | KANAL         | PRIORITÄT |
| ------------------------------------------------ | ----------------- | ------------- | --------- |
| FBA-Bestand einliefern (Min. 60-Tage-Reichweite) | 6 Wochen vor Peak | Amazon        | KRITISCH  |
| PPC-Kampagnen Budget erhöhen (+50-100%)          | 2 Wochen vor Peak | Amazon        | HOCH      |
| Saisonale Keywords in Titel/Backend ergänzen     | 3 Wochen vor Peak | Amazon + eBay | HOCH      |
| Preise für Peak optimieren (nicht zu günstig)    | 1 Woche vor Peak  | Alle          | HOCH      |
| Repricing-Regeln auf Peak-Modus schalten         | Woche vor Peak    | Amazon + eBay | HOCH      |
| eBay PLS Ad-Rate auf Trend+2% erhöhen            | 2 Wochen vor Peak | eBay          | MITTEL    |
| Versand-Kapazität sicherstellen                  | 4 Wochen vor Peak | Alle          | KRITISCH  |
| Lager-Personal für Peak organisieren             | 4 Wochen vor Peak | Intern        | KRITISCH  |
| Return-Prozesse vorbereiten (Post-Peak)          | 2 Wochen vor Peak | Alle          | MITTEL    |
| Carrier-Backup vereinbaren                       | 3 Wochen vor Peak | Intern        | MITTEL    |
| ARIA-Alert Daily Cap erhöhen (Peak-Modus)        | 1 Woche vor Peak  | Comentra      | MITTEL    |
| A/B-Tests pausieren während Peak                 | Start Peak        | Amazon        | NIEDRIG   |


## 27.3 Nach Stockout — Ranking-Recovery-Plan

```
RANKING-RECOVERY NACH AMAZON-STOCKOUT:

  TAG 1 NACH WIEDERVERFÜGBARKEIT:
    □ PPC-Budget verfünffachen (Visibility zurückkaufen)
    □ Externe Traffic-Kampagne aktivieren
    □ Preis kurz unter Markt-Median senken (CVR maximieren)

  WOCHE 1-2:
    □ PPC hochhalten (3x Normalbudget)
    □ Velocity aufbauen (Sales-Geschwindigkeit = Ranking-Signal)
    □ Preis wieder auf Normal-Niveau (sobald Ranking stabilisiert)

  WOCHE 3-4:
    □ PPC auf 2x Normalbudget
    □ Keywords prüfen ob alle noch ranken
    □ A/B-Test reaktivieren wenn möglich

  WOCHE 5-8:
    □ Normaler Betrieb
    □ Ranking-Vergleich: vor Stockout vs. jetzt
    □ Bei weiterhin schlechtem Ranking: Listing-Optimierung prüfen

  ERWARTETE ERHOLUNGSZEIT:
    1-2 Tage Stockout:   2-4 Wochen
    3-7 Tage Stockout:   4-8 Wochen
    > 1 Woche Stockout:  8-16 Wochen
    > 1 Monat Stockout:  Ranking teilweise dauerhaft verloren
```


---

*ARIA-MARKTPLAETZE.md — Production Ready*
*Comentra Intelligence Layer*
*Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
===============================================================================
# TEIL 28 — AMAZON A10: INDEXIERUNG & CRAWLING
===============================================================================


## 28.1 Wie Amazon ASINs indexiert

```
AMAZON INDEXIERUNGS-MECHANIK:

  WAS AMAZON INDEXIERT (Keyword erscheint in Suchindex):
    • Produkttitel: vollständig indexiert
    • Backend Keywords (Subject Matter): vollständig indexiert
    • Bullet Points: vollständig indexiert
    • Produktbeschreibung: indexiert (wenn kein A+)
    • A+ Content Text: NICHT direkt indexiert (indirekt durch CVR-Effekt)
    • Bilder-Alt-Text: wird intern genutzt aber nicht direkt indexiert
    • Q&A-Antworten: indexiert
    • Kundenbewertungen: indexiert

  WIE INDEXIERUNG PRÜFEN:
    Methode 1: Amazon Suche 'ASIN B09XYZ keyword'
      → Wenn Listing erscheint: indexiert für dieses Keyword
      → Wenn nicht: nicht indexiert (oder Backend-Fehler)

    Methode 2: Seller Central Brand Analytics → Search Query Report
      → Zeigt für welche Queries das Produkt impressions bekommt

  INDEXIERUNGS-PROBLEME UND URSACHEN:
    Problem: Keyword nicht indexiert obwohl im Titel
    Ursache: Amazon hat das Keyword als verboten/irrelevant markiert

    Problem: Backend Keywords nicht indexiert
    Ursache: Zeichenlimit überschritten, verbotene Zeichen, HTML-Tags

    Problem: Listing komplett aus Index verschwunden
    Ursache: Policy Violation, Listing-Deaktivierung, ASIN-Zusammenführung
```


## 28.2 Amazon Algorithmus-Updates — Timeline


| ZEITRAUM | UPDATE / BEOBACHTUNG                     | AUSWIRKUNG                                     |
| -------- | ---------------------------------------- | ---------------------------------------------- |
| 2021     | A10 Launch                               | Externe Traffic-Signale stark gewichtet        |
| 2022 Q1  | Bewertungs-Recency-Update                | Neue Bewertungen > alte Bewertungen            |
| 2022 Q3  | Keyword-Stuffing-Penalisierung verstärkt | Mehrfach-Keywords bestraft                     |
| 2023 Q1  | Seller Authority globaler                | Account-weite Performance beeinflusst Listings |
| 2023 Q3  | Mobile-CVR-Faktor erhöht                 | Mobile-optimierte Bilder wichtiger             |
| 2024 Q1  | AI-generierte Listings erkannt           | Generic AI-Text ohne Differenzierung bestraft  |
| 2024 Q2  | Brand Analytics erweitert                | Mehr Insights für Brand Registry Brands        |
| 2024 Q3  | A+ Content CVR-Boost bestätigt           | A+ messbar positiver Ranking-Einfluss          |
| 2025     | Generative AI in Suchalgorithmus         | Semantisches Matching verbessert               |
| 2025 Q2  | External Traffic stärker gewichtet       | Google → Amazon Links noch wertvoller          |


## 28.3 Amazon DACH vs. Amazon.com Unterschiede


| ASPEKT             | AMAZON.DE (DACH)             | AMAZON.COM (USA)                           |
| ------------------ | ---------------------------- | ------------------------------------------ |
| Marktgröße         | Kleiner, weniger Wettbewerb  | Massiv, sehr hoher Wettbewerb              |
| Käufer-Verhalten   | Mehr Recherche, vorsichtiger | Schnellere Kaufentscheidungen              |
| Preis-Sensitivität | Sehr hoch                    | Mittel                                     |
| Bewertungs-Anzahl  | Weniger Reviews = ok (< 50)  | > 100 Reviews fast Pflicht für Top-Ranking |
| Marken-Awareness   | Regional/EU-Marken gut       | US-Marken dominant                         |
| FBA-Kosten         | Ähnlich, leicht höher        | Basis-Referenz                             |
| Compliance         | EU-Recht (CE, GPSR, WEEE)    | US-Recht (UL, ASTM)                        |
| Sprache            | Deutsch Pflicht              | Englisch                                   |
| Lieferzeiten       | 1-2 Tage Prime erwartet      | 2-3 Tage Prime standard                    |
| A+ Content         | Gleiche Features             | Mehr Traffik pro A+ Content                |


===============================================================================
# TEIL 29 — EBAY CASSINI: SPEZIALTHEMEN
===============================================================================


## 29.1 eBay Marktplatz-Charakter DACH 2025

```
EBAY.DE KÄUFER-PROFIL 2025:

  DEMOGRAFIK:
    • Breite Altersgruppe: 25–65 Jahre
    • Stärker als Amazon: Gebrauchtwaren-Affinität
    • Starke Sammler-Community
    • Preisbewusste Käufer

  KAUFVERHALTEN:
    • Mehr Vergleiche vor Kauf als Amazon-Käufer
    • Best Offer häufig genutzt
    • Feedback-orientiert (schauen auf Verkäufer-Bewertung)
    • Gebrauchtwaren + Nischenprodukte = eBay-Stärke

  WO EBAY BESONDERS STARK IST (für Neuware):
    ✓ Elektronik-Zubehör
    ✓ Ersatzteile
    ✓ Werkzeug
    ✓ Garten und Outdoor
    ✓ Modellbau / Hobbyartikel
    ✓ Bürobedarf

  WO AMAZON BESSER IST:
    → Neue, populäre Konsumgüter mit hohem Volumen
    → Produkte die von Amazon Prime profitieren
    → Kategorien mit hoher Bewertungsrelevanz
```


## 29.2 eBay Store — Vorteile und Optimierung


| STORE-STUFE | MONATLICHE GEBÜHR | VORTEILE                                       | EMPFEHLUNG                      |
| ----------- | ----------------- | ---------------------------------------------- | ------------------------------- |
| Kein Store  | 0€                | Begrenztes Freilistungs-Kontingent             | Nicht empfohlen für Gewerbliche |
| Basis       | 4,99€/Monat       | 250 kostenlose Festpreis-Angebote              | < 50 aktive Listings            |
| Top         | 29,99€/Monat      | 5.000 kostenlose Angebote, Rabatt auf Gebühren | 100–2000 Listings               |
| Premium     | 99,99€/Monat      | Unbegrenzte Angebote, Max-Rabatt               | > 2000 aktive Listings          |


```
eBay STORE SEO:

  Store-Name:
    • Hauptkeyword der Nische einbauen
    • Markenname wenn bekannt
    • Beispiel: 'Holz-Spielzeug-Welt by [Marke]'

  Store-Beschreibung:
    • Kategorie-Keywords einbauen
    • USP benennen
    • 200–500 Wörter

  Store-Kategorien:
    • Eigene Kategorien für Produkt-Gruppen
    • Käufer-Navigation verbessern
    • Keywords in Kategorie-Namen

  Store-Newsletter (wenn aktiviert):
    • Stammkäufer erneut aktivieren
    • Saisonale Aktionen kommunizieren
```


## 29.3 eBay Verkäufer-Typen und optimale Strategien


| VERKÄUFER-TYP                     | STRATEGIE                                  | CASSINI-OPTIMIERUNG                |
| --------------------------------- | ------------------------------------------ | ---------------------------------- |
| Großhändler (100+ SKUs)           | Bulk-Listing, Item Specifics automatisiert | Feed-Qualität wichtig, TRS halten  |
| Spezialist (10-50 SKUs)           | Tiefe Optimierung pro Listing              | Perfekte Item Specifics, High CVR  |
| Einzelartikel-Händler (1-10 SKUs) | Maximale Einzeloptimierung                 | Alle Hebel ausschöpfen             |
| Eigenmarke                        | Brand-Building + Performance               | Konsistente Qualität, Store nutzen |
| Reseller Gebrauchtware            | Zustand klar kommunizieren                 | Zustandsattribute vollständig      |


===============================================================================
# TEIL 30 — KANAL-SPEZIFISCHE CONTENT-ERSTELLUNG
===============================================================================


## 30.1 Texterstellungs-Prinzipien je Kanal


### Amazon: Benefit-First-Copywriting

```
AMAZON COPYWRITING PRINZIPIEN:

  BULLET-POINT FORMEL (7-Sekunden-Regel):
    Käufer lesen die ersten 3 Worte eines Bullets.
    Diese 3 Worte müssen das Feature benennen.
    Der Rest erklärt den Benefit.

  BEISPIEL (Sandkasten):

  ❌ SCHLECHT:
    'Unser Sandkasten ist aus hochwertigem Fichtenholz gefertigt
    und bietet durch seine robuste Bauweise eine lange Haltbarkeit'

  ✓ GUT:
    'ROBUSTES FICHTENHOLZ 26MM — Im Vergleich zu Standard-Sandkästen
    mit 18mm Holz übersteht dieser Jahrzehnte ohne zu splittern,
    auch bei Dauerregen und direkter Sonneneinstrahlung'

  SCHLÜSSEL-UNTERSCHIED:
    Schlecht: Feature → Feature (kein Benefit)
    Gut: Feature IN CAPS → Benefit (warum interessiert den Käufer das Feature?)

  EMOTIONAL VS. RATIONAL:
    Rationale Features: Maße, Material, Zertifikate, Lieferumfang
    Emotionale Benefits: Sicherheit, Spaß, Stolz, Sorgenfreiheit
    Amazon-Formel: RATIONAL in Caps → EMOTIONAL als Benefit
```


### eBay: Keyword-Dichte-Optimization

```
EBAY BESCHREIBUNGS-STRATEGIE:

  eBay-SPEZIFIK:
    Cassini liest die Beschreibung — Keywords dort geben zusätzliche
    Ranking-Signale (wenn auch schwächer als Titel/Specifics).

  EMPFOHLENE STRUKTUR:
    1. H2-Heading: Produkt-Name + Haupt-Keyword
    2. Einleitungs-Paragraph: 3-5 Sätze, Haupt-Keyword natürlich 2x
    3. Feature-Liste: <ul> mit 5-8 Punkten
       → Keywords in Feature-Beschreibungen einbauen
    4. Technische Daten: <table> mit Maßen, Material, Gewicht
    5. Versand/Rückgabe: Standard-Block (Template)

  KEYWORD-DICHTE EMPFEHLUNG:
    Haupt-Keyword: 3-5x in 500-Wort-Beschreibung
    Neben-Keywords: je 1-2x
    Nicht: mehr als 5x (Keyword Stuffing = Cassini-Strafe)
```


### Otto: Strukturierter Fachdeutsch-Stil

```
OTTO TEXTOPTIMIERUNG:

  OTTO-KÄUFER-CHARAKTER:
    • Qualitätsbewussty, informationsorientiert
    • Erwarten vollständige technische Informationen
    • Weniger Geduld für Marketing-Sprech als Amazon-Käufer

  EMPFOHLENER SCHREIBSTIL FÜR OTTO:
    ✓ Sachlich und präzise
    ✓ Technische Details vollständig
    ✓ Verarbeitung und Material klar benennen
    ✓ Pflegehinweise wenn relevant
    ✓ Montage-Information wenn nötig

  OTTO BESCHREIBUNGS-STRUKTUR:
    Absatz 1: Was ist das Produkt + Hauptnutzen (3-4 Sätze)
    Absatz 2: Material und Verarbeitung
    Absatz 3: Anwendung und Zielgruppe
    Absatz 4: Technische Details (Maße, Gewicht, Lieferumfang)
    Absatz 5: Pflegehinweise / Wartung (wenn relevant)

  WICHTIG FÜR OTTO:
    Retourenquote-Prävention durch Listing:
    → Maßangaben auf 0,5cm genau
    → Materialfotos zeigen echte Textur
    → Montageaufwand ehrlich beschreiben
    → Farbton möglichst realitätsnah (Bildkalibrierung)
```


===============================================================================
# TEIL 31 — AMAZON BRAND ANALYTICS INTERPRETATION
===============================================================================


## 31.1 Search Query Performance Report

```
SEARCH QUERY PERFORMANCE REPORT — METRIKEN:

  VERFÜGBAR NUR FÜR: Brand Registry Verkäufer

  METRIKEN IM REPORT:
    Search Query:           Das gesuchte Keyword
    Search Query Volume:    Wie oft dieses Keyword gesucht wurde
    Impressions:            Wie oft unser Produkt bei diesem Keyword gezeigt wurde
    Clicks:                 Wie oft geklickt wurde
    CTR:                    Klicks / Impressionen
    Basket Adds:            In Warenkorb gelegt
    Purchases:              Tatsächliche Käufe
    CVR:                    Purchases / Clicks

  WAS ARIA DARAUS LERNT:

  SZENARIO 1: Hohe Impressionen, niedrige Klicks
    → Problem: CTR. Lösung: Hauptbild, Preis, Titel
    → ARIA-Alert: AD-003 Variant

  SZENARIO 2: Hohe Klicks, niedrige CVR
    → Problem: Landing Page (Listing). Lösung: Bullets, Bilder, A+
    → ARIA-Alert: Listing-Optimierungs-Empfehlung

  SZENARIO 3: Keyword mit hohem Volumen, 0 Impressionen
    → Nicht indexiert. Lösung: Keyword in Titel/Backend ergänzen
    → ARIA-Alert: Indexierungs-Lücke erkannt

  SZENARIO 4: Keyword mit gutem CVR, wir zeigen nur selten
    → Ranking-Lücke. Lösung: PPC auf dieses Keyword
    → ARIA-Alert: PPC-Opportunity erkannt
```


## 31.2 Marktkorb-Analyse

```
AMAZON MARKTKORB-ANALYSE (Market Basket):

  ZEIGT: Welche Produkte werden zusammen mit unserem Produkt gekauft

  NUTZUNGSMÖGLICHKEITEN:
    1. Bundle-Ideen: häufig zusammengekaufte Produkte bündeln
    2. Cross-Sell: eigene Produkte die häufig mit unserem gekauft werden promoten
    3. Virtual Bundle: FBA-Bundles ohne neuen ASIN erstellen
    4. Wettbewerber-Insights: welche Wettbewerber-Produkte mit uns gekauft werden

  BEISPIEL SANDKASTEN:
    Häufig zusammen gekauft: Spielsand, Sandspielzeug, Sandkastenabdeckung
    → Opportunity: Bundle mit Sandspielzeug-Set
    → Virtual Bundle: Sandkasten + Abdeckplane
```


===============================================================================
# TEIL 32 — KEYWORD-TOOLS UND METHODEN
===============================================================================


## 32.1 Tool-Vergleich für Keyword-Recherche


| TOOL                          | STÄRKE                         | SCHWÄCHE                      | PREIS (2025)           | EMPFEHLUNG       |
| ----------------------------- | ------------------------------ | ----------------------------- | ---------------------- | ---------------- |
| Helium 10 (Cerebro)           | Reverse ASIN, Keyword-Tracking | Komplex, teuer                | ab 39$/Monat           | Top für Amazon   |
| Jungle Scout                  | Marktgrößen-Schätzung          | Weniger Keyword-Tiefe als H10 | ab 49$/Monat           | Amazon Launch    |
| Keyword Tool.io               | Amazon + eBay + Google         | Volumen nur mit Pro           | ab 89$/Monat           | Multi-Kanal      |
| Google Keyword Planner        | Google-Volumen                 | Kein Amazon-Volumen           | Kostenlos (Google Ads) | Externer Traffic |
| eBay Keyword Tool (mächtig)   | eBay-spezifisch                | Limitierte Daten              | Verschiedene Tools     | eBay-spezifisch  |
| Amazon Autocomplete (manuell) | Direkte Amazon-Daten           | Zeitaufwändig, kein Volumen   | Kostenlos              | Quick Check      |
| Brand Analytics (Amazon)      | Offizielle Amazon-Daten        | Nur Brand Registry            | Kostenlos (im Account) | Pflicht nutzen   |


## 32.2 Keyword-Mapping pro Kanal

```
KEYWORD-MAPPING MATRIX (Beispiel: Sandkasten):

  KEYWORD                    AMAZON  EBAY    OTTO    KL
  ──────────────────────────────────────────────────────
  Sandkasten                 Titel   Titel   Titel   Titel
  Sandkasten Holz            Titel   Titel   Titel   Titel
  Sandkiste                  Backend Titel   Descr.  Attr.
  Sandkiste Holz             Backend Titel   Descr.  Attr.
  Sandkasten für Kinder      Bullet  Backend Descr.  Attr.
  Sandkasten wetterfest      Bullet  Specific Attr.  Attr.
  Fichtenholz Sandkasten     Backend Backend Attr.   Attr.
  Sandkasten 150x150         Bullet  Specific Attr.  Attr.
  Spielsandkasten            Backend Backend Descr.  —
  Outdoor Sandkasten         Backend Specific Attr.  Attr.
  Holz Sandkasten Kinder     Backend Backend Descr.  Attr.
  Sandkasten mit Deckel      Bullet  Specific Attr.  Attr.
  FSC Sandkasten             Backend Backend Attr.   —
  Sandkasten ab 2 Jahre      Backend Specific Attr.  Attr.
  playground sandbox         Backend —       —       —
  bac à sable bois           Backend —       —       —

  LEGENDE:
  Titel    = im Produkttitel einbauen
  Bullet   = in Bullet Points einbauen
  Backend  = Backend Keywords / Subject Matter
  Specific = Item Specifics (eBay) / Attribute (Otto/KL)
  Attr.    = Kategorie-Attribute
  Descr.   = Produktbeschreibung
  —        = nicht relevant
```


===============================================================================
# TEIL 33 — ARIA MARKTPLATZ-WISSEN FÜR TÄGLICHE ARBEIT
===============================================================================


## 33.1 Häufige Listing-Fehler und Fixes


| FEHLER                          | KANAL    | SYMPTOM                           | FIX                                            |
| ------------------------------- | -------- | --------------------------------- | ---------------------------------------------- |
| Keyword nicht indexiert         | Amazon   | Kein Ranking obwohl im Titel      | Titel neu speichern, Backend prüfen            |
| Buy Box weg ohne Preisänderung  | Amazon   | Plötzlicher Umsatz-Einbruch       | Seller Central: Account Health prüfen          |
| CVR unter 5% obwohl guter Preis | Amazon   | Traffic aber keine Käufe          | Hauptbild, Bullets, Preis analysieren          |
| Cassini-Ranking eingebrochen    | eBay     | Weniger Impressionen              | Item Specifics prüfen, Defect Rate prüfen      |
| Listing bei Otto abgelehnt      | Otto     | Status 'Fehler' im Portal         | Fehlercodes lesen, Pflichtfelder prüfen        |
| Hohe Retouren auf Otto          | Otto     | Ranking-Einbruch                  | Maßangaben, Bilder, Beschreibung prüfen        |
| EAN-Konflikt auf Kaufland       | Kaufland | Listing wird nicht veröffentlicht | Support kontaktieren, EAN-Eigentümer prüfen    |
| TRS-Status verloren             | eBay     | Ranking-Einbruch                  | Defect Rate-Gründe analysieren, Maßnahmen      |
| FBA-Bestand stranded            | Amazon   | Kosten ohne Umsatz                | Listing für ASIN reaktivieren oder FBA Removal |
| ODR > 0.75%                     | Amazon   | Kontowarnung                      | Alle A-to-Z Claims sofort bearbeiten           |


## 33.2 ARIA Marktplatz-Wissensbasis — Schnell-Referenz

Die wichtigsten Zahlen die ARIA kennen muss:

```
AMAZON SCHNELL-REFERENZ:
  Titelformat:         [Marke] [Hauptkw.] [Feature] [Maß]
  Titellimit:          200 Byte (≈ 150 Zeichen praktisch)
  Backend Keywords:    250 Byte total
  Bullet-Limit:        5 Bullets × 500 Byte
  A+ Content:          Nur Brand Registry
  ODR-Grenze:          1.0% (Warnung bei 0.75%)
  LSR-Grenze:          4.0%
  Pre-Fulfillment CR:  2.5%
  FBA-Vorteil:         +3-5 Rankings vs. FBM equivalent
  Vine:                Max. 30 Reviews, 200€ je ASIN
  Buy Box FBA-Vorteil: Bis +10-15% Preis trotzdem Buy Box

EBAY SCHNELL-REFERENZ:
  Titellimit:          80 Zeichen
  Item Specifics:      Alle ausfüllen (Ranking-kritisch)
  Bilder-Minimum:      1 (Empfehlung: 6+)
  Bilder-Auflösung:    Min. 500px (Empfehlung: 1600px)
  TRS Defect Rate:     ≤ 0.5%
  TRS Late Shipment:   ≤ 3%
  TRS Feedback:        ≥ 98%
  GTC Listing:         Perpetual, immer aktivieren
  PLS Trend Rate:      Kategorie-spezifisch (eBay zeigt Empfehlung)

OTTO SCHNELL-REFERENZ:
  Titellimit:          100 Zeichen empfohlen
  Quality Score Ziel:  > 80
  Quality Score Min.:  60 (darunter: kaum sichtbar)
  Retouren Warn.:      > 15%
  Retouren Krit.:      > 30%
  API Update Latenz:   1-5 Min (Preis/Bestand)
  Neue Listings:       24-72h Prüfzeit

KAUFLAND SCHNELL-REFERENZ:
  EAN:                 Absolut Pflicht
  Titellimit:          255 Zeichen
  Bilder-Minimum:      1 (Empfehlung: 5+)
  Stornoquote Krit.:   > 2%
  Lieferverlässl. Min: 93%
  Produktdaten Min.:   > 50%
```


## 33.3 ARIA Tagesablauf Marktplatz-Überwachung

```
TÄGLICH (automatisch durch ARIA Worker):
  06:30  Morning Briefing: Umsatz gestern, offene Issues
  09:00  Bestandsprüfung: Stockout-Risiken
  10:00  Buy Box Check: Welche ASINs haben Buy Box verloren?
  12:00  PPC-Performance: ACoS, Budget verbraucht?
  14:00  Repricing-Health: Läuft die Engine?
  16:00  Order-Check: Aufgestaut? SLA-Verletzungen?
  18:00  Evening Bundle: LOW/INFO des Tages
  20:00  Review-Check: Neue negative Bewertungen

WÖCHENTLICH (automatisch):
  Mo 08:00  Wochenstart-Bundle: Was ist am Wochenende passiert?
  Mi 10:00  Listing-Quality-Scan: Scores unter 70
  Fr 17:00  Wochenretro + Bestandsplanung Woche+2

MONATLICH (manuell oder Semi-automatisch):
  01.  Monatsbericht: Umsatz, Marge, Trends
  07.  Keyword-Review: Rankings analysieren, Backend auffrischen
  15.  Wettbewerber-Analyse: Neue Anbieter, Preisveränderungen
  25.  Peak-Vorbereitung wenn nächster Monat Peak
```


## 33.4 EmsCraft24-spezifische Optimierungs-Hinweise

```
EMSCRAFT24 PRODUKTPORTFOLIO — KANAL-STRATEGIE:

  SANDKÄSTEN (150cm, 170cm, 190cm):
    Amazon: Haupt-Kanal. FBA bevorzugt (groß und schwer = guter FBA-Margin-Vergleich)
             Titel: 'Brand Sandkasten Holz [Maß] cm Kinder Garten FSC Fichtenholz'
             Saisonpeak: März–Juni (Frühling), September (Spätsommer)

    eBay:   Zweiter Kanal. GTC-Listings, Item Specifics: Maße, Material, Alter
             PLS in Frühlingssaison aktivieren

    Otto:   Dritter Kanal. Vollständige Maßangaben kritisch (Retouren-Prävention)
             Description: Montageaufwand ehrlich beschreiben

  AKUSTIKPANEELE:
    Amazon: Konkurrenzstarke Kategorie. Differenzierung über A+ Content
             Keywords: Schallschutz, Akustikpaneele, Büro, Studio
             Zielgruppe: Home-Office-Nutzer, Studios, Büros

    eBay:   Gute Nische. Weniger Wettbewerb als Amazon
             Professioneller Käufer → vollständige technische Specs

  TREPPENSCHUTZGITTER (CLAMARO):
    Amazon: Stark gesucht. Sicherheitsprodukt → CE-Zertifikat prominenz
             Keywords: Treppenschutzgitter, Kinderschutzgitter, Treppe Gitter
             Bewertungen: Sicherheits-USP kommunizieren

    Otto:   Kaufland-affine Zielgruppe. Vollständige Attribute (Breite, Höhe)

  BILDERRAHMEN (BUBBLE, SFR35, Antik, Memo):
    Amazon: Lifestyle-Bilder kritisch. A+ mit Raumszenen
             Cross-Sell zwischen Rahmenvarianten (Virtual Bundle)

    eBay:   Sammler-affine Zielgruppe bei Antik-Variante
             Standard-Varianten: GTC, Festpreis
```


===============================================================================
# TEIL 34 — GLOSSAR: ALLE MARKTPLATZ-BEGRIFFE
===============================================================================


## 34.1 Amazon-Begriffe


| BEGRIFF        | BEDEUTUNG                                                                   |
| -------------- | --------------------------------------------------------------------------- |
| ASIN           | Amazon Standard Identification Number — eindeutige Produkt-ID auf Amazon    |
| BSR            | Best Seller Rank — Rang in Kategorie basierend auf Verkaufsvolumen          |
| FBA            | Fulfillment by Amazon — Amazon lagert und versendet                         |
| FBM            | Fulfillment by Merchant — Händler versendet selbst                          |
| SFP            | Seller Fulfilled Prime — Händler versendet mit Prime-Garantie               |
| ODR            | Order Defect Rate — Prozent fehlerhafter Bestellungen                       |
| LSR            | Late Shipment Rate — Prozent verspätet versendeter Bestellungen             |
| A+             | Enhanced Brand Content — erweiterter Produktbeschreibungsbereich            |
| CVR            | Conversion Rate — Käufe dividiert durch Besuche                             |
| CTR            | Click-Through Rate — Klicks dividiert durch Impressionen                    |
| ACoS           | Advertising Cost of Sale — Werbekosten dividiert durch Werbeumsatz          |
| ROAS           | Return on Ad Spend — Werbeumsatz dividiert durch Werbekosten                |
| Buy Box        | Haupt-Kaufbutton auf Produktseite — rotiert zwischen Verkäufern             |
| Vine           | Amazon-Programm für kostenlose Produkt-Reviews durch ausgewählte Reviewer   |
| Brand Registry | Amazon-Programm für Marken-Registrierung                                    |
| GS1            | Global Standards Organisation — vergibt offizielle EAN-Codes                |
| Parent ASIN    | Haupt-ASIN die Varianten (Child ASINs) zusammenfasst                        |
| Hijacking      | Fremder Verkäufer übernimmt unberechtigt ein Listing                        |
| Price Parity   | Amazon-Anforderung: Preis nicht dauerhaft höher als auf anderen Plattformen |


## 34.2 eBay-Begriffe


| BEGRIFF             | BEDEUTUNG                                                               |
| ------------------- | ----------------------------------------------------------------------- |
| Cassini             | eBays Suchalgorithmus (seit 2013)                                       |
| Best Match          | Standard-Sortierung der eBay-Suchergebnisse                             |
| TRS                 | Top Rated Seller — Performance-basierter Status                         |
| TRS+                | Erweiterter Top-Rated-Status mit zusätzlichen Anforderungen             |
| Item Specifics      | Strukturierte Kategorie-Attribute in eBay-Listings                      |
| GTC                 | Good Till Cancelled — permanentes Festpreisangebot                      |
| PLS                 | Promoted Listings Standard — CPA-basierte Werbung                       |
| PLA                 | Promoted Listings Advanced — CPC-basierte Werbung                       |
| Defect Rate         | eBay-Metrik für fehlerhafte Transaktionen                               |
| Feedback Score      | eBay-Bewertungssystem für Käufer und Verkäufer                          |
| Best Offer          | Funktion die Käufern ermöglicht ein alternatives Preisangebot zu machen |
| Watchers            | Käufer die ein Listing beobachten                                       |
| Second Chance Offer | Angebot an Bieter auf Auktionen die nicht gewonnen haben                |
| SNAD                | Significantly Not As Described — Käuferschutz-Anspruch                  |
| INR                 | Item Not Received — Käuferschutz-Anspruch                               |


## 34.3 Otto/Kaufland-Begriffe


| BEGRIFF                   | BEDEUTUNG                                                                      |
| ------------------------- | ------------------------------------------------------------------------------ |
| Partner Portal            | Otto-Händler-Backend für Produkt-Upload und Order-Management                   |
| Product Quality Score     | Otto-interner Score für Listing-Qualität (0–100)                               |
| Kaufland Fulfillment (KF) | Kauflands eigenes FBA-Äquivalent                                               |
| SFTP                      | Secure File Transfer Protocol — Datei-Upload-Methode für Produktdaten          |
| GPSR                      | General Product Safety Regulation — EU-Produktsicherheitsverordnung            |
| EAN                       | European Article Number — 13-stelliger Produktbarcode                          |
| GTIN                      | Global Trade Item Number — übergeordnetes Konzept, EAN ist ein Typ             |
| LUCID                     | Deutsches Verpackungsregister — Pflicht für alle Händler mit Versandverpackung |
| CE-Zeichen                | Conformité Européenne — Produktkonformitätskennzeichnung für EU                |
| Händler-Qualitätsscore    | Otto-intern: kombinierter Performance-Score für Händler                        |
| Seller Scorecard          | Kaufland's Performance-Übersicht für Händler                                   |


---

*ARIA-MARKTPLAETZE.md — Production Ready*
*Comentra Intelligence Layer*
*Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*34 Sektionen · Vollständige Ranking-Faktoren · Gewichtungen · Hebel · Verbotenes*
===============================================================================
# TEIL 28 — AMAZON A10: INDEXIERUNG & CRAWLING
===============================================================================


## 28.1 Wie Amazon ASINs indexiert

```
AMAZON INDEXIERUNGS-MECHANIK:

  WAS AMAZON INDEXIERT (Keyword erscheint in Suchindex):
    • Produkttitel: vollständig indexiert
    • Backend Keywords (Subject Matter): vollständig indexiert
    • Bullet Points: vollständig indexiert
    • Produktbeschreibung: indexiert (wenn kein A+)
    • A+ Content Text: NICHT direkt indexiert (indirekt durch CVR-Effekt)
    • Bilder-Alt-Text: wird intern genutzt aber nicht direkt indexiert
    • Q&A-Antworten: indexiert
    • Kundenbewertungen: indexiert

  WIE INDEXIERUNG PRÜFEN:
    Methode 1: Amazon Suche 'ASIN B09XYZ keyword'
      → Wenn Listing erscheint: indexiert für dieses Keyword
      → Wenn nicht: nicht indexiert (oder Backend-Fehler)

    Methode 2: Seller Central Brand Analytics → Search Query Report
      → Zeigt für welche Queries das Produkt impressions bekommt

  INDEXIERUNGS-PROBLEME UND URSACHEN:
    Problem: Keyword nicht indexiert obwohl im Titel
    Ursache: Amazon hat das Keyword als verboten/irrelevant markiert

    Problem: Backend Keywords nicht indexiert
    Ursache: Zeichenlimit überschritten, verbotene Zeichen, HTML-Tags

    Problem: Listing komplett aus Index verschwunden
    Ursache: Policy Violation, Listing-Deaktivierung, ASIN-Zusammenführung
```


## 28.2 Amazon Algorithmus-Updates — Timeline


| ZEITRAUM | UPDATE / BEOBACHTUNG                     | AUSWIRKUNG                                     |
| -------- | ---------------------------------------- | ---------------------------------------------- |
| 2021     | A10 Launch                               | Externe Traffic-Signale stark gewichtet        |
| 2022 Q1  | Bewertungs-Recency-Update                | Neue Bewertungen > alte Bewertungen            |
| 2022 Q3  | Keyword-Stuffing-Penalisierung verstärkt | Mehrfach-Keywords bestraft                     |
| 2023 Q1  | Seller Authority globaler                | Account-weite Performance beeinflusst Listings |
| 2023 Q3  | Mobile-CVR-Faktor erhöht                 | Mobile-optimierte Bilder wichtiger             |
| 2024 Q1  | AI-generierte Listings erkannt           | Generic AI-Text ohne Differenzierung bestraft  |
| 2024 Q2  | Brand Analytics erweitert                | Mehr Insights für Brand Registry Brands        |
| 2024 Q3  | A+ Content CVR-Boost bestätigt           | A+ messbar positiver Ranking-Einfluss          |
| 2025     | Generative AI in Suchalgorithmus         | Semantisches Matching verbessert               |
| 2025 Q2  | External Traffic stärker gewichtet       | Google → Amazon Links noch wertvoller          |


## 28.3 Amazon DACH vs. Amazon.com Unterschiede


| ASPEKT             | AMAZON.DE (DACH)             | AMAZON.COM (USA)                           |
| ------------------ | ---------------------------- | ------------------------------------------ |
| Marktgröße         | Kleiner, weniger Wettbewerb  | Massiv, sehr hoher Wettbewerb              |
| Käufer-Verhalten   | Mehr Recherche, vorsichtiger | Schnellere Kaufentscheidungen              |
| Preis-Sensitivität | Sehr hoch                    | Mittel                                     |
| Bewertungs-Anzahl  | Weniger Reviews = ok (< 50)  | > 100 Reviews fast Pflicht für Top-Ranking |
| Marken-Awareness   | Regional/EU-Marken gut       | US-Marken dominant                         |
| FBA-Kosten         | Ähnlich, leicht höher        | Basis-Referenz                             |
| Compliance         | EU-Recht (CE, GPSR, WEEE)    | US-Recht (UL, ASTM)                        |
| Sprache            | Deutsch Pflicht              | Englisch                                   |
| Lieferzeiten       | 1-2 Tage Prime erwartet      | 2-3 Tage Prime standard                    |
| A+ Content         | Gleiche Features             | Mehr Traffik pro A+ Content                |


===============================================================================
# TEIL 29 — EBAY CASSINI: SPEZIALTHEMEN
===============================================================================


## 29.1 eBay Marktplatz-Charakter DACH 2025

```
EBAY.DE KÄUFER-PROFIL 2025:

  DEMOGRAFIK:
    • Breite Altersgruppe: 25–65 Jahre
    • Stärker als Amazon: Gebrauchtwaren-Affinität
    • Starke Sammler-Community
    • Preisbewusste Käufer

  KAUFVERHALTEN:
    • Mehr Vergleiche vor Kauf als Amazon-Käufer
    • Best Offer häufig genutzt
    • Feedback-orientiert (schauen auf Verkäufer-Bewertung)
    • Gebrauchtwaren + Nischenprodukte = eBay-Stärke

  WO EBAY BESONDERS STARK IST (für Neuware):
    ✓ Elektronik-Zubehör
    ✓ Ersatzteile
    ✓ Werkzeug
    ✓ Garten und Outdoor
    ✓ Modellbau / Hobbyartikel
    ✓ Bürobedarf

  WO AMAZON BESSER IST:
    → Neue, populäre Konsumgüter mit hohem Volumen
    → Produkte die von Amazon Prime profitieren
    → Kategorien mit hoher Bewertungsrelevanz
```


## 29.2 eBay Store — Vorteile und Optimierung


| STORE-STUFE | MONATLICHE GEBÜHR | VORTEILE                                       | EMPFEHLUNG                      |
| ----------- | ----------------- | ---------------------------------------------- | ------------------------------- |
| Kein Store  | 0€                | Begrenztes Freilistungs-Kontingent             | Nicht empfohlen für Gewerbliche |
| Basis       | 4,99€/Monat       | 250 kostenlose Festpreis-Angebote              | < 50 aktive Listings            |
| Top         | 29,99€/Monat      | 5.000 kostenlose Angebote, Rabatt auf Gebühren | 100–2000 Listings               |
| Premium     | 99,99€/Monat      | Unbegrenzte Angebote, Max-Rabatt               | > 2000 aktive Listings          |


```
eBay STORE SEO:

  Store-Name:
    • Hauptkeyword der Nische einbauen
    • Markenname wenn bekannt
    • Beispiel: 'Holz-Spielzeug-Welt by [Marke]'

  Store-Beschreibung:
    • Kategorie-Keywords einbauen
    • USP benennen
    • 200–500 Wörter

  Store-Kategorien:
    • Eigene Kategorien für Produkt-Gruppen
    • Käufer-Navigation verbessern
    • Keywords in Kategorie-Namen

  Store-Newsletter (wenn aktiviert):
    • Stammkäufer erneut aktivieren
    • Saisonale Aktionen kommunizieren
```


## 29.3 eBay Verkäufer-Typen und optimale Strategien


| VERKÄUFER-TYP                     | STRATEGIE                                  | CASSINI-OPTIMIERUNG                |
| --------------------------------- | ------------------------------------------ | ---------------------------------- |
| Großhändler (100+ SKUs)           | Bulk-Listing, Item Specifics automatisiert | Feed-Qualität wichtig, TRS halten  |
| Spezialist (10-50 SKUs)           | Tiefe Optimierung pro Listing              | Perfekte Item Specifics, High CVR  |
| Einzelartikel-Händler (1-10 SKUs) | Maximale Einzeloptimierung                 | Alle Hebel ausschöpfen             |
| Eigenmarke                        | Brand-Building + Performance               | Konsistente Qualität, Store nutzen |
| Reseller Gebrauchtware            | Zustand klar kommunizieren                 | Zustandsattribute vollständig      |


===============================================================================
# TEIL 30 — KANAL-SPEZIFISCHE CONTENT-ERSTELLUNG
===============================================================================


## 30.1 Texterstellungs-Prinzipien je Kanal


### Amazon: Benefit-First-Copywriting

```
AMAZON COPYWRITING PRINZIPIEN:

  BULLET-POINT FORMEL (7-Sekunden-Regel):
    Käufer lesen die ersten 3 Worte eines Bullets.
    Diese 3 Worte müssen das Feature benennen.
    Der Rest erklärt den Benefit.

  BEISPIEL (Sandkasten):

  ❌ SCHLECHT:
    'Unser Sandkasten ist aus hochwertigem Fichtenholz gefertigt
    und bietet durch seine robuste Bauweise eine lange Haltbarkeit'

  ✓ GUT:
    'ROBUSTES FICHTENHOLZ 26MM — Im Vergleich zu Standard-Sandkästen
    mit 18mm Holz übersteht dieser Jahrzehnte ohne zu splittern,
    auch bei Dauerregen und direkter Sonneneinstrahlung'

  SCHLÜSSEL-UNTERSCHIED:
    Schlecht: Feature → Feature (kein Benefit)
    Gut: Feature IN CAPS → Benefit (warum interessiert den Käufer das Feature?)

  EMOTIONAL VS. RATIONAL:
    Rationale Features: Maße, Material, Zertifikate, Lieferumfang
    Emotionale Benefits: Sicherheit, Spaß, Stolz, Sorgenfreiheit
    Amazon-Formel: RATIONAL in Caps → EMOTIONAL als Benefit
```


### eBay: Keyword-Dichte-Optimization

```
EBAY BESCHREIBUNGS-STRATEGIE:

  eBay-SPEZIFIK:
    Cassini liest die Beschreibung — Keywords dort geben zusätzliche
    Ranking-Signale (wenn auch schwächer als Titel/Specifics).

  EMPFOHLENE STRUKTUR:
    1. H2-Heading: Produkt-Name + Haupt-Keyword
    2. Einleitungs-Paragraph: 3-5 Sätze, Haupt-Keyword natürlich 2x
    3. Feature-Liste: <ul> mit 5-8 Punkten
       → Keywords in Feature-Beschreibungen einbauen
    4. Technische Daten: <table> mit Maßen, Material, Gewicht
    5. Versand/Rückgabe: Standard-Block (Template)

  KEYWORD-DICHTE EMPFEHLUNG:
    Haupt-Keyword: 3-5x in 500-Wort-Beschreibung
    Neben-Keywords: je 1-2x
    Nicht: mehr als 5x (Keyword Stuffing = Cassini-Strafe)
```


### Otto: Strukturierter Fachdeutsch-Stil

```
OTTO TEXTOPTIMIERUNG:

  OTTO-KÄUFER-CHARAKTER:
    • Qualitätsbewussty, informationsorientiert
    • Erwarten vollständige technische Informationen
    • Weniger Geduld für Marketing-Sprech als Amazon-Käufer

  EMPFOHLENER SCHREIBSTIL FÜR OTTO:
    ✓ Sachlich und präzise
    ✓ Technische Details vollständig
    ✓ Verarbeitung und Material klar benennen
    ✓ Pflegehinweise wenn relevant
    ✓ Montage-Information wenn nötig

  OTTO BESCHREIBUNGS-STRUKTUR:
    Absatz 1: Was ist das Produkt + Hauptnutzen (3-4 Sätze)
    Absatz 2: Material und Verarbeitung
    Absatz 3: Anwendung und Zielgruppe
    Absatz 4: Technische Details (Maße, Gewicht, Lieferumfang)
    Absatz 5: Pflegehinweise / Wartung (wenn relevant)

  WICHTIG FÜR OTTO:
    Retourenquote-Prävention durch Listing:
    → Maßangaben auf 0,5cm genau
    → Materialfotos zeigen echte Textur
    → Montageaufwand ehrlich beschreiben
    → Farbton möglichst realitätsnah (Bildkalibrierung)
```


===============================================================================
# TEIL 31 — AMAZON BRAND ANALYTICS INTERPRETATION
===============================================================================


## 31.1 Search Query Performance Report

```
SEARCH QUERY PERFORMANCE REPORT — METRIKEN:

  VERFÜGBAR NUR FÜR: Brand Registry Verkäufer

  METRIKEN IM REPORT:
    Search Query:           Das gesuchte Keyword
    Search Query Volume:    Wie oft dieses Keyword gesucht wurde
    Impressions:            Wie oft unser Produkt bei diesem Keyword gezeigt wurde
    Clicks:                 Wie oft geklickt wurde
    CTR:                    Klicks / Impressionen
    Basket Adds:            In Warenkorb gelegt
    Purchases:              Tatsächliche Käufe
    CVR:                    Purchases / Clicks

  WAS ARIA DARAUS LERNT:

  SZENARIO 1: Hohe Impressionen, niedrige Klicks
    → Problem: CTR. Lösung: Hauptbild, Preis, Titel
    → ARIA-Alert: AD-003 Variant

  SZENARIO 2: Hohe Klicks, niedrige CVR
    → Problem: Landing Page (Listing). Lösung: Bullets, Bilder, A+
    → ARIA-Alert: Listing-Optimierungs-Empfehlung

  SZENARIO 3: Keyword mit hohem Volumen, 0 Impressionen
    → Nicht indexiert. Lösung: Keyword in Titel/Backend ergänzen
    → ARIA-Alert: Indexierungs-Lücke erkannt

  SZENARIO 4: Keyword mit gutem CVR, wir zeigen nur selten
    → Ranking-Lücke. Lösung: PPC auf dieses Keyword
    → ARIA-Alert: PPC-Opportunity erkannt
```


## 31.2 Marktkorb-Analyse

```
AMAZON MARKTKORB-ANALYSE (Market Basket):

  ZEIGT: Welche Produkte werden zusammen mit unserem Produkt gekauft

  NUTZUNGSMÖGLICHKEITEN:
    1. Bundle-Ideen: häufig zusammengekaufte Produkte bündeln
    2. Cross-Sell: eigene Produkte die häufig mit unserem gekauft werden promoten
    3. Virtual Bundle: FBA-Bundles ohne neuen ASIN erstellen
    4. Wettbewerber-Insights: welche Wettbewerber-Produkte mit uns gekauft werden

  BEISPIEL SANDKASTEN:
    Häufig zusammen gekauft: Spielsand, Sandspielzeug, Sandkastenabdeckung
    → Opportunity: Bundle mit Sandspielzeug-Set
    → Virtual Bundle: Sandkasten + Abdeckplane
```


===============================================================================
# TEIL 32 — KEYWORD-TOOLS UND METHODEN
===============================================================================


## 32.1 Tool-Vergleich für Keyword-Recherche


| TOOL                          | STÄRKE                         | SCHWÄCHE                      | PREIS (2025)           | EMPFEHLUNG       |
| ----------------------------- | ------------------------------ | ----------------------------- | ---------------------- | ---------------- |
| Helium 10 (Cerebro)           | Reverse ASIN, Keyword-Tracking | Komplex, teuer                | ab 39$/Monat           | Top für Amazon   |
| Jungle Scout                  | Marktgrößen-Schätzung          | Weniger Keyword-Tiefe als H10 | ab 49$/Monat           | Amazon Launch    |
| Keyword Tool.io               | Amazon + eBay + Google         | Volumen nur mit Pro           | ab 89$/Monat           | Multi-Kanal      |
| Google Keyword Planner        | Google-Volumen                 | Kein Amazon-Volumen           | Kostenlos (Google Ads) | Externer Traffic |
| eBay Keyword Tool (mächtig)   | eBay-spezifisch                | Limitierte Daten              | Verschiedene Tools     | eBay-spezifisch  |
| Amazon Autocomplete (manuell) | Direkte Amazon-Daten           | Zeitaufwändig, kein Volumen   | Kostenlos              | Quick Check      |
| Brand Analytics (Amazon)      | Offizielle Amazon-Daten        | Nur Brand Registry            | Kostenlos (im Account) | Pflicht nutzen   |


## 32.2 Keyword-Mapping pro Kanal

```
KEYWORD-MAPPING MATRIX (Beispiel: Sandkasten):

  KEYWORD                    AMAZON  EBAY    OTTO    KL
  ──────────────────────────────────────────────────────
  Sandkasten                 Titel   Titel   Titel   Titel
  Sandkasten Holz            Titel   Titel   Titel   Titel
  Sandkiste                  Backend Titel   Descr.  Attr.
  Sandkiste Holz             Backend Titel   Descr.  Attr.
  Sandkasten für Kinder      Bullet  Backend Descr.  Attr.
  Sandkasten wetterfest      Bullet  Specific Attr.  Attr.
  Fichtenholz Sandkasten     Backend Backend Attr.   Attr.
  Sandkasten 150x150         Bullet  Specific Attr.  Attr.
  Spielsandkasten            Backend Backend Descr.  —
  Outdoor Sandkasten         Backend Specific Attr.  Attr.
  Holz Sandkasten Kinder     Backend Backend Descr.  Attr.
  Sandkasten mit Deckel      Bullet  Specific Attr.  Attr.
  FSC Sandkasten             Backend Backend Attr.   —
  Sandkasten ab 2 Jahre      Backend Specific Attr.  Attr.
  playground sandbox         Backend —       —       —
  bac à sable bois           Backend —       —       —

  LEGENDE:
  Titel    = im Produkttitel einbauen
  Bullet   = in Bullet Points einbauen
  Backend  = Backend Keywords / Subject Matter
  Specific = Item Specifics (eBay) / Attribute (Otto/KL)
  Attr.    = Kategorie-Attribute
  Descr.   = Produktbeschreibung
  —        = nicht relevant
```


===============================================================================
# TEIL 33 — ARIA MARKTPLATZ-WISSEN FÜR TÄGLICHE ARBEIT
===============================================================================


## 33.1 Häufige Listing-Fehler und Fixes


| FEHLER                          | KANAL    | SYMPTOM                           | FIX                                            |
| ------------------------------- | -------- | --------------------------------- | ---------------------------------------------- |
| Keyword nicht indexiert         | Amazon   | Kein Ranking obwohl im Titel      | Titel neu speichern, Backend prüfen            |
| Buy Box weg ohne Preisänderung  | Amazon   | Plötzlicher Umsatz-Einbruch       | Seller Central: Account Health prüfen          |
| CVR unter 5% obwohl guter Preis | Amazon   | Traffic aber keine Käufe          | Hauptbild, Bullets, Preis analysieren          |
| Cassini-Ranking eingebrochen    | eBay     | Weniger Impressionen              | Item Specifics prüfen, Defect Rate prüfen      |
| Listing bei Otto abgelehnt      | Otto     | Status 'Fehler' im Portal         | Fehlercodes lesen, Pflichtfelder prüfen        |
| Hohe Retouren auf Otto          | Otto     | Ranking-Einbruch                  | Maßangaben, Bilder, Beschreibung prüfen        |
| EAN-Konflikt auf Kaufland       | Kaufland | Listing wird nicht veröffentlicht | Support kontaktieren, EAN-Eigentümer prüfen    |
| TRS-Status verloren             | eBay     | Ranking-Einbruch                  | Defect Rate-Gründe analysieren, Maßnahmen      |
| FBA-Bestand stranded            | Amazon   | Kosten ohne Umsatz                | Listing für ASIN reaktivieren oder FBA Removal |
| ODR > 0.75%                     | Amazon   | Kontowarnung                      | Alle A-to-Z Claims sofort bearbeiten           |


## 33.2 ARIA Marktplatz-Wissensbasis — Schnell-Referenz

Die wichtigsten Zahlen die ARIA kennen muss:

```
AMAZON SCHNELL-REFERENZ:
  Titelformat:         [Marke] [Hauptkw.] [Feature] [Maß]
  Titellimit:          200 Byte (≈ 150 Zeichen praktisch)
  Backend Keywords:    250 Byte total
  Bullet-Limit:        5 Bullets × 500 Byte
  A+ Content:          Nur Brand Registry
  ODR-Grenze:          1.0% (Warnung bei 0.75%)
  LSR-Grenze:          4.0%
  Pre-Fulfillment CR:  2.5%
  FBA-Vorteil:         +3-5 Rankings vs. FBM equivalent
  Vine:                Max. 30 Reviews, 200€ je ASIN
  Buy Box FBA-Vorteil: Bis +10-15% Preis trotzdem Buy Box

EBAY SCHNELL-REFERENZ:
  Titellimit:          80 Zeichen
  Item Specifics:      Alle ausfüllen (Ranking-kritisch)
  Bilder-Minimum:      1 (Empfehlung: 6+)
  Bilder-Auflösung:    Min. 500px (Empfehlung: 1600px)
  TRS Defect Rate:     ≤ 0.5%
  TRS Late Shipment:   ≤ 3%
  TRS Feedback:        ≥ 98%
  GTC Listing:         Perpetual, immer aktivieren
  PLS Trend Rate:      Kategorie-spezifisch (eBay zeigt Empfehlung)

OTTO SCHNELL-REFERENZ:
  Titellimit:          100 Zeichen empfohlen
  Quality Score Ziel:  > 80
  Quality Score Min.:  60 (darunter: kaum sichtbar)
  Retouren Warn.:      > 15%
  Retouren Krit.:      > 30%
  API Update Latenz:   1-5 Min (Preis/Bestand)
  Neue Listings:       24-72h Prüfzeit

KAUFLAND SCHNELL-REFERENZ:
  EAN:                 Absolut Pflicht
  Titellimit:          255 Zeichen
  Bilder-Minimum:      1 (Empfehlung: 5+)
  Stornoquote Krit.:   > 2%
  Lieferverlässl. Min: 93%
  Produktdaten Min.:   > 50%
```


## 33.3 ARIA Tagesablauf Marktplatz-Überwachung

```
TÄGLICH (automatisch durch ARIA Worker):
  06:30  Morning Briefing: Umsatz gestern, offene Issues
  09:00  Bestandsprüfung: Stockout-Risiken
  10:00  Buy Box Check: Welche ASINs haben Buy Box verloren?
  12:00  PPC-Performance: ACoS, Budget verbraucht?
  14:00  Repricing-Health: Läuft die Engine?
  16:00  Order-Check: Aufgestaut? SLA-Verletzungen?
  18:00  Evening Bundle: LOW/INFO des Tages
  20:00  Review-Check: Neue negative Bewertungen

WÖCHENTLICH (automatisch):
  Mo 08:00  Wochenstart-Bundle: Was ist am Wochenende passiert?
  Mi 10:00  Listing-Quality-Scan: Scores unter 70
  Fr 17:00  Wochenretro + Bestandsplanung Woche+2

MONATLICH (manuell oder Semi-automatisch):
  01.  Monatsbericht: Umsatz, Marge, Trends
  07.  Keyword-Review: Rankings analysieren, Backend auffrischen
  15.  Wettbewerber-Analyse: Neue Anbieter, Preisveränderungen
  25.  Peak-Vorbereitung wenn nächster Monat Peak
```


## 33.4 EmsCraft24-spezifische Optimierungs-Hinweise

```
EMSCRAFT24 PRODUKTPORTFOLIO — KANAL-STRATEGIE:

  SANDKÄSTEN (150cm, 170cm, 190cm):
    Amazon: Haupt-Kanal. FBA bevorzugt (groß und schwer = guter FBA-Margin-Vergleich)
             Titel: 'Brand Sandkasten Holz [Maß] cm Kinder Garten FSC Fichtenholz'
             Saisonpeak: März–Juni (Frühling), September (Spätsommer)

    eBay:   Zweiter Kanal. GTC-Listings, Item Specifics: Maße, Material, Alter
             PLS in Frühlingssaison aktivieren

    Otto:   Dritter Kanal. Vollständige Maßangaben kritisch (Retouren-Prävention)
             Description: Montageaufwand ehrlich beschreiben

  AKUSTIKPANEELE:
    Amazon: Konkurrenzstarke Kategorie. Differenzierung über A+ Content
             Keywords: Schallschutz, Akustikpaneele, Büro, Studio
             Zielgruppe: Home-Office-Nutzer, Studios, Büros

    eBay:   Gute Nische. Weniger Wettbewerb als Amazon
             Professioneller Käufer → vollständige technische Specs

  TREPPENSCHUTZGITTER (CLAMARO):
    Amazon: Stark gesucht. Sicherheitsprodukt → CE-Zertifikat prominenz
             Keywords: Treppenschutzgitter, Kinderschutzgitter, Treppe Gitter
             Bewertungen: Sicherheits-USP kommunizieren

    Otto:   Kaufland-affine Zielgruppe. Vollständige Attribute (Breite, Höhe)

  BILDERRAHMEN (BUBBLE, SFR35, Antik, Memo):
    Amazon: Lifestyle-Bilder kritisch. A+ mit Raumszenen
             Cross-Sell zwischen Rahmenvarianten (Virtual Bundle)

    eBay:   Sammler-affine Zielgruppe bei Antik-Variante
             Standard-Varianten: GTC, Festpreis
```


===============================================================================
# TEIL 34 — GLOSSAR: ALLE MARKTPLATZ-BEGRIFFE
===============================================================================


## 34.1 Amazon-Begriffe


| BEGRIFF        | BEDEUTUNG                                                                   |
| -------------- | --------------------------------------------------------------------------- |
| ASIN           | Amazon Standard Identification Number — eindeutige Produkt-ID auf Amazon    |
| BSR            | Best Seller Rank — Rang in Kategorie basierend auf Verkaufsvolumen          |
| FBA            | Fulfillment by Amazon — Amazon lagert und versendet                         |
| FBM            | Fulfillment by Merchant — Händler versendet selbst                          |
| SFP            | Seller Fulfilled Prime — Händler versendet mit Prime-Garantie               |
| ODR            | Order Defect Rate — Prozent fehlerhafter Bestellungen                       |
| LSR            | Late Shipment Rate — Prozent verspätet versendeter Bestellungen             |
| A+             | Enhanced Brand Content — erweiterter Produktbeschreibungsbereich            |
| CVR            | Conversion Rate — Käufe dividiert durch Besuche                             |
| CTR            | Click-Through Rate — Klicks dividiert durch Impressionen                    |
| ACoS           | Advertising Cost of Sale — Werbekosten dividiert durch Werbeumsatz          |
| ROAS           | Return on Ad Spend — Werbeumsatz dividiert durch Werbekosten                |
| Buy Box        | Haupt-Kaufbutton auf Produktseite — rotiert zwischen Verkäufern             |
| Vine           | Amazon-Programm für kostenlose Produkt-Reviews durch ausgewählte Reviewer   |
| Brand Registry | Amazon-Programm für Marken-Registrierung                                    |
| GS1            | Global Standards Organisation — vergibt offizielle EAN-Codes                |
| Parent ASIN    | Haupt-ASIN die Varianten (Child ASINs) zusammenfasst                        |
| Hijacking      | Fremder Verkäufer übernimmt unberechtigt ein Listing                        |
| Price Parity   | Amazon-Anforderung: Preis nicht dauerhaft höher als auf anderen Plattformen |


## 34.2 eBay-Begriffe


| BEGRIFF             | BEDEUTUNG                                                               |
| ------------------- | ----------------------------------------------------------------------- |
| Cassini             | eBays Suchalgorithmus (seit 2013)                                       |
| Best Match          | Standard-Sortierung der eBay-Suchergebnisse                             |
| TRS                 | Top Rated Seller — Performance-basierter Status                         |
| TRS+                | Erweiterter Top-Rated-Status mit zusätzlichen Anforderungen             |
| Item Specifics      | Strukturierte Kategorie-Attribute in eBay-Listings                      |
| GTC                 | Good Till Cancelled — permanentes Festpreisangebot                      |
| PLS                 | Promoted Listings Standard — CPA-basierte Werbung                       |
| PLA                 | Promoted Listings Advanced — CPC-basierte Werbung                       |
| Defect Rate         | eBay-Metrik für fehlerhafte Transaktionen                               |
| Feedback Score      | eBay-Bewertungssystem für Käufer und Verkäufer                          |
| Best Offer          | Funktion die Käufern ermöglicht ein alternatives Preisangebot zu machen |
| Watchers            | Käufer die ein Listing beobachten                                       |
| Second Chance Offer | Angebot an Bieter auf Auktionen die nicht gewonnen haben                |
| SNAD                | Significantly Not As Described — Käuferschutz-Anspruch                  |
| INR                 | Item Not Received — Käuferschutz-Anspruch                               |


## 34.3 Otto/Kaufland-Begriffe


| BEGRIFF                   | BEDEUTUNG                                                                      |
| ------------------------- | ------------------------------------------------------------------------------ |
| Partner Portal            | Otto-Händler-Backend für Produkt-Upload und Order-Management                   |
| Product Quality Score     | Otto-interner Score für Listing-Qualität (0–100)                               |
| Kaufland Fulfillment (KF) | Kauflands eigenes FBA-Äquivalent                                               |
| SFTP                      | Secure File Transfer Protocol — Datei-Upload-Methode für Produktdaten          |
| GPSR                      | General Product Safety Regulation — EU-Produktsicherheitsverordnung            |
| EAN                       | European Article Number — 13-stelliger Produktbarcode                          |
| GTIN                      | Global Trade Item Number — übergeordnetes Konzept, EAN ist ein Typ             |
| LUCID                     | Deutsches Verpackungsregister — Pflicht für alle Händler mit Versandverpackung |
| CE-Zeichen                | Conformité Européenne — Produktkonformitätskennzeichnung für EU                |
| Händler-Qualitätsscore    | Otto-intern: kombinierter Performance-Score für Händler                        |
| Seller Scorecard          | Kaufland's Performance-Übersicht für Händler                                   |


---

*ARIA-MARKTPLAETZE.md — Production Ready*
*Comentra Intelligence Layer*
*Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*34 Sektionen · Vollständige Ranking-Faktoren · Gewichtungen · Hebel · Verbotenes*
===============================================================================
# TEIL 35 — AMAZON A10: MOBILE OPTIMIERUNG
===============================================================================


## 35.1 Mobile vs. Desktop Unterschiede

```
AMAZON MOBILE NUTZUNG DACH (2025):
  ~62% aller Amazon-Suchanfragen kommen von Mobilgeräten.
  Mobile CVR ist typisch 15-25% niedriger als Desktop.
  Mobile-Optimierung = direkte CVR-Steigerung.

WAS AUF MOBILE ANDERS DARGESTELLT WIRD:

  TITEL:
    Desktop: erste 80-100 Zeichen sichtbar
    Mobile:  erste 60-80 Zeichen sichtbar
    → Wichtigste Keywords müssen in die ersten 60 Zeichen

  BILDER:
    Desktop: Haupt + 6 Thumbnails sichtbar
    Mobile:  Swipe-Galerie, Hauptbild dominant
    → Hauptbild ist auf Mobile noch kritischer
    → Zoom-Funktion oft nicht genutzt → Produkt muss ohne Zoom erkennbar sein

  BULLET POINTS:
    Desktop: alle 5 sichtbar
    Mobile:  oft nur 3 initial sichtbar (mehr durch 'Mehr anzeigen')
    → Erste 3 Bullets sind entscheidend

  A+ CONTENT:
    Desktop: volle Breite, side-by-side Layouts wirken gut
    Mobile:  stacked Layouts, kein side-by-side
    → A+ Module müssen mobil funktionieren
    → Zu viele Module = lange Ladezeit = Abbruch

  PREIS:
    Mobile:  Preis sehr prominent (oben rechts neben Hauptbild)
    → Preis und Prime-Badge sind erste Kauf-Signale auf Mobile
```


## 35.2 Mobile-optimierte Bilder

```
BILD-STRATEGIE FÜR MOBILE:

  HAUPTBILD mobile-optimiert:
    • Produkt nimmt > 90% der Fläche ein (noch mehr als Desktop-Standard)
    • Keine winzigen Details die auf Mobile nicht erkennbar sind
    • Kontrastreiche Farben wenn Produkt farbig
    • Produktname/Marke NICHT im Hauptbild (nicht erlaubt, auch nicht nötig)

  INFOGRAFIK-BILDER für Mobile:
    • Große, gut lesbare Schrift (min. 24pt Äquivalent nach Skalierung)
    • Maximal 3 Key-Points pro Bild (nicht 6-8 wie auf Desktop lesbar)
    • Icons groß und eindeutig
    • Wenig Text pro Bild

  LIFESTYLE-BILDER für Mobile:
    • Produkt im Mittelpunkt (nicht in weitem Kontext verloren)
    • Emotionale Wirkung muss auf kleinem Screen funktionieren
```


===============================================================================
# TEIL 36 — EBAY CASSINI: KATEGORIE-SPEZIFIKA
===============================================================================


## 36.1 Kategorie-Unterschiede im Cassini-Ranking

```
EBAY KATEGORIEN MIT BESONDEREN RANKING-RULES:

  ELEKTRONIK (Computer, Telefone, Kameras):
    • Technische Spezifikationen in Item Specifics sehr wichtig
    • Modellnummer-Exaktheit kritisch
    • Zustand-Angabe (Neu, wie Neu, Gebraucht) sehr wichtig
    • Kompatibilitätsliste (wenn Zubehör)

  MODE & BEKLEIDUNG:
    • Größentabellen in Item Specifics Pflicht
    • Material-Angabe wichtig
    • Stil-Keywords (casual, formal, sport)
    • Bilder aus verschiedenen Winkeln wichtig (Rück-, Seitenansicht)

  MÖBEL & WOHNEN:
    • Maße in cm pflichtartig angeben
    • Material und Oberfläche detailliert
    • Montage-Hinweis wenn nötig
    • Gewicht für Versandkosten-Transparenz

  GARTEN & OUTDOOR:
    • Wetterfestigkeit angeben
    • Maße besonders wichtig
    • Materialqualität (FSC, Herkunftsland)
    • Saisonales Timing für Listing-Refresh

  SPIELZEUG & SPIELE:
    • Altersempfehlung in Item Specifics Pflicht
    • Sicherheitszertifikate (CE, EN 71) angeben
    • Material (kein BPA, FSC-Holz usw.)
    • Spielzeugtyp (Sandspielzeug, Bauspielzeug usw.)
```


===============================================================================
# TEIL 37 — OTTO LISTING-OPTIMIERUNG DEEP DIVE
===============================================================================


## 37.1 Otto Produktbeschreibungs-Templates

```
OTTO PRODUKTBESCHREIBUNGS-TEMPLATE (Sandkasten-Beispiel):

[PRODUKT-NAME] — [HAUPTBENEFIT]

Entdecken Sie [KURZE PRODUKTBESCHREIBUNG] — die ideale Lösung für [ZIELGRUPPE].
[2-3 Sätze mit wichtigstem Nutzen. Hauptkeyword einmal.]

Hochwertige Verarbeitung:
• [Feature 1]: [Benefit in einem Satz]
• [Feature 2]: [Benefit in einem Satz]
• [Feature 3]: [Benefit in einem Satz]
• [Feature 4]: [Benefit in einem Satz]

Technische Details:
• Maße: [Breite] x [Tiefe] x [Höhe] cm
• Material: [Genaue Materialangabe]
• Gewicht: [kg]
• Lieferumfang: [Was ist alles dabei]

[Abschluss-Satz: Qualitäts- oder Service-Versprechen]

---

GEFÜLLTES BEISPIEL (Sandkasten):

Holz-Sandkasten 150x150 cm — Robustes Spielspaß für den Garten

Dieser wetterfeste Holz-Sandkasten aus massivem Fichtenholz bietet Kindern ab
2 Jahren ausreichend Platz für kreatives Sandspiel. Die 26mm starken Holzbretter
gewährleisten eine außergewöhnliche Stabilität und lange Lebensdauer.

Hochwertige Verarbeitung:
• Massives Fichtenholz 26mm: Deutlich dicker als Standard (18mm) für maximale Stabilität
• Wetterfeste Oberfläche: Behandelt gegen Feuchtigkeit und UV-Strahlung
• Sichere Ecken: Alle Kanten abgerundet — kein Verletzungsrisiko
• Einfache Montage: Komplett-Set mit Schrauben und Anleitung — in 30 Min aufgebaut

Technische Details:
• Maße: 150 x 150 x 25 cm (L x B x H)
• Material: Fichtenholz massiv, 26mm stark
• Gewicht: ca. 18,5 kg
• Lieferumfang: 4 Seitenteile, Montageschrauben, Anleitung

Hergestellt in Deutschland — inkl. 24 Monate Händler-Garantie.
```


## 37.2 Otto API — Wichtige Endpunkte für Comentra

```typescript
// services/marketplace/otto/otto-api.service.ts

const OTTO_BASE_URL = 'https://api.otto.market'

// Produkt-Upload
async function uploadProducts(products: OttoProduct[]): Promise<void> {
  const response = await fetch(`${OTTO_BASE_URL}/v3/products`, {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${await getOttoToken()}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ products })
  })
  // Returns upload task ID — status muss separat abgerufen werden
}

// Preis-Update (schnellste Methode: direkt via Preise-Endpoint)
async function updatePrices(prices: OttoPrice[]): Promise<void> {
  await fetch(`${OTTO_BASE_URL}/v3/prices`, {
    method: 'POST',
    headers: { 'Authorization': `Bearer ${await getOttoToken()}` },
    body: JSON.stringify({ prices })
  })
  // Preis-Update: 1-5 Minuten bis live
}

// Bestand-Update
async function updateQuantities(quantities: OttoQuantity[]): Promise<void> {
  await fetch(`${OTTO_BASE_URL}/v3/quantities`, {
    method: 'POST',
    headers: { 'Authorization': `Bearer ${await getOttoToken()}` },
    body: JSON.stringify({ quantities })
  })
}

// Order-Abruf (alle neuen Orders)
async function getNewOrders(): Promise<OttoOrder[]> {
  const response = await fetch(
    `${OTTO_BASE_URL}/v4/orders?fulfillmentStatus=ANNOUNCED&limit=50`,
    { headers: { 'Authorization': `Bearer ${await getOttoToken()}` } }
  )
  const data = await response.json()
  return data.resources ?? []
}

// Sendung melden
async function shipOrder(shipment: OttoShipment): Promise<void> {
  await fetch(`${OTTO_BASE_URL}/v4/shipments`, {
    method: 'POST',
    headers: { 'Authorization': `Bearer ${await getOttoToken()}` },
    body: JSON.stringify(shipment)
  })
}
```


===============================================================================
# TEIL 38 — KANAL-PERFORMANCE-BENCHMARKS DACH 2025
===============================================================================


## 38.1 Umsatz-Marktanteile Online DACH


| MARKTPLATZ               | MARKTANTEIL DACH | WACHSTUM 2024 | ZIELGRUPPE STÄRKE                 |
| ------------------------ | ---------------- | ------------- | --------------------------------- |
| Amazon.de                | ~55%             | +8%           | Alle Kategorien, starke Breite    |
| Otto.de                  | ~8%              | +3%           | Möbel, Mode, Haushalt             |
| eBay.de                  | ~7%              | -2%           | Gebrauchtware, Elektronik, Nische |
| Zalando                  | ~6%              | +5%           | Mode und Schuhe                   |
| Kaufland.de              | ~3%              | +15%          | Haushalt, Garten, Elektronik      |
| MediaMarkt/Saturn Online | ~4%              | +2%           | Elektronik                        |
| Andere                   | ~17%             | Mix           | Spezial-Shops, DTC-Brands         |


## 38.2 Typische KPIs nach Kanal DACH


| KPI                         | AMAZON.DE      | EBAY.DE         | OTTO.DE     | KAUFLAND.DE |
| --------------------------- | -------------- | --------------- | ----------- | ----------- |
| Ø Conversion Rate           | 8-15%          | 3-8%            | 4-10%       | 3-7%        |
| Ø Bewertungs-Rate           | 2-4% der Käufe | 5-10% der Käufe | 3-6%        | 2-4%        |
| Ø Retourenquote (Mode)      | 25-40%         | 20-35%          | 20-35%      | 15-25%      |
| Ø Retourenquote (Outdoor)   | 8-15%          | 5-12%           | 10-18%      | 6-12%       |
| Ø Verkäufer-Marge nach Fees | 25-45%         | 30-50%          | 25-40%      | 28-45%      |
| Ø Plattform-Gebühr          | 10-15%         | 7-12%           | 12-18%      | 8-15%       |
| Ø Customer Lifetime Value   | Hoch           | Mittel          | Mittel-Hoch | Mittel      |
| Wiederkäufer-Rate           | 35-45%         | 25-35%          | 30-40%      | 20-30%      |


## 38.3 Empfohlene Ressourcen-Allokation

```
RESSOURCEN-ALLOKATION FÜR EMSCRAFT24 (Empfehlung ARIA):

  LISTING-AUFWAND PRO KANAL (% der Optimierungs-Zeit):
    Amazon:   55% — Haupt-Kanal, höchste Marge-Potential
    eBay:     25% — Zweiter Kanal, etabliert, wichtig für Bewertungs-Basis
    Otto:     15% — Wachstums-Kanal, Qualitäts-Score kritisch
    Kaufland: 5%  — Aufbau-Phase, niedrige Priorität

  PPC-BUDGET PRO KANAL:
    Amazon:   70% des PPC-Gesamtbudgets
    eBay PLS: 30% des PPC-Gesamtbudgets
    Otto/KL:  0% (kein direktes PPC verfügbar)

  BESTAND-ALLOKATION (wenn FBA genutzt):
    FBA-ready: 40-50% Gesamtbestand
    FBM/Eigen: 50-60% Gesamtbestand
    Ziel: Stockout-Risiko minimieren auf allen Kanälen gleichzeitig
```


===============================================================================
# TEIL 39 — ARIA MARKTPLATZ TYPESCRIPT SERVICES
===============================================================================


## 39.1 Listing Quality Checker

```typescript
// services/aria/marketplace/listing-quality-checker.ts

export interface ListingQualityResult {
  score: number  // 0-100
  empfehlungen: QualityEmpfehlung[]
  fehlend_kritisch: string[]
  fehlend_empfohlen: string[]
}

export interface QualityEmpfehlung {
  element: string
  aktuell: string
  empfohlen: string
  prioritaet: 'hoch' | 'mittel' | 'niedrig'
  erwarteter_cvr_lift: string
}

export function checkAmazonListingQuality(
  listing: AmazonListing
): ListingQualityResult {
  let score = 0
  const empfehlungen: QualityEmpfehlung[] = []
  const fehlend_kritisch: string[] = []
  const fehlend_empfohlen: string[] = []

  // HAUPTBILD (20 Punkte)
  if (listing.mainImageWidth >= 2000 && listing.mainImageHeight >= 2000) {
    score += 20
  } else if (listing.mainImageWidth >= 1000) {
    score += 12
    empfehlungen.push({
      element: 'Hauptbild Auflösung',
      aktuell: `${listing.mainImageWidth}x${listing.mainImageHeight}px`,
      empfohlen: 'min. 2000x2000px für Zoom-Funktion',
      prioritaet: 'hoch',
      erwarteter_cvr_lift: '+3-8% CTR'
    })
  } else {
    score += 4
    fehlend_kritisch.push('Hauptbild unter 1000px — Zoom-Funktion deaktiviert')
  }

  // BILD-ANZAHL (15 Punkte)
  if (listing.imageCount >= 7) score += 15
  else if (listing.imageCount >= 5) {
    score += 10
    empfehlungen.push({
      element: 'Bild-Anzahl',
      aktuell: `${listing.imageCount} Bilder`,
      empfohlen: '7+ Bilder (Lifestyle, Detail, Infografik)',
      prioritaet: 'mittel',
      erwarteter_cvr_lift: '+2-5% CVR'
    })
  } else {
    score += 3
    fehlend_kritisch.push(`Nur ${listing.imageCount} Bilder — mindestens 7 empfohlen`)
  }

  // TITEL (15 Punkte)
  const titleBytes = Buffer.byteLength(listing.title, 'utf8')
  if (titleBytes >= 80 && titleBytes <= 150) score += 15
  else if (titleBytes >= 50 && titleBytes < 80) {
    score += 8
    empfehlungen.push({
      element: 'Titel Länge',
      aktuell: `${titleBytes} Byte`,
      empfohlen: '80-150 Byte mit Haupt-Keywords vorne',
      prioritaet: 'hoch',
      erwarteter_cvr_lift: '+5-10% Keyword-Abdeckung'
    })
  } else if (titleBytes > 150) {
    score += 8
    empfehlungen.push({
      element: 'Titel zu lang',
      aktuell: `${titleBytes} Byte`,
      empfohlen: 'Max. 150 Byte, Titel kürzen ohne Keywords zu verlieren',
      prioritaet: 'mittel',
      erwarteter_cvr_lift: 'Verhindert Abschneiden in Suchergebnissen'
    })
  }

  // BULLETS (15 Punkte)
  if (listing.bulletCount === 5 && listing.avgBulletLength >= 80) score += 15
  else if (listing.bulletCount >= 3) score += 8
  else {
    fehlend_kritisch.push('Weniger als 3 Bullet Points')
    score += 2
  }

  // A+ CONTENT (15 Punkte)
  if (listing.hasAPlus) score += 15
  else {
    fehlend_empfohlen.push('A+ Content fehlt (Brand Registry erforderlich)')
  }

  // BACKEND KEYWORDS (10 Punkte)
  if (listing.backendKeywordsBytes >= 240) score += 10
  else if (listing.backendKeywordsBytes >= 100) {
    score += 6
    empfehlungen.push({
      element: 'Backend Keywords',
      aktuell: `${listing.backendKeywordsBytes} Byte`,
      empfohlen: 'Auf 240-250 Byte auffüllen mit Synonymen und Long-Tail',
      prioritaet: 'hoch',
      erwarteter_cvr_lift: '+10-20% indexierte Keywords'
    })
  } else {
    fehlend_kritisch.push('Backend Keywords fast leer')
    score += 1
  }

  // PREIS (10 Punkte)
  if (listing.pricePosition === 'below_median') score += 10
  else if (listing.pricePosition === 'at_median') score += 7
  else score += 3

  return {
    score: Math.min(100, score),
    empfehlungen: empfehlungen.sort((a, b) => {
      const prio = { hoch: 0, mittel: 1, niedrig: 2 }
      return prio[a.prioritaet] - prio[b.prioritaet]
    }),
    fehlend_kritisch,
    fehlend_empfohlen
  }
}
```


## 39.2 Kanal-Ranking-Tracker

```typescript
// services/aria/marketplace/ranking-tracker.ts

// Speichert tägliche Ranking-Snapshots für Trend-Analyse
export async function saveRankingSnapshot(
  tenantId: string,
  supabase: SupabaseClient
): Promise<void> {

  const { data: activeListings } = await supabase
    .from('marketplace_listings')
    .select('id, sku, kanal, main_keywords')
    .eq('tenant_id', tenantId)
    .eq('listing_status', 'active')

  for (const listing of activeListings ?? []) {
    for (const keyword of listing.main_keywords ?? []) {
      // Ranking für dieses Keyword abfragen (Kanal-spezifisch)
      const rank = await fetchKeywordRanking(listing.sku, keyword, listing.kanal)

      await supabase.from('keyword_rankings').upsert({
        tenant_id: tenantId,
        listing_id: listing.id,
        sku: listing.sku,
        kanal: listing.kanal,
        keyword,
        rank_today: rank,
        snapshot_date: new Date().toISOString().split('T')[0],
        is_main_keyword: true
      }, {
        onConflict: 'tenant_id,sku,kanal,keyword,snapshot_date'
      })
    }
  }
}

// Ranking-Trend analysieren
export async function analyzeRankingTrend(
  tenantId: string,
  sku: string,
  keyword: string,
  kanal: string,
  supabase: SupabaseClient
): Promise<{ trend: 'up' | 'down' | 'stable', change7d: number }> {

  const { data: history } = await supabase
    .from('keyword_rankings')
    .select('rank_today, snapshot_date')
    .eq('tenant_id', tenantId)
    .eq('sku', sku)
    .eq('keyword', keyword)
    .eq('kanal', kanal)
    .gte('snapshot_date', new Date(Date.now() - 7 * 86400000).toISOString())
    .order('snapshot_date', { ascending: true })

  if (!history || history.length < 2) {
    return { trend: 'stable', change7d: 0 }
  }

  const oldest = history[0].rank_today
  const newest = history[history.length - 1].rank_today
  const change7d = oldest - newest  // positiv = Verbesserung (niedrigerer Rang)

  const trend = change7d > 5 ? 'up' : change7d < -5 ? 'down' : 'stable'
  return { trend, change7d }
}
```


===============================================================================
# TEIL 40 — CHECKLISTE: NEUES PRODUKT AUF ALLEN KANÄLEN LISTEN
===============================================================================


## 40.1 Pre-Launch Checkliste

```
PRE-LAUNCH CHECKLISTE — NEUES PRODUKT:

  PRODUKTDATEN-BASIS:
  □ EAN/GTIN registriert (GS1 oder eigene Registrierung)
  □ Produktfotos: min. 8 professionelle Bilder
     □ Hauptbild 2000x2000px weißer BG
     □ Lifestyle-Bild
     □ Maß-Infografik
     □ Detail-Close-ups (2-3 Stück)
     □ Lieferumfang-Bild
  □ Produkttitel für jeden Kanal (unterschiedliche Formeln)
  □ Produktbeschreibung (Basis, kanalübergreifend anpassbar)
  □ Technische Spezifikationen vollständig
  □ Gewicht und Maße für Versand-Kalkulation

  COMPLIANCE-CHECK:
  □ CE-Zeichen vorhanden wenn pflichtig
  □ GPSR-konforme Produktsicherheitsdaten
  □ Verpackung LUCID-konform
  □ Altersempfehlung wenn Kinderspielzeug
  □ Gefahrgut-Check (ist nichts Gefährliches dabei?)

  PREIS-KALKULATION:
  □ Einkaufspreis bekannt
  □ Alle Plattform-Gebühren berechnet
  □ Versandkosten kalkuliert
  □ Ziel-Marge definiert
  □ Mindestpreis festgelegt
  □ Launch-Preis (leicht unter Markt-Median) definiert
  □ Langfristig-Zielpreis definiert
```


## 40.2 Launch-Ablauf je Kanal

```
LAUNCH-REIHENFOLGE EMPFEHLUNG:

  TAG 1: AMAZON LISTING LIVE
    □ Listing vollständig befüllen
    □ FBA-Bestand eingelagert (wenn FBA)
    □ PPC Auto-Kampagne starten
    □ Listing in Vine anmelden (wenn Brand Registry)

  TAG 2-3: EBAY LISTING LIVE
    □ Item Specifics vollständig
    □ GTC Festpreis-Listing
    □ PLS aktivieren (Trend Rate)
    □ Store-Kategorie zugeordnet

  WOCHE 1: OTTO LISTING
    □ Produktdaten via API hochladen
    □ Qualitäts-Score > 80 sicherstellen
    □ Kategorie-Pflichtattribute alle gefüllt
    □ 72h Prüfzeit einkalkulieren

  WOCHE 2: KAUFLAND LISTING
    □ EAN-Konflikt prüfen
    □ Daten über Portal/API hochladen
    □ Preis wettbewerbsfähig setzen

  NACH 2 WOCHEN: ERSTE ANALYSE
    □ Welcher Kanal performt am besten?
    □ Keyword-Rankings prüfen
    □ PPC-Daten Amazon auswerten
    □ Erster Optimierungs-Sprint planen
```


---

*ARIA-MARKTPLAETZE.md — Production Ready*
*Comentra Intelligence Layer*
*Stand: 2025/2026*
*40 Sektionen — Amazon A10 · eBay Cassini · Otto · Kaufland*
*Ranking-Faktoren · Gewichtungen · Optimierungshebel · Verbotenes*
*Vollständige Referenz für ARIA und EmsCraft24 Tagesgeschäft*
===============================================================================
# TEIL 35 — AMAZON A10: INDEXIERUNG & CRAWLING
===============================================================================


## 35.1 Indexierungs-Mechanik

```
AMAZON INDEXIERT FOLGENDE FELDER:
  Produkttitel:            vollständig indexiert (höchste Gewichtung)
  Backend Keywords:        vollständig indexiert (hohe Gewichtung)
  Bullet Points (alle 5):  vollständig indexiert (hohe Gewichtung)
  Produktbeschreibung:     indexiert wenn kein A+ vorhanden (mittlere Gewichtung)
  A+ Content Textfelder:   NICHT direkt indexiert (indirekt über CVR-Effekt)
  Q&A Antworten:           indexiert (niedrige Gewichtung)
  Kundenbewertungen:       indexiert (sehr niedrig, aber vorhanden)

NICHT INDEXIERT:
  Bilder (nur Alt-Text intern genutzt, kein direkter Ranking-Effekt)
  PDF-Anhänge
  External Links
```


## 35.2 Index-Prüfung

```
METHODE 1 — AMAZON SUCHE:
  Eingabe: '[DEINE ASIN] [KEYWORD]' in Amazon-Suchfeld
  Wenn Listing erscheint: indexiert für dieses Keyword
  Wenn nicht erscheint: NICHT indexiert
  Beispiel: 'B09XYZ123 Fichtenholz wetterfest'

METHODE 2 — BRAND ANALYTICS (Search Query Performance Report):
  Seller Central → Brand → Analytics → Search Query Performance
  Zeigt: für welche Queries das Produkt Impressionen bekommt
  Wenn Query keine Impressionen: kein Index für dieses Keyword

TYPISCHE INDEX-PROBLEME:
  Problem: Keyword im Titel, aber nicht indexiert
  Fix:     Listing neu speichern (Edit → Save). Amazon re-crawlt.

  Problem: Backend Keywords nicht indexiert
  Fix:     Zeichenlimit prüfen, HTML-Tags entfernen, neu speichern.

  Problem: Listing komplett aus Index verschwunden
  Fix:     Policy-Violation prüfen, Account Health, Support.
```


===============================================================================
# TEIL 36 — AMAZON: VARIANTEN-STRATEGIE
===============================================================================


## 36.1 Wann Varianten sinnvoll sind

| SZENARIO                        | EMPFEHLUNG        | BEGRÜNDUNG                        |
| ------------------------------- | ----------------- | --------------------------------- |
| Gleiche Basis, nur Farbe/Größe  | Varianten         | Reviews gebündelt, ein Listing    |
| Sehr unterschiedliche Keywords  | Separate Listings | Bessere Keyword-Abdeckung         |
| > 20 Varianten                  | Prüfen ob nötig   | Zu viele Varianten = schlechte UX |
| Unterschiedliche Kategorien     | Separate Listings | Kategorisierungs-Konflikt         |
| Neues Produkt neben etabliertem | Variante prüfen   | Von Reviews profitieren           |


## 36.2 Varianten-Ranking-Logik

```
VARIANTEN UND RANKING:
  Parent-ASIN:  eigenes BSR, eigenes Keyword-Ranking
  Child-ASINs:  eigene BSRs, Ranking teilweise auf Parent vererbt
  Beste Variante erscheint in Suchergebnissen (automatisch)
  Klicks auf eine Variante können andere Varianten mitbosten

BEST PRACTICES:
  1. Populärste Variante als Standard-Variante setzen
  2. Alle Varianten vollständig befüllen (Bilder, Bullets)
  3. Variantenspezifische Keywords in Child-Titeln integrieren
  4. Preis-Differenzierung sinnvoll (Basis vs. Premium)
  5. Gleiche Bilder-Qualität für alle Varianten
```


===============================================================================
# TEIL 37 — EBAY: STORE-OPTIMIERUNG
===============================================================================


## 37.1 Store-Stufen und Vorteile

| STUFE      | MONATLICH | KOSTENLOSE LISTINGS   | GEBÜHREN-RABATT |
| ---------- | --------- | --------------------- | --------------- |
| Kein Store | 0€        | 25 Festpreis / Monat  | 0%              |
| Basis      | 4,99€     | 250 Festpreis / Monat | 10%             |
| Top        | 29,99€    | 5.000 / Monat         | 15%             |
| Premium    | 99,99€    | Unbegrenzt            | 20%             |


## 37.2 Store SEO

```
EBAY STORE KEYWORD-OPTIMIERUNG:

  STORE-NAME:
  • Hauptkeyword der Nische + Marke/Eigenname
  • Beispiel: 'Holzspielzeug-Welt by MusterMarke'

  STORE-BESCHREIBUNG:
  • Kategorie-Keywords einbauen
  • USP benennen
  • 200–500 Wörter

  STORE-KATEGORIEN:
  • Eigene Kategorien für Produktgruppen
  • Keywords in Kategorie-Namen
  • Käufer-Navigation verbessern
```


===============================================================================
# TEIL 38 — AMAZON: LAUNCH DEEP DIVE
===============================================================================


## 38.1 Honeymoon-Phase maximieren

```
AMAZON HONEYMOON WINDOW (WOCHE 1–2):

  WARUM KRITISCH:
  Amazon gibt neuen ASINs temporären Sichtbarkeits-Boost.
  CVR und Velocity in Woche 1–2 entscheidet dauerhaftes Ranking.
  Hohe CVR Woche 1 = gutes Ranking für Monate.
  Niedrige CVR Woche 1 = schlechtes Ranking, schwer zu erholen.

  CHECKLISTE TAG 1:
  □ PPC Auto-Kampagne: hohes Tagesbudget, kein ACoS-Limit
  □ PPC Manual Exact: Top-3 Keywords aus Recherche
  □ Preis: 5–10% unter Markt-Median (höhere CVR)
  □ Vine: angemeldet (wenn Brand Registry, 3–4 Wochen Vorlauf!)
  □ Externen Traffic: E-Mail-Liste + Social

  CHECKLISTE WOCHE 1:
  □ Täglich: Bestand prüfen — kein Stockout in Woche 1
  □ Täglich: 'Request a Review' für alle Bestellungen
  □ Täglich: PPC-Budget ausgeschöpft? → erhöhen
  □ Täglich: CTR und CVR aus Brand Analytics

  CHECKLISTE WOCHE 2:
  □ Auto-Kampagne: Converting Keywords extrahieren
  □ Manual Exact für neue Keywords starten
  □ Erste Vine-Reviews eingegangen?
  □ Preis langsam Richtung Ziel-Preis anpassen
```


===============================================================================
# TEIL 39 — AMAZON: BEWERTUNGS-MANAGEMENT VOLLSTÄNDIG
===============================================================================


## 39.1 Request-a-Review Automation

```typescript
// Amazon erlaubt 1 Review-Anfrage pro Bestellung
// Über Seller Central API automatisierbar

async function requestReviewForOrder(orderId: string, token: string) {
  const response = await fetch(
    `https://sellingpartnerapi-eu.amazon.com/messaging/v1/orders/${orderId}/messages/requestReview`,
    {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${token}`,
        'x-amz-access-token': token,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({ marketplaceIds: ['A1PA6795UKMFR9'] })  // Amazon.de
    }
  )
  return response.ok
}

// WANN ANFRAGEN:
// Optimal: 7–10 Tage nach bestätigter Lieferung
// Nicht anfragen wenn: Retoure offen, Dispute offen
// Erlaubt: 1x pro Bestellung (automatischer Block durch Amazon wenn nochmal)
```


## 39.2 Vine-Programm vollständig

| ASPEKT         | DETAIL                                                           |
| -------------- | ---------------------------------------------------------------- |
| Voraussetzung  | Brand Registry + neue ASIN (empfohlen: 0–5 organische Reviews)   |
| Kosten         | 200€ pro ASIN (Stand 2024)                                       |
| Max. Reviewer  | Bis 30 Vine-Reviewer pro ASIN                                    |
| Produkt-Kosten | Produkt wird kostenlos an Reviewer geliefert                     |
| Zeitrahmen     | Ca. 3–4 Wochen bis erste Vine-Reviews eingehen                   |
| Kein Einfluss  | Nicht auf Inhalt oder Rating steuerbar (Amazon-Policy)           |
| Vine-Badge     | Reviews zeigen 'Vine Kundenrezension eines kostenlosen Produkts' |
| Wann sinnvoll  | Neue ASINs mit 0 Reviews — erste 15 Reviews kritisch             |
| Wann nicht     | ASINs mit > 30 organischen Reviews — kein zusätzlicher Effekt    |


===============================================================================
# TEIL 40 — KANALÜBERGREIFEND: OPERATIVES
===============================================================================


## 40.1 Täglicher Marktplatz-Workflow

```
TÄGLICHER STANDARD-WORKFLOW:

  07:00 — ARIA MORNING BRIEFING:
    Umsatz gestern alle Kanäle
    Buy Box Status alle aktiven ASINs (Amazon)
    Offene Bestellungen (alle Kanäle)
    Neue negative Bewertungen
    Stockout-Risiken (< 7 Tage Reichweite)

  09:00 — BESTAND & LOGISTIK:
    Neue Bestellungen verarbeiten
    FBA-Einlieferungen planen (wenn nötig)
    Kaufland/Otto Bestellungen abrufen

  11:00 — PPC-CHECK (Amazon):
    Budget noch verfügbar?
    ACoS im Zielbereich?
    Neue Converting Keywords?

  14:00 — PREISE & REPRICING:
    Repricing-Engine läuft? (ARIA Alert PA-007)
    Buy Box Status prüfen
    Manueller Preis-Check bei Abweichungen

  17:00 — KOMMUNIKATION:
    Buyer Messages beantworten (< 24h Pflicht)
    A-to-Z Claims prüfen und bearbeiten
    eBay Best Offers beantworten

  WÖCHENTLICH (Montag):
    PPC Optimierung (Keywords, Gebote, Budget)
    Keyword-Rankings prüfen
    Wettbewerber-Analyse
    Listing-Score-Check (< 70: sofort optimieren)
```


## 40.2 Peak-Season Vorbereitung

| AUFGABE                               | TIMING            | KANAL         | PRIORITÄT |
| ------------------------------------- | ----------------- | ------------- | --------- |
| FBA-Bestand einliefern (min. 60 Tage) | 6 Wochen vor Peak | Amazon        | KRITISCH  |
| PPC-Budget erhöhen (+50–100%)         | 2 Wochen vor Peak | Amazon        | HOCH      |
| Saisonale Keywords aktivieren         | 3 Wochen vor Peak | Amazon + eBay | HOCH      |
| Repricing auf Peak-Modus              | 1 Woche vor Peak  | Amazon + eBay | HOCH      |
| eBay PLS Ad-Rate erhöhen              | 2 Wochen vor Peak | eBay          | MITTEL    |
| Otto-Bestand auffüllen                | 4 Wochen vor Peak | Otto          | MITTEL    |
| Versand-Kapazität sichern             | 4 Wochen vor Peak | Intern        | KRITISCH  |
| ARIA Daily Cap erhöhen (Peak-Modus)   | 1 Woche vor Peak  | Comentra      | MITTEL    |


===============================================================================
# TEIL 41 — EMSC RAFT24-SPEZIFISCHE OPTIMIERUNG
===============================================================================


## 41.1 Produktportfolio Kanal-Strategie

```
SANDKÄSTEN (150cm, 170cm, 190cm):
  Amazon:   Haupt-Kanal. FBA bevorzugt.
            Titel: 'Brand Sandkasten Holz Kinder [Maß]cm Fichtenholz FSC'
            Peak: März–Juni (Frühling), Vine für neue Varianten

  eBay:     GTC-Listings. Item Specifics: Maße, Material, Alter, Zertifikat.
            PLS in Frühlingssaison aktivieren.

  Otto:     Vollständige Maßangaben (Retouren-Prävention kritisch).
            Montageaufwand ehrlich beschreiben.

AKUSTIKPANEELE:
  Amazon:   Konkurrenzreiche Kategorie. A+ Content Differenzierung.
            Keywords: Schallschutz, Akustikpaneele, Büro, HomeOffice, Studio.

  eBay:     Weniger Wettbewerb als Amazon. Professionelle Käufer.
            Technische Specs vollständig in Specifics.

TREPPENSCHUTZGITTER (CLAMARO):
  Amazon:   Sicherheitsprodukt — CE-Zertifikat prominent in Bullets.
            Keywords: Treppenschutzgitter, Kinderschutzgitter, Treppe sichern.

  Otto:     Vollständige Attribute (Breite-Range, Befestigungsart).

BILDERRAHMEN:
  Amazon:   Lifestyle-Bilder kritisch. Cross-Sell zwischen Varianten.
            Virtual Bundle: Rahmen + Passepartout.

  eBay:     Antik-Variante: Sammler-affine Zielgruppe.
            Standard-Varianten: GTC, Festpreis.
```


===============================================================================
# TEIL 42 — AMAZON: POST-STOCKOUT RANKING RECOVERY
===============================================================================


## 42.1 Recovery-Plan nach Stockout

| ZEITRAUM                 | MASSNAHMEN                                       | ZIEL                              |
| ------------------------ | ------------------------------------------------ | --------------------------------- |
| Tag 1 nach Wiederbestand | PPC × 5, Preis 10% unter Markt                   | Sofort Velocity aufbauen          |
| Woche 1–2                | PPC × 3, extern Traffic, Review-Anfragen täglich | Ranking-Signal senden             |
| Woche 3–4                | PPC × 2, Preis normalisieren                     | Organisches Ranking stabilisieren |
| Woche 5–8                | Normaler PPC, A/B-Tests reaktivieren             | Vollständige Erholung             |

```
ERWARTETE ERHOLUNGSZEITEN:
  Stockout 1–2 Tage:     2–4 Wochen Recovery
  Stockout 3–7 Tage:     4–8 Wochen Recovery
  Stockout 1–2 Wochen:   8–16 Wochen Recovery
  Stockout > 1 Monat:    Ranking teilweise dauerhaft verloren
                          Neustart-Strategie nötig
```


===============================================================================
# TEIL 43 — FINAL: SCHNELL-REFERENZ ALLE KANÄLE
===============================================================================


## 43.1 Zahlen die ARIA kennen muss

```
AMAZON — KRITISCHE ZAHLEN:
  Titellimit:         200 Byte (≈ 150 Zeichen praktisch)
  Backend Keywords:   250 Byte total
  Bullets:            5 × 500 Byte
  ODR-Grenze:         1.0% (Warnung ab 0.75%)
  LSR-Grenze:         4.0% (Warnung ab 3.0%)
  VTR-Minimum:        95%
  Vine:               30 Reviews max, 200€/ASIN
  FBA Buy Box Vorteil: bis +15% Preisunterschied
  Stockout 1 Woche:   8–16 Wochen Recovery
  Honeymoon-Phase:    2 Wochen nach Listing-Launch

EBAY — KRITISCHE ZAHLEN:
  Titellimit:         80 Zeichen
  Item Specifics:     100% ausfüllen (Pflicht + Empfohlen)
  TRS Defect Rate:    ≤ 0.5%
  TRS Late Shipment:  ≤ 3%
  TRS Feedback:       ≥ 98% positiv
  TRS Transaktionen:  ≥ 100 in 12 Monaten
  PLS Trend Rate:     Kategoriespezifisch (eBay zeigt Empfehlung)

OTTO — KRITISCHE ZAHLEN:
  Quality Score Ziel: > 85
  Quality Score Min:  60 (darunter kaum sichtbar)
  Retourenquote Warn: > 15%
  Retourenquote Krit: > 30% (Deaktivierung droht)
  API Update Latenz:  1–5 Min (Preis/Bestand)
  Neue Listings:      24–72h Prüfzeit

KAUFLAND — KRITISCHE ZAHLEN:
  EAN:                Absolut Pflicht (kein Upload ohne EAN)
  Stornoquote Grenze: 2%
  Lieferzuverl. Min:  93%
  Produktdaten Min:   50% Vollständigkeit
```


---

*ARIA-MARKTPLAETZE.md — Neu aufgebaut. Version 3.0*
*Comentra Intelligence Layer — Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*43 Sektionen — Vollständig — Production Ready*
===============================================================================
# TEIL 44 — AMAZON A10: SAISONALE DEEP DIVES
===============================================================================


## 44.1 Q4 Strategie vollständig

```
Q4 ZEITPLANUNG (September – Dezember):

  SEPTEMBER — VORBEREITUNG:
  □ FBA-Einlieferungen für Q4: Bestand für min. 90 Tage
  □ Check: Amazon FBA Einlieferungs-Frist für Q4 (variiert jährlich)
  □ Lightning Deals für November einreichen (Deadline ca. Anfang Oktober)
  □ PPC-Strategie für Q4 planen: Budget × 2-3
  □ Backend Keywords: Winter/Weihnachts-Keywords ergänzen

  OKTOBER — AUFBAU:
  □ PPC schrittweise erhöhen (+20% pro Woche)
  □ Saisonale Keywords in Titel prüfen (wenn relevant)
  □ A+ Content auf Weihnachts-Thema anpassen (optional)
  □ Bestand täglich prüfen — erste Peak-Traffic-Spikes

  NOVEMBER — PEAK:
  □ Woche vor Black Friday: PPC auf Maximum
  □ Lightning Deals aktiv
  □ Repricing: aggressiv aber nicht unter Mindestmarge
  □ Bestand: täglich, ggf. FBM als Backup
  □ Reaktionszeit Kundenanfragen < 12h

  DEZEMBER — WEIHNACHTEN:
  □ PPC bis 18. Dezember hoch halten
  □ Ab 19. Dezember: PPC senken (Liefergarantie nicht mehr möglich)
  □ Letzte FBA-Einlieferungen: Anfang Dezember
  □ FBM als Backup wenn FBA-Bestand erschöpft
```


## 44.2 Frühjahr-Saison Outdoor/Garten

```
FRÜHJAHRS-SAISON STRATEGIE (März – Juni):

  FÜR SANDKÄSTEN, OUTDOOR, GARTEN:

  FEBRUAR — VORBEREITUNG:
  □ Bestand aufbauen: 60–90 Tage Reichweite vor März
  □ FBA einliefern Ende Februar
  □ Frühlings-Keywords in Backend aktivieren
  □ PPC Frühjahrs-Kampagne starten (Anfang März)

  MÄRZ–APRIL — WACHSTUM:
  □ Stärkste organische Traffic-Phase für Outdoor
  □ PPC: Outdoor + Garten Keywords priorisieren
  □ Bestand wöchentlich prüfen (schnelle Velocity)

  MAI — PEAK:
  □ Muttertag: Gift-Keywords ergänzen
  □ PPC-Budget: Peak-Niveau
  □ Preise: leicht erhöhen wenn Wettbewerb OOS

  JUNI — NORMALISIERUNG:
  □ PPC schrittweise senken
  □ Restbestand: Summer-Keywords ergänzen
  □ Überbestand: Preissenkung erwägen
```


===============================================================================
# TEIL 45 — EBAY: KÄUFER-TYPEN UND VERKAUFSSTRATEGIE
===============================================================================


## 45.1 eBay.de Käufer-Profil

```
EBAY.DE KÄUFER-SEGMENTE (2025):

  SEGMENT 1 — PREISBEWUSSTE KÄUFER (ca. 40%):
    • Vergleichen intensiv vor dem Kauf
    • Nutzen Best Offer aktiv
    • Bevorzugen kostenloser Versand
    • Kaufen oft Gebrauchtware wenn günstiger
    STRATEGIE: Wettbewerbsfähiger Preis + Kostenloser Versand

  SEGMENT 2 — QUALITÄTS-SUCHENDE (ca. 30%):
    • Lesen Beschreibung vollständig
    • Prüfen Seller-Feedback sorgfältig
    • Bereit höheren Preis für TRS+ zu zahlen
    • Bevorzugen detaillierte Item Specifics
    STRATEGIE: TRS-Status halten, vollständige Specifics, gute Bilder

  SEGMENT 3 — SAMMLER UND NISCHEN (ca. 20%):
    • Suchen spezifische Produkte gezielt
    • Weniger preis-sensitiv bei Nischen-Produkten
    • Nutzen Best Offer und Auktionen
    STRATEGIE: Genaue Kategorisierung, detaillierte Beschreibung

  SEGMENT 4 — IMPULSKÄUFER (ca. 10%):
    • Buy-it-Now sofort
    • Hauptbild und Preis entscheidend
    • Wenig Recherche
    STRATEGIE: Starkes Hauptbild, klarer Preis, Promoted Listing
```


## 45.2 eBay Verkäufer-Performance-Optimierung

| METRIK                 | EINFLUSS AUF CASSINI | VERBESSERUNGS-HEBEL                         |
| ---------------------- | -------------------- | ------------------------------------------- |
| Handling-Time 1 Tag    | Hoch                 | Täglich versenden, Sa optional              |
| Tracking hochgeladen   | Hoch                 | Automatisch über Versand-Integration        |
| Response-Rate > 98%    | Mittel-Hoch          | Täglich Nachrichten prüfen, < 12h antworten |
| Feedback > 98% positiv | Sehr hoch            | Probleme direkt lösen, keine Disputes       |
| Defect Rate < 0.5%     | Sehr hoch            | Bei Problem: direkt mit Käufer lösen        |
| Kostenlosen Versand    | Hoch                 | Versandkosten in Preis einkalkulieren       |


===============================================================================
# TEIL 46 — OTTO: HÄNDLER-MANAGEMENT VOLLSTÄNDIG
===============================================================================


## 46.1 Otto Partner-Typen

| PARTNER-TYP       | BESCHREIBUNG                      | ANFORDERUNGEN                        | VORTEILE                          |
| ----------------- | --------------------------------- | ------------------------------------ | --------------------------------- |
| Standard Partner  | Normaler Marketplace-Händler      | Basisanforderungen                   | Grundlegende Platzierung          |
| Premium Partner   | Überdurchschnittliche Performance | Score > 80, niedrige Retouren        | Bessere Sichtbarkeit              |
| Preferred Partner | Top-Händler                       | Auf Einladung, sehr hohe Performance | Top-Platzierung, direkter Support |


## 46.2 Otto Qualitätsgespräch — Was droht wann

```
OTTO ESKALATIONS-STUFEN:

  STUFE 1 — AUTOMATISCHE BENACHRICHTIGUNG:
    Auslöser: Qualitätsscore < 70 oder Retouren > 20%
    Otto sendet automatische E-Mail mit Hinweis
    Reaktionszeit: 14 Tage für Verbesserung

  STUFE 2 — QUALITÄTSGESPRÄCH:
    Auslöser: Score < 60 oder Retouren > 30% über 30 Tage
    Otto kontaktiert direkt für Gespräch
    Verbesserungsplan muss eingereicht werden

  STUFE 3 — LISTING-DEAKTIVIERUNG:
    Auslöser: Retouren > 40% oder keine Verbesserung nach Gespräch
    Betroffenes Listing wird offline genommen
    Neuaktivierung nach nachgewiesener Verbesserung

  STUFE 4 — VERTRAGSBEENDIGUNG:
    Auslöser: Dauerhaft schlechte Performance oder Policy-Verstöße
    Otto kündigt Partner-Vertrag

  PRÄVENTIV-MAßNAHMEN:
  □ Wöchentlich: Product Quality Scores prüfen
  □ Monatlich: Retourenquoten prüfen
  □ Sofort handeln wenn Score < 75 (Puffer vor Warnung)
```


===============================================================================
# TEIL 47 — KAUFLAND: DEEP DIVE STRATEGIE
===============================================================================


## 47.1 Kaufland Kategorie-Stärken

| KATEGORIE        | KAUFLAND-STÄRKE | STRATEGIE                                    |
| ---------------- | --------------- | -------------------------------------------- |
| Haushalt & Küche | Stark           | Preis wettbewerbsfähig, vollständige Specs   |
| Garten & Outdoor | Wachsend        | Saisonale Keywords, Frühjahr-Push            |
| Spielzeug        | Mittel          | CE-Zertifikat prominent, Sicherheitshinweise |
| Elektro-Zubehör  | Mittel          | Technische Specs vollständig                 |
| Möbel            | Mittel          | Maßangaben präzise, Montagehinweise          |
| Mode             | Schwach         | Kaum Empfehlenswert für Modehändler          |


## 47.2 Kaufland Listing-Optimierung Details

```
KAUFLAND OPTIMIERUNGS-CHECKLIST:

  EAN UND DATEN:
  □ EAN korrekt und GS1-registriert
  □ EAN-Konflikt mit Kaufland-Katalog geprüft
  □ Alle Pflicht-Attribute der Kategorie ausgefüllt
  □ Alle empfohlenen Attribute ausgefüllt

  TITEL:
  □ 80–150 Zeichen
  □ Hauptkeyword vorne
  □ Wichtigste Maße oder Attribut
  □ Marke wenn bekannt und relevant

  BILDER:
  □ Mindestens 5 Bilder
  □ Hauptbild: weißer/heller Hintergrund
  □ Auflösung: min. 1200x1200px
  □ Verschiedene Winkel, Lifestyle, Maß

  PREIS:
  □ Am oder unter Markt-Median
  □ Kostenloser Versand wenn möglich
  □ Preis täglich durch Repricing geprüft

  PERFORMANCE:
  □ Stornoquote < 1% einhalten
  □ Lieferung täglich (keine Wochenend-Pause wenn möglich)
  □ Tracking täglich hochladen
```


===============================================================================
# TEIL 48 — ARIA MARKTPLATZ: SQL DASHBOARD-QUERIES
===============================================================================


## 48.1 Listing-Health Queries

```sql
-- Listings unter Qualitätsschwelle (alle Kanäle)
SELECT
  p.sku,
  p.product_name,
  ml.kanal,
  ml.listing_quality_score,
  ml.image_count,
  ml.has_a_plus_content,
  ml.backend_keywords_bytes,
  ml.bullet_count,
  ml.review_count,
  ml.avg_rating
FROM marketplace_listings ml
JOIN products p ON p.id = ml.product_id
WHERE ml.tenant_id = $1
  AND ml.listing_status = 'active'
  AND ml.listing_quality_score < 70
ORDER BY ml.listing_quality_score ASC;

-- Buy Box Status Amazon
SELECT
  p.sku, ml.current_price,
  ml.buybox_status, ml.competitor_price, ml.competitor_name,
  ml.last_buybox_check
FROM marketplace_listings ml
JOIN products p ON p.id = ml.product_id
WHERE ml.tenant_id = $1
  AND ml.kanal = 'amazon'
  AND ml.buybox_status = 'lost'
ORDER BY ml.last_buybox_check DESC;

-- Keyword-Ranking-Trend
SELECT
  kr.keyword, kr.kanal,
  kr.rank_today,
  kr.rank_7d_ago,
  kr.rank_today - kr.rank_7d_ago AS change_7d
FROM keyword_rankings kr
WHERE kr.tenant_id = $1
  AND kr.is_main_keyword = true
  AND ABS(kr.rank_today - (kr.rank_7d_ago :: int)) > 10
ORDER BY ABS(kr.rank_today - kr.rank_7d_ago) DESC;

-- Wettbewerber OOS Opportunities
SELECT
  p.sku, ml.kanal,
  ci.main_competitor_name,
  EXTRACT(DAYS FROM (NOW() - ci.main_competitor_oos_since)) AS oos_days,
  p.stock_quantity AS our_stock,
  ml.current_price
FROM competitor_intelligence ci
JOIN marketplace_listings ml ON ml.id = ci.listing_id
JOIN products p ON p.id = ml.product_id
WHERE ci.tenant_id = $1
  AND ci.main_competitor_stock_status = 'out_of_stock'
  AND p.stock_quantity > 7
ORDER BY oos_days DESC;
```


## 48.2 Performance-Vergleich SQL

```sql
-- Kanal-Performance Monatsvergleich
SELECT
  o.kanal,
  COUNT(DISTINCT o.id) AS bestellungen,
  SUM(oi.quantity) AS einheiten,
  ROUND(SUM(oi.revenue)::numeric, 2) AS umsatz,
  ROUND(SUM(oi.revenue - oi.platform_fees - oi.cogs)::numeric, 2) AS deckungsbeitrag,
  ROUND(100.0 * SUM(oi.revenue - oi.platform_fees - oi.cogs)
    / NULLIF(SUM(oi.revenue), 0), 1) AS marge_pct
FROM orders o
JOIN order_items oi ON oi.order_id = o.id
WHERE o.tenant_id = $1
  AND DATE_TRUNC('month', o.ordered_at) = DATE_TRUNC('month', CURRENT_DATE)
GROUP BY o.kanal
ORDER BY umsatz DESC;

-- Retouren-Rate pro Kanal und SKU
SELECT
  p.sku, p.product_name, o.kanal,
  COUNT(DISTINCT o.id) AS bestellungen,
  COUNT(DISTINCT ret.id) AS retouren,
  ROUND(100.0 * COUNT(DISTINCT ret.id) / NULLIF(COUNT(DISTINCT o.id), 0), 1) AS retouren_pct
FROM orders o
JOIN order_items oi ON oi.order_id = o.id
JOIN products p ON p.id = oi.product_id
LEFT JOIN returns ret ON ret.order_id = o.id AND ret.sku = p.sku
WHERE o.tenant_id = $1
  AND o.ordered_at >= NOW() - INTERVAL '30 days'
GROUP BY p.sku, p.product_name, o.kanal
HAVING COUNT(DISTINCT o.id) >= 5
ORDER BY retouren_pct DESC;
```


---

*ARIA-MARKTPLAETZE.md — Production Ready. Version 3.1*
*Comentra Intelligence Layer — Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*48 Sektionen abgeschlossen — Vollständige Referenz für ARIA und EmsCraft24*
*Alle Gewichtungsangaben: empirische Schätzwerte — keine offizielle Amazon/eBay-Quelle.*
===============================================================================
# TEIL 49 — AMAZON: LISTING-FEHLER UND FIXES
===============================================================================


## 49.1 Häufige Fehler und Sofort-Fixes

| FEHLER                             | SYMPTOM                                | URSACHE                                           | FIX                                                   |
| ---------------------------------- | -------------------------------------- | ------------------------------------------------- | ----------------------------------------------------- |
| Keyword nicht indexiert            | Kein Ranking obwohl Keyword im Titel   | Amazon hat nicht gecrawlt                         | Listing neu speichern (Edit → Save)                   |
| Buy Box weg ohne Preisänderung     | Umsatz-Einbruch ohne erkennbaren Grund | ODR/Performance-Problem                           | Seller Central: Account Health sofort prüfen          |
| CVR unter Kategorie-Benchmark      | Traffic da, aber Käufe ausbleiben      | Hauptbild, Preis, Bullets                         | A/B-Test Hauptbild starten, Preis prüfen              |
| BSR fällt obwohl Velocity gleich   | Ranking-Verlust ohne Velocity-Änderung | Wettbewerber hat Velocity erhöht                  | Wettbewerber analysieren, PPC erhöhen                 |
| FBA Stranded Inventory             | Bestand im Lager ohne Listing          | Listing deaktiviert oder ASIN-Fehler              | Fix listing oder Removal-Order                        |
| Vine-Reviews kommen nicht          | Vine angemeldet, 4 Wochen kein Review  | Reviewer haben abgelehnt oder Produkt passt nicht | Anderen Vine-Slot buchen                              |
| A+ Content nicht genehmigt         | Submission pending > 7 Tage            | Policy-Verstoß im Inhalt                          | Content überarbeiten, keine Vergleiche mit Wettbewerb |
| Listing unter falschem Browse Node | Kaum organischer Traffic               | Falsche Kategorie beim Upload                     | Kategorie-Korrektur über Case bei Amazon              |


## 49.2 Account Health Notfall-Protokoll

```
WENN ODR > 1% — NOTFALL-PROTOKOLL:

  SCHRITT 1 — SOFORT (innerhalb 2 Stunden):
    □ Seller Central öffnen: Account Health → Order Defect Rate
    □ Welche Bestellungen haben zum ODR beigetragen?
    □ Alle offenen A-to-Z Claims identifizieren
    □ Bei jedem offenen Claim: sofortige Kontaktaufnahme mit Käufer

  SCHRITT 2 — HEUTE:
    □ Alle A-to-Z Claims bearbeiten (Amazon antwortet in 3–5 Tagen)
    □ Käufer-Nachrichten bei negativen Bewertungen: Response-Entwurf
    □ POA vorbereiten (Struktur: Ursache → Sofortmaßnahmen → Prävention)

  SCHRITT 3 — INNERHALB 72h:
    □ Plan of Action einreichen wenn Amazon Aufforderung kommt
    □ Tägliches Monitoring: ODR-Wert jeden Morgen
    □ Neue Bestellungen: noch höhere Qualität sicherstellen

  WICHTIG:
    ODR-Messfenster ist 60 Tage — Verbesserungen wirken LANGSAM.
    Auch wenn sofort gehandelt wird: ODR sinkt erst nach Wochen.
    Deswegen: Präventiv handeln bevor ODR die Grenze erreicht.
```


---

*ARIA-MARKTPLAETZE.md — Abgeschlossen. Version 3.2 FINAL*
*Comentra Intelligence Layer — Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland*
*49 Sektionen — Production Ready*

================================================================================
# TEIL 49 — AMAZON: BRAND ANALYTICS REPORT-ÜBERSICHT
================================================================================

## 49.1 Verfügbare Reports (Brand Registry)

| REPORT | INHALT | NUTZUNG |
| --- | --- | --- |
| Search Query Performance | Impressionen, Klicks, CVR pro Keyword | Keyword-Gaps, CTR-Probleme |
| Market Basket Analysis | Was wird zusammen mit unserem Produkt gekauft | Bundle-Ideen, Cross-Sell |
| Repeat Purchase Behavior | Wiederkäufer-Rate pro ASIN | Loyalitätsmessung |
| Demographics | Alters-/Geschlechtsverteilung der Käufer | Zielgruppen-Optimierung |
| Item Comparison | Mit welchen Produkten wird verglichen | Wettbewerber-Insight |
| Alternate Purchase | Was kaufen Besucher statt unserem Produkt | Direkte Wettbewerber |
| Search Catalog Performance | Gesamte Suchperformance des Katalogs | Portfolio-Optimierung |

## 49.2 Search Query Performance Interpretation

```
HÄUFIGE SZENARIEN UND MASSNAHMEN:

SZENARIO A — Hohes Volumen, 0 Impressionen:
  Diagnose:  Keyword nicht indexiert
  Massnahme: Keyword in Titel oder Backend ergänzen

SZENARIO B — Hohe Impressionen, CTR < 0.5%:
  Diagnose:  Hauptbild oder Preis schreckt ab
  Massnahme: A/B-Test Hauptbild, Preis prüfen

SZENARIO C — Gute CTR, CVR < 3%:
  Diagnose:  Listing enttäuscht nach Klick
  Massnahme: Bullets, A+, Bilder überarbeiten

SZENARIO D — CVR gut, Impression Share < 10%:
  Diagnose:  PPC-Potential nicht ausgeschöpft
  Massnahme: PPC-Gebot für dieses Keyword erhöhen
```

================================================================================
# TEIL 50 — ABSCHLUSS: ARIA MARKTPLATZ-WISSENSBASIS KOMPLETT
================================================================================

## 50.1 Dokument-Übersicht

```
DOKUMENT:     ARIA-MARKTPLAETZE.md
VERSION:      3.1
STAND:        2025/2026
KANÄLE:       Amazon A10 · eBay Cassini · Otto · Kaufland
SEKTIONEN:    50 Teile

INHALTS-ZUSAMMENFASSUNG:
  Amazon A10:     Teil 1–22  (vollständige Algorithmus-Dokumentation)
  eBay Cassini:   Teil 23–30 (vollständige Algorithmus-Dokumentation)
  Otto:           Teil 31–35 (Ranking, Listing, API, Compliance)
  Kaufland:       Teil 36–38 (Ranking, EAN, Fulfillment)
  Übergreifend:   Teil 39–50 (Vergleich, Strategie, SQL, Glossar)

NUTZUNG DURCH ARIA:
  Dieses Dokument ist die Wissensbasis für alle marktplatzbezogenen
  Empfehlungen, Alerts und Optimierungs-Vorschläge von ARIA.
  Gewichtungsangaben sind empirische Schätzwerte —
  Amazon/eBay/Otto/Kaufland veröffentlichen keine offiziellen Werte.
```

## 50.2 Wichtigste Regeln auf einen Blick

```
AMAZON:
  1. CVR ist Ranking-Faktor #1 — Listing-Qualität vor PPC
  2. Stockout bestraft dauerhaft — Bestand ist heilig
  3. Externer Traffic (Google → Amazon) hat hohen Ranking-Wert
  4. Backend Keywords vollständig füllen — 250 Byte nutzen
  5. ODR > 1% = Account-Sperre droht — täglich prüfen

EBAY:
  1. Item Specifics vollständig = höchster Einzelhebel auf Cassini
  2. TRS/TRS+ halten — Ranking-Multiplikator
  3. Kostenloser Versand — direkt Ranking-positiv
  4. Titel 80 Zeichen vollständig nutzen
  5. GTC-Listings statt Auktionen für Standardware

OTTO:
  1. Product Quality Score > 85 anstreben
  2. Retourenquote < 15% — kritischer Ranking-Faktor
  3. Alle Pflicht-Attribute der Kategorie ausfüllen
  4. Maßangaben extrem präzise (Retouren-Prävention)
  5. API-Updates: Preise/Bestand in 1–5 Minuten live

KAUFLAND:
  1. EAN ist absolute Pflicht — ohne EAN kein Listing
  2. Preis sehr wettbewerbsfähig — preissensitivster Marktplatz
  3. Datenqualität vollständig — Kaufland bewertet explizit
  4. Stornoquote < 1% halten
  5. Kostenloser Versand erhöht Ranking
```

---

*ARIA-MARKTPLAETZE.md — Abgeschlossen. Version 3.1*
*Comentra Intelligence Layer — Stand: 2025/2026*
*Amazon A10 · eBay Cassini · Otto · Kaufland · 50 Sektionen*
