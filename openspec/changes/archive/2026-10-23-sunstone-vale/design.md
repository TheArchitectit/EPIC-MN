# Design

## Context

Sunstone Vale is a single-file vanilla HTML/CSS/JS top-down
adventure (`sunstone.html`) in the house showcase style, wearing a
stained-glass skin: jewel panels, dark leading, golden light. It is
the student's "Zelda-style RPG" scoped to one complete slice —
explore, fight, key, door, relic — on two hard-coded screens
(overworld + dungeon). The trademarked series gives only the
*feeling*; the name, hero, world, and art are original.

## Goals / Non-Goals

**Goals**
- One full quest loop that reads instantly: grass → monsters →
  chest/key → ruin → golden door → Sunstone.
- Fair, chunky action: one sword swing, four hearts, mercy flash,
  never a cheap hit.
- Stained-glass look drawn entirely in code — the "whoa" is the
  light through the glass.
- House standards: sound unlocks on first input, records with
  toast, phase-aware HUD text.

**Non-Goals**
- No NPC towns, inventories, or multi-dungeon campaigns (parked as
  later changes).
- No real series names, characters, or symbols (compliance note in
  the proposal).
- No scrolling camera — both screens fit whole on the canvas.

## Decisions

1. **File & frame**: single `sunstone.html`; CSS vars themed; canvas
   `draw()` + DOM `render()`; top-level functions for the test
   harness; `TICK_MS = 50` clock. Canvas 540×720: HUD band 0–60,
   world 60–720 (`TILE = 30`, map 18×22 = 540×660).
2. **Palette (stained-glass golden hour)**: `--gold:#ffd24a`,
   `--ruby:#e63956`, `--amethyst:#9b5cff`, `--sapphire:#3d7dff`,
   `--emerald:#2fbf71`, `--lead:#201436`, `--panel:#31205e`,
   `--ink:#fff6e8`, `--dim:#9a86c8`, `--danger:#ff5a6a`.
3. **Phases & scenes**: `ready → playing → over`; `state.scene` is
   `"overworld"` or `"dungeon"`. `startRun()` arms a fresh quest:
   scene overworld, hero at the map's `S`, hearts 4, score 0, key/
   chest/door flags 0, elapsed 0, monsters rebuilt from spawn defs.
4. **World maps** (deterministic strings, legend `#` wall, `.` floor,
   `S` spawn, `C` chest, `A` ruin arch, `D` golden door, `P`
   Sunstone pedestal): two hard-coded 18×22 maps. Walls solid; the
   `D` tile is solid until opened. Stepping on `A` swaps the scene
   to the dungeon (one-way).
5. **Movement**: `HERO_SPEED = 150` px/s; arrows/WASD held keys plus
   an on-screen pad (pointerdown/up held state); per-axis AABB
   collision against solid tiles; facing recorded for the sword.
6. **Sword**: space / X / canvas click / SWORD button —
   `SWORD_REACH = 36` px in the facing direction, `SWORD_MS = 300`
   cooldown, a gold arc (`SWORD_ARC_MS = 200`) drawn on every swing;
   hits knock monsters back 20 px; `slime` 2 HP, `bat` 1 HP.
7. **Monsters**: hard-coded spawn defs (no randomness) — each has a
   home point, patrol axis, amplitude, phase, and speed; they patrol
   on a sine and chase the hero within `130` px. Contact within
   `20` px outside the mercy window: `hearts -= 1`,
   `mercy = 24 ticks` (1.2 s), hero flashes. `hearts <= 0` →
   `endRun("fell")`.
8. **The quest**: `C` chest touch → `key = 1`, `score += 200`,
   burst + sound. `D` touch with key → `doorOpen = 1` + flash;
   without key → judge "LOCKED!". `P` touch → `endRun("won")` with
   `score += 500` counted before the result.
9. **Scoring & records**: slime/bat `+100`, chest `+200`, Sunstone
   `+500`. `GKEY = "sunstone-vale:v1"` holds
   `{ bestScore, bestTime }` (`bestTime` ms, 0 = never cleared) —
   each field updates only on improvement; NEW BEST banner if
   either improved; house seed/load/save/reset + toast on CLEAR
   RECORDS; try/catch everything.
10. **Sound (Web Audio, optional)**: `unlockAudio()` on every input
    path (the new house rule — browsers mute until asked); `blip()`
    sweeps for swing/hit/pickup/door/hurt and a short victory
    arpeggio on win; silent-safe without `AudioContext`.
11. **HUD (phase-aware — the backyard lesson)**: hearts (ruby
    glass), score, time `m:ss`, and the quest line
    (`FIND THE CHEST` → `ENTER THE RUIN` → `UNLOCK THE GOLDEN DOOR`
    → `CLAIM THE SUNSTONE`; over: `QUEST COMPLETE` / `THE LIGHT
    FADED`).
12. **Screens**: `screen-ready` ("SUNSTONE VALE" + how-to + records
    + PRESS START!), `screen-over` ("The Sunstone is yours!" or "The
    light faded" + score + time + NEW BEST + PLAY AGAIN). Toast
    absolute `top: 100px` inside `.boardwrap`.
13. **Art (stained-glass)**: jewel floor panels with lead grid
    lines and slight per-tile shade shifts; golden light shafts
    (translucent gold wedges from the top); trees as dark emerald
    glass clusters; dungeon walls deep violet with ruby gems; hero
    as a small glass knight (gold helm, sapphire tunic, lead
    outline); slimes as emerald domes; bats as amethyst wings;
    chest, golden door, and pulsing Sunstone all glow; gold diamond
    bursts; warm vignette — zero images.

## Risks / Tradeoffs

- Fixed screens can feel small — accepted for the slice: the quest
  is the content, and `sunstone-vale-worlds` is the parked home for
  more land.
- Chase AI on a tiny map can corner the hero — accepted: mercy
  flash + slow monsters keep it school-friendly.
- Stained glass needs thick leading to stay readable at game size —
  accepted: 2–3 px lead lines everywhere, shapes over texture.

## Migration

None — new capability, new file. Existing showcase apps untouched.

## Open Questions

None — the student locked the shape: Zelda-style slice, golden-hour
kingdom, stained-glass flash.
