# Proposal

## Why

Crossing games are the oldest joy in arcades — read the chaos, find the
gap, make it across. But the famous old ones are stop-and-go, and their
look and names belong to someone else. **Neon Delivery** keeps the joy
and invents the rest: a synthwave night highway where a delivery hero
auto-runs through glowing traffic while you steer — and the pizza on
top wobbles with every bump. Survive the lanes, arrive with dinner
intact. It's ours from bumper to skyline.

## What Changes

- New single-file HTML app `neon.html`, working title **Neon Delivery**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **retro-neon night** skin: deep-purple sky, glowing cyan /
  magenta / gold traffic streaks, neon skyline, dark asphalt with light
  trails — zero image assets, all drawn in code.
- **Auto-run steering**: the hero runs up the highway on their own; the
  player steers left / right between lanes (arrow keys or on-screen
  buttons). Simple to hold, frantic to master.
- **The delivery box**: a pizza rides on top of the hero. Grazing a car
  makes it slide; steering smooth keeps it steady. Slide it off the box
  and the delivery is ruined — arrive with it intact for the full tip.
- **Neon traffic**: cars, vans, and semis streak across the lanes at
  mixed speeds in both directions, glowing tails and headlight beams.
- **Blocks & score**: each block crossed = one delivery made; the next
  block adds more traffic and speed. The board records your best
  delivery streak and best score with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `neon-delivery`: the retro-neon delivery runner — auto-run steering,
  the wobbly pizza mechanic, neon traffic, block progression, and the
  best-streak / best-score records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `neon.html` and `openspec/specs/neon-delivery/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `neon-delivery` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `neon-toppings` (collect toppings mid-run for bonus tips), `neon-sound`
  (synthwave beats and horn honks), `neon-city-tour` (new highway
  biomes — beach drive, snow night, desert dusk).
