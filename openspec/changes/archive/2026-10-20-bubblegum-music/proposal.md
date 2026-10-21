# Proposal

## Why

The owner wants the game to feel like a classic arcade cabinet. Real music
files are off-limits (no assets, no internet), so we synthesize a retro
chiptune loop live in the browser with WebAudio — a small square-wave bass,
a triangle lead, and a noise hat, sequenced in a loop.

## What Changes

- A synthesized chiptune loop plays during play, starting after the first
  interaction (browsers require a gesture before audio).
- A "🎵" toggle button turns music on/off at any time.
- No audio files, no network — everything generated in code.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `bubblegum-zap`: the game gains synthesized retro background music and a
  music toggle.

## Impact

- Code: edits inside `bubblegum.html` (WebAudio sequencer + toggle button).
- Data: unchanged.
