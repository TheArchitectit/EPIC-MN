# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, `flourish()`/`sparkBurst()`, canvas draw pipelines, stub-DOM test
harness). Maze Maker is the first **creator game** in the set — a build
mode and a solve mode in one file — wearing the retro-neon skin the student
picked for arcade-style games.

## Goals / Non-Goals

**Goals**
- Build a playable maze in under a minute: paint walls, drop start/goal,
  scatter treasures, press PLAY.
- Solve it with either input style: arrows/WASD at a desk, clicks on a
  trackpad or touch screen.
- Trustworthy validation: never start a run the player cannot finish.
- Per-maze best runs (time + steps) as the replay hook.
- All neon drawn in code: glowing walls, light-cycle trail, pulsing beacon.

**Non-Goals**
- Maze generation from scratch (`maze-levels` parked for that).
- Sharing mazes between players (`maze-share` parked).
- Sound (`maze-sounds` parked).
- Diagonal movement, enemies, or moving obstacles.

## Decisions

1. **Single-file `maze.html`** in house style: vanilla JS, CSS vars
   (`--ink`, `--pink`, `--cyan`, `--yellow`, `--mint`, `--mono`,
   `--hard:6px 6px 0`) remapped to neon glow values on a deep-indigo page.
2. **Grid model** — 15×15; `walls[y][x]` booleans; single `start`/`goal`
   cells (nullable); `treasures` list capped at 5. Collecting during a run
   mutates a separate `collectedList` so the maze definition stays intact
   and reset-run can restore treasures for free.
3. **Tools** — `state.tool` ∈ wall | erase | start | goal | treasure;
   mousedown/drag paints; wall paint over a treasure removes it; wall
   paint over start/goal is ignored (never bury the specials); start/goal
   and treasure placement refuse wall cells.
4. **Validation** — `validateMaze()` returns a friendly message
   ("PLACE THE BALL START" / "PLACE THE GOAL FLAG" / "NO PATH FROM START
   TO GOAL") or "" when ready; BFS over open cells decides connectivity.
   PLAY shows the message via toast + status line and refuses to switch.
5. **Solve controls** — `moveBall(dx,dy)` one cell per key (arrows/WASD via
   top-level `onKey`); refused walls/edges don't count steps. `clickCell`
   picks the dominant axis (bigger |dx| or |dy|) and takes one step that
   way if open. Both paths funnel through `moveBall` — one movement rule.
6. **Run clock** — 100 ms `setInterval` tick accumulates `elapsedMs` while
   `mode === "solve"` (harness-friendly, deterministic); steps and
   treasures counted live on the HUD.
7. **Win** — entering the goal cell calls `winGame()`: overlay with time,
   steps, treasures, NEW BEST banner(s); best time and best steps stored
   independently (each updates only when better).
8. **Best-run persistence** — `GKEY = "maze-maker:v1"` holding
   `{ bests: { signature: { timeMs, steps } } }`, where the signature is a
   compact string of wall bits + start + goal (so different mazes keep
   their own records). Trim to the 12 most recent signatures to bound
   storage. Corrupt/missing data → seed (empty bests map).
9. **Rendering** — one `<canvas>` (600×600, 40 px cells): deep-indigo fill,
   dim purple grid lines, walls as dark boxes with glowing cyan edges,
   fading cyan→pink trail squares behind the ball, pink light-cycle ball
   with bright core, pulsing yellow goal rings, mint diamond treasures
   with sparkle ticks, `sparkBurst()` particles on collect and win.
   DOM holds the title, tool buttons, HUD (TIME/STEPS/TREASURES/BEST),
   mode buttons (PLAY / RESET RUN / CLEAR BOARD / EDIT), win overlay, and
   toast. `frame` counter drives pulsing/flicker.
10. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness in `vm.runInNewContext` (makeEl, shared localStorage across
    boots, canvas op recorder, interval capture, event-handler capture)
    exercising tools, validation, moves, click-steps, treasures, win,
    bests save/skip/reload, reset-run, clear-records; headless Chromium
    CDP screenshots (build, solve, win) for visual review.

## Risks / Tradeoffs

- **Click-to-step ambiguity** — one-step-toward (dominant axis) is less
  magical than full path-walking but keeps solving a puzzle; arrows remain
  the precise tool. Spec'd explicitly so it's a promise, not an accident.
- **Signature collisions** — wall-bit strings are unique per maze layout,
  so records stay per-maze; 12-entry trim means very old mazes lose records
  first (acceptable for a local showcase).
- **Timer granularity** — 100 ms steps display as `12.3S`; fine for kids'
  arcade scoring and keeps the harness deterministic.
- **Drag-painting on touch** — touchmove maps to the same paint path as
  mouse; click-steering makes solving work by tap alone.

## Migration Plan

New file `maze.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the four product decisions: Maze Maker,
build + solve, arrows + clicks, neon grid art )
