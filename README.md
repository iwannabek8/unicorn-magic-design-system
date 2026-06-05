# 🦄✨ UnicornMagic — A Maximalist Design System 🌈🐬

Neon rainbow gradients, holographic foil, glitter, sparkles, dolphins, unicorns,
shooting stars, and kawaii energy — wrapped around a disciplined token system so the
chaos stays usable and accessible.

> **Philosophy:** Maximalist on the surface, systematic underneath. Every sparkle is a
> reusable token or class. Nothing is hard-coded twice.

## ✨ Quick start

Open `index.html` in any browser — that is the live showcase. To use the system in your
own page, link the four CSS files in order:

```html
<link rel="stylesheet" href="css/tokens.css" />
<link rel="stylesheet" href="css/base.css" />
<link rel="stylesheet" href="css/effects.css" />
<link rel="stylesheet" href="css/components.css" />
```

## 📁 Structure

| File | Purpose |
| --- | --- |
| `css/tokens.css` | Single source of truth — colors, gradients, type, spacing, radii, shadows, motion |
| `css/base.css` | Resets, fonts, page canvas, layout helpers, reduced-motion support |
| `css/effects.css` | Holographic foil, glitter, sparkles, stars, floats, rainbow rings |
| `css/components.css` | Buttons, cards, badges, stickers, inputs, toggle, nav, alerts, progress |
| `index.html` | Full live showcase / component gallery |

## 🎨 Design tokens

All tokens are CSS custom properties under `:root`. A few favorites:

```css
--lf-grad-rainbow    /* the signature multi-stop rainbow */
--lf-grad-unicorn    /* pink → purple → blue */
--lf-grad-holo       /* iridescent foil */
--lf-pink-hot        /* #ff2e9a */
--lf-ink             /* #2a0a3d — readable deep-grape text */
--lf-radius-pill     /* fully rounded */
--lf-ease-bounce     /* playful spring easing */
```

## 🧩 Component cheat sheet

```html
<!-- Buttons -->
<button class="lf-btn lf-btn--rainbow">Sparkle</button>
<button class="lf-btn lf-btn--ghost lf-ring">Outline</button>

<!-- Card with glitter -->
<article class="lf-card lf-glitter">...</article>

<!-- Badges & stickers -->
<span class="lf-badge lf-badge--cyan">New</span>
<span class="lf-sticker">🦄 Unicorn Mode</span>

<!-- Holographic surface -->
<div class="lf-holo">...</div>

<!-- Gradient / holographic text -->
<h1 class="lf-text-gradient">Rainbow words</h1>
<h2 class="lf-text-holo">Foil words</h2>
```

## ♿ Accessibility & UX clarity

- Body text uses **deep grape (`#2a0a3d`)** on light surfaces for AA contrast — the neon stays in gradients and accents, not in reading copy.
- `:focus-visible` shows a clear dashed ring on every interactive element.
- All decorative sparkles/stars are wrapped in `aria-hidden="true"`.
- Every animation collapses under `prefers-reduced-motion: reduce`.
- Components keep generous hit targets and a consistent 4px spacing scale.

## 🛠️ Customizing

Change the entire vibe by editing tokens. For example, shift the whole system warmer:

```css
:root {
  --lf-grad-unicorn: linear-gradient(135deg, #ff2e9a, #ff9a3a, #ffe93a);
}
```

Stay sparkly. ✨🦄🌈🐬💖
