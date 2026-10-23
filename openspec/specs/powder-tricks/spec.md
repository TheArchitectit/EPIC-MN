# powder-tricks Specification

## Purpose
A cartoon snowboard trick game where a squishy rider zooms down a puffy
mountain while the player carves between lanes, pops off ramps, and
stacks grabs and flips for combo points — land clean, laugh at the
tumbles, chase the best score.

## Requirements

### Requirement: Carve & pop riding
The app SHALL move the rider down the mountain automatically, speeding
up as the run continues, and SHALL let the player carve left or right
between lanes and pop a jump with the trick control, using arrow keys or
on-screen buttons.

#### Scenario: The rider zooms on
- **WHEN** the run is active and the player steers not at all
- **THEN** the rider keeps descending and the mountain scrolls by

#### Scenario: Carving changes lanes
- **WHEN** the player presses a left or right carve control
- **THEN** the rider slides toward the neighboring lane

#### Scenario: The slope steepens
- **WHEN** the rider has descended a long way
- **THEN** the rider moves faster than at the start of the run

### Requirement: Trick & air
The app SHALL launch the rider into the air when the trick control is
pulled near a ramp, let each extra trick pull mid-air add a grab, flip,
or spin worth growing points, and bank those points times the combo
multiplier on a clean landing, raising the multiplier each clean landing.
A run with four or more tricks in a single air SHALL come down
over-rotated and tumble.

#### Scenario: Tricks stack in the air
- **WHEN** the rider is airborne and pulls the trick control again
- **THEN** another trick is added and the air points grow

#### Scenario: Clean landing banks the combo
- **WHEN** the rider lands with tricks and without over-rotating
- **THEN** the air points times the combo multiplier are added to the score and the multiplier grows

#### Scenario: Too showy
- **WHEN** the rider stacks four or more tricks in one air
- **THEN** the landing is an over-rotated tumble

### Requirement: Mountain hazards and tumbles
The app SHALL tumble the rider when a pine tree is hit, dropping any
unbanked air points and resetting the combo, and SHALL end the run with
a run-over screen after the third tumble.

#### Scenario: Tree tumble
- **WHEN** the rider hits a pine tree
- **THEN** the rider tumbles, the combo resets, and the unbanked air points are lost

#### Scenario: Third tumble ends the run
- **WHEN** the rider tumbles for the third time
- **THEN** the run ends and the run-over screen shows the final score

### Requirement: Score and records
The app SHALL save the best score and the best combo multiplier of one
run in local storage, update them only when improved, show a NEW BEST
banner on improvement, and keep them across reloads. Save failures SHALL
NOT break the game.

#### Scenario: New best
- **WHEN** a run beats the saved best score or best combo
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker run keeps records
- **WHEN** a run ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best score and best combo are shown

### Requirement: Cartoon snow presentation
The app SHALL render a chunky cartoon mountain — puffy snow hills,
squishy pine trees, candy-striped ramps, and a bold-outlined rider —
all drawn in code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the cartoon snow scene and chunky buttons are drawn with no image files used

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the run and on to the
run-over screen, with a play-again action that starts a fresh run. A
clear-records action SHALL reset saved records and confirm with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from the result screen
- **THEN** a fresh run starts with the rider at the top of the slope

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
