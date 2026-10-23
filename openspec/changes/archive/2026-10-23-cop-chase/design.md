# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with
shared house machinery (CSS vars, localStorage try/catch +
seed/load/save/reset + toast, canvas draw pipelines, top-level
functions for the stub-DOM harness, `TICK_MS=100` clocks). Cop Chase is
the third **runner** geometry in the set (vertical scrolling highway,
pinned hero car — like Neon Delivery and Powder Tricks) but the first
with a **player-driven speed**: gas and brake change how fast the world
closes in, and a pursuit system lives on top. The student picked the
**retro-neon × arcade pixel** fusion: synthwave night colors wearing
blocky pixel cars and CRT scanlines.

## Goals / Non-Goals

**Goals**
- Getaway-driver fantasy from the first tap: gas to fly, brake to
  survive, cops in the mirror.
- One-thumb simple, hard to master: the arcade clock forces pace,
  traffic punishes greed, the cop punishes mistakes.
- Legible pursuit drama: you can SEE the cop gaining and overshooting.
- All art drawn in code: zero images.

**Non-Goals**
- Real car physics, drifting, or gear shifts (`cop-chase-garage`
  parked for upgrades).
- Multiple cities or map variety (`cop-chase-maps` parked).
- Sound (`cop-chase-sirens` parked).
- Multiplayer or online leaderboards.

## Decisions

1. **Single-file `chase.html`** with a neon-pixel remap of the CSS
   vars: `--bg:#120a2e` (deep night), `--road:#1c1140`, `--pink:#ff2e88`,
   `--cyan:#22e6ff`, `--gold:#ffd23f`, `--ink:#0b0620` (outline dark),
   `--green:#3dffa0`, chunky rounded buttons with 3px outlines and
   offset hard shadows, arcade font stack `"Courier New", monospace`
   with heavy weights and wide tracking on titles. CRT scanline overlay
   layered over the whole page (`repeating-linear-gradient` at low
   alpha).
2. **Highway** — one `<canvas>` (540×720), top-down-ish runner view.
   Road spans x=30..510 with 5 lanes (`LANE_W=96`). Night sky gradient +
   pixel stars + neon sun/moon disc; distant blocky skyline; glowing
   cyan/pink edge lines; gold dashed lane markers scrolling with
   `runDist`; shade bands scroll under the cars.
3. **Gas, brake, steering** — `speed` px/s clamped
   `[MIN_SPEED=80, MAX_SPEED=440]`. Per tick (0.1 s): gas → `speed +=
   28`; brake → `speed -= 36`; no input → drag toward `CRUISE=240` at
   4 px/tick. `runDist += speed * 0.1` every tick. `steer(dir)` moves
   `targetLane` ±1 (clamped 0..4); hero x eases 22%/tick toward the
   lane center. Arrow keys / W / S / A / D and on-screen pedals +
   ◀ ▶ all drive the same functions.
4. **Traffic** — hash-seeded bands every `BAND_GAP=260` world-px
   (`ensureTraffic()` keeps ~3 screens ahead, recycles behind). Each
   band: 1–3 cars in distinct lanes (always one free lane), each with a
   civilian speed `[130, 230]` px/s and a candy pixel paint. Cars are
   world-positioned: screen y = `HERO_Y + (carY - runDist)`. Relative
   motion is honest — flooring it makes traffic close faster.
5. **Near-misses** — when a traffic car crosses the hero's row within
   46 px lateral and the hero was not hit, `score += 50` and a floating
   "NEAR MISS +50" text pops. Traffic contact = **crash**: `speed` drops
   to 120, `copGap -= 120` ("the net tightens"), `crashMs = 700` spin
   flash, toast "CRASH!". Crash is on a short cooldown so a wedged car
   cannot multi-hit.
6. **Cops & pursuit** — `copGap` px behind the hero (screen y =
   `HERO_Y + copGap`), starts `500`. Every tick the cop gains ground:
   `copGap -= (4 + 2 * heat)` where `heat = 1 + floor(runDist /
   4000)`. Braking while `copGap < 250` and `overshootCd == 0` triggers
   **overshoot**: `copGap = 420`, `overshootCd = 2500`, score += 100,
   toast "COP OVERSHOOT! +100" — the cop surges past and falls back.
   When `copGap <= 40` the player is **busted**: run over. The cop car
   flashes a red/blue light bar (alternating on `frame`), and at
   `heat >= 3` a second cop joins (drawn at `copGap + 180`, same math
   via `cop2Gap` — busted when either reaches 40).
7. **Arcade clock** — `timeLeft` starts `START_TIME=50` s and counts
   down 0.1 s per tick. Checkpoint gates every
   `CHECKPOINT_DIST=3000` world-px (gold neon arch across the road):
   `timeLeft += 25`, `checkpoints++`, toast "CHECKPOINT! +25s". At
   `timeLeft <= 0` the run ends **OUT OF TIME**. Two end states: BUSTED
   or OUT OF TIME — both record the run.
8. **Score & records** — score grows `floor(speed * 0.02)` per tick
   (distance feel) plus near-miss (+50) and overshoot (+100) bonuses.
   `GKEY="cop-chase:v1"` holds `{ bestScore, bestDist }`. Seed
   `{ bestScore: 0, bestDist: 0 }`; corrupt → seed. Each metric updates
   only when improved; either improvement shows the NEW BEST banner.
   `CLEAR RECORDS` resets + toast. Save failures never break play.
9. **Screens** — `screen-ready` (title, rules, START THE CHASE) and
   `screen-over` ("BUSTED!" or "OUT OF TIME!", score, distance,
   checkpoints, NEW BEST banner, PLAY AGAIN). Enter = start/again. HUD:
   SCORE, TIME (big seconds), SPEED (km/h-flavored `speed/2`), BEST.
10. **Rendering** — neon-pixel pipeline: gradient sky, square pixel
    stars, blocky skyline, glowing road edges and dashed lane markers
    (scroll offset `runDist % 80`), pixel cars (stacked rects: body,
    cabin, windshield, wheels — cyan/pink/gold civilian paints; hero is
    a gold muscle car with pink stripes), cop cars with alternating
    red/blue light-bar blocks and a glow halo, checkpoint arch with
    "CHECKPOINT" pixel text, crash flash overlay, floating bonus text,
    and a full-canvas CRT scanline pass every frame. DOM handles
    HUD/overlays/buttons.
11. **Verification** — extract inline `<script>` → `node --check`;
    stub-DOM harness (shared localStorage across boots, canvas op
    recorder with gradient stubs, interval capture, direct function
    calls) covering gas/brake/clamps, steering + keys + buttons,
    traffic scroll + near-miss + crash, checkpoint bonus, out-of-time,
    cop closing, overshoot, busted, heat second cop, records
    better/keep/reload/clear, flow resets, no images; CDP screenshots
    (ready, chase, overshoot, busted, out-of-time, phone) for visual
    review.

## Risks / Tradeoffs

- **Cop pressure vs fairness** — a flat 4–6 px/tick gain means every
  run eventually ends BUSTED unless checkpoints and overshoots buy
  time; that is the arcade loop (chase high score, not "win"). Harness
  locks the numbers; play feel tunes them later.
- **Gas makes traffic faster** — honest relative motion is the core
  risk/reward: distance (score) vs crash risk. Braking is the defensive
  tool and the overshoot trick in one pedal.
- **Runner reuse** — same scrolling geometry as the previous runners
  keeps the code small and honest; speed control + pursuit + clock are
  what make it a different game, not a skin.

## Migration Plan

New file `chase.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the three product decisions: highway
chase + cops, gas + brake controls, retro-neon × arcade pixel art )
