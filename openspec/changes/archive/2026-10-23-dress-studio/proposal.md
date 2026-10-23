# Proposal

## Why

Students at EPIC-MN events love style and fashion as much as games and
art, and the showcase has no fashion app yet. The owner wants a fifth
example: a retro dress-up studio where students style a model with a big
mix-and-match closet — building complete looks like a fashion stylist.
A lookbook lets them keep their best looks and take them home as PNGs.

## What Changes

- New app `dress.html` — a retro "Dress Studio" fashion arcade: one static
  page, no server, no network, no accounts. Playful, flashy, arcade-style
  like the other examples.
- **The model** — a friendly paper-doll style model to dress up, shown
  center stage.
- **The big fashion closet** — layered categories to mix: tops, bottoms
  and dresses, shoes, hats, bags, and jewelry. Each worn piece layers on
  the model in order.
- **Style it up** — tap or click garment pieces to try them on and take
  them off; the model updates instantly. One look at a time, built piece
  by piece.
- **Lookbook** — name the current look and save it to a lookbook in the
  browser; browse, reopen, and delete saved looks. Looks persist in
  localStorage with a restore/reset control, same contract as the other
  examples.
- **Export PNG** — a "save as PNG" button turns the current look into a
  real image file the student can keep, share, or print.

Parked as later changes (named now so nothing gets lost):

- `dress-runway` — 🎀 the runway show: watch the model walk in your look
- `dress-packs` — 🎪 theme packs: curated collections like Royal Ball and
  Street Style

## Capabilities

### New Capabilities

- `dress-studio`: the retro dress-up studio — a layered mix-and-match
  closet styled onto a model, a locally persisted lookbook of saved looks,
  and PNG export. Later slices (runway show, theme packs) extend this same
  capability.

### Modified Capabilities

None.

## Impact

- Code: new file `dress.html` (vanilla HTML/CSS/JS, one page). No changes
  to the four existing examples.
- Data: all garments invented (drawn in code); looks live in localStorage
  only and can be reset; PNG export produces a local file download — no
  network.
- Docs: README gains a fifth-example row at ship time.
- History: three changes planned — this one plus `dress-runway` and
  `dress-packs`.
