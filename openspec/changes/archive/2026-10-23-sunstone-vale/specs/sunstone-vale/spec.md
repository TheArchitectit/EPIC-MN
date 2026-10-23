# Spec Delta

## Purpose

Sunstone Vale is a top-down stained-glass adventure: the hero
explores a golden-hour overworld and a ruin dungeon, fights
monsters with a sword, and completes the chest-key-door-relic
quest. This delta contracts the full first slice — explore, fight,
quest, art, sound, and records.

## ADDED Requirements

### Requirement: Exploring the kingdom

The game SHALL move the hero across two screens — the overworld and
the dungeon — with solid walls that block movement and a ruin
entrance that carries the hero into the dungeon.

#### Scenario: walking the overworld
- **WHEN** the player holds a direction (arrow keys, WASD, or the
  on-screen pad)
- **THEN** the hero walks that way until a tree, wall, or screen
  edge stops them

#### Scenario: entering the ruin
- **WHEN** the hero steps onto the ruin arch on the overworld
- **THEN** the scene changes to the dungeon and the hero appears at
  its entrance

#### Scenario: leaving the ruin
- **WHEN** the hero steps onto the dungeon entrance tile
- **THEN** the scene returns to the overworld at the ruin arch, so a
  keyless visit can always turn around and hunt for the chest

### Requirement: Sword and monsters

The game SHALL let the hero swing a sword at nearby monsters, SHALL
patrol and chase monsters on fixed paths, and SHALL cost the hero a
heart on monster contact — with the run ending when the last heart
is gone.

#### Scenario: swinging the sword
- **WHEN** the player swings (space, X, canvas click, or the SWORD
  button)
- **THEN** a gold arc flashes in the hero's facing direction and
  any monster within reach takes a hit

#### Scenario: defeating a monster
- **WHEN** a monster takes its last hit
- **THEN** it bursts away and the score climbs

#### Scenario: a monster bites back
- **WHEN** a monster touches the hero outside the mercy window
- **THEN** a heart is lost, the hero flashes safe for a moment, and
  the run continues

#### Scenario: the light fades
- **WHEN** the last heart is lost
- **THEN** the run ends with a "the light faded" result

### Requirement: The Sunstone quest

The game SHALL guide one quest: take the key from the chest, open
the ruin's golden door with it, and claim the Sunstone behind it.

#### Scenario: cracking the chest
- **WHEN** the hero reaches the chest on the overworld
- **THEN** the chest opens, the key is collected, and the score
  climbs

#### Scenario: the golden door
- **WHEN** the hero touches the golden door carrying the key
- **THEN** the door opens with a flash; without the key it stays
  shut and says so

#### Scenario: claiming the relic
- **WHEN** the hero touches the Sunstone
- **THEN** the run ends with a "quest won" result and the final
  score and time are shown

### Requirement: Stained-glass presentation

The game SHALL draw its world in code as glowing stained glass —
jewel-tone panels, dark leading, and golden light — with zero image
assets, and SHALL show the current quest step in the HUD.

#### Scenario: the glass world
- **WHEN** the game draws the overworld or the dungeon
- **THEN** floors, walls, hero, monsters, and relic are painted from
  code as jewel panels with leading and glow (no image files)

#### Scenario: the quest line
- **WHEN** the quest stage changes (find the key, enter the ruin,
  unlock the door, claim the relic)
- **THEN** the HUD quest line updates to match what to do next

### Requirement: Sound plays while you explore

The game SHALL unlock the browser audio on the player's first input
and play its synthesized sounds, and SHALL keep running silently
when no audio is available.

#### Scenario: the first input unlocks the speaker
- **WHEN** the player gives any first input
- **THEN** the browser audio is resumed and the game's sounds are
  audible from then on

#### Scenario: every action sounds off
- **WHEN** the hero swings, hits, picks up, opens, hurts, or wins
- **THEN** the matching sound plays

#### Scenario: silent browsers still run
- **WHEN** the browser offers no audio support
- **THEN** the quest continues on visual cues alone, with no error
  and no missing game behavior

### Requirement: Score and records

The game SHALL keep the top score and the fastest quest-clear time
in local storage with the house records machinery, and SHALL never
let a storage failure break the game.

#### Scenario: a new best
- **WHEN** a run sets a new top score or a faster clear time
- **THEN** a NEW BEST banner shows and the records save

#### Scenario: a weaker run keeps the old records
- **WHEN** a run beats neither record
- **THEN** the old records stay and no banner shows

#### Scenario: clearing records
- **WHEN** the player presses CLEAR RECORDS
- **THEN** the records reset and a toast confirms it

#### Scenario: save failures never break the game
- **WHEN** saving to local storage throws
- **THEN** the run still finishes and play continues in memory

### Requirement: Run flow and recovery

The game SHALL run ready → play → result → play again, with both
endings (won / faded) leading back to a fresh quest.

#### Scenario: starting the quest
- **WHEN** the player presses START on the ready screen
- **THEN** a fresh quest begins on the overworld with full hearts

#### Scenario: play again
- **WHEN** the player presses PLAY AGAIN on the result screen
- **THEN** a brand-new quest starts with score, hearts, key, and
  door all reset
