# Tasks

## 1. Build the arena core
- [x] 1.1 Create `backyard.html` with the house skeleton (CSS vars,
  `.boardwrap`, canvas + `draw()`/`render()`, `TICK_MS=100` clock,
  toast at `top:100px` inside `.boardwrap`) — verify: `node --check`
  on the extracted script passes and the page boots to the ready screen
- [x] 1.2 Paint the golden-hour arena (grass patches, sun flare,
  pebbles/flowers/twig decor, bottle-cap fort with flag, HUD bar with
  fort hearts/crumbs/wave) — verify: canvas paints with zero image
  assets (harness records fillRect/arc/gradient calls)
- [x] 1.3 Implement hero steering on the fixed arena (arrows/WASD at
  `HERO_SPEED=7` in build and wave phases) — verify: harness holds a
  direction and sees the hero move 7px/tick

## 2. Siege, defenses, and buddies
- [x] 2.1 Implement waves: spawn queue (`4+n*2` bugs, one every 8
  ticks from random edges), bug kinds ant/beetle/fly, bugs march to
  the fort and bite it, wave clear → build phase + crumb bonus +
  `wave++` — verify: harness sees bugs spawn and march, the fort take
  bite damage, and the wave clear into the next build phase
- [x] 2.2 Implement the zap (nearest bug within `70px`, 2 damage,
  6-tick recharge) — verify: harness zaps a staged bug for 2 damage
  and sees the cooldown block a second zap
- [x] 2.3 Implement the three defenses (spike trap / pebble turret /
  stick wall), crumb costs, placement rules at the hero's feet, and
  their auto-attacks — verify: harness places each (crumbs deducted,
  bad spots refused), sees the turret shoot, the trap bite, and the
  wall block and get chewed
- [x] 2.4 Implement stray bugs and tamed buddies (touch to tame, max
  2, follow hero, bite nearby bugs, +1 damage per wave survived) —
  verify: harness rescues a stray and sees the buddy bite a staged bug

## 3. Screens and records
- [x] 3.1 Implement the ready/over screens and the full loop (ready →
  build/wave cycles → fort fell → defend again) — verify: harness
  reaches the over screen at fort hp 0 and restarts a fresh siege
- [x] 3.2 Implement records (`GKEY="backyard-bastion:v1"` →
  `{bestWave, mostBonks}`), NEW BEST banner, keep-weaker-no-banner,
  reload persistence, CLEAR RECORDS + toast, save-failure safety —
  verify: harness stages each record scenario and the toast path

## 4. Check and ship
- [x] 4.1 Run the stub-DOM harness over every spec scenario — verify:
  all tests pass (node /tmp/backyard-test.js)
- [x] 4.2 Take CDP screenshots (ready, build phase with defenses,
  mid-wave combat, buddy rescue, fort fell, phone) and review them —
  verify: PNGs reviewed, any visual bug fixed and re-shot
- [x] 4.3 Update README with the Example #17 run line, serve line,
  table row, and specs bullet — verify: `openspec validate --all` is
  green

## Workflow follow-up
- [x] 5.1 Show the student the finished siege and wait for "ship it"
  before `openspec archive backyard-bastion --yes`
- [x] 5.2 Verify the merged spec at
  `openspec/specs/backyard-bastion/spec.md` after archiving
