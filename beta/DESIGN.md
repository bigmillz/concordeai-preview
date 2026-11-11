# ConcordeAI 7.0 — Balance and Sting, the quiet version

The tokens behind `beta/index.html`, written so the app can take the same values exactly.
Balanced is the default effects level; Full is opt-in; Calm is the stillest. Everything
below is design, not effect: it applies in every level.

## Type

The wordmark (Michroma, which has one weight), PINNED: CONCORDE with a hairline of fake bold
`-webkit-text-stroke: .02em currentColor` and `letter-spacing: .18em`; "AI" at `.865em` with
`-webkit-text-stroke: .14em currentColor` (clearly bolder than CONCORDE); the wing's lines `stroke-width: 1.3`.
10.25 px in the header, `clamp(25px, 3.25vw, 42px)` in the opening.


Three families, no others: **Space Grotesk** (UI and reading), **IBM Plex Mono** (digits
and labels), **Michroma** (the wordmark, with the wing).

| Token | Size / leading | Weight, tracking | Used for |
|---|---|---|---|
| `--t-display` | `clamp(44px, 6.2vw, 96px)` / 1.0 | 500, −0.03em | the greeting (89 px at 1440, 96 at 1600+, 44–56 under 600) |
| `--t-h2` | 22 / 1.3 | 500, −0.012em | headings in answers, margin 32 above 12 below |
| `--t-h3` | 17 / 1.4 | 600 | subheadings, margin 24 above 8 below |
| `--t-read` | 17 / 1.65 | 400, +0.002em | answers, the question, the composer |
| `--t-ui` | 14 / 1.5 | 400 (500 when selected) | nav, rows, chips, bylines |
| `--t-small` | 13 / 1.5 | 400 | descriptions, suggestion pills, Details, code blocks |
| `--t-label` | 12 | mono, 400 | stats, numbers, the effort level, captions, footer |
| `--t-micro` | 11 | mono, 500, +0.12em, caps | table heads, sidebar day labels |

- Reading column: 640 px (about 70 characters at 17 px). Paragraphs 16 px apart.
- Lists: 24 px indent, 6 px between items; ordered lists numbered in mono 12, right-aligned
  in a 20 px gutter. Block quotes: 1 px hairline left, 20 px inset, `--ink2`.
- Inline code: mono at 0.88em, `rgba(255,255,255,.06)` fill, hairline, radius 4.
  Code blocks: mono 13 / 1.6, `rgba(4,7,18,.55)` fill, hairline, radius 8, 14×16 padding.
- Tables: 15 px, hairline top and bottom, `--hair` between rows, heads in `--t-micro`;
  numbers in mono 13 with `tabular-nums`, right-aligned (`.num`).
- Labels in caps track +0.12em (`--track-label`). Nothing else is tracked.
- Space Grotesk at 500 with −0.03em is the display voice; 600 in Full's greeting. The greeting is one text node in
  one box in every mode, crisp `#f8faff`. Its light, two layers, both zero offset and from that one node (never a copy):
  a close glow on the letters, `text-shadow: 0 0 20px rgba(255,246,232,a), 0 0 36px rgba(255,240,222,.55a)` with
  a = .30 (Balanced) / .38 (Full); and the wide bloom behind the block (the afterglow), now resting at .66 / .78 (was
  .50 / .62), its warm white touched by the hour's light (22 % of the palette's light colour in a second radial). Both
  rise with the afterglow over 2 s and are then still. Calm and reduced motion: none.

## Colour

PINNED: **Silver and one hue** (per the owner: "get the rainbow effect right ... we have too much rainbow"; ChatGPT
and Claude stay monochrome and think in a grey-to-white sweep, Gemini keeps its blue-violet for its signature moment).
The interface is silver and white. Colour appears in exactly two places: Ultra, in one cool pair, ice `#8fb7ff` →
soft violet `#a58bff` (white highlights, the faintest violet at most in its stars); and the ember `#e8415a` at
decisions only (the send strike and the send key with text, the keyboard focus ring, errors). No rose, pink, red, gold,
green or rainbow gradient anywhere in the interface or its effects. The footage's hour grade (below) is the one
exception: a light tint on real footage. The machine dies keep their makers' colours.

