# Github Dashboard Design System

> **Category:** Project Design System  
> **Surface:** web — responsive dashboard / admin UI  
> **Product context:** LavanderPro — industrial & commercial laundry management platform  
> **Source project:** c3b8a464-8510-4a9f-8f01-7d1b4aa05745  
> **Design system id:** user:github-dashboard-design-system

## 0. Source Context & Evidence

This design system was extracted from the **LavanderPro** source project (id: `c3b8a464-8510-4a9f-8f01-7d1b4aa05745`). All tokens, component patterns, copy conventions, and interaction rules below are derived directly from the source artifact — not invented or assumed.

### Source files analyzed

| File | Size | What was extracted |
|---|---|---|
| `index.html` | 48 KB | All CSS `:root` tokens; every component class; full layout structure; JS interaction patterns; live data shape; copy tone |
| `critique.json` | 1 KB | Confirmed quality scores: clarity 5/5, hierarchy 5/5, typography 5/5, motion 4/5, brand 5/5 |

### Source product summary

- **Product:** LavanderPro — Panel de Control (industrial laundry management dashboard)
- **Primary surfaces:** single-page responsive admin dashboard
- **Primary users:** laundry business owner / administrator (dueño / administrador)
- **Core capabilities:** active order tracking (pedidos activos), daily revenue (ingresos hoy), registered customers (clientes registrados), order history (historial), average cycle time (tiempo de ciclo promedio)
- **Language:** Spanish (es-MX) throughout
- **Tech stack:** Vanilla HTML + CSS + JavaScript; Google Fonts (Public Sans); no frontend framework
- **Critique score:** 5/5 overall — a deliberately high-quality reference artifact

### Key design decisions confirmed by source evidence

- Cool blue-gray `#F0F4F8` canvas (not warm/beige) — source `:root` `--bg`
- Teal `#0F766E` accent applied exactly 6 times per screen (brand icon, active nav, focus ring, progress bar, client count, today bar) — adjusted from source `#0D9488` for WCAG AA text contrast
- Public Sans 400/500/600/700 loaded via Google Fonts — verified from source `<link>`
- Negative letter-spacing progressively tightens with display size (−0.02 → −0.03 → −0.04em) — verified from `.kpi-value`, `.revenue-total`, `.cycle-value` source CSS
- ALL-CAPS labels at 10px, 700 weight, 0.07–0.09em tracking — verified from `.kpi-label`, `thead th`, `.nav-label`
- `font-variant-numeric: tabular-nums` on all data columns — verified from `tbody td`, `.kpi-value`, `.revenue-total`
- No entrance animations — confirmed by critique note: "Sin animaciones de entrada de datos — correcto para dashboard operativo v1"

---

## 1. Visual Theme & Atmosphere

LavanderPro is an operational command centre for laundry business owners and administrators. Every design decision serves legibility under real working conditions: glancing at KPIs between customer interactions, scanning order queues mid-shift, reading status at a distance.

**Mood:** cool, clinical, trustworthy — a working tool, not a portfolio piece.  
**Palette stance:** neutral cool-grey canvas with a single teal accent used at disciplined points. No gradient washes. No warm/cozy tones.  
**Density:** medium-high. Information is the feature — breathing room is earned, not given by default.  
**Typography posture:** tight negative tracking on display numerics; ALL-CAPS small-caps labels for scannable metadata; tabular-numeral font-variant throughout data columns.

---

## 2. Color

All colors are defined as CSS custom properties. Semantic soft variants exist for icon backgrounds and badge fills; they are never used as large surface washes.

### Brand palette

| Token | Hex | Role |
|---|---|---|
| `--bg` | `#F0F4F8` | Page canvas — cool blue-gray |
| `--surface` | `#FFFFFF` | Card / panel background |
| `--surface-2` | `#F8FAFC` | Subtle alternate surface, hover fill |
| `--fg` | `#1A2332` | Primary text — deep navy |
| `--muted` | `#64748B` | Secondary text, icons, metadata |
| `--border` | `#E1E8F0` | Hairline borders and dividers |
| `--accent` | `#0F766E` | Teal — primary action / brand accent |
| `--accent-soft` | `#CCFBF1` | Light teal for active nav, hover fills |

