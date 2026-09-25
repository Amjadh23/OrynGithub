---
name: orynlab-brand
description: OrynLab's brand system — monochrome palette, geometric type, the three-dot mark, and the curve-and-chevron shape language. Use when producing anything that carries the OrynLab name: slide decks, documents, reports, web pages, social graphics, posters, business cards, diagrams, email signatures, or README headers. Also use when asked to "match the OrynLab brand", "use our branding", or to check whether an existing design is on-brand.
---

# OrynLab brand system

Monochrome, geometric, high-contrast. Black and white do the work; grey carries
the secondary voice. **There is no accent colour** — if a design needs emphasis,
it comes from weight, scale, or space, never from hue.

## Palette

The whole system is five values. Use them as CSS custom properties from
`references/tokens.css`, or the raw hex below.

| Token | Hex | Where it goes |
|---|---|---|
| `--oryn-black` | `#000000` | Large shapes, headline text on light, the curve |
| `--oryn-ink` | `#101A28` | The "Oryn" half of the wordmark; body text on light |
| `--oryn-slate` | `#5C6672` | The "Lab" half; secondary text, captions, the light dot |
| `--oryn-steel` | `#3A4450` | Mid-tone fills, chevrons, icon circles |
| `--oryn-mist` | `#F2F4F7` | Section backgrounds, the faint chevron pattern |
| `--oryn-paper` | `#FFFFFF` | Primary background |

Rules:

- **Never introduce a colour.** No blue, no gold, no status colours. A chart with
  five series uses five greys between `--oryn-ink` and `--oryn-slate`, separated
  by fill pattern or weight if they must be told apart.
- Body text is `--oryn-ink` on `--oryn-paper`, or `--oryn-paper` on
  `--oryn-black`. Both clear AA comfortably.
- `--oryn-slate` on white is ~4.9:1 — fine for body, but do **not** drop it below
  14px or use it for anything that must be read quickly.
- Dark surfaces are `--oryn-black`, not a softened charcoal. The contrast is the
  brand.

## Typography

Geometric sans throughout. **Poppins** is the working face — circular `O`,
single-storey `a`, straight-tailed `y`, which is what the wordmark shows.

| Role | Family | Weight | Size | Tracking | Case |
|---|---|---|---|---|---|
| Display / name | Poppins | 800 | 48–72px | `0.08em` | UPPERCASE |
| Section heading | Poppins | 700 | 24–32px | `0.06em` | UPPERCASE |
| Subtitle / role | Poppins | 700 | 14–16px | `0.14em` | UPPERCASE |
| Body | Poppins | 400 | 16–18px | `0` | Sentence case |
| Caption / meta | Poppins | 500 | 11–13px | `0.10em` | UPPERCASE |

- **Wide tracking on caps is the signature.** Every uppercase run gets letter-spacing;
  uppercase with default tracking looks wrong in this system.
- Body copy never gets extra tracking, and never goes uppercase.
- Line height: `1.15` for display, `1.6` for body.
- Fallback stack: `Poppins, "Montserrat", "Century Gothic", system-ui, sans-serif`.
  Montserrat is the closest substitute where Poppins is unavailable.

## The mark

Three dots ascending left-to-right, growing as they rise — a diagonal roughly
30°. Smallest and darkest at lower-left, largest and lightest at upper-right.

- Lower dot: `--oryn-ink`, smallest
- Middle dot: `--oryn-ink`, ~1.6× the lower
- Upper dot: `--oryn-slate`, ~1.3× the middle

The wordmark sets **Oryn** in `--oryn-ink` and **Lab** in `--oryn-slate`, one
word, no space, capital O and capital L. Written as plain text it is `OrynLab`.

- Never `Oryn Lab`, `ORYNLAB`, or `orynlab` in branded material.
- The dots sit above and right of the wordmark, never inline with it.
- Minimum clear space around the lockup: the height of the capital `O` on all sides.

See `assets/` for the logo files and what is currently available there.

## Shape language

Two families, used together and never mixed into each other:

**Organic** — one large, soft, off-centre curve bleeding off an edge, filled
`--oryn-black` or a grey gradient. One per layout. It anchors a corner; it never
sits in the middle or gets mirrored into a symmetric frame.

**Geometric** — chevrons and rotated squares, always at 45°, in `--oryn-mist` as
near-invisible texture or `--oryn-steel` as a small solid cluster. They cluster
in a corner opposite the curve.

Icons sit in solid filled circles (`--oryn-black` or `--oryn-steel`) with the
glyph knocked out in white.

Rules and dividers may use a short hatched segment — angled parallel strokes —
as a full stop under a heading. Keep it under ~25% of the heading's width.

## Layout

- Generous white space. Aim for at least 40% of any composition unoccupied.
- Content sits on one side; the curve occupies the other. Asymmetry is the point.
- Align to a left edge and keep it; centred layouts are off-brand except for the
  standalone logo lockup.

## Checking a design

A layout is on-brand when all of these are true:

1. No hue anywhere — every pixel is black, white, or a neutral grey.
2. Every uppercase run has visible letter-spacing.
3. Exactly one organic curve, bleeding off an edge, off-centre.
4. The wordmark reads `OrynLab` with the two-tone split.
5. Body copy is sentence case, untracked, at least 16px.

## Note: this differs from the oryn-labs-website

The marketing site (`oryn-labs-website`) runs a **different, older system** —
Space Grotesk / Newsreader / JetBrains Mono, a blue accent (`#2E47B0`), a gold
(`#E5C58E`), and a lowercase `oryn labs` wordmark.

This skill describes the newer monochrome `OrynLab` identity from the logo and
business cards. **They are not compatible.** When working on the website, follow
the site's existing tokens in `app/globals.css`. When producing standalone
material — decks, cards, documents, social — follow this skill. Do not mix them,
and flag the conflict if someone asks for both at once.
