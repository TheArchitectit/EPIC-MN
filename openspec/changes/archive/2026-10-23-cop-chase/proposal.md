# Proposal

## Why

Every racing game promises speed — then buries the rush under sim
physics and garage menus. **Cop Chase** keeps the getaway feeling from
the first second: you are the driver on a neon midnight highway, the
gas and brake pedals answer to your thumb, and pixel cop cars with
flashing lights fill the mirror. It is the arcade cabinet every kid
wanted: outrun the law, dodge the traffic, and see how far a full tank
of nerve can go.

## What Changes

- New single-file HTML app `chase.html`, working title **Cop Chase**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **retro-neon × arcade pixel** skin: a glowing synthwave
  night highway, blocky pixel cars, CRT scanlines, and flashing cop
  lights — zero image assets, all drawn in code.
- **Gas & brake driving**: the player sets the speed with gas and
  brake (arrow keys or on-screen pedal buttons) and steers left / right
  between lanes — braking hard lets chasing cops overshoot, flooring it
  eats distance but invites trouble.
- **Highway chase**: a scrolling multi-lane highway full of civilian
  traffic to dodge, with checkpoint gates that add time on the classic
  arcade clock.
- **Cops on your tail**: pixel police cars pursue from behind and weave
  toward the player's lane; contact costs the car (a crash slows you
  down and tightens the net) — clever driving is the only escape.
- **Score & records**: distance and near-misses feed the score; the
  board keeps the best run with the house seed/load/save/reset + toast
  machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `cop-chase`: the retro-neon arcade cop chase — gas/brake/steer
  driving, highway traffic and checkpoint timing, pursuing cop cars
  with contact consequences, pixel-neon presentation, and best-run
  records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `chase.html` and `openspec/specs/cop-chase/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps.
- README gains a `cop-chase` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `cop-chase-maps` (new cities and coast highways), `cop-chase-sirens`
  (engine growls, siren wails, and radio chatter), `cop-chase-garage`
  (paint jobs and silly getaway-car upgrades).
