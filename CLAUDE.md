## Geheugen
Update deze CLAUDE.md automatisch wanneer:
- Er belangrijke architectuurkeuzes gemaakt worden
- Nieuwe patterns of conventies worden afgesproken
- Er context is die handig is voor volgende sessies

## Project overzicht
Action App prototypes — mobiele UI prototypes als single-file HTML. Overzichtspagina: `index.html` (root).

### Varianten
- `variant-1/` t/m `variant-4/` — Ecom integratie varianten (standalone, eigen CSS)
- `variant-5/` — Accessibility toggle via hamburgermenu (standalone, eigen CSS)
- `systemized/` — Gedeeld design system met live componenten (gebruikt `styles.css`)

## Architectuur

### Systemized variant (gekoppeld design system)
- `systemized/styles.css` — **Gedeeld CSS bestand** met alle design tokens en component-stijlen
- `systemized/index.html` — Prototype, importeert `styles.css`
- `systemized/design-system.html` — Design system overzicht, importeert zelfde `styles.css`
- **Koppeling**: wijzigingen in `styles.css` werken door in zowel prototype als design system

### Variant-5 (standalone)
- `variant-5/index.html` — Alles inline (CSS + JS), niet gekoppeld aan systemized
- Eigen z-index layering: header (210), menu overlay (220), menu (221), a11y-page (230)
- High-contrast mode via `.phone-frame.high-contrast` class

## Design Tokens (`systemized/styles.css` :root)
```
--brand-darkblue: #001489
--brand-orange: #ff8200
--brand-cyan: #00b6e7
--a11y-cyan: #007a99
--a11y-orange: #b34d00
--neutral-50 / 150 / 300 / 500 / 700
--white: #ffffff
--radius-xs: 4px / --radius-sm: 8px / --radius-round: 360px
```

## Componenten & conventies

### Logo
- **Bestand**: `images/action-logo.svg` (vector, 127x24 viewBox, wit + blauw)
- Logo is wit — gebruik op donkere achtergrond
- "webshop" wordt als tekst-element toegevoegd: `<span>` met Ubuntu Bold Italic, #66D3F1
- Gebruikt in: menu topbar, header, footer (footer zonder "webshop")

### Chevron
- **Eén unified class**: `.chevron` (20x20, neutral-300, flex-shrink:0)
- Vervangt oude `category-list-item-arrow`, `myaction-menu-arrow`, `category-item-caret`
- SVG: `<svg class="chevron" viewBox="0 0 20 20" fill="none"><path d="M7.5 15l5-5-5-5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>`

### Badges (clip-path stijl)
- `clip-path: polygon(0 0, 100% 0, calc(100% - 8px) 100%, 0 100%)`
- `padding: 3px 10px 3px 6px`
- Varianten: `.badge-orange` (#ff8200), `.badge-darkblue` (#001489), default cyan (#00b6e7)

### Buttons
- Alle buttons: **44px hoogte**, **16px font-size**, **font-weight 500**, `font-family: inherit`
- `.basket-empty-btn` — cyan, pill, filled
- `.new-lijstje-btn` — dashed border, transparent
- `.myaction-logout` — outlined, brand-darkblue border

### Typografie (gekoppeld via CSS classes)
- `.hero-title` — 32px/36, 700
- `.category-list-title` — 24px, 700, brand-darkblue
- `.product-lane-title` — 20px, 700, brand-orange
- `.myaction-section-title` — 18px, 700, brand-darkblue
- `.menu-item-title` — 16px, 500, brand-darkblue
- `.hero-subtitle` — 16px, 400
- `.top-tab.active` — 15px, 700, brand-darkblue
- `.menu-item-subtitle` — 14px, 400, neutral-700
- `.webshop-card-name` — 14px, 700, brand-darkblue
- `.product-card-name` — 12px, 500, brand-darkblue
- `.category-bubble-label` — 12px, 500, brand-darkblue
- `.tabbar-tab-label` — 11px, 400, neutral-700
- `.product-card-price` / `.webshop-card-price` — 18px, 700, brand-darkblue

### Hero Banner
- `aspect-ratio: 343 / 323` (bijna vierkant, iets breder dan hoog)
- `width: calc(100% - 32px)`, `margin: 0 16px`, `border-radius: var(--radius-sm)`
- Afbeelding: `margin-top: -30px`

## Variant-5 specifiek

### Accessibility (high-contrast) mode
- Toggle via `.phone-frame.high-contrast` class
- Cyan → `#007a99` (webshop-card-badge, webshop-card-cta, a11y-toggle, webshop-promo-bar, basket-badge)
- Oranje → `#b34d00` (badge-orange, product-card-badge, basket-badge)
- Darkblue badges blijven `var(--brand-darkblue)`
- Prijzen (brand-darkblue) blijven ongewijzigd in high-contrast

### Menu (slide-out)
- Eigen USP bar + topbar met Action logo + close button
- Z-index 221, bedekt header volledig
- A11y page opent vanuit menu (slide right) of footer (slide left)
- A11y page z-index 230, witte achtergrond

### Webshop cards (variant-5)
- 6 kaarten: cards 1,3 = Weekactie (orange) + Nieuw (cyan)
- Cards 2,4 = Met kussens (darkblue) + Nieuw (cyan)
- Cards 5,6 = alleen Nieuw (cyan)

## Git
- Remote: github.com/dspbrg/Mobile-proto.git
- Main branch: `main`
- Altijd committen met `Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>`

## Uncommitted wijzigingen
Er staan nog uncommitted wijzigingen in:
- `systemized/styles.css` — card-name merge, bubble-label updates, hero banner, buttons
- `systemized/index.html` — chevron unified, badge tekst Weekactie
- `systemized/design-system.html` — typografie gekoppeld, logo sectie, chevron unified