| Token | Value | Contrast on `--night` | Role |
|---|---|---|---|
| `--night` | `#030305` | | the ground: black (per the owner, "over black instead of blue"); near-black so it never bands |
| `--indigo` | `#0a0a0c` | | the stage gradient's middle (a neutral near-black; the name is kept for the app) |
| `--ink` | `#f4f5fa` | 18.9 | primary type |
| `--read` | `#e8ebf5` | 17.3 | answer prose |
| `--ink2` | `#c6cde0` | 13.0 | secondary type, placeholders |
| `--ink3` | `#9aa6c6` | 8.5 | tertiary type, labels (6.7 on the lightest glass) |
| `--ember` | `#e8415a` | 5.2 (black on ember 5.2) | the one accent: send strike, send key with text, keyboard focus ring, errors |
| `--ice` | `#9fc0ff` | | light only (the die for Cloud, the writing star's warmth) |
| `--rose` | `#dfe6f2` | | retired as a hue: now a silver (the name is kept for the app) |
| `--champagne` | `#e6e8ee` | | silver (the name is kept for the app); hairlines keep their faint warm grey |

Small labels straight over the sky (the sidebar's day labels, the footer's credit and links) wear a tight halo in the
near-black, `--halo-dark: ±1px 0 1px and 0 ±1px 1px at rgba(3,3,5,.7), 1px 1px 2px and −1px −1px 2px at .5,
0 0 4px at .75, 0 0 9px at .45` (a blur alone barely reaches past a 1 px stroke; the offsets give it body), so a bright
star or the noon sky behind cannot take them under 4.5:1 within 2 px of the ink. Invisible on the black; `--ink3`
itself and the sky are unchanged. Two places also get a soft local backing, since the noon sky and the brightest
footage sit right behind them: the suggestion pills (`rgba(3,3,5,.22)` fill plus the halo) and the footer's credit
(a `rgba(3,3,5,.34)` block, `blur(10px)`, 8 px above and below and 14 px either side of the text, under the credit only).

Hairlines are champagne silver, never pure white:

| Token | Value | Role |
|---|---|---|
| `--hair` | `rgba(241,230,206,.09)` | the faintest rule (table rows, folded panel) |
| `--hair2` | `rgba(241,230,206,.15)` | borders of controls, panels, chips |
| `--line` | `rgba(243,235,216,.32)` | the beam, the send key's outline, a focused composer |
| `--spec` | `rgba(255,250,240,.12)` | the 1 px specular along the top of every glass |

The horizon: a flat band low in the sky, `linear-gradient(180deg, transparent 52%,
silver `rgba(220,224,234,.1)` at 86%, `rgba(232,234,240,.15)` at 100%)` (was rose and champagne), screen-blended, opacity .24 on the home (was .62: over black it read as a coloured base), .12 in a
chat and in Calm. Flat on purpose: no dome, no arc, no limb anywhere (the NASA clips are
cropped to their horizon-free band; the moonlight is an edgeless corner glow).

## Glass

One material everywhere (composer, sidebar, menus, popovers, tooltips):

```
background: linear-gradient(180deg, rgba(255,255,255,.065), rgba(255,255,255,.03))   /* --glass */
            (menus and popovers add rgba(8,8,10,.78) beneath: --glass-dense; every dark tint is neutral black, never navy)
backdrop-filter: blur(24px) saturate(140%)                                           /* --blur */
border: 1px solid var(--hair2)
box-shadow: inset 0 1px 0 var(--spec), var(--shadow)
```

Shadows, two depths, both soft and long:

```
--shadow:       0 1px 2px rgba(0,0,0,.18), 0 12px 32px -8px rgba(0,0,0,.34), 0 40px 96px -32px rgba(0,0,0,.55)
--shadow-float: 0 1px 2px rgba(0,0,0,.22), 0 16px 40px -8px rgba(0,0,0,.42), 0 48px 120px -32px rgba(0,0,0,.6)
```

## Shape

| Token | Value | Used for |
|---|---|---|
| `--r-panel` | 14 | the composer, the sidebar |
| 12 | 12 | the mode menu |
| `--r-ctl` | 8 | every control: keys, chips, rows, pills, code blocks |
| `--r-chip` | 6 | small chips inside controls (models, sources, Effects buttons) |
| `--r-tag` | 4 | tags and badges (beta, Demo, citations, inline code) |

Strokes: 1 px hairlines, 1.5 px icon strokes, 1.5 px rim. The chosen mode in the mode menu wears a 5 px white
diamond; the effort slider's knob is a round orb (see The effort slider).

## Spacing

An 8 px grid: 8 / 16 / 24 / 32 / 40 / 64. Header 64. Controls 36 (32 under 600). Rows 32.
Pills 32. Hit areas at least 32 (an invisible extension where the drawn control is smaller). Sidebar 248 wide, 8 px padding, 16 from the edge, 72 from the top, 16 above the
credit. Home column 800; chat column 640 (Full, 1200 px and up: 900, the 640 column, 40 and the 220 margin notes, centred in the room). The composer's centre sits at the golden point
(61.8 %) of the free height below the header.

## Motion

One family. `--out: cubic-bezier(.16,1,.3,1)` for anything that arrives or settles;
`--inout: cubic-bezier(.65,0,.35,1)` for anything that leaves. Durations
`--t1: 120ms` (hover, press, the diamond's snap), `--t2: 200ms` (menus, popovers, colour),
`--t3: 320ms` (the mode menu's rise, the ember strike). Big cinematic fades (the home,
the composer's arrival) keep their own seconds but use the same curve. No bounce anywhere.

States: hover brightens the border to `--line` and the fill to `rgba(255,255,255,.06)`
(Balanced also lifts 1 px with a soft shadow); press scales to .97 in 120 ms; selected is
`rgba(255,255,255,.09)` with `--ink` type; the chosen mode wears a small white diamond.
Keyboard focus is a 1 px ember hairline; on the slider it is a ring round the pill (2 px off it)
and shows only for keyboard focus: after an arrow, Home, End, Page or Tab key, with `:focus-visible`; any pointer press
clears it, so a click or a drag never leaves it behind (WKWebView can report a clicked range as focus-visible).

### The opening
The star field turns about a point above the wordmark: 10° in Balanced, 16° in Full, 0 in
Calm and reduced motion; 4 s on a smootherstep (zero velocity at both ends); the stars
lengthen briefly along their arcs at the fastest moment (2 s in).

### The writing star
- Writing: a 4 px white point with a 14 px four-point glint rides 5 px after the newest word;
  it follows with a 120 ms `--out` transition. Words appear behind it with a 160 ms fade and
  a 2 px rise (`.wf`), one per 40 ms (30 at Extra and Ultra). No blur, no glow, no comets.
- Draft → polish: the star runs down the answer's left edge (14 px outside it) in 350 ms,
  `cubic-bezier(.3,0,.2,1)`, while the text crossfades (170 ms out, 280 ms in). It then
  glides to the end of the polished text in 260 ms (or to the column's foot if that is out
  of view).
- Landing: the star lifts to the byline's dot in 400 ms `--out` and becomes it (the dot
  reads 1.0 for 700 ms, then rests at .7). Then sources (+0), Details (+120 ms) and the
  fine print (+240 ms) fade in over 400 ms each.
- Calm: words in one plain 350 ms fade, no star. Reduced motion: no motion.

### The greeting: traced, then the afterglow
- Every visit, Balanced and Full: after the wordmark and the twist (Balanced: at 3.9 s, waiting out the twist by at
  most 0.9 s more; Full: at 7.5 s) the greeting is traced in light once (the night page's tracer: margin 56, speed 620,
  spread .9). The trace ends with a cut: the crisp text appears and the trace canvas is removed in the same frame, so
  two copies are never on screen. A trace in flight is dropped at once (no fade) if the text changes, the window
  resizes, the sidebar moves or the greeting's box moves or changes size by more than 0.5 px.
- The afterglow is light, not text: a radial gradient behind the word block (`::before`, 22 % wider than the text
  each side, 72 % taller above and below), warm white `rgba(255,244,228,.30)` at the centre falling through
  `.24 / .15 / .07 / .02` to 0. It rises over 2 s on `--out` (0 → 1 at 20 %, scale .9 → 1) and rests at `.5`
  (Balanced) or `.62` (Full), then is still: no breathing, no loop. With the text hidden it shows no letterforms.
- Calm and reduced motion: the plain greeting, no trace, no afterglow.

### The effort slider
A slim, squared-off track, a segmented control in Gemini's luminous language (one `<input type=range>` on top for the hit area).

| Part | Value |
|---|---|
| Size | PINNED ("a little slimmer and more squared off", superseding the 20 px pill): 220 × 36 (hit), track `--ph: 16px`, radius `--sr: 4.5px`; in a conversation 200 wide, `--ph: 12px`, `--sr: 4px`; under 600 px 88 × 32, `--ph: 16px`, `--sr: 4.5px`; the hit area stays 36 (32 on a phone) whatever the track, the composer's row on one line with the phone's 6 px gaps (the pill may give up to 8 px rather than wrap). The level sits beside it |
| Channel | `linear-gradient(180deg, rgba(255,255,255,.05), rgba(255,255,255,.085))`, inset 1 px `rgba(255,255,255,.08)`, inset `0 1px 2px rgba(0,0,0,.25)` |
| Fill | PINNED silver from the left to round the knob: `linear-gradient(180deg, rgba(255,255,255,top), rgba(255,255,255,bottom))`, top / bottom .86 / .58 at Low, .88 / .60, .90 / .61, .92 / .62 at Extra (the steps differ only in length and that slight brightening); at Ultra `linear-gradient(90deg, #8fb7ff, #a58bff)`, flowing (below); 1 px inner top light |
| Bloom | a copy of the fill beneath it, `blur(8px)`: a faint white bloom, opacity `.18 / .21 / .24 / .27`, and `.42` in the pair at Ultra |
| Notches | PINNED (per the owner: "very slim and very fluid, not just a bunch of dots"): none at rest. Only while the slider is hovered, dragged or keyboard-focused, five faint 2.5 px squares (radius .5 px) fade in on the centre line in 200 ms `--out`: `rgba(255,255,255,.18)`, passed ones `.5`, no glow |
| Knob | a rounded square, `--ob: 14px`, radius `--kr: 4px` (11 and 3.5 in a conversation, 14 and 4 on a phone), near-white `radial-gradient(110% 90% at 50% 25%, #fff, #f4f7ff 45%, #dde5fa)`, 1 px `rgba(255,255,255,.95)` edge, shadow `0 1px 2px rgba(4,8,30,.45), 0 2px 6px rgba(4,8,30,.35)`; hover 1.05, held 1.10 |
| Halo | the knob's shape: a rounded square 1.5 × the knob (radius 1.6 × `--kr`), `#e9edf5` (silver at every step), `blur(6px)`, opacity .45 at scale .85; hover .70 / 1.05; held .85 / 1.22; 300 ms `--out`; at Ultra a slow conic of `#8fb7ff`, `#a58bff`, `#dce8ff`, blurred the same |
| Drag | the knob and the fill follow the pointer continuously (no transition while held: position = (pointer x − left − track/2) ÷ (width − track), clamped 0–1); the level name and everything tied to the level change as it crosses each stop (the nearest stop) |
| Snap | on release, and for every key step: 140 ms `cubic-bezier(.22,1,.36,1)` to the stop, no bounce (knob, fill and bloom together) |
| Level | beside it, Space Grotesk 13/500 `--ink2`, PINNED 12 px off the track (10 on a phone: the row's gap plus 4), so the knob's glow at the track's end has room and never touches the word; updating live: Low · Medium · High · Extra · Ultra. No tooltip and no explanations of the levels anywhere (per the owner: "pretty damn obvious") |

Click anywhere to jump, arrows step. Calm and reduced motion: the same look, no transitions.

### Ultra's light: one cool pair
Ice `#8fb7ff` → soft violet `#a58bff`, with white highlights. Nothing warmer, ever.

- **The label and the byline:** "Ultra" is silver text (`#c6cad4`), not gradient text, with the "thinking" shimmer: a
  white highlight band (`rgba(255,255,255,.98)`, 20 % of a 250 % background) passes over it every 3 s (across in about
  1.3 s on `cubic-bezier(.45,0,.25,1)`, then rest; now every 2.5 s, in step with the fill's marquee); no glow. The byline reads
  "Concorde Thinking · Ultra"; its sweep stops when the answer lands (still silver).
  Under the composer's label, a feathered black pill holds it at AA at the sky's brightest (Full at 1280 and on a phone
  dipped to 3.5:1, and 2.9:1 under the noon sky): the slider's first layer, 80 × 34 centred on the word (its left edge
  at the track's end + the label gap − 24 px), `radial-gradient(closest-side, rgba(3,3,5,.62), .56 35%, .30 62%,
  .10 82%, transparent)`, in with Ultra (600 ms), out with it (900 ms) and while dictating. It sits under the
  slider's fill, bloom and knob and under the word, so nothing of the show is dimmed; feathered wide so it reads as
  shade, not a shape.
- **The typed words:** a mirror over the textarea carries the same shimmer on near-white silver (`#eceef3`), a subtler
  sweep every 3.6 s; "Ask anything" at .85 (AA in Full). Leaving Ultra crossfades back to white in 600 ms.
- **The send key** at Ultra: unchanged (see "No flashes, no shine on controls"): no gradient, no sheen, no outline colour.
- **The writing star:** a 20 px tail behind it, soft violet (fading) → ice → `#eef3ff` at the star.
- **The stars (every burst, the chandelier, the motes, the constellation, shooting stars, rain):** white and ice, the
  faintest violet at most: `#ffffff`, `#eef3ff`, `#dce8ff`, `#c6d8ff`, `#e6efff`, `#d9d4ff`. No gold.

### The Ultra moment
Arriving (about 1.5 s), Balanced and Full:
- **The beat** (under 1.2 s): 0 ms the orb clicks into place (scale 1 → 1.12 → 1, 220 ms) as the first star wave and
  the sweep leave; +200 ms the second star wave and the sky's glint flash; +400 ms the lit glass edge comes up (the
  line of light runs round in 600 ms); +600 ms the ULTRA label's light sweep and the fill's marquee start together.
- **The knob at Ultra:** PINNED (per the owner: "one star that sits there spinning just looks tacky"; the star knob is
  removed): the same rounded-square near-white knob as every level, with a soft, still ice halo of about 5 px
  (`box-shadow: 0 0 5px 1px rgba(143,183,255,.42)` on the knob, its square halo at `blur(4px)`, .35, scale .85). No star
  shape, no morph, no spin, no breathing. On arrival it flashes once within about 6 px (white 4 px, ice 6 px, 900 ms)
  and settles to that halo. The fill runs to the knob as at every level, in the ice → violet pair. PINNED (per the owner: "special, not over the top", like
  ultrathink): over the fill at Ultra only, a dot-matrix texture: 1 px square dots on a 4 px pitch, white at .16
  (matching the field above the box); and a slow LED-marquee shimmer: a soft band (20 % of a 250 % mask, the dots at .9
  inside it) lights the dots left to right every 2.5 s (across in about 1.1 s on `cubic-bezier(.45,0,.25,1)`, then
  rest), starting 600 ms after arrival, in step with the word Ultra's silver sweep. No stars in the track; no travelling
  glint (superseded). Below Ultra: plain silver, none of this. Calm and reduced motion: the dots, still. The label
  keeps the silver shimmer. Calm and reduced motion: the same knob, no drift.
- **A star trail and a stream:** as the knob slides to Ultra, 18 tiny stars light along the track behind it (over its
  140 ms snap, each 380–500 ms); as it lands, 12 stars stream up out of it (28 ms apart, 640–860 ms).
- **The stars lead.** Three waves of four-point stars burst from where the knob lands (120 in all), drawn on the GPU
  (a canvas above the glass, pooled quads, no DOM): 0 ms, 60 (6 hero stars, 9–12 px half-arms, white; the rest
  3–6.4 px), flying 26–74 px; +200 ms, 36 smaller (2.2–4.8 px), 16–46 px; +400 ms, 24 more of those. White, ice-blue
  (white and ice, the faintest violet: the list above). Each twinkles twice as it flies and fades
  (opacity 0 → 1 → .45 → .95 → .35 → 0 at 0 / 15 / 35 / 55 / 78 / 100 %, scale .4 → 1 → .8 → 1 → .7 → .3, ease
  with drag: out fast and slowing (1 − e^(−kt), k 4.5–7 /s), then floating like dust in light (a 2–3 px bob, a slow
  rise), dissolving at 2–4 s, staggered; on the home 40 % drift to the chandelier on the knob's side (x over .45 s, y
  over 1.1 s) and settle near a hanging star (3.2–4.5 s). Nothing leaves the screen.
  They fly only into open sky, never over text: on the home up through the composer's top edge into the space above
  the box (a ±49° cone; each flies the distance to that edge plus 6–86 px, so they hang above the glass, not in it);
  in a conversation low and to the sides (not up over the answer).
- **The chandelier (per the owner: "hang them like something"):** 8–22 hairline threads lower from the top edge as Ultra
  arrives, only where no text or control sits under the thread (each ends 22 px above the nearest), in the top third:
  each a 0.5 px `#cfe0ff` line (.05 at the top to .16 at the star) ending in a four-point star (three heroes, white,
  7–9 px; the rest 3–5 px in white, ice-blue and violet), three in ten with a tiny star partway up. They lower over
  700 ms each (a soft spring, 1 − e^(−4.6u) cos 5.2u), staggered across 320 ms, then sway as slow pendulums (1.4–3.6°,
  3.6–6.2 s, each its own phase), twinkle (.72–1), and up to six neighbours are joined by faint lines (.12). The pointer
  pushes the nearest within 70 px (up to 16 px) and they spring back. Leaving, the curtain lifts and fades in 600 ms.
  Calm and reduced motion: hung and still.
- **The hero glint:** one 24 px four-point star (plus a fainter one turned 45°) blooms at the knob, sin(πu)^.7 over
  400 ms, turning 25°. The signature beat.
- **The constellation:** 7–12 of the sky's own brightest stars near the composer (above it on the home, beside it in a
  conversation; never over the greeting, the reading column, the sidebar or the glass) are joined by their minimum
  spanning tree in hairlines (0.8 px, `#cfe0ff`, .30 → .42 along each line, additive), each line drawing in over 260 ms
  (all within about 600), a faint point at each joined star; it holds to 1.1 s and fades over 1.2 s, riding the
  field's turn. Different every time; lines, no circles. (The sky's star hash is one the CPU repeats exactly, so the
  lines meet real stars.)
