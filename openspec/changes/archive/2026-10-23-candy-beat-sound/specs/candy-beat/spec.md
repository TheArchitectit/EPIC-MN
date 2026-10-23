# Spec Delta

## Purpose

Candy Beat computes a full beat groove and action sounds, but real
browsers keep the speaker muted until the game unlocks it from inside
the player's first input — so the shipped game played in silence.
This delta contracts for sound the player can actually hear.

## ADDED Requirements

### Requirement: Sound plays while you run

The game SHALL unlock the browser's audio on the player's first
input and play its synthesized groove and action sounds, and SHALL
keep running silently when no audio is available.

#### Scenario: the first input unlocks the speaker
- **WHEN** the player gives any first input (key, canvas tap, or
  button press)
- **THEN** the browser audio is resumed and the game's sounds are
  audible from then on

#### Scenario: the groove plays on the clock
- **WHEN** beats pass during the run
- **THEN** kick, snare, hat, and bass play on the beat clock

#### Scenario: every action sounds off
- **WHEN** the hero jumps, grabs a beat-orb, or stumbles
- **THEN** the matching jump, sparkle, or stumble sound plays

#### Scenario: silent browsers still run
- **WHEN** the browser offers no audio support
- **THEN** the run continues on visual cues alone, with no error and
  no missing game behavior
