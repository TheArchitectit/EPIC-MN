# Design

## Context

See proposal.md — Why. Builds on the archived Bubblegum Zap game and the
open `bubblegum-tuning` change's 1-minute rounds.

## Goals / Non-Goals

**Goals:**
- Aim-assist feel: laser follows the pointer while held; missiles/spread
  fire automatically as assists.
- Random gum objects with distinct visuals and announced effects.
- 3-phase timeline inside the 60-second round; moderate base speed.

**Non-Goals:**
- No new data persistence; no network; no assets (all visuals drawn,
  sounds synthesized).

## Decisions

**D1 — Pointer-aim laser.** The beam originates at the bottom of the screen
and tracks the pointer's X; while the pointer is held, every bubble whose
column overlaps the beam pops. Reticle drawn at pointer. Touch: drag fires.

**D2 — Auto-assist fire.** While firing, a missile launches every ~1.2s
toward the nearest cluster (computed from bubble positions); every ~0.6s a
spread shot adds two angled mini-beams. Cooldowns tuned so assists feel
generous but not automatic-win.

**D3 — Gum object system.** One object type (gum package) spawns on a timer
during phases B/C; it drifts like a bubble but is larger and distinct.
On collect, `random()` picks an effect from a pool: jackpot, missile boost,
gold rain, freeze (bubbles pause 2s), gravity flip (5s), extra heart
(once per round), sour rain (penalty wave). Effects announce via the
existing banner + a colored glow.

**D4 — Phase timeline.** `phase(dt)`: A: 0–15s, spawn base 950, no
objects, no missiles; B: 15–40s, spawn 700, objects every ~6s, missiles
on; C: 40–60s, spawn 450, objects every ~4s, chaos event interval halved,
storm-like burst every 10s.

**D5 — Pace constants.** Reintroduce a `SPEED` factor of 0.75 (between 1.0
original and 0.5 slow) for bubble velocity; level milestones still increase
it.

## Risks / Trade-offs

- Laser making zapping too easy → assistants are still limited by hold
  duration and missile cooldowns; score ceiling stays bounded.
- Random effects can feel unfair → every effect is short, announced, and
  mostly positive or comedic.
- Perf with beams + particles → beam is one gradient rect; particle caps
  reused from before.
