# Design

## Context

Two examples already ship as single-file vanilla HTML/CSS/JS pages
(`index.html`, `bubblegum.html`) with zero frameworks, zero network calls,
invented data, and localStorage persistence guarded by try/catch with a
visible restore control. `study.html` joins them under the same rules.
See proposal.md — Why for motivation and specs/study-app/spec.md for the
behavior contract.

## Goals / Non-Goals

**Goals:**
- One self-contained `study.html`, openable straight from disk.
- A tiny state machine (decks view → study session → round summary) that
  a student can follow in the code.
- Stable card identity so "missed" tracking survives deck edits and reloads.
- Retro arcade look achieved with CSS only — no webfonts, no image assets,
  no audio (all offline).

**Non-Goals:**
- Timer, trivia, and easter eggs (parked: `study-timer`, `study-trivia`,
  `study-eggs`).
- Creating/editing cards in the UI — starter decks are invented in code.
- Sound (bubblegum's chiptune covers the audio showpiece).
- Any backend, sync, or accounts.

## Decisions

- **Single file, no build step.** Same as the other examples: inline CSS/JS
  in `study.html`. *Alternative:* split into `study.css`/`study.js` —
  rejected: the showcase runs by double-clicking one file; keeping every
  example one file is the house pattern.
- **State as one plain object + full re-render.** `state = { screen, deckId,
  queue, round, flipped, progress }`; a single `render()` redraws the
  screen from state. *Alternative:* DOM-diffing per action — rejected: more
  machinery than a 3-deck study app needs, and the code stays readable for
  students.
- **Cards carry stable ids** (`"math-01"`, `"vocab-03"`, …), not array
  indexes. Missed-card tallies store these ids. *Alternative:* store by
  index — rejected: reordering or editing a deck would silently reassign
  who was missed.
- **Progress in one localStorage key** (`study-app-progress:v1`), holding
  missed tallies per deck and best clear-run (fewest rounds). Seeded and
  saved the same way as the Clubhouse (`seed()` / `save()` / restore with
  toast). Version suffix on the key lets later slices change the shape
  without corrupting old data.
- **Missed-drill is a queue, not a loop flag.** A session holds `queue` and
  `missed`; cards marked "missed it" go to `missed`; when `queue` empties,
  a new round starts from `missed` (if any) and clears it — until one clean
  round ends the session. *Alternative:* recursion over "retry deck" —
  rejected: the queue makes "which round am I on" trivial and testable.
- **Retro look via CSS only.** System monospace/`--mono` stacks (no
  webfonts — offline rule), chunky borders, hard offset shadows, bright
  arcade palette on a dark cabinet background, CSS "flip" (3D transform)
  for cards. *Alternative:* pixel webfont file — rejected: an asset the
  other examples don't have; CSS sells the vibe fine.

## Risks / Trade-offs

- [Two-tap flow (flip, then mark) could feel slow] → the mark buttons are
  large, arcade-style, and appear with the flip flourish so the next tap
  is instant.
- [Full re-render on every mark loses CSS animation state] → render only
  the card stage on flip/mark; full `render()` on screen changes.
- [localStorage unavailable (private mode, file:// quirks)] → try/catch
  around every read/write, exactly like the other examples; the app runs
  fully without persistence, just without saved progress.
- [Clear-deck celebration is the one "wow" moment and must not glitch] →
  it is a dedicated screen state (not an overlay on the study screen) with
  rounds-taken count; simpler to get right and to test.

## Migration Plan

Brand-new file, nothing to migrate. Ship = add `study.html` + a README row;
rollback = remove those. The two existing examples are untouched.

## Open Questions

- Exact starter-deck contents (Math / Vocab / History card text) are
  invented at build time — flavor only, no spec impact.
