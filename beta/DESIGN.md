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

Type is white or near-white. Colour appears only in light: the sky, the dies, the Ultra
rim, the horizon, the ember at decisions.

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
| `--rose` | `#f2a6b4` | | light only (horizon, Ultra rim) |
| `--champagne` | `#f1dcb2` | | light only (horizon, focused composer's top light) |

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
rose .11 at 86%, champagne .17 at 100%)`, screen-blended, opacity .24 on the home (was .62: over black it read as a coloured base), .12 in a
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
and shows only after a keydown (never after a click).

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
| Fill | from the left to round the orb: `linear-gradient(90deg, #4f8cff, #9b72ff 55%, #f07aa6)` fixed to the track (each step has its own colour); 1 px inner top light |
| Bloom | a copy of the fill beneath it, `blur(8px)`, opacity by step `.32 / .40 / .50 / .62 / .78` |
| Notches | PINNED (per the owner: "very slim and very fluid, not just a bunch of dots"): none at rest. Only while the slider is hovered, dragged or keyboard-focused, five faint 2.5 px squares (radius .5 px) fade in on the centre line in 200 ms `--out`: `rgba(255,255,255,.18)`, passed ones `.5`, no glow |
| Knob | a rounded square, `--ob: 14px`, radius `--kr: 4px` (11 and 3.5 in a conversation, 14 and 4 on a phone), near-white `radial-gradient(110% 90% at 50% 25%, #fff, #f4f7ff 45%, #dde5fa)`, 1 px `rgba(255,255,255,.95)` edge, shadow `0 1px 2px rgba(4,8,30,.45), 0 2px 6px rgba(4,8,30,.35)`; hover 1.05, held 1.10 |
| Halo | the knob's shape: a rounded square 1.5 × the knob (radius 1.6 × `--kr`) in the fill's colour where it stands (`#4f8cff`, `#6f80ff`, `#9b72ff`, `#c776d2`, `#f07aa6`), `blur(6px)`, opacity .45 at scale .85 (at Ultra the cool conic gradient, blurred the same); hover .70 / 1.05; held .85 / 1.22; 300 ms `--out`; never a loop |
| Drag | the knob and the fill follow the pointer continuously (no transition while held: position = (pointer x − left − track/2) ÷ (width − track), clamped 0–1); the level name and everything tied to the level change as it crosses each stop (the nearest stop) |
| Snap | on release, and for every key step: 140 ms `cubic-bezier(.22,1,.36,1)` to the stop, no bounce (knob, fill and bloom together) |
| Level | beside it, Space Grotesk 13/500 `--ink2`, PINNED 12 px off the track (10 on a phone: the row's gap plus 4), so the knob's glow at the track's end has room and never touches the word; updating live: Low · Medium · High · Extra · Ultra. No tooltip and no explanations of the levels anywhere (per the owner: "pretty damn obvious") |

Click anywhere to jump, arrows step. Calm and reduced motion: the same look, no transitions.

### Ultra's light (the cool palette)
Electric blue `#4f8cff` → violet `#9b72ff` → soft rose `#f07aa6`, with white highlights; warm gold `#f3d27a` only as a
rare glint (one sparkle in twelve). No green, orange or red. Text tints that pass AA on the glass, even over Full's lifted Ultra sky: `#9cc0ff`,
`#c4b0ff`, `#f7a3c3`.

- **The label and the byline:** "Ultra" in the text tints with a white-blue highlight band (`rgba(240,246,255,.95)`,
  20 % of a 250 % background) that glides across once every 2.5 s (across in about 1.1 s on
  `cubic-bezier(.45,0,.25,1)`, then rest), `drop-shadow(0 0 6px rgba(155,114,255,.4))`. The byline reads
  "Concorde Thinking · Ultra"; its sweep stops when the answer lands (a still gradient).
  Under the composer's label, a feathered black pill holds it at AA at the sky's brightest (Full at 1280 and on a phone
  dipped to 3.5:1, and 2.9:1 under the noon sky): the slider's first layer, 80 × 34 centred on the word (its left edge
  at the track's end + the label gap − 24 px), `radial-gradient(closest-side, rgba(3,3,5,.62), .56 35%, .30 62%,
  .10 82%, transparent)`, in with Ultra (600 ms), out with it (900 ms) and while dictating. It sits under the
  slider's fill, bloom and knob and under the word, so nothing of the show is dimmed; feathered wide so it reads as
  shade, not a shape.
- **The typed words:** a mirror over the textarea carries the same light in near-white tints (`#dbe6ff`, `#e4dcff`,
  `#f8dde9`), a subtler sweep every 3.6 s; "Ask anything" at .85 (AA in Full). Leaving Ultra crossfades back to white in 600 ms.
