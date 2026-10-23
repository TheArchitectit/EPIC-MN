# Spec Delta

## Purpose

A classic blacktop streetball arcade match: two tiny 2-on-2 teams share
a sunset court with a basket at each end, the player drives the ball
handler around the asphalt, shakes the defender for an open look, and
shoots — deep shots count three, close shots count two, and drawing a
foul earns timing-tap free throws where swishes in a row build a streak
bonus. The buzzer decides the winner.

## ADDED Requirements

### Requirement: Streetball match
The app SHALL run a timed 2-on-2 blacktop match on a court with a
basket at each end, ticking a countdown clock, adding points when
shots land, and ending at the buzzer with a final result screen.

#### Scenario: The clock ticks down
- **WHEN** the match is running
- **THEN** the game clock counts down toward the buzzer while players
  drive and shoot

#### Scenario: Baskets score points
- **WHEN** a shot lands
- **THEN** two or three points are added to the shooting team's score
  depending on the shot distance

#### Scenario: The buzzer decides
- **WHEN** the clock reaches zero
- **THEN** the match ends and the result screen shows the final score
  and which team won

### Requirement: Drive, shoot, and pass
The app SHALL move the ball handler with directional controls, fire a
shot from the handler's current position with a shoot control, and pass
the ball to the open teammate with a pass control. Shots from beyond
the arc SHALL count three points and closer shots two.

#### Scenario: Driving moves the handler
- **WHEN** the player holds a directional control
- **THEN** the ball handler dribbles across the blacktop in that
  direction

#### Scenario: Distance decides the points
- **WHEN** the ball handler shoots from beyond the arc
- **THEN** the shot is worth three points, and closer shots are worth
  two

#### Scenario: Passing switches the handler
- **WHEN** the player takes the pass control
- **THEN** the ball flies to the teammate and the player controls the
  new ball handler

### Requirement: Open looks and defenders
The app SHALL keep a defender on the ball handler, make guarded shots
harder to land than open shots, and give the handler a turbo burst that
can shake the defender for an open look.

#### Scenario: Guarded shots are bricks
- **WHEN** the ball handler shoots while the defender is glued on
- **THEN** the shot is much less likely to land than an open look

#### Scenario: The burst creates space
- **WHEN** the player bursts away from the defender and shoots from
  the open
- **THEN** the shot uses the better open-look odds

### Requirement: Free-throw streaks
The app SHALL award a timing-tap free throw when a guarded shot draws a
foul, bank a streak bonus on the match score for each consecutive made
free throw, and reset the streak when a free throw misses.

#### Scenario: A foul earns a free throw
- **WHEN** a guarded shot draws a foul
- **THEN** play pauses for a free throw the player takes with one
  well-timed tap

#### Scenario: Streaks bank bonus points
- **WHEN** the player makes consecutive free throws
- **THEN** each make banks a growing streak bonus on the match score

#### Scenario: A miss resets the streak
- **WHEN** a free throw misses
- **THEN** the streak bonus resets to zero

### Requirement: Blacktop streetball presentation
The app SHALL render a sunset streetball court — asphalt with painted
lines, chain-link fence, city skyline, rim and net, chunky streetballer
players — all drawn in code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the blacktop scene and chunky buttons are drawn with no
  image files used

### Requirement: Score and records
The app SHALL save the best win margin and the longest free-throw
streak in local storage, update them only when improved, show a NEW
BEST banner on improvement, and keep them across reloads. Save failures
SHALL NOT break the game.

#### Scenario: New best
- **WHEN** a match beats the saved win margin or free-throw streak
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker match keeps records
- **WHEN** a match ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best margin and best streak are shown

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the match and on to the
buzzer result screen, with a play-again action that starts a fresh
match. A clear-records action SHALL reset saved records and confirm
with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from the result
  screen
- **THEN** a fresh match starts

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
