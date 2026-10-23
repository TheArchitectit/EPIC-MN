# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, canvas draw pipelines, top-level functions for the stub-DOM
harness, `TICK_MS=100` clocks). Powder Tricks is the second **runner**
geometry in the set (auto-descend + steering, like Neon Delivery) but
the first **sports trick** game: ramps, air combos, and slapstick
tumbles, wearing the **cartoon snow** skin the student picked (puffy
hills, squishy pines, bold outlines). Classic snowboard games get the
joy; the physics and menus stay out.

## Goals / Non-Goals

**Goals**
- One-thumb trick riding: carve the line, pop the ramp, spam TRICK in
  the air, stick the landing.
- Legible risk/reward: 1–3 tricks bank safely, 4+ is showy and ends in a
  comedy tumble — plus trees that punish sloppy lines.
- "One more run" pull: combo multiplier climbs, score explodes, three
  tumbles and it's over. Best score + best combo beg for a rematch.
- All art drawn in code: zero images.

**Non-Goals**
- Real snowboard physics, grinds, or rails (`powder-mountain` parked for
  jump parks and slopes).
- Sound (`powder-sounds` parked).
- Unlockable gear (`powder-gear` parked).
- Multiplayer, ghosts, or leaderboards.

## Decisions

1. **Single-file `snow.html`** with a cartoon-snow remap of the CSS vars:
   `--sky:#8fd6ff` (light blue day), `--snow:#ffffff`, `--snow2:#cfe9ff`
   (shadow blue), `--ink:#1e3a5f` (bold outline navy), `--pink:#ff6b9d`,
   `--gold:#ffc93c`, `--green:#3cb878`, chunky rounded buttons with
   3px navy outlines and offset hard shadows (`4px 4px 0 var(--ink)`),
   playful font stack `"Trebuchet MS", "Verdana", sans-serif` with heavy
   weights and wide tracking on titles.
2. **Mountain** — one `<canvas>` (540×720), top-down-ish runner view
   scrolling down as the rider descends. Slope spans x=30..510 with 5
   lanes (`LANE_W=96`). Sky: blue gradient + cartoon sun (circle + ray
   triangles) + puffy cloud blobs; scrolling puffy hill bumps along the
   slope edges; snow surface white with pale-blue shading bands whose
   offset scrolls with `runDist`.
3. **Carve & pop riding** — `runSpeed()` = `min(420, 300 + floor(runDist
   / 3000) * 15)` px/s (steepens every 3000 px). Rider pinned at
   `HERO_Y=560`; `steer(dir)` moves `targetLane` ±1 (clamped 0..4);
   hero x eases 25%/tick toward the lane center. Arrow keys / A / D and
   on-screen ◀ ▶ all call `steer()`.
4. **Pop & air** — `pop()` (Space / W / ArrowUp / TRICK button): on the
   ground it starts a jump — `airTicks = HOP_TICKS=10` (1.0 s), or
   `RAMP_TICKS=22` (2.2 s big air) when a ramp row is within the launch
   window (`|rowY - runDist| < 50` and within one lane width of the
   rider). While `airTicks > 0`, each extra `pop()` adds a trick: count
   1 → GRAB +100, 2 → FLIP +200, 3 → SPIN +300, 4+ → MEGA +400 each
   (air points = `100*count` per trick, cumulative `airPoints +=
   100*trickCount`). Trick pulls are ignored while grounded (beyond the
   initial pop) and while tumbling.
5. **Landings** — when `airTicks` hits 0: if `trickCount >= 4` the
   landing is an **over-rotated tumble** ("TOO SHOWY!"); else if
   `airPoints > 0` the landing is **clean**: `score += airPoints *
   comboMult`, `comboMult = min(comboMult + 1, 8)`, tracking
   `comboMax`; toast "CLEAN LANDING! ×N". A landing with zero tricks is
   a plain ride-away.
6. **Hazards & tumbles** — rows of pine trees scatter the slope; a tree
   overlapping the rider (window `|rowY - runDist| < 36`) causes a
   **tumble**: unbanked `airPoints` lost, `comboMult = 1`, `tumbles++`,
   `tumbleMs = 900` spin-lock (steering/tricks ignored), dizzy stars
   drawn around the rider. Over-rotation landing also counts as a
   tumble. Third tumble (`MAX_TUMBLES=3`) → run over.
7. **Terrain rows** — objects every `ROW_GAP=220` world-px, hash-seeded:
   ~25% ramp row (one candy-striped ramp in a random lane), ~45% tree
   row (1–2 pines in distinct lanes), ~30% open breather. Never more
   than 2 obstacles per row — the slope always has a safe line. Rows
   recycle ahead as `runDist` grows (`ensureRows()`).
8. **Score & records** — trick points only (banked on landings).
   `GKEY="powder-tricks:v1"` holds `{ bestScore, bestCombo }` where
   `bestCombo` is the highest multiplier reached in a run. Seed
   `{ bestScore: 0, bestCombo: 0 }`; corrupt → seed. Each metric updates
   only when improved; either improvement shows the NEW BEST banner.
   `CLEAR RECORDS` resets + toast. Save failures never break play.
9. **Screens** — `screen-ready` (title, rules, START THE RUN) and
   `screen-over` (RUN OVER!, score, best combo reached, tumble count,
   NEW BEST banner, PLAY AGAIN). Enter = start/again. HUD: SCORE, COMBO
   (live multiplier), TUMBLES (x/3), BEST.
10. **Rendering** — cartoon pipeline: sun + clouds + puffy edge hills,
    white slope with scrolling pale-blue shade bands, candy-striped
    ramps (pink/white diagonal stripes, navy outline), squishy pines
    (stacked rounded triangles, green + white snow cap, squash bob via
    `frame`), bold-outlined rider (round head, candy jacket color,
    striped board; airborne pose tilts the board with `trickCount`;
    tumble pose spins with `tumbleMs` and orbiting dizzy stars), snow
    spray particles while carving, floating "+P ×N!" text on banked
    landings. DOM handles HUD/overlays/buttons.
11. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness (shared localStorage across boots, canvas op recorder,
    interval capture, direct function calls) covering auto-descend,
    carving, steepening, pop/ramp air, trick stacking, clean bank +
    combo growth, over-rotation, tree tumble, third-tumble run-over,
    records better/keep/reload/clear, flow resets, no images; CDP
    screenshots (ready, mid-run, big air, tumble, run-over, phone) for
    visual review.

## Risks / Tradeoffs

- **Trick spam vs skill** — flat per-trick growth (100·n) rewards
  stacking but the 4-trick tumble cap keeps greed honest; harness
  locks the numbers, play feel tunes them later if needed.
- **Deterministic rows** — hash-seeded terrain makes every run's shape
  reproducible (great for tests and fair retries); variety comes from
  lane choices and speed, not randomness.
- **Runner reuse** — same auto-descend geometry as Neon Delivery keeps
  the code honest and small; the trick system and terrain are what make
  it a different game, not a skin.

## Migration Plan

New file `snow.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the three product decisions: trick & air,
carve & pop controls, cartoon snow art )
