# Tasks

## 1. Aim-assist weapons

- [x] 1.1 Draw the aim reticle and held-laser beam from the bottom tracking
      pointer X; verify held fire pops column bubbles
- [x] 1.2 Add auto missiles (nearest-cluster target, ~1.2s cadence) and
      spread shots (~0.6s); verify they fire only while holding
- [x] 1.3 Add satisfying beam/missile visuals and sounds; verify no FPS
      hit on low-end machines

## 2. Random gum objects

- [x] 2.1 Spawn distinct gum-package objects during phases B/C with a
      timer; verify they appear and are collectible
- [x] 2.2 Implement the random effect pool (jackpot, missile boost, gold
      rain, freeze, gravity flip, extra heart, sour rain) with banner
      announcements; verify each effect triggers and reverts

## 3. Escalating 60-second round

- [x] 3.1 Implement the 3-phase timeline (A/B/C) and verify object and
      missile unlocks align with phases
- [x] 3.2 Set SPEED 0.75 and phase spawn bases (950/700/450); verify the
      round builds to a finale without returning to frantic aiming
- [x] 3.3 Chaos event interval halves in phase C; verify event frequency
      increases at the end

## 4. Final checks

- [x] 4.1 Verify the 1-minute timer, miss hearts, and game-over reasons
      still work with weapons active
- [x] 4.2 Run `openspec validate --all` and fix any findings
- [x] 4.3 Manual wow-pass: play a full round on desktop and at phone width

## Workflow follow-up

- Archive this change after the owner approves.