- The sky's brightest stars (now the top 4.5 %, three times as many) flash their four-point glint at +200 ms
  (2.6 × at .55 s, x e^(1−x)), then settle to their gentle twinkle.
- The orb flares: eight fine rays (38 px, 400 ms) and a small bloom `0 0 6px 2px #fff, 0 0 12px 3px violet .7`.
- **The sweep:** one thin horizontal band of light (a 7 px core, a faint 28 px skirt; white at its core, blue → violet
  at its edges, screen-blended at .6) rises from the composer's top edge to above the sky in 700 ms (ease in-out),
  fading as it goes; the stars brighten as it passes. Lines, never circles.
- **The sky:** the field turns 5.5° (1.6 s smootherstep, the opening's direction) and springs back to its rest drift the
  same way on leaving; the aurora erupts to
  1.6 × Full's level for the mode at 1 s (x² e^(2(1−x))), both curtains, briefly faster, richer, leaning to the pair
  (`mix(col, mix(ice (.56,.72,1), violet (.65,.55,1), height) × luminance, .7)`), and rests at 1.3 ×; the stars flare once
  (+.9, x e^(1−x), peak .35 s) and rest 30 % brighter; a faint rectangular tint along the screen's edges
  (`smoothstep(.78, 1, max(|x|,|y|))`, .24 at the peak, .04 at rest). In Balanced the sky is lifted to Full while at Ultra.
- The composer lifts once: scale 1.01 at 30 % of 1.5 s, then settles.
- The line of light runs round the border (600 ms, from the beam's angle) and leaves the lit edge.

While at Ultra:
- **The lit glass edge:** a 1.5 px rim in the cool light with a white highlight
  in ice and white (`conic-gradient(#8fb7ff, #c9d8ff 26%, #fff 46%, #b9b0ff 62%, #dce8ff 69%, #fff 71%, #dce8ff 73%, #8fb7ff 84%)`)
  that turns once every 6 s, and a tight glow (a 2 px copy, `blur(3px)`, .75): about 2–6 px of light, no halo.
- **Inside the glass:** `linear-gradient(180deg, rgba(143,183,255,.13), rgba(165,139,255,.06) 38%, transparent 72%)`
  plus a faint horizontal ice → violet → ice-white wash, clipped to the glass.
- **The horizon line:** 1 px, 4 px under the composer, 10 % in from each end, `#8fb7ff .55 → #e2ecff .95 → #a58bff .55`,
  fading at both ends, `0 0 4px rgba(165,139,255,.45)`.
- **The sky's stars answer:** the brightest (top 1.5 %) wear a faint four-point glint (arms falling off over about
  3 px) that twinkles gently, each at its own pace (.55 ± .45).
- **Stars drift round the composer:** one every 170 ms, at most 40, from the outer thirds of the top edge (60 %; the
  centre stays clear so text is never covered) or a side, 5–9 px (one in five 10–13 px), drifting 30–130 px over
  5.2–7.6 s with a calm twinkle.
- **The charged state:** hairlines and outlines turn faintly blue-violet (`--hair rgba(150,165,255,.13)`,
  `--hair2 rgba(150,160,255,.22)`, `--line rgba(170,160,255,.45)`, registered so they ease), keyboard focus stays the
  ember ring, the chosen mode's mark is an ice → violet diamond, the mode chip wears no badge (removed: it repeated the label beside the
  slider). The send key is not charged (no outline, no sheen).
