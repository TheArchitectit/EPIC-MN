# Design

## Context

Five single-file examples already ship in the house style (vanilla
HTML/CSS/JS, invented data, localStorage + reset + toast, canvas artwork).
This is the first app whose core is a *computed visualization* — the monster
is a live function of the day's minutes — and the first with a hard
tone constraint ("cute, never scary"). A web page cannot see real desktop
apps, so the "day" is invented data plus live tap-to-use sessions. See
proposal.md for motivation; behavior is fixed in the spec delta.

## Goals / Non-Goals

**Goals:**
- One state object + one pure draw pipeline, reused for the big stage and
  every small thumbnail (proven pattern in `dress.html`).
- Growth and patch sizes derived from a single minutes model — stage,
  happiness meter, star summary, and saved thumbnails can never disagree.
- Demo-visible growth: a class can watch the monster change within seconds.
- Deterministic, tunable feel: one clock constant and one happiness formula
  that can be tuned live in front of students.

**Non-Goals:**
- Real OS process tracking (impossible in a browser — invented data instead).
- Multi-day history and trends → parked change `monster-week`.
- Unlockable hats/props → parked change `monster-hats`.
- Sound/music and animations beyond gentle floating flourishes.

## Decisions

1. **Accelerated demo clock** — while an app is active, a 250ms interval adds
   `MIN_PER_TICK = 1.25` demo-minutes (≈5 min per real second), so ~2 real
   minutes "spends" a whole day. *Alternative:* real-time minutes — too slow
   for a booth demo; *alternative:* fixed +10min chunks per tap — less like
   "spending time" and less fun to watch.
2. **Canvas monster** — one `<canvas>` (≈420×420) + `drawMonster(c, day)`.
   Rounded shapes only: pill body, big oval eyes, smile arc, blush circles,
   stub feet, wavy fur edge. **Forbidden in the draw code: teeth, spikes,
   angry eyebrows, dark muddy palettes** — the "never scary" rule made
   checkable. *Alternative:* CSS/emoji monster — not enough control of
   patches and can't reuse for PNG-like thumbnails.
3. **Fixed fur-patch slots** — each app gets a permanent slot around the
   body (angles like 8 clock positions chosen by its index in `APPS`);
   patch radius = clamp(`share * maxR`). Stable: patches never jump around
   as numbers change. Colors come from one `APPS = [{id, name, emoji,
   color, seedMin}]` table (invented school apps: Math Quest, Drawing Pad,
   Book Nook, Music Maker, Chat Club, Video Tube).
4. **Size mapping** — body scale = `0.55 + 0.45 * sqrt(total / 240)` clamped
   to [0.55, 1.25]. Square-root growth: fast at first (baby monster!), then
   flattens so the huge monster still fits the stage.
5. **Happiness formula** — `variety` = distinct apps used (0–6), `balance` =
   `1 − topAppShare`. Happiness = round(`(variety/6 * 0.6 + balance * 0.4) * 100`),
   clamped 0–100. Meter labels, kind-only: "still cute!" / "getting cozy" /
   "happy!" / "over the moon!". Stars: ≥80 → 3★, ≥45 → 2★, else 1★; each
   star band has celebratory/encouraging/gentle message arrays — wording
   reviewed to never shame.
6. **State + persistence** — `state = { mins: {id: n}, active: id|null,
   finished: bool }` at `GKEY = "time-monster-day:v1"`; `seed()` builds the
   pretend day (Math 35, Drawing 45, Video 50, Book 25, Chat 20, Music 15);
   `load()/save()` try/catch with in-memory fallback; reset re-seeds + toast.
7. **Layout** — stage (monster canvas) left, app buttons + day list +
   happiness meter right, "★ finish my day" opens a summary panel (reuses
   `drawMonster` on a small canvas), reset in the chrome. CSS variables and
   `flourish()`/`sparkBurst()` helpers copied in the house idiom.

## Risks / Trade-offs

- [Monster accidentally looks scary] → draw-code checklist (decision 2) +
  screenshot review at every size band before ship; spec scenario "Cute at
  any size" is the acceptance gate.
- [Patches make the silhouette messy] → clamp patch radius to 34px max,
  cap visible patches at the 6 apps, keep face area patch-free.
- [Clock speed feels wrong at a booth] → `MIN_PER_TICK` is one constant at
  the top of the script, tunable live in front of students.
- [Happiness math feels arbitrary] → one small formula (decision 5), shown
  as a simple meter; if it feels off, thresholds are tunable without
  touching the spec.
- [localStorage blocked (school laptops)] → try/catch everywhere + fully
  functional in-memory mode (same harness test as the other examples).

## Migration Plan

New file `time.html` + new spec `time-monster` — nothing existing changes.
Deploy = build, verify, README row, commit. Rollback = delete `time.html`;
the five shipped examples are untouched either way.

## Open Questions

None — remaining unknowns (exact emoji per app, wavy fur style) are build
details that don't move the spec, the approach, or the task breakdown.
