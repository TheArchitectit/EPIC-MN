# Spec Delta

## ADDED Requirements

### Requirement: One-minute round timer
The game SHALL show a countdown timer starting at 1:00, and the round SHALL
end when the timer reaches 0:00 with a time-up game-over screen.

#### Scenario: Round ends when time runs out
- **WHEN** the timer reaches 0:00
- **THEN** play ends, the game-over screen shows the final score, and
  restart begins a new 1-minute round

## MODIFIED Requirements

### Requirement: Bubblegum spawn & zap
The game SHALL spawn bubblegum bubbles that float upward, SHALL let the
player zap them with a click or tap, SHALL award points per pop, and SHALL
produce a satisfying pop burst. Special bubbles SHALL exist: gold gum (big
points) and sour gum (penalty if not popped quickly). Bubble motion and
spawn pacing SHALL run at roughly half the original speed, while level-up
scaling still makes the game faster as the score grows.

#### Scenario: Pop a bubble
- **WHEN** the player clicks a floating bubble
- **THEN** the bubble pops with a burst effect and points are added to the
  score

#### Scenario: Special bubbles
- **WHEN** a gold gum bubble appears and is popped
- **THEN** the player earns a large point bonus
- **WHEN** a sour gum bubble is left unpopped for too long
- **THEN** the game punishes the player with a small score penalty

#### Scenario: Slower pace
- **WHEN** the player starts a round
- **THEN** bubbles rise and spawn noticeably slower than the original
  version, and the pace still increases at score milestones

### Requirement: End of play & feedback
The game SHALL end play when a bubble escapes past the top of the screen
(one miss too many) OR when the round timer reaches zero, SHALL show a fun
game-over screen with the final score and the reason play ended, and SHALL
offer an instant restart.

#### Scenario: Game over and restart
- **WHEN** the player misses enough bubbles or the timer runs out
- **THEN** a game-over screen appears with the final score and a restart
  button that begins a new 1-minute round immediately
