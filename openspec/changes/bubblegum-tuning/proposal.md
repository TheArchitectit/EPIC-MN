# Proposal

## Why

The owner played Bubblegum Zap and found the base speed too frantic for a
first touch. They want the game to feel calmer while keeping the fun: slow
the action down by about 50%, and give each round a fixed **1-minute
timed** length so it's a quick, snackable experience.

## What Changes

- Bubble motion and spawn pacing slow to ~50% of current values (a relaxed
  "chill" feel, still frenzy-like as score climbs).
- A visible round timer counts down from 1:00; when it hits zero, the round
  ends with a time-up game-over screen (the old "miss too many" ending
  stays as a second way to lose).
- Restart starts a fresh 1-minute round.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `bubblegum-zap`: the spawn & zap behavior slows by 50%; end-of-play now
  includes the timed 1-minute ending.

## Impact

- Code: small edits inside `bubblegum.html` (speed constants, spawn pacing,
  timer HUD, game-over reason).
- Data: no change — best score persistence untouched.
