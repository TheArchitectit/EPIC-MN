# Tasks

## 1. Build the booth core
- [x] 1.1 Create `beats.html` with the house skeleton (CSS vars,
  `.boardwrap`, canvas + `draw()`/`render()`, `TICK_MS=50` clock,
  toast at `top:100px` inside `.boardwrap`) — verify: `node --check`
  on the extracted script passes and the page boots to the ready
  screen
- [x] 1.2 Paint the CRT synth club (void background, four neon lanes,
  hit line, pads, scanline overlay + flicker, HUD with score/streak/
  crowd/set) — verify: canvas paints with zero image assets (harness
  records fillRect/arc/gradient calls)
- [x] 1.3 Implement the set clock and note travel (120 BPM, 16-bar
  chart, `hitTime` on the song clock, notes ride to the hit line) —
  verify: harness sees notes positioned from the clock and the set
  reach its end

## 2. Beat, streak, and sound
- [x] 2.1 Implement judgment (lane keys D/F/J/K + arrows + pads,
  PERFECT ≤60 ms / HIT ≤120 ms / MISS past, pad flash + judge
  floats) — verify: harness stages a note at each window and sees
  perfect/hit/miss outcomes
- [x] 2.2 Implement streak multiplier and crowd meter (mult up to 4×,
  crowd +4/+2/−8, crowd empty ends the set early, glow rides the
  crowd) — verify: harness chains hits to a ×2 multiplier, misses a
  note into a crowd drop, and empties the crowd into an early end
- [x] 2.3 Implement the synthesized beat (kick/snare/hat/bass from
  the chart, hit blips, silent-safe without audio) — verify: harness
  runs with an AudioContext stub and sees oscillators scheduled, and
  without one and still plays

## 3. Screens and records
- [x] 3.1 Implement the ready/over screens and the full loop (ready →
  set → crowd home or set's over → play again) — verify: harness
  reaches each screen and restarts a fresh set
- [x] 3.2 Implement records (`GKEY="beat-booth:v1"` →
  `{bestScore, bestStreak}`), NEW BEST banner, keep-weaker-no-banner,
  reload persistence, CLEAR RECORDS + toast, save-failure safety —
  verify: harness stages each record scenario and the toast path

## 4. Check and ship
- [x] 4.1 Run the stub-DOM harness over every spec scenario — verify:
  all tests pass (node /tmp/beat-test.js)
- [x] 4.2 Take CDP screenshots (ready, notes riding, perfect hit,
  streak alive, crowd home, phone) and review them — verify: PNGs
  reviewed, any visual bug fixed and re-shot
- [x] 4.3 Update README with the Example #18 run line, serve line,
  table row, and specs bullet — verify: `openspec validate --all` is
  green

## Workflow follow-up
- [x] 5.1 Show the student the finished set and wait for "ship it"
  before `openspec archive beat-booth --yes`
- [x] 5.2 Verify the merged spec at
  `openspec/specs/beat-booth/spec.md` after archiving
