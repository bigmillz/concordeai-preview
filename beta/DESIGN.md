# ConcordeAI 7.0 — Balance and Sting, the quiet version

The tokens behind `beta/index.html`, written so the app can take the same values exactly.
Balanced is the default effects level; Full is opt-in; Calm is the stillest. Everything
below is design, not effect: it applies in every level.

## Type

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
- Space Grotesk at 500 with −0.03em is the display voice; 600 only in Full's glowing greeting.

## Colour

Type is white or near-white. Colour appears only in light: the sky, the dies, the Ultra
rim, the horizon, the ember at decisions.

| Token | Value | Contrast on `--night` | Role |
|---|---|---|---|
| `--night` | `#070b1c` | | the ground |
| `--indigo` | `#0d1434` | | the stage gradient's middle |
| `--ink` | `#f4f5fa` | 18.0 | primary type |
| `--read` | `#e8ebf5` | 16.1 | answer prose |
| `--ink2` | `#c6cde0` | 12.3 | secondary type, placeholders |
| `--ink3` | `#9aa6c6` | 8.1 | tertiary type, labels (6.7 on the lightest glass) |
| `--ember` | `#e8415a` | 5.0 (navy on ember 5.0) | the one accent: send strike, send key with text, keyboard focus ring, errors |
| `--ice` | `#9fc0ff` | | light only (the die for Cloud, the writing star's warmth) |
| `--rose` | `#f2a6b4` | | light only (horizon, Ultra rim) |
| `--champagne` | `#f1dcb2` | | light only (horizon, focused composer's top light) |

Hairlines are champagne silver, never pure white:

| Token | Value | Role |
|---|---|---|
| `--hair` | `rgba(241,230,206,.09)` | the faintest rule (table rows, folded panel) |
| `--hair2` | `rgba(241,230,206,.15)` | borders of controls, panels, chips |
| `--line` | `rgba(243,235,216,.32)` | the beam, the send key's outline, a focused composer |
| `--spec` | `rgba(255,250,240,.12)` | the 1 px specular along the top of every glass |

The horizon: a flat band low in the sky, `linear-gradient(180deg, transparent 52%,
rose .11 at 86%, champagne .17 at 100%)`, screen-blended, opacity .62 on the home, .3 in a
chat and in Calm. Flat on purpose: no dome, no arc, no limb anywhere (the NASA clips are
cropped to their horizon-free band; the moonlight is an edgeless corner glow).

## Glass

One material everywhere (composer, sidebar, menus, popovers, tooltips):

```
background: linear-gradient(180deg, rgba(255,255,255,.065), rgba(255,255,255,.03))   /* --glass */
            (menus and popovers add rgba(10,14,32,.78) beneath: --glass-dense)
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

Strokes: 1 px hairlines, 1.5 px icon strokes, 1.5 px rim. The diamond is 8 px square
turned 45°, 1 px white; it fills white while dragged and at Ultra.

## Spacing

An 8 px grid: 8 / 16 / 24 / 32 / 40 / 64. Header 64. Controls 36 (32 under 600). Rows 32.
Pills 32. Sidebar 248 wide, 8 px padding, 16 from the edge, 72 from the top, 16 above the
credit. Home column 800; chat column 640. The composer's centre sits at the golden point
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
Keyboard focus is a 1 px ember hairline; on the slider it hugs the beam with rounded ends
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

### The Ultra moment
Once per arrival at Ultra, about 900 ms, in Full and Balanced:
- 0 ms: the diamond ignites — white core, a bloom `0 0 6px 2px #fff, 0 0 22px 8px
  violet .75, 0 0 44px 16px rose .45` at 18 %, gone by 900 ms. ULTRA is lit (a white text
  glow that settles in 900 ms).
- While at Ultra, the one approved loop on text: the label's gradient
  `linear-gradient(90deg, #cfe0ff, #b9a8ff, #f2a6b4, #e8415a, #f1dcb2, #cfe0ff)` at
  `background-size: 300%` flows across the letters, one cycle in 3.5 s, linear, crisp
  letters, no blur; the diamond carries a faint 7 px glow of the same hue in step
  (`diamondFlow`, 3.5 s). It stops the instant Ultra is left. Calm and reduced motion keep
  the still gradient. The rim stays still.
- 0–160 ms: a 22 px spark runs from the diamond back along the beam to its start.
- 160–760 ms: a line of light leaves the beam's start and runs all the way round the
  composer's border (a conic reveal from that point's angle, `cubic-bezier(.45,0,.2,1)`),
  a white head at its edge; the border settles into a still 1.5 px spectral rim:
  `conic-gradient(from a0, #cfe0ff, #b9a8ff 28%, #f2a6b4 56%, #e8415a 78%, #cfe0ff)` at .9.
  No rotation, no loop.
- The aurora takes one breath: +.45 peaking at about 200 ms, settled within 2 s.
- Leaving Ultra: the rim drains back along the same path in 300 ms `--inout`; the diamond
  and the label return to plain.
- Calm and reduced motion: the still rim (a 300 ms fade in Calm) and the label only.

## Modes and effort

Modes: **Fast** (fast answers) · **Thinking** (thinks it through) · **Pro** (every model on
your machines) · **Max** (every model, every machine) · **Deep** (keeps going until you stop
it). Effort: **Low · Medium · High · Extra · Ultra**. Bylines read "Concorde Thinking".
