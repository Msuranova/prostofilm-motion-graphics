# Master prompt — AI ad clip (frame-by-frame, image-to-video)

A block-structured generation prompt that gets a coherent multi-shot ad clip out of an AI video model
(Seedance 2 / Syntx.AI and similar) in one pass. Reverse-engineered from a working commercial
(@mostafa__layegh's "football" ad; 29-post teardown, 2026-07, server `/data/reels-teardown/out/REELS_TEARDOWN.md`).

- [Where it sits in the pipeline](#where-it-sits-in-the-pipeline)
- [Block anatomy — what each block does](#block-anatomy--what-each-block-does)
- [Frame-by-frame craft rules](#frame-by-frame-craft-rules)
- [Fill-in template](#fill-in-template)
- [Full worked example — "football"](#full-worked-example--football)
- [Prohibitions library for the technical tail](#prohibitions-library-for-the-technical-tail)

## Where it sits in the pipeline

1. Character / crowd / location **model sheets** (Midjourney or similar) — one image per identity you must keep.
2. **This master prompt**, one per clip, referencing those sheets as `@image1..N`.
3. Render in **Seedance 2** (via Syntx.AI or directly). Next clip references the previous one in `{CONTINUITY}`.
4. Soundtrack (Suno) and edit on top.

Frame-style + revival prompt library (paper-cut, parallax, motion-graphics-over-own-video):
`~/.claude/skills/image-prompt-builder/references/styles/lib-ai-ads-i2v.md`.
A copy of this template also lives in `video-prompt-builder/references/lib-master-ad-reel.md`.

## Block anatomy — what each block does

Keep the blocks in this order. Every block name in `{CAPS}` on its own line.

| Block | What to write | Why |
|---|---|---|
| `{CONTINUITY}` | Clip 2+: reference the previous clip (`@PrevVideo — DIRECT CONTINUATION`), restate style + atmosphere in one line, state the live situation. | The model has no memory between clips; you are its memory. |
| `{REFERENCES}` | Number every image `@image1..N`. Per image: what it LOCKS (kit, character identity, crowd design, location). Use the words STRICT / ONLY. If a reference has a flaw (e.g. an empty stadium), say explicitly to IGNORE that aspect. | References silently override text; disarm their flaws in writing. |
| `{FORMAT}` | Aspect ratio, total seconds, cut rhythm ("multiple dynamic cuts", a pacing adjective — broadcast-cinematic, fast but readable). | Sets the edit density before any content. |
| `{VISUAL STYLE}` | Name the look + 3–5 concrete texture markers (painterly brush strokes, bold ink-line accents, halftone texture, slight chromatic offset) + a negative anchor ("NOT photorealistic"). | Style words without markers drift toward default photoreal. |
| `{CRITICAL — ...}` | One block per non-negotiable the model tends to break (crowd density, weather, wardrobe). Noun in CAPS in the header. | Promoting a constraint to its own block roughly doubles compliance. |
| `{CRITICAL STAGING}` | Screen direction ("RED attacks LEFT-TO-RIGHT across the ENTIRE sequence"), 180-degree rule, single-object continuity ("one ball, one continuous play"). | Without it every cut re-rolls geography and the action stops reading. |
| `{SHOT LIST}` | Timecoded `{0:00–0:02}` lines. Each line: CAMERA TYPE in caps (WIDE DYNAMIC / TIGHT TRACKING / POV / SIDE ANGLE / MEDIUM / BEHIND-THE-NET / CELEBRATION BEAT) — action — camera movement — background state. | The actual edit. See craft rules below. |
| `{SFX}` | Plain list of diegetic sounds matched to the shots, loudest first. | Seedance renders audio; unspecified = random music. |
| `{TECHNICAL TAIL}` | Hard bans + one-line re-assertions of every CRITICAL block + "Match previous clips' style EXACTLY" + a closing quality line. | The model weighs the end of the prompt heavily; repeat what must not break. |

## Frame-by-frame craft rules

- **One continuous action across all cuts.** Chain the object logically: pass → dribble → flick over tackle → cross → bicycle kick → goal. If you cannot narrate the chain in one sentence, the model can't either.
- **1.2–2 s per shot.** Shorter does not resolve; longer goes mushy. The hero moment gets "slight slow-motion at apex".
- **Direction never flips.** Pick a screen direction in `{CRITICAL STAGING}` and keep it in every shot-list line.
- **Vary shot size every cut** (wide → tight → POV → side → medium) — same size twice in a row reads as a jump cut.
- **Give the hero an emotion beat**, spelled out ("SMILING, pure joy") — otherwise faces default to neutral.
- **End on a reaction, not the action** — celebration / crowd eruption / logo beat sells the payoff.
- **Say critical constraints at least twice** — once in their own block, once in the tail. Single mentions get forgotten.
- **Crowd / background state in every shot line** ("packed stands roaring behind") — backgrounds silently empty out otherwise.

## Fill-in template

```
{CONTINUITY}
@PrevVideo — DIRECT CONTINUATION. Same [стиль] animation, same [грейд], same [атмосфера/локация].
The situation is LIVE: [что происходит прямо сейчас].

{REFERENCES}
@image1 — [СУЩНОСТЬ] model sheet. STRICT [что замораживаем: kit and character identity].
@image2 — [СУЩНОСТЬ] model sheet. STRICT ...
@imageN — [ЛОКАЦИЯ] reference for ARCHITECTURE AND LIGHTING ONLY. [Если в референсе изъян: IGNORE ...]

{FORMAT}
[16:9 / 9:16]. Total [N] seconds. Multiple dynamic cuts. Fast, readable, broadcast-cinematic pacing.

{VISUAL STYLE}
[Название стиля]. [3–5 маркеров текстуры]. Dynamic energetic camera. NOT photorealistic.

{CRITICAL — [ГЛАВНОЕ ТРЕБОВАНИЕ CAPS]}
[Развёрнуто, что обязано быть в каждом кадре и чего быть не должно.]

{CRITICAL STAGING}
[Кто] moves LEFT-TO-RIGHT across the ENTIRE sequence. Screen direction stays coherent across every cut
(180-degree rule). [Объект] continuity is logical: [цепочка действия]. One [объект], one continuous action.

{SHOT LIST — [N] SECONDS}
{0:00–0:0X} [ТИП КАМЕРЫ CAPS] — [действие]. [Движение камеры]. [Состояние фона].
{0:0X–0:0Y} ...
{...–0:0N} [REACTION/CELEBRATION BEAT] — [реакция, а не действие].

{SFX}
[Список диегетических звуков по кадрам, без музыки если её кладёте отдельно.]

{TECHNICAL TAIL}
[Повтор каждого CRITICAL в одну строку.] Keep [направление]. [Идентичности] EXACTLY per @image1/@imageN.
Match previous clips' style EXACTLY. NO eye sparkle. NO glow. NO lens flares. No morphing, no deformation,
no flickering, no extra limbs/fingers, no broken geography. Fast editing but every move readable.
4K cinema [стиль].
```

## Full worked example — "football"

(@mostafa__layegh, Syntx.AI / Seedance 2 — verbatim, keep as the calibration reference.)

```
{CONTINUITY}
@ProvVideo — DIRECT CONTINUATION. Same stylized 2D Spider-Verse-like animation, painterly grade, same
PACKED World Cup final atmosphere. The match is LIVE: red team attacking the green team.

{REFERENCES}
@image1 — RED TEAM model sheet. STRICT kit and character identity for all red players.
@image2 — GREEN TEAM model sheet. STRICT kit and character identity for all green players (defenders +
goalkeeper #1 in dark green/black kit)
@image3 — CROWD/FANS model sheet. Use these fan designs to populate the PACKED stands.
@image4 — PLAYER 42 model sheet. STRICT identity: dark short dreads, earrings, light stubble, tattoo sleeve
on left arm, red/white striped shirt NUMBER 42, red shorts, warm friendly smile.
@image5 — STADIUM reference for ARCHITECTURE AND LIGHTING ONLY. The reference image shows it empty —
IGNORE the emptiness. Final render MUST show this stadium COMPLETELY PACKED with cheering fans.

{FORMAT}
16:9 horizontal. Total 10 seconds. Multiple dynamic cuts. Fast, readable, broadcast-cinematic sports pacing.

{VISUAL STYLE}
Stylized 2D cinematic animation, Spider-Verse / modern feature look. Painterly brush strokes, bold ink-line
accents, halftone texture, slight chromatic offset. Dynamic energetic camera. NOT photorealistic.

{CRITICAL — STADIUM MUST BE FULL}
Every shot shows a COMPLETELY PACKED, SOLD-OUT stadium: all tiers densely filled with tens of thousands of
fans (@Image3 designs), flags, scarves, waving arms. NO empty seats. Crowd reaction VARIED and natural,
NOT synchronized.

{CRITICAL STAGING}
RED team attacks LEFT-TO-RIGHT across the ENTIRE sequence. Ball direction and screen direction stay coherent
across every cut (180-degree rule). Ball continuity is logical: pass to dribble to flick over tackle to cross
to bicycle kick to goal. One ball, one continuous play.

{SHOT LIST — 10 SECONDS}
{0:00–0:02} WIDE DYNAMIC — midfield build-up. A red player receives the ball and fires a sharp forward pass.
Camera drifts laterally. Packed stands roaring behind.
{0:02–0:04} TIGHT TRACKING — a red attacker dribbles past a green defender (@Image2) with a quick feint;
the defender lunges and misses. Camera low, following feet and ball.
{0:04–0:05.2} POV / BALL-RIDE — attacker's POV: flicks ball up and LEAPS over a sliding green tackle.
Camera rides with the ball.
{0:05.2–0:06.8} SIDE ANGLE — wing. A red player whips a fast curling CROSS into the box. Camera pans with
the arcing ball.
{0:06.8–0:08.3} MEDIUM SHOT — PLAYER 42 (@Image4) airborne, perfect BICYCLE KICK while SMILING, pure joy.
Strong silhouette, slight slow-motion at apex, crisp impact.
{0:08.3–0:09.5} BEHIND-THE-NET — green goalkeeper #1 dives but ball slips past, flying TOWARD CAMERA into
the net. Net ripples toward lens. Crowd ERUPTS.
{0:09.5–0:10.0} CELEBRATION BEAT — player 42 wheels away arms wide, teammates sprinting, packed stadium
exploding.

{SFX}
Deafening packed-stadium roar, grass footsteps, sharp ball strikes, tackle swish, whoosh on the bicycle kick,
net ripple, explosive goal cheer.

{TECHNICAL TAIL}
Stadium COMPLETELY PACKED in every shot — NO empty seats, NOT empty like @Image5. Keep red attack
left-to-right. Kits and numbers EXACTLY per @Image1/@Image2/@Image4. Player 42 smiles during the bicycle
kick. Match previous clips' 2D painterly style EXACTLY. NO eye sparkle. NO glow. NO lens flares.
No morphing, no deformation, no flickering, no extra limbs/fingers, no broken geography. Fast editing but
every move readable. 4K cinema stylized 2D animation.
```

## Prohibitions library for the technical tail

Copy the ones that apply; add project-specific ones in the same voice.

- `NO eye sparkle. NO glow. NO lens flares.` — kills the default "AI-pretty" varnish.
- `No morphing, no deformation, no flickering.` — object stability across cuts.
- `No extra limbs, no extra fingers.` — anatomy.
- `No broken geography.` — pairs with the 180-degree rule in `{CRITICAL STAGING}`.
- `NOT photorealistic.` / `NOT [чужой стиль]` — style fencing, keep in `{VISUAL STYLE}` too.
- `Match previous clips' style EXACTLY.` — mandatory on every clip after the first.
- `Fast editing but every move readable.` — pacing guard.
- `NO text, no captions, no watermark.` — when type goes on in the edit, not in generation.
