# Animation dynamics, easing & timing

How graphics enter, move, and leave — and what makes movement feel alive instead of robotic.

- [Enter / exit](#enter--exit)
- [Easing curves & concrete durations](#easing-curves--concrete-durations)
- [The feel of movement (dynamics)](#the-feel-of-movement-dynamics)
- [The 12 principles, condensed for mograph](#the-12-principles-condensed-for-mograph)
- [Holding to read](#holding-to-read)

## Enter / exit

**The single most important rule: entrance ≠ exit.**

- **Entrance** uses `ease-out` (deceleration) — the element arrives at speed and settles. It can be expressive:
  slide, reveal, focus-pull, scale-up.
- **Exit** uses `ease-in` (acceleration) — starts slow, leaves fast. It is uniform and quick. **The exit is
  always shorter than the entrance**, and elements leave *together*, not staggered.
- **Stagger the entrance in reading order.** Header → subline → accent, ~6–16 frames apart. Reading order =
  animation order. Sequential reveal emphasises hierarchy and stops the viewer feeling dumped on.
- **Animate only with purpose** — state change, emphasis, feedback. Don't animate for liveliness alone.
- **Keep it interruptible.** A graphic should be able to leave mid-entrance cleanly; never lock the viewer into
  waiting for an animation to finish.

## Easing curves & concrete durations

Three curves cover almost everything:

| Curve | a.k.a. | Use for |
|---|---|---|
| `ease-out` (decelerate) | "ease out" | **entrances** — element flies in and settles |
| `ease-in` (accelerate) | "ease in" | **exits** — element starts slow and shoots off |
| `ease-in-out` (standard) | "standard" | **moves within frame** — accelerate then decelerate between two points |

Never use linear — it reads dead. In Remotion: `spring()` for entrances, `Easing.inOut(Easing.cubic)` for moves.

**Durations (starting points, then tune to distance):**
- Small objects (icon, dot, chip): **50–200 ms**
- Medium objects (plate, card, dialog): **250–400 ms**
- Screen-to-screen / large blocks: **300–600 ms**
- Keep most UI-style motion **≤ 0.3–0.4 s** so it feels fast.

**Scale duration to the distance travelled.** A move across the whole frame takes longer than a nudge; matching
duration to distance keeps the *perceived speed* constant across all the motion in a piece.

## The feel of movement (dynamics)

This is what separates a living animation from a mechanical one. It all comes from **spacing** — how far the
thing moves between frames.

- **Spacing.** Even spacing = smooth, steady, mechanical. *Varied* spacing = weight, realism, impact. Spacing
  distribution (ease) is what turns robotic motion into organic motion.
- **Momentum / inertia.** Spacing grows as the object speeds up and shrinks as it slows. That's how the eye
  reads acceleration and deceleration.
- **Weight via timing.** More frames between key poses = heavier, more deliberate. Fewer frames = light, snappy.
  Timing is how you give an object a sense of mass.
- **Overshoot.** The object slightly passes its resting point, then settles back — momentum made visible, adds
  weight and life. *Use with care:* great on sharp, energetic entrances; wrong on calm slides, where an
  invented spring just leaves a hole. Match the overshoot to the energy of the move; if in doubt, don't.
- **Follow-through & overlapping action.** Loose/secondary parts keep moving and catch up after the main mass
  stops — the recovery that lets motion come to rest gradually instead of snapping dead.
- **Secondary action.** A supporting movement layered on the primary one (a shadow shifting, a blick, particles)
  — it enriches, it never competes with or obscures the main action.
- **Anticipation.** A small counter-move before the action (a tiny pull-back before a launch) primes the eye.
- **Arcs.** Move along curves, not straight lines — natural motion travels in arcs.

## The 12 principles, condensed for mograph

Disney's principles still govern motion graphics. The ones that matter most here:

- **Squash & stretch** — subtle scale on impact/launch gives weight and flexibility.
- **Anticipation** — wind-up before action.
- **Staging** — one focus in the frame; never two heroes.
- **Slow in / slow out** — easing; the foundation of believable motion.
- **Follow-through / overlapping** — parts settle at different times.
- **Arcs** — curved paths.
- **Timing** — speed sets weight and meaning.
- **Secondary action** — supporting motion.
- **Appeal** — clean, readable silhouette; if the shape doesn't read, nothing else matters.

## Holding to read

Whatever the motion, the payload has to be readable while it's up. Minimum on-screen ≈ **words × 0.3s + 1s**,
and align the whole entrance/hold/exit to the voiceover line length. Motion that's beautiful but gone before
it's read has failed its one job.
