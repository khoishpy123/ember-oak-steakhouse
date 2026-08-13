# Build Prompt — Ember & Oak (dark-luxury steakhouse landing page)

Paste this into Claude Code (or any AI coding tool) to regenerate this website.

---

Build a single-page "dark luxury" landing page for a fictional wood-fire
steakhouse called "Ember & Oak" on Capitol Hill, Seattle. Editorial,
high-end restaurant feel — the kind of site that looks like it cost $10k.
Output ONE self-contained index.html file (inline CSS + JS, no framework,
no build step, no external requests at runtime).

## Art direction
Mood: warm near-black, firelit, elegant, restrained. Lots of negative space.
The personality comes from typography + a live-fire atmosphere, not decoration.

## Design tokens
Colors:
  --char:    #14110E  (warm near-black background)
  --char-2:  #1B1712  (raised surface)
  --bone:    #ECE3D2  (primary cream text)
  --ash:     #948A79  (muted text)
  --ash-dim: #5F594E  (faint labels / rules)
  --ember:   #C46A3B  (copper accent — hovers, arrows, active states)
  --brass:   #C9A24B  (gold accent — used ONLY on the "&" and prices)
  --line:    rgba(236,227,210,.14) (hairline borders)

Type:
  Display + headings: "Cormorant Garamond" (serif) — light weight (300),
    UPPERCASE, wide letter-spacing (~.04–.06em), huge hero size
    (clamp(52px,12vw,168px)). Embed the woff2 as a base64 data URI so the
    font never fails to load; do NOT rely on a Google Fonts <link>.
  Tagline + prices: Cormorant Garamond ITALIC.
  Labels / nav / body UI: "Jost" (or a clean geometric sans fallback),
    UPPERCASE, letter-spacing ~.24–.42em, small sizes.

## Layout & sections (in order)
1. Fixed transparent header: wordmark "EMBER & OAK" (the "&" in brass),
   nav (Menu / Story / Visit) + an outlined "Reserve" button. On scroll >40px
   the header gains a blurred dark background and a bottom hairline.
2. Full-screen hero (100svh), centered:
   - eyebrow with flanking rules: "EST. 2026 · CAPITOL HILL"
   - giant two-line display: "EMBER" / "& OAK" (brass italic ampersand,
     with a soft glow behind it)
   - italic tagline: "Wood-fire steakhouse. Cooked over live oak."
   - two CTAs: a solid-outline "Reserve a table →" and a ghost/underline
     "View the menu →"; arrows slide right and turn ember on hover
   - a bottom "Scroll" cue with a thin bar and an ember drop animation
3. "The Cuts" — a 3-column hairline grid of signature steaks
   (Bone-In Ribeye $68, Coal Porterhouse $96, Smoked Short Rib $44), each
   with a number, name, sensory description, brass italic price, and weight.
4. "Reservations" band, centered: big serif headline "PULL UP TO THE FIRE",
   a short paragraph, and CTAs (Book a table / address).
5. Footer: wordmark, "Capitol Hill · Seattle", "Open Tue–Sun · 5pm–late".

## Atmosphere (CSS only — no images, must never break)
- Two large blurred radial "ember glow" blobs (ember + deep red) that
  slowly flicker via keyframes, screen blend mode.
- A field of ~26 small ember particles drifting upward with random size,
  speed, delay and slight horizontal drift.
- A faint SVG fractal-noise grain overlay + a radial vignette.

## Motion
- Page-load: hero elements fade + rise in a staggered sequence.
- Scroll: sections reveal (fade + translateY) via IntersectionObserver.
- IMPORTANT: content must be visible by DEFAULT. Only hide-then-reveal when
  JS is active (e.g. add a `.js` class to <body> from script, and gate the
  hidden state behind `body.js .reveal`). Never leave content stuck at
  opacity:0 if JS doesn't run.
- Hover micro-interactions on nav links (ember underline) and buttons.

## Quality bar
- Fully responsive; collapse the nav links and the cuts grid to 1 column on
  mobile.
- Respect `prefers-reduced-motion: reduce` (disable animations).
- Visible keyboard focus states; semantic HTML; valid, well-formed markup.
- Use clamp() for fluid type and spacing. Warm-biased neutrals, not pure grey.
- Write real, evocative copy — no lorem ipsum.

Deliver the complete index.html, ready to open in a browser and to host as a
static file on GitHub Pages / Netlify / Vercel.

---

## How to reskin for a different brand
Swap these and keep the structure:
- Brand name, tagline, city/neighborhood, and the "Est." year.
- The two accent colors (`--ember`, `--brass`) to match the new brand;
  keep one warm background + one bright accent + one metallic.
- The section-3 items (name / description / price / weight).
- Optional: change the display serif for a different personality, but keep
  it embedded as a data URI.
