# Context
Werkende HTML prototypes gebouwd voor Action (Europese discountretailer),
onderdeel van mijn UX portfolio als freelance designer.

Structuur:
- index.html (navigatiepagina, één niveau boven de varianten)
- variant-1/index.html t/m variant-7/index.html
- variant-7 heet "Systemized" en heeft een gekoppelde design system file

# Opdrachten

## 1. Vertaal index.html naar Engels

Alleen zichtbare tekst, geen CSS/JS/structuur aanraken.

Vertalingen:
- "Kies een variant om te bekijken" → "Choose a variant to explore"
- "ECOM INTEGRATIE" → "ECOM INTEGRATION"
- "Twee verschillende tabs, een mijn action omgeving" → 
  "Dual-tab navigation with a dedicated My Action space"
- "Splash screens bij modus-wissel, enkele toggle-knop met wissel-icoon" → 
  "Mode switching via a single button with animated splash transition"
- "Webview bottom sheet voor online assortiment" → 
  "Online assortment surfaced in a bottom sheet webview"
- "Op alle schermen kunnen switchen - contextueel" → 
  "Context-aware mode switching available on every screen"
- "Donkerblauw kleurschema voor online assortiment" → 
  "Dark blue visual theme for the online assortment experience"
- "ACCESSIBILITY SWITCH" → "ACCESSIBILITY SWITCH"
- "Via hamburgermenu" → "Mode toggle accessible via hamburger menu"
- "IMPROVEMENTS" → "IMPROVEMENTS"
- "Gedeeld design system met live componenten" → 
  "Unified design system with shared live components"

## 2. Herstel consistente schermafmetingen in alle varianten

Alle varianten moeten exact dezelfde phone frame afmetingen krijgen:
- Breedte: 375px (fixed, niet fluid)
- Hoogte: 844px (iPhone 14, fixed)
- Dit geldt ongeacht de browserhoogte of -breedte

Werkwijze:
- Analyseer eerst alle variant index.html bestanden op afwijkende 
  breedte- of hoogte-instellingen en noteer die in audit.md
- Pas dan elke variant aan zodat de afmetingen overeenkomen
- Gebruik geen vh, dvh of andere viewport-eenheden voor het phone frame
- De achtergrondkleur buiten het frame mag blijven zoals die is

## 3. Koppel de design system file van Systemized aan alle varianten

- Zoek in variant-7 welk bestand de design system styles bevat
- Noteer de bestandsnaam en het pad in audit.md
- Voeg een import toe aan het begin van het <head> blok van 
  variant-1 t/m variant-6, met een relatief pad naar de 
  design system file in variant-7
- Controleer per variant of er lokale stijlen zijn die conflicteren 
  met de design system definities (zelfde selector, andere waarde)
- Noteer alle conflicten in audit.md met aanbeveling: 
  overschrijven of bewaren
- Los de conflicten op conform de aanbeveling, tenzij het 
  een bewuste variantspecifieke stijl is

## 4. Voeg gesimuleerd iOS toetsenbord toe aan alle varianten

Voeg aan elke variant een gesimuleerd iOS toetsenbord toe dat:
- Verschijnt wanneer een gebruiker op een search input klikt of tapt
- Van onderen omhoog animeert (slide-up, 0.3s ease-out)
- De juiste iOS QWERTY lay-out toont (NL/EN, geen speciale tekens nodig)
- Het scherm omhoog duwt: de content scrollt zodat het actieve 
  veld zichtbaar blijft boven het toetsenbord
- Verdwijnt bij klik buiten het input veld of op een dismiss knop
- Puur HTML/CSS/JS is, geen externe dependencies
- De vaste hoogte van 844px respecteert: toetsenbord en content 
  blijven binnen het frame

Referentie iOS toetsenbord hoogte: 291px (staand, iPhone 14)

# Wat NIET aanraken
- Functionaliteit, flows, animaties van de prototypes
- Bestandsnamen en mappenstructuur
- CSS en JS die niet gerelateerd is aan bovenstaande opdrachten

# Criteria voor succes
- index.html bevat alleen Engelse tekst
- Alle varianten tonen een 375x844px frame, ongeacht browserhoogte
- De design system file is geïmporteerd in variant-1 t/m variant-6
- Alle conflicterende stijlen zijn gedocumenteerd in audit.md
- Toetsenbord animeert correct omhoog bij focus op search input
- git diff toont alleen wijzigingen gerelateerd aan bovenstaande opdrachten
- audit.md bevat een samenvatting van alle wijzigingen per variant
```

