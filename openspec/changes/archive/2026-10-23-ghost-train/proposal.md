# Proposal

## Why

Every spooky game reaches for cheap screams — then forgets to be fun.
**Harvest Haunt** is the ghost train everyone loved at the fall fair:
a rickety little train rolls through golden corn rows and hay fields,
cheeky frights pop out at the windows, and the player gets one job —
pan the view, blast the boos, and laugh at the splats. It is spooky-
lite on purpose: grinning pumpkins and clumsy scarecrows, not horror.
Pure autumn-night arcade joy.

## What Changes

- New single-file HTML app `train.html`, working title **Harvest
  Haunt**, in the house showcase style (vanilla HTML/CSS/JS, invented
  data) wearing an **autumn harvest** skin: golden dusk sky, scrolling
  corn rows, hay bales, crunchy falling leaves, wooden ghost-train
  cars, and goofy lantern-lit frights — zero image assets, all drawn
  in code.
- **Ghost train ride**: the train advances on rails through the
  harvest night while scenery slides past the windows; frights pop up
  from the fields and along the cars between rides of calm.
- **Pan & shoot**: arrow keys (or on-screen ◀ ▶) swing the view left
  and right along the train; a click / tap fires at the crosshair —
  hit the fright before it ducks away.
- **Hits & combos**: each splatted fright scores points, back-to-back
  hits build a combo multiplier, and a miss drops the chain; some
  frights take a quick second shot to pop.
- **Score & records**: the board keeps the best score and best combo
  with the house seed/load/save/reset + toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `ghost-train`: the autumn ghost-train rail shooter — the ride and
  fright pop-outs, pan-and-shoot controls with hit detection, combo
  scoring, autumn-harvest presentation, and best-run records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `train.html` and `openspec/specs/ghost-train/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `ghost-train` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `ghost-train-maps` (a winter holiday ride and a pumpkin-patch run),
  `ghost-train-sounds` (creaky rails, crow caws, and fairground
  organ), `ghost-train-carnival` (ticket prizes and silly hats for the
  conductor).
