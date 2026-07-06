---
name: Github Dashboard Design System
description: >
  Production-extracted design system for dense, operational web dashboards.
  Built from LavanderPro — an industrial laundry management platform.
  Provides cool-neutral palette (teal accent #0F766E), Public Sans typography
  with tabular-numeral display sizes, medium-high density layout, and a full
  component set (KPI cards, data tables, status pills, bar chart, modal).
user-invocable: true
---

# Github Dashboard Design System

## What is inside

| File | Contents |
|---|---|
| `DESIGN.md` | Full authoritative design documentation: color, type, spacing, layout, components, motion, voice, anti-patterns — all source-backed |
| `colors_and_type.css` | Paste-ready `:root` CSS custom properties + typography utilities |
| `variables.css` | Standalone `:root` token file |
| `brand.json` | Machine-readable brand metadata and palette |
| `theme.json` | Theme token bundle (light mode) |
| `kit.html` | UI kit launcher/redirect |
| `README.md` | Usage guide + product overview + preview manifest |
| `context/provenance.md` | Extraction notes — which source files were read, what was found |
| `assets/brand-icon.svg` | LavanderPro water-drop brand icon (teal background, white path) |
| `preview/colors-primary.html` | Color swatches — brand palette + semantic status pairs |
| `preview/typography-specimens.html` | Typography specimens — display numerics, nav, table headers, card titles |
| `preview/spacing-tokens.html` | Spacing scale, border radius catalogue, shadow layers |
| `preview/components-buttons.html` | Button + control states — filter pills, period buttons, icon buttons, search input, status pills, focus rings |
| `preview/components.html` | Full component catalogue — KPI cards, tables, charts, modal, avatars |
| `preview/surfaces.html` | Applied dashboard mockup with layout annotations |
| `ui_kits/app/index.html` | UI kit launcher — links to all surfaces and component files |
| `ui_kits/app/dashboard.html` | Complete dashboard application (source artifact) |

## Source context

- **Source project:** Github Dashboard (`c3b8a464-8510-4a9f-8f01-7d1b4aa05745`)
- **Product:** LavanderPro — industrial/commercial laundry management dashboard
- **Primary surface:** single-page responsive admin dashboard
- **Users:** business owner / administrator (dueño / administrador)
- **Language:** Spanish (es-MX)
- **Source quality:** critique score 5/5 (clarity 5, hierarchy 5, typography 5, motion 4, brand 5)
- **Tech:** vanilla HTML + CSS + JS; Public Sans via Google Fonts; no framework

## When to use

Apply this design system when building:
- Operations / management dashboards
- Admin panels with data tables and KPI summaries
- B2B SaaS tools requiring high information density
- Spanish-language business tools
- Any project where the brief calls for a cool, clinical, trustworthy visual posture

## How to use

1. Load `colors_and_type.css` after your Google Fonts link:
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link href="https://fonts.googleapis.com/css2?family=Public+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
   <link rel="stylesheet" href="path/to/colors_and_type.css">
   ```

2. Bind `:root` tokens in your project — all tokens are in `colors_and_type.css`.

3. Read `DESIGN.md` sections 2–6 for component HTML patterns and usage rules.

4. Copy component snippets from `preview/components.html` and `preview/components-buttons.html`.

5. Open `ui_kits/app/dashboard.html` for the full applied reference.

## Design system highlights

All highlights below are verified from the source artifact:

- **Palette:** Cool blue-gray canvas `#F0F4F8` + white surfaces `#FFFFFF` + teal accent `#0F766E`
- **Accent economy:** teal appears at ≤ 6 points per screen (brand icon, active nav, focus ring, progress bar, client count numerals, today bar)
- **Typography:** Public Sans 400–700; display numerics with progressive negative tracking (−0.02 → −0.04em); ALL-CAPS small-caps labels at 0.07–0.09em
- **Density:** medium-high — KPI strip × 5, 2fr/1fr grid, data tables, multi-region layout
- **Status colors:** warning amber, success green, info blue, danger red — each with a soft tint variant for icon backgrounds
- **No entrance animations** — operational tool; motion reserved for hover/active/open-close state transitions only
- **Accessibility:** skip link, `aria-live` on filtered tables, keyboard row navigation (Enter/Space), `focus-visible` ring using `--accent`
- **Responsive:** sidebar drawer on mobile, 2-column KPI collapses to 1, column hiding on narrow tables
