# Spec Delta

## Purpose

A storybook pixel pet game where students hatch an egg, train a wiggly
pet through timing and memory trick exercises, and star together in a
talent show scored with hand-drawn stars — a coaching friendship drawn
on cream paper and ink.

## ADDED Requirements

### Requirement: Hatching a pet
The app SHALL let the player choose one of three storybook eggs, warm it
with a hatch action, and hatch a named chunky-pixel pet whose colors come
from the egg. The player SHALL be able to rename the pet, and the pet
SHALL survive a page reload.

#### Scenario: Choose and warm an egg
- **WHEN** the player picks an egg and warms it to the hatch mark
- **THEN** the egg hatches into a pet colored after that egg

#### Scenario: Name the pet
- **WHEN** the player types a new name and confirms it
- **THEN** the pet is called by that name everywhere in the app

#### Scenario: Reload keeps the pet
- **WHEN** the page is reloaded after hatching
- **THEN** the same named pet is waiting at home

### Requirement: Tap-timing tricks
The app SHALL run tap-timing tricks (dance, jump rope) where a marker
slides along a timing bar and each tap of SPACE or a click is graded
PERFECT, GOOD, or FLOP by distance from the sweet spot. Flops SHALL play
as funny stumbles that never block the game.

#### Scenario: Perfect tap
- **WHEN** the player taps while the marker sits in the sweet spot
- **THEN** the tap grades PERFECT and the pet performs a graceful move

#### Scenario: Flop tap
- **WHEN** the player taps far from the sweet spot
- **THEN** the tap grades FLOP and the pet stumbles comically without penalty

### Requirement: Memory tricks
The app SHALL run memory tricks where the pet demonstrates a sequence of
moves (spin, jump, clap) one at a time and the player repeats the
sequence with move buttons or keys. A wrong move SHALL end the round with
a friendly try-again message.

#### Scenario: Repeat the sequence
- **WHEN** the pet shows a move sequence and the player repeats each move in order
- **THEN** the round is passed and the player earns practice credit

#### Scenario: Wrong move
- **WHEN** the player presses a move that breaks the sequence
- **THEN** the round ends with a try-again message and the game continues

### Requirement: Training day
The app SHALL run a training day of three exercises that mix both trick
styles (a dance timing trick, a memory tricks round, and a jump-rope
timing trick). Each exercise SHALL award one to five practice stars, and
finishing all three SHALL unlock the talent show.

#### Scenario: Mixed practice
- **WHEN** the player starts a training day
- **THEN** three exercises play in order, mixing timing and memory styles

#### Scenario: Training unlocks the show
- **WHEN** the player finishes all three exercises
- **THEN** the talent show unlocks and practice stars are summarized

### Requirement: Talent show
The app SHALL perform the day's three tricks as stage acts, awarding one
to five stars per act, a total score, and an ENCORE banner when the show
earns twelve or more stars.

#### Scenario: Scored acts
- **WHEN** an act finishes at the talent show
- **THEN** it earns one to five stars that add to the show's total score

#### Scenario: Encore finish
- **WHEN** the show's acts total twelve or more stars
- **THEN** an ENCORE banner celebrates the great show

### Requirement: Best show records
The app SHALL save the pet's best (highest) show score in local storage,
update it only when beaten, show a NEW BEST banner on improvement, and
keep it across page reloads. Save failures SHALL NOT break the game.

#### Scenario: New best show
- **WHEN** a show beats the saved best score
- **THEN** the new best is saved and a NEW BEST banner appears

#### Scenario: Weaker show keeps the record
- **WHEN** a show scores below the saved best
- **THEN** the saved best stays unchanged

#### Scenario: Reload keeps the record
- **WHEN** the page is reloaded after a best show
- **THEN** the same best score is shown at home

### Requirement: Storybook pixel presentation
The app SHALL render a cream-paper world with ink outlines, a chunky
pixel pet drawn in code, stamped-wood buttons, and hand-drawn scribble
stars, with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the paper page, pixel pet, wood buttons, and scribble stars are drawn with no image files used

### Requirement: Screen flow and recovery
The app SHALL flow between hatch, home, training, show, and result
screens with a way back home at any time. A new-pet action SHALL reset
the pet and records after confirming with a toast.

#### Scenario: Back home
- **WHEN** the player presses home from a result screen
- **THEN** the pet returns to the home page with progress intact

#### Scenario: New pet
- **WHEN** the player takes the new-pet action
- **THEN** the pet and records reset and a toast confirms it
