# art-studio Specification

## Purpose
A retro, local-only pixel-art studio where students draw chunky pixel art
with classic painting tools, keep a gallery wall of saved drawings, and
export their art as PNG files — built to turn students into creators.

## Requirements

### Requirement: App opens instantly, no gate
The app SHALL be a single static page that opens with no server, network,
or setup, and SHALL present the pixel canvas and painting tools immediately
on load — no menus to click through, no demo mode, no accounts.

#### Scenario: Open and draw
- **WHEN** a student opens the page
- **THEN** the pixel canvas, palette, and tools are ready to use right away

### Requirement: Pixel canvas drawing
The app SHALL show a chunky pixel grid. Clicking, tapping, or dragging on
the grid SHALL paint the selected color onto the pixels under the pointer,
and painted pixels SHALL stay until changed or erased.

#### Scenario: Paint a pixel
- **WHEN** a student clicks or taps a pixel with the brush selected
- **THEN** that pixel takes the selected palette color

#### Scenario: Drag-paint a stroke
- **WHEN** a student drags across the grid with the brush selected
- **THEN** every pixel along the path is painted

### Requirement: Classic toolbox
The app SHALL provide four tools: paint brush, eraser, fill bucket, and
undo. The eraser SHALL clear pixels to empty; the fill bucket SHALL flood
the connected region of one color with the selected color; undo SHALL
revert the most recent change.

#### Scenario: Erase pixels
- **WHEN** a student paints with the eraser
- **THEN** the touched pixels become empty again

#### Scenario: Flood fill
- **WHEN** a student clicks a region with the fill bucket
- **THEN** the whole connected region of that same color changes to the
  selected color

#### Scenario: Undo a change
- **WHEN** a student presses undo after a change
- **THEN** that change is reverted on the canvas

### Requirement: Retro palette
The app SHALL offer a curated palette of bright arcade colors; selecting a
swatch SHALL make it the active paint color and SHALL be visibly indicated.

#### Scenario: Pick a color
- **WHEN** a student taps a palette swatch
- **THEN** that swatch becomes the active paint color, shown as selected

### Requirement: Gallery wall with local persistence
A student SHALL be able to name the current drawing and save it to a
gallery wall. The gallery SHALL show saved drawings as thumbnails and
SHALL let the student reopen one into the canvas or delete it. Saved
drawings SHALL persist across reloads via browser-local storage only. A
visible reset control SHALL restore the starter state: empty canvas and
empty gallery.

#### Scenario: Save to gallery
- **WHEN** a student names and saves the current drawing
- **THEN** it appears as a thumbnail on the gallery wall

#### Scenario: Reopen a drawing
- **WHEN** a student picks a saved drawing
- **THEN** its pixels load into the canvas for more editing

#### Scenario: Delete a drawing
- **WHEN** a student deletes a saved drawing
- **THEN** it leaves the gallery wall

#### Scenario: Progress survives reload
- **WHEN** a student reloads the page after saving drawings
- **THEN** the gallery still shows them

#### Scenario: Reset everything
- **WHEN** the student uses the reset control
- **THEN** the canvas and gallery return to the empty starter state

### Requirement: Export PNG
The app SHALL provide a "save as PNG" control that downloads the current
drawing as a PNG image file at a shareable size. Empty pixels SHALL export
as transparent.

#### Scenario: Export the art
- **WHEN** a student uses the PNG export control
- **THEN** a PNG file of the current drawing downloads to their device

### Requirement: Retro arcade presentation
The app SHALL look and feel like a retro arcade art studio: bright arcade
colors, pixel-style text and buttons, and playful feedback on saving and
exporting. It SHALL stay readable and usable on both phone and desktop
widths.

#### Scenario: Playful feedback
- **WHEN** a student saves or exports a drawing
- **THEN** the app responds with a visible retro flourish, not a silent,
  plain state change
