# Tasks

## 1. Scaffold (`train.html` skeleton)

- [x] 1.1 Create `train.html` with autumn-harvest CSS vars (dusk/gold/leaf remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/over overlays, ◀ ▶ pan buttons + FIRE button, HUD (score, combo, ride %, best), clear-records — verify: harness can flip ready → running → over → again

## 2. The ride & the frights

- [x] 2.1 Ride scroll and pan — verify: tests see rideDist grow on its own, pan() shift the view with clamps at the ends, and the ride reach the barn at RIDE_END
- [x] 2.2 Frights pop up in view and duck away if unhit — verify: tests cover a fright rising when it enters the view, its up-timer expiring into a duck-away, and a tough fright needing two shots

## 3. Shooting & combos

- [x] 3.1 Shoot hits open frights at the crosshair — verify: tests see shoot(x, y) pop a fright whose sprite covers the point, respect the fire cooldown, and ignore frights already ducking
- [x] 3.2 Combo banking and the miss reset — verify: tests see a hit bank 100 × combo and grow the multiplier (cap 8), and an empty shot drop the chain to ×1

## 4. Scoring & presentation

- [x] 4.1 Ride-complete summary and records: best score + best combo save only when improved, survive reload, clear-records toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas autumn pipeline: dusk sky, moon + crows, corn rows, hay bales, leaves, wooden train, fright sprites, crosshair + splat floats, barn ending — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, ride, hit combo, tough scarecrow, ride-complete, phone) and review them — verify: PNGs show the autumn look with readable HUD, clear fright sprites, and a visible crosshair

## Workflow follow-up

- Update README with `ghost-train` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
