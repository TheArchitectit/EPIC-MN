# Spec Delta

## Purpose

An autumn ghost-train rail shooter where a rickety train rolls through
golden corn rows while spooky-lite frights pop up at the windows —
pan the view left and right along the train, shoot the grinning
pumpkins and clumsy scarecrows before they duck away, and chain hits
into combo multipliers for the best score of the ride.

## ADDED Requirements

### Requirement: Ghost train ride
The app SHALL run a finite ghost-train ride through the autumn night,
scrolling the harvest scenery past while frights pop up into view and
duck away again if they are not hit, and SHALL end the ride at the
harvest barn with a ride-complete screen.

#### Scenario: The train rolls on
- **WHEN** the ride is active
- **THEN** the autumn scenery slides past and the ride makes progress toward the barn

#### Scenario: Frights pop out and duck away
- **WHEN** a fright rises into the player's view and is not shot in time
- **THEN** it ducks away and the player's chance to hit it is gone

#### Scenario: Ride complete
- **WHEN** the train reaches the harvest barn
- **THEN** the ride ends and the ride-complete screen shows the final score

### Requirement: Pan and shoot
The app SHALL pan the view left or right along the train with arrow
keys or on-screen buttons, and SHALL fire at the crosshair with a click
or tap, hitting frights that are up in the open. Some frights SHALL
take a second shot to pop.

#### Scenario: Panning shifts the view
- **WHEN** the player presses a left or right pan control
- **THEN** the view slides toward that side of the train

#### Scenario: A shot hits an open fright
- **WHEN** the player fires at a fright that is up in the open
- **THEN** the fright is hit and reacts

#### Scenario: Tough frights need two shots
- **WHEN** the player hits a tough fright once
- **THEN** it stays up damaged and a second shot pops it

### Requirement: Hits and combos
The app SHALL score each popped fright with points times the combo
multiplier and raise the multiplier after each hit, and SHALL drop the
chain back to one when a shot hits nothing.

#### Scenario: Hits bank the combo
- **WHEN** the player pops a fright
- **THEN** points times the combo multiplier are added to the score and the multiplier grows

#### Scenario: A miss drops the chain
- **WHEN** the player fires at nothing
- **THEN** the combo multiplier resets to one

### Requirement: Score and records
The app SHALL save the best score and the best combo multiplier of one
ride in local storage, update them only when improved, show a NEW BEST
banner on improvement, and keep them across reloads. Save failures
SHALL NOT break the game.

#### Scenario: New best
- **WHEN** a ride beats the saved best score or best combo
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker ride keeps records
- **WHEN** a ride ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best score and best combo are shown

### Requirement: Autumn harvest presentation
The app SHALL render a golden autumn night — dusk sky, scrolling corn
rows, hay bales, falling leaves, a wooden ghost train, and goofy
lantern-lit frights — all drawn in code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the autumn harvest scene and chunky buttons are drawn with no image files used

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the ride and on to the
ride-complete screen, with a ride-again action that starts a fresh
ride. A clear-records action SHALL reset saved records and confirm
with a toast.

#### Scenario: Ride again
- **WHEN** the player takes the ride-again action from the result screen
- **THEN** a fresh ghost-train ride starts

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
