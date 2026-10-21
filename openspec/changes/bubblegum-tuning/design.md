# Design

## Context

See proposal.md — Why. Small, low-risk tuning of `bubblegum.html`.

## Goals / Non-Goals

**Goals:**
- Reduced speed: multiply base bubble velocity by 0.5 and slow spawn pacing
  (~1.5× the interval, still level-scaled).
- Add a 1:00 countdown in the HUD; game-over screen distinguishes
  "time up" from "missed too many".
- Keep all existing features (gold/sour, combos, chaos events, best score).

**Non-Goals:**
- No new visuals, events, or persistence changes.

## Decisions

**D1 — Speed constants.** One `SPEED_CHILL = 0.5` factor applied where
bubble velocity is computed; spawn base interval raised (e.g. 650 → 950,
storm 120 → 170). Level-up escalation unchanged so rounds still build.

**D2 — Timer.** `G.timeLeft = 60000` decremented in `update()`; HUD box
renders m:ss. On ≤0, `gameOver("time")`. `startGame()` resets it.
Game-over card title/subtitle switch by reason (⏰ TIME'S UP vs 💥 POPPED
OUT).

## Risks / Trade-offs

- With 50% slower speed, a round may feel easy to strong players → the
  level-up ramp and chaos events still provide challenge; 1-minute cap
  keeps each round short regardless.
- Timer changes miss-heart budget → both loss conditions remain, so the
  round simply ends at the first one to trigger.
