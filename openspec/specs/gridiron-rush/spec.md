# gridiron-rush Specification

## Purpose
A retro pro-football arcade match on a crisp classic gridiron: the
player quarterbacks the blue Comets against the CPU Stampede — snap
the ball, steer the run with the arrows, fire passes to three
receivers with one button each, and on defense steer the star tackler
into the ball carrier for the stop. Short quarters, touchdowns worth
seven, and a final scoreboard that begs for a rematch.

## Requirements

### Requirement: The match
The app SHALL run a four-quarter arcade football game between the
Comets and the Stampede, ticking a quarter clock while a play is live,
scoring touchdowns for either team, and ending at the final whistle
with a result screen showing the final score.

#### Scenario: Quarters tick down
- **WHEN** a play is live
- **THEN** the game clock counts down through the quarters toward the
  final whistle

#### Scenario: Touchdowns score points
- **WHEN** a ball carrier crosses the goal line
- **THEN** seven points are added to the scoring team's total

#### Scenario: The final whistle decides
- **WHEN** the fourth-quarter clock reaches zero
- **THEN** the match ends and the result screen shows the final score
  and which team won

### Requirement: Run and throw offense
The app SHALL snap the ball into a live play where directional controls
steer the ball carrier, and SHALL let the player throw to any of three
receivers with a per-receiver throw control — a completed pass hands
control to the catch-maker, who keeps running until tackled.

#### Scenario: Steering runs the ball
- **WHEN** the player holds a directional control while carrying the
  ball
- **THEN** the ball carrier runs across the field in that direction

#### Scenario: A pass finds the receiver
- **WHEN** the player throws to a receiver who is open
- **THEN** the pass is completed and the player controls the receiver
  running with the ball

#### Scenario: Yards are gained
- **WHEN** a play ends by tackle
- **THEN** the ball is placed at the spot and the yards gained are
  counted toward the next down

### Requirement: Defense
The app SHALL put the player on defense when the Stampede have the
ball, steering the star defender with the directional controls, and
SHALL end the Stampede play when the ball carrier is tackled.

#### Scenario: The star defender tackles
- **WHEN** the player steers the star defender into the Stampede ball
  carrier
- **THEN** the play ends and the Stampede are stopped at that spot

### Requirement: Plays and scoring
The app SHALL let the player pick a run, pass, or deep play at the
line, SHALL award a new set of downs when ten yards are gained, and
SHALL turn the ball over when four downs pass without ten yards. A
juke SHALL give the ball carrier a burst of speed that is harder to
tackle.

#### Scenario: Four downs decide the drive
- **WHEN** the offense fails to gain ten yards in four downs
- **THEN** the ball is turned over to the other team

#### Scenario: The juke slips the tackle
- **WHEN** the player triggers a juke while carrying the ball
- **THEN** the carrier bursts forward and is harder to tackle for a
  moment

### Requirement: Gridiron classic presentation
The app SHALL render a classic football gridiron — green turf with
stripes, white yard lines and hash marks, painted end zones, goal
posts, and chunky helmeted players — all drawn in code with zero image
assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the gridiron scene and chunky buttons are drawn with no
  image files used

### Requirement: Score and records
The app SHALL save the best win margin and the most touchdowns in one
match in local storage, update them only when improved, show a NEW
BEST banner on improvement, and keep them across reloads. Save
failures SHALL NOT break the game.

#### Scenario: New best
- **WHEN** a match beats the saved win margin or touchdown record
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker match keeps records
- **WHEN** a match ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best margin and touchdown record are shown

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the match and on to the
final-whistle result screen, with a play-again action that starts a
fresh match. A clear-records action SHALL reset saved records and
confirm with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from the result
  screen
- **THEN** a fresh match starts

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
