# Spec Delta

## Purpose

A retro-neon delivery runner where the hero auto-runs up a synthwave
highway while the player steers between glowing traffic lanes, keeping a
wobbly pizza intact until the customer — cross each block, bank the tip,
survive the faster night.

## ADDED Requirements

### Requirement: Auto-run steering
The app SHALL move the hero forward up the highway automatically, and
SHALL let the player steer the hero left or right between lanes using
arrow keys or on-screen steer buttons.

#### Scenario: The hero runs on
- **WHEN** the run is active and the player steers not at all
- **THEN** the hero keeps running forward and the highway scrolls by

#### Scenario: Steering changes lanes
- **WHEN** the player presses a left or right steer control
- **THEN** the hero slides toward the neighboring lane

### Requirement: Wobbly delivery box
The app SHALL carry a pizza on the hero that slides toward a bump when
traffic grazes the hero and loses integrity on every bump; the pizza
SHALL slide gently back toward the center while the hero runs clean, and
the run SHALL end in a lost delivery when the pizza slides off the box or
loses all integrity.

#### Scenario: Bump makes it slide
- **WHEN** a car grazes the hero
- **THEN** the pizza slides toward the hit and loses some integrity

#### Scenario: Smooth running keeps it steady
- **WHEN** the hero runs without bumps for a while
- **THEN** the pizza slides gently back toward the center of the box

#### Scenario: Pizza lost
- **WHEN** the pizza slides off the box or its integrity reaches zero
- **THEN** the run ends with a lost-delivery screen

### Requirement: Neon traffic
The app SHALL stream neon cars and long trucks across the highway lanes
in both directions at mixed speeds, growing denser and faster with each
block.

#### Scenario: Traffic streams
- **WHEN** the run is active
- **THEN** glowing vehicles cross the road in both directions at different speeds

#### Scenario: Traffic escalates
- **WHEN** the player enters a later block
- **THEN** vehicles come faster and closer together than in the block before

### Requirement: Blocks, deliveries, and score
The app SHALL count a delivery each time the hero completes a block,
award a score of a delivery bonus plus a tip scaled by how intact the
pizza is, and move the hero into a harder next block.

#### Scenario: Delivery made
- **WHEN** the hero reaches the end of a block with pizza still aboard
- **THEN** a delivery is counted and the score grows by the bonus and tip

#### Scenario: Harder next block
- **WHEN** a delivery is completed
- **THEN** the next block runs faster with heavier traffic

### Requirement: Records
The app SHALL save the best score and the best delivery count of one run
in local storage, update them only when improved, show a NEW BEST banner
on improvement, and keep them across reloads. Save failures SHALL NOT
break the game.

#### Scenario: New best
- **WHEN** a run beats the saved best score or best deliveries
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Weaker run keeps records
- **WHEN** a run ends below the saved bests
- **THEN** the saved records stay unchanged and no banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best score and best deliveries are shown

### Requirement: Retro-neon presentation
The app SHALL render a synthwave night highway — deep-purple sky,
glowing neon traffic streaks, light-trail lane lines, and a neon skyline
— all drawn in code with zero image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the neon night scene and glowing levers are drawn with no image files used

### Requirement: Run flow and recovery
The app SHALL flow from a ready screen into the run and on to the
lost-delivery screen, with a play-again action that starts a fresh run. A
clear-records action SHALL reset saved records and confirm with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from the result screen
- **THEN** a fresh run starts with the hero at the first block and a full pizza

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
