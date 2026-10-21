# Design

## Context

See proposal.md — Why. This is Example #2 for EPIC-MN, and it must match
Example #1's constraints: one static file, zero dependencies, zero network,
local-only, invented everything, and immediately impressive when opened.

## Goals / Non-Goals

**Goals:**
- One self-contained `bubblegum.html` at the repo root.
- A full game loop with gooey candy visuals and maximum-chaos events.
- Feels "amazing" within the first 5 seconds: spawn → zap → burst → combo.
- Same style language as the house style but distinct and candy-themed.

**Non-Goals:**
- No multiplayer, no accounts, no online leaderboards, no backend.
- No downloaded assets — color, shapes, sounds (synthesized via WebAudio)
  are all generated in code.
- No frameworks or build tooling.

## Decisions

**D1 — Canvas renderer + DOM overlay UI.** One `<canvas>` draws the bubbles,
particles, and juice; DOM elements overlay for score/combo/banners/buttons.
Rationale: full visual control and 60fps cheaply, while UI stays easy to
build. Alternative considered: pure DOM bubbles (rejected: too slow for
frenzy + particles).

**D2 — Game state machine.** Three states: `menu` (a single "play" moment —
but the page auto-starts to satisfy R1), `playing`, `over`. Restart is one
button, instant.

**D3 — Spawner & difficulty curve.** Bubbles spawn from the bottom with
random x, wobble upward with per-bubble speed. Difficulty = spawn interval
and speed scale, stepped by score milestones (R4). Bubbles are zapped via
pointer hit-testing on their circles.

**D4 — Chaos event engine.** A timer rolls a dice every ~12–20s during
play (never during the first few seconds). Each event is a small state
override with a banner + duration + revert. Events are pure code: "Gum
Tsunami" (crowd of bubbles), "Gravity Flip" (bubbles fall), "All Gold"
(only gold gum), "Slow-Mo Gum" (time slows), "Bubble Storm" (fast waves).

**D5 — Juice stack.** WebAudio-synthesized pop blips (no audio files),
screen shake on sour penalty, floating score text, canvas-confetti particles,
combo pulse on the score counter, bouncing page title.

**D6 — Persistence.** Best score in localStorage under one key, guarded
try/catch, with a hidden-but-accessible "start fresh" button in the footer.

## Risks / Trade-offs

- Canvas perf on weak school laptops → mitigation: cap particle counts,
  use simple shapes, DPR cap at 2, and auto-lower particles if fps dips.
- WebAudio may be blocked until first interaction → mitigation: audio is a
  bonus, never required; guard all AudioContext access.
- "Maximum chaos" can overwhelm → mitigation: events never stack more than
  one at a time; each is short and readable.

## Open Questions

None — style detail (exact candy palette, event names) is open to the
owner's taste and safe to adjust after they see the first build.
