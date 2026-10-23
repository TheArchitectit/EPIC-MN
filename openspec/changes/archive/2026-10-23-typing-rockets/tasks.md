# Tasks

## 1. Scaffold (`typing.html` skeleton)

- [x] 1.1 Create `typing.html` with house CSS vars (neon remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots to the ready screen
- [x] 1.2 DOM screens: ready (track picker + START), racing (word + HUD), finished (time + FLY AGAIN) — verify: harness can flip between all three screens via `startRace`/`finishRace`

## 2. Typing engine

- [x] 2.1 Word pools (space/school/silly, ≥12 each) + rotation + length ramp `3 + floor(progress*5.5)` — verify: tests show pool rotation and boss-rush lengths near the finish
- [x] 2.2 `handleChar`: correct letter advances + fuels speed/progress, typo sputters without progress loss, word complete bursts + swaps word — verify: tests cover all three paths
- [x] 2.3 100 ms tick: elapsed clock, speed decay, progress from speed, finish detection at `progress >= 1` — verify: harness steps a fake clock to a finish and checks the recorded time
- [x] 2.4 Best-time persistence per track: save only when beaten, survives reload, reset clears with toast — verify: tests cover new-best, slower-keeps-best, reload, and reset

## 3. Presentation (retro-neon)

- [x] 3.1 Canvas pipeline: sky gradient, 3-layer parallax starfield, striped synthwave sun, perspective grid horizon — verify: draw() runs without errors in the recorder harness
- [x] 3.2 Neon rocket + flickering flame + trail + `sparkBurst` on correct keys — verify: recorder shows rocket/flame draws each frame
- [x] 3.3 Arcade HUD: TIME/BEST/WORDS, speed bar, big neon word with caret, `flourish()` on word complete — verify: all labels render at launch and update during a race
- [x] 3.4 Finish screen: final time, stats, NEW BEST banner when beaten — verify: finish state shows the banner only when the best was improved

## 4. Integration checks

- [x] 4.1 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.2 Capture screenshots (ready, mid-race, finish) and review them — verify: PNGs show the retro-neon look with readable HUD

## Workflow follow-up

- Update README with `typing-rockets` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
