# Proposal

## Why

Every kid wants a pet that is truly *theirs* — one they hatched, trained,
and cheered for on stage. Pet Hatchery hands students that story in one
file: pick an egg, hatch a wiggly pixel pet, **train it through trick
practice** (tap-timing and memory games), then take the stage at the
**talent show** and earn stars together. It's a storybook game cartridge
about coaching a small friend to do silly, wonderful things.

## What Changes

- New single-file HTML app `pet.html`, working title **Pet Hatchery**, in
  the house showcase style (vanilla HTML/CSS/JS, invented data) wearing a
  **storybook pixel** skin: cream paper background, ink outlines, chunky
  pixel pet sprites drawn in code, stamped-wood buttons, hand-drawn
  scribble stars — zero image assets.
- **Hatch**: choose one of several storybook eggs, keep it warm with a
  hatch action, and meet a chunky pixel pet whose colors and name grow
  with the player.
- **Training day**: three exercises that mix the two trick styles the
  student picked —
  - **tap-timing tricks** (dance, jump rope): tap SPACE/click when a
    sliding marker hits the sweet spot; perfect taps win graceful moves,
    sloppy taps flop (funny on purpose);
  - **memory sequences** (tricks round): the pet demonstrates a move
    sequence (spin, jump, clap…), the player repeats it back with
    clicks/keys.
- **Talent show**: after training, perform the day's tricks on a stage,
  earn 1–5 stars per trick and a total score, with an ENCORE when the
  show is great.
- **Progression**: stars fill a scrapbook of show posters; best show
  score per pet is saved with the house seed/load/save/reset + toast
  machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `pet-hatchery`: the storybook pet-training game — hatching, timing and
  memory trick training, the star-scored talent show, and the paper-pixel
  presentation.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `pet.html` and `openspec/specs/pet-hatchery/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `pet-hatchery` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `pet-costumes` (dress your pet for the show), `pet-sounds` (chirps and
  fanfares), `pet-stable` (hatch and keep several pets).
