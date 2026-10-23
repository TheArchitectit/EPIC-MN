# Proposal

## Why

Candy Beat shipped with a full beat engine — kick, snare, hat, and
bass on the groove, plus jump chirps, orb sparkles, and stumble buzz
— but **the player hears silence**. Real browsers hold the speaker
muted (`AudioContext` stays `suspended`) until the game unlocks it
from inside the player's first input. Nothing in `candy.html` ever
asks for that unlock, so the oscillators fire into a dead speaker
forever. A rhythm game you can't hear isn't a rhythm game — this
change turns the speaker on the moment the player touches the game.

## What Changes

- New `unlockAudio()` helper that resumes the browser audio on the
  player's first input — guarded so it can never throw or break the
  game, idempotent so every later tap is safe.
- Every input path unlocks the speaker: keydown (space/up/W/enter),
  tapping the canvas, the JUMP button, and start/restart buttons.
- The existing groove keeps playing once unlocked: kick/snare/hat/bass
  on the beat clock, jump/orb/stumble blips on the actions.
- Silent-safe stays: with no `AudioContext` at all the run continues
  on visual cues, exactly like before.
- Harness gains unlock tests (stub counts `resume()` calls) and a
  real-browser check (`actx.state` flips to `running` after the first
  key).

## Capabilities

### New Capabilities

( none )

### Modified Capabilities
- `candy-beat`: gains a working, audible sound stage — the beat the
  game already computes finally reaches the player's speakers.

## Impact

- Touches only `candy.html` (audio unlock + tests); no README change
  needed — Example #19's write-up already stands.
- No new dependencies — still plain Web Audio, no audio files.
- **Parked later changes** (named aloud, not built today):
  `candy-beat-tunes` (hummable melodies on top of the beat),
  `candy-beat-costumes` (hero skins and trails), `candy-beat-worlds`
  (new cabinet lands), and `beat-booth-sound` (Beat Booth likely has
  this same mute bug — its own change, another day).
- The sound is all invented synthesis (no real songs), like every
  other showcase app.

## Compliance note

No new names, marks, or songs — the same invented Candy Beat world;
real game and studio marks stay out, as always.
