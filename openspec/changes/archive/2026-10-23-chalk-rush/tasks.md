# Tasks

## 1. Scaffold (`chalk.html` skeleton)

- [x] 1.1 Create `chalk.html` with chalk war-room CSS vars (board/wood remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/won/lost overlays, wooden levers (hire/hatch/rush), HUD (energy, workers, soldiers, time), clear-records — verify: harness can flip ready → playing → won → again

## 2. Economy

- [x] 2.1 Worker income ticks energy up each second, faster with more workers — verify: tests step the clock and see energy rise with 0/3/5 workers
- [x] 2.2 Hire/hatch spend energy and spawn stamps; unaffordable purchases refuse with a message — verify: tests cover an affordable buy, a refusal, and button disable states

## 3. Battle

- [x] 3.1 Soldiers march, fight nearby enemies, siege the castle, and die into dust — verify: tests cover a fight, a siege hit, and a unit removed at 0 hp
- [x] 3.2 RUSH boosts friendly speed and damage, then rests on a visible cooldown — verify: tests measure faster travel and extra damage during the surge, then the cooldown
- [x] 3.3 Rival general gains energy, hires workers, and hatches soldiers with a rising cap — verify: tests see the enemy grow over stepped time

## 4. Scoring & presentation

- [x] 4.1 Victory when the enemy castle falls, defeat when yours falls; best time + streak save only when better, survive reload, clear-records toast — verify: tests cover win, loss, new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas chalk pipeline: board, castles, stamps, fight scribbles, dust, RUSH arrow, HP bars — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, mid-battle, victory) and review them — verify: PNGs show the chalk war-room look with readable HUD

## Workflow follow-up

- Update README with `chalk-rush` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
