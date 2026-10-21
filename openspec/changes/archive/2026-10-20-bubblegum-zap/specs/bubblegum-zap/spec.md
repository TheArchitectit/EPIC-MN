# Spec Delta

## Purpose

A silly, flashy, local-only web game where players zap floating bubblegum
bubbles in a gooey candy world — built to amaze and entertain students.

## ADDED Requirements

### Requirement: Game starts instantly, no gate
The game SHALL be a single static page that opens with no server, network,
or setup, and SHALL present playable gameplay immediately on load — no
menus to click through, no demo mode, no accounts.

#### Scenario: Open and play
- **WHEN** a player opens the page
- **THEN** the game begins immediately, with bubbles already floating and
  the score visible

### Requirement: Bubblegum spawn & zap
The game SHALL spawn bubblegum bubbles that float upward, SHALL let the
player zap them with a click or tap, SHALL award points per pop, and SHALL
produce a satisfying pop burst. Special bubbles SHALL exist: gold gum (big
points) and sour gum (penalty if not popped quickly).

#### Scenario: Pop a bubble
- **WHEN** the player clicks a floating bubble
- **THEN** the bubble pops with a burst effect and points are added to the
  score

#### Scenario: Special bubbles
- **WHEN** a gold gum bubble appears and is popped
- **THEN** the player earns a large point bonus
- **WHEN** a sour gum bubble is left unpopped for too long
- **THEN** the game punishes the player with a small score penalty

### Requirement: Zap frenzy & combos
The game SHALL escalate speed as the score grows, SHALL track a combo chain
when bubbles are popped in quick succession, and SHALL award bonus points
for long chains.

#### Scenario: Combo chain
- **WHEN** the player pops bubbles quickly one after another
- **THEN** the combo counter rises and bonus points scale with the chain

#### Scenario: Speed escalation
- **WHEN** the player's score crosses milestone thresholds
- **THEN** bubbles spawn faster and move quicker

### Requirement: Maximum chaos events
The game SHALL inject random silly events throughout play that temporarily
change how the game behaves (e.g., "Gum Tsunami", "Gravity Flip", "All Gold
Bubble"). Each event SHALL announce itself with a fun banner and SHALL
revert to normal after a few seconds.

#### Scenario: A chaos event fires
- **WHEN** a chaos event triggers during play
- **THEN** a playful banner announces it and the game behavior changes for
  the event's duration, then returns to normal

### Requirement: Gooey candy world
The game SHALL present a bright, gooey candy aesthetic — wobbly glossy
bubbles, juicy particles, playful typography — and SHALL work at phone
widths as well as desktop, with mouse and touch input.

#### Scenario: Play on desktop and phone
- **WHEN** the player uses a mouse or a touchscreen
- **THEN** zapping works in both cases and the layout stays usable

### Requirement: Score & persistence
The game SHALL show the current score, combo, and best score, SHALL persist
the best score in browser storage, and SHALL provide a "start fresh"
control that resets the best score. All data SHALL stay local.

#### Scenario: Best score survives reload
- **WHEN** the player reloads the page
- **THEN** the best score from the previous session is still shown

#### Scenario: Start fresh
- **WHEN** the player confirms "start fresh"
- **THEN** the best score resets to zero

### Requirement: End of play & feedback
The game SHALL end play when a bubble escapes past the top of the screen
(one miss too many), SHALL show a fun game-over screen with the final score,
and SHALL offer an instant restart.

#### Scenario: Game over and restart
- **WHEN** the player misses enough bubbles
- **THEN** a game-over screen appears with the final score and a restart
  button that begins a new game immediately
