# Tasks

## 1. Scaffold & canvas

- [x] 1.1 Create `art.html` shell with retro CSS (arcade palette, chunky
      shadows, monospace stack) and verify the page opens from disk with
      canvas, toolbox, and palette visible immediately (spec: opens
      instantly, retro presentation)
- [x] 1.2 Implement canvas rendering of the 32×32 pixel grid with readable
      empty cells and verify the grid draws correctly at phone and desktop
      sizes

## 2. Toolbox

- [x] 2.1 Implement the paint brush with click/tap/drag strokes (with
      path interpolation) and verify painting applies the selected color
      along the whole stroke
- [x] 2.2 Implement palette selection and the eraser and verify tapping a
      swatch changes the paint color (with visible selection) and the
      eraser clears pixels to empty
- [x] 2.3 Implement the fill bucket (iterative flood fill) and the undo
      stack and verify fill repaints a connected region and undo reverts
      the most recent change

## 3. Gallery & export

- [x] 3.1 Implement name + save + thumbnail gallery (open, delete) with
      `seed()` / `load()` / `save()` on `art-studio-gallery:v1` and verify
      saved drawings persist across reloads and reopen into the canvas
- [x] 3.2 Implement PNG export via data-URL download and verify a PNG
      file downloads and empty pixels are transparent in it
- [x] 3.3 Implement the reset control with toast and verify canvas and
      gallery return to the empty starter state

## 4. Integration checks

- [x] 4.1 Verify the full experience at phone and desktop widths — draw,
      tools, gallery, and export all readable and usable
- [x] 4.2 Verify the studio works fully with storage blocked
      (private-mode simulation) — painting and export work, only gallery
      persistence is skipped
- [x] 4.3 Run `openspec validate --all` and fix any findings; play-check
      one full path: draw → fill → undo → save → reopen → export

## Workflow follow-up

- Add a fourth-example row to README.md and note `art.html` in the run
  commands at ship time.
- Archive this change after the owner says "ship it", then verify the
  merged spec at `openspec/specs/art-studio/spec.md`.
