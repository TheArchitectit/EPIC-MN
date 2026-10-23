# Tasks

## 1. Scaffold & data

- [x] 1.1 Create `study.html` shell with retro CSS (arcade palette,
      chunky shadows, monospace stack) and verify the page opens from disk
      with all three subject decks visible immediately (spec: opens
      instantly, retro presentation)
- [x] 1.2 Define the Math, Vocab, and History starter decks with stable
      card ids (`math-01`, …) and verify every card has a front and a back

## 2. Study flow

- [x] 2.1 Build the card stage with CSS flip and verify tapping a card
      reveals its answer side
- [x] 2.2 Add the "got it" / "missed it" mark buttons with retro flourish
      feedback and verify marking advances to the next card (or ends the
      run when none remain) with a visible flourish
- [x] 2.3 Implement the missed-card drill queue and verify missed cards
      return in a new round, and that a clean round triggers the
      clear-deck celebration showing rounds taken

## 3. Progress persistence

- [x] 3.1 Add `seed()` / `save()` / `load()` for the
      `study-app-progress:v1` key (missed tallies per deck, best clear-run)
      and verify progress survives a reload
- [x] 3.2 Add the reset control with toast and verify it returns to
      starter state while the starter decks remain intact

## 4. Integration checks

- [x] 4.1 Verify the full experience at phone and desktop widths — decks,
      flip, marks, celebration all readable and usable
- [x] 4.2 Verify the app runs fully with storage blocked (private-mode
      simulation) — study flow works, only saved progress is skipped
- [x] 4.3 Run `openspec validate --all` and fix any findings; play-check
      one full deck from first flip to clear-deck celebration

## Workflow follow-up

- Add a third-example row to README.md and note `study.html` in the run
  commands at ship time.
- Archive this change after the owner says "ship it", then verify the
  merged spec at `openspec/specs/study-app/spec.md`.
