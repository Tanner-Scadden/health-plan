# Design System

Single source of truth for how **health-goals-site** looks and how themes behave. Implementation lives in `index.html` (Tailwind + font hooks), `css/site.css` (semantic CSS variables per theme), and page markup.

## Stack

- **Tailwind CSS** via the [Play CDN](https://tailwindcss.com/docs/installation/play-cdn) — utilities in HTML; extend the theme in the `<script>` next to the CDN tag (`tailwind.config`).
- **Google Fonts** — Cormorant Garamond (display), Source Sans 3 (body); wired through Tailwind `fontFamily.display` and `fontFamily.sans`.
- **Themes** — `data-theme="demi" | "tanner"` on `<html>`. All color usage goes through **CSS custom properties** (see below), never one-off hex in components.

## Dual palettes (person themes)

| Theme | Mood | Palette |
| --- | --- | --- |
| **Demi** | Warm editorial, soft metallics | **Ivory** (base surfaces), **Champagne** (section wash / depth), **Rose Gold** (dividers, card edges, glow tints), **Mauve** (primary accent, emphasis) |
| **Tanner** | Crisp, energetic, minimal | **White** / cool paper (surfaces), **Electric Blue** (primary accent, focus, interactive ring) |

**Rules**

- Demi stays in the ivory–champagne family; rose gold carries borders and warmth; mauve is the solid CTA / strong accent (not neon).
- Tanner stays **light**: white and cool off-white elevations; electric blue is the only strong chroma — use it for links, buttons, and focus — keep body copy in deep blue-gray, not pure black.

## Semantic color tokens (CSS)

Tokens are defined in `css/site.css` on `:root` and overridden under `:root[data-theme="tanner"]`. Tailwind references them via `theme.extend.colors` in `index.html` (e.g. `bg-canvas`, `text-ink`, `bg-accent`).

| Token | Role |
| --- | --- |
| `--surface` | Page background |
| `--surface-elevated` | Cards, raised panels |
| `--surface-accent` | Alternating band / subtle wash |
| `--surface-badge` | Pills, segmented control fill |
| `--hero-glow-inner` / `--hero-glow-mid` | Hero radial gradient stops |
| `--text-strong` | Headings, primary text |
| `--text` | Body |
| `--text-soft` / `--text-muted` | Secondary / tertiary |
| `--accent-solid` / `--accent-solid-hover` | Primary button / link emphasis |
| `--accent-ring` | Button shadow / focus aura |
| `--border-soft` / `--border-strong` | Rules, strokes |
| `--card-border` / `--card-shadow` | Card chrome |
| `--bullet-bg` | Numbered steps, chips |
| `--header-surface` / `--footer-surface` | Sticky header / footer fills |
| `--selection-bg` / `--selection-text` | Text selection |

**Dark inverted bands** (e.g. future “targets” strip) should add a dedicated pair of tokens in `site.css` when built — do not overload Demi/Tanner base tokens.

## Typography

| Role | Font | Tailwind |
| --- | --- | --- |
| Display / headlines | Cormorant Garamond | `font-display` |
| UI / body | Source Sans 3 | `font-sans` (default on `<body>`) |

- Prefer `text-balance` on large headings where supported.
- Body copy: comfortable line height (`leading-relaxed` / `text-lg` on hero descriptions).
- Avoid more than two weights in a single block unless hierarchy demands it.

## Layout & Tailwind conventions

- **Width**: content column `max-w-5xl`, horizontal padding `px-6` (adjust with responsive variants as pages grow).
- **Vertical rhythm**: section spacing `py-20`–`py-28` with occasional `border-t` + `border-divider-soft`.
- **Radius**: cards and shells use `rounded-2xl`; pills use `rounded-full`.
- **Semantic utilities**: prefer extended theme colors (`bg-canvas`, `text-ink`, `border-divider-strong`) over repeating arbitrary `var(...)` in every class.

## Motion

- Defaults are fine: short `transition` on hovers (`transition`, `hover:border-accent`, `hover:bg-accent-hover`).
- No bouncy springs; keep easing subtle (`ease` or default).

## Responsive breakpoints

Use Tailwind defaults (`sm`, `md`, `lg`). Patterns in `index.html`:

- Stack grids: `grid` + `md:grid-cols-3`
- Typography scale: `text-4xl md:text-5xl lg:text-6xl` on hero

## References

- Landing scaffold: `index.html`
- Theme persistence: `localStorage` key `health-goals-theme` in inline `<script>`
- Page structure for future program pages: `specs/page-structure.md`
