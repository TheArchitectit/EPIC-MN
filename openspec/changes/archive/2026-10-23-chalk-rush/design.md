# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, canvas draw pipelines, top-level functions for the stub-DOM
harness, `TICK_MS=100` clocks). Chalk Rush is the first **real-time
strategy** game in the set — economy, armies, a rival general — wearing
the chalk war-room skin the student picked (chalkboard green, chalk
strokes, wooden levers).

## Goals / Non-Goals

**Goals**
- A full RTS loop in one thumb: hire workers → energy rolls in → hatch
  soldiers → pull RUSH → smash their castle.
- Auto-battle that reads clearly: chalk stamps march, meet, scribble-
  fight, and siege.
- A rival general that escalates pressure without unfair spikes.
- Records that make "one more battle" irresistible (best win time + streak).
- All art drawn in code on the board: no images.

**Non-Goals**
- Map control, fog of war, tech trees, or multiple unit types (3 levers
  only — `chalk-campaign`/`chalk-skirmish` parked for depth).
- Sound (`chalk-sounds` parked).
- Pathfinding beyond a single battle lane.
- Pause or speed controls.

## Decisions

1. **Single-file `chalk.html`** with a chalk remap of the CSS vars:
   `--ink:#e8e6d5` (chalk white), `--board:#2e4739` (dusty green),
   `--wood:#8a5a33`, `--red:#d97b6c` (red chalk, enemy), `--gold:#d9b441`,
   `--mono` → handwriting stack (`"Segoe Print", "Bradley Hand", "Comic
   Sans MS", cursive`), `--hard:4px 4px 0 rgba(0,0,0,0.35)`. Buttons look
   like wooden levers (wood fill, inset highlight, chunky caps).
2. **Battlefield** — one `<canvas>` (900×420). Player castle at x=70,
   enemy castle at x=830, units walk the lane between them. Castles:
   chalk-stroke battlement shapes with HP bars (green → red chalk).
3. **Economy** — `TICK_MS=100`; each worker adds `WORKER_RATE=2` energy
   per second (0.2 per tick). Prices: `WORKER_COST=25`, `SOLDIER_COST=50`.
   Start: 50 energy, 3 workers, 0 soldiers (enemy mirror). Purchases the
   player can't afford show "NEED MORE ENERGY!" via toast + status and
   change nothing.
4. **Units** — `{ side: "p"|"e", x, hp, atk, cool }`; soldier: hp 30,
   atk 6, cooldown 0.5 s, speed 42 px/s. Spawn at x=120 (player) / x=780
   (enemy). Workers are economy stamps that stay near their castle (drawn
   bobbing at the base; they never fight).
5. **Auto-battle** — each tick every soldier: (a) nearest enemy soldier
   within `FIGHT_RANGE=64` → stop, trade hits on cooldown; (b) else if
   within 36 px of the enemy castle → siege hits on cooldown; (c) else
   march toward it. Dead units (hp ≤ 0) leave in a dust puff. Castles
   also fire a chalk arrow every 1 s at the nearest enemy soldier within
   130 px for 5 damage (turtling is survivable, not free).
6. **RUSH lever** — `RUSH_MS=5000` surge: friendly soldiers get speed ×1.8
   and damage ×1.5; a big chalk arrow sweeps the board while it lasts.
   `RUSH_CD=15000` cooldown after the surge ends; the lever shows
   "RUSHING..." / "RUSH (12s)" / "RUSH!".
7. **Rival general** — every `AI_PERIOD=2500` ms the enemy spends energy:
   hire a worker when under `4 + floor(elapsedMs/30000)` workers and
   affordable, else hatch soldiers (1, or 2 when sitting on 120+ energy).
   Enemy income also creeps up: rate ×(1 + elapsedMs/90000). Readable
   ramp, no spikes.
8. **Win / lose** — castle HP `CASTLE_HP=600` each. Enemy castle 0 →
   victory screen (win time, streak, NEW BEST if the time or streak
   improved); player castle 0 → defeat screen (streak resets to 0).
   `state.result` carries the summary to the overlay.
9. **Records** — `GKEY="chalk-rush:v1"` holding `{ bestWinMs, bestStreak }`.
   Seed `{ bestWinMs: null, bestStreak: 0 }`; corrupt → seed. `CLEAR
   RECORDS` button resets + toast. Save failures never break play.
10. **Rendering** — chalkboard fill with faint grid smudges, hand-drawn
    wobble lines for castles, stick-stamp soldiers (circle head, body
    line, side chalk color: player gold-white, enemy red), fight
    scribbles (short random strokes at contact points), marching dust
    dots under moving units, RUSH arrow (dashed chalk arrow + glow), HP
    bars, wooden DOM levers. `frame` counter wobbles the chalk lines.
11. **Controls** — DOM levers + keyboard: W hire, S hatch, R rush, Enter
    start/again. All handlers top-level for the harness.
12. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness (shared localStorage across boots, canvas op recorder,
    interval capture, direct function calls) covering income, purchases,
    refusals, march/fight/siege/death, rush boost + cooldown, enemy AI
    ramp, victory/defeat, best save/skip/reload/clear, flow resets; CDP
    screenshots (ready, mid-battle, victory) for visual review.

## Risks / Tradeoffs

- **Balance by feel** — constants chosen so an unattended player loses in
  ~2–3 min and a rushing player can win in ~90 s; the harness verifies
  mechanics, not fun; screenshots + playtest tune the knobs.
- **Single lane** — no flanking keeps the read simple (it's the point of
  "fun and simple"); two lanes would fit later as `chalk-skirmish`.
- **Auto-battle agency** — the player's levers are the strategy (economy
  vs army vs RUSH timing); units handle tactics. Matches the student's
  "buttons + auto-battle" pick.

## Migration Plan

New file `chalk.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the four product decisions: RTS
gather-and-rush, buttons + auto-battle, chalk war-room art )
