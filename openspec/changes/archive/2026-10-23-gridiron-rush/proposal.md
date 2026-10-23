# Proposal

## Why

Every football fan remembers the feeling: the snap, the pocket, the
receiver streaking open down the sideline — **Gridiron Rush** is that
feeling in one retro arcade match. The player quarterbacks the blue
**Comets** against the CPU **Stampede** on a clean gridiron: call the
play, hike the ball, steer the run or fire a pass with one tap per
receiver, and on defense steer the star tackler for the stop. It is
classic Sunday-football joy — short quarters, big plays, a final
scoreboard that begs for a rematch. (Original teams and art in the
classic pro-football spirit — no real-league branding, like every
smart studio does.)

## What Changes

- New single-file HTML app `football.html`, working title **Gridiron
  Rush**, in the house showcase style (vanilla HTML/CSS/JS, invented
  data) wearing a **gridiron classic** skin: crisp green field with
  white yard lines and hash marks, end zones with team colors, a big
  classic scoreboard, chunky helmeted players — zero image assets, all
  drawn in code.
- **The match**: a short 4-quarter arcade game on a 100-yard field —
  the Comets (player) vs the Stampede (CPU), each with drives, a game
  clock, and a final scoreboard with the win/lose result.
- **Run & throw offense**: arrows steer the ball carrier (QB on the
  snap, or the receiver after a catch); three throw buttons fire to
  each receiver's route; a juke button slips past tacklers.
- **Defense**: when the Stampede have the ball, arrows steer the star
  defender — collide with the ball carrier for the tackle and the stop.
- **Plays & scoring**: a quick run/pass play pick at the line; the
  ball moves by yards gained; touchdowns (and the extra point) put 7
  on the board; turnovers hand the ball over.
- **Score & records**: the board keeps the best win margin and the
  most touchdowns in one match with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `gridiron-rush`: the retro football arcade match — the match clock
  and quarters, run-and-throw offense with catchable passes, defensive
  tackling, play picks and scoring, gridiron-classic presentation, and
  best-run records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `football.html` and `openspec/specs/gridiron-rush/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `gridiron-rush` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `gridiron-field-goals` (the placekicking meter), `gridiron-playbook`
  (draw-your-own plays), `gridiron-sound` (crowd roars and whistles).

## Compliance note

Real league names, team names, and logos are trademarked — like the
Frogger-inspired build, we keep the *mechanics and feel* (not
protected) and invent our own names, teams, and art (protected): no
NFL marks anywhere in the app or the README.
