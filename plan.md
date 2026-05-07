# Coffee House — Landing Page Build Plan
**For:** AI Agent Implementation
**Stack:** HTML5 + CSS3 only (no JavaScript, no frameworks)
**Fonts:** Google Fonts (external CDN link in `<head>`)

---

## 1. Project File Structure

```
coffee-house/
├── index.html
├── style.css
└── assets/
    └── images/
        ├── hero.jpg          # Coffee shop interior, wide atmospheric shot
        ├── espresso.jpg      # Espresso cup on saucer with beans
        ├── cappuccino.jpg    # Cappuccino with latte art
        ├── latte.jpg         # Tall latte glass with foam
        ├── mocha.jpg         # Mocha with whipped cream
        └── footer.jpg        # Steaming coffee cup on wooden table with beans
```

---

## 2. Google Fonts

Include both fonts in a single `<link>` tag inside `<head>`:

- **Dancing Script** — weight 700 → used for the navbar logo only
- **Playfair Display** — weights 400, 700 → used for all headings and section titles
- **Lato** — weights 400, 600 → used for body text, nav links, buttons, prices

```html
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@400;700&family=Lato:wght@400;600&display=swap" rel="stylesheet">
```

---

## 3. Design System

### 3.1 Color Tokens (CSS Variables)

```css
--color-primary-bg: #F4E8D9;
--color-contact-bg: #EDD9C0;
--color-surface-dark: #4A2D22;
--color-surface-darkest: #2F1B14;
--color-text-light: #FFF8F0;
--color-text-dark: #3A241C;
--color-border-light: #D9C4B1;
--color-accent-brown: #8A5A3B;
--color-card-footer-bg: #4A2D22;
--color-overlay: rgba(30, 15, 8, 0.45);
```

### 3.2 Typography Tokens

```css
--font-logo: 'Dancing Script', cursive;
--font-heading: 'Playfair Display', Georgia, serif;
--font-body: 'Lato', Arial, sans-serif;

--size-logo: 2rem;
--size-hero-heading: clamp(1.8rem, 4vw, 2.8rem);
--size-section-title: clamp(1.6rem, 3vw, 2.2rem);
--size-card-title: 1.2rem;
--size-card-price: 1.5rem;
--size-nav-link: 1rem;
--size-body: 1rem;
--size-button: 0.95rem;
```

### 3.3 Spacing & Layout Tokens

```css
--container-max: 1240px;
--section-padding-desktop: 64px 24px;
--section-padding-mobile: 40px 16px;
--card-gap: 24px;
--nav-height: 72px;
--hero-height-desktop: 560px;
--radius-card: 0px;
--radius-button: 4px;
```

### 3.4 Shadows

```css
--shadow-card: 0 2px 10px rgba(42, 20, 10, 0.12);
```

---

## 4. CSS Architecture

All styles live in a single `style.css` file, organized in this exact order:

1. CSS Reset + box-sizing
2. CSS Variables (`:root`)
3. Global base styles (body, a, img)
4. Utility classes (`.container`, `.section-title`, `.decorative-line`)
5. Component styles, one section at a time following the phase order below

---

## 5. HTML Semantic Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- meta, title, Google Fonts link, stylesheet link -->
</head>
<body>
  <header>
    <nav> <!-- logo left, links right --> </nav>
  </header>
  <main>
    <section id="hero"> ... </section>
    <section id="menu"> ... </section>
    <section id="about"> ... </section>
    <section id="contact"> ... </section>
  </main>
  <footer>
    <div class="footer-image"> ... </div>
    <div class="footer-copyright"> ... </div>
  </footer>
</body>
</html>
```

---

## 6. Build Phases

### Phase 1 — Project Setup
- Create `index.html` with full document shell.
- Add `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.
- Link Google Fonts and `style.css` in `<head>`.
- Scaffold all semantic sections as empty containers with correct IDs.
- Create `style.css` with the CSS reset, `:root` variables, and body base styles only.

### Phase 2 — Utility Classes
- Build `.container` with `max-width: var(--container-max)` and `margin: 0 auto`.
- Build `.section-title` using `font-family: var(--font-heading)`, bold, dark brown, centered.
- Build `.decorative-line` as the horizontal rule flanking section titles — thin `1px` lines in `var(--color-accent-brown)`, achieved with CSS `::before` and `::after` pseudo-elements on a flex container, or a dedicated wrapper div with three flex children (line, text, line).

