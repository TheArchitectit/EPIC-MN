# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, `flourish()`/`sparkBurst()`, canvas draw pipelines, top-level
functions for the stub-DOM harness, `TICK_MS=100` clocks). Pet Hatchery
is the first **pet-training game** in the set — hatch, practice, perform —
wearing the storybook-pixel skin the student picked (cream paper, ink
lines, chunky sprites, stamped wood).

## Goals / Non-Goals

**Goals**
- Hatch a one-of-a-kind pet from a storybook egg in seconds.
- Two trick engines the student picked: tap-timing (dance, jump rope) and
  memory sequences (spin, jump, clap).
- A training day of three mixed exercises that unlocks the talent show.
- A star-scored talent show with ENCORE energy and a best-show record.
- All art drawn in code: pixel pet, paper page, wood buttons, scribble stars.

**Non-Goals**
- Care/feeding simulation (`pet-costumes`/`pet-stable` parked for extras).
- Sound (`pet-sounds` parked).
- Multiple saved pets (one pet per player; `pet-stable` parked).
- Real keyboard text capture for names (a text input is enough).

## Decisions

1. **Single-file `pet.html`** in house style with a storybook remap of the
   CSS vars: `--ink:#3b2f2f` (sepia), `--paper:#f7ecd9`, `--berry:#d9556c`,
   `--sage:#7a9e7e`, `--sky:#6b8fbd`, `--gold:#d9a441`, `--mono` →
   Georgia/serif stack, `--hard:5px 5px 0 rgba(59,47,47,0.25)` ink shadow.
   Buttons look like stamped wood panels (border + offset shadow + caps).
2. **Egg types** — three hardcoded eggs: Speckle (terracotta pet "Pip"),
   Stripe (sage pet "Moss"), Starry (sky pet "Luna"). Chosen egg sets
   `state.pet = { name, egg, colors }`. Rename via a text input +
   CONFIRM button (harness-friendly `value` property).
3. **Hatch action** — WARM THE EGG button advances `state.warmth` 0→3;
   each press narrates ("toasty... warmer... IT'S WOBBLING!"); at 3 the
   egg hatches (crack animation on canvas via `frame`), home screen shows.
4. **Screens** — DOM overlays like Maze Maker: `state.screen` ∈
   hatch | home | timing | memory | result. A single `setScreen(name)`
   flips `hidden` classes; `render()` updates HUD text from state.
5. **Training plan** — `state.act` ("train" | "show") and `state.plan`
   (list of {kind, name}); train plan = [timing DANCE, memory TRICKS,
   timing JUMP ROPE], show plan = the same three as acts. `nextRound()`
   starts the next plan entry; when the plan empties, `finishAct()`
   builds the result screen and (for train) sets `state.trained = true`.
6. **Timing engine** — `state.timing = { pos, dir, speed, taps, verdict }`;
   `tick()` advances `pos` in 0..1 bouncing at the edges
   (`pos += dir * speed * TICK_MS/1000`, speed 0.9). `tapTiming()` grades
   |pos − 0.5| ≤ 0.06 PERFECT, ≤ 0.15 GOOD, else FLOP; each grade pushes
   points (2/1/0) and shows a verdict line + pet reaction. Training = 5
   taps, show acts = 3 taps. Stars = clamp(round(points / 2), 1, 5) →
   10 pts → 5 stars.
7. **Memory engine** — `state.memory = { seq, input, phase, showIdx, showTimer }`.
   Sequences use moves "spin" | "jump" | "clap". Demo phase plays each
   move on the pet for 6 ticks (600 ms) with 2-tick gaps (tick-driven, so
   the harness can step it). Input phase: `memoryPress(move)` appends and
   checks; a wrong move sets `phase = "fail"` with "TRY AGAIN!" and ends
   the round at its current stars. Training = 3 rounds (lengths 2, 3, 4);
   show acts = 1 round of length 3. Stars from rounds passed (1–5 map).
8. **Talent show scoring** — show acts reuse the engines with fewer taps /
   one round; per-act stars 1–5; `totalStars`; `score = totalStars * 100 +
   perfectTaps * 25`. ENCORE banner when `totalStars >= 12`. `state.best`
   (score + stars) updates only when `score` beats it; NEW BEST banner.
9. **Persistence** — `GKEY = "pet-hatchery:v1"` holding
   `{ pet: { name, egg }, best: { score, stars }, trained }`. Corrupt or
   missing data → seed (`pet: null`, `best: null`, `trained: false`).
   `newPet()` wipes state + storage with a toast.
10. **Rendering** — one `<canvas>` (640×360): cream fill, ink frame line,
    hand-drawn ground scribble, chunky pixel pet (12×12 pixel map of
    fillRects with body/belly/eye colors from the egg, idle bob via
    `frame`), reaction poses (jump y-offset, spin rotation, clap feet,
    flop tilt), egg with crack lines during hatch, stage curtains +
    spotlights during the show, scribble stars (`sparkBurst` particles in
    gold). DOM holds title, HUD (STARS / SCORE / BEST), screen overlays,
    wood buttons, name input, toast.
11. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness (makeEl with `value` support for the name input, shared
    localStorage across boots, canvas op recorder, interval capture) covering
    hatch/rename/reload, both engines' grades and rounds, plan flow, show
    scoring/ENCORE, best save/skip/reload, new-pet; headless Chromium CDP
    screenshots (hatch, home, timing, memory, result).

## Risks / Tradeoffs

- **Memory demo timing in tests** — tick-driven demo (not setTimeout) keeps
  the harness deterministic; real players just watch the pet move.
- **One pet per player** — renaming is free, but multi-pet needs
  `pet-stable`; keeps `GKEY` simple.
- **Name input** — a DOM `input.value` read at confirm time is simpler and
  more accessible than canvas typing.
- **Star mapping** — floors at 1 star so every try ends in applause
  (kindergarten-friendly), ENCORE stays the aspirational goal.

## Migration Plan

New file `pet.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the four product decisions: Pet Hatchery,
trick training, both trick styles, storybook pixel art )
