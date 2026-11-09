# ConcordeAI 7.0 — Balance and Sting, the quiet version

The tokens behind `beta/index.html`, written so the app can take the same values exactly.
Balanced is the default effects level; Full is opt-in; Calm is the stillest. Everything
below is design, not effect: it applies in every level.

## Type

The wordmark (Michroma, which has one weight) is set lighter: `letter-spacing: .2em` (was .15), 10 px in the
header (was 10.5) and `clamp(24px, 3.1vw, 40px)` in the opening (was 26–44); "AI" keeps a fake bold of
`-webkit-text-stroke: .055em` (was .12), so it stays a little bolder than CONCORDE; the wing's lines are 1.1 (was 1.5).


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
  one box in every mode, crisp `#f8faff`, no text shadow.

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

Strokes: 1 px hairlines, 1.5 px icon strokes, 1.5 px rim. The chosen mode in the mode menu wears a 5 px white
diamond; the effort slider's knob is a round orb (see The effort slider).

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
A 20 px pill, a segmented control in Gemini's luminous language (one `<input type=range>` on top for the hit area).

| Part | Value |
|---|---|
| Size | PINNED ("slightly slimmer", superseding the earlier 26 px): 220 × 36 (hit), pill `--ph: 20px`; in a conversation 200 wide, `--ph: 16px`; under 600 px 88 × 32, `--ph: 20px`. The level sits beside it |
| Channel | `linear-gradient(180deg, rgba(255,255,255,.05), rgba(255,255,255,.085))`, inset 1 px `rgba(255,255,255,.08)`, inset `0 1px 2px rgba(0,0,0,.25)` |
| Fill | from the left to round the orb: `linear-gradient(90deg, #4f8cff, #9b72ff 55%, #f07aa6)` fixed to the track (each step has its own colour); 1 px inner top light |
| Bloom | a copy of the fill beneath it, `blur(8px)`, opacity by step `.32 / .40 / .50 / .62 / .78` |
| Notches | five 3 px dots on the centre line: `rgba(255,255,255,.22)`; passed ones `.85` with a 4 px glow |
| Orb | `--ob: 16px` (12 in a conversation, 16 on a phone), near-white `radial-gradient(110% 90% at 50% 25%, #fff, #f4f7ff 45%, #dde5fa)`, 1 px `rgba(255,255,255,.95)` edge, shadow `0 1px 2px rgba(4,8,30,.45), 0 2px 6px rgba(4,8,30,.35)`; hover 1.05, held 1.10 |
| Halo | 2 × the orb, the fill's colour where it stands (`#4f8cff`, `#6f80ff`, `#9b72ff`, `#c776d2`, `#f07aa6`), opacity .45 at scale .85; hover .70 / 1.05; held .85 / 1.22; 300 ms `--out`; never a loop |
| Snap | 160 ms `cubic-bezier(.22,1,.36,1)`, no bounce |
| Tip | glass above the orb while hovered, held or stepped with keys (1.4 s): the step in `--ink` 500, then one honest line in `--ink3` 12 px; a 1 px blue → violet → rose edge at .55 and `0 0 18px -4px rgba(155,114,255,.35)` |
| Level | beside it, Space Grotesk 13/500 `--ink2`, 4 px off the pill: Low · Medium · High · Extra · Ultra |

The tip's lines (the app's NOTES 6b534): Low "one pass, no second look"; Medium "the usual second pass"; High "always a
second pass, drafts double-checked"; Extra "the models review each other"; Ultra "all of that, with deeper reasoning".
Click anywhere to jump, arrows step. Calm and reduced motion: the same look, no transitions.

### Ultra's light (the cool palette)
Electric blue `#4f8cff` → violet `#9b72ff` → soft rose `#f07aa6`, with white highlights; warm gold `#f3d27a` only as a
rare glint (one sparkle in twelve). No green, orange or red. Text tints that pass AA on the glass: `#86b0ff`,
`#b9a2ff`, `#f7a3c3`.

