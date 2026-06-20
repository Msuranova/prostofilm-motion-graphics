---
name: prostofilm-motion-graphics
description: >-
  A design rulebook for motion graphics and on-screen infographics — the judgment behind graphics that read in
  two seconds and move with intent. Reach for it whenever you design or critique anything graphical that lives
  in a video frame: infographic layout and visual hierarchy, lower-thirds and titles, plate / card surfaces and
  their textures (frosted glass / glassmorphism, grainy blur, gradient borders, inner glow, neumorphism, liquid
  glass, noise), accent backgrounds (mesh gradients, blobs, grain), the element library (callouts, connectors,
  badges, progress rings, timelines, number counters) and chart-choice rules, animation dynamics and easing
  (enter / exit timing, spacing, momentum, overshoot, kinetic typography, the 12 principles of animation),
  scene transitions and broadcast bumpers / stings / idents, vertical 9:16 reel safe zones, render and delivery
  specs, depth and parallax, motion branding, colour grade and sound. It covers motion design end to end —
  моушн-графика и моушн-дизайн. Trigger it even when the user never says "rules": any "how should this graphic
  look, move, or be laid out" question, or asks about «правила инфографики», «текстуры плашек», «акцентный фон»,
  «элементы инфографики», «анимация инфографики», «переходы / отбивки», «динамика анимации». A rulebook, not a
  build engine — for the Remotion build itself, pair with the `motion` skill.
---

# Motion graphics & infographics — design rulebook (Prosto.Film)

This skill is the **rulebook / reference pack**: how on-screen graphics should be laid out, surfaced,
coloured, animated, and transitioned so they read instantly, move with intent, and stay on-brand.

It is the companion to the `motion` skill. Division of labour:
- **`motion`** = how to *build* it (Remotion/React workflow, rendering, brand loading from the client folder).
- **`prostofilm-motion-graphics`** (this) = how to *decide* it (the design rules across infographics, plates, motion, transitions, type).

Load the relevant reference file(s) below for the task at hand. Apply the universal core on every job.

## Universal core (apply every time)

These are the non-negotiables. Everything in the reference files serves these.

1. **Read instantly.** The viewer can't pause. A graphic must be understood in ~2 seconds. If it needs
   study, it's too dense — split it across beats.
2. **One hero, three levels.** One element carries the message (a number, a name, a verb). Hierarchy has at
   most three tiers: primary (the one thing to remember) → secondary (support) → tertiary (labels/details).
   Make the hero ~2–3× the body. Size + colour + timing carry it, not decoration.
3. **Guide the eye.** Compose on a grid. Place key elements on rule-of-thirds power points or along an
   F-pattern (data-dense) / Z-pattern (narrative). Reading order = animation order.
4. **Stay inside the safe zone.** Text lives in the inner **80%** (title-safe); important visuals in the
   inner **90%** (action-safe). Edges get clipped on real screens.
5. **Restraint over flash.** Motion must have a reason — state change, emphasis, feedback. Decoration that
   doesn't aid comprehension is noise.
6. **Easing always, never linear.** Enter ≠ exit (see `animation-dynamics.md`). Stagger entrances in reading
   order; exit together and faster.
7. **Hold to read.** Minimum time on screen ≈ words × 0.3s + 1s. Match graphic timing to the voiceover line.
8. **Readability is non-negotiable.** Contrast the text against the footage with a plate or a soft shadow,
   and test it on the **busiest frame** of the shot — not an empty one. Aim for ≥ 4.5:1 contrast.
9. **Consistency = brand.** One font system, one accent, one entrance family across a set — it should feel
   like one designed system, not a pile of effects. Brand specifics (fonts/palette/locked decisions) live in
   the client's folder, never hardcoded here — see the `motion` skill §3.

## Reference map — read what the task needs

| Task / question | Read |
|---|---|
| Laying out an infographic, explainer, full-screen data, visual hierarchy, story structure | `references/infographic-layout.md` |
| Picking infographic parts — callouts, connectors, badges, progress, timelines, counters, charts; accent backgrounds | `references/infographic-elements.md` |
| Choosing a plate / card / panel surface beyond transparent-matte-blur (glass, grainy, gradient, glow, noise…) | `references/plate-textures.md` |
| How elements appear/disappear, easing, timing in ms, the feel of movement, the 12 principles | `references/animation-dynamics.md` |
| Scene transitions, bumpers, stings, idents, sweeps, sound sync | `references/transitions-and-bumpers.md` |
| On-screen type, colour ratios, safe zones, caption accessibility, motion-safety (flashing) | `references/typography-color-safezones.md` |
| Output format — vertical 9:16 reel safe zones, aspect ratios, render/delivery specs, broadcast-legal levels, seamless loops | `references/formats-and-delivery.md` |
| Faking depth — parallax, z-depth, 2.5D, camera moves, lighting | `references/depth-and-3d.md` |
| Turning a brand into a motion system — signature movement, consistent DNA across a set | `references/motion-branding.md` |
| Making the graphic live in the finished video — matching the colour grade & grain, sound design for graphics | `references/finishing-grade-and-sound.md` |

Each reference file is self-contained with a short table of contents at the top. When a job spans several
(a typical animated infographic touches layout + elements + plate + animation), read the ones that apply and
synthesise — the universal core keeps them coherent.

## How to use this in practice

- **Designing from scratch:** start with the layout file (hierarchy + grid + story), pick elements + a plate
  surface, then apply the animation file for entrances/exits and the type/colour file for readability.
- **Critiquing an existing graphic:** walk the universal core as a checklist, then drill into the specific
  reference for the weak area (e.g. plate has no contrast → `plate-textures.md`; motion feels robotic →
  `animation-dynamics.md`).
- **Building in Remotion:** decide the design here, then hand off to the `motion` skill for the React/render
  workflow. Concrete CSS/Remotion recipes for the trickier plate surfaces live in `plate-textures.md`.
