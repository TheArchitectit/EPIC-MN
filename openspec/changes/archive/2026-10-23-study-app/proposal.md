# Proposal

## Why

Students drill school material every day — math facts, vocab words, history
dates — but study tools are usually dull. The owner wants a third EPIC-MN
example: a retro, arcade-flavored study app that makes drilling feel like
play, built with the same local-only, zero-setup rules as the Clubhouse and
Bubblegum Zap. This first slice ships the heart of studying: flashcard
decks sorted by subject.

## What Changes

- New app `study.html` — a single static page in retro pixel-arcade style:
  no server, no network, no accounts. Playful and flashy like the other
  examples.
- **Flashcard decks sorted by subject** — starter decks of invented data
  (e.g. Math, Vocab, History), each a stack of cards.
- **Study flow** — flip a card to see its answer, mark it "got it" or
  "missed it", and drill the missed cards again until the deck is clear.
- **Local progress** — best runs and which cards keep getting missed persist
  in localStorage, with a restore/reset control, same contract as the other
  examples.
- **Retro fun from day one** — arcade colors, pixel-style type, playful
  feedback on every flip and pop of a card.

Parked as later changes (named now so nothing gets lost):

- `study-timer` — focus timer: Pomodoro-style study rounds, breaks, streaks
- `study-trivia` — trivia quiz: game-show mode against the clock
- `study-eggs` — 🥚 the easter egg pack

## Capabilities

### New Capabilities

- `study-app`: the retro study app — subject-sorted flashcard decks, the
  flip/mark/drill study flow, and locally persisted progress. Later slices
  (timer, trivia, easter eggs) extend this same capability.

### Modified Capabilities

None.

## Impact

- Code: new file `study.html` (vanilla HTML/CSS/JS, one page). No changes to
  `index.html` or `bubblegum.html`.
- Data: all invented (starter decks); user progress lives in localStorage
  only and can be reset.
- Docs: README gains a third-example row at ship time.
- History: four changes planned — this one plus `study-timer`,
  `study-trivia`, `study-eggs`.
