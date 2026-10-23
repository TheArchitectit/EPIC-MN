# Tasks

## 1. Scaffold (`snow.html` skeleton)

- [x] 1.1 Create `snow.html` with cartoon-snow CSS vars (sky/snow/navy outline remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/over overlays, chunky carve buttons (◀ ▶) and TRICK button, HUD (score, combo, tumbles, best), clear-records — verify: harness can flip ready → running → over → again

## 2. Riding

- [x] 2.1 Auto-descend scroll and lane carving — verify: tests see the rider descend with no input, steer() move the rider toward the neighboring lane, and runSpeed() grow with distance
- [x] 2.2 Pop & ramps: trick control hops on the ground, launches big air over ramps, and rows of trees/ramps scroll and recycle — verify: tests cover a plain hop, a ramp launch, and terrain rows present

## 3. Tricks & tumbles

- [x] 3.1 Air tricks stack points and clean landings bank them times the combo — verify: tests see trick presses add 100/200/300..., a clean landing add airPoints × combo to the score, and the multiplier climb (cap 8)
- [x] 3.2 Over-rotation and trees tumble the rider; the third tumble ends the run — verify: tests cover a 4-trick over-rotation tumble, a tree hit resetting the combo and dropping unbanked points, and run-over at three tumbles

## 4. Scoring & presentation

- [x] 4.1 Run-over summary and records: best score + best combo save only when improved, survive reload, clear-records toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas cartoon pipeline: sun, clouds, puffy hills, candy ramps, squishy pines, bold rider + board poses, snow spray, dizzy stars, banked pop-text — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, mid-run, big air, tumble, run-over, phone) and review them — verify: PNGs show the cartoon snow look with readable HUD and clear trick poses

## Workflow follow-up

- Update README with `powder-tricks` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
