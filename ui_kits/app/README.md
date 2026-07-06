# UI Kit — LavanderPro Dashboard

Applied interface kit for the **Github Dashboard Design System** (`user:github-dashboard-design-system`). All components are extracted from LavanderPro — a production industrial laundry dashboard (source: `c3b8a464-8510-4a9f-8f01-7d1b4aa05745`, critique 5/5).

---

## Structure

```
ui_kits/app/
├── index.html       ← launcher, links to surfaces and component previews
├── dashboard.html   ← complete LavanderPro app — all components in context
└── README.md        ← this file
```

`index.html` loads `../../colors_and_type.css` for all design tokens.

Component equivalents for teams extracting to a framework: `components/Sidebar.jsx`, `components/TopBar.jsx`, `components/KpiCard.jsx`, `components/DataTable.jsx`, `components/StatusPill.jsx`, `components/RevenueChart.jsx`.

---

## Component Files

All components below are implemented in `dashboard.html`. Use it as a copy-paste reference when building new surfaces with this design system.

| Component | Key classes | Notes |
|---|---|---|
| Sidebar | `.sidebar`, `.sidebar-brand`, `.nav-item`, `.nav-item.active` | 256px fixed; `grid-row: 1/-1`; accent-soft active state |
| Topbar | `.topbar`, `.page-title`, `.breadcrumb`, `.icon-btn` | 56px sticky; z-index 90 |
| KPI Strip | `.kpi-strip`, `.kpi-card`, `.kpi-label`, `.kpi-value`, `.kpi-delta` | 5 cards; 28px tabular value; semantic soft-bg icon |
| Status Pills | `.pill`, `.pill-dot`, `.pill.proceso`, `.pill.listo`, `.pill.pendiente`, `.pill.entregado` | 999px radius; 11px 700; dot + text same semantic color |
| Filter Pills | `.filter-group`, `.filter-pill`, `.filter-pill.active` | bg group; active = white + shadow; press `translateY(1px)` |
| Active Orders Table | `table`, `thead th`, `tbody td`, `.td-mono`, `.td-bold`, `.td-muted` | 10px ALL-CAPS headers; tabular-nums; clickable rows keyboard-accessible |
| Revenue Bar Chart | `.bar-chart`, `.bar`, `.bar.today`, `.period-btn` | 88px height; today bar = accent; period switcher via period-btn.active |
| Cycle Time | `.cycle-value`, `.progress-track`, `.progress-fill`, `.cycle-stats` | 44px −0.04em; accent progress fill; 2×2 stat grid |
| Order History | `.search-input` + `tbody[aria-live]` | Focus glow ring; live filtered; empty-state fallback |
| Top Clients | `.client-row`, `.client-avatar`, `.client-count` | Initials avatar; accent-colored count numerals |
| Modal | `.modal-overlay`, `.modal`, `.detail-grid` | Backdrop blur; 2-col detail; Escape + overlay-click dismiss |
| Empty State | `.empty-row`, `.empty-state-wrap` | Icon (opacity .3) + plain text statement |
| Skip Link | `.skip-link` | Visible on focus only; accent bg; accessibility |

---

## Reuse Guide

1. Open `dashboard.html` in a browser to inspect all components in context
2. Copy the `:root` block from `../../colors_and_type.css` into your `<style>` block
3. Load Google Fonts: `Public Sans` weights 400/500/600/700
4. Lift component HTML + matching CSS class rules from `dashboard.html`
5. See `../../preview/components.html` for isolated component variants
6. See `../../preview/components-buttons.html` for button/control interactive states
7. Read `../../DESIGN.md` section 9 for anti-patterns to avoid
8. Check `../../context/provenance.md` for token fidelity documentation

---

## Design Notes

Design decisions extracted from source and documented in `../../DESIGN.md`:

- **Layout:** CSS Grid `256px 1fr` × `56px 1fr`; sidebar spans full height with `grid-row: 1/-1`
- **Accent economy:** teal `#0F766E` at exactly 6 anchor points per screen — brand icon bg, active nav, focus-visible ring, progress fill, client count numerals, today chart bar
- **Typography:** Public Sans 400–700; `font-variant-numeric: tabular-nums` on all data columns; negative tracking from −0.02em (28px KPI) to −0.04em (44px cycle hero)
- **Status palette:** warning/process, success/ready, info/pending, muted/delivered — each with a soft tint variant for icon backgrounds
- **Motion:** No entrance animations (operational tool). Transitions only: hover 0.12–0.15s, sidebar slide 0.22s, chart height 0.30s. Press states: `translateY(1px)` on buttons, `scale(.93)` on modal close
- **Accessibility:** skip link, `aria-live="polite"` on filtered tables, keyboard row navigation (Enter/Space), 44px mobile touch targets
- **Responsive:** sidebar drawer on ≤768px; KPI grid 5→3→2 columns; table cols 3+4 hidden at ≤600px

---

## Source Basis

`dashboard.html` is the original LavanderPro production dashboard, preserved exactly from the source project. All component shapes, spacing values, color applications, and interaction patterns are intentional design decisions — documented in `../../DESIGN.md`.

Future agents reusing this kit should treat `dashboard.html` as the canonical applied-surface reference for the Github Dashboard Design System.

---

## Token Reference

Load from `../../colors_and_type.css`:

```css
--bg: #F0F4F8;       /* page canvas      */
--surface: #FFFFFF;  /* cards / panels   */
--fg: #1A2332;       /* primary text     */
--muted: #64748B;    /* secondary text   */
--border: #E1E8F0;   /* hairlines        */
--accent: #0F766E;   /* teal — sparingly */
--radius: 10px;      /* card corners     */
--shadow: 0 1px 3px rgba(0,0,0,.06), 0 1px 2px rgba(0,0,0,.04);
```