### Phase 3 — Navbar
- Dark brown background (`var(--color-surface-darkest)`), height `var(--nav-height)`.
- Flex layout: logo flush left, nav links flush right, both vertically centered.
- Logo: `font-family: var(--font-logo)`, `font-size: var(--size-logo)`, color `var(--color-text-light)`.
- Nav links: `font-family: var(--font-body)`, medium weight, color `var(--color-text-light)`, spaced with `gap: 32px`.
- Active state on "Home": `border-bottom: 2px solid var(--color-text-light)`, `padding-bottom: 2px`.
- No hover effects requiring JavaScript. CSS `:hover` may add a subtle underline.

### Phase 4 — Hero Section
- Height: `var(--hero-height-desktop)` on desktop.
- `background-image: url('assets/images/hero.jpg')`, `background-size: cover`, `background-position: center`.
- Dark overlay using a pseudo-element or a child `div` with `background: var(--color-overlay)`, positioned absolutely filling the parent.
- Content centered both axes via flexbox (`display: flex; flex-direction: column; align-items: center; justify-content: center`).
- Heading: `font-family: var(--font-heading)`, `font-size: var(--size-hero-heading)`, color `var(--color-text-light)`, bold, centered, `text-shadow` for legibility.
- CTA Button ("View Menu"): outlined style — transparent background, `2px solid var(--color-text-light)`, white text, padding `12px 36px`, `border-radius: var(--radius-button)`. On `:hover`: background becomes `var(--color-surface-dark)`, smooth `transition: background 0.2s ease`.

### Phase 5 — Menu Section
- Background: `var(--color-primary-bg)`.
- Section title with decorative flanking lines.
- Card grid: `display: grid; grid-template-columns: repeat(4, 1fr); gap: var(--card-gap)` on desktop.
- Each `<article class="menu-card">` contains:
  - `<div class="card-image">` → `<img src="assets/images/[item].jpg" alt="[Item Name]">` — fixed height `200px`, `object-fit: cover`, full width.
  - `<div class="card-body">` → dark brown background (`var(--color-card-footer-bg)`), color `var(--color-text-light)`, padding `16px`.
    - `<h3 class="card-title">` — item name, `font-family: var(--font-heading)`, bold.
    - Thin `1px` horizontal rule in a muted brown tone, separating title from price.
    - `<p class="card-price">` — `font-size: var(--size-card-price)`, bold.
    - `<button class="btn-order">Order</button>` — `background: var(--color-accent-brown)`, white text, full width, `border: 2px solid var(--color-accent-brown)`, `border-radius: var(--radius-button)`, padding `10px 0`. On `:hover`: background lightens slightly or border brightens via `filter: brightness(1.1)`.
- All four cards must be equal height: use `display: flex; flex-direction: column` on the card, and `margin-top: auto` on the order button to push it to the bottom.

### Phase 6 — About Section
- Background: `var(--color-primary-bg)`.
- Section title with decorative lines, centered.
- Single `<p>` centered, `max-width: 640px`, `margin: 0 auto`, `color: var(--color-text-dark)`, `font-family: var(--font-body)`.

### Phase 7 — Contact Section
- Background: `var(--color-contact-bg)` — slightly darker cream than the main background, matching the reference.
- Section title with decorative lines, centered.
- Three contact items in a horizontal flex row (`justify-content: center; gap: 64px`).
- Each item is a flex column or flex row pairing an SVG icon with its text.
- Icons: inline SVG or Unicode characters styled in `var(--color-surface-dark)`, size `28px–32px`.
  - Envelope icon → Email label + `info@coffeehouse.com` on a second line.
  - Phone icon → `Phone: +123 456 7890` inline.
  - Location pin icon → `Location: 123 Coffee St., City` inline.
- Text: `font-family: var(--font-body)`, `color: var(--color-text-dark)`.

### Phase 8 — Footer
- **Footer image strip**: `<div class="footer-image">` with `background-image: url('assets/images/footer.jpg')`, `background-size: cover`, `background-position: center top`, height `280px` on desktop.
- **Copyright bar**: `background: var(--color-surface-darkest)`, color `var(--color-text-light)`, `font-family: var(--font-body)`, `font-size: 0.9rem`, `text-align: center`, padding `18px 24px`.
- Text: `© 2026 Coffee Shop — All Rights Reserved`.

