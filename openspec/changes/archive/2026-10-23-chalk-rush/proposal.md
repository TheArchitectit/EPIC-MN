# Proposal

## Why

Real-time strategy games teach the best kind of thinking — spending
resources under pressure, reading a battlefield, making the big call at
the right second. But most RTS games hide that fun behind giant menus.
**Chalk Rush** keeps the heart and drops the clutter: a general's
chalkboard where you hire workers, watch energy roll in, hatch toy
soldiers, and launch the big rush at the enemy castle. Fun and simple —
one-thumb strategy.

## What Changes

- New single-file HTML app `chalk.html`, working title **Chalk Rush**, in
  the house showcase style (vanilla HTML/CSS/JS, invented data) wearing a
  **chalk war-room** skin: dusty chalkboard-green background, chalk-stroke
  units and castles drawn in code, chalk arrows and scribbled explosions,
  wooden-lever buttons — zero image assets.
- **Gather & rush economy**: worker stamps gather energy each second;
  energy buys more workers or soldiers; the army auto-marches toward the
  enemy castle and fights whatever it meets on the way.
- **Command levers** (buttons, auto-battle): HIRE WORKER, HATCH SOLDIER,
  and a big **RUSH!** lever that sends a chalk-arrow surge (all soldiers
  charge with a temporary speed-and-damage boost).
- **Enemy commander**: a simple rival general on the right hires its own
  workers and soldiers, growing tougher over time — a fair, readable
  fight that escalates.
- **Win / lose / score**: destroy the enemy castle to win, defend yours
  to survive; the board records your best win time (and best win streak)
  with the house seed/load/save/reset + toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `chalk-rush`: the chalkboard real-time strategy game — the gather-and-
  rush economy, auto-battling troops, the RUSH surge, the rival general,
  win/lose scoring, and the chalk war-room presentation.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `chalk.html` and `openspec/specs/chalk-rush/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `chalk-rush` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `chalk-campaign` (a series of rival generals), `chalk-sounds` (bugles
  and clacking toy soldiers), `chalk-skirmish` (two-player hot-seat on
  one keyboard).
