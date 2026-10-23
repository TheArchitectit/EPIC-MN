# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with
shared house machinery (CSS vars, localStorage try/catch +
seed/load/save/reset + toast, canvas draw pipelines, top-level
functions for the stub-DOM harness, `TICK_MS=100` clocks). Street Hoops
is the first **sports game** in the set: a timed 2-on-2 blacktop match
where the player drives the ball handler, shakes a defender, and shoots
from wherever they stand. The student picked the **classic basketball**
fantasy blended into one match — 3-pointers, free-throw streaks, and
1-on-1 defender energy all woven in — with **drive & shoot** controls
and the **blacktop streetball** skin (asphalt, chain-link, sunset
skyline). The pure solo modes are parked as later changes.

## Goals / Non-Goals

**Goals**
- Classic "one more game" pull: 45 seconds on the blacktop, buzzer
  glory, rematch is one button away.
- Drive & shoot purity: movement IS the skill — find the open spot,
  burst past the guard, let it fly.
- The full promised mix inside one match: 3-pointers, free-throw
  streaks, and a glued-on defender.
- All art drawn in code: zero images.

**Non-Goals**
- Season mode, rosters, or stats sheets.
- Pure solo drills (`hoops-free-throw-lab`, `hoops-three-point-night`
  parked).
- Pure 1-on-1 duel mode (`hoops-street-duel` parked).
- Sound (`hoops-sounds` parked if the student asks later).

## Decisions

1. **Single-file `hoops.html`** with a blacktop remap of the CSS vars:
   `--sky:#ff6b35` (sunset orange), `--dusk:#7a2d5c` (sky plum),
   `--asphalt:#3a3d44`, `--chalk:#f4f1ea` (court lines), `--ink:#1c1e24`
   (warm dark), `--cream:#ffe9c7`, `--team:#2f6fed` (your jersey blue),
   `--rival:#e8482f` (rival jersey red), `--chain:#8a929e` (fence),
   chunky rounded buttons with 3px outlines and offset hard shadows,
   warm bold font stack `"Trebuchet MS", "Verdana", sans-serif` with
   heavy weights and wide tracking on titles.
2. **The court** — one `<canvas>` (540×720). Side view of a blacktop
   half-street: sunset sky gradient + city skyline + chain-link fence
   behind, asphalt with painted key/arc/line markings, one rim + net +
   backboard per side (`LEFT_HOOP = {x: 70, y: 250}`,
   `RIGHT_HOOP = {x: 470, y: 250}`). Your team (blue) attacks the RIGHT
   basket; the rivals (red) attack the LEFT basket. Players move in a
   pseudo-depth lane `y ∈ [320, 560]`, `x ∈ [40, 500]`; sprite scale
   eases with y for depth.
3. **Match clock** — `MATCH_SECS = 45` (`MATCH_TICKS = 450` at
   `TICK_MS = 100`). HUD shows the clock as `0:SS`. At zero the buzzer
   fires: `rideComplete`-style result — "BUZZER!" + "YOU WIN!" /
   "RIVALS WIN" / "TIE GAME" + final score + stats (margin, streak) +
   NEW BEST banner + "PLAY AGAIN".
4. **Drive & shoot** — arrows / WASD move the ball handler
   (`DRIVE_SPEED = 7` px per tick) in the x/y lane; the ball dribbles
   at his side while he owns it. `shoot()` fires from the handler's
   current position at his attack hoop: distance `dist = hypot(dx, dy)`;
   `THREE_DIST = 250` → three points beyond the arc, two inside. The
   ball flies as a 10-tick arc tween (`state.shot`) to the rim — make
   = swish through the net, miss = clank off the rim and bounce away —
   then possession flips to the other team. `pass()` fires the ball to
   the teammate (short tween) and control follows the new handler.
   Space / a SHOOT button fires; P / a PASS button passes.
