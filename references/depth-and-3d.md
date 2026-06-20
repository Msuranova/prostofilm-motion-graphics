# Depth & 3D for video graphics

Making a flat graphic feel three-dimensional — usually with 2.5D/parallax, not real 3D.

- [Parallax — the core depth trick](#parallax--the-core-depth-trick)
- [Z-depth & layering (2.5D)](#z-depth--layering-25d)
- [Camera moves](#camera-moves)
- [Lighting & shadow](#lighting--shadow)
- [Keep depth from hurting the read](#keep-depth-from-hurting-the-read)

## Parallax — the core depth trick

Depth comes for free when foreground and background layers move at **different speeds**: near objects move
faster than far ones as the camera moves, and the brain reads that as space. You rarely need true 3D — layered
parallax sells it.

Three kinds, by how the camera moves:
- **Lateral parallax** — side-to-side camera move; layers slide at different horizontal speeds.
- **Forward parallax** — push *into* the scene along the z-axis; near layers grow faster, the frame opens up.
- **Rotational parallax** — orbit/arc around the subject; the strongest depth cue, but the hardest to fake
  cleanly from flat art.

## Z-depth & layering (2.5D)

- Separate the scene into **layers by distance** from camera (foreground / subject / mid / background).
- Move each layer at a rate matched to its distance — closer = faster.
- From a single still you can build a **2.5D** move: use a depth map to cut the image into distance layers and
  animate each at its own rate, simulating a camera move from one flat frame.
- A little separation goes a long way; you don't need many layers, you need the *right* speed ratios.

## Camera moves

- Animate the camera (or the layer offsets) with **eased** keyframes — the camera obeys the same slow-in/out
  rules as everything else; a linear camera move feels robotic.
- Keep camera moves slow and motivated. A drift or a gentle push adds life; a swooping move distracts from the
  message.
- Closer layers lead, distant layers lag — that lag *is* the depth.

## Lighting & shadow

- A subtle key light + a **contact/floor shadow** under a hero object grounds it and reads as real depth (the
  "product/part on a photo: drop-in + floor shadow" treatment).
- Soft shadows and a hair of gradient on surfaces imply volume without modelling anything.
- Light direction should agree across all elements in the frame — mismatched light kills the illusion instantly.

## Keep depth from hurting the read

Depth is *ambience*; the message stays legible. Don't tumble or perspective-skew the text so far it's hard to
read — keep hero copy on a flat, front-facing, readable plane and let the depth live in the background and the
supporting elements. Subtle beats showy: the goal is "this feels three-dimensional," not "look, it's 3D."
