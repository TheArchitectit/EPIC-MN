# bubblegum-zap Specification

## Purpose
A silly, flashy, local-only web game where players zap floating bubblegum
bubbles in a gooey candy world — built to amaze and entertain students.

## Requirements

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
player zap them with a click, tap, or the aim-assist weapons, SHALL award
points per pop, and SHALL produce a satisfying pop burst. Gold gum gives
big points; sour gum penalizes if not popped quickly. Bubble motion and
spawn pacing SHALL run at a moderate level between the original and the
slow tuning, escalating through score milestones and round phases.

#### Scenario: Pop a bubble
- **WHEN** the player clicks, taps, or hits a bubble with a weapon
- **THEN** the bubble pops with a burst effect and points are added to the
  score

#### Scenario: Special bubbles
- **WHEN** a gold gum bubble appears and is popped
- **THEN** the player earns a large point bonus
- **WHEN** a sour gum bubble is left unpopped for too long
- **THEN** the game punishes the player with a small score penalty

#### Scenario: Slower pace
- **WHEN** the player starts a round
- **THEN** the pace is gentler than the original but livelier than the
  slow tuning, and it speeds up through score milestones and round phases

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
(one miss too many) OR when the round timer reaches zero, SHALL show a fun
game-over screen with the final score and the reason play ended, and SHALL
offer an instant restart.

#### Scenario: Game over and restart
- **WHEN** the player misses enough bubbles or the timer runs out
- **THEN** a game-over screen appears with the final score and a restart
  button that begins a new 1-minute round immediately

### Requirement: One-minute round timer
The game SHALL show a countdown timer starting at 1:00, and the round SHALL
end when the timer reaches 0:00 with a time-up game-over screen.

#### Scenario: Round ends when time runs out
- **WHEN** the timer reaches 0:00
- **THEN** play ends, the game-over screen shows the final score, and
  restart begins a new 1-minute round

### Requirement: Retro chiptune music
The game SHALL synthesize a looping, classic arcade-style chiptune using
WebAudio (no audio files, no network) and SHALL begin playing after the
player's first interaction. A toggle control SHALL let the player mute and
unmute the music at any time.

#### Scenario: Music starts after first interaction
- **WHEN** the player clicks or taps the game for the first time
- **THEN** the synth loop starts playing quietly

#### Scenario: Toggle music on/off
- **WHEN** the player clicks the music toggle
- **THEN** the music stops; clicking again resumes it from the loop point

### Requirement: Aim-assist weapons
The game SHALL provide a laser beam that the player aims with the pointer,
SHALL fire the beam continuously while the pointer is held, and SHALL
automatically launch missiles and spread shots as assists while firing.

#### Scenario: Hold to fire the aimed laser
- **WHEN** the player holds the pointer on a bubble
- **THEN** a visible beam fires from the bottom toward the pointer and pops
  every bubble it touches

#### Scenario: Auto-assist missiles
- **WHEN** the player fires the beam continuously
- **THEN** missiles launch automatically toward bubble clusters and spread
  shots widen the blast area

### Requirement: Random gum objects
The game SHALL periodically spawn gum-themed objects, each with a random
effect chosen from a pool (e.g., score jackpot, missile boost, gold rain,
freeze, gravity flip, extra heart). Objects SHALL be visually distinct and
SHALL announce the effect when collected.

#### Scenario: Collect a gum object
- **WHEN** the player pops/collects a gum object
- **THEN** a random effect triggers, is announced, and changes the round
  briefly

### Requirement: Escalating round phases
The game SHALL structure the 60-second round in three phases: warm-up
(0–15s, calmer), mid-round (15–40s, gum objects and missiles appear), and
finale (40–60s, faster spawns and frequent chaos events), so the round
builds to a peak.

#### Scenario: Round builds to a finale
- **WHEN** the round reaches the finale phase
- **THEN** spawns speed up, chaos events come more often, and the final
  seconds feel like a frenzy
