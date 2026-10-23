# Proposal

## Why

Students use apps all day but never *see* where their time goes — and most
"screen time" tools feel like alarm clocks or scoldings. We want the opposite:
a friendly monster that eats the minutes and shows them back as color and size,
like a pet for your day. It fills a new corner of the EPIC-MN showcase —
digital wellbeing, told with kindness — and the hard design rule is that the
monster is **cute, never scary**.

## What Changes

- New single-file app `time.html`, working title **Time Monster** (Example #6),
  in the house retro-arcade style (vanilla HTML/CSS/JS, invented data, no
  network, no accounts).
- Opens instantly with a **pretend day** of invented app usage already loaded,
  so the monster is mid-growth the moment the page appears.
- A **tap-to-use** live mode: tap an app button to "use" that app (a fast
  demo-time clock, switchable any time) and watch the monster grow live.
- The monster grows **larger with total time** and grows **colorful fur
  patches** — every app has its own color, more time = bigger patch — so the
  monster visibly "shows which apps you used."
- A gentle **happiness meter** that fills as the day gets more varied, and an
  **end-of-day summary** where the monster gives **1–3 stars** for balance with
  kind coaching words — a coach, never a judge.
- localStorage persistence of the current day with a visible reset control and
  toast, guarded by try/catch like every other example.
- README updated with Example #6 at ship time.

## Capabilities

### New Capabilities
- `time-monster`: a friendly time-tracking monster app — pretend-day data,
  live tap-to-use tracking, fur-patch growth, happiness meter, and kind
  end-of-day star summaries, with local persistence and a retro arcade look.

### Modified Capabilities

( none — all five shipped examples stay exactly as they are )

## Impact

- Adds `time.html` (new file) and `openspec/specs/time-monster/spec.md` (new).
- README gains an Example #6 row and run instructions at ship time.
- No changes to existing apps, specs, or data.
- **Parked later changes** (named aloud, not built today):
  `monster-week` (a week of days with trends and charts) and
  `monster-hats` (unlock silly hats and props for happy streaks).
