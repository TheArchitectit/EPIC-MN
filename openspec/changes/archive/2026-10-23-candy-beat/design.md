# Design

## Context

Candy Beat is a single-file vanilla HTML/CSS/JS rhythm auto-runner
(`candy.html`) in the house showcase style. The hero runs through a
pixel arcade-cabinet world — candy mountains, pipes, star fields —
and the only control is TAP to jump. Everything lands on a 120 BPM
beat clock: the route, the orbs, the sounds, and the grading of every
tap. It is the student's "mix of them all": one-tap party + beat
runner + pop-up beats + dance-floor crowd, blended into one loop.

## Goals / Non-Goals

**Goals**
- A complete run: auto-scroll, tap-jump, hazards, orbs, groove
  grade, finish line (or lights out).
- Timing that feels fair: obstacles sit ON the beat so good play
  feels musical; every tap is graded against the real millisecond
  clock.
- Candy-80s coin-op flash drawn entirely in code.
- House records machinery (seed/load/save/reset + toast).

**Non-Goals**
- No real game marks or levels (compliance note in the proposal) —
  the world, name, and tune are invented.
- No extra tracks, costumes, or worlds (parked later changes).
- No multi-button moves — one tap keeps the cabinet honest.

## Decisions

1. **File & frame**: single `candy.html`; CSS vars themed; canvas
   `draw()` + DOM `render()`; top-level functions for the test
   harness; `TICK_MS = 50` clock. Canvas 540×720.
2. **Palette (candy-80s)**: `--pink:#ff2e88`, `--blue:#2e8bff`,
   `--yellow:#ffe94a`, `--mint:#4affc8`, `--grape:#7a3cff`,
   `--cabinet:#241040`, `--road:#3c1d6e`, `--ink:#fff6ff`,
   `--dim:#8a6ab8`, `--danger:#ff4a4a`.
3. **Phases**: `ready → playing → over → playing → …`. `startRun()`
   arms a fresh run: `songStart` stamps the clock, the route is
   rebuilt, `streak = 0`, `crowd = 60`, `score = 0`, hero grounded.
4. **The run**: 120 BPM (`BEAT_MS = 500`), 32 bars = 128 beats
   (~64 s). World scrolls at `SPEED = 0.24 px/ms` (120 px per beat).
   An object on beat `b` sits at hero x exactly when
   `songT = b * BEAT_MS`; its screen x is
   `HERO_X + (objMs - songT) * SPEED` with `HERO_X = 140`. The run
   ends when `songT > BEATS * BEAT_MS + 1000` ("cabinet cleared")
   or `crowd <= 0` ("the lights went out").
5. **One-tap jump**: Space / ArrowUp / W / click / the big JUMP
   button. Physics in px/s: `JUMP_V = -700`, `GRAVITY = 2200`
   (~0.64 s air time ≈ 1.3 beats, ~111 px height). Only from the
   ground (`GROUND_Y = 560`); landing snaps back to ground.
6. **Hazards** (deterministic route): **gaps** (1 beat of missing
   ground — the ~0.64 s jump arc clears exactly this), **spikes**
   (candy triangles on the ground), **pipes** (short candy columns).
   A grounded hero overlapping a hazard **stumbles**: `crowd -= 12`,
   1 s mercy invulnerability (red flash), run continues — never
   instant game over.
7. **Pop-up beat-orbs**: the route seeds orbs at jump height
   (`GROUND_Y - 100`) on fixed beats. An orb glows from 700 ms
   before its time to 700 ms after, then vanishes. Hero touch
   (`30 px` x, `40 px` y): `score += 200 * mult`, `crowd += 3`, a
   star burst pops.
8. **On-beat judgment**: every tap grades against the nearest beat —
   `ONBEAT_MS = 90` → ON BEAT (`+50 * mult`, `crowd += 3`, `streak++`,
   star burst), `CLOSE_MS = 180` → CLOSE (`crowd += 1`), else OFF
   BEAT (`crowd -= 2`, `streak = 0`). `mult = min(4, 1 +
   floor(streak / 6))`. Progress score `+10` per beat survived.
9. **Route (invented "Candy Circuit")**: deterministic 32-bar
   pattern — warmup bars, then 1-beat gaps every 4th bar from bar 2,
   spikes from bar 3, pipes from bar 5, an orb every bar from bar 1
   plus high extras. No randomness: every run faces the same cabinet.
10. **Sound (Web Audio, optional)**: `blip()` helper; kick/snare/
    hat/bass on the beats (same spirit as Beat Booth), jump chirp,
    orb sparkle, stumble buzz. Created only if `AudioContext`
    exists; without it the game runs on visual cues alone.
11. **Records**: `GKEY = "candy-beat:v1"` holds
    `{ bestScore, bestStreak }` — updated only when improved; NEW
    BEST banner on the result screen; house seed/load/save/reset
    with try/catch; CLEAR RECORDS button resets and toasts.
12. **Screens**: `screen-ready` ("Candy Beat!" + records + PRESS
    START!), `screen-over` ("Cabinet cleared!" or "The lights went
    out!" + score + best streak + NEW BEST + PLAY AGAIN). Toast sits
    absolute `top: 100px` inside `.boardwrap` — under the HUD, never
    over the track or the JUMP button.
13. **HUD**: canvas bar on top — SCORE, STREAK ×mult, CROWD meter,
    STAGE (bar n of 32) — with judge words (ON BEAT! / OFF BEAT) as
    floats at the hero.
14. **Art**: candy gradient sky with hard-coded star field (slow
    parallax), chunky pixel mountains (0.4× parallax), checkered
    candy road with void gaps, pipes and spikes in candy colors, a
    chunky blocky hero with running legs, glowing star orbs, star-
    burst particles on ON BEAT and orb grabs, beat-pulse flash on
    downbeats — zero images.

## Risks / Tradeoffs

- Jump physics at 50 ms ticks can look slightly stepped — accepted:
  the hero and world are chunky pixel shapes; the beat clock (real
  ms) still grades taps precisely, like Beat Booth.
- One deterministic route could get stale — accepted for the
  showcase: the chase is the groove grade and the best score, and
  `candy-beat-worlds` is the parked home for more cabinet lands.
- Stumble-mercy (no instant death) keeps it school-friendly —
  accepted: the real fail state is the crowd walking out.

## Migration

None — new capability, new file. Existing showcase apps untouched.

## Open Questions

None — the student locked the shape: mix of tap/runner/orbs/crowd,
arcade cabinet stage, candy-80s flash.
