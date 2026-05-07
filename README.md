# Coffee House

Coffee House is a static, responsive coffee shop landing page built with pure HTML5 and CSS3. It includes a navbar, hero section, menu grid, about section, contact section, and footer in a clean one-page layout.

## Tech Stack

- HTML5
- CSS3
- Google Fonts: Dancing Script, Playfair Display, Lato

Zero JavaScript. Zero frameworks.

## Project Structure

```text
coffee-house/
├── index.html
├── style.css
├── README.md
└── assets/
    └── images/
        ├── hero.jpg
        ├── espresso.jpg
        ├── cappuccino.jpg
        ├── latte.jpg
        ├── mocha.jpg
        └── footer.jpg
```

## Sections Overview

### Navbar
The navbar anchors the page with the Coffee House logo and smooth in-page navigation links.

### Hero
The hero introduces the brand with a full-width image, dark overlay, headline, and call-to-action button.

### Menu
The menu presents four coffee cards in a responsive grid with images, prices, and order buttons.

### About
The about section shares the brand story and sourcing values in a centered text block.

### Contact
The contact section lists email, phone, and location with inline SVG icons and stacked labels.

### Footer
The footer closes the page with a photographic strip and a compact copyright bar.

## Responsive Breakpoints

- **Below 768px:** Mobile default; sections use mobile padding, the menu becomes one column, the hero is 300px tall, the navbar wraps, and contact items stack vertically.
- **768px:** The menu shifts to two columns and the hero grows to 420px while desktop spacing is restored.
- **1024px:** The menu returns to four columns, the hero returns to desktop height, and the contact items return to a horizontal row.
- **1280px:** The container remains capped at 1240px with no additional layout changes.

## Design System Summary

The logo uses Dancing Script, headings use Playfair Display, and all body text uses Lato. The color palette is a warm coffee theme built around cream backgrounds, dark brown surfaces, and accent brown interactive elements.

## Image Assets

All six images must be JPEG files in `assets/images/` and should be landscape-oriented.

- `hero.jpg` — hero background, minimum width 1400px
- `espresso.jpg` — espresso menu card
- `cappuccino.jpg` — cappuccino menu card
- `latte.jpg` — latte menu card
- `mocha.jpg` — mocha menu card
- `footer.jpg` — footer background strip, minimum width 1400px

## Getting Started

No build step or dependency installation is required. Open `index.html` directly in a browser or place the folder on any static file server.

## Credits

Google Fonts is the sole external dependency. For image sourcing, Unsplash and Pexels are recommended starting points.
