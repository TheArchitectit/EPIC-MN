# Proposal

## Why

Typing speed is a real-world superpower — but typing drills feel like
homework. Typing Rockets turns practice into an **80s arcade time trial**:
your words fuel a glowing neon rocket, and every correct keystroke pushes
you closer to the finish line. Students race the clock, save their best
times, and secretly become faster typists.

## What Changes

- New single-file HTML app `typing.html`, working title **Typing Rockets**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data).
- **Time-trial races**: type the fuel words to fly a rocket from launchpad
  to finish line against the clock; your best time per track is saved.
- **Word fuel**: a rotating mix of **space**, **school spelling**, and
  **silly** words — correct letters burn fuel (speed up the rocket), typos
  make the engine sputter (brief slow-down), never punishing beyond that.
- **Retro-neon arcade art**: glowing synthwave rockets, parallax starfield,
  neon trail flames and a chunky arcade HUD — all drawn in code with CSS
  vars and canvas, zero image assets.
- **Difficulty ramp**: words get longer and appear faster as the rocket
  nears the finish line, so the final stretch feels like a boss rush.
- **Best-time persistence**: per-track best times saved to localStorage
  with the house seed/load/save/reset + toast machinery, so replaying to
  beat yourself is the core loop.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `typing-rockets`: the neon typing time-trial — race setup and finish,
  word-fuel typing mechanics with typo sputter, rotating word pools,
  difficulty ramp, best-time persistence, and retro-neon presentation.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `typing.html` and `openspec/specs/typing-rockets/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `typing-rockets` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `rocket-skins` (customize your rocket), `rocket-sounds` (typing sound
  effects), `rocket-worlds` (more tracks and planets to unlock).
