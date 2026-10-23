# cop-chase Specification

## Purpose
A retro-neon arcade cop chase where the player drives a getaway car
down a glowing pixel highway — gas and brake set the speed, steering
weaves through traffic, checkpoint gates add time on the arcade clock,
and pixel police cars close in from behind until clever braking makes
them overshoot. Dodge, accelerate, and see how long the chase can last.

## Requirements

### Requirement: Gas, brake, and steering
The app SHALL let the player set the getaway car's speed with gas and
brake controls and steer left or right between lanes, using arrow keys
or on-screen buttons, with gas raising speed toward a maximum and brake
lowering it toward a minimum.

#### Scenario: Gas accelerates
- **WHEN** the player holds the gas control while driving
- **THEN** the car's speed climbs toward the maximum

#### Scenario: Brake slows the car
- **WHEN** the player holds the brake control while driving
- **THEN** the car's speed falls toward the minimum

#### Scenario: Steering changes lanes
- **WHEN** the player presses a left or right steer control
- **THEN** the car slides toward the neighboring lane

### Requirement: Highway, traffic, and the arcade clock
The app SHALL scroll a multi-lane highway of civilian traffic that the
player dodges, SHALL run a countdown clock, and SHALL add bonus time at
checkpoint gates. When the clock reaches zero the run SHALL end.

#### Scenario: Traffic scrolls by
- **WHEN** the run is active
- **THEN** civilian cars travel the highway and the player's car can weave around them

#### Scenario: Checkpoints add time
- **WHEN** the car passes a checkpoint gate
- **THEN** bonus seconds are added to the countdown clock and a message confirms it

#### Scenario: Out of time
- **WHEN** the countdown clock reaches zero
- **THEN** the run ends with an out-of-time result

### Requirement: Cops on your tail
The app SHALL pursue the player with pixel police cars that close in
from behind, SHALL let a hard brake when a cop is close make the cop
overshoot and fall back, SHALL tighten the pursuit when the player
crashes into traffic, and SHALL end the run when a cop catches the
player.

#### Scenario: Cops close in
- **WHEN** the run is active and the player does not shake the pursuit
- **THEN** the pursuing cop gains ground on the player's car

#### Scenario: Brake makes the cop overshoot
- **WHEN** the player brakes hard while a cop is close behind
- **THEN** the cop overshoots and falls back, giving the player breathing room

#### Scenario: Crash tightens the net
- **WHEN** the player's car crashes into civilian traffic
- **THEN** the car slows down and the pursuing cop closes in

#### Scenario: Busted
- **WHEN** a cop catches the player's car
- **THEN** the run ends with a busted result

### Requirement: Score and records
The app SHALL score the run by distance driven and near-misses with
traffic, and SHALL save the best score and best distance in local
storage, updating them only when improved and keeping them across
reloads. Save failures SHALL NOT break the game.

#### Scenario: New best
- **WHEN** a run beats the saved best score or best distance
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker run keeps records
- **WHEN** a run ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best score and best distance are shown

### Requirement: Neon pixel presentation
The app SHALL render a retro-neon night highway with blocky pixel cars,
flashing police lights, glowing edges, and CRT scanlines — all drawn in
code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the neon pixel chase scene and chunky buttons are drawn with no image files used

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the chase and on to the
result screen, with a play-again action that starts a fresh run. A
clear-records action SHALL reset saved records and confirm with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from the result screen
- **THEN** a fresh chase starts with the car on the highway

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