- **Sending at Ultra:** no glint on the key; a bright streak (a 90 px line, ice to white at its
  head) runs from the key to where the answer starts in 460 ms, leaving nine tiny stars that twinkle out in 520 ms;
  the writing star is born where it lands, with its prism tail.
- The slider's fill flows slowly in the pair (`#8fb7ff → #a58bff → #b8ccff → #a58bff → #8fb7ff`, one 2 × width period
  per 7 s) with its bloom; the knob's halo turns to the pair; the knob's glow breathes ice ↔ violet (3.5 s).

- **The star signs (per the owner: "definitely keep the star signs dynamic"):** at Ultra, every 20–30 s (the first 9–15 s
  after arriving) a constellation forms from the sky's own near-layer stars, in a different place each time: left of the
  column, right of it, above the greeting, or above the box. 4–6 neighbouring stars are joined by their minimum spanning
  tree (one in three closes into a figure), each line drawing star to star in 420 ms with a travelling light at its head
  (a 3.2 px white point), 0.7 px `#cfe0ff` at .24 → .34, a 4.6 px point lighting at each star reached; it holds 2 s and
  dissolves over 1.2 s; one in three drifts slowly up (9 px/s) as it fades. Plain geometry: no art, names or symbols.
- **The smash (per the owner: "a little more smash effect when somebody slides to Ultra", like Astra or Ultra Code):**
  once per arrival, about 700 ms, ice, violet and white only; no circles, rings or ovals.
  1. *Light rush* (0–180 ms): a 56 px white highlight (`.95` at 72 %) races along the fill from the knob back to the start.
  2. *Edge bloom* (80–500 ms): the composer's top edge ignites at the knob's x and races left and right as a 1 px
     `rgba(240,245,255,.98)` line with `0 0 6px 1px rgba(205,222,255,.85), 0 0 14px 2px rgba(143,183,255,.45)` (within
     16 px), revealed by `clip-path` from the knob outward by 55 % of 420 ms, then fading as the 1 px ice rim takes over.
  3. *Star burst* (100–700 ms): the field above the box launches up from the composer's top edge, each star after
     100–400 ms, rising over 420–600 ms (ease-out cubic) to its place; two or three go 60–110 px further and fade.
  4. *Kick* (0–220 ms, Full): the composer scales 1 → 1.012 → 1 on `cubic-bezier(.2,.8,.2,1)`, no wobble.
  5. *Label*: one fast bright sweep on "Ultra" (450 ms), then the slow silver sweep (every 3 s).
  Balanced: the rush, a dimmer bloom (`0 0 5px 1px … .55, 0 0 10px 1px … .25`), half the stars, no kick. Calm and
  reduced motion: none. It never retriggers within 1.5 s and only fires arriving from a lower level; coming back within
  that window the Ultra state returns quietly (no surge, wave or launch). The constellation and the chandelier are built
  a frame or two later, so the arrival's own frame stays light.
- **Ultra at rest (per the owner: "give Ultra a little more effect"):** Full:
  - every 8 s a soft ice-white comet travels once along the composer's top edge (a 120 px, 1 px line, ice to a white
    head, `0 0 4px` glow, 900 ms on `cubic-bezier(.45,0,.25,1)`, clipped 14 px in from each corner);
  - the field above the box drifts up 4 px/s and wraps seamlessly (14 px soft edges), with more twinkle variety
    (periods 2–7 s, depth .2–.55, three in ten sharp sparkles); a shooting star crosses its band every 12–18 s (the
    first 5 s in): 90–150 px, 450 ms, a 1 px ice tail and a white head;
  - a faint wide strip of ice light spills up out of the box: 52 px tall, 5 % in from each side, `rgba(200,218,255,.08)`
    at the edge to nothing, horizontal fade at the ends, breathing to .75 of that over 10 s (a strip, never an oval);
  - the fill's dot-matrix marquee (see the knob at Ultra).
  Balanced: half the light (the strip .5, the glint .35), no comet, the band's shooting star every 25–35 s. Calm and
  reduced motion: none. All of it pauses while the page is hidden or not in front.
- **The dot matrix (per the owner: "we do dots, like dot matrix, like Ultra Code"):** at Ultra a fine LED grid fills the
  band above the box (the stars' band; a thinner strip in a conversation): square dots 1.8 px across (a 0.5 px soft
  edge), on an 11 px pitch, at 4 % white, feathered 30 px at the sides, 22 px at the top and 8 px at the bottom. Soft
  sweeps of light pass through it, horizontal or diagonal (±0.8, ±0.6), never radial: a Gaussian front 52 px wide moving
  at 180 px/s (so a dot takes about 290 ms to light, never a flash), lifting the dots to 35 % ice-white `(.86,.92,1)` and
  letting them fall back; a sweep every 4–6 s (Balanced: every 8–12 s at half the brightness), and one in five comes early
  so two cross. On arrival, as part of the smash, one fast sweep (600 ms) runs out from the knob's x along the box's top
  edge and then up (its front `|x − kx| + 1.6 (top − y)`), up to 45 %. Drawn in the sky's shader (no DOM), behind
  everything, never under the greeting; fades with Ultra; none in Calm or reduced motion.
- **Stars above the box (per the owner: "more stars above the box versus in the box"):** at Ultra a gentle field of
  small white-ice stars (1.5–3.2 px, one in eight 1.4 px larger; the star palette) fills the space between the greeting
  and the composer, across the composer's width plus 30 px each side: 40 in Full, 20 in Balanced, four in ten sitting on
  the dot matrix's grid (one system). Four of them (two in Balanced) are larger four-point glints (5–6.5 px, a brighter
  core, .7–.9) that twinkle by brightening over 4–7 s, never turning. It fades in over
  600 ms; each twinkles slowly (.62–1 of its .38–.78 brightness, 3–6 s); every 4–8 s one drifts up 28 px over 3 s and
  fades, and another appears elsewhere. In a conversation, a subtler strip in the 34 px above the composer (half as
  many, .7 as bright). In the sky layer, behind everything; never over the greeting's letters; re-seated when the
  composer moves; fades with Ultra's power-down. None in Calm or reduced motion.
