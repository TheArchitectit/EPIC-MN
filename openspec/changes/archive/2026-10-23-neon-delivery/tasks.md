# Tasks

## 1. Scaffold (`neon.html` skeleton)

- [x] 1.1 Create `neon.html` with retro-neon CSS vars (bg/cyan/pink/gold glow remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/over overlays, glowing steer buttons (◀ ▶), HUD (score, deliveries, pizza, block, best), clear-records — verify: harness can flip ready → running → over → again

## 2. Run mechanics

- [x] 2.1 Auto-run scroll and lane steering — verify: tests see the hero run with no input, and steer() move the hero toward the neighboring lane from keys and buttons
- [x] 2.2 Neon traffic bands stream in both directions and escalate per block — verify: tests see vehicles moving, and later blocks run faster with tighter gaps

## 3. The delivery box

- [x] 3.1 Bumps slide the pizza and dent integrity; ruin at slide ±1 or integrity 0 — verify: tests cover a graze moving slide, and both ruin paths ending the run
- [x] 3.2 Clean running recenters the pizza, deliveries bank the tip — verify: tests see slide ease back toward 0 and a block completion add bonus + tip to the score

## 4. Scoring & presentation

- [x] 4.1 Run-over summary and records: best score + best deliveries save only when improved, survive reload, clear-records toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas neon pipeline: sky, skyline, road dashes, glow vehicles, head/tail streaks, hero + pizza box, customer arch, bump sparks — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, mid-run, delivery, run-over, phone) and review them — verify: PNGs show the neon night look with readable HUD and a visible wobble pizza

## Workflow follow-up

- Update README with `neon-delivery` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
