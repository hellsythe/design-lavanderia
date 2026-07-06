# Provenance

## Source

| Field | Value |
|---|---|
| Source project name | Github Dashboard |
| Source project ID | c3b8a464-8510-4a9f-8f01-7d1b4aa05745 |
| Design system project ID | f36c2d84-3434-4846-a3bb-c057f23f583c |
| Design system ID | user:github-dashboard-design-system |
| Extracted on | 2026-07-05 |
| Source skill | (none — freeform project) |
| Source design system | (none — tokens extracted from source HTML) |

## Extraction method

Tokens, component patterns, and design decisions were extracted by reading:
1. `index.html` (48 KB) — the complete LavanderPro dashboard application, including all CSS custom properties, component HTML structure, and JavaScript interaction patterns
2. `critique.json` (1 KB) — a scored design critique confirming quality across clarity, hierarchy, typography, motion, and brand dimensions

All CSS custom properties in `:root` were lifted verbatim from the source. Component class names, HTML structure, and interaction patterns were documented as-is from the source artifact.

## Source artifact summary

- **Product:** LavanderPro — Panel de Control (industrial laundry management dashboard)
- **Language:** Spanish (es-MX)
- **Tech:** Vanilla HTML + CSS + JavaScript, no dependencies except Google Fonts (Public Sans)
- **Font:** Public Sans 400/500/600/700 via Google Fonts
- **Critique score:** 5/5 overall (clarity 5, hierarchy 5, typography 5, motion 4, brand 5)

## Token fidelity

All color tokens extracted exactly from source CSS `:root`. No interpolation or approximation was performed. The following were extracted verbatim:

```css
--bg: #F0F4F8; --surface: #FFFFFF; --surface-2: #F8FAFC;
--fg: #1A2332; --muted: #64748B; --border: #E1E8F0;
--accent: #0D9488; --accent-soft: #CCFBF1;
--success: #059669; --success-soft: #D1FAE5;
--warning: #D97706; --warning-soft: #FEF3C7;
--danger: #DC2626; --danger-soft: #FEE2E2;
--info: #2563EB; --info-soft: #DBEAFE;
--purple: #7C3AED; --purple-soft: #EDE9FE;
--sidebar-w: 256px; --topbar-h: 56px;
--radius: 10px;
--shadow: 0 1px 3px rgba(0,0,0,.06), 0 1px 2px rgba(0,0,0,.04);
```

## Typography fidelity

Font family, weights, and scale extracted from source CSS. Precise sizes verified from class definitions:
- `.kpi-value`: 28px, −0.02em
- `.revenue-total`: 30px, −0.03em  
- `.cycle-value`: 44px, −0.04em
- `.brand-name`: 15px, 700, −0.01em
- `.nav-label / thead th`: 10px ALL-CAPS, 0.07–0.09em

## Assets extracted

| Asset | Source location | Destination |
|---|---|---|
| Brand icon SVG | Inline in `index.html` sidebar | `assets/brand-icon.svg` |

## Skipped files

None — all copied files were read and analyzed.

## Limitations

- No logo image file existed in the source project; the brand mark is a pure SVG path (water-drop shape)
- No font files — Public Sans is loaded via Google Fonts CDN; no offline font files to preserve
- No additional screenshot or reference images were present in the source project
