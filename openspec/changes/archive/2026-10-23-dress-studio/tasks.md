# Tasks

## 1. Scaffold & model

- [x] 1.1 Create `dress.html` shell with retro CSS (arcade palette, chunky
      shadows, monospace stack) and the portrait canvas stage, and verify
      the page opens from disk with model and closet visible immediately
      (spec: opens instantly, retro presentation)
- [x] 1.2 Draw the paper-doll model and the fixed layer pipeline
      (body → dress | top+bottom → shoes → bag → jewelry → hat) and verify
      the bare model renders correctly

## 2. Closet & styling

- [x] 2.1 Define closet pieces across all seven categories with draw
      functions and scaled chip previews, and verify chips show
      recognizable previews grouped by category
- [x] 2.2 Implement try-on / take-off with instant updates, slot swaps,
      and the dress-XOR-outfit rule, and verify tap wears, tap again
      removes, same-slot taps swap, and a dress and top+bottom never show
      together
- [x] 2.3 Verify a layered look (top, shoes, hat, jewelry) shows every
      worn piece at once in the fixed order

## 3. Lookbook & export

- [x] 3.1 Implement name + save + thumbnail lookbook (open, delete) with
      `seed()` / `load()` / `save()` on `dress-studio-lookbook:v1`, and
      verify saved looks persist across reloads and reopen onto the model
- [x] 3.2 Implement PNG export via data-URL download at 2× stage size and
      verify a PNG of the dressed model downloads with a slugged filename
- [x] 3.3 Implement the reset control with toast and verify the model
      returns to bare and the lookbook empties

## 4. Integration checks

- [x] 4.1 Verify the full experience at phone and desktop widths —
      closet, styling, lookbook, and export all readable and usable
- [x] 4.2 Verify the studio works fully with storage blocked
      (private-mode simulation) — styling and export work, only lookbook
      persistence is skipped
- [x] 4.3 Run `openspec validate --all` and fix any findings; play-check
      one full path: style → save → reopen → export

## Workflow follow-up

- Add a fifth-example row to README.md and note `dress.html` in the run
  commands at ship time.
- Archive this change after the owner says "ship it", then verify the
  merged spec at `openspec/specs/dress-studio/spec.md`.
