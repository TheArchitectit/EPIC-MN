# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, canvas draw pipelines, top-level functions for the stub-DOM
harness, `TICK_MS=100` clocks). Neon Delivery is the first **runner**
in the set — auto-run steering, a wobbly delivery box, escalating night
traffic — wearing the retro-neon skin the student picked (synthwave
highway, glowing traffic streaks). It draws on the crossing-game joy the
student loves while inventing its own identity: no instant death, the
pizza is the life bar.

## Goals / Non-Goals

**Goals**
- One-thumb runner feel: the hero runs, the player only steers, and the
  pizza turns every graze into a drama.
- Readable neon chaos: traffic streaks, headlight beams, and a pizza
  wobble you can feel.
- "One more block" pull: deliveries bank tips, each block gets meaner,
  best score + best deliveries beg for a rematch.
- All art drawn in code: zero images.

**Non-Goals**
- Grid-by-grid hopping or stop-and-go crossing (that's the classic we're
  deliberately not cloning).
- Multiple foods, power-ups, or traffic laws (`neon-toppings` parked).
- Sound (`neon-sound` parked).
- Extra biomes (`neon-city-tour` parked).
- Pause or tilt controls.

## Decisions

1. **Single-file `neon.html`** with a retro-neon remap of the CSS vars:
   `--bg:#12081f` (deep purple night), `--road:#1c1230`, `--cyan:#39e6ff`,
   `--pink:#ff4fd8`, `--gold:#ffd166`, `--green:#59ffa1`, `--ink:#f4eeff`,
   font stack `"Lucida Console", "Courier New", monospace`, neon glow via
   `text-shadow`/`box-shadow` (`0 0 12px <color>`), buttons look like
   glowing arcade levers.
2. **Highway** — one `<canvas>` (540×720), top-down runner view scrolling
   down as the hero runs up. Road spans x=30..510 with 5 lanes
   (`LANE_W=96`), cyan neon edge lines, gold dashed lane markers whose
   offset scrolls with `runDist`. Skyline strip + stars at the top of the
   canvas.
3. **Auto-run steering** — `RUN_PX_S=260` forward scroll (world px/s),
   hero pinned at `HERO_Y=560`, hero x eases toward the target lane
   center (`steer(dir)` moves `targetLane` ±1, clamped 0..4). Arrow keys
   / A / D / on-screen ◀ ▶ buttons all call `steer()`.
4. **Traffic bands** — bands every `BAND_GAP=130` world-px; each band has
   a direction (±1), speed `140 + hash*140` px/s scaled up per block, and
   a repeating vehicle pattern (gaps 220–380 px, occasionally a semi of
   length 180 vs car 92). Bands stream across the road and recycle ahead
   of the hero. Density knob: gaps shrink by `12*block` px per block.
5. **The delivery box** — pizza state: `slide` (-1..1 position on the
   box), `integrity` (1 → 0). A graze (vehicle box overlapping hero box
   within the hit window) applies `slide += dir*0.38`, `integrity -=
   0.14`, 600 ms bump cooldown, spark burst + flash. While unbumped,
   `slide` eases toward 0 by 0.01/tick and integrity holds. **Run over**
   when `|slide| >= 1` or `integrity <= 0`. No instant death — the pizza
   is the life bar, which is what makes it ours.
6. **Blocks, deliveries, score** — block length `BLOCK_DIST=1700`
   world-px. Reaching the block's neon "customer arch" counts a delivery:
   `deliveries++`, `score += 100 + round(integrity*100)` (the tip), toast
   "DELIVERY MADE! +N". Next block: scroll speed `260 + 18*block`, band
   gaps shrink. HUD shows SCORE, DELIVERIES, PIZZA bar, BLOCK, BEST.
7. **Records** — `GKEY="neon-delivery:v1"` holding `{ bestScore,
   bestDeliveries }`. Seed `{ bestScore: 0, bestDeliveries: 0 }`; corrupt
   → seed. Each metric updates only when improved; either improvement
   shows the NEW BEST banner. `CLEAR RECORDS` button resets + toast.
   Save failures never break play.
8. **Screens** — `screen-ready` (title, rules, START THE RUN) and
   `screen-over` (RUN OVER!, score, deliveries, NEW BEST banner, PLAY
   AGAIN). Enter = start/again.
9. **Rendering** — synthwave palette: purple sky gradient, neon skyline
   silhouettes, scrolling road dashes, vehicles as glow-rounded rects
   with headlight streaks ahead and tail-light streaks behind (per
   direction), hero as a neon hover-skater with the pizza box balanced on
   top (pizza circle slides and tilts with `slide`), customer arch at the
   block end, spark bursts on bump, `frame` counter pulses the glow.
   Everything in the `draw()` pipeline; DOM handles HUD/overlays.
10. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness (shared localStorage across boots, canvas op recorder,
    interval capture, direct function calls) covering auto-run, steering,
    bumps, recentering, pizza-lost, deliveries, escalation, records
    better/keep/reload/clear, flow resets, no images; CDP screenshots
    (ready, mid-run, delivery, run-over, phone) for visual review.

## Risks / Tradeoffs

- **Runner fairness** — band patterns must always leave a survivable
  gap; the harness proves mechanics, but screenshot review + the 600 ms
  bump cooldown keep the feel forgiving. Constant soup tuned in one place.
- **Lane-steer vs free-move** — lane steering keeps collisions simple and
  thumb-precise; free x-movement would feel floatier and test messier.
- **No death except the pizza** — one rule ("keep it aboard") does the
  work of lives, health, and fail states together; easy to read at a
  glance during a frantic run.

## Migration Plan

New file `neon.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the three product decisions: delivery-dash
twist, auto-run steering, retro-neon night art )
