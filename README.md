# bello~

Hand-drawn loading animations for thoughtful products.

Ten sketchy, ink-and-paper loaders — the kind you show while your product is writing, thinking,
or brewing something for the user. Each one is a **single self-contained `.svg` file**: animation,
easing, and reduced-motion handling baked in. No JavaScript, no CSS file, no dependencies.

**Demo:** open [`index.html`](index.html) (serve the folder for the copy buttons to work):

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

## Use

**As an image** — simplest, fully isolated:

```html
<img src="loaders/quill.svg" width="120" height="120" alt="Writing your draft…">
```

**Inline** — paste the file's markup into your HTML/JSX to theme it. Colors are CSS custom
properties with the defaults built in:

```css
.my-loader {
  --bello-ink: #211E1B;       /* line work */
  --bello-accent: #C4502C;    /* the burnt-orange pop */
  --bello-highlight: #F3BFA9; /* marker swipe */
  --bello-paper: #FFFEFA;     /* fills (note page, plane body) */
}
```

Class names are prefixed per loader (`q-`, `n-`, `t-`, …), so multiple loaders inlined on one
page won't collide. Size with `width`/`height` or CSS — everything is stroke-based on a
`120×120` viewBox and scales cleanly.

## Details

- **Reduced motion:** the CSS-driven loaders render their finished, static frame under
  `prefers-reduced-motion: reduce`. Quill and Plane animate via SMIL (for perfect
  motion-along-path); pause them with `svg.pauseAnimations()` if you need to.
- **Accessibility:** every file carries `role="img"` and an `aria-label`; when used decoratively
  next to a visible caption, add `aria-hidden="true"`.
- **The look:** wobbly paths, round caps, a touch of "line boil" (Note and Progress redraw their
  outlines a few times a second, like a pencil test).

MIT — see [LICENSE](LICENSE).