- **The aurora: level, shifting a touch, something special (per the owner: "level and a little more dynamic ... that
  doesn't mean faster"):** level always: the curtain's base sits horizontal (its waviness .035, its ripple .012, its
  segments rising and falling .03) and the rays stay vertical; the layer never rotates or tilts, and the CSS curtains
  only slide (±44–48 px, no skew). Its centre wanders gently: legs of 60–120 s on a smootherstep (`u³(6u² − 15u + 10)`)
  to targets 10–25 % of the width either side of centre (three in ten back to centre), never within 8 % of the last.
  Its half-width breathes between .22 and .38 (legs 30–60 s). Its folds roll subtly: x displaced by
  `tam × (.12 sin(2.2x − φ) + .05 sin(5.1x + 1.7φ))`, `tam` .45, φ one turn per 20–40 s. Its height breathes ±12 % over
  26 s. Inside it: the rays brighten and fade along their length (`× (.72 + .28 noise(16x, 5d − 1.4ℓ))`) and across it
  (`× (.7 + .3 noise(1.3x, ℓ))`), ℓ advancing .05 per second; the colour runs from blue `(.62,.78,1)` at the lower edge
  to violet `(.7,.6,1)` towards the tips (a .18 touch of the blue-violet palette); the lower edge is crisp (rising over
  .012) and softly luminous (`exp(−55|d|)`). Every 2–4 min it splits in two (the lobes ±.17 apart) for about 20 s: 6 s to
  split, 8 s held, 6 s to merge. Balanced: 1.6 × slower and half the amplitude. Calm and reduced motion: still and
  centred. Paused while the page is hidden or not in front. ?aur=0.5 pins its centre (for checks).
- **The aurora's lower edge undulates (per the owner: "a slow, soft, wavy line, not a ruler"):** the base (60 % up,
  the second curtain 70 %) carries two long waves along the folded x, `wam × (.07 sin(4.2x + 1.2ℓ + 1.7k) + .03 sin(7.3x −
  .35ℓ + k))`: about ±10 % of the height, one crest every quarter to half a screen, drifting about one cycle per 100 s
  and carried by the folds (they ride the displaced x). The waves are symmetric, so the edge stays level overall.
  `wam` is 1 in Full and .5 in Balanced and in Calm (still there). Each ray ends at its own depth: the body fades in
  over `.014 + .085 × rays` below the base, so the brightest rays reach up to 10 % lower and fade out gradually;
  the crisp luminous edge (`exp(−55|d|)`) follows the wavy line. The reach breathes: legs of 30–60 s on the same
  smootherstep, 45 % of them reaching (a depth of .35–1 of the full reach), the rest retreating to 0; where it
  reaches (a broad noise along x, `smoothstep(.45, .95, noise(1.6x, .18ℓ))`) the base drops up to 8 % more. The
  base keeps a smooth floor (a smooth max, width .08) one ray-tail (.1) above the line 36 px over the composer's top
  (`flo`, read once a second), so near the floor the edge rounds off instead of flattening, and below that line the
  light fades out over 4 % of the height: nothing reaches the composer. Under the greeting (across its width, feathered over 10 % of the
  width) the first curtain's crests round off 2.5 % below the greeting's bottom (a smooth min, width .06), so the
  bright edge never crosses the text; the dips are free. Balanced: half the reach
  and the 1.6 × slower clock; Calm and reduced motion: no reach, the edge holds still; paused while the page is
  hidden or not in front. ?aurlow=1 holds the full reach (for checks).
