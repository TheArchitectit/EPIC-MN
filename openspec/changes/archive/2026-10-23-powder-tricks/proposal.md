# Proposal

## Why

Every snowboard game promises big air — then buries the fun under real
physics and serious menus. **Powder Tricks** keeps the joy and cartoon-
ifies the rest: a squishy little rider, a chunky mountain, and a trick
button that begs to be spammed. Carve the line, pop off the ramp, grab
the board, land it clean — and when you wipe out, the tumble is the
funniest part. It's the snow day everyone wanted as a kid.

## What Changes

- New single-file HTML app `snow.html`, working title **Powder Tricks**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **cartoon snow** skin: puffy white hills, squishy pine trees,
  chunky bold outlines, candy-colored rider and ramps — zero image
  assets, all drawn in code.
- **Carve & pop riding**: the rider zooms down the mountain on their own;
  the player carves left / right between lanes (arrow keys or on-screen
  buttons) and pulls a **TRICK** lever to pop off ramps.
- **Trick & air**: mid-air, each extra tap on TRICK adds a grab or a
  flip; landing clean banks the trick with a combo multiplier; a bad
  landing is a funny tumble that costs the combo — three tumbles and the
  run is over.
- **Cartoon mountain**: rolling puffy slopes, ramps glowing with candy
  stripes, pine trees to dodge (a tree hit = tumble), and a
  finish-line-lodge feel as the run gets faster and steeper.
- **Score & records**: trick points chain through the combo multiplier;
  the board records your best score and best combo with the house
  seed/load/save/reset + toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `powder-tricks`: the cartoon snowboard trick game — carve & pop
  controls, the trick/landing system, the three-tumble run, cartoon
  mountain presentation, and best-score / best-combo records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `snow.html` and `openspec/specs/powder-tricks/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `powder-tricks` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `powder-mountain` (new slopes and jump parks), `powder-sounds`
  (whooshes and snow-crunch beats), `powder-gear` (boards, jackets, and
  silly hats to unlock).
