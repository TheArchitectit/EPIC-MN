# Spec Delta

## ADDED Requirements

### Requirement: Retro chiptune music
The game SHALL synthesize a looping, classic arcade-style chiptune using
WebAudio (no audio files, no network) and SHALL begin playing after the
player's first interaction. A toggle control SHALL let the player mute and
unmute the music at any time.

#### Scenario: Music starts after first interaction
- **WHEN** the player clicks or taps the game for the first time
- **THEN** the synth loop starts playing quietly

#### Scenario: Toggle music on/off
- **WHEN** the player clicks the music toggle
- **THEN** the music stops; clicking again resumes it from the loop point
