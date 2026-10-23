# Design

## Context

Three examples already ship as single-file vanilla HTML/CSS/JS pages with
zero frameworks, zero network calls, invented data, and localStorage
guarded by try/catch with a visible restore control. `art.html` joins them
under the same rules. See proposal.md — Why for motivation and
specs/art-studio/spec.md for the behavior contract.

## Goals / Non-Goals

**Goals:**
- One self-contained `art.html`, openable straight from disk.
- Smooth click/tap/drag painting on touch and mouse.
- Real PNG output — art the student can actually take home.
- Code a student can follow: one state object, plain functions, no
  libraries.

**Non-Goals:**
- Spin art, poster maker, and doodle arcade (parked: `art-spin`,
  `art-poster`, `art-doodle`).
- Layers, selection tools, resizeable canvases, text tool.
- Cloud sync, accounts, or any network — including "sharing" buttons.
- Audio (Bubblegum Zap owns the chiptune showpiece).

## Decisions

- **`<canvas>` for the pixel grid, not a DOM grid.** PNG export is a
  first-class promise, and `canvas.toDataURL()` is the natural, offline
  way to produce it; drag-painting also stays smooth at pointer speed.
  *Alternative:* a grid of divs — rejected: export would need a second
  render path anyway, and hundreds of DOM nodes jank on drag.
- **32×32 grid, editor scale 16px/cell (512px canvas), export at
  16px/cell.** Chunky enough to look retro, fine enough for a smiley or a
  heart. *Alternative:* 16×16 — too coarse for gallery art; 64×64 — too
  tiny to tap on a phone.
- **Cells store a palette hex or `null` (empty).** Empty renders as
  cabinet-dark in the editor (readable grid) but as **transparent** in the
  export — the promise in the spec. *Alternative:* a real checkerboard
  pattern in the editor — rejected: visual noise behind the art.
- **Undo = snapshot stack capped at 30.** Each stroke/fill/erase gesture
  pushes a copy of the cell array before it runs. *Alternative:* command
  pattern (inverse ops) — rejected: more machinery than a paint toy needs.
- **Fill bucket = iterative BFS flood fill.** No recursion, so a
  32×32 all-same-color canvas can't blow a call stack.
- **Gallery in one localStorage key** `art-studio-gallery:v1`, items:
  `{id, name, cells, created}`, full cell arrays as JSON (a few KB each).
  Cap 24 items; on full, toast asks the student to delete one.
  *Alternative:* run-length compression — rejected: premature for this
  size.
- **PNG download via an anchor + data URL.** Works from `file://` and
  `http://`, no server, no Blob quirks. Filename derived from the art's
  name (`my-art.png`, fallback `pixel-art.png`).
- **Naming without `prompt()`** — an inline name field next to the save
  button (house style keeps all UI in-page; `prompt()` is also blocked in
  some embedded browsers).

## Risks / Trade-offs

- [Drag-painting scrolls the page on touch] → `touch-action:none` on the
  canvas plus pointer capture during a stroke.
- [Fast drags skip cells] → interpolate the cell path between pointer
  events (steps along the grid line).
- [localStorage quota with many drawings] → 24-item gallery cap + toast;
  try/catch on every write so a full disk never breaks painting.
- [storage blocked (private mode)] → try/catch fallback to in-memory
  gallery; the studio still paints, exports, and undoes.
- [Undo during a long stroke double-fires] → one snapshot per gesture
  (pointerdown), not per cell.

## Migration Plan

Brand-new file, nothing to migrate. Ship = add `art.html` + a README row;
rollback = remove those. The three existing examples are untouched.

## Open Questions

- Exact palette colors and gallery empty-state wording are flavor —
  invented at build time, no spec impact.