- **The send key** (with text): `#6f9bff → #9b72ff → #f07aa6 → #fff → #9b72ff`, flowing one 108 px period per 4 s; a black arrow.
- **The writing star:** a 20 px tail behind it, rose → violet → blue → `#e6efff` at the star.
- **The sparkles:** four-point stars, a white core (2 px; 3 px for the big ones) with two crossed 1 px rays tinted
  white, ice `#cfe0ff`, `#86b0ff`, `#b9a2ff`, `#9b72ff` (gold one in twelve).

### The Ultra moment
Arriving (about 1.5 s), Balanced and Full:
- **The beat** (under 1.2 s): 0 ms the orb clicks into place (scale 1 → 1.12 → 1, 220 ms) as the first star wave and
  the sweep leave; +200 ms the second star wave and the sky's glint flash; +400 ms the lit glass edge comes up (the
  line of light runs round in 600 ms); +600 ms the ULTRA label's light sweep starts and the chip's badge appears.
- **The slider becomes the star (per the owner: "like ultracode"):** the knob folds into a living star, crisp vector,
  white at its core (`#fff → #e6efff → #a99bff`) with blue → violet light, stepping through four, six, eight and six
  points, one form every 140 ms; leaving, it folds back into the rounded square in 200 ms. Seven tiny four-point stars
  drift left to right through the filled track (3.2–5 s each, twinkling, clipped to it). The label keeps its light sweep
  on `#9cc0ff → #c4b0ff → #f7a3c3`. Calm and reduced motion: a still four-point star, no drift.
- **A star trail and a stream:** as the knob slides to Ultra, 18 tiny stars light along the track behind it (over its
  140 ms snap, each 380–500 ms); as it lands, 12 stars stream up out of it (28 ms apart, 640–860 ms).
- **The stars lead.** Three waves of four-point stars burst from where the knob lands (120 in all), drawn on the GPU
  (a canvas above the glass, pooled quads, no DOM): 0 ms, 60 (6 hero stars, 9–12 px half-arms, white; the rest
  3–6.4 px), flying 26–74 px; +200 ms, 36 smaller (2.2–4.8 px), 16–46 px; +400 ms, 24 more of those. White, ice-blue
  and violet (`#fff`, `#dce8ff`, `#cfe0ff`, `#86b0ff`, `#b9a2ff`, `#9b72ff`). Each twinkles twice as it flies and fades
  (opacity 0 → 1 → .45 → .95 → .35 → 0 at 0 / 15 / 35 / 55 / 78 / 100 %, scale .4 → 1 → .8 → 1 → .7 → .3, ease
  with drag: out fast and slowing (1 − e^(−kt), k 4.5–7 /s), then floating like dust in light (a 2–3 px bob, a slow
  rise), dissolving at 2–4 s, staggered; on the home 40 % drift to the chandelier on the knob's side (x over .45 s, y
  over 1.1 s) and settle near a hanging star (3.2–4.5 s). Nothing leaves the screen.
  They fly only into open sky, never over text: the upper half on the home (not down over the suggestions), and low
  to the sides in a conversation (not up over the answer).
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
  1.6 × Full's level for the mode at 1 s (x² e^(2(1−x))), both curtains, briefly faster, richer, leaning blue and
  violet (`mix(col, mix(#4f8cff, #9b72ff, height) × luminance, .7)`), and rests at 1.3 ×; the stars flare once
  (+.9, x e^(1−x), peak .35 s) and rest 30 % brighter; a faint rectangular tint along the screen's edges
  (`smoothstep(.78, 1, max(|x|,|y|))`, .24 at the peak, .04 at rest). In Balanced the sky is lifted to Full while at Ultra.
- The composer lifts once: scale 1.01 at 30 % of 1.5 s, then settles.
- The line of light runs round the border (600 ms, from the beam's angle) and leaves the lit edge.

While at Ultra:
- **The lit glass edge:** a 1.5 px rim in the cool light with a white highlight
  (`conic-gradient(#4f8cff, #9b72ff 26%, #f07aa6 46%, #9b72ff 62%, #dce8ff 69%, #fff 71%, #dce8ff 73%, #4f8cff 84%)`)
  that turns once every 6 s, and a tight glow (a 2 px copy, `blur(3px)`, .75): about 2–6 px of light, no halo.
- **Inside the glass:** `linear-gradient(180deg, rgba(79,140,255,.13), rgba(155,114,255,.06) 38%, transparent 72%)`
  plus a faint horizontal blue → violet → rose wash, clipped to the glass.
- **The horizon line:** 1 px, 4 px under the composer, 10 % in from each end, `#4f8cff .55 → #e2ecff .95 → #9b72ff .55`,
  fading at both ends, `0 0 4px rgba(155,114,255,.45)`.
- **The sky's stars answer:** the brightest (top 1.5 %) wear a faint four-point glint (arms falling off over about
  3 px) that twinkles gently, each at its own pace (.55 ± .45).
