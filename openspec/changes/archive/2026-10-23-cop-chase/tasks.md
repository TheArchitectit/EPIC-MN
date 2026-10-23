# Tasks

## 1. Scaffold (`chase.html` skeleton)

- [x] 1.1 Create `chase.html` with neon-pixel CSS vars (night/road/pink/cyan remap + scanlines), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the ready screen
- [x] 1.2 DOM screens and controls: ready/over overlays, gas/brake pedal buttons + ◀ ▶ steering, HUD (score, time, speed, best), clear-records — verify: harness can flip ready → running → over → again

## 2. Driving & highway

- [x] 2.1 Gas, brake, and steering physics — verify: tests see gas raise speed toward the max, brake lower it toward the min, coast drift toward cruise, steer() move the rider toward the neighboring lane, and keys + buttons drive the same functions
- [x] 2.2 Traffic bands scroll, recycle, and near-misses score — verify: tests cover traffic movement, a near-miss adding 50, and a crash dropping speed and tightening the cop gap

## 3. Cops & clock

- [x] 3.1 Pursuit closes in, hard brake overshoots, busted ends the run — verify: tests see copGap shrink over time, overshoot fire only when the cop is close and the brake is held, and copGap ≤ 40 end the run as BUSTED
- [x] 3.2 Arcade clock and checkpoint gates — verify: tests see time count down, a checkpoint add 25s with a toast, and zero time end the run OUT OF TIME

## 4. Scoring & presentation

- [x] 4.1 Run-over summary and records: best score + best distance save only when improved, survive reload, clear-records toast — verify: tests cover new-best, weaker-keeps, reload, and clear
- [x] 4.2 Canvas neon-pixel pipeline: night sky, skyline, glowing road, pixel cars, light-bar cop, checkpoint arch, scanline pass — verify: recorder shows scene draws each frame
- [x] 4.3 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.4 Capture screenshots (ready, chase, overshoot, busted, out-of-time, phone) and review them — verify: PNGs show the neon-pixel look with readable HUD, visible cop lights, and clear car sprites

## Workflow follow-up

- Update README with `cop-chase` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
