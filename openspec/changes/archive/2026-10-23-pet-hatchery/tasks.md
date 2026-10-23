# Tasks

## 1. Scaffold (`pet.html` skeleton)

- [x] 1.1 Create `pet.html` with storybook CSS vars (cream/ink remap), page shell, toast + localStorage seed/load/save/reset machinery — verify: `node --check` passes on the extracted script and the page boots on the hatch screen
- [x] 1.2 DOM screens and controls: hatch (eggs + warm + name), home (train/show buttons), timing, memory, result overlays, HUD — verify: harness can flip hatch → home → training → show → result → home

## 2. Hatch and pet

- [x] 2.1 Egg picker (3 storybook eggs) + warm action that hatches a colored pet — verify: tests cover choosing each egg and the hatch at full warmth
- [x] 2.2 Rename flow via name input + confirm — verify: a new name shows in the HUD everywhere
- [x] 2.3 Reload keeps the pet and best record — verify: a second boot on a shared store restores name, egg, and best

## 3. Trick engines

- [x] 3.1 Tap-timing engine: sliding marker, PERFECT/GOOD/FLOP grading, funny flops — verify: tests grade a sweet-spot tap, a mid tap, and a flop
- [x] 3.2 Memory engine: pet demo of spin/jump/clap sequences, repeat-input, try-again on wrong move — verify: tests pass a full sequence and break one mid-way
- [x] 3.3 Training day plan of 3 mixed exercises awarding 1–5 stars each and unlocking the show — verify: tests run the full day and see the show unlock

## 4. Talent show and records

- [x] 4.1 Show acts reuse the engines (3 taps / 1 round), stars per act, total score, ENCORE at 12+ stars — verify: tests cover a scored act, an ENCORE finish, and a quiet finish
- [x] 4.2 Best show: save only when better, NEW BEST banner, weaker keeps, reload restores — verify: tests cover all four cases
- [x] 4.3 New-pet action resets pet and records with a toast — verify: test wipes state and storage
- [x] 4.4 Canvas storybook pipeline: paper, pixel pet, reactions, egg cracks, stage, scribble stars — verify: recorder shows scene draws each frame
- [x] 4.5 `node --check` + stub-DOM harness all green — verify: every spec scenario passes in the harness run
- [x] 4.6 Capture screenshots (hatch, home, timing, memory, result) and review them — verify: PNGs show the storybook look with readable HUD

## Workflow follow-up

- Update README with `pet-hatchery` (run instructions, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the web app on the student's display.
