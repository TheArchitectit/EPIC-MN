# Design

## Context

Backyard Bastion is a single-file vanilla HTML/CSS/JS arena-defense
game (`backyard.html`) in the house showcase style. One fixed top-down
arena — no camera — shows the whole backyard: a grass jungle at golden
hour with a bottle-cap fort in the middle. The player is a tiny hero
who builds defenses between waves and fights during them. Everything
is invented data, local-only, zero images.

## Goals / Non-Goals

**Goals**
- A complete siege loop: build → wave → survive → build again, until
  the fort falls.
- Three kinds of play in one match: place defenses, steer-and-zap the
  hero, command up to two tamed bug buddies.
- Warm golden-hour look drawn entirely in code.
- House records machinery (seed/load/save/reset + toast).

**Non-Goals**
- No story mode, sound, or co-op (parked later changes).
- No movie names or marks (compliance note in the proposal).
- No scrolling world — one arena keeps the code classroom-readable.

## Decisions

1. **File & frame**: single `backyard.html`; CSS vars themed; canvas
   `draw()` + DOM `render()`; top-level functions for the test harness;
   `TICK_MS = 100` `setInterval` clock. Canvas 540×720, fixed arena —
   hero and bugs live in canvas coordinates (no world/camera math).
2. **Palette (golden-hour giant)**: `--sun:#ffcf6e`, `--grass:#4e8a3a`,
   `--grass2:#5c9c46`, `--dirt:#a8845a`, `--ink:#2b1e12`,
   `--cream:#fff3d6`, `--gold:#ffb13d`, `--fort:#c98f4e`, `--bug:#6b3f2a`,
   `--buddy:#5ec8e0`, `--petal:#e86a8a`, `--board:#2e2417`.
3. **Phases**: `ready → build → wave → build → wave → … → over`.
   `startGame()` opens a fresh siege at build phase (wave 1) with
   `START_CRUMBS = 28` and `FORT_HP = 30` at the fort
   (`FORT_X=270, FORT_Y=380, FORT_R=46`). `startWave()` flips to the
   wave phase and fills the spawn queue.
4. **Waves**: wave `n` sends `4 + n*2` bugs, one every
   `SPAWN_TICKS = 8` ticks from random yard edges. Bug kinds: `ant`
   (speed 2.2, hp 3, bite 1, bounty 2), `beetle` (speed 1.5, hp 8,
   bite 2, bounty 4, from wave 2), `fly` (speed 3.4, hp 2, bite 1,
   bounty 2, from wave 3). A bug at the fort (`FORT_R + 14`) stops and
   bites every 5 ticks. Wave clear (queue empty and yard empty) →
   build phase, `wave++`, and a crumb bonus `12 + wave * 3`.
5. **Hero**: arrows/WASD steer at `HERO_SPEED = 7` in build and wave
   phases. Zap (Space/J) hits the nearest bug within `ZAP_R = 70` for
   `ZAP_DMG = 2`, recharge `ZAP_CD = 6` ticks.
6. **Build phase**: TRAP 8 crumbs (spike seed — 1 damage to every bug
   within `26px` every 2 ticks), TURRET 14 (acorn — 1 damage to the
   nearest bug within `170px` every 3 ticks, with a flash line),
   WALL 6 (stick planks — `hp 14`, blocks bugs; a blocked bug chews it
   for 1 damage every 4 ticks). Placement lands at the hero's feet and
   is refused within `FORT_R + 24` of the fort, within `42px` of
   another defense, or outside the arena margins (`x 50..490`,
   `y 90..650`). Keys 1/2/3 = trap/turret/wall; during a wave these
   toast "build between waves" instead.
7. **Buddies**: a stray friendly bug appears at the start of each
   build phase (if fewer than 2 buddies) at a random edge. Hero touch
   (`24px`) tames it. Buddies follow the hero at `44px` and bite the
   nearest enemy bug within `36px` for `1 + level` every 2 ticks;
   `level` grows by 1 after every cleared wave. Max 2 buddies.
8. **Records**: `GKEY = "backyard-bastion:v1"` holds
   `{ bestWave, mostBonks }` — the farthest wave reached and the most
   bugs bonked in one siege. Updated only when improved; NEW BEST
   banner on the result screen; house seed/load/save/reset with
   try/catch; CLEAR RECORDS button resets and toasts.
9. **Screens**: `screen-ready` ("Backyard Bastion!" + records),
   `screen-over` ("The fort fell!" + wave reached + bugs bonked +
   NEW BEST + DEFEND AGAIN). Toast sits absolute `top: 100px` inside
   `.boardwrap` — under the HUD bar, never over the action strip
   (the Street Hoops/football lesson).
10. **HUD**: a classic bar on canvas top — fort hearts, crumbs, wave —
    with floats and zap flashes drawn under it.
11. **Keys**: arrows/WASD move, Space/J zap, 1/2/3 build, Enter starts
    the wave (build phase) or the game (ready/over). On-screen: ◀▶▲▼
    toggles, ZAP, TRAP, TURRET, WALL, START WAVE, CLEAR RECORDS.
12. **Art**: flat warm greens with alternating mow patches, a radial
    sun-flare overlay (`createRadialGradient`) from the top-right,
    hard-coded decor (pebbles, dandelions, a twig), bottle-cap fort
    with a flag, chunky top-down sprites for hero/bugs/buddies — zero
    images.

## Risks / Tradeoffs

- Endless waves with no difficulty cap can crush the player — accepted:
  the fun is the personal best ("how far did you get?"), and the wave
  size grows linearly so early waves stay friendly.
- Instant placement at the hero's feet (no drag-and-drop grid) keeps
  the controls classroom-simple: walk there, press the button.
- The hero has no health — bugs ignore the hero and go for the fort.
  This keeps the arcade clean: you defend the fort, you don't get
  whacked while learning the map.

## Migration

None — new capability, new file. Existing showcase apps untouched.

## Open Questions

None — the student locked the shape: base defense, mix of hero +
build + bug army, golden-hour giant.
