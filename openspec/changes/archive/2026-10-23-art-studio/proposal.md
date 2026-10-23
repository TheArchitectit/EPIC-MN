# Proposal

## Why

Students at EPIC-MN events love art, and the showcase has no creative app
yet — the Clubhouse organizes, Bubblegum Zap entertains, Study Quest
teaches. The owner wants a fourth example: a retro pixel-art studio where
students MAKE something and take it home. Pixel art is the perfect first
tool — chunky, colorful, and retro by nature.

## What Changes

- New app `art.html` — a retro "Art Arcade" pixel studio: one static page,
  no server, no network, no accounts. Playful, flashy, arcade-style like
  the other examples.
- **Pixel canvas** — draw pixel art on a big chunky grid by clicking,
  tapping, or dragging.
- **Classic toolbox** — paint brush, eraser, fill bucket, and undo.
- **Juicy retro palette** — a curated set of bright arcade colors to paint
  with.
- **Gallery wall** — name a finished drawing and save it to a gallery in
  the browser; browse, reopen, and delete saved art. Progress persists in
  localStorage with a restore/reset control, same contract as the other
  examples.
- **Export PNG** — a "save as PNG" button turns any drawing into a real
  image file the student can keep, share, or put on a poster.

Parked as later changes (named now so nothing gets lost):

- `art-spin` — 🌀 Spin-Art kaleidoscope tool
- `art-poster` — 🎪 Poster & Sticker Maker tool
- `art-doodle` — 🖍️ Doodle Arcade wild brushes

## Capabilities

### New Capabilities

- `art-studio`: the retro art studio — pixel canvas with classic painting
  tools, a curated palette, a locally persisted gallery wall of saved
  drawings, and PNG export. Later slices (spin art, poster maker, doodle
  arcade) extend this same capability.

### Modified Capabilities

None.

## Impact

- Code: new file `art.html` (vanilla HTML/CSS/JS, one page). No changes to
  the three existing examples.
- Data: user drawings live in localStorage only and can be reset; PNG
  export produces a local file download — no network.
- Docs: README gains a fourth-example row at ship time.
- History: four changes planned — this one plus `art-spin`, `art-poster`,
  `art-doodle`.
