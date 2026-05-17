# Scadden Family Fitness Site — Build Handoff

A static multi-page website documenting two parallel 12–18 month fitness programs: one for Tanner (lean bulk → cut), one for Demi (recomposition). Built as a personal reference, not a public product.

## What you're building

A small static site with three pages sharing one visual identity:

```
/
├── index.html          # Landing page — links to both plans
├── tanner.html         # Tanner's 18-month bulk + cut plan
├── demi.html           # Demi's 12-month recomp plan
└── (assets as needed)
```

No build tools required. Vanilla HTML/CSS, fonts loaded from Google Fonts CDN, minimal JS for scroll-reveal animations only. Should work opened directly from the filesystem (`file://`) or hosted on any static server.

## Design system

A single editorial design system governs all three pages. See [`specs/design-system.md`](specs/design-system.md) for the full token set (colors, type scale, spacing, components). It must be applied consistently — these are companion pages, not standalone designs.

The aesthetic is **editorial monograph**: serif display type (Fraunces), warm paper-cream background, dark ink, gold accents, monospace data labels. Think gallery catalog or design journal, not fitness app.

A working reference implementation exists for Tanner's page (see [`reference/tanner-reference.html`](reference/tanner-reference.html)) — match its visual quality precisely. Demi's page uses the same system with content swapped. The landing page uses the same primitives in a simpler composition.

## Build order

1. **Read** [`specs/design-system.md`](specs/design-system.md) end to end before writing any code.
2. **Build** `tanner.html` from [`content/tanner.md`](content/tanner.md). Use [`reference/tanner-reference.html`](reference/tanner-reference.html) as the canonical implementation — match it closely.
3. **Build** `demi.html` from [`content/demi.md`](content/demi.md). Same structure and components, content swapped. Section numbering and order matches Tanner's.
4. **Build** `index.html` from [`content/index.md`](content/index.md). Simpler page — masthead, two large linked cards (one per person), shared footer.
5. **Verify** all three pages render correctly at desktop (1440px), tablet (820px), and mobile (380px) widths.

## Non-negotiables

- **Same visual system across all three pages.** Same fonts, colors, spacing, typographic patterns. No per-person color variants.
- **No frameworks.** No React, no Tailwind, no build step. Plain HTML + CSS + vanilla JS only.
- **Accessibility basics.** Semantic HTML (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`). Sufficient color contrast. Keyboard-navigable. Hover effects are decoration, not function.
- **No icons or emoji.** Typography and rules do all the visual work.
- **No stock photography.** No imagery at all. The design is pure typography and composition.

## File index

- `specs/design-system.md` — colors, fonts, spacing, components, responsive rules
- `specs/page-structure.md` — section order and HTML structure that all program pages share
- `content/index.md` — landing page content
- `content/tanner.md` — Tanner's full plan content
- `content/demi.md` — Demi's full plan content
- `reference/tanner-reference.html` — working implementation to match