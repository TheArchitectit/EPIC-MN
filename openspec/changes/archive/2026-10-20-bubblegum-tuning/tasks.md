# Tasks

## 1. Slow the pace

- [x] 1.1 Apply a 0.5 speed factor to bubble velocity and verify motion is
      visibly ~50% slower
- [x] 1.2 Raise spawn base intervals (normal and storm) and verify spawn
      rate feels calmer while still level-scaled

## 2. One-minute round

- [x] 2.1 Add the countdown timer to the HUD and update it every frame;
      verify it starts at 1:00 and counts down in m:ss
- [x] 2.2 End play at 0:00 with a "time up" game-over screen (distinct
      title/subtitle) and verify the final score shows
- [x] 2.3 Reset the timer on restart and verify a new 1-minute round starts

## 3. Final checks

- [x] 3.1 Verify miss-based game over still works as a second loss path
- [x] 3.2 Run `openspec validate --all` and fix any findings
- [x] 3.3 Manual wow-pass: play a full 1-minute round on desktop and at
      phone width

## Workflow follow-up

- Archive this change after the owner approves.
