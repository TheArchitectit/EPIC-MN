# Spec Delta

## ADDED Requirements

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

## MODIFIED Requirements

### Requirement: Bubblegum spawn & zap
The game SHALL spawn bubblegum bubbles that float upward, SHALL let the
player zap them with a click or tap OR with the aim-assist weapons, SHALL
award points per pop, and SHALL produce a satisfying pop burst. Special
bubbles SHALL exist: gold gum (big points) and sour gum (penalty if not
popped quickly). Bubble motion and spawn pacing SHALL run at a moderate
level between the original and the very slow tuning, with level-up scaling
and phase escalation making the game faster as the round progresses.

#### Scenario: Pop a bubble
- **WHEN** the player clicks, taps, or hits a bubble with a weapon
- **THEN** the bubble pops with a burst effect and points are added to the
  score

#### Scenario: Special bubbles
- **WHEN** a gold gum bubble appears and is popped
- **THEN** the player earns a large point bonus
- **WHEN** a sour gum bubble is left unpopped for too long
- **THEN** the game punishes the player with a small score penalty

#### Scenario: Moderate pace that escalates
- **WHEN** the player starts a round
- **THEN** the pace is gentler than the original but livelier than the
  slow tuning, and it speeds up through score milestones and round phases
