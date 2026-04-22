# AGENTS.md

Guidance for autonomous coding agents operating in `RealTech`.
This repo is a static website, so quality checks are mostly runtime/manual.

## Project Overview

- Type: static multi-page site (HTML + CSS)
- Entry page: `index.html`
- Major areas: `laptop/`, `cpu/`, `mthrbrd/`, `ram/`, `casing/`, `about/`, `cart/`
- Shared styles: `css/style.css`
- Section styles: each section has a local `css/` folder
- Tooling status: no `package.json`, no CI config, no test framework configured

## Rule Files (Cursor/Copilot)

Checked locations:

- `.cursor/rules/` -> not present
- `.cursorrules` -> not present
- `.github/copilot-instructions.md` -> not present

If any of these files are added later, treat them as higher-priority instructions and merge them into this guide.

## Build / Run Commands

No build step exists. Use a static server for runtime checks.

- Preferred:
  - `python -m http.server 5500`
  - Open `http://localhost:5500`
- Alternatives:
  - VS Code Live Server
  - Any static file server that preserves relative paths

## Lint Commands

No mandatory linters are configured.

Optional ad-hoc commands (run only when useful):

- HTML: `npx htmlhint "**/*.html"`
- CSS: `npx stylelint "**/*.css"`

Notes:

- Do not add new lint dependencies unless the user requests it
- Report lint results, but do not treat them as hard gates unless instructed

## Test Commands

There is no automated test suite in this repository.
Testing is manual and browser-based.

### Full Smoke Test

1. Start server: `python -m http.server 5500`
2. Open `index.html` via server URL
3. Navigate each category page (`laptop`, `cpu`, `mthrbrd`, `ram`, `casing`)
4. Open at least one `*-spec.html` page per category
5. Verify images/icons load and links do not 404
6. Check desktop and narrow/mobile widths

### Single Test (important)

Because no runner exists, a "single test" means a targeted single-page validation.

- Example single-page check:
  - `http://localhost:5500/cpu/cpu-spec/14900K-spec.html`
- Validate on that page:
  - CSS loads
  - image paths resolve
  - nav/back links work

If automated tests are added later, update this section with exact single-test commands.

## Suggested Pre-Handoff Validation

- `git status --short` to confirm only intended files changed
- Runtime check through local server for pages you edited
- If shared CSS changed, verify at least 3 pages from different sections

## Architecture and Organization

- Top-level pages:
  - `index.html`
  - `about/about.html`
  - `cart/cart.html`
- Category pattern:
  - listing page: `[category]/[category].html`
  - detail pages: `[category]/[category]-spec/*.html`
- Shared assets:
  - `logoimg/`, `categimg/`, root `css/`

## Code Style Guidelines

Follow existing file-local style; prefer minimal, low-risk edits.

### HTML

- Keep indentation consistent (existing files use 4 spaces)
- Use lowercase tags/attributes
- Keep semantic structure when possible (`nav`, `section`, `footer`)
- Preserve meaningful `<title>`
- Keep explicit closing tags
- Ensure every `<img>` has `alt`

Path conventions in this repo:

- Existing code uses both root-like (`/path`) and relative (`./`, `../`) links
- For new edits, prefer relative paths compatible with static hosting
- Stay consistent with the style already used in the file you modify
- After any path update, manually verify navigation and asset loading

### CSS

- One declaration per line
- Keep selector blocks focused by component/area
- Reuse existing classes before adding new ones
- Prefer class selectors over broad element overrides for new behavior
- Preserve current breakpoints unless a new one is clearly required
- Avoid broad rewrites in legacy files; keep changes scoped

### JavaScript / TypeScript / Types

- No JS/TS currently exists in this project
- No type checker or TS config exists
- If adding JS, keep it page-scoped and minimal unless asked otherwise
- If adding TS/tooling, do so only with explicit user approval

### Imports and Dependencies

- No module-import architecture is present
- Current external dependency: Font Awesome CDN in HTML
- Do not add new third-party libraries/CDNs unless necessary and approved

### Naming Conventions

- Filenames: lowercase, kebab-case where applicable
- Detail pages follow existing `*-spec.html` naming
- CSS files are short and section-oriented (`cpu.css`, `lapt.css`, etc.)
- Class/ID names should be clear and consistent with local patterns

### Error Handling and Reliability

In this repo, reliability issues are usually broken links, bad paths, or invalid markup/CSS.

Before finishing, always verify:

- Edited links resolve correctly
- Edited image paths load
- No unclosed/invalid HTML tags in changed blocks
- No obvious CSS syntax errors in changed blocks
- File/path casing matches actual filenames

## Change Management

- Keep changes narrow and request-focused
- Avoid repo-wide formatting churn
- Do not rename/move files unless requested
- Preserve content structure when doing style-only updates
- For repeated UI changes, keep related pages consistent

## Commit / PR Notes (when requested)

- Describe user-visible impact (layout, navigation, content)
- List which pages were manually validated
- Mention limitation: no automated tests currently available

## Quick Checklist

1. Identify affected pages and related shared CSS
2. Implement minimal, consistent edits
3. Run local server and validate changed pages
4. Check desktop + mobile/narrow layout behavior
5. Report exactly what changed and how it was verified
