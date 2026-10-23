# Tasks

## 1. Build the glass world
- [x] 1.1 Create `sunstone.html` with the house skeleton (CSS vars,
  `.boardwrap`, canvas + `draw()`/`render()`, `TICK_MS=50` clock,
  toast at `top:100px` inside `.boardwrap`, `unlockAudio()`) —
  verify: `node --check` on the extracted script passes and the page
  boots to the ready screen
- [x] 1.2 Paint the stained-glass world (jewel floor panels with
  leading, golden light shafts, trees/walls, HUD with hearts/score/
  time/quest line) — verify: canvas paints with zero image assets
  (harness records fillRect/stroke/gradient calls)
- [x] 1.3 Implement the two hard-coded maps and hero movement
  (held keys + on-screen pad, AABB wall collision, scene swap at the
  ruin arch) — verify: harness walks the hero into a wall (blocked),
  across the map, and through the arch into the dungeon

## 2. Fight and quest
- [x] 2.1 Sword swinging (space/X/click/SWORD, facing arc, cooldown,
  knockback) and monsters (deterministic patrols, chase radius,
  1–2 HP) — verify: harness swings into a slime and sees hp drop,
  knockback, and the burst on defeat
- [x] 2.2 Hearts and mercy (contact damage, 1.2 s flash, "the light
  faded" at zero) — verify: harness stages a hit, a mercy window,
  and a final-heart death
- [x] 2.3 The quest (chest → key, locked golden door, Sunstone win)
  and the phase-aware quest line — verify: harness cracks the chest,
  bounces off the locked door, opens it with the key, and claims the
  relic
- [x] 2.4 Sound (unlock on first input, swing/hit/pickup/door/hurt/
  win blips, silent-safe) — verify: harness sees `resume()` after a
  gesture and oscillators on each action, and the no-audio run
  still plays

## 3. Screens and records
- [x] 3.1 Implement the ready/over screens and the full loop (ready
  → quest → won/faded → play again) — verify: harness reaches each
  screen and restarts a fresh quest
- [x] 3.2 Implement records (`GKEY="sunstone-vale:v1"` →
  `{bestScore, bestTime}`), NEW BEST banner, keep-weaker-no-banner,
  reload persistence, CLEAR RECORDS + toast, save-failure safety —
  verify: harness stages each record scenario and the toast path

## 4. Check and ship
- [x] 4.1 Run the stub-DOM harness over every spec scenario —
  verify: all tests pass (node /tmp/sunstone-test.js)
- [x] 4.2 Take CDP screenshots (ready, overworld fight, sword hit,
  key moment, dungeon door/relic, win screen, phone) and review
  them — verify: PNGs reviewed, any visual bug fixed and re-shot
- [x] 4.3 Update README with the Example #20 run line, serve line,
  table row, and specs bullet — verify: `openspec validate --all` is
  green

## Workflow follow-up
- [x] 5.1 Show the student the finished quest and wait for "ship
  it" before `openspec archive sunstone-vale --yes`
- [x] 5.2 Verify the merged spec at
  `openspec/specs/sunstone-vale/spec.md` after archiving
