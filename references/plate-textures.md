# Plate / surface texture catalog

A "plate" is the panel a title/stat/lower-third sits on so it reads over busy footage. Beyond the three you
already use (transparent, matte/solid, blurred), here is the full menu — what each looks like, when it fits,
and a compact CSS/Remotion recipe. All recipes assume a `<div>`/`<AbsoluteFill>` styled element.

- [The surfaces](#the-surfaces)
- [Choosing a surface](#choosing-a-surface)
- [Recipes](#recipes)

## The surfaces

1. **Transparent** — no fill, text only with a shadow for contrast (recipe in `typography-color-safezones.md`).
   Lightest touch; relies on the shadow. Good over calm footage.
2. **Matte / solid** — flat opaque fill (or high-opacity, e.g. 85–100%). Maximum legibility, zero distraction.
   The safe default for dense text or accessibility.
3. **Blur / frosted (glassmorphism)** — semi-transparent fill + backdrop blur + a subtle light border. Footage
   shows through softly; feels light, airy, premium. The card-over-blur look. Needs a *bright/colourful* or busy
   background behind it to read as glass.
4. **Grainy blur** — frosted glass + a fine grain/noise overlay. The signature 2026 texture: soft edges plus
   visible grain feels emotional, tactile, immersive. Warmer and less sterile than clean glass.
5. **Gradient fill** — the plate itself is a (mesh or linear) gradient. Adds energy and brand colour; keep it
   low-contrast under the text or reserve the vivid part for an empty corner.
6. **Gradient border / stroke** — transparent or dark fill with a bright gradient outline. Modern, neon-ish,
   defines the panel edge without a heavy fill. Great on dark backgrounds.
7. **Inner glow / light-emitting stroke** — soft glow on the inside edge or a luminous outline. Keeps a soft
   panel visible in dark/low-light scenes and gives a "neon guide" feel without a solid fill.
8. **Neumorphism / claymorphism** — soft monochrome panel embossed with a light shadow + a dark shadow (clay
   adds an inner glow for a tangible, friendly look). Beautiful but **low contrast — an accessibility trap**;
   use only for decorative chrome, never for the primary readable text on busy footage.
9. **Liquid glass / through-the-glass** — reflective, refractive glass with condensation/highlights; content
   appears behind real-looking glass. The high-end "expensive" overlay. Heavier to produce; use as a hero
   moment, not for every lower-third.
10. **Drop-shadow plate** — a solid/blurred plate floated above the footage with a soft cast shadow for depth.
    The shadow separates plate from background; classic, reliable.
11. **Noise / texture overlay** — any of the above with a subtle noise layer on top to kill banding and add
    tactility. The cheapest way to make a flat plate feel designed.

## Choosing a surface

- **Busy/bright footage behind** → frosted glass or grainy blur (they need texture behind to read), or a solid
  plate if legibility must be guaranteed.
- **Dark scene** → gradient border or inner glow keeps the panel visible without a heavy fill.
- **Calm/emotional scene** → transparent + shadow, or a soft matte; let the footage breathe.
- **Premium brand moment** → grainy blur, liquid glass, or a mesh-gradient fill.
- **Accessibility / lots of text / small screens** → solid matte, high contrast. Avoid neumorphism.
- **Always:** check the plate on the **busiest frame** of the shot. A plate that reads over an empty sky may
  vanish over a face or a window.

## Recipes

Compact, paste-ready. Tune colours/blur to the brand. For Remotion these are just inline styles on a `<div>`.

**Frosted glass (glassmorphism)**
```css
background: rgba(255, 255, 255, 0.12);
backdrop-filter: blur(16px);
-webkit-backdrop-filter: blur(16px);
border: 1px solid rgba(255, 255, 255, 0.22);
border-radius: 20px;
box-shadow: 0 8px 32px rgba(0, 0, 0, 0.25);
```

**Grainy blur** — frosted glass above, plus a noise layer on top:
```css
/* on a child element stretched over the plate, pointer-events:none */
position: absolute; inset: 0; border-radius: inherit; opacity: 0.12;
mix-blend-mode: overlay;
background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
```

**Gradient border / stroke** (dark fill, bright gradient edge):
```css
border-radius: 20px;
background:
  linear-gradient(#0b0b0f, #0b0b0f) padding-box,
  linear-gradient(120deg, #E3010F, #ff7a00) border-box;
border: 2px solid transparent;
```

**Inner glow / light stroke**:
```css
border-radius: 20px;
background: rgba(10, 10, 14, 0.55);
box-shadow: inset 0 0 18px rgba(120, 180, 255, 0.55),
            0 0 12px rgba(120, 180, 255, 0.25);
```

**Neumorphism** (decorative only — low contrast):
```css
background: #e6e7ee; border-radius: 24px;
box-shadow: 8px 8px 16px #c5c6cc, -8px -8px 16px #ffffff;
```

**Drop-shadow plate** (solid panel, floated):
```css
background: rgba(15, 15, 20, 0.9);
border-radius: 18px;
box-shadow: 0 18px 40px rgba(0, 0, 0, 0.45);
```

**Noise overlay** — reuse the `feTurbulence` SVG from grainy blur at low opacity (0.05–0.1) over any plate to
remove banding and add tactility.

> Remotion note: `backdrop-filter` works in the Chromium renderer, so glass/grainy plates render correctly.
> Render plate-only overlays as ProRes 4444 with alpha for the editor (see the `motion` skill §4).
