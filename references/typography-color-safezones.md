# Typography, colour, safe zones & accessibility

Making on-screen text legible on any screen, for any viewer.

- [Typography for video](#typography-for-video)
- [Colour balance](#colour-balance)
- [Safe zones](#safe-zones)
- [Caption / subtitle accessibility standards](#caption--subtitle-accessibility-standards)
- [Motion safety (flashing)](#motion-safety-flashing)

## Typography for video

- **Clean sans-serif.** Reads at small sizes and over motion. One typeface across the whole piece for cohesion;
  at most three across a system (display + body usually suffices).
- **Understand in two seconds.** Few words, big enough for the smallest target screen (size up for TV).
- **Contrast is mandatory.** White text on a darker base is the reliable default. Where there's no plate, use a
  soft dark shadow (blur ~7px, low alpha) or a frosted/solid plate (see `plate-textures.md`).
- **Test on the busiest frame** of the shot, never an empty one. Legibility that survives a face or a bright
  window survives everything.
- **Animation must not fight legibility** — smooth, restrained moves; nothing that smears or strobes the text.

## Colour balance

- **60 / 30 / 10.** 60% dominant (usually a neutral / the background), 30% secondary, **10% accent**. The accent
  is where the eye goes — CTAs, the hero number, the one highlight. Spread the accent everywhere and you destroy
  the hierarchy it's meant to create.
- **Accent on the hero only.** Colour is a pointer, not wallpaper.
- **Quieter on emotional scenes.** Less saturated colour lets the footage carry the moment.

## Safe zones

Originated with CRT overscan; still essential because phones, tablets, and TVs all crop the edges differently.

- **Title-safe = inner 80%** of the frame. *All* text and critical information lives here, or it risks being
  clipped.
- **Action-safe = inner 90%.** Important visuals and motion stay inside this; only backgrounds bleed to the edge.
- Compose key elements on the **rule-of-thirds** grid inside the safe area — power points, not dead centre.

## Caption / subtitle accessibility standards

The professional broadcast/streaming baseline (BBC, Netflix, EBU R37, WCAG):

- **Contrast.** Minimum **4.5:1** for text (WCAG AA). Large text (≥18 pt) or bold (≥14 pt) may go to **3:1**.
  AAA is 7:1. The Netflix/BBC standard look: white `#FFFFFF` on a semi-transparent black plate
  `rgba(0, 0, 0, 0.75)`.
- **Font.** Sans-serif, always — mandated by BBC/Netflix/EBU caption guidelines for legibility.
- **Width.** Caption block ≤ **68%** of media width on 16:9. Position so it never covers critical visuals.
- **Lines & timing.** No more than ~3 lines at once; keep characters-per-line limited. Captions align exactly to
  the audio and stay up long enough to read comfortably.

These aren't only for the hearing-impaired — the same contrast/size/placement rules make *any* on-screen text
hold up on a phone in daylight, which is most of the audience.

## Motion safety (flashing)

Fast flashing can trigger migraines, nausea, dizziness, and seizures in photosensitive viewers — and just
looks cheap. The standard (WCAG 2.3.1):

- **No more than 3 flashes in any 1-second window.** If something must flash/strobe, keep it under that rate.
- **Saturated red is extra dangerous** — people are more sensitive to red flashing; avoid rapid saturated-red
  flashes entirely.
- **No full-frame strobes.** A large area flashing is worse than a small one. Replace strobe with a soft pulse
  or a glow that ramps rather than snaps.
- **Offer calm by default.** Where a piece reuses across contexts, prefer a reduced-motion version — gentle
  fades over violent flashes. Restraint reads as premium anyway.
