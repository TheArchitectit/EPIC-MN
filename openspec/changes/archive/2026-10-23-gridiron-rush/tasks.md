# Tasks

## 1. Build the match core
- [x] 1.1 Create `football.html` with the house skeleton (CSS vars,
  `.boardwrap`, canvas + `draw()`/`render()`, `TICK_MS=100` clock,
  toast at top inside `.boardwrap`) — verify: `node --check` on the
  extracted script passes and the page boots to the ready screen
- [x] 1.2 Implement the field world and camera (100 yards at
  `y=300..3300`, end zones, yard lines, hashes, goal posts, `camY`
  easing) — verify: canvas paints turf/stripes/lines with zero image
  assets (harness records fillRect/arc calls)
- [x] 1.3 Implement the match state: 4 quarters × `QUARTER_TICKS=240`,
  clock ticks only while live, touchdown = +7 with possession flip to
  own 20, final whistle → result screen — verify: harness ticks the
  clock during play, scores a TD, and sees the over screen at clock 0

## 2. Offense and defense
- [x] 2.1 Implement the snap, carrier steering, and juke
  (`JUKE_MULT=1.5`, `JUKE_TICKS=8`, `JUKE_CD=20`, halved tackle radius
  while juking) — verify: harness holds a direction and sees the
  carrier move at 7px/tick, and a juke raises speed and shrinks the
  tackle radius for 8 ticks
- [x] 2.2 Implement throws to WR1/WR2/WR3 (8-tick pass flight with
  lead, 32px catch check, interception on a crowded arrival) and
  control hand-off to the receiver — verify: harness throws to an open
  receiver, sees a completion, and controls the receiver afterward;
  a staged crowded throw intercepts
- [x] 2.3 Implement tackles, downs, and turnovers (gain ≥10 resets,
  `down>4` turns the ball over) — verify: harness ends a play at a
  tackle spot, sees yards counted, and sees a turnover on the 4th-down
  failure
- [x] 2.4 Implement defense: steer the star defender among 4 chasing
  teammates, CPU carrier seek, tackle ends the Stampede play — verify:
  harness steers the star into the carrier and the play ends

## 3. Plays, presentation, and records
- [x] 3.1 Implement the play pick (RUN / QUICK PASS / DEEP BOMB =
  keys 1/2/3, pick-and-snap) and the DEFEND! prompt between defensive
  series — verify: harness picks each play and the snap starts
- [x] 3.2 Paint the gridiron-classic look (turf stripes, chalk lines,
  painted end zones with team names, gold goal posts, chunky helmeted
  sprites, classic scoreboard) — verify: `node --check` passes and
  screenshots show the classic gridiron with readable sprites
- [x] 3.3 Implement records (`GKEY="gridiron-rush:v1"` →
  `{bestMargin, mostTDs}`), NEW BEST banner, keep-weaker-no-banner,
  reload persistence, CLEAR RECORDS + toast, save-failure safety —
  verify: harness stages each record scenario and the toast path

## 4. Check and ship
- [x] 4.1 Run the stub-DOM harness over every spec scenario — verify:
  all tests pass (node /tmp/football-test.js)
- [x] 4.2 Take CDP screenshots (ready, mid-play, throw/catch, tackle
  or touchdown, final whistle, phone) and review them — verify: PNGs
  reviewed, any visual bug fixed and re-shot
- [x] 4.3 Update README with the Example #16 run line, serve line,
  table row, and specs bullet — verify: `openspec validate --all` is
  green

## Workflow follow-up
- [x] 5.1 Show the student the finished match and wait for "ship it"
  before `openspec archive gridiron-rush --yes`
- [x] 5.2 Verify the merged spec at
  `openspec/specs/gridiron-rush/spec.md` after archiving
