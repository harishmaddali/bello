# bello~

Hand-drawn loading animations for thoughtful products.

Thirty sketchy, ink-and-paper loaders — the kind you show while your product is writing, thinking,
or brewing something for the user. Each one is a **single self-contained `.svg` file**: animation,
easing, and reduced-motion handling baked in. No JavaScript, no CSS file, no dependencies.

**Demo:** open [`index.html`](index.html) (serve the folder for the copy buttons to work).
The header has six selectable themes — Moss, Ember, Indigo, Plum, Slate and a dark Midnight —
which restyle the page and every loader live, since all color is CSS variables:

```sh
python3 -m http.server 4173   # then visit http://localhost:4173
```

## The set

| File | Loader | Caption it pairs with | Good for |
| --- | --- | --- | --- |
| [`loaders/quill.svg`](loaders/quill.svg) | Quill | "Writing your draft…" | text generation |
| [`loaders/note.svg`](loaders/note.svg) | Note | "Sketching your post…" | composing documents |
| [`loaders/typing.svg`](loaders/typing.svg) | Typing | "Thinking it through…" | chat / assistant replies |
| [`loaders/highlight.svg`](loaders/highlight.svg) | Highlight | "Polishing your words…" | editing, rewriting |
| [`loaders/loop.svg`](loaders/loop.svg) | Loop | "Pulling it together…" | generic busy spinner |
| [`loaders/brew.svg`](loaders/brew.svg) | Brew | "Steeping ideas…" | long-running jobs |
| [`loaders/sparkle.svg`](loaders/sparkle.svg) | Sparkle | "Adding the magic…" | AI enhancement |
| [`loaders/progress.svg`](loaders/progress.svg) | Progress | "Inking it in…" | determinate-ish progress |
| [`loaders/plane.svg`](loaders/plane.svg) | Plane | "Sending it off…" | submitting, publishing |
| [`loaders/check.svg`](loaders/check.svg) | Check | "And… done." | success states |
| [`loaders/search.svg`](loaders/search.svg) | Search | "Looking it up…" | search, retrieval |
| [`loaders/eraser.svg`](loaders/eraser.svg) | Eraser | "Tidying it up…" | cleanup, revisions |
| [`loaders/bulb.svg`](loaders/bulb.svg) | Bulb | "Having an idea…" | brainstorming |
| [`loaders/clock.svg`](loaders/clock.svg) | Clock | "Any moment now…" | queued / waiting |
| [`loaders/gears.svg`](loaders/gears.svg) | Gears | "Turning the gears…" | heavy processing |
| [`loaders/waveform.svg`](loaders/waveform.svg) | Waveform | "Listening closely…" | voice, transcription |
| [`loaders/cloud.svg`](loaders/cloud.svg) | Cloud | "Tucking it away…" | saving, syncing |
| [`loaders/sprout.svg`](loaders/sprout.svg) | Sprout | "Growing the idea…" | drafts taking shape |
| [`loaders/stack.svg`](loaders/stack.svg) | Stack | "Gathering sources…" | research, aggregation |
| [`loaders/signal.svg`](loaders/signal.svg) | Signal | "Reaching the model…" | API / network calls |
| [`loaders/scissors.svg`](loaders/scissors.svg) | Scissors | "Trimming it down…" | summarizing, condensing |
| [`loaders/envelope.svg`](loaders/envelope.svg) | Envelope | "Sealing it up…" | sending, sharing |
| [`loaders/dice.svg`](loaders/dice.svg) | Dice | "Rolling the options…" | sampling, brainstorming |
| [`loaders/compass.svg`](loaders/compass.svg) | Compass | "Finding the way…" | planning, routing |
| [`loaders/boat.svg`](loaders/boat.svg) | Boat | "Sailing along…" | steady background work |
| [`loaders/hourglass.svg`](loaders/hourglass.svg) | Hourglass | "Counting the grains…" | queued / long waits |
| [`loaders/constellation.svg`](loaders/constellation.svg) | Constellation | "Connecting the dots…" | linking ideas, graphs |
| [`loaders/thread.svg`](loaders/thread.svg) | Thread | "Untangling the thread…" | debugging, resolving |
| [`loaders/footprints.svg`](loaders/footprints.svg) | Footprints | "Step by step…" | agent steps, multi-stage runs |
| [`loaders/mountain.svg`](loaders/mountain.svg) | Mountain | "Almost at the top…" | finishing long jobs |

## Use

**As an image** — simplest, fully isolated:

```html
<img src="loaders/quill.svg" width="120" height="120" alt="Writing your draft…">
```

**Inline** — paste the file's markup into your HTML/JSX to theme it. Colors are CSS custom
properties with the defaults built in:

```css
.my-loader {
  --bello-ink: #1E2A21;       /* line work */
  --bello-accent: #3E7B4F;    /* the leaf-green pop */
  --bello-highlight: #C7E0C3; /* marker swipe */
  --bello-paper: #FCFEFA;     /* fills (note page, plane body) */
}
```

Class names are prefixed per loader (`q-`, `n-`, `t-`, …), so multiple loaders inlined on one
page won't collide. Size with `width`/`height` or CSS — everything is stroke-based on a
`120×120` viewBox and scales cleanly.

## Details

- **Reduced motion:** the CSS-driven loaders render their finished, static frame under
  `prefers-reduced-motion: reduce`. Quill, Plane and Mountain animate via SMIL (for perfect
  motion-along-path); pause them with `svg.pauseAnimations()` if you need to.
- **`<img>` vs inline:** Chromium only advances an SVG image's internal animation clock while
  the image is painted on screen. For a loader that's shown when it's needed, that's fine —
  but if you need animation state to survive off-screen scrolling, inline the SVG (the demo
  page does).
- **Accessibility:** every file carries `role="img"` and an `aria-label`; when used decoratively
  next to a visible caption, add `aria-hidden="true"`.
- **The look:** wobbly paths, round caps, a touch of "line boil" (Note and Progress redraw their
  outlines a few times a second, like a pencil test).

MIT — see [LICENSE](LICENSE).
