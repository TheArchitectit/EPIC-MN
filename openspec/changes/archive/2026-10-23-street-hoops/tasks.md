# Tasks

## 1. Scaffold (`hoops.html` skeleton)

- [x] 1.1 Create `hoops.html` with blacktop CSS vars (sunset/asphalt/chalk remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/over overlays, ◀ ▶ ▲ ▼ drive pad + PASS/SHOOT/TURBO buttons, HUD (you, rivals, clock, streak), clear-records — verify: harness can flip ready → running → over → again

## 2. The match & the court

- [x] 2.1 Match clock and buzzer — verify: tests see the clock tick down each frame and the buzzer fire the result screen at zero with the final score and win/lose banner
- [x] 2.2 Drive the handler and pass — verify: tests see directional controls move the ball handler inside the court bounds and the pass control hand the ball to the teammate

## 3. Shooting & streetball rules

- [x] 3.1 Shoot from position: distance points and the flight — verify: tests see a shot beyond the arc bank 3, a close shot bank 2, and possession flip after the shot resolves
- [x] 3.2 Guarded vs open odds + turbo fuel — verify: tests see a guarded shot use the hard odds, a burst create an open look with the better odds, and the turbo fuel drain/refill correctly
- [x] 3.3 Foul → free-throw tap + streak bank/reset — verify: tests see a guarded shot draw a foul into the free-throw pause, a well-timed tap bank 1 + streak bonus and grow the streak, and a miss reset the streak to 0

## 4. Scoring & presentation

- [x] 4.1 Records: best margin + best streak save only when improved, survive reload, clear-records toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas blacktop pipeline: sunset sky + skyline, chain-link fence, asphalt lines, rims + nets, streetballers, ball arcs, splash text — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, mid-match, free throw, buzzer result, phone) and review them — verify: PNGs show the blacktop look with readable HUD, clear player sprites, and no toast over the controls

## Workflow follow-up

- Update README with `street-hoops` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
