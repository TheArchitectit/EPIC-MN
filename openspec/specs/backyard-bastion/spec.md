# backyard-bastion Specification

## Purpose
A golden-hour backyard siege game for one tiny hero: the player is
shrunk to the size of a bug and holds a little fort in the grass
against waves of bugs. Between waves the player spends crumbs on spike
traps, pebble turrets, and stick walls; during the wave the hero zaps
bugs up close while tamed bug buddies bite anything that gets near the
fort. The fort falls one day — how long can you hold?

## Requirements

### Requirement: The siege
The app SHALL run an endless backyard siege: waves of bugs march
toward the fort and bite it, each wave bigger and meaner than the
last, and the siege ends when the fort's health reaches zero.

#### Scenario: Waves march on the fort
- **WHEN** a wave is running
- **THEN** bugs spawn from the edges of the yard and walk toward the
  fort

#### Scenario: Bugs bite the fort
- **WHEN** a bug reaches the fort
- **THEN** it stops and bites until the fort's health drops

#### Scenario: The fort falls
- **WHEN** the fort's health reaches zero
- **THEN** the siege ends and the result screen shows how far the
  player got

### Requirement: Build between waves
The app SHALL give the player a calm build phase between waves to
place spike traps, pebble turrets, and stick walls around the fort,
spending crumbs earned from the bugs. Defenses SHALL fire on their own
during the wave — traps bite bugs that step on them, turrets shoot the
nearest bug in range, and walls block bugs and soak up bites.

#### Scenario: Spending crumbs on defenses
- **WHEN** the player places a trap, turret, or wall during the build
  phase
- **THEN** the cost in crumbs is deducted and the defense stands on
  the grass at the hero's feet

#### Scenario: The turret fires on its own
- **WHEN** a bug comes within range of a pebble turret during a wave
  **THEN** the turret shoots it until the bug is gone or out of range

#### Scenario: The wall blocks the way
- **WHEN** a bug bumps into a stick wall
- **THEN** it stops to chew the wall instead of marching on the fort

### Requirement: Hero during the wave
The app SHALL let the player steer the tiny hero around the yard with
the directional controls and zap the nearest bug with a zap control
that has a short cooldown and a limited reach.

#### Scenario: Steering the hero
- **WHEN** the player holds a directional control
- **THEN** the hero runs across the grass in that direction

#### Scenario: The zap bonks a bug
- **WHEN** the player zaps while a bug is within reach
- **THEN** the nearest bug takes damage and the zap needs a moment to
  recharge

### Requirement: Tamed bug buddies
The app SHALL place stray friendly bugs in the yard that join the
fight when the hero touches them, up to two buddies. Tamed buddies
SHALL follow the hero and bite enemy bugs that get close, and SHALL
grow stronger after every wave they survive.

#### Scenario: A stray joins the cause
- **WHEN** the hero touches a stray friendly bug
- **THEN** it becomes a tamed buddy and fights beside the hero

#### Scenario: The buddy bites back
- **WHEN** an enemy bug comes near a tamed buddy
- **THEN** the buddy bites it until the bug is gone

### Requirement: Golden-hour giant presentation
The app SHALL render a golden-hour backyard at tiny scale — warm sun
light over a grass jungle, giant pebbles and flowers, a little fort,
and chunky bug and hero sprites — all drawn in code with zero image
assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the backyard scene and chunky buttons are drawn with no
  image files used

### Requirement: Score and records
The app SHALL save the farthest wave reached and the most bugs bonked
in one siege in local storage, update them only when improved, show a
NEW BEST banner on improvement, and keep them across reloads. Save
failures SHALL NOT break the game.

#### Scenario: New best
- **WHEN** a siege beats the saved wave or bonk record
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker siege keeps records
- **WHEN** a siege ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best wave and bonk record are shown

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into build and wave phases and
on to the fort-fell result screen, with a defend-again action that
starts a fresh siege. A clear-records action SHALL reset saved records
and confirm with a toast.

#### Scenario: Defend again
- **WHEN** the player takes the defend-again action from the result
  screen
- **THEN** a fresh siege starts with a full fort and starting crumbs

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
