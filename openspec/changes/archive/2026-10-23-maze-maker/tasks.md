# Tasks

## 1. Scaffold (`maze.html` skeleton)

- [x] 1.1 Create `maze.html` with house CSS vars (neon remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots in build mode
- [x] 1.2 DOM screens and controls: tool buttons, PLAY/RESET RUN/CLEAR BOARD, HUD, win overlay, status line — verify: harness can flip build → solve → win and back to edit

## 2. Build mode

- [x] 2.1 Wall paint/erase with drag, start/goal placement, treasure toggle capped at 5 — verify: tests cover each tool and the cap
- [x] 2.2 Clear board removes walls, treasures, start, and goal — verify: test wipes a full board back to empty
- [x] 2.3 Validation with friendly messages (missing start, missing goal, disconnected) and BFS path check — verify: tests cover all three refusals and one connected pass

## 3. Solve mode

- [x] 3.1 `moveBall` one cell per arrow/WASD with wall/edge refusal and step counting — verify: tests cover a step, a blocked step (no count), and key mapping
- [x] 3.2 Click-to-step toward a cell along the dominant direction — verify: tests cover a free step and a blocked click-step
- [x] 3.3 Treasure collection (sparkle + count) and goal win with stats overlay — verify: tests cover collecting and winning
- [x] 3.4 100 ms run clock + reset-run (ball home, counters zero, treasures restored) — verify: tests step a fake clock and check the reset

## 4. Scoring & presentation

- [x] 4.1 Best runs per maze signature: save only when better, survive reload, clear-records with toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas neon pipeline: grid, glowing walls, trail, ball, pulsing goal, treasures, sparks — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (build mode, solve mid-run, win screen) and review them — verify: PNGs show the neon grid look with readable HUD

## Workflow follow-up

- Update README with `maze-maker` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
