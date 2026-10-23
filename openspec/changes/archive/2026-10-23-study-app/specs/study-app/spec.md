# Spec Delta

## Purpose

A retro, local-only study app where students drill school material with
flashcard decks sorted by subject — built to make studying feel like an
arcade game. This first slice is flashcards; timer, trivia, and easter
eggs come in later changes.

## ADDED Requirements

### Requirement: App opens instantly, no gate
The app SHALL be a single static page that opens with no server, network,
or setup, and SHALL present its subject decks immediately on load — no
menus to click through, no demo mode, no accounts.

#### Scenario: Open and see decks
- **WHEN** a student opens the page
- **THEN** the subject decks are visible and ready to study right away

### Requirement: Subject-sorted flashcard decks
The app SHALL ship starter flashcard decks of invented data, sorted by
subject (at least Math, Vocab, and History), each deck a stack of cards
with a front (question) and back (answer). A student SHALL be able to open
any deck to study it.

#### Scenario: Pick a subject
- **WHEN** a student picks a subject deck
- **THEN** that deck opens with its cards ready to flip

### Requirement: Flip and mark flow
Studying a deck SHALL show one card at a time: the student flips the card
to reveal its answer, then marks it "got it" or "missed it", and the next
card appears.

#### Scenario: Flip a card
- **WHEN** a student clicks or taps a card
- **THEN** it flips to show the answer side

#### Scenario: Mark the card
- **WHEN** a student marks a flipped card "got it" or "missed it"
- **THEN** the next card of the deck appears, or the session ends if no
  cards remain

### Requirement: Missed-card drill
When a student finishes a deck with any cards marked "missed it", those
cards SHALL come back for another round — and keep coming back until every
card has been marked "got it" at least once in the session.

#### Scenario: Missed cards return
- **WHEN** a deck run ends with one or more cards marked "missed it"
- **THEN** a new round starts with just those missed cards

#### Scenario: Clear the deck
- **WHEN** every card in a session has been marked "got it"
- **THEN** the app shows a clear-deck celebration with how many rounds it
  took

### Requirement: Local progress with reset
Progress SHALL persist across reloads using browser-local storage only:
which cards keep getting missed per subject and the student's best
clear-deck runs. The app SHALL provide a visible reset control that
restores the starter state.

#### Scenario: Progress survives reload
- **WHEN** a student reloads the page after studying
- **THEN** missed-card tallies and best runs are still shown

#### Scenario: Reset everything
- **WHEN** the student uses the reset control
- **THEN** progress returns to the starter state, and the starter decks
  remain intact

### Requirement: Retro arcade presentation
The app SHALL look and feel like a retro arcade game: bright arcade
colors, pixel-style text and buttons, and playful feedback on flips,
marks, and the clear-deck celebration. It SHALL stay readable and usable
on both phone and desktop widths.

#### Scenario: Playful feedback
- **WHEN** a student flips or marks a card
- **THEN** the app responds with a visible retro flourish (not a silent,
  plain state change)
