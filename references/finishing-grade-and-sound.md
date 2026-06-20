# Finishing — sitting graphics in the grade & sound

Two things that make a graphic feel *part of the video* instead of pasted on top: matching the picture, and
giving the motion sound.

- [Graphics in the colour grade](#graphics-in-the-colour-grade)
- [Sound design for graphics](#sound-design-for-graphics)

## Graphics in the colour grade

Clean computer graphics dropped onto graded footage look stuck-on — too sharp, too pure, too bright. Tie them
into the image:

- **Don't use pure white/black.** `#FFFFFF` is super-white: it buzzes, aliases, and screams "sticker." Back
  titles off to ~`#F0F0F0` and lift pure black a hair (see `formats-and-delivery.md` for the level detail).
  Graded footage has no true 0/255 — your graphics shouldn't either.
- **Match grain.** Film/graded footage carries grain or noise; pristine vector graphics don't, so they float.
  Lay a **matching grain/noise pass over the graphics** (or a single global grain pass on top of the whole
  composite) so everything shares one texture. Real grain is exposure-dependent — heavier in mids, finer in
  highlights — so match it by luminance, not as a flat layer.
- **Nudge toward the scene.** A pure saturated brand colour can clash with a warm/cool grade. Letting a hair of
  the scene's contrast/tint touch the graphic helps it belong — without losing brand recognition.
- **Bind it to the plate.** Subtle blend modes (overlay/screen for glows), a soft contact shadow, and slight
  edge feather connect the graphic to what's beneath it rather than hovering over it.

## Sound design for graphics

Motion without sound feels dead; a synced sound makes a move feel physical. Sound is half of a good graphic hit.

- **Build a sound palette.** Pick **6–12 recurring SFX** + a couple of music beds and reuse them — a sonic
  identity that parallels the visual consistency. Random one-off sounds feel as messy as random fonts.
- **Hit durations.** Short, punchy hits **30–150 ms** for transitions, counters, and UI-style pops; layered
  **risers/whooshes** for scene changes and big reveals.
- **Whoosh tells a story.** A whoosh implies weight, velocity, and material — a slow gritty whoosh reads
  industrial; a bright short one reads techy/screen-activating. Match the sound's character to the motion's.
- **Sync to the frame.** Land the audio accent on the exact frame of the visual hit. A sound a few frames off
  feels broken even if the viewer can't say why.
- **Make room for the voice.** Duck music under voiceover (sidechain or manual gain) and low-cut the music
  ~120–200 Hz so the VO stays clear.
- **Use silence.** A beat of quiet before a big hit makes it land harder. Not every element needs a sound —
  over-sounding is as tiring as over-animating.