- **The aurora at resting Ultra (per the owner: stronger, leaning violet):** the curtain's colour is mixed `.7 × cool`
  of the way (`cool` is 1 at rest in Ultra, up to 1.3 in a surge, 0 outside Ultra) towards a blue-violet,
  `(.56,.72,1)` at the lower edge to `(.65,.55,1)` at the tips (25 % further to violet in Ultra), then rescaled so its
  relative luminance (`.2126 R + .7152 G + .0722 B`) is exactly `1 + .2 × min(cool, 1)` times the curtain's own: 20 %
  stronger, never more, never white. Behind the greeting (its box, read once a second, feathered over 7 % of the width
  and 10 % of the height) it stays 25 % under its resting strength instead, so the greeting keeps AA at Ultra.
  In the same zone, always (at rest, at Ultra and through the arrival's surge), the curtain's light rolls off with a
  soft knee: luminance `ℓ` (after the level) becomes `ℓ / (1 + ℓ / .06)`, so a bright fold never sits on the text. (This line had been lost to a stray comment
  until 7.0 beta; it is now drawn.)
- **Shooting stars:** every 6–10 s in Full, 10–16 s in Balanced (the first 4–7 s after arriving), one thin streak (1.1 px, white, a tail fading to
  nothing over the last 42 % of its run, a 4.5 px glint at its head) crosses 120–260 px of the upper sky (72 px to
  26 % down) at 18–32° in 500 ms, only in the sky beside the text column (never over it, the sidebar or the header).
- **Star rain:** at the far left and right edges (6 % of the width, at most 90 px), tiny stars (1.6–3.2 px) fall at
  14–30 px/s with a 2–6 px sway and a twinkle, one every 350–650 ms, at most 22, fading out by 86 % down.

Leaving Ultra, the power-down: the accent drains back in 800 ms, the drifting stars drift 24 px up and fade (800 ms),
the sky eases back to the chosen level (time constant .3 s, about 900 ms) and its twist springs back, the constellation,
shooting stars and rain fade with it, the burst fades in 300 ms; the rim drains
back the way it came; tints, line, glow and knob fade in 900 ms.

Calm and reduced motion: the still rim, the still gradient label and a brighter still sky (stars 30 % brighter,
exposure 8 % up) only.

### The sideways lock
No layer may widen the page. The colour wash (12 % past each side) and the aurora band live in a clipped layer
(`#decor`, `overflow:clip`); the stage itself is `overflow:clip` (it cannot be scrolled by focus, find-in-page or a
selection drag, which is how the page once slid sideways at 2000 px); a guard returns any window or stage scroll to 0;
the conversation scrolls vertically only. Checked: `scrollWidth === innerWidth` at 2000, 1440, 1280 and 390 through
the opening, the menus, Ultra, a slider drag and typing.

## The ink: how an answer streams
- **Cadence:** tokens arrive as a real stream would (bursts of 1–8 words, 30–170 ms apart, after 120 ms) into a buffer;
  words leave it at an even 30 a second (36 at Extra and Ultra), ×0.82 when fewer than 6 are buffered and ×1.12 when
  more than 30, with a 0.09 s breath after `. ! ? :`. Code blocks and tables arrive whole and take the time of 4–8 words.
- **Each word:** fades in over 220 ms with a 1 px rise and a 2 px → 0 blur, `cubic-bezier(.2,.7,.2,1)`; its light, a
  `drop-shadow(0 0 6px rgba(255,255,255,.6 → .38 → .14 → 0))`, lasts 300 ms in all, so the newest three or four words
  glow like wet ink and settle to plain white. The writing star rides the newest word.
- **No jumps:** the answer's height follows its content on a 240 ms `--out` transition; the reading column follows the
  newest line (it closes 9 × the overshoot per second) until the reader scrolls away. A paragraph's space opens in
  120 ms (its top margin from −16 px; a list item's from −6 px); headings rise 3 px and fade in 340 ms; list numbers
  fade in 300 ms; code and tables fade in whole over 400 ms.
- **The weight settles:** each word arrives lighter and settles to its weight over 280 ms (`font-variation-settings`
  "wght", Space Grotesk loaded as its variable 300–700): reading text 320 → 400, bold and headings 150 lighter (bold
  450 → 600; the 500 heading from 350). Its width is held at the rest weight, measured as it lands, so nothing reflows;
  code does not morph (it arrives whole).
- **No reflow:** the answer sets `text-wrap: wrap` (not `pretty`, which re-breaks earlier lines as words arrive); a
  word's trailing space is laid down just before the next word; text splits at hyphens as it may break there; a new
  block opens its space before its first word (a 170 ms pause); kerning is off while the words are separate boxes
  (`.body.inking`), so a settled, unwrapped word sits exactly where its box did; the answer's height stays held from
  the stream into the dissolve; on a phone the live numbers always take their own line. Measured: no word moves and
  CLS 0 while streaming at 1440 (0.0001 on a phone, a blockquote's space opening).
- **Light DOM:** a word settles 420 ms after it appears and is unwrapped to plain text; at most about 16 spans live.
- **Draft → polish:** the draft and the polish share their structure. Word by word (a longest-common-subsequence per
  text run) unchanged words stay; changed passages dim to .12 with a 1.5 px blur in 220 ms, then their new words
  shimmer in (620 ms: opacity 0 → 1 and blur 1.5 px → 0 by 55 %, the same light fading out), 45 ms apart in reading
  order, at most 480 ms of stagger. The height eases between the two.
- **Calm:** a plain per-word fade (220 ms), no blur, no light; the dissolve is a plain 400 ms fade. **Reduced motion:**
  the words appear with no animation, and the polish replaces the draft at once.

## The hour's grade (the footage and the sky as one image)
The footage is mapped on its luminance into the hour's palette: shadow → middle (at luminance .5) → light,
smoothstep within each half, the map faded in over luminance 0–.18 so black stays the sky; more than half of the real
colour is kept so cities and auroras read as real Earth. Trails and bloom take the palette's hue at their own
brightness (the map at luminance + .35, rescaled), the same share kept. PINNED (per the owner: "more of the NASA one,
less blue, a little more day colour"):

| Mood | Shadow | Middle | Light | Real colour kept | Footage weight | Gradient thins by |
|---|---|---|---|---|---|---|
| night | `#060608` | `#3e3f4e` silver | `#e8eaf0` silver | 64 % | 1.45 | 0 |
| dawn | `#0a0809` | `#c98c80` rose | `#ffe2b8` gold | 62 % | 1.32 | 0 |
| day | `#090a0c` | `#96b2ce` soft sky | `#fff7ec` warm white | 66 % | 1.28 | 0 |
| dusk | `#0a0809` | `#d69654` amber | `#ffd4c2` warm rose | 62 % | 1.32 | 0 |

PINNED (per the owner, "composite the background over black instead of blue"): the footage sits on black at every
hour. The sky's own gradient is near-black and the same all day (top, middle, low, sRGB 0–255: `3,3,5 / 4,4,6 /
7,7,10`, the small lift keeps it from banding); the shadows of every mood are neutral near-black; the hour lives only
in the footage's grade (its middle and light). No coloured wash over the black: the warm foot glow at dawn and dusk is
off, the moonlight is neutral (warm white to `rgb(214,217,222)`, peak .22), the opening's colour wash keeps only its
rose and amber (its blue and teal are gone), and the horizon band is a trace (.24).

- The moods turn at 5:30 (night → dawn), 7:30 (→ day), 17:30 (→ dusk) and 19:30 (→ night) local time, each over 20
  minutes on a smoothstep; the clock is read every 20 s while the page is open and the shader's palette eases toward it
  (time constant 2 s), never a step. `?hour=6|12|18|23` pins the clock
  (for checks).
- **Blend, not stack:** the graded footage is screen-blended into the sky, its weight falling off with height as before
  (`foot`, `rise` per clip) and feathered at the sides (8 %) and the foot (12 %) so there is no frame. Weight by level, times the mood's: Full 1, Balanced .85 (was
  .75), Calm .6 on a still frame, graded the same way. The flash limiter (the trails' attack)
  and the highlight knee (above .45, rolling off toward .85) are unchanged; the horizon-free bands are unchanged.
- Until this build a comment in the sky's uniform upload swallowed the rest of its line, so the exposure, warmth, tint,
  Ultra sweep, edge tint and the twist's centre were never set: the footage itself (as opposed to its trails) never
  drew, and the field turned about the top-left corner. All are set now.

## The composer: flat and low (per the owner: "flatten out the Ask anything, make it lower, more centred")
One line of text and the control row, as one unit centred in the glass: 99 px tall at rest on the home (95 on a phone):
padding 13 px top, 12 px bottom, 16 px left and 14 px right (14 and 12 on a phone); the textarea one line (26 px), 2 px
then the row's own 8 px above the 36 px row (a 10 px gap in all). Only typed text grows it, up to 156 px of text, then it
scrolls. Its centre sits at the golden point of the free height below the header (61.8 %), measured within 0.5 px at
1440 and 390, and re-seated whenever it grows.

## The lanes: Chat · Code · Funnels
A glass segmented control in the header's centre (the same place and centring as before), three equal segments
(at least 88 px, 76 on a phone), 32 px tall, radius 6 outside and 4.5 inside (the slider's language). The lit box
(`linear-gradient(180deg, rgba(255,255,255,.13), .06)`, an inner top light, a 1 px `rgba(150,165,255,.3)` edge and a
12 px blue glow) slides between segments in 200 ms on `--out`; the labels cross from `--ink3` to `--ink`. Funnels wears a
9 px four-point star (it twinkles once on hover, never otherwise); selected, its box's edge is a brighter silver
(`rgba(240,242,248,.46)`, a soft white glow); the other segments' box is silver too (`rgba(226,230,240,.28)`). Tabs with arrow keys, Home and End; an inset ember ring for the keyboard. On a
phone it sits just under the header. Chat returns home; Code shows a sample task (two reads and an approval card for a
write: Approve or Skip, the preview runs nothing); Funnels shows a sample funnel (three narrowing questions with the
chosen option lit, then the one pick with its reason and next step), as the app's funnels work.

## Subtract and refine (the latest pass)
- Removed: the Effects popover's own "Effects" heading (its button already says so); the hairline under the chosen
  lane (the sliding box replaces it); the landed answer's token, speed and time line (Details already holds them).
- Kept on purpose: the status dot (Calm and Balanced) and the machine chips (Full) are one indicator shown per level,
  not a duplicate.
- Feel: every control in the composer row and the lanes presses in 1 px (and to .985) in 80 ms and lets go cleanly,
  with no glow on release (see "No flashes, no shine on controls"). The row's
  controls are all 36 px tall (32 on a phone); the slider's hit area matches them.

## The sidebar's chats
Every row is a button. In the preview each of the six opens a short sample conversation at once (history: no writing,
no star): one question and one polished answer, the byline with the mode, the finished live line and stats, Details
(the steps that mode takes, the machines) and sources where they fit, and the fine print "Sample chat. This preview
runs no models." The chosen row is `.on` with `aria-current`; focus moves to the question (the live region stays quiet,
so a screen reader is not read the whole answer); under 1100 px the sidebar closes. A chat asked in the preview
reopens the same way. New chat returns home and clears the selection. The rows' keyboard ring sits inside the row
(the list clips outside it).

## Silver and one hue: the sweep (what changed from the rainbow)
- The effort fill, Low to Extra: silver-white (above); only Ultra has colour, in the pair.
- The wet-ink edge while an answer streams and the polish's shimmer: neutral white.
- The lanes: a silver box for every lane; Funnels' edge a brighter silver, never violet → rose. The sample funnel's
  chosen options: silver.
- The aurora (Full): blue-violet only, its curtains in `(.56,.68,1)`, `(.66,.56,1)`, `(.8,.86,1)`, `(.6,.62,1)` and a
  base `(.55,.7,1)` (was pink, gold and green); the DOM curtain that was teal is violet.
- The opening: the wordmark's glints, flare and glow in silver and ice (was pink, teal and gold); its wash silver.
- The greeting's trace: the same blue-violet palette.
- The sky's rare warm stars are near-white (`1, .98, .95`).
- Approval card's write tag: silver (the ember is kept for the send strike, the focus ring and errors). Keyboard focus is
  the ember ring at Ultra too (the violet ring is gone).
- Checked by a scan of every colour literal and shader constant for rose, pink, red, gold, orange, green or teal: the
  only warm ones left are the ember (send key, its hover, errors), the greeting's warm-white glow, and the machine dies.

## Modes and effort

Modes: **Fast** (fast answers) · **Thinking** (thinks it through) · **Pro** (every model on
your machines) · **Max** (every model, every machine) · **Deep** (keeps going until you stop
it). Effort: **Low · Medium · High · Extra · Ultra**. Bylines read "Concorde Thinking" ("Concorde Thinking · Ultra" at Ultra).

## The arrival's hang (PINNED, per the owner: "if somebody clicks Ultra, it has a certain hang to it"): weight and timing
One family of easing: `--out` `cubic-bezier(.16,1,.3,1)` to release; `--inout` `cubic-bezier(.65,0,.35,1)` (and the
smootherstep `u³(6u² − 15u + 10)`) to hang and settle; no bounce, no overshoot anywhere.
1. **Anticipation, 0–140 ms:** the sky holds its breath: its exposure dims to .92 (ease-out over the 140 ms), the sky's
   clock (twinkles, aurora flow, wander, drift) slows to a tenth; the knob settles to scale .97 (140 ms, `--out`).
   Nothing fires.
2. **Release, 140–500 ms:** the sky's clock eases back to full speed by 500 ms; the bar's rush (180 ms) and the knob's
   lift back to 1 (300 ms, `--out`); the box's edge ignites from the knob outward (420 ms, `--out`, from 180 ms); the burst
   leaves the knob; the kick (Full, 1 → 1.012 → 1 over 360 ms, `--inout`); the label's fast sweep; the matrix's arrival
   sweep along the edge.
3. **Hang, 500–1600 ms:** the field's stars launch from the box's edge (each after 80–340 ms of the release) and go
   nine tenths of the way on a hard exponential ease-out in 420 ms, then float the last tenth on the smootherstep over
   the next 0.9–1.2 s, like sparks at the top of their arc; the matrix's wave rolls up to the greeting on an in-out over
   1.1 s (from 500 ms); the greeting's rim light rises as it arrives (1.3 s; Balanced 1.0 s at half) and fades over
   1.2 s; the aurora's swell peaks at about 1.14 s and eases off.
4. **Settle, 1600–2600 ms:** the exposure returns from .92 to 1 on the smootherstep; everything breathes out into
   resting Ultra.
Resting Ultra is thinned so the arrival stays the hero: showers every 60–90 s (was 45–60), the matrix's sweeps every
3.4–4.6 s (one in four early), the greeting's rim glide every 16 s at .55.

## Ultra, pushed further (per the owner: "push the Ultra effect even more"; the rules still hold)
**Arrival (Full):**
- After the bar's rush and the edge bloom, a wave rolls up through the dot matrix from the box to the greeting: a
  horizontal band (Gaussian 34 px) lifting the dots by up to 42 %, starting 500 ms in and taking 1.1 s (in-out) to
  cross the band (see the hang).
- As it reaches the greeting (1.3 s in) the letters catch a thin ice rim light along their top edges: a copy of the
  words (the same text, never offset sideways) whose `0 −1px 0 rgba(214,230,255,.9), 0 −1px 3px rgba(170,200,255,.3)`
  shadow shows only above each letter (the copy sits beneath the letters, `z-index: −1` inside the greeting's own
  stacking context, so the white letters cover all but the light above their top edges); it rises in 250 ms and fades
  over 1.2 s.
- The aurora swells for about 1.5 s with the arrival's surge (x² e^(2(1−x)), peak at 1 s): brighter (+.45), taller
  (its height × 1 + .22), a little more violet (its cool lean × 1 + .3), then eases back.
- The star burst lingers longer before settling: 3–5.2 s (those drifting to the chandelier 4.2–6 s); still 120 stars.
**Resting Ultra (Full):**
- The aurora 20 % stronger than before (× 1 + .56 at Ultra, was .3) and leaning violet (+.25 towards violet in its cool tint).
- The dot matrix busier: a sweep every 3.4–4.6 s, one in four early so two cross (thinned from 2.6–3.4 s for the hang).
- Meteor showers: every 60–90 s (the first 20 s after arriving), 3–5 shooting stars from one radiant (16–28°, all the same
  way) cross the band between the header and the greeting, 120–380 ms apart, each 110–200 px over 480–600 ms, a 1 px ice
  tail and a 3.8 px white head.
- The greeting's rim light glides once across the letters every 16 s: the same rim, revealed by a soft band (20 % of a
  250 % mask) moving left to right over 2 s, at .55.
**Balanced:** about half of everything: the aurora's lift and surge at half, the arrival rim at half, no rim light at
rest, the matrix every 5.2–6.8 s, showers about every 2 min (110–130 s). **Calm and reduced motion:** none. All of it
pauses while the page is hidden or not in front.

## The beauty pass (per the owner: "30 % more beautiful without being tacky, keep the look dark")
- **Depth:** the sky's stars in three layers: near (46 px cells, 16 % of cells lit, core .8 px, full brightness, the rest
  turn speed; the constellations' layer), mid (19 px, 7 %, .55 px, × .5, × .7 the turn) and far (12 px, 4.5 %, .42 px,
  × .3, × .45 the turn). A barely-there camera drift moves the whole sky 4 px × 3 px over 97 s and 131 s; no rotation;
  none in Calm or reduced motion.
- **Darker and richer:** exposure × .9; a vignette `clamp(1 − 1.25 |d|², .16, 1)` (d from (.5,.48), scaled .9 × 1.15)
  keeps the corners near-black; a gentle toe deepens the blacks (`× (1 − .3 e^(−28 L))`) without touching the footage's
  mid-tones; a fine blue-noise dither (interleaved gradient noise, ±0.6 %, re-seeded each frame) kills banding.
- **Light quality:** every star has a tiny core and a soft halo (sky stars `e^(−d²/σ²) + .14 e^(−d²/10σ²)`; the GPU
  particles `1.3 e^(−90r²) + .16 e^(−9r²)` with arms `.7`); the brightest sky stars wear faint diffraction spikes
  always (.16, more at Ultra), never turning.
- **The glass:** `--blur: blur(30px) saturate(108%)` (was 24 px, 140 %); every glass panel keeps its 1 px top highlight
  (`--spec`) and gains a whisper of inner shadow at the bottom (`inset 0 −1px 0 rgba(0,0,0,.28), inset 0 −12px 18px −14px
  rgba(0,0,0,.45)`).
- **Type:** the greeting tracks −0.03 em above 600 px and −0.02 em on a phone; its close glow is tighter (16 px and
  34 px at .42 of it).

## No flashes, no shine on controls (PINNED, per the owner: "maximize and run VFX hard, but we don't want tacky")
- **No flashes.** Nothing on screen goes from dark to bright in under about 200 ms, except the deliberate Ultra arrival
  rush along the bar. Every effect fades in and out over at least 300 ms; nothing spawns or ends with a flare.
- **The footage's loop seam** is never a hard cut and never a dip: there is no native `loop`; through the last half
  second the newest frame is kept in a texture (so a clip that stalls short of its end is covered too), the clip is
  sent back to 0 on `ended` (or by the watchdog), and the footage dissolves from the held frame
  into the new start over 1.4 s (smootherstep). This was the bottom-right flash: the city-lights clip jumped 23/255 in
  that region's mean at every 7.2 s seam. (A 700 ms fade through black was tried first: its own fade-in brightened a
  region by 8–10/255 in 200 ms.)
- **The footage's lights** may not rise faster than the trails' attack limiter allows: the limiter now lets a light
  climb at most 0.8 of full scale per second (about 600 ms from dark to bright; was 1.8), and the footage's highlights are
  capped by that limited trail in Full and Balanced alike (the trails' feed now runs in Balanced too, unseen; their
  bloom and streaks stay Full's). The highlight knee (above .45, rolling off toward .85) stays.
- **Measured** by recording 60 s at rest (home and Ultra, Full and Balanced, at 1440, every clip) and reading every
  frame: a spike is the bottom-right quadrant's peak rising by more than 8 % of full scale, or its mean by more than
  8 %, within 100 ms; anywhere, an 8 × 5 region's mean rising by more than 8/255 within 200 ms.
- **No shine on controls.** The composer's keys are clean, flat keys. Send: neutral glass when the box is empty, a solid
  ember fill while there is text (a flat, slightly lighter ember on hover), a crisp 1 px press on click. No gradient,
  sheen, glint, glow, outline colour or lift, at any level, Ultra included; no glow on release anywhere. Attach and
  mic: the same; the mic's listening state is a plain brighter fill (its glow pulse is gone). The send strike stays: one
  1 px ember line across the composer's top, 240 ms, no glow.

## Footage on WebKit
- Every `<video>` lists the `.mp4` first, then the `.webm` (WKWebView and Safari can freeze a `.webm` on its last frame).
- The clip loops by script (see the loop seam above), not by the `loop` attribute.
- A loop watchdog checks every 400 ms: a clip stalled within 0.6 s of its end for two checks is sent back to 0 and played.
- The sky draws from its first frame with a one-texel black footage texture; the footage is uploaded only once a frame
  has been decoded (`requestVideoFrameCallback`, else `loadeddata`), and fades in. No stall at the opening.

## THE GOVERNING RULE: Claude-sharp chrome, GPT-grade motion (PINNED, per the owner: "super GPT smooth and beautiful, but at the same time Claude very tight and to the point")
The working views (the conversation, Code, Funnels and the sidebar) are flat and exact; the motion in them is rich,
smooth and purposeful. The full sky show belongs to the home and to the Ultra moment.
- **Surfaces:** flat neutral near-black, no gradients and no glow: the working ground `#0e0e10`, the sidebar `#141416`,
  the composer and cards `#151517`, the question bubble and the selected row `#1f1f22`. Separated by hairlines of white
  at 8 % that are one device pixel (`--hl`: 1 px, 0.5 px at 2×). No soft outer shadows on panels, chips or keys.
- **Radii:** tags 4, chips 6, keys and rows 8, option and approval cards 10, the composer and the question bubble 14.
- **Type:** Inter for all UI and reading text (Google Fonts, variable `opsz,wght`, `display=swap`); Space Grotesk only
  for the greeting; the wordmark keeps Michroma; Plex Mono only for code. `-webkit-font-smoothing: antialiased`.
  - UI 13 px at 450–500, letter-spacing −0.005em; chips and metadata 12 px; labels 11 px caps at 0.06em, 50 % ink.
  - Reading 15 px on 1.6, weight 400, ink 88 % (`#e0e0e2`), −0.01em, about 66 characters; bold 600; headings 17 and 15
    at 600; paragraphs 0.8 em apart.
  - Metadata 12 px at 55 % ink. Times and figures in tabular numbers. No text-shadow anywhere in the conversation.
  - `cv11`/`ss01` are not applied: the default Inter forms are already the sharper read at these sizes.
- **Spacing:** every gap on the 8 px grid; byline to text 12; question to answer 24; 64 below the last answer.
- **The sky in the working views** recedes to 30 % of its home strength (60 % at Ultra) over 1.2 s, and its footage to
  12 %, so no out-of-focus city light reads as a round blob. Behind the conversation a near-solid flat band
  (`#0e0e10` at 93 %, feathered over 160 px at its sides, a gradient, not a blur) carries the reading column and the
  flow: the sky shows through at most faintly and no star sits behind text. No constellation lines, shooting stars or
  showers while a conversation is open (one that is showing fades). Ultra's resting field in a conversation is the
  short, light version: half the stars, centred over the composer's top edge, each living 2–4 s; motes half as many,
  centred, rising 10–24 px over 1.8–3 s.
- **Motion:** one easing family, `--e: cubic-bezier(.2,.7,.2,1)`, 150–300 ms for interface motion (400 ms for a step
  arriving, 1.2 s for the sky). New turns rise 6 px; steps slide and fade in 6 px; the lanes highlight slides 320 ms;
  hover reveals 150 ms; the silver "Thinking" sweep (2.4 s a pass). 120 Hz, no flashes.

## The header (beta 3)
One row in three columns, `minmax(0,1fr) auto minmax(0,1fr)`, so the lanes sit at the exact centre and a title's
length never moves them (no layout shift when it changes). Left: the chats button, the wordmark (the 7.0 beta tag on
the home), and in a conversation a one-device-pixel hairline then its title, 13 px at 450, ellipsis. Right: the status
dot (its card: "Your machines", This Mac · MLX · Ready, Ollama1 · NVIDIA · Ready; no MLX/NVIDIA chips in the header), a
quiet "Update ready" pill (24 px, hairline; in the demo only with `?update=1`), and the 32 px Settings gear (flat
glass, hairline, radius 8; tooltip "Settings (⌘,)" after 400 ms; ⌘, opens it). As the width shrinks: the title goes
first (once it would show under 96 px), then the wordmark becomes the mark, then the lanes go compact. The lanes are a
flat segmented control: track `#1a1a1d`, selected `#26262a`, no glow. Checked: no overlap and no sideways scroll at
1440, 760 and 390.

## The home (beta 3)
The greeting, the composer and the sky; nothing else. No recent chats (the sidebar opens from the chats button) and no
suggestion chips. The composer's centre sits on the golden point of the space under the header.

## The answer (beta 3, and the live flow)
- **The working line** sits in the byline's row: one phrase in a silver sweep ("Searching the web", "Asking Ollama1",
  "Asking three models", "Comparing three drafts", "Polishing", "Checking the facts"), and after 3 s a clock (12 px,
  tabular). On landing it becomes the byline, "Concorde Thinking · Ollama1" (the machine by name, never an id; "· Ultra"
  in its still gradient when the effort was Ultra). Nothing moves when it does. No "Done in" line and no token counts.
- **Under the answer:** one quiet line of sources as text links ("Sources NOAA · NOAA Tides · RMG · Britannica"), then,
  where the flow column does not fit, one line of hairline chips ("Your machines" or "On this Mac" or "Made on
  Ollama1"; "3 drafts, reviewed" or "One draft, polished" or "One pass"; the shield "Stayed on your machines" only when
  nothing left them) ending in a quiet "Details" that opens a card in place: the journey (3–5 step chips on one
  hairline, each with a crisp check), the total time, the sources numbered with their titles, and "Show the numbers".
  The sample note: 11 px at 50 % ink (the requested 40 % fails AA at 11 px).
- **The flow** (the right column, 240 px beside the 640 reading column, where the window has room for 920 px; else the
  chip line stands in). One vertical hairline; a rounded-square node per stage (28 × 20, radius 6, never a circle):
  Sources → First draft (or Drafts ×3) → Review → Polish → (Fact check) → Answer, each machine a tiny 11 px tag. While
  it runs a soft silver light (1 × 36 px) travels the hairline into the active node over 560 ms; the active node
  shimmers silver (ice at Ultra) and counts inside (the words as they grow, else seconds); sources slide in beside the
  Sources node as chips (6 px, 350 ms) as they are read; a finished node takes a crisp check and settles. On landing one
  gentle pass runs the whole line (1.1 s), then the foot: the shield when true, the total time, and "Show the numbers"
  (tokens and tok/s per node, closed by default). A past answer opens with the finished flow at rest, no motion.
- **Messages:** the question a quiet right-aligned bubble (`#1f1f22`, radius 14, 14 px, padding 10/14); the answer plain
  text under a tiny 13 px byline at 55 % ink.
- **"hi"** (or hello, hey) answers at once, in one pass, on this Mac: the "One pass" chip.

## Streaming v2 (per the owner: "super clean, super smooth")
- A steady, adaptive cadence: 32 words a second (38 at Extra and Ultra), eased toward 25–45 by how much is buffered
  (never a catch-up burst: at most 1.2 words of credit); a 0.12 s breath after a sentence, 0.17 s as a paragraph opens.
- Each word fades in over 180 ms from 1 px of blur to none (the filter ends at exactly none); no weight morph, no glow,
  no sideways move. A word that opens a new line rises 4 px. Settled words become plain text after 240 ms.
- Structure renders as it streams, so landing never reflows (measured: no layout shift at landing, 1440 and 390;
  before: 0.025 at 390). Tables fade in whole; code arrives line by line. The height grows eased (240 ms); the column
  follows eased and holds when the reader scrolls up.
- A 4 px silver dot (no flare, no glow) glides at the end of the text and fades on landing. At Ultra the prism star.
- Draft to final: only the changed words cross: out in 120 ms, in over 250 ms (staggered at most 100 ms). No blur.
- Calm: a plain fade. Reduced motion: none. Balanced and Full share the same motion.

## Code and Funnels (the middle ground)
- **Code:** the same flat surfaces; command output and the approval card flat (`#151517`, hairline, radius 8 and 10),
  mono for commands. Each run slides in, shimmers "Running" in silver, then shows its output and settles to "Done";
  the approval card arrives last.
- **Funnels:** a vertical flow on a hairline. Each step slides in; the current question shimmers silver; options are
  flat cards (`#151517`, hairline, radius 10) that lift 1 px on hover; the chosen one flies (520 ms) into the trail of
  choices at the top, the step takes a crisp check (12 px, on the hairline) and the others step back to 45 %. The pick
  arrives last. Calm and reduced motion: the finished state at once.
