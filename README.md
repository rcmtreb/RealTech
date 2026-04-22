# RealTech

RealTech is a static multi-page PC hardware showcase built with HTML and CSS.

## Quick Start

This project has no build step and no framework.

1. Start a local static server from the project root.
   - `python -m http.server 5500`
2. Open `http://localhost:5500`
3. Browse pages from the navbar or category cards.

## Project Structure

- `index.html` - home page and main category navigation
- `css/style.css` - shared home styling
- `laptop/`, `cpu/`, `mthrbrd/`, `ram/`, `casing/` - product category pages
- `about/about.html` - about page
- `cart/cart.html` - cart page
- `logoimg/` - brand and favicon assets

## Current UI/UX Behavior

- Responsive layout improvements for desktop and mobile
- Unified visual style across major pages
- Smaller top logo header spacing for cleaner page density
- Product gallery on laptop spec pages now uses:
  - arrow navigation (prev/next)
  - dot navigation
  - no horizontal bottom scroll

## Favicon

The tab icon now uses:

- `logoimg/Rlogo.png`

Each page links it with a depth-correct relative path in `<head>`.

## Notes

- No JavaScript framework is used
- No package manager or build tooling is required
- Manual browser testing is the primary validation workflow
