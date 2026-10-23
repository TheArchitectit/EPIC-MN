# Spec Delta

## Purpose

A retro, local-only dress-up studio where students style a paper-doll
model with a layered mix-and-match fashion closet, keep a lookbook of
saved looks, and export them as PNG files — built to turn students into
fashion stylists.

## ADDED Requirements

### Requirement: App opens instantly, no gate
The app SHALL be a single static page that opens with no server, network,
or setup, and SHALL present the model and the fashion closet immediately
on load — no menus to click through, no demo mode, no accounts.

#### Scenario: Open and style
- **WHEN** a student opens the page
- **THEN** the model and the closet are ready to use right away

### Requirement: Layered mix-and-match closet
The closet SHALL offer garment pieces across categories: tops, bottoms,
dresses, shoes, hats, bags, and jewelry. Worn pieces SHALL layer onto the
model together in a consistent order so every worn piece stays visible.

#### Scenario: Browse the closet
- **WHEN** the student looks through the closet
- **THEN** the pieces are grouped by category

#### Scenario: Layered look
- **WHEN** the student wears several pieces at once (e.g. top, shoes, hat,
  necklace)
- **THEN** all of them show layered on the model together

### Requirement: Try-on and take-off flow
Tapping a closet piece SHALL wear it on the model in its category slot,
replacing any piece already worn there; tapping a worn piece SHALL remove
it. A dress and a top-plus-bottom outfit SHALL be mutually exclusive. The
model SHALL update instantly on every change.

#### Scenario: Wear a piece
- **WHEN** the student taps a closet piece
- **THEN** it appears on the model in its slot

#### Scenario: Swap or remove
- **WHEN** the student taps a different piece in the same category, or
  taps the worn piece again
- **THEN** the look updates instantly — swapped or removed

#### Scenario: Dress or outfit, not both
- **WHEN** the student wears a dress while a top and bottom are on (or the
  reverse)
- **THEN** the conflicting pieces come off so only one style shows

### Requirement: Lookbook with local persistence
The student SHALL be able to name the current look and save it to a
lookbook. The lookbook SHALL show saved looks as thumbnails and SHALL let
the student reopen one onto the model or delete it. Saved looks SHALL
persist across reloads via browser-local storage only. A visible reset
control SHALL restore the starter state: bare model and empty lookbook.

#### Scenario: Save a look
- **WHEN** the student names and saves the current look
- **THEN** it appears as a thumbnail in the lookbook

#### Scenario: Reopen a look
- **WHEN** the student picks a saved look
- **THEN** its worn pieces load onto the model for more styling

#### Scenario: Delete a look
- **WHEN** the student deletes a saved look
- **THEN** it leaves the lookbook

#### Scenario: Looks survive reload
- **WHEN** the student reloads the page after saving looks
- **THEN** the lookbook still shows them

#### Scenario: Reset everything
- **WHEN** the student uses the reset control
- **THEN** the model returns to bare and the lookbook empties

### Requirement: Export PNG
The app SHALL provide a "save as PNG" control that downloads the current
dressed model as a PNG image file at a shareable size.

#### Scenario: Export the look
- **WHEN** the student uses the PNG export control
- **THEN** a PNG file of the model wearing the current look downloads to
  their device

### Requirement: Retro arcade presentation
The app SHALL look and feel like a retro arcade fashion studio: bright
arcade colors, pixel-style text and buttons, and playful feedback on
saving and exporting. It SHALL stay readable and usable on both phone and
desktop widths.

#### Scenario: Playful feedback
- **WHEN** the student saves or exports a look
- **THEN** the app responds with a visible retro flourish, not a silent,
  plain state change
