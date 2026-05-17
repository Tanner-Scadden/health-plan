# Page Structure

Both program pages (`tanner.html` and `demi.html`) follow the same section sequence and HTML structure. Only content differs.

## Shared section sequence

```
1. <header>          Sticky masthead + nav
2. <section.hero>    Display headline + meta data table
3. <section.targets-band>     The four key numbers (dark inverted)
4. <section #timeline>        Phase timeline with milestones
5. <section #operations>      Daily operations (3-card grid)
6. <section #training>        Training split (card grid)
7. <section #rules>           Adjustment triggers (dark inverted)
8. <section.closing>          Pull quote + signature
9. <footer>                   3-column mono row
```

The reference implementation (`reference/tanner-reference.html`) has the complete working HTML for every section. Build Demi's page by copying the structure and swapping content.

## Section ID and class conventions

| Section | ID | Notes |
|---|---|---|
| Hero | — | `<section class="hero">` |
| Targets | `targets` | `<section class="targets-band">` (dark) |
| Timeline | `timeline` | `<section class="section">` |
| Operations | `operations` | `<section class="section ops-section">` (warm bg) |
| Training | `training` | `<section class="section">` |
| Rules | `rules` | `<section class="section rules-section">` (dark) |
| Closing | — | `<section class="closing">` |

Nav links target these IDs. Keep them identical across both pages so internal nav behaves consistently.

## Section numbering

Each section head has a mono "§ N · CATEGORY" label on the right:

| Section | Label |
|---|---|
| Targets | (no label — uses eyebrow instead) |
| Timeline | `§ I · CHECKPOINTS` |
| Operations | `§ II · [PHASE]` |
| Training | `§ III · [N] DAYS / WEEK` |
| Rules | `§ IV · ADJUSTMENT TRIGGERS` |

For each page, fill in the phase name and frequency:
- Tanner: `§ II · BULK PHASE` and `§ III · 4 DAYS / WEEK`
- Demi: `§ II · RECOMP PHASE` and `§ III · 5 DAYS / WEEK`

## Per-page customization

**Header issue label:** small mono detail in the top left of every page.
- Tanner: `№ 01 · TS · MAY 2026`
- Demi: `№ 02 · DS · MAY 2026`

**Hero subject mark** (vertical mono text, top right of hero):
- Tanner: `SUBJECT · TS · 28Y · 73IN · 201.7LB`
- Demi: `SUBJECT · DS · 32Y · 61IN · 131LB`

**Closing signature:**
- Tanner: `Program authored · May 17, 2026 · Calistoga`
- Demi: same

**Footer center label:**
- Tanner: `Vol. I · 2026—2027`
- Demi: `Vol. II · 2026—2027`

## Landing page (index.html)

Simpler structure — only three sections:

```
1. <header>          Same masthead, no nav (or nav points to the two plan pages)
2. <section.hero>    "The Scadden Programs" headline + brief intro
3. <section>         Two large cards, one per person, each linking to their page
4. <footer>          Same mono row
```

Each person card on the landing page contains:
- Their name (Fraunces with italic gold accent)
- A one-line program description
- Three key target numbers in mono
- "Read the program →" link

Cards should be larger and more dramatic than the smaller card patterns inside program pages — they're the entire purpose of the landing page. Use the day-card hover pattern (lift + gold border) at a larger scale.