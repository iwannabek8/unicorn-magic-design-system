# ✨ Afterglow — a design system with a saturation knob

> The joy of [UnicornMagic](../), grown up. Semantic tokens, a vibe dial, and the boring components that let it ship in real products — without losing the sparkle.

**Positioning:** nobody else is doing tunable joy. `--ag-vibe` is a single CSS custom property between `0` and `1` that scales the entire system's saturation, sparkle, motion amplitude, and border radius. Same components, radically different register.

## What's new vs. UnicornMagic

| Layer | UnicornMagic | Afterglow |
|---|---|---|
| **Tokens** | Brand primitives only (`--lf-pink-hot`, `--lf-grad-rainbow`) | Two layers: brand primitives **+ semantic aliases** (`--ag-color-accent`, `--ag-color-danger`) |
| **Typography** | Baloo 2 + Quicksand — playful throughout | **Fraunces** (variable, SOFT axis dialed by vibe) + **Inter** for body |
| **Vibe** | Fixed — always maximum | `--ag-vibe` dial: `0` = boardroom, `1` = rave. Five presets shipped. |
| **Motion** | Ambient sparkle everywhere | Motion **intent tokens** (`--ag-motion-celebrate`, `--ag-motion-acknowledge`, `--ag-motion-transition`). Sparkles fire on state changes. |
| **Themes** | Light + Galaxy (dark) | Daylight + **Twilight** (mature dark) + **High Contrast** + print styles. All theme-safe via semantic layer. |
| **Components** | Party set (buttons, cards, stickers, alerts) | Party set **+ tables, forms with validation, tabs, breadcrumbs, modal, toast, skeleton, empty state, kbd** |
| **A11y** | AA contrast, focus-visible, reduced-motion | Above, **plus** `prefers-reduced-transparency`, HC theme, validation via icon+text (never color alone) |

## Quick start

```html
<link rel="stylesheet" href="afterglow/css/tokens.css" />
<link rel="stylesheet" href="afterglow/css/base.css" />
<link rel="stylesheet" href="afterglow/css/effects.css" />
<link rel="stylesheet" href="afterglow/css/components.css" />
```

Or open [`afterglow/index.html`](index.html) — that's the live showcase with the vibe slider wired up.

## The vibe dial

```css
:root { --ag-vibe: 0.35; } /* whole-page override */
.hero { --ag-vibe: 0.9; }  /* localized on one section */
```

Or use a preset attribute:

```html
<body data-vibe="boardroom">  <!-- 0.15, animations paused -->
<body data-vibe="weekday">    <!-- 0.35 -->
<body data-vibe="studio">     <!-- 0.55 — default-ish -->
<body data-vibe="afterhours"> <!-- 0.80 -->
<body data-vibe="rave">       <!-- 1.00 — full unicorn -->
```

What scales with vibe:
- Gradient **saturation** (60% → 140%)
- Sparkle & glitter **opacity** (0 → 1)
- Glow **strength** (all `--ag-glow-*` tokens)
- Border **radius** (0.6× → 1.0×)
- Animation **amplitude** (0.4× → 1.2×)
- Fraunces display **SOFT axis** (20 → 100)

At `vibe: 0` all decorative animations pause. `prefers-reduced-motion` still hard-overrides everything.

## Semantic tokens (Layer 2)

Components read only these. Rebrand by remapping them; never by touching Layer 1.

```css
--ag-color-bg
--ag-color-surface
--ag-color-surface-2
--ag-color-surface-sunk
--ag-color-border
--ag-color-border-strong

--ag-color-ink
--ag-color-ink-muted
--ag-color-ink-subtle
--ag-color-ink-inverse

--ag-color-accent           /* CTA color */
--ag-color-accent-hover
--ag-color-accent-soft
--ag-color-accent-gradient  /* CTA gradient */

--ag-color-success / -soft
--ag-color-warning / -soft
--ag-color-danger  / -soft
--ag-color-info    / -soft

--ag-color-focus
--ag-focus-ring

--ag-motion-transition
--ag-motion-acknowledge
--ag-motion-celebrate
```

## Component quick reference

```html
<!-- Buttons -->
<button class="ag-btn ag-btn--primary">Primary</button>
<button class="ag-btn ag-btn--secondary">Secondary</button>
<button class="ag-btn ag-btn--ghost">Ghost</button>
<button class="ag-btn ag-btn--danger">Delete</button>
<button class="ag-btn ag-btn--rainbow">Rainbow ✨</button>

<!-- Card -->
<article class="ag-card">
  <div class="ag-card__header"><h3 class="ag-card__title">Title</h3></div>
  <div class="ag-card__body">…</div>
  <div class="ag-card__footer">…</div>
</article>

<!-- Form with validation -->
<div class="ag-field" data-state="error">
  <label class="ag-label" for="email">Email</label>
  <input class="ag-input" id="email" aria-invalid="true" />
  <div class="ag-field__help">⚠ Please enter a valid email.</div>
</div>

<!-- Feedback -->
<div class="ag-alert ag-alert--success">…</div>
<div class="ag-toast">…</div>

<!-- Nav / breadcrumbs / tabs -->
<nav class="ag-nav">…</nav>
<ol class="ag-crumbs">…</ol>
<div class="ag-tabs" role="tablist">…</div>

<!-- States -->
<span class="ag-skeleton"></span>
<div class="ag-empty">…</div>
<div class="ag-progress"><div class="ag-progress__bar" style="width:35%"></div></div>
```

## Themes

```html
<html data-theme="twilight">      <!-- mature dark: gradients confined to accents -->
<html data-theme="highcontrast">  <!-- WCAG AAA: solids only, borders everywhere -->
<!-- no attribute = Daylight -->
```

Print styles automatically flatten to black-on-white.

## Usage guidance

**Do**
- One primary/rainbow button per view.
- Use gradients on 5–10% of surface. The rest reads as calm ink on paper.
- Fire sparkles on success — never as ambient decoration.
- Set `--ag-vibe` **per section** to give a page dynamic tempo (calm content areas, energetic CTAs).

**Don't**
- Stack multiple rainbow buttons.
- Put body text on a gradient background — use `--ag-color-surface` behind copy.
- Reach into Layer 1 tokens from your app CSS. If you need a new brand color, add a Layer 2 semantic alias for it.
- Rely on color alone for state — every validation state pairs color with an icon and text.

## Accessibility

- Body text uses semantic ink tokens (grape-800 in light, grape-100 in twilight) — AA at all vibes.
- Focus ring is a solid 2px outline **plus** a soft shadow ring for extra clarity.
- All animations honor `prefers-reduced-motion`.
- Page wash honors `prefers-reduced-transparency`.
- High Contrast theme provided; solid colors replace gradients, borders on everything.
- Decorative sparkles are wrapped in `aria-hidden="true"`.
- Validation communicates state with **icon + text + color** — never color alone.

## What's not here yet (v0.2 targets)

- DataGrid / sortable table
- Menu / dropdown primitive
- Combobox / autocomplete
- Popover / tooltip
- Real toast queue (not just the CSS shell)
- Figma library + Tokens Studio JSON export
- npm publish (`@afterglow/tokens`, `@afterglow/css`)

## License

Same as parent (see [`../LICENSE`](../LICENSE)).

---

*Stay sparkly — but on your own terms. ✨*
