# Proposal

## Why

Remember the feeling of being tiny in a giant world — grass like tall
trees, ants the size of dogs, the house a castle on the horizon?
**Backyard Bastion** is that feeling as a game: the player is shrunk
to the size of a bug at golden hour and must hold a tiny fort in the
grass against waves of bugs. Build the defenses, fight as a hero, and
command tamed bug buddies — three kinds of fun, one epic backyard.
(Original name, story, and art in the tiny-world spirit — the feeling
is free, the movie title isn't, like every smart studio does.)

## What Changes

- New single-file HTML app `backyard.html`, working title **Backyard
  Bastion**, in the house showcase style (vanilla HTML/CSS/JS, invented
  data) wearing a **golden-hour giant** skin: warm sun-flared grass
  jungle, giant pebbles and twigs, the fort glowing in the last light —
  zero image assets, all drawn in code.
- **The siege**: endless waves of bugs attack the fort — each wave is
  bigger and meaner, with a calm build phase in between. Survive the
  wave, patch up, place the next trap.
- **Build between waves**: spend collected crumbs on spike traps,
  pebble turrets, and stick walls placed in the grass around the fort.
- **Hero during the wave**: arrows steer the tiny hero around the fort,
  and a zap control whacks the nearest bug — the hero is the last line
  when the defenses crack.
- **Tamed bug buddies**: friendly bugs you rescue join the fight and
  bite bugs that get close — they level up the longer they survive.
- **Score & records**: the board keeps the best wave survived and the
  most bugs bonked in one siege, with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `backyard-bastion`: the tiny backyard siege game — waves and build
  phases, trap/turret/wall defenses, the steerable hero with the zap,
  tamed bug allies, golden-hour presentation, and best-siege records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `backyard.html` and `openspec/specs/backyard-bastion/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `backyard-bastion` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `backyard-campaign` (the story mode across the yard), `backyard-sound`
  (chirps, buzzes, and the porch-light hum), `backyard-coop` (two tiny
  heroes, one fort).

## Compliance note

Real movie titles and studio marks are protected — like the
Frogger-inspired and football builds, we keep the *feeling* (not
protected) and invent our own name, story, and art (protected): no
movie marks anywhere in the app or the README.
