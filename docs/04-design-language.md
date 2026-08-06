# Design language

The visual system, as it actually exists in the code today — not the original brief. It went through several rounds: an initial light/dark editorial theme, a full conversion to an all-dark theme, a full palette swap to dark-blue/sky-blue, and a later single-accent-colour unification pass. This describes where it landed.

## Colour

Defined once, in the `tailwind.config` block at the top of `index.html` — six tokens, nothing else used anywhere on the page:

| Token | Hex | Used for |
|---|---|---|
| `ink` | `#0A1930` | Page background, dark section fills, footer |
| `paper` | `#F3F7FC` | Foreground text on dark backgrounds, a couple of inverted light buttons |
| `teal` | `#1E69D2` | **The single accent colour.** Every blue highlight, stat, icon, border, and filled button on the page |
| `tealdeep` | `#0B3D75` | The darker half of the crisis-section split panel |
| `mist` | `#122A4D` | Elevated card surfaces sitting on top of the `ink` background (team grid, some tiles) |
| `cyan` | `#1E69D2` | Reserved, by explicit direction, for exactly one element: the "TRL 9" badge |
| `stone` | `#A9B9D6` | Muted/secondary text on dark backgrounds |

The colour work went through a real audit loop, not just eyeballing: a low-effort review pass (against screenshots, blind to any code context) checked whether the single-accent-colour goal actually landed pixel-for-pixel against its source — the crisis section's right-hand panel background — and caught two real misses that got fixed: a gradient panel that only *looked* like the right colour at one edge, and a hero stat number sized so large it read as a different visual weight than the rest of the accent usage.

**Rule going forward:** if a new blue is needed anywhere, it should be the `teal` token, not a new hex value. Every time a one-off blue hex crept into the file during earlier iterations, it later had to be found and unified — grep the file for `#[0-9A-Fa-f]{6}` occasionally to catch drift.

## Type

- **Display font:** Fraunces (serif) — headlines, big numbers, pull-quotes. Loaded from Google Fonts.
- **Body font:** Inter (sans) — everything else, including the small uppercase "eyebrow" labels (`.lab` class — 13px, bold, wide letter-spacing, uppercase).
- No third typeface anywhere.

## Spacing rhythm

Section vertical padding is standardized through one shared class, `.sec` (`padding-block: clamp(84px, 11vw, 144px)`), applied to every full section on the page. Two sections (the crisis split-panel and the demo+partners split-panel) originally used bespoke padding values instead of `.sec` and were brought in line with it during the design-review pass, so scroll rhythm stays consistent top to bottom.

## Dark theme

The entire page is dark — there is no light-mode section anywhere (an earlier version alternated light and dark sections; that was fully converted). Card surfaces use `mist` (#122A4D) to read as "raised" against the `ink` page background; hover states on interactive-feeling cards (team grid, comparison rows) lighten slightly toward `#0F3D6E`. A subtle repeating-dot `.grain` texture is applied to a few sections for texture without adding a second colour.

## Motion

- Scroll-reveal: elements with `.rv` fade up and in via `IntersectionObserver`, staggered with `.rv-d1` through `.rv-d4` delay classes.
- Hero headline lines mask-wipe in via `.lmask`.
- Stat numbers count up from 0 on scroll into view.
- A thin progress bar at the very top of the page fills as you scroll.
- Everything respects `prefers-reduced-motion` — all of the above is disabled outright for users who've asked for reduced motion at the OS level.
