# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with
shared house machinery (CSS vars, localStorage try/catch +
seed/load/save/reset + toast, canvas draw pipelines, top-level
functions for the stub-DOM harness, `TICK_MS=100` clocks). Harvest
Haunt is the first **rail shooter** in the set: the camera lives on a
moving train and the player aims at pop-up targets instead of driving.
The student picked the **ghost train ride** fantasy with **pan & shoot**
controls and the **autumn harvest** skin (spooky-lite: grinning
pumpkins and clumsy scarecrows, golden dusk, falling leaves).

## Goals / Non-Goals

**Goals**
- Fairground ghost-train joy: the ride does the moving, the player
  does the laughing and the blasting.
- Dead-simple aim loop: pan to find frights, click to splat them,
  chain hits for combo glory.
- "One more ride" pull: finite ride to the barn, score + combo records
  beg for a rematch.
- All art drawn in code: zero images.

**Non-Goals**
- Horror or jump-scare intensity (spooky-lite on purpose).
- Free movement or exploration (`ghost-train-maps` parked for more
  rides and routes).
- Sound (`ghost-train-sounds` parked).
- Unlockable prizes/hats (`ghost-train-carnival` parked).

## Decisions

1. **Single-file `train.html`** with an autumn-harvest remap of the
   CSS vars: `--sky:#2b1636` (dusk plum), `--gold:#ffb13d` (lantern
   gold), `--orange:#ff7a2f`, `--leaf:#e8542f`, `--ink:#2a1408` (warm
   dark brown), `--cream:#ffe9c7`, `--green:#5a7d2a` (corn), chunky
   rounded buttons with 3px outlines and offset hard shadows, warm
   bold font stack `"Trebuchet MS", "Verdana", sans-serif` with heavy
   weights and wide tracking on titles.
2. **The ride** — one `<canvas>` (540×720). World is a long horizontal
   strip; `rideDist` grows `RIDE_SPEED=240` px/s every tick (the train
   moves; scenery slides left). The player can pan the camera
   `panX ∈ [-PAN_MAX, PAN_MAX]` (`PAN_MAX=260`), eased 18%/tick toward
   `panTarget`. Screen x of a world object: `sx = objX - rideDist +
   270 + panX`. The ride is finite: `RIDE_END=21600` world-px (~90 s)
   to the **harvest barn**, then ride-complete.
3. **Pan & shoot** — `pan(dir)` nudges `panTarget += dir * 90`
   (clamped). Arrow keys / A / D and on-screen ◀ ▶ call `pan()`.
   `shoot(x, y)` fires at canvas coordinates: muzzle flash, 250 ms
   cooldown, hit test against frights that are up. Canvas click / tap
   maps event coords through the canvas rect into canvas space; a
   FIRE button fires at the current crosshair (keyboard-friendly).
   `setCrosshair(x, y)` tracks the mouse for the reticle.
4. **Frights** — hash-seeded bands every `BAND_GAP=700` world-px
   (`ensureFrights()` keeps 3 screens ahead, prunes behind). Each
   band spawns 0–2 frights at distinct x offsets with a height slot
   (low `y≈470`, high `y≈330`) and a type:
   `0` crow (1 HP), `1` pumpkin-head (1 HP), `2` ghost-sheet (1 HP),
   `3` scarecrow (2 HP — tough). Lifecycle: `waiting → up (UP_MS=2200)
   → ducking (400 ms) → gone`. Frights rise only when they enter the
   view (`|sx - 270| < 300`); unhit frights duck away and cannot be
   hit after they start ducking.
5. **Hits & combos** — shooting an open fright: `hp--`; at 0 it pops
   (splat float) and banks `score += 100 * comboMult`, then
   `comboMult = min(comboMult + 1, 8)`; `comboMax` tracks the highest
   multiplier that banked. A shot that hits **nothing** resets
   `comboMult = 1` ("the chain drops"). Tough frights show a damaged
   pose after the first hit.
6. **Score & records** — fright points only. `GKEY="ghost-train:v1"`
   holds `{ bestScore, bestCombo }`. Seed `{ bestScore: 0, bestCombo:
   0 }`; corrupt → seed. Each metric updates only when improved;
   either improvement shows the NEW BEST banner. `CLEAR RECORDS`
   resets + toast. Save failures never break play.
7. **Screens** — `screen-ready` (title, rules, START THE RIDE) and
   `screen-over` ("RIDE COMPLETE!", score, pops + best combo of the
   ride, NEW BEST banner, RIDE AGAIN). Enter = start/again. HUD:
   SCORE, COMBO (live multiplier), RIDE (percent to the barn), BEST.
8. **Rendering** — autumn pipeline: dusk sky gradient (plum → gold),
   pale moon with a few blocky crows, distant hills and fence line,
   scrolling corn rows (stacked stalk sprites), hay bales, pumpkins
   and orange-canopy trees at hash positions, drifting leaf particles,
   the wooden train (planked cars with gold trim and window frames
   along the bottom ~150 px), fright sprites (grinning jack-o-lantern
   head, sheet ghost with goofy eyes, patched scarecrow with hat,
   flapping crow) with rise/duck y-offsets, damaged scarecrow pose,
   splat starbursts + floating "+N ×M!" text, gold crosshair reticle
   with a muzzle flash ring, and a big barn silhouette + "THE BARN!"
   text as the ride ends. DOM handles HUD/overlays/buttons.
9. **Verification** — extract inline `<script>` → `node --check`;
    stub-DOM harness (shared localStorage across boots, canvas op
    recorder with gradient stubs, interval capture, direct function
    calls) covering ride progress + fright lifecycle + duck-away,
    pan clamps + keys + buttons, hit + tough two-shot, combo bank +
    cap + miss reset, ride-complete at the barn, records
    better/keep/reload/clear, flow resets, no images; CDP screenshots
    (ready, ride, hit combo, tough scarecrow, ride-complete, phone)
    for visual review.

## Risks / Tradeoffs

- **Pop-up timing vs fairness** — 2.2 s up-windows at 240 px/s ride
  speed keep the aim stress arcade-fair; the harness locks the
  numbers, play feel tunes them later.
- **Combo on miss** — dropping the chain on an empty shot punishes
  spam-clicking and rewards patience; a generous 250 ms cooldown keeps
  rapid legit shooting possible.
- **Rail simplicity** — no fail state, no health: the ride is a
  score chase to the barn, matching the fairground fantasy. If a
  fail-state urge appears later, a "frights escaped" counter can
  motivate a future change.

## Migration Plan

New file `train.html` only; existing apps untouched. README row +
specs bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the three product decisions: ghost
train ride, pan & shoot controls, autumn harvest art )