### Semantic status palette

| Token | Hex | Soft hex | Soft token | Role |
|---|---|---|---|---|
| `--success` | `#059669` | `#D1FAE5` | `--success-soft` | Positive delta, completed orders |
| `--warning` | `#B45309` | `#FEF3C7` | `--warning-soft` | In-process orders, notification dot |
| `--danger` | `#DC2626` | `#FEE2E2` | `--danger-soft` | Negative delta, critical alerts |
| `--info` | `#2563EB` | `#DBEAFE` | `--info-soft` | Pending orders, informational |
| `--purple` | `#7C3AED` | `#EDE9FE` | `--purple-soft` | Cycle time KPI icon only |

### Accent economy

`--accent` (#0F766E) appears in a limited set of anchors only:
- Brand icon background (sidebar header)
- Active nav item text + `--accent-soft` background
- Focus-visible ring (`outline: 2px solid var(--accent)`)
- Progress bar fill (cycle time widget)
- Client order count numerals
- Bar chart "today" highlight bar
- Active period/filter button: accent-soft bg + accent text

**Never** use `--accent` as a page background, hero block, or large panel fill.

---

## 3. Typography

**Family:** Public Sans (Google Fonts)  
**Fallback stack:** `system-ui, -apple-system, 'Segoe UI', 'Helvetica Neue', Arial, sans-serif`  
**Base size:** 14px (1rem = 14px on `html`)  
**Smoothing:** `-webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale`

### Type scale

| Role | Size | Weight | Tracking | Usage |
|---|---|---|---|---|
| Display KPI | 28px | 700 | −0.02em | KPI card values |
| Display Revenue | 30px | 700 | −0.03em | Revenue summary total |
| Display Cycle | 44px | 700 | −0.04em | Cycle time hero value |
| Card title | 13px | 700 | 0 | Card headings |
| Brand name | 15px | 700 | −0.01em | Sidebar logo text |
| Page title | 15px | 700 | 0 | Topbar page heading |
| Body / nav | 13.5px | 500 | 0 | Navigation items, table cells |
| Body small | 13px | 400/600 | 0 | General UI copy |
| Label / ALL-CAPS | 10–10.5px | 700 | 0.07–0.09em | KPI labels, table headers, section headings |
| Meta / caption | 11–12px | 500/600 | 0 | Breadcrumbs, dates, card meta |
| Badge | 11px | 700 | 0 | Status pills, nav badges |
| Monospace | 12px | 400 | 0 | Order IDs, timestamps |

**Monospace stack:** `ui-monospace, 'Cascadia Code', Menlo, monospace`

### Typography rules

- Display numerics always use `font-variant-numeric: tabular-nums` to prevent layout shift.
- ALL-CAPS labels: `text-transform: uppercase; letter-spacing: 0.07–0.09em; font-weight: 700`.
- Negative letter-spacing intensifies as display size increases (−0.02 → −0.03 → −0.04em).
- Use `text-wrap: pretty` on card titles and KPI labels to prevent orphaned words.
- Never use Inter, Roboto, or Arial as the display face.

---

## 4. Spacing

**Baseline grid:** 4px atomic / 8px standard step  
**Content padding:** 24px (desktop), 16px (mobile ≤ 768px)

### Layout dimensions

| Token | Value | Usage |
|---|---|---|
| `--sidebar-w` | `256px` | Sidebar column width |
| `--topbar-h` | `56px` | Topbar / sidebar-brand height |
| `--radius` | `10px` | Default card border-radius |

### Spacing scale (in use)

| Value | Usage |
|---|---|
| 3px | Pill filter group inner gap |
| 4px | Pill padding-block; bar chart gap |
| 8px | Nav item padding; icon radius; cycle stat radius |
| 10px | Nav item horizontal gap; brand icon gap; client row gap |
| 12px | KPI strip gap; sidebar nav padding; sidebar footer padding |
| 14px | Card-head padding-block |
| 16px | Card-head padding-inline; KPI card padding; main grid gap |
| 20px | Main content section gap; nav section margin-bottom |
| 24px | Main content padding (desktop) |

### Border radius reference

| Context | Radius |
|---|---|
| Cards, KPI cards | `var(--radius)` = 10px |
| Brand icon | 8px |
| Icon buttons | 8px |
| Nav items | 7px |
| Modal | 14px |
| Progress track | 2px |
| Status pills | 999px (fully rounded) |
| Bar chart bars | 4px 4px 0 0 |
| Cycle stats | 8px |

### Shadow system

Default card shadow (subtle, two-layer):
```css
box-shadow: 0 1px 3px rgba(0,0,0,.06), 0 1px 2px rgba(0,0,0,.04);
```
KPI hover lift shadow:
```css
box-shadow: 0 4px 12px rgba(0,0,0,.10), 0 1px 3px rgba(0,0,0,.06);
```
Modal shadow (deep):
```css
box-shadow: 0 24px 64px rgba(0,0,0,.2);
```

---

## 5. Layout & Composition

### Page skeleton

```
┌─────────────────────────────────────────────┐
│ Sidebar (256px fixed, sticky)│ Topbar (56px)│
│                              ├──────────────┤
│ brand + nav + user           │ Main content │
│                              │ (scrollable) │
└─────────────────────────────────────────────┘
```

CSS Grid implementation:
```css
.app {
  display: grid;
  grid-template-columns: var(--sidebar-w) 1fr;
  grid-template-rows: var(--topbar-h) 1fr;
  min-height: 100vh;
}
```

### Sidebar anatomy

- Spans full height (`grid-row: 1 / -1`), sticky, `z-index: 100`
- `border-right: 1px solid var(--border)` — the only visual separation from main content
- Nav sections grouped by `nav-label` (ALL-CAPS, 10px, muted)
- Active state: `background: var(--accent-soft); color: var(--accent); font-weight: 700`
- Mobile: fixed + `transform: translateX(-256px)` / `.open` restores to `translateX(0)`
- Custom scrollbar: 4px track, `--border` thumb

### Topbar anatomy

- `position: sticky; top: 0; z-index: 90`
- Left: hamburger (mobile) + page-title (15px, 700) + breadcrumb (12px, muted)
- Right: date + icon buttons (notification dot on bell)
- Icon buttons: 34px desktop, 44px mobile

### Main content regions

1. KPI strip (5 cards, auto-collapse)
2. Main grid: Orders table (2fr) + right column (1fr): Revenue chart + Cycle time
3. Bottom grid: History table (2fr) + Top clients (1fr)

### Responsive breakpoints

| Breakpoint | Changes |
|---|---|
| ≤ 1280px | KPI: 3 columns |
| ≤ 1024px | Main grid: single column |
| ≤ 768px | Sidebar drawer; hamburger; 16px padding; KPI: 2 col |
| ≤ 600px | Table columns 3+4 hidden |
| ≤ 480px | KPI: 2 col; filter pills hidden; search input narrows to 140px |

### Information hierarchy

Urgency flows top-to-bottom, left-to-right:
1. KPI strip — immediate operational snapshot (pedidos activos first)
2. Active orders table — what needs action now
3. Revenue chart + cycle time — performance signals
4. History + top clients — contextual / retrospective

---

## 6. Components

### KPI Card

```html
<div class="kpi-card">
  <div class="kpi-label">Pedidos Activos</div>
  <div class="kpi-icon" style="background:var(--warning-soft)"><!-- 17px svg --></div>
  <div class="kpi-value">24</div>
  <div class="kpi-delta up">
    <!-- 10px arrow svg --> +3 vs. ayer
  </div>
</div>
```

- Icon: 34px square, 8px radius, semantic soft bg, semantic colored stroke SVG
- KPI value: 28px, 700, −0.02em, `tabular-nums`, line-height 1
- Delta: 11.5px, 600; `.up` = success, `.down` = danger, `.neutral` = muted
- Hover lift: `translateY(-2px)` + deeper shadow, 0.15s ease

### Status Pills

Four states: `proceso` (warning), `listo` (success), `pendiente` (info), `entregado` (muted)

```html
<span class="pill proceso">
  <span class="pill-dot"></span>En proceso
</span>
```

- 6px dot, 999px radius pill, 3px 9px padding, 11px 700
- Pair dot color with text color (same semantic token)

### Filter Pills (tab-style)

```html
<div class="filter-group">
  <button class="filter-pill active">Todos</button>
  <button class="filter-pill">En proceso</button>
</div>
```

- Group: `background: var(--bg); padding: 3px; border-radius: 8px`
- Active pill: `--surface` bg, `--fg` color, subtle shadow
- Inactive: no bg, `--muted` color; 0.12s transition

### Data Table

- `thead th`: 10px ALL-CAPS, 0.07em, muted, `white-space: nowrap`
- `tbody tr`: `border-top: 1px solid var(--border)`; hover → `--surface-2`
- `td`: 11px 16px padding, `tabular-nums`
- `.td-mono`: monospace stack, 12px, muted (order IDs, times)
- `.td-bold`: 700 weight; `.td-right`: right-aligned
- Keyboard: `tabindex="0"`, `role="button"`, Enter/Space opens detail modal
- `aria-live="polite"` on filtered tbody; empty state with icon + text

### Card

```html
<div class="card">
  <div class="card-head">
    <span class="card-title">Title</span>
    <span class="card-meta">Metadata</span>
  </div>
  <!-- body -->
</div>
```

- `background: --surface; border: 1px solid --border; border-radius: --radius; box-shadow: --shadow`
- card-head: 14px 16px padding, border-bottom, flex space-between, flex-wrap

### Search Input

```css
.search-input {
  padding: 5px 10px;
  border: 1px solid var(--border);
  border-radius: 7px;
  background: var(--surface-2);
  width: 190px; /* 140px mobile */
}
/* focus */
border-color: var(--accent);
background: var(--surface);
box-shadow: 0 0 0 3px rgba(13,148,136,.12);
```

**Usos** (2 contextos):
- **Global**: en el `Topbar` (header sticky), placeholder "Buscar pedido, cliente…". Sirve para búsqueda cross-módulo.
- **Por-tabla**: en el `CardHeader` de listas admin (categorías, servicios, clientes, etc.) para filtrar la tabla localmente. Siempre combinado con `FilterPill`s cuando aplica. Sin debounce (filtro client-side instantáneo).

Cuando el resultado de la búsqueda es vacío mostrar un `EmptyState` con copy distinto del "no hay datos aún" — ej: "Sin resultados para «xxx»".

### Spinner

Indicador de carga circular. **SIEMPRE** usar `<Spinner />` (primitiva de `@lavanderpro/ui`) en lugar del patrón inline `<span className="inline-block h-X w-X border-2 border-muted/30 border-t-accent rounded-full animate-spin" />`.

Props:
- `size`: `xs` (12px, inline en texto) · `sm` (14px, dentro de botón primary) · `md` (16px) · `lg` (24px, secciones) · `xl` (32px, hidratación full-screen).
- `tone`: `default` (muted border + accent top, sobre fondo claro) · `inverse` (white/40 + white top, sobre fondo teal/oscuro) · `muted` (border + muted top, deshabilitado).
- `label`: texto accesible (default "Cargando…").

Reglas:
- `xl` + `default` para "página hidratando" (dentro de AppShell).
- `sm` + `inverse` dentro de botones primary durante submit.
- `xs`/`sm` + `default` para inputs con loading inline.
- **SIEMPRE** dentro de un contenedor centrado (`flex items-center justify-center`).

### PageHeader

Wrapper estándar del header de página para admin pages.

```
[ícono teal] [Título + subtítulo] ........................  [acción]
```

Props:
- `icon`: `ReactNode` — ícono lucide 20px (se renderiza dentro de un cuadrado `bg-accent-soft` 36×36).
- `title`: string — texto principal (text-card font-bold).
- `subtitle`: string opcional — 1 línea debajo (text-meta text-muted).
- `action`: `ReactNode` opcional — típicamente `<Button>` alineado a la derecha.

Usar SIEMPRE en lugar del bloque inline `<div className="flex items-center gap-3 min-w-0">` con ícono teal. Garantiza consistencia entre módulos.

### ConfirmDialog

Modal de confirmación reutilizable. Usar SIEMPRE para:
- Delete (tone: 'danger', confirmLabel: 'Eliminar').
- Publish / approve (tone: 'primary').
- Acciones irreversibles en general.

Props:
- `open`, `onOpenChange`: control.
- `title`, `description`: `ReactNode` para description (permite JSX).
- `confirmTone`: 'danger' | 'primary' (default 'danger').
- `confirmLabel`, `cancelLabel`: textos.
- `pending`, `pendingLabel`: estado loading con label alternativo.
- `onConfirm`: callback.

El `description` debe incluir **consecuencias reales** de la acción. Ej: "Los servicios asociados quedarán sin categoría." (no "Esta acción es irreversible." genérico).

**Usos** (2 contextos):
- **Global**: en el `Topbar` (header sticky), placeholder "Buscar pedido, cliente…". Sirve para búsqueda cross-módulo.
- **Por-tabla**: en el `CardHeader` de listas admin (categorías, servicios, clientes, etc.) para filtrar la tabla localmente. Siempre combinado con `FilterPill`s cuando aplica. Sin debounce (filtro client-side instantáneo).

Cuando el resultado de la búsqueda es vacío mostrar un `EmptyState` con copy distinto del "no hay datos aún" — ej: "Sin resultados para «xxx»".

### Admin List Pattern (módulos CRUD)

Patrón estándar para páginas de administración (categorías, servicios, clientes, etc.). Composición:

```tsx
<div className="min-h-screen bg-canvas grid grid-cols-app">
  <Sidebar />
  <div className="min-w-0 flex flex-col">
    <Topbar title="..." breadcrumb="..." />
    <main id="main" className="flex-1 p-5 sm:p-6">

      {/* 1. Page header: ícono + título + acción primaria */}
      <div className="flex items-center justify-between gap-3 flex-wrap mb-5">
        <div className="flex items-center gap-3 min-w-0">
          <div className="h-9 w-9 rounded-icon bg-accent-soft text-accent flex items-center justify-center shrink-0">
            <Icon className="h-5 w-5" />
          </div>
          <div className="min-w-0">
            <h2 className="text-card font-bold text-fg">Título del módulo</h2>
            <p className="text-meta text-muted">Subtítulo corto (1 línea).</p>
          </div>
        </div>
        <Button>Crear / Nueva…</Button>
      </div>

      {/* 2. Card única con la lista */}
      <Card>
        <CardHeader>
          <div className="flex items-center gap-3 flex-wrap">
            <CardTitle>Listado</CardTitle>
            <FilterGroup> {/* opcional, si aplica */}
              <FilterPill active>Filtro 1</FilterPill>
              <FilterPill>Filtro 2</FilterPill>
            </FilterGroup>
            <SearchInput value={q} onChange={setQ} placeholder="Buscar…" />
          </div>
          <CardMeta>{filtered.length} resultado{filtered.length === 1 ? '' : 's'}</CardMeta>
        </CardHeader>
        <CardBody className="p-0">
          {/* 3. Empty state SI no hay data O si no hay matches */}
          {filtered.length === 0 ? (
            <EmptyState
              icon={<Inbox />}
              title={q ? `Sin resultados para «${q}»` : 'Sin datos aún'}
              description={q ? 'Probá con otro término.' : 'Conectá tu primera…'}
            />
          ) : (
            <Table>
              <TableHeader>
                <tr>
                  <TableHead>Col 1</TableHead>
                  <TableHead>Col 2</TableHead>
                  <TableHead className="text-right">Acciones</TableHead>
                </tr>
              </TableHeader>
              <TableBody>
                {filtered.map(row => (
                  <TableRow key={row.id}>
                    <TableCell>{row.col1}</TableCell>
                    <TableCell>{row.col2}</TableCell>
                    <TableCell className="text-right">
                      <IconButton icon={<Pencil />} ariaLabel="Editar" onClick={...} />
                      <IconButton icon={<Trash2 />} ariaLabel="Eliminar" onClick={...} />
                    </TableCell>
                  </TableRow>
                ))}
              </TableBody>
            </Table>
          )}
        </CardBody>
      </Card>

      {/* 4. Modales (crear/editar + confirmar delete) */}
    </main>
  </div>
</div>
```

**Reglas duras**:
- **Header**: ícono teal (accent-soft bg) + título (text-card font-bold) + 1 línea de subtítulo (text-meta text-muted). Acción primaria alineada a la derecha.
- **Card única**: una sola `Card` envolviendo la lista (no múltiples cards). `CardBody className="p-0"` para que la tabla ocupe todo el ancho.
- **CardHeader**: a la izquierda `CardTitle` (text-card) + opcional `FilterGroup` (filtros categóricos) + `SearchInput` (filtro libre). A la derecha `CardMeta` con el count ("8 categorías" / "3 resultados").
- **Búsqueda**: SIEMPRE presente. Filtra client-side sobre lo que ya está en memoria (cache offline-first). Sin debounce. Placeholder corto: "Buscar categoría…", "Buscar cliente…", etc.
- **Empty state dual**:
  - Sin data aún: "Sin categorías" / "Creá tu primera categoría para empezar a agrupar servicios."
  - Con búsqueda sin matches: "Sin resultados para «xxx»" / "Probá con otro término."
- **Acciones inline en la última columna**: `IconButton` con íconos `Pencil` (editar) y `Trash2` (eliminar). Tamaño 34px desktop, 44px mobile. `ariaLabel` específico.
- **Modales**: dos — uno de form (crear/editar) y uno de confirmación de delete. Patrón de `Modal > Content > Header (Title + Description) + Body (form) + Footer (Cancelar + Submit)`.
- **Errores del server** (ej. 409 conflicto de nombre único) → `setError('name', { type: 'manual', message: msg })` para mostrar inline en el field.

**Por qué**:
- Mantiene consistencia visual entre módulos → menos carga cognitiva para el usuario.
- Permite escanear la lista rápidamente (header + count + filter + table).
- Offline-first: la búsqueda opera sobre el cache local (Dexie), sin round-trip al server.

### Icon Button

- 34px square (44px mobile), 8px radius, 1px `--border` border
- Hover: `--bg` bg, `--fg` color; Press: `translateY(1px)`
- SVG icons: 15px, stroke-based, `stroke-width: 1.8`

### Buttons

Primary action (`.btn-new-order`):
- `padding: 6px 12px; border-radius: 7px; background: var(--accent); color: #fff;`
- `font-size: 12px; font-weight: 700;` with 14px stroke icon + 6px gap
- Hover: `#0F766E`; Press: `translateY(1px)`; Disabled: `opacity: 0.7`

Secondary action (`.btn-secondary`):
- Same padding/radius/type scale as primary
- `background: var(--surface); color: var(--muted); border: 1px solid var(--border);`
- Hover: `background: var(--bg); color: var(--fg)`; Press: `translateY(1px)`
- Use for auxiliary actions inside cards and modals (e.g. "Nuevo cliente", "Cancelar")

### Service Tabs

```html
<div class="service-tabs" role="tablist" aria-label="Vista de servicios">
  <button class="service-tab active" role="tab" aria-selected="true">Populares</button>
  <button class="service-tab" role="tab" aria-selected="false">Categorías</button>
</div>
```

- Inline flex container with `--bg` background, 3px padding, 8px radius (same posture as filter pills)
- Tab: 4px 12px padding, 6px radius, 12px 600 weight; active tab uses `--surface` bg + subtle shadow
- Update `aria-selected` and `.active` class on switch

### Service Search

```css
.service-search {
  padding: 5px 10px;
  border: 1px solid var(--border);
  border-radius: 7px;
  background: var(--surface-2);
  font-size: 12px;
  width: 170px;
}
/* focus */
border-color: var(--accent);
background: var(--surface);
box-shadow: 0 0 0 3px rgba(13,148,136,.12);
```

- Place inside `.card-head` to filter the service list as the user types
- Used in the POS service picker and the services catalog table
- Filters by service name, description, and category label

### Service Accordion

```html
<div class="service-accordion">
  <div class="accordion-item">
    <button class="accordion-header" aria-expanded="true">
      <span>Servicios generales</span>
      <span class="accordion-count">3 servicios</span>
      <svg class="accordion-icon">…chevron…</svg>
    </button>
    <div class="accordion-body open">
      <!-- service-card items -->
    </div>
  </div>
</div>
```

- `.accordion-item`: 1px `--border`, 8px radius, `--surface` bg
- `.accordion-header`: full-width button, 11px 12px padding, 13px 700, flex space-between
- `.accordion-icon`: 16px chevron, rotates 180deg when `aria-expanded="true"`
- `.accordion-body`: hidden by default, `display: flex` + gap when `.open`
- Each body contains `.service-card` items with checkbox, info, price, and stepper
- Service data includes `unit: 'kg' | 'piece'`; display price as `$55 / pz` or `$12 / kg`, and quantity as `x2 pz` / `x3 kg`
- Categories are managed from `categories.html` and stored under `lavanderpro_categories` (`{ id, name }`). Both `services.html` and `pos.html` load categories dynamically; deleted categories fall back to "Sin categoría".
- Use for browsing services by category inside POS and similar grouped selections

### Pagination

```html
<div class="pagination-bar">
  <span class="pagination-info">Mostrando 1–10 de 12 servicios · Página 1 de 2</span>
  <div class="pagination-actions">
    <button type="button" class="pagination-btn" disabled>Anterior</button>
    <button type="button" class="pagination-btn">Siguiente</button>
  </div>
</div>
```

- Container: 12px 16px padding, top border `--border`, flex space-between, wraps on mobile
- Info text: 12px, `--muted`, tabular-nums
- Buttons: 5px 12px padding, 6px radius, `--surface` bg, 1px `--border`, 12px 600
- Disabled state: 50% opacity, `--muted` text
- Place below data tables; default page size 10; clamp current page when filters or deletions change total pages

### Modal

- Backdrop: `rgba(15,23,42,.45)` + `backdrop-filter: blur(2px)`, `z-index: 300`
- Modal: `max-width: 680px`, `border-radius: 14px`, deep shadow
- Detail grid: 2-column label/value; labels 10px ALL-CAPS muted, values 14px 600
- Form modals: stacked `.form-group` fields, 2-column `.form-row` for paired fields, error message below fields, action row at bottom with secondary + primary buttons
- Form inputs: 9px 12px padding, 7px radius, `--surface-2` bg; focus: `--accent` border + 3px soft ring
- Close: Escape key, backdrop click, × button

### Onboarding Stepper

Use for multi-step post-registration flows (business info, branch, WhatsApp verification).

```html
<div class="stepper" aria-label="Progreso de configuración">
  <div class="stepper-track"><div class="stepper-progress"></div></div>
  <div class="step active">
    <div class="step-circle">1</div>
    <div class="step-label">Negocio</div>
  </div>
  <div class="step">
    <div class="step-circle">2</div>
    <div class="step-label">Sucursal</div>
  </div>
  <div class="step">
    <div class="step-circle">3</div>
    <div class="step-label">WhatsApp</div>
  </div>
</div>

<div class="step-panel active">…step content…</div>
```

- `.onboarding-card`: centered card, `max-width: 560px`, `32px 28px` padding, same surface/border/shadow as auth cards.
- `.stepper`: horizontal layout with a `4px` track (`--border`) and `--accent` progress fill; each step shows a numbered circle and ALL-CAPS label.
- `.step-circle`: `28px`, bordered circle; `.active` and `.completed` states use `--accent` background and white text.
- `.step-panel`: hidden by default; `.active` reveals the panel. Use `<fieldset>` + `<legend class="panel-title">` for each step.
- `.form-actions`: top-border separator, flex space-between; secondary **Atrás** button + primary **Continuar**/**Finalizar** button.
- `.code-input`: verification code field, `tabular-nums`, centered, `max-width: 160px`, `maxlength="6"`.
- Validate fields per step before advancing; show an error alert and focus the first invalid field.
- "Same as fiscal address" checkbox copies fiscal values into branch fields and disables them.
- Demo WhatsApp verification: generate a random 6-digit code, display it as a hint, enable the code input, and offer a resend countdown.

### Revenue Bar Chart

- Container: `height: 88px`, flex, `align-items: flex-end`, `gap: 6px`
- Bars: `--border` fill, 4px 4px 0 0 radius, `min-height: 3px`
- Today bar: `--accent` fill; heights = % of max value
- Day label: 9.5px, muted, tabular-nums below each bar

### Progress Track

```css
.progress-track { height: 4px; background: var(--border); border-radius: 2px; overflow: hidden; }
.progress-fill  { height: 100%; border-radius: 2px; background: var(--accent); }
```

### Empty State

```html
<tr class="empty-row">
  <td colspan="7">
    <div class="empty-state-wrap">
      <!-- 32px svg icon, opacity .3 -->
      <p>Sin pedidos en este estado</p>
    </div>
  </td>
</tr>
```

### Nav Badge

```css
.nav-badge {
  background: var(--warning); color: #fff;
  border-radius: 999px; padding: 1px 7px;
  font-size: 11px; font-weight: 700;
  font-variant-numeric: tabular-nums;
}
```

### Skip Link (accessibility)

```html
<a class="skip-link" href="#main">Ir al contenido principal</a>
```

- `position: absolute; top: -100%` — visible on focus, `--accent` bg, white text

---

## 7. Motion & Interaction

### Transition speeds

| Duration | Usage |
|---|---|
| 0.10s | Table row hover background |
| 0.12s | Nav item bg/color; filter pill; icon button; input border |
| 0.15s | KPI hover lift (shadow + transform); bar color |
| 0.22s | Sidebar slide (mobile open/close) |
| 0.30s | Bar chart height |

### Press states

```css
.filter-pill:active,
.period-btn:active,
.icon-btn:active { transform: translateY(1px); }
.modal-close:active { transform: scale(.93); }
```

### Focus-visible ring

```css
:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
  border-radius: 4px;
}
```

### No entrance animations

Dashboard is an operational tool. No data-load or mount animations. Motion is reserved for state changes (hover, active, open/close) only.

### Reduced motion

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { transition-duration: .01ms !important; }
}
```

---

## 8. Voice & Brand

**Product name:** LavanderPro  
**Tagline badge:** INDUSTRIAL (ALL-CAPS, 10px, muted, alongside brand name)  
**Locale:** `es-MX` — all copy in Spanish

### Copy conventions

- Labels: ALL-CAPS, no trailing punctuation — "PEDIDOS ACTIVOS", "N° ORDEN"
- Delta copy: concise comparative — "+12% vs. ayer", "+3 vs. ayer"
- Empty states: plain declarative — "Sin pedidos en este estado"
- Nav items: noun-only — "Panel Principal", "Pedidos", "Clientes"
- Dates: `sábado, 5 de julio de 2026` (weekday long + full)
- Times: 24-hour HH:MM — "08:15", "09:30"
- Order IDs: `ORD-` prefix + zero-padded number — "ORD-2847"
- Currency: `$` + `toLocaleString('es-MX')` — "$4,280"

### Tone

Functional, direct, no decorative language. Status is communicated by numbers and state labels, not by copy flourish. Empty and error states are terse and helpful, not apologetic.

---

## 9. Anti-patterns

Design choices this system explicitly avoids:

- ❌ Warm/cozy page backgrounds (beige, peach, cream) — use `#F0F4F8` cool-grey only
- ❌ `--accent` teal as a large block or hero fill — accent is a point emphasis only
- ❌ Gradient backgrounds on cards, heroes, or the page canvas
- ❌ Emoji or emoji-like SVG icons as section ornament
- ❌ Left-border colored card accents (the classic admin-dashboard cliché)
- ❌ Inter or Roboto as the display face
- ❌ Entering/mounting animations on data rows or KPI values
- ❌ Dark-mode toggle shipped as a visible UI control in the product
- ❌ Invented metrics without a real data source
- ❌ Lorem ipsum or generic "Feature One / Feature Two" placeholder copy
- ❌ Floating "demo controls" or "platform selector" panels inside the artifact
- ❌ Shadow-only cards with no border hairline — `--border` is always present
- ❌ `--purple` as anything other than the cycle-time KPI icon background
