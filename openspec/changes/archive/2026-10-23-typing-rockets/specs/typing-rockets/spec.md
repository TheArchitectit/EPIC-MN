# Spec Delta

## Purpose

Typing practice disguised as an 80s arcade time trial: words fuel a neon
rocket toward the finish line, races are beat-the-clock, and saved best
times keep students flying again until typing feels like a superpower.

## ADDED Requirements

### Requirement: Race setup and track choice
The app SHALL offer at least three named tracks and a start action. A race
SHALL begin on start with the rocket at the launchpad, the clock at zero,
and the first fuel word shown, and SHALL end when the rocket reaches the
finish line.

#### Scenario: Pick a track and launch
- **WHEN** the player picks a track and presses the start action
- **THEN** the race begins at the launchpad with the clock at zero and the first fuel word shown

#### Scenario: Reach the finish
- **WHEN** the rocket reaches the finish line
- **THEN** the race ends, the final time is shown, and the player may fly again

### Requirement: Word-fuel typing
The app SHALL display one fuel word at a time. Correct letters SHALL advance
the word and push the rocket forward. A wrong letter SHALL NOT advance the
word and SHALL trigger a brief engine sputter that slows the rocket without
losing any progress. Completing a word SHALL add a fuel burst and show the
next word.

#### Scenario: Correct letters fuel the rocket
- **WHEN** the player types the next letter of the current word correctly
- **THEN** the caret advances, a spark burst shows, and the rocket gains speed and progress

#### Scenario: Typo makes the engine sputter
- **WHEN** the player types a wrong letter
- **THEN** the word does not advance, the engine sputters briefly, and no progress is lost

#### Scenario: Word complete
- **WHEN** the player finishes typing the current word
- **THEN** a fuel burst is added and the next fuel word appears

### Requirement: Rotating word pools
The app SHALL draw fuel words from three pools — space, school spelling, and
silly — rotating to the next pool for each new word. Words SHALL be at least
three letters long.

#### Scenario: Pools rotate
- **WHEN** each new fuel word is chosen
- **THEN** it comes from the next pool in the space → school → silly rotation

### Requirement: Difficulty ramp
The app SHALL scale fuel-word length with race progress so words are short
near the launchpad and the final stretch of the track uses the longest words
(up to eight letters).

#### Scenario: Final stretch is a boss rush
- **WHEN** the rocket is in the final third of the track
- **THEN** the shown words are longer than the words at launch

### Requirement: Timing and best times
The app SHALL measure each race's elapsed time and SHALL save the best
(lowest) time per track in local storage, updating it only when beaten.
Best times SHALL survive a page reload, and save failures SHALL NOT break
the game.

#### Scenario: New best time
- **WHEN** a race finishes faster than the saved best for that track
- **THEN** the new best is saved and a NEW BEST banner is shown

#### Scenario: Slower race keeps the old best
- **WHEN** a race finishes slower than the saved best for that track
- **THEN** the saved best stays unchanged

#### Scenario: Reload keeps best times
- **WHEN** the page is reloaded after a best time is saved
- **THEN** the same best time is shown on that track

### Requirement: Retro-neon arcade presentation
The app SHALL render a dark starfield with a glowing neon rocket, a
flickering trail flame, a synthwave sun and grid horizon, and a chunky
monospace arcade HUD. All visuals SHALL be drawn in code with zero image
assets.

#### Scenario: Launch screen look
- **WHEN** the app loads
- **THEN** the starfield, sun and grid horizon, neon rocket, and arcade HUD are visible with no image files used

### Requirement: Game controls and recovery
The app SHALL start races with the start action and advance them by typing
letter keys. After a race it SHALL offer a FLY AGAIN action that starts a
fresh race on the same track. A reset action SHALL clear saved best times
and confirm it with a toast.

#### Scenario: Fly again
- **WHEN** the player presses FLY AGAIN on the finish screen
- **THEN** a fresh race starts on the same track with the clock at zero

#### Scenario: Clear records
- **WHEN** the player presses the reset action
- **THEN** saved best times are cleared and a toast confirms it
