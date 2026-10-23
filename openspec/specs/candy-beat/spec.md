# candy-beat Specification

## Purpose
Candy Beat is the candy-80s rhythm auto-runner for the showcase: the
hero runs through a pixel arcade-cabinet world on the beat, one tap
jumps the gaps, pop-up beat-orbs beg to be grabbed, and the dance-
floor crowd grades every tap until the cabinet is cleared or the
lights go out.

## Requirements

### Requirement: The run
The game SHALL run an auto-scrolling track on a 120 BPM beat clock
through the arcade-cabinet world, ending when the hero reaches the
end of the track or the crowd empties.

#### Scenario: the world scrolls to the music
- **WHEN** the run is going
- **THEN** the hero runs in place while mountains, ground, and
  hazards slide past on the beat clock

#### Scenario: the track runs to the finish
- **WHEN** the song clock passes the end of the 32-bar track
- **THEN** the game ends the run with a "cabinet cleared" result

#### Scenario: the lights can go out early
- **WHEN** the crowd meter empties before the track is done
- **THEN** the game ends the run early with a "lights went out"
  result

### Requirement: One-tap jumping
The game SHALL make the single TAP control (space, up-arrow, click,
or the on-screen JUMP button) jump the hero from the ground, clearing
gaps, spikes, and pipes, and stumbling on a hit.

#### Scenario: a tap jumps
- **WHEN** the player taps while the hero is on the ground
- **THEN** the hero leaps and lands again under gravity

#### Scenario: clearing a hazard
- **WHEN** the hero jumps over a gap, spike, or pipe
- **THEN** the run continues unbroken and the score keeps climbing

#### Scenario: a stumble
- **WHEN** a hazard catches the hero on the ground
- **THEN** the hero stumbles (crowd drops, brief flash of mercy),
  then runs on — no instant game over

### Requirement: Pop-up beat-orbs
The game SHALL pop candy beat-orbs up along the route at jump height
that vanish again if ungrabbed, and score bonus when the hero flies
through one.

#### Scenario: an orb pops up
- **WHEN** the hero's run brings a beat-orb into view
- **THEN** the orb glows at jump height for a moment, then vanishes
  if ungrabbed

#### Scenario: grabbing an orb
- **WHEN** the hero touches a beat-orb mid-run
- **THEN** the orb scores bonus points, a star burst flashes, and
  the crowd cheers up

### Requirement: On-beat judgment and the dance floor
The game SHALL grade every tap against the nearest beat as ON BEAT
(within 90 ms), CLOSE (within 180 ms), or OFF BEAT, feeding a
dance-floor crowd meter and a streak multiplier up to 4×.

#### Scenario: tapping on the beat
- **WHEN** a tap lands within 90 ms of the beat
- **THEN** the streak climbs, the score multiplies, the crowd fills,
  and a star burst flashes

#### Scenario: sloppy timing dims the room
- **WHEN** a tap lands more than 180 ms off the beat
- **THEN** the streak resets and the crowd meter drops

#### Scenario: the crowd rides the groove
- **WHEN** the crowd meter is high
- **THEN** the candy flash burns brighter; when it is low, the room
  dims toward dark

### Requirement: Candy-80s presentation
The game SHALL look like a candy-colored coin-op: pixel mountains,
pipes, star fields, and star-burst flashes in hot pink, electric
blue, and lemon yellow — drawn with zero image assets and the house
palette variables.

#### Scenario: the cabinet is drawn in code
- **WHEN** the game paints the canvas
- **THEN** sky, stars, mountains, ground, hazards, hero, orbs, HUD,
  and star bursts are drawn with canvas calls and no images

#### Scenario: perfect taps explode in candy flash
- **WHEN** a tap grades ON BEAT
- **THEN** a star burst in candy colors flashes at the hero

### Requirement: Score and records
The game SHALL keep house records `bestScore` and `bestStreak` under
key `candy-beat:v1`, banner NEW BEST only on improvement, survive
reload, and reset via CLEAR RECORDS.

#### Scenario: a new best banners and saves
- **WHEN** a run ends with a top score or longest on-beat streak
- **THEN** the records update, the NEW BEST banner shows, and the
  values persist across reload

#### Scenario: a weaker run keeps the old records
- **WHEN** a run ends below the saved bests
- **THEN** the records stay and no banner shows

#### Scenario: clearing records
- **WHEN** the player presses CLEAR RECORDS
- **THEN** the records reset, a toast confirms it, and a broken
  save can never crash the game

### Requirement: Run flow and recovery
The game SHALL boot to a ready screen and loop ready → running →
over → play again, with keys and on-screen controls, and toasts that
ride under the HUD without covering the track or controls.

#### Scenario: from ready to the run
- **WHEN** the player presses the start control on the ready screen
- **THEN** a fresh run begins at the top of the track

#### Scenario: play again
- **WHEN** the run ends and the player presses play again
- **THEN** a brand-new run starts with streak and crowd reset

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
