# Infographic element library & accent backgrounds

The parts you assemble an infographic from, when to use each, and the backgrounds that sit behind them.

- [Element catalog](#element-catalog)
- [Charts — choosing & rules](#charts--choosing--rules)
- [Accent backgrounds](#accent-backgrounds)

## Element catalog

Pick the element that matches the *kind* of information, not the one that looks coolest.

- **Callouts / speech bubbles** — pin a short annotation to a point. Use for a popup explanation or a single
  highlighted fact. Keep the text to a few words; the callout is a pointer, not a paragraph.
- **Icons** — compress a concept into one glyph. Must be from one consistent system (one style, one stroke
  weight, one grid — see the icon rules below). Icons label and speed reading; they don't decorate.
- **Connectors / arrows / arcs** — show sequence, flow, or cause→effect between elements. Animate them
  *drawing on* in reading order so the relationship reveals itself.
- **Badges / chips / tags** — small labelled containers for a status, category, or rank. Good for "NEW",
  a percentage, a step number.
- **Progress bars** — linear fill for "how much / how far". Drive the fill with a single variable and animate
  it filling, not popping in full.
- **Circular progress rings** — percentage of a whole where the circular format reads naturally (scores,
  shares, completion). Animate the sweep.
- **Timelines** — a central line connecting points in time. Bold the year/name of each event, add a small icon
  per point, reveal points sequentially along the line.
- **Number counters** — a value that ticks up to its target. The motion *is* the emphasis; pair with a label.
  Hold on the final number long enough to read.

### Icon-system rules (consistency is the whole game)

- **One pixel grid for all** (24×24 is the industry default; it scales cleanly to 48/72/96 with no blur).
- **One style** — outline OR filled, never a mix.
- **One stroke weight, one corner radius, one set of proportions.** Every icon should carry the same visual
  weight; none should look heavier or lighter than its neighbours. A single icon must not mix stroke weights.
- **Document the set** — categories, naming, when to use which. A shared visual language is read faster.

## Charts — choosing & rules

The most common chart types in infographics are **pie, bar, column, and line**. Choosing well matters more
than styling.

- **No 3D. Ever.** 3D pies/bars distort proportion through perspective and break the link between a datapoint
  and the size that represents it. 2D only.
- **Pie: ≤ 5–6 slices.** Beyond that it's unreadable. Often a **horizontal bar chart, sorted greatest→least**,
  communicates the same comparison far more clearly — reach for it before a pie.
- **Label directly.** Put labels on the slice/bar, not in a legend off to the side; the eye shouldn't ping-pong.
- **Contrasting colours** so every segment is distinguishable.
- **No decoration** — no shadows, no exploded slices, no gradients that obscure the value. The shape *is* the data.
- **Animate to reveal, not to dazzle.** Bars grow, lines draw on, pies sweep — sequentially, so the viewer follows.

## Accent backgrounds

The surface *behind* the content. In 2025–2026 the dominant looks:

- **Mesh gradients** — multiple colour points blending organically in 2D, almost liquid. The signature premium
  background; works across many brands. Keep it soft so foreground text stays readable.
- **Bold multi-colour gradients** — vibrant, unexpected colour pairings for depth and energy. Strong as a hero
  background; dial saturation down where text sits.
- **Blobs / organic shapes** — imperfect, soft, often gently moving. Modern and friendly; good for separating
  zones without hard boxes.
- **Shape-blur gradients** — soft shapes with heavy blur creating smooth colour fields (the "Apple-style"
  background). Premium, calm, lets foreground breathe.
- **Geometric patterns** — grids, lines, dots. Signal order and tidiness; good structural backing for
  data-heavy frames. Keep them low-contrast so they don't fight the content.
- **Grain / noise overlay** — a very subtle noise texture over a gradient breaks up the smoothness and adds an
  emotional, tactile, "expensive" feel. Just enough to texture, never enough to distract (see `plate-textures.md`
  for the recipe — it's the same noise technique used on plates).

**Rule for all of them:** the background serves the content. If it competes with the text for attention, mute
it — lower contrast, add blur, or drop a plate between background and text.