### Phase 9 — Responsive Breakpoints

Apply all responsive rules in `style.css` after the base styles, using mobile-first `min-width` media queries.

**Below 768px (mobile default, no media query needed):**
- Menu cards: `grid-template-columns: 1fr` (single column).
- Hero height: `300px`.
- Nav: logo and links stacked, or links hidden and replaced with a simple centered row — since no JS, use a flex-wrap approach with reduced font size.
- Contact items: `flex-direction: column; align-items: center; gap: 32px`.

**@media (min-width: 480px):**
- No major changes; minor padding and font-size adjustments.

**@media (min-width: 768px):**
- Menu cards: `grid-template-columns: repeat(2, 1fr)`.
- Hero height: `420px`.
- Nav: full horizontal layout restored.

**@media (min-width: 1024px):**
- Menu cards: `grid-template-columns: repeat(4, 1fr)`.
- Hero height: `var(--hero-height-desktop)`.
- Contact row: full horizontal.

**@media (min-width: 1280px):**
- Container reaches `var(--container-max)`.
- Minor spacing refinements.

### Phase 10 — Polish Pass
- Verify all images render at correct aspect ratios using `object-fit: cover`.
- Confirm section title decorative lines are perfectly centered on all screen sizes.
- Confirm button widths are consistent across all cards.
- Audit color contrast: light text on dark backgrounds and dark text on cream backgrounds must both pass readability.
- Confirm no content overflows horizontally at 375px viewport width.
- Confirm `cursor: pointer` is applied to all buttons and nav links.
- Confirm smooth transitions on interactive elements (`:hover`) are CSS-only.
- Remove all unused CSS rules.

---

## 7. Reusable CSS Class Reference

| Class | Purpose |
|---|---|
| `.container` | Centered max-width wrapper |
| `.section-title` | Heading with decorative flanking lines |
| `.btn-order` | Dark brown order button, full-width inside card |
| `.btn-cta` | Hero outlined CTA button |
| `.menu-card` | Full card component, flex-column |
| `.card-image` | Fixed-height image container |
| `.card-body` | Dark card footer with name, price, button |

---

## 8. Final QA Checklist

- [ ] Project uses only `index.html` and `style.css` — zero JavaScript
- [ ] Google Fonts load correctly from CDN
- [ ] All six image assets are referenced with correct relative paths
- [ ] Navbar logo renders in cursive Dancing Script font
- [ ] Navbar links are right-aligned; "Home" has active underline
- [ ] Hero background image covers its section fully with dark overlay
- [ ] Hero heading and CTA button are centered vertically and horizontally
- [ ] Section titles display decorative flanking lines on both sides
- [ ] All four menu cards are equal height with bottom-aligned Order buttons
- [ ] Menu grid is 4 columns on desktop, 2 on tablet, 1 on mobile
- [ ] About section paragraph is centered and readable
- [ ] Contact section displays three items in a row on desktop
- [ ] Contact items stack vertically on mobile
- [ ] Footer image strip spans full viewport width
- [ ] Copyright bar has dark brown background and centered light text
- [ ] No horizontal scroll appears at 375px, 768px, 1024px, or 1440px
- [ ] All `:hover` states function via CSS only
- [ ] Color palette matches warm coffee theme throughout
- [ ] Typography hierarchy is consistent: logo → section headings → card titles → body

---

## 9. Key Implementation Notes for the AI Agent

The decorative flanking lines around section titles are a defining visual element of this design. Implement them as a flex row: `[line][title text][line]` where each line is a `flex: 1` element with a `border-top` rule and `margin` aligned to the text midpoint.

Cards must use `display: flex; flex-direction: column` with the `.card-body` set to `flex: 1` so all cards in a row stretch to the same height regardless of content length.

The contact section background is visibly distinct from the menu and about sections — use `var(--color-contact-bg)` specifically for that section to match the reference.

The footer consists of two entirely separate elements: the image strip and the copyright bar. Do not nest them inside a single div with a background image — they require different backgrounds and must be siblings.