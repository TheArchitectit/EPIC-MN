# Spec Delta

## Purpose

A neon puzzle workshop where students build their own mazes and then solve
them: paint glowing walls, hide treasures, and race a light-cycle ball to
the goal beacon with arrows or clicks — designing and playing in one file.

## ADDED Requirements

### Requirement: Build mode tools
The app SHALL provide a build mode on a 15×15 grid with tools to paint and
erase walls, place one ball start, one goal flag, and up to five treasures,
plus a clear-board action that removes everything.

#### Scenario: Paint and erase walls
- **WHEN** the player paints a cell with the wall tool and later erases it
- **THEN** the cell becomes a wall or an open path accordingly

#### Scenario: Place start, goal, and treasures
- **WHEN** the player uses the start, goal, or treasure tool on an open cell
- **THEN** the ball start, the goal flag, or a treasure appears there, with treasures capped at five

#### Scenario: Clear the board
- **WHEN** the player presses the clear-board action
- **THEN** all walls, treasures, the start, and the goal are removed

### Requirement: Maze validation before play
The app SHALL refuse to start solving unless a start and a goal exist and
open cells connect them, and SHALL explain what is missing.

#### Scenario: Missing pieces block play
- **WHEN** the player presses play with no start or goal, or with them disconnected
- **THEN** solving does not start and a message explains the problem

#### Scenario: Connected maze starts
- **WHEN** the start and goal exist and open cells connect them
- **THEN** solving starts with the ball at the start cell

### Requirement: Ball steering with arrows and clicks
In solve mode the app SHALL move the ball one cell per arrow key or WASD
press into an open cell, refusing walls and grid edges without penalty. In
solve mode, clicking any cell SHALL move the ball one step toward that
cell along the dominant direction when that step is open.

#### Scenario: Arrow key steps
- **WHEN** the player presses an arrow key in solve mode and the next cell is open
- **THEN** the ball moves one cell and the step counter increases by one

#### Scenario: Wall blocks the ball
- **WHEN** the player steers into a wall or off the grid
- **THEN** the ball stays put and the step counter does not increase

#### Scenario: Click to roll toward a cell
- **WHEN** the player clicks a cell away from the ball in solve mode
- **THEN** the ball takes one step toward that cell along the dominant direction if the step is open

### Requirement: Treasures and goal
The app SHALL let the ball collect treasures with a sparkle and a count
increase, and SHALL end the run with a win screen showing time, steps, and
treasures when the ball reaches the goal.

#### Scenario: Collect a treasure
- **WHEN** the ball enters a cell holding a treasure
- **THEN** the treasure is collected with a sparkle and the treasure count increases

#### Scenario: Reach the goal
- **WHEN** the ball reaches the goal cell
- **THEN** the run ends with a win screen showing the time, steps, and treasures collected

### Requirement: Scoring and best runs
The app SHALL measure each run's elapsed time and steps and SHALL save the
best (lowest) time and fewest steps per maze in local storage, updating
them only when better. Best runs SHALL survive a page reload, and save
failures SHALL NOT break the game.

#### Scenario: New best run
- **WHEN** a run finishes with a better time or fewer steps than the saved bests for that maze
- **THEN** the improved bests are saved and a NEW BEST banner is shown

#### Scenario: Weaker run keeps old bests
- **WHEN** a run finishes with a worse time and more steps than the saved bests
- **THEN** the saved bests stay unchanged

#### Scenario: Reload keeps bests
- **WHEN** the page is reloaded after a best run is saved
- **THEN** the same bests are shown for that maze

### Requirement: Neon grid presentation
The app SHALL render a dark grid with glowing wireframe walls, a light-cycle
ball with a fading trail, a pulsing goal beacon, and sparkling treasures,
all drawn in code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the glowing grid, wall cells, ball, goal beacon, and treasures are drawn with no image files used

### Requirement: Mode switching and recovery
The app SHALL switch between build and solve modes and return to editing
the unchanged maze after a win. A reset-run action SHALL return the ball
to the start with time, steps, and treasures reset. A clear-records action
SHALL clear saved bests and confirm with a toast.

#### Scenario: Back to editing
- **WHEN** the player chooses to edit after winning
- **THEN** the maze returns to build mode with the maze unchanged

#### Scenario: Reset run
- **WHEN** the player presses the reset-run action in solve mode
- **THEN** the ball returns to the start and the run's time, steps, and treasures reset

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved bests are cleared and a toast confirms it
