# rules.md

## CORE AUTHORITY
This file is the permanent source of behavioral and technical rules for the AI agent during the entire Coffee House Landing Page build.

The agent must obey these rules in every phase regardless of the current prompt.

If a phase prompt conflicts with this file, this file has higher authority.

---

## PRIMARY MISSION
Build a responsive Coffee House landing page using HTML and CSS only.

The final result must visually reflect:
- warm coffee aesthetic
- balanced clean structure
- elegant typography
- dark brown + cream palette
- simple premium landing page composition

The goal is not random webpage generation.

The goal is controlled, visually coherent, reference-faithful implementation.

---

## TECHNOLOGY LIMITS
The agent is strictly limited to:

- HTML5
- CSS3

The following are forbidden:

- JavaScript
- frameworks
- bootstrap
- tailwind
- libraries
- preprocessors
- external UI kits
- canvas tricks
- svg-generated layouts unless explicitly requested

No tool outside native HTML/CSS may be introduced.

---

## SECTION-BY-SECTION EXECUTION LAW
The agent must build only the section requested in the current phase.

The agent must never:
- jump ahead
- partially build future sections
- inject speculative styling for unfinished areas
- restructure previous completed sections unless asked

Allowed workflow:
1. build requested section structure
2. build requested section layout
3. build requested section styling
4. ensure requested section responsiveness
5. stop

Then wait for next phase.

---

## STRUCTURE BEFORE BEAUTY RULE
Visual polish is forbidden before structural correctness.

For every section:
1. semantic HTML must be completed first
2. dimensions and alignment second
3. spacing third
4. colors fourth
5. visual refinement last

The agent must not chase aesthetics while layout is unstable.

---

## SIMPLICITY LAW
The agent must always choose the simplest stable implementation.

Avoid:
- over-nesting
- unnecessary wrappers
- duplicate classes
- complicated selectors
- hardcoded hacks
- position absolute abuse
- transform hacks when normal layout tools can solve it

Every block should remain easy to read and easy to maintain.

---

## CSS LAYOUT LAW
The agent must follow these layout responsibilities:

### CSS Grid must be preferred for:
- main page sectional spacing when needed
- menu card layout
- any repeated card group
- two-dimensional content arrangement

### Flexbox must be preferred for:
- navbar horizontal alignment
- button/icon alignment
- contact info rows
- centering small groups of elements
- one-dimensional row/column alignment

The agent must not misuse flex where grid is cleaner, or misuse grid where flex is simpler.

---

## RESPONSIVENESS IS MANDATORY
Responsiveness is not optional.

Every section built in every phase must immediately support responsive behavior.

The agent may not postpone responsiveness until the end.

Required breakpoints:

```css
@media (max-width: 1280px) { }
@media (max-width: 1024px) { }
@media (max-width: 768px) { }
@media (max-width: 480px) { }# rules.md — Coffee House Landing Page
## Agent Behavioral & Design System Rules

---

## AUTHORITY

This file is the permanent authority for the entire build.
The agent must read this file before executing any phase prompt.
If a phase prompt conflicts with this file, this file wins.

---

## PRIMARY MISSION

Build a responsive Coffee House landing page using HTML5 and CSS3 only.

The result must reflect:
- A warm, premium coffee aesthetic
- A dark brown and cream color palette
- Elegant serif-driven typography
- Clean, balanced, reference-faithful layout

The goal is controlled, visually coherent implementation — not generic webpage generation.

---

## TECHNOLOGY RULES

**Allowed:**
- HTML5 (semantic tags only)
- CSS3 (native features only)
- Google Fonts (via a single `<link>` tag in `<head>`)
- Inline SVG (only when used for contact icons)

**Forbidden:**
- JavaScript of any kind
- CSS frameworks (Bootstrap, Tailwind, etc.)
- CSS preprocessors (SASS, LESS, etc.)
- External UI libraries or icon kits
- Canvas-based layouts
- Any tool outside native HTML and CSS

---

## FILE STRUCTURE

The agent must respect this exact structure and never deviate from it.

```
coffee-house/
├── index.html
├── style.css
└── assets/
    └── images/
        ├── hero.jpg
        ├── espresso.jpg
        ├── cappuccino.jpg
        ├── latte.jpg
        ├── mocha.jpg
        └── footer.jpg