- **The label and the byline:** "Ultra" in the text tints with a white-blue highlight band (`rgba(240,246,255,.95)`,
  20 % of a 250 % background) that glides across once every 2.5 s (across in about 1.1 s on
  `cubic-bezier(.45,0,.25,1)`, then rest), `drop-shadow(0 0 6px rgba(155,114,255,.4))`. The byline reads
  "Concorde Thinking · Ultra"; its sweep stops when the answer lands (a still gradient).
- **The typed words:** a mirror over the textarea carries the same light in near-white tints (`#dbe6ff`, `#e4dcff`,
  `#f8dde9`), a subtler sweep every 3.6 s; "Ask anything" at .72. Leaving Ultra crossfades back to white in 600 ms.
- **The send key** (with text): `#6f9bff → #9b72ff → #f07aa6 → #fff → #9b72ff`, flowing one 108 px period per 4 s; navy arrow.
- **The writing star:** a 20 px tail behind it, rose → violet → blue → `#e6efff` at the star.
- **The sparkles:** four-point stars, a white core (2 px; 3 px for the big ones) with two crossed 1 px rays tinted
  white, ice `#cfe0ff`, `#86b0ff`, `#b9a2ff`, `#9b72ff` (gold one in twelve).

### The Ultra moment
Arriving (about 1.5 s), Balanced and Full:
- **The beat** (under 1.2 s): 0 ms the orb clicks into place (scale 1 → 1.12 → 1, 220 ms) as the first star wave and
  the sweep leave; +200 ms the second star wave and the sky's glint flash; +400 ms the lit glass edge comes up (the
  line of light runs round in 600 ms); +600 ms the ULTRA label's light sweep starts and the chip's badge appears.
- **The stars lead.** Two waves of four-point stars burst from where the orb lands (80 in all). The first, 56: 5 hero
  stars (11–14 px rays), the rest 4–8 px, each twinkling twice (opacity 1 → .45 → .95 → .35 → 0, scale with it) as it
  flies 26–72 px and fades in 760–1040 ms on `--out`, seven of them drifting up across the composer (70–150 px,
  1.3–1.7 s). The second, 200 ms later: 24 smaller ones (3–6 px), 18–46 px. Above the glass, clipped to the screen;
  compositor work only (transform and opacity on pooled-size elements).
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

Leaving Ultra, the power-down: the accent drains back in 800 ms, the drifting stars drift 24 px up and fade (800 ms),
the sky eases back to the chosen level (time constant .3 s, about 900 ms) and its twist springs back; the rim drains
back the way it came; tints, line, glow and knob fade in 900 ms.

Calm and reduced motion: the still rim, the still gradient label and a brighter still sky (stars 30 % brighter,
exposure 8 % up) only.

### The sideways lock
No layer may widen the page. The colour wash (12 % past each side) and the aurora band live in a clipped layer
(`#decor`, `overflow:clip`); the stage itself is `overflow:clip` (it cannot be scrolled by focus, find-in-page or a
selection drag, which is how the page once slid sideways at 2000 px); a guard returns any window or stage scroll to 0;
the conversation scrolls vertically only. Checked: `scrollWidth === innerWidth` at 2000, 1440, 1280 and 390 through
the opening, the menus, Ultra, a slider drag and typing.

## Modes and effort

Modes: **Fast** (fast answers) · **Thinking** (thinks it through) · **Pro** (every model on
your machines) · **Max** (every model, every machine) · **Deep** (keeps going until you stop
it). Effort: **Low · Medium · High · Extra · Ultra**. Bylines read "Concorde Thinking" ("Concorde Thinking · Ultra" at Ultra).

## Footage on WebKit
- Every `<video>` lists the `.mp4` first, then the `.webm` (WKWebView and Safari can freeze a `.webm` on its last frame).
- A loop watchdog checks every 400 ms: a clip stalled within 0.6 s of its end for two checks is sent back to 0 and played.
- The sky draws from its first frame with a one-texel black footage texture; the footage is uploaded only once a frame
  has been decoded (`requestVideoFrameCallback`, else `loadeddata`), and fades in. No stall at the opening.