- **Stars drift round the composer:** one every 170 ms, at most 40, from the outer thirds of the top edge (60 %; the
  centre stays clear so text is never covered) or a side, 5–9 px (one in five 10–13 px), drifting 30–130 px over
  5.2–7.6 s with a calm twinkle.
- **The charged state:** hairlines and outlines turn faintly blue-violet (`--hair rgba(150,165,255,.13)`,
  `--hair2 rgba(150,160,255,.22)`, `--line rgba(170,160,255,.45)`, registered so they ease), keyboard focus is a
  1 px `#9b72ff` ring, the chosen mode's mark is a blue-violet diamond, the mode chip wears a 9 px "Ultra" badge
  (the label's light sweep, a `#9b72ff` .5 hairline) on its corner, and the send key is charged: a violet outline
  and a slow inner sheen (every 3 s).
- **Sending at Ultra:** a 22 px star glint on the key (420 ms); a bright streak (a 90 px line, ice to white at its
  head) runs from the key to where the answer starts in 460 ms, leaving nine tiny stars that twinkle out in 520 ms;
  the writing star is born where it lands, with its prism tail.
- The slider's fill flows (`#4f8cff → #9b72ff → #f07aa6 → #fff → #9b72ff → #4f8cff`, one 2 × width period per 4 s)
  with its bloom; the orb's halo turns to the cool spectrum; the knob's glow cycles blue, violet, rose (3.5 s).

- **Shooting stars:** every 10–16 s (the first 4–7 s after arriving), one thin streak (1.1 px, white, a tail fading to
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
  `drop-shadow(0 0 6px rgba(214,228,255,.6 → .38 → .14 → 0))`, lasts 300 ms in all, so the newest three or four words
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

## The lanes: Chat · Code · Funnels
A glass segmented control in the header's centre (the same place and centring as before), three equal segments
(at least 88 px, 76 on a phone), 32 px tall, radius 6 outside and 4.5 inside (the slider's language). The lit box
(`linear-gradient(180deg, rgba(255,255,255,.13), .06)`, an inner top light, a 1 px `rgba(150,165,255,.3)` edge and a
12 px blue glow) slides between segments in 200 ms on `--out`; the labels cross from `--ink3` to `--ink`. Funnels wears a
9 px four-point star (it twinkles once on hover, never otherwise); selected, its box's edge turns violet → rose
(`rgba(196,140,240,.42)`, a rose glow). Tabs with arrow keys, Home and End; an inset ember ring for the keyboard. On a
phone it sits just under the header. Chat returns home; Code shows a sample task (two reads and an approval card for a
write: Approve or Skip, the preview runs nothing); Funnels shows a sample funnel (three narrowing questions with the
chosen option lit, then the one pick with its reason and next step), as the app's funnels work.

## Subtract and refine (the latest pass)
- Removed: the Effects popover's own "Effects" heading (its button already says so); the hairline under the chosen
  lane (the sliding box replaces it); the landed answer's token, speed and time line (Details already holds them).
- Kept on purpose: the status dot (Calm and Balanced) and the machine chips (Full) are one indicator shown per level,
  not a duplicate.
- Feel: every control in the composer row and the lanes presses in 1 px (and to .985) in 80 ms and lets go with a soft
  glow (`0 0 0 1px rgba(207,224,255,.32), 0 0 14px rgba(159,192,255,.32)` fading in 450 ms on `--out`). The row's
  controls are all 36 px tall (32 on a phone); the slider's hit area matches them.

## The sidebar's chats
Every row is a button. In the preview each of the six opens a short sample conversation at once (history: no writing,
no star): one question and one polished answer, the byline with the mode, the finished live line and stats, Details
(the steps that mode takes, the machines) and sources where they fit, and the fine print "Sample chat. This preview
runs no models." The chosen row is `.on` with `aria-current`; focus moves to the question (the live region stays quiet,
so a screen reader is not read the whole answer); under 1100 px the sidebar closes. A chat asked in the preview
reopens the same way. New chat returns home and clears the selection. The rows' keyboard ring sits inside the row
(the list clips outside it).

## Modes and effort

Modes: **Fast** (fast answers) · **Thinking** (thinks it through) · **Pro** (every model on
your machines) · **Max** (every model, every machine) · **Deep** (keeps going until you stop
it). Effort: **Low · Medium · High · Extra · Ultra**. Bylines read "Concorde Thinking" ("Concorde Thinking · Ultra" at Ultra).

## Footage on WebKit
- Every `<video>` lists the `.mp4` first, then the `.webm` (WKWebView and Safari can freeze a `.webm` on its last frame).
- A loop watchdog checks every 400 ms: a clip stalled within 0.6 s of its end for two checks is sent back to 0 and played.
- The sky draws from its first frame with a one-texel black footage texture; the footage is uploaded only once a frame
  has been decoded (`requestVideoFrameCallback`, else `loadeddata`), and fades in. No stall at the opening.
