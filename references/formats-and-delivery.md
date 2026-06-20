# Formats, safe zones & delivery specs

Designing to the right frame, and rendering it so it survives the editor, the platform, and the broadcaster.

- [Aspect ratios](#aspect-ratios)
- [Vertical 9:16 platform safe zones](#vertical-916-platform-safe-zones)
- [Render & delivery specs](#render--delivery-specs)
- [Broadcast-legal levels](#broadcast-legal-levels)
- [Seamless loops](#seamless-loops)

## Aspect ratios

Design to the *delivery* aspect from the first frame — never lay out for 16:9 and crop into 9:16 afterwards,
the hierarchy breaks.

- **16:9** — landscape: TV, YouTube, waiting-room screens, brand reels.
- **9:16** (1080×1920) — vertical feed: Reels, Shorts, TikTok.
- **1:1 / 4:5** — square/portrait social posts.

In a vertical feed the first ~1–2 seconds decide whether the viewer keeps watching — front-load the hook
(the key number/claim) instead of a slow build.

## Vertical 9:16 platform safe zones

In a vertical canvas the platform UI (like/comment/share, caption, username, progress bar, CTA) covers the
edges. Keep text and key content out of these margins or it gets hidden.

Canvas: **1080 × 1920 px**.

| Platform | Keep clear |
|---|---|
| **TikTok** | 108 px top, 320 px bottom, 60 px left, 120 px right |
| **Instagram / FB Reels** | safe area ≈ 1010 × 1280, set 220 px from top, 420 px from bottom (boosted; organic gives a little more) |
| **Universal (all platforms)** | keep crucial content inside a centred **900 × 1400** box; avoid the top and bottom 10% (overlays + device notches) |

Use a transparent safe-zone overlay PNG for the target platform while composing to check nothing important
lands under the UI. For 16:9 broadcast use the title-safe 80% / action-safe 90% rule (see
`typography-color-safezones.md`).

## Render & delivery specs

- **Even dimensions, always.** Render at an even width *and* height. An odd width (e.g. 827) makes DaVinci show
  "Media Offline" on the video while the PCM audio still plays — a silent, confusing failure. Round to an even
  number of pixels.
- **Overlay for the editor:** transparent **ProRes 4444 with alpha** (`--codec=prores --prores-profile=4444
  --pixel-format=yuva444p10le`) so the editor can place it over footage; plus a burned-in preview on the real
  shot so they see the intent.
- **Match the frame rate** of the target timeline exactly (24 / 25 / 30…). A mismatch judders the motion.
- **Match the colour space** (Rec.709 for HD) and keep graphics broadcast-legal (below).

## Broadcast-legal levels

Computer graphics default to full-range RGB; broadcast wants video range. If it goes to TV — or just to look
right — keep levels legal:

- **8-bit video range: black = 16, white = 235.** Keep luma ≤ 100 IRE. Clip super-whites/sub-blacks on the
  master.
- **Back off pure white for text.** `#FFFFFF` at full level is "super-white" (~109%); it looks harsh on TV,
  causes aliasing/buzzing on edges, and reads like a sticker pasted on top. Drop titles to roughly `#F0F0F0`
  (or pull the level back in the scopes) — it looks cleaner and sits in the image.
- Same logic for pure black — a hair above 0 reads better than crushed black.

## Seamless loops

For brand reels, ambient/waiting-room screens, and animated presentations that play on repeat, the loop must
be invisible:

- **First frame state == last frame state.** Design the motion to return exactly to where it started.
- No element mid-transition at the loop point; nothing snaps or jumps on the wrap.
- Test by playing the render twice back-to-back and watching the seam. If you can spot the restart, it's not
  done.
