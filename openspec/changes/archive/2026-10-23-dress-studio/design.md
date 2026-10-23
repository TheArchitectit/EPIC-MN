# Design

## Context

Four examples already ship as single-file vanilla HTML/CSS/JS pages with
zero frameworks, zero network calls, invented data, and localStorage
guarded by try/catch with a visible restore control. `dress.html` joins
them under the same rules. See proposal.md — Why for motivation and
specs/dress-studio/spec.md for the behavior contract.

## Goals / Non-Goals

**Goals:**
- One self-contained `dress.html`, openable straight from disk.
- Garments drawn entirely in code (zero image assets, house rule) yet
  instantly recognizable — a paper-doll model that looks friendly.
- Layered looks that render the same way on the stage, in lookbook
  thumbnails, and in the exported PNG (one drawing pipeline, three uses).
- Code a student can follow: one state object, plain draw functions.

**Non-Goals:**
- Runway show and theme packs (parked: `dress-runway`, `dress-packs`).
- Drag-and-drop positioning of garments (tap-to-wear is the contract; free
  placement is a different app).
- Designing new garments in-app, cloth physics, or photo import.
- Audio (Bubblegum Zap owns the chiptune showpiece).

## Decisions

- **`<canvas>` stage (480×640 portrait), not DOM/SVG clothes.** PNG export
  is a spec promise, and `canvas.toDataURL()` is the same proven offline
  path `art.html` uses. *Alternative:* SVG garments rasterized to canvas —
  rejected: async image loading for no gain; DOM clothes — rejected:
  export can't capture them faithfully.
- **Garments are draw functions with color palettes.** Each piece is
  `draw(ctx)` using plain shapes (rects, arcs, curves) at fixed stage
  coordinates; a declared `box [x,y,w,h]` frames its closet-chip preview.
  *Alternative:* sprite images — rejected: violates the zero-assets rule.
- **Fixed layer order: body → dress | (top → bottom) → shoes → bag →
  jewelry → hat.** Guarantees the "every worn piece stays visible" promise
  and matches real dress-up layering.
- **Slots + mutual exclusion.** `worn = {top, bottom, dress, shoes, hat,
  bag, jewelry}`; wearing a dress clears top+bottom and vice versa (the
  spec's dress-XOR-outfit rule) — enforced in one `wear()` function.
- **One drawing pipeline, three uses.** `drawLook(ctx)` renders the full
  stage; the lookbook thumbnails and the PNG export call it at different
  scales, so what you see is what you save and what you export.
- **Lookbook in one localStorage key** `dress-studio-lookbook:v1`, items:
  `{id, name, worn, created}` — only slot ids, so a look is a few hundred
  bytes. Cap 24 looks; on full, toast asks the student to delete one.
- **PNG download via anchor + data URL** at 2× stage size for a crisp,
  shareable image, filename slugified from the look's name (fallback
  `my-look.png`) — same proven pattern as `art.html`.
- **Naming via in-page input** (no `prompt()`), same house style.

## Risks / Trade-offs

- [Garment drawings look wonky in tiny closet chips] → chips re-run the
  same `draw(ctx)` scaled inside the piece's declared box — one source of
  truth, no hand-drawn mini icons to drift.
- [Layer order surprises (bag under a jacket, hat under hair)] → hair is
  part of the body layer, and the fixed order above is documented in code.
- [localStorage quota with many looks] → 24-look cap + toast; try/catch on
  every write so a full disk never breaks styling.
- [storage blocked (private mode)] → try/catch falls back to in-memory
  lookbook; styling and PNG export still work.
- [Export needs the model's backdrop] → export paints the same retro
  backdrop as the stage, so the PNG is poster-ready (no transparency
  promise in this spec).

## Migration Plan

Brand-new file, nothing to migrate. Ship = add `dress.html` + a README
row; rollback = remove those. The four existing examples are untouched.

## Open Questions

- Exact garment colors and piece counts per category are flavor —
  invented at build time, no spec impact.
