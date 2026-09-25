# OrynLab logo assets

Drop the real logo files here. Anything using this skill will look in this
folder, so a file placed here becomes available to every deck, document, and
page built from the brand.

## What to put here

| Filename | What it is | Why it matters |
|---|---|---|
| `orynlab-lockup.svg` | Full lockup: three dots + `OrynLab` wordmark | The one to use most of the time |
| `orynlab-lockup-light.svg` | Same, recoloured for dark backgrounds | Inverting a dark SVG by hand goes wrong |
| `orynlab-wordmark.svg` | Wordmark only, no dots | Tight horizontal spaces |
| `orynlab-mark.svg` | Three dots only | Favicons, avatars, watermarks |

**SVG is strongly preferred.** It scales to a billboard or a 16px favicon from
one file, the two-tone split stays editable, and it stays sharp in print. A PNG
at 2000px wide is a workable fallback; a screenshot or a JPEG is not — JPEG
compression fringes the edges of flat black on white.

If the wordmark was set in a licensed typeface, export it with **outlines
converted to paths** so it renders without the font installed.

## Already here

`mark-dots.svg` — the three-dot motif, rebuilt from the brand geometry. Pure
shapes, no type, so it is safe to use anywhere. Replace it if the official file
differs.

## The typeface

The wordmark reads as a geometric sans — circular `O`, single-storey `a`,
straight-tailed `y`. This skill specifies **Poppins** as the closest free match.

If the logo was actually set in something else (Gilroy, Product Sans, Futura,
Century Gothic, a custom face), say so and the type section becomes one line's
change. Naming the real face is the single most useful correction you can make
to this skill.
