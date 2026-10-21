# Proposal

## Why

The owner's playtest says the slow tuning is **too calm** — the minute
drags and tapping bubbles one-by-one is too hard to aim. They want the
60 seconds to stay alive, with **fun weapons** that assist aiming and
**random gum objects** that keep every round surprising.

## What Changes

- **Aim-assist weapons**: a laser beam aims with the cursor and fires while
  held; missiles and spread shots auto-fire as assists.
- **Gum objects**: random objects appear during play, each doing a wild,
  random thing (score jackpots, missile boosts, gold rain, freeze, gravity
  flips, and more).
- **Escalating 60-second round**: gentle start (0–15s), objects + missiles
  unlock mid-round (15–40s), and the final 20 seconds become a chaotic
  frenzy.
- Bubble pace rises partway back toward the original energy so the minute
  stays gripping without returning to impossible aiming.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `bubblegum-zap`: gameplay gains weapon aiming/assist systems, random gum
  objects, and the escalating round shape.

## Impact

- Code: edits inside `bubblegum.html` (aim/beam rendering, object system,
  phase timeline).
- Data: unchanged — best score persistence stays local.