```

All image references in HTML and CSS must use relative paths from the root.
Example: `assets/images/hero.jpg`

---

## DESIGN SYSTEM

### Colors

The agent must declare all colors as CSS variables in `:root` and never hardcode a color value outside of this block.

```css
:root {
  --color-primary-bg: #F4E8D9;
  --color-contact-bg: #EDD9C0;
  --color-surface-dark: #4A2D22;
  --color-surface-darkest: #2F1B14;
  --color-text-light: #FFF8F0;
  --color-text-dark: #3A241C;
  --color-border-light: #D9C4B1;
  --color-accent-brown: #8A5A3B;
  --color-card-body-bg: #4A2D22;
  --color-overlay: rgba(30, 15, 8, 0.45);
  --shadow-card: 0 2px 10px rgba(42, 20, 10, 0.12);
}
```

### Typography

```css
:root {
  --font-logo: 'Dancing Script', cursive;
  --font-heading: 'Playfair Display', Georgia, serif;
  --font-body: 'Lato', Arial, sans-serif;
}
```

Font roles:
- `--font-logo` → navbar logo only
- `--font-heading` → all section titles, card titles, hero heading
- `--font-body` → nav links, body text, buttons, prices, copyright

Google Fonts link to include in `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@400;700&family=Lato:wght@400;600&display=swap" rel="stylesheet">
```

### Layout

```css
:root {
  --container-max: 1240px;
  --section-padding-desktop: 64px 24px;
  --section-padding-mobile: 40px 16px;
  --card-gap: 24px;
  --nav-height: 72px;
  --hero-height-desktop: 560px;
  --radius-button: 4px;
}
```

---

## CSS LAYOUT LAW

**CSS Grid must be used for:**
- Menu card layout (4 columns → 2 → 1)
- Any repeated card or tile group
- Two-dimensional content regions

**Flexbox must be used for:**
- Navbar alignment (logo left, links right)
- Centering hero content
- Contact items row
- Button and icon alignment
- Any single-axis alignment task

The agent must not use Grid where Flexbox is the correct tool, and must not use Flexbox where Grid is the correct tool.
`position: absolute` is permitted only for the hero overlay layer. It must not be used as a general layout mechanism.

---

## RESPONSIVENESS LAW

Responsiveness is mandatory and must be applied within the same phase as the section being built. It must never be deferred.

The agent must use `max-width` media queries in this order:

```css
@media (max-width: 1280px) { }
@media (max-width: 1024px) { }
@media (max-width: 768px)  { }
@media (max-width: 480px)  { }
```

Required responsive behaviors:
- Menu cards: 4 columns → 2 at 768px → 1 at 480px
- Hero height reduces on mobile
- Navbar simplifies on small screens (flex-wrap is permitted)
- Contact items stack vertically below 768px
- No horizontal overflow at any breakpoint

---

## STRUCTURAL EXECUTION LAW

The agent builds only the section specified in the current phase prompt.
It must never build ahead, inject speculative styles, or restructure a completed section unless explicitly instructed.

For every section, the agent must follow this sequence:
1. Semantic HTML structure
2. Dimensions and alignment
3. Spacing
4. Colors and typography
5. Responsiveness
6. Stop and wait

---

## STRUCTURE BEFORE BEAUTY

Visual polish is forbidden before structural correctness.
The agent must not adjust font sizes, shadows, or decorative details while the layout is still unstable.
Aesthetics are addressed only after the layout is confirmed correct.

---

## SIMPLICITY LAW

The agent must always choose the simplest stable solution.

**Avoid:**
- Unnecessary wrapper divs
- Duplicate or redundant classes
- Overly specific CSS selectors
- `position: absolute` outside the hero overlay
- Hardcoded pixel hacks
- `transform` tricks when standard layout solves the problem

Every block of HTML and CSS must be easy to read and easy to maintain.

---

## CSS FILE ORGANIZATION

`style.css` must follow this exact section order:

1. CSS Reset + `box-sizing: border-box`
2. `:root` variables (colors, typography, layout)
3. Global base styles (`body`, `a`, `img`)
4. Utility classes (`.container`, `.section-title`, `.btn-cta`, `.btn-order`)
5. Section styles in page order: navbar → hero → menu → about → contact → footer
6. Media queries at the bottom, grouped by breakpoint

---

## REUSABLE CLASS REFERENCE

The agent must use these class names consistently across all phases:

| Class | Purpose |
|---|---|
| `.container` | Centered max-width wrapper for all sections |
| `.section-title` | Heading with decorative flanking lines |
| `.btn-cta` | Hero outlined CTA button |
| `.btn-order` | Card order button, full width, accent brown |
| `.menu-card` | Full card component using flex-column |
| `.card-image` | Fixed-height image container inside card |
| `.card-body` | Dark card lower section with name, price, button |

---

## DO AND DON'T SUMMARY

| DO | DON'T |
|---|---|
| Use CSS variables for every color and spacing value | Hardcode color or size values outside `:root` |
| Use semantic HTML tags (`header`, `nav`, `main`, `section`, `article`, `footer`) | Use generic `div` soup instead of semantic elements |
| Apply responsiveness in the same phase as the section | Defer responsiveness to a later phase |
| Use Grid for cards and two-dimensional layouts | Use Flexbox for grid-style card layouts |
| Use Flexbox for navbar, contact row, and alignment | Use Grid where a single axis is all that is needed |
| Keep all image paths relative | Use absolute or external image URLs |
| Build one section per phase, then stop | Jump ahead or partially scaffold future sections |
| Follow structure → spacing → color → polish sequence | Chase aesthetics before layout is stable |
| Keep CSS organized in the defined file order | Scatter section styles randomly through the file |
| Use `var(--font-heading)` for all titles | Mix font families freely |