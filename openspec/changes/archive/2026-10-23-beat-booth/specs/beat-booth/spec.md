# Spec Delta

## Purpose

Beat Booth is the neon rhythm game for the showcase: the player is
the DJ at a CRT-lit club, notes rush four glowing lanes toward a hit
line, and clean strikes on the beat keep the crowd roaring through
an original synthesized set — every tune invented in code.

## ADDED Requirements

### Requirement: The set
The game SHALL run a timed set on a 120 BPM beat clock where notes
travel down four lanes toward a hit line, and the set ends when the
track finishes or the crowd empties.

#### Scenario: notes ride the lanes
- **WHEN** the set is playing
- **THEN** notes travel from the top of the canvas toward the hit
  line at the bottom, each arriving exactly on its beat

#### Scenario: the set runs to the end of the track
- **WHEN** the last note of the 16-bar track has passed the hit line
- **THEN** the game ends the set and shows the result screen

#### Scenario: the crowd can end the set early
- **WHEN** the crowd meter empties before the track is done
- **THEN** the game ends the set early with a "the crowd went home"
  result

### Requirement: Hitting the beat
The game SHALL judge a lane press against the nearest unjudged note
in that lane as PERFECT (within 60 ms), HIT (within 120 ms), or MISS
when a note passes unstruck.

#### Scenario: a perfect strike
- **WHEN** the player presses a lane key within 60 ms of a note
  crossing the hit line
- **THEN** the note scores a PERFECT hit, the pad flashes, and the
  streak counts up

#### Scenario: a close strike
- **WHEN** the player presses a lane key 61–120 ms from the note
- **THEN** the note scores a HIT for fewer points and the streak
  counts up

#### Scenario: an unstruck note
- **WHEN** a note passes more than 120 ms beyond its hit time with
  no press
- **THEN** the note scores a MISS, the streak resets to zero, and
  the crowd meter drops

### Requirement: Streaks and the crowd
The game SHALL score hits with a streak multiplier that grows to 4×,
and keep a crowd meter that fills on hits and drains on misses.

#### Scenario: the streak multiplies
- **WHEN** clean hits stack up without a miss
- **THEN** the multiplier grows every 10 streak (1× to 4×) and the
  score climbs faster

#### Scenario: a miss cuts the crowd
- **WHEN** a note is missed
- **THEN** the crowd meter loses ground and the room's glow dims

### Requirement: Original synth beats
The game SHALL generate its music in code with the browser's Web
Audio — kick, snare, hat, and bass patterns plus hit sounds — with
no audio files and no real songs.

#### Scenario: the beat plays from code
- **WHEN** the set is playing in a browser with audio
- **THEN** synthesized drum and bass sounds play on their beats

#### Scenario: silent browsers still play
- **WHEN** audio is unavailable
- **THEN** the game runs normally with the visual beat cues alone

### Requirement: CRT synth presentation
The game SHALL look like a neon club on a giant CRT: scanlines and
flicker over glowing lanes, pads, and notes, drawn with zero image
assets and the house palette variables.

#### Scenario: the club is drawn in code
- **WHEN** the game paints the canvas
- **THEN** lanes, notes, hit line, pads, HUD, and a scanline overlay
  are drawn with canvas calls and no images

#### Scenario: the light show rides the crowd
- **WHEN** the crowd meter is high
- **THEN** the neon glow brightens with it

### Requirement: Score and records
The game SHALL keep house records `bestScore` and `bestStreak` under
key `beat-booth:v1`, banner NEW BEST only on improvement, survive
reload, and reset via CLEAR RECORDS.

#### Scenario: a new best banners and saves
- **WHEN** a set ends with a top score or longest streak
- **THEN** the records update, the NEW BEST banner shows, and the
  values persist across reload

#### Scenario: a weaker set keeps the old records
- **WHEN** a set ends below the saved bests
- **THEN** the records stay and no banner shows

#### Scenario: clearing records
- **WHEN** the player presses CLEAR RECORDS
- **THEN** the records reset, a toast confirms it, and a broken
  save can never crash the game

### Requirement: Run flow and recovery
The game SHALL boot to a ready screen and loop ready → playing →
over → play again, with keys and on-screen controls, and toasts that
ride under the HUD without covering the lanes or controls.

#### Scenario: from ready to the drop
- **WHEN** the player presses the start control on the ready screen
- **THEN** a fresh set begins at the top of the track

#### Scenario: play again
- **WHEN** the set ends and the player presses play again
- **THEN** a brand-new set starts with streak and crowd reset
