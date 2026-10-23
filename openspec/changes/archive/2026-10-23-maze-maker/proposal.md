# Proposal

## Why

Mazes train planning and spatial thinking — but solving someone else's
maze is half the fun. Maze Maker hands students both hats: **build** a maze
on a glowing grid (walls, start, goal, treasures), then **solve** your own
creation with a light-cycle ball that leaves a neon trail. It's a puzzle
designer's workshop and an arcade game in one file.

## What Changes

- New single-file HTML app `maze.html`, working title **Maze Maker**, in
  the house showcase style (vanilla HTML/CSS/JS, invented data).
- **Build mode**: paint and erase walls on a 15×15 grid; place the ball
  start, the goal flag, and up to 5 treasures; a clear-board tool; the
  maze is validated before play (start and goal must exist and connect).
- **Solve mode**: steer the ball with **arrow keys / WASD** or **click a
  cell** to roll there step by step; collect treasures for bonus points;
  reach the goal flag to win; a timer and step counter score the run.
- **Best-run persistence**: fastest time and fewest steps per maze saved
  locally with the house seed/load/save/reset + toast machinery.
- **Neon grid art**: dark background, glowing wireframe walls, a Tron-style
  light-cycle ball with fading trail, bright goal beacon and sparkling
  treasures — all drawn in code with canvas + CSS vars, zero image assets.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `maze-maker`: the neon build-and-solve maze workshop — build tools and
  validation, arrow/click ball steering with trail, treasures and goal,
  run scoring with best-run persistence, and glowing grid presentation.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `maze.html` and `openspec/specs/maze-maker/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `maze-maker` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `maze-share` (share mazes with friends), `maze-sounds` (engine and win
  jingles), `maze-levels` (a campaign of built-in puzzles).
