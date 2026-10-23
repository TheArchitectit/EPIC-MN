# Design

## Context

Gridiron Rush is the house showcase's first football game: a single-file
vanilla HTML/CSS/JS arcade app (`football.html`) in the same style as
Street Hoops and Harvest Haunt. One canvas paints the gridiron; DOM
buttons and a small state machine run the match. Everything is invented
data, local-only, zero images. The Comets (player, blue) take on the
Stampede (CPU, red) in a short four-quarter arcade game.

## Goals / Non-Goals

**Goals**
- A complete arcade football match: snap, run, throw, tackle, score,
  final whistle — in one file.
- Instant feel: arrows steer, one button per receiver, one juke button.
- Classic gridiron look drawn entirely in code.
- House records machinery (seed/load/save/reset + toast).

**Non-Goals**
- No playbook editor, field-goal meter, or sound (parked later changes).
- No real league/team names or logos (compliance note in the proposal).
- No multiplayer, no seasons — one match per launch.

## Decisions

1. **File & frame**: single `football.html`; CSS vars themed; canvas
   `draw()` + DOM `render()`; top-level functions for the test harness;
   `TICK_MS = 100` `setInterval` clock.
2. **Field world**: top-down vertical field. `PX_PER_YARD = 30`; the
   100 yards live at world `y = 300..3300` (yard 0 = own goal at
   `y = 3300`, yard 100 = opponent goal at `y = 300`). End zones are
   `y = 0..300` (Stampede end) and `y = 3300..3600` (Comets end).
   Sidelines at `FIELD_L = 60`, `FIELD_R = 480`. Mowing stripes every
   15 yards, white yard lines + numbers + hash marks, gold goal posts.
3. **Camera**: `camY` eases toward
   `clamp(ballWorldY - 360, 0, 2880)` each tick so the ball stays near
   the middle of the 540×720 canvas.
4. **Clock & quarters**: `QUARTER_TICKS = 240` (24 s × 4 quarters).
   The clock ticks only while a play is live. Quarter end flips
   possession and spots the ball at the new team's own 20.
5. **Offense set piece**: QB + RB + WR1/WR2/WR3 vs 5 defenders. After
   the snap the QB is the carrier; receivers run pre-set routes at
   `ROUTE_SPEED = 6.4` (streak, out, post). Arrows steer the carrier
   (`PLAYER_SPEED = 7`); Shift triggers the juke.
6. **Juke**: `JUKE_MULT = 1.5` speed burst for `JUKE_TICKS = 8`, with
   `JUKE_CD = 20` ticks between uses. While juking the tackle radius
   against the carrier is halved.
7. **Throws**: three throw buttons (keys 1/2/3 also snap) fire to
   WR1/WR2/WR3. The ball flies `PASS_TICKS = 8` toward the receiver's
   position plus ~3 ticks of lead (route velocity × 3). Catch check:
   completion if no defender is within `32px` of the arrival point,
   else interception. A completion hands control to the receiver, who
   keeps running until tackled.
8. **Tackles**: `TACKLE_R = 26` (13 while juking). When any defender
   is inside the radius the play ends at that spot; yards gained are
   `spotYard - lineOfScrimmage`. Gain ≥ 10 resets the down counter to
   1; otherwise `down++`; `down > 4` (i.e. fifth down) is a turnover —
   possession flips and the ball is spotted at the new team's own 20.
9. **Defense**: when the Stampede have the ball, the player steers one
   star defender (`PLAYER_SPEED`) among 4 chasing teammates
   (`DEF_SPEED = 6.5`); the CPU ball carrier follows a simple seek
   toward the end zone with occasional cuts. Tackling the carrier ends
   the Stampede play.
10. **Play pick**: before each offensive snap
    (`state.situation = "pick"`), three chunky buttons — RUN / QUICK
    PASS / DEEP BOMB (keys 1/2/3) — both pick and snap. Defense series
    get a "DEFEND!" prompt instead.
11. **Scoring**: touchdown (yard ≥ 100) = 7 points, then possession
    flips and the ball goes to the new team's own 20. Final whistle at
    quarter 4, clock 0 → result screen.
12. **Records**: `GKEY = "gridiron-rush:v1"` holds
    `{ bestMargin, mostTDs }` (margin counts only wins). Updated only
    when improved; NEW BEST banner on the result screen; house
    seed/load/save/reset with try/catch — save failures never break
    play; CLEAR RECORDS button resets and toasts.
13. **Screens**: `screen-ready` ("KICK OFF!" + records line),
    `screen-pick` (play buttons overlay during the pick), `screen-over`
    ("FINAL WHISTLE!" + YOU WIN / RIVALS WIN / TIE + score + stats +
    NEW BEST + PLAY AGAIN). Toast sits absolute at top **inside**
    `.boardwrap` so it never covers the action strip.
14. **Palette**: `--turf:#2e7d44`, `--turf2:#348a4c` (stripes),
    `--chalk:#f4f1ea`, `--ink:#131a16`, `--cream:#ffe9c7`,
    `--team:#2f6fed`, `--rival:#e8482f`, `--gold:#ffb13d` (posts),
    `--board:#1c2b22`.
15. **Keys**: arrows/WASD move (keydown/keyup holds), J = juke,
    1/2/3 = throw to WR1/2/3 (also pick the play at the line),
    Enter = kick off / play again. On-screen: ◀▶▲▼, JUKE, THROW 1/2/3,
    CLEAR RECORDS.

## Risks / Tradeoffs

- A live clock during play can end a match mid-drive — accepted: the
  final whistle is part of the arcade drama (quarter end always
  re-spots the ball, so no drive is stranded).
- Fixed routes (no free-form receiver steering) keep the code honest
  and readable for the classroom; `gridiron-playbook` is parked for
  the student who wants more.
- The tick-based pass flight (8 ticks ≈ 0.8 s) is predictable for the
  harness; real feel is tuned by lead ticks and the 32px catch check.

## Migration

None — new capability, new file. Existing showcase apps untouched.

## Open Questions

None — the student locked the shape: full arcade match, run & throw,
gridiron classic.
