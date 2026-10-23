# Proposal

## Why

Every great adventure starts with one screen: a hero, a wild
kingdom, and a relic worth finding. **Sunstone Vale** is that
adventure in a showcase-sized game — a top-down action quest in a
**golden-hour kingdom**, drawn as **glowing stained glass** (jewel
panels and golden light, like sun through a castle window). Wander
the grass, swing your sword at the monsters, crack the chest for the
key, unlock the ruin's golden door, and claim the Sunstone before
the light fades.
(The top-down explore-fight-solve *feeling* is free — real game
series names aren't — so the name, hero, and world are original,
like every smart studio does.)

## What Changes

- New single-file HTML app `sunstone.html`, working title
  **Sunstone Vale**, in the house showcase style (vanilla
  HTML/CSS/JS, invented data) with a stained-glass art look: jewel
  tone floor panels, dark leading on every shape, golden light
  shafts — zero image assets, all drawn in code.
- **Exploring**: arrow keys / WASD (plus an on-screen pad) walk the
  hero across two hard-coded screens — the grassy overworld and the
  ruin dungeon — with solid trees/walls and one-way travel into the
  ruin.
- **Sword & monsters**: space (or the SWORD button) swings a gold
  arc; slimes and bats patrol fixed paths and chase when close;
  contact costs a heart with a mercy flash — lose all four hearts
  and the light fades.
- **The quest**: a chest on the overworld holds the key; the ruin's
  golden door opens only with it; behind the door waits the
  Sunstone — touch it and the quest is won.
- **Score & records**: monsters and quest steps score points; the
  board keeps the top score and the fastest clear time with the
  house seed/load/save/reset + toast machinery.
- **Sound plays for real**: the speaker unlocks on the first input
  (the new house rule), with sword, hit, pickup, door, hurt, and
  victory sounds synthesized in code.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `sunstone-vale`: the stained-glass top-down adventure — exploring
  the golden-hour kingdom, sword-and-monsters combat with hearts,
  the chest-key-door-relic quest, stained-glass presentation, sound,
  and best-run records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `sunstone.html` and `openspec/specs/sunstone-vale/spec.md`
  (new).
- No new dependencies — plain HTML like the other showcase apps; the
  sounds come from the browser's built-in Web Audio, no audio files.
- README gains a `sunstone-vale` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `sunstone-vale-worlds` (more lands and dungeons),
  `sunstone-vale-gear` (bow, bombs, shield pickups),
  `sunstone-vale-quests` (villagers and side stories),
  `sunstone-vale-boss` (a dungeon boss fight).

## Compliance note

Real game series titles and studio marks are protected (a certain
famous adventure series especially) — we keep only the top-down
adventure *feeling* (not protected) and invent our own name, hero,
world, and art (protected): no real game or studio marks, characters,
or symbols anywhere in the app or the README.
