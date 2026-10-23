# Tasks

## 1. Build the cabinet core
- [x] 1.1 Create `candy.html` with the house skeleton (CSS vars,
  `.boardwrap`, canvas + `draw()`/`render()`, `TICK_MS=50` clock,
  toast at `top:100px` inside `.boardwrap`) — verify: `node --check`
  on the extracted script passes and the page boots to the ready
  screen
- [x] 1.2 Paint the candy-80s cabinet (gradient sky, star field,
  pixel mountains, checkered road with gaps, pipes/spikes, blocky
  hero, HUD with score/streak/crowd/stage) — verify: canvas paints
  with zero image assets (harness records fillRect/arc/gradient
  calls)
- [x] 1.3 Implement the run clock and scrolling world (120 BPM,
  32-bar deterministic route, objects ride to the hero on the song
  clock) — verify: harness sees objects positioned from the clock
  and the run reach its end

## 2. Jump, orbs, and groove
- [x] 2.1 One-tap jumping (space/up/W/click/JUMP button, gravity,
  land on ground) and hazard handling (gaps/spikes/pipes clear or
  stumble with mercy) — verify: harness taps mid-run, sees the hero
  airborne, clears a staged hazard, and stumbles into a crowd drop
- [x] 2.2 Pop-up beat-orbs (glow window, vanish ungrabbed, grab =
  bonus + burst + crowd) — verify: harness grabs a staged orb and
  watches an ungrabbed one vanish
- [x] 2.3 On-beat judgment and the dance floor (ON BEAT ≤90 ms /
  CLOSE ≤180 ms / OFF, streak ×mult to 4×, crowd fill/drain, glow
  rides the crowd) — verify: harness stages taps at each window and
  sees streak/mult/crowd move
- [x] 2.4 Synthesized beat (kick/snare/hat/bass, jump/orb/stumble
  blips, silent-safe without audio) — verify: harness runs with an
  AudioContext stub and sees oscillators scheduled, and without one
  and still plays

## 3. Screens and records
- [x] 3.1 Implement the ready/over screens and the full loop (ready
  → run → lights out or cabinet cleared → play again) — verify:
  harness reaches each screen and restarts a fresh run
- [x] 3.2 Implement records (`GKEY="candy-beat:v1"` →
  `{bestScore, bestStreak}`), NEW BEST banner, keep-weaker-no-banner,
  reload persistence, CLEAR RECORDS + toast, save-failure safety —
  verify: harness stages each record scenario and the toast path

## 4. Check and ship
- [x] 4.1 Run the stub-DOM harness over every spec scenario — verify:
  all tests pass (node /tmp/candy-test.js)
- [x] 4.2 Take CDP screenshots (ready, run mid-track, jump + burst,
  orb grab, lights out, phone) and review them — verify: PNGs
  reviewed, any visual bug fixed and re-shot
- [x] 4.3 Update README with the Example #19 run line, serve line,
  table row, and specs bullet — verify: `openspec validate --all` is
  green

## Workflow follow-up
- [x] 5.1 Show the student the finished run and wait for "ship it"
  before `openspec archive candy-beat --yes`
- [x] 5.2 Verify the merged spec at
  `openspec/specs/candy-beat/spec.md` after archiving