5. **Defenders & open looks** — a red `guard` eases toward the ball
   handler every tick (`GUARD_SPEED = 6.2`, just under the handler so
   skill wins). `guarded = dist(guard, owner) < 90`. Make odds:
   `open 0.80`, `guarded 0.32`, minus `0.12` for a three. A TURBO
   burst (Shift / on-screen button) multiplies speed ×1.7 while
   `turboFuel` lasts (starts 100, drains 5/tick while held, refills
   1.5/tick, needs ≥ 15 to engage). The teammate drifts to an open
   spot; the rival ball handler (`opp`) attacks the left hoop on an AI
   timer (`hash`-seeded 22–30 tick cadence, `opp chance 0.55`, minus
   `0.30` when the hero is within 100px — playing defense pays).
6. **Free-throw streaks** — while `guarded`, a shot draws a foul with
   chance `0.28` (rolled at release): `state.mode = "ft"` pauses the
   play, the ball goes to the line, and a marker sweeps `0→100→0` at
   `6` per tick. One tap (Space / SHOOT) locks it: `|marker - 50| < 14`
   is a make, `< 5` is a perfect "SWISH!". A make banks
   `1 + ftStreak` points on the match score, then `ftStreak++`; a miss
   resets `ftStreak = 0`. After the tap, play resumes and possession
   flips.
7. **Score & records** — `GKEY = "street-hoops:v1"` holds
   `{ bestMargin, bestStreak }`. `bestMargin` = `scoreYou - scoreRival`
   at the buzzer (only positive margins count); `bestStreak` = longest
   free-throw streak of the match. Seed `{ bestMargin: 0, bestStreak:
   0 }`; corrupt → seed. Each metric updates only when improved; either
   improvement shows the NEW BEST banner. `CLEAR RECORDS` resets +
   toast. Save failures never break play.
8. **Screens** — `screen-ready` (title, rules, START THE GAME) and
   `screen-over` ("BUZZER!", win/lose banner, final score, margin +
   streak line, NEW BEST banner, PLAY AGAIN). Enter = start/again.
   HUD: YOU, RIVALS, CLOCK, STREAK. On-screen levers: ◀ ▶ ▲ ▼ drive
   pad, PASS, SHOOT, TURBO.
9. **Rendering** — blacktop pipeline: sunset sky gradient (orange →
   plum), skyline silhouettes, sun ball glow, chain-link fence hatch,
   asphalt with chalk lines (paint arc + key + sideline), rim + net +
   backboard per side, chunky streetballers (round heads, jersey
   blocks, sneaker feet, bobbing dribble), the ball with seams
   (bouncing while driving, arcing on shots), score-and-clock strip
   painted on the fence board, splash text ("SWISH!", "+3", "BRICK!",
   "FOUL!"), and a toast-safe DOM HUD/overlays. Toast sits at the TOP
   inside `.boardwrap` (the chase/snow lesson — never cover controls).
10. **Verification** — extract inline `<script>` → `node --check`;
     stub-DOM harness (shared localStorage across boots, canvas op
     recorder with gradient stubs, interval capture, direct function
     calls, controllable `Math.random`) covering clock + buzzer,
     drive + shoot distance points, pass switch, guarded vs open odds,
     turbo fuel, foul → free-throw tap + streak bank/reset, rival AI
     scoring, records better/keep/reload/clear, flow resets, broken
     storage, no images; CDP screenshots (ready, mid-match, free throw,
     buzzer result, phone) for visual review.

## Risks / Tradeoffs

- **Odds vs fairness** — open 0.80 / guarded 0.32 keeps the "drive to
  get open" lesson instant; the harness locks both numbers so play feel
  can tune them later in one place.
- **Simulated shots** — the flight is a tween to a pre-rolled result
  (like classic arcade hoops) instead of true ball physics; honest
  aim-skill lives in spacing, not pixel aiming. True arc physics can
  be a later change.
- **One match length** — 45 seconds is short enough for class demos
  and "one more game"; a longer clock can be a later knob.

## Migration Plan

New file `hoops.html` only; existing apps untouched. README row +
specs bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the three product decisions: one blended
match, drive & shoot, blacktop streetball )
