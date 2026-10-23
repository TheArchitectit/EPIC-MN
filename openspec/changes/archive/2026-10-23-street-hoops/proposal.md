# Proposal

## Why

Everyone knows the feeling of a perfect shot — the arc, the swish, the
net snapping. **Street Hoops** is that feeling in one classic arcade
match: two tiny streetball teams on a blacktop court under a sunset
skyline, chain-link fences rattling, one basket, and a buzzer in the
sky. You drive your player around the asphalt, shake the defender,
pull up, and shoot. Sink 3-pointers from deep, earn free-throw streaks
when you are hot, and feed the open teammate for the buzzer-beater.
Pure classic basketball joy — no season mode, no stats sheets, just
"one more game".

## What Changes

- New single-file HTML app `hoops.html`, working title **Street Hoops**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **blacktop streetball** skin: asphalt court with painted
  lines, chain-link fence, sunset city skyline, hanging rim and net,
  chunky streetballers — zero image assets, all drawn in code.
- **The match**: a finite 2-on-2 streetball game on one basket — your
  team and the rival team take turns with the ball, the clock ticks
  down, and the higher score when the buzzer sounds wins.
- **Drive & shoot**: arrow keys (or on-screen pads) dribble your player
  around the half-court; a shoot button fires a shot from wherever you
  stand — distance decides 2 or 3 points; a pass button feeds the
  open teammate.
- **Defenders & open looks**: a rival defender sticks to your ball
  handler; shooting while guarded is a tough brick, shooting from the
  open is a clean look. Drive past (speed burst past the defender) for
  the open shot.
- **Free-throw streaks**: drawing a foul sends you to the line — a
  simple timing tap; swishes in a row build a streak bonus that carries
  into the match score.
- **Score & records**: the board keeps the best win margin and the
  longest free-throw streak with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `street-hoops`: the blacktop streetball arcade match — the 2-on-2
  game clock and possession flow, drive-and-shoot controls with open
  and guarded shot odds, 3-point shots, free-throw streaks, blacktop
  presentation, and best-run records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `hoops.html` and `openspec/specs/street-hoops/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `street-hoops` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `hoops-free-throw-lab` (the pure free-throw streak shooter),
  `hoops-three-point-night` (the around-the-arc clock contest),
  `hoops-street-duel` (the pure 1-on-1 street duel).
