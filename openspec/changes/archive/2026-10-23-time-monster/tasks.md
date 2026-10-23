# Tasks

## 1. Page shell & house style

- [x] 1.1 Create `time.html` with house CSS variables, hard-shadow cards, mono chrome, and the stage|panel layout — verify: file loads with zero console errors and both sections render on boot
- [x] 1.2 Add toast, flourish, and sparkBurst helpers plus the reset control chrome — verify: each helper renders on call and reset shows a toast

## 2. Day model & data

- [x] 2.1 Build the APPS table (6 invented apps with color/emoji/seed minutes) and the day state with `seed()` pretend day — verify: seeded minutes match (Math 35, Drawing 45, Video 50, Book 25, Chat 20, Music 15)
- [x] 2.2 Add load/save/reset via localStorage guarded by try/catch with in-memory fallback — verify: reload keeps the day, reset re-seeds with toast, and storage-blocked boot still works

## 3. Monster draw engine

- [x] 3.1 Implement `drawMonster` with rounded body, smiling face, blush, stub feet/arms, and sqrt size mapping from total minutes — verify: larger totals render a larger scale and the canvas draws on load
- [x] 3.2 Draw fur patches in fixed per-app slots sized by each app's share, colors from APPS, face area kept clear — verify: active apps show matching patches and the day list colors agree
- [x] 3.3 Enforce the never-scary rule in every state (smile, rounded shapes, bright palette) and reuse the pipeline for the summary thumbnail — verify: renders cleanly at small and max size with no banned shapes

## 4. Live tap-to-use tracking

- [x] 4.1 App buttons with active ring, demo clock (`MIN_PER_TICK`), switch-on-tap, stop-on-retap — verify: tap accrues minutes, switching stops the old app, retapping the active app stops the clock

## 5. Happiness & stars

- [x] 5.1 Happiness meter from variety + balance with kind-only labels — verify: 4+ apps reads high, one-app day reads low with a gentle label and no scolding words
- [x] 5.2 "Finish my day" summary: 1–3 stars, kind coaching message, finished state saved — verify: balanced day → 3 stars + celebration, one-app day → 1 star + gentle note, no shame words in any message

## 6. Integration checks

- [x] 6.1 Run the full play-test harness over the real script covering every spec scenario — verify: all assertions pass with zero failures
- [x] 6.2 Capture headless-Chromium screenshots (desktop home, mid-growth, summary, phone) and review them — verify: PNGs show a cute monster at every size and a clean layout

## Workflow follow-up

- Update README with Example #6 (run commands, table row, specs bullet).
- Run `openspec validate --all` after implementation.
- Archive the change once the student says "ship it", then verify the merged spec.
- Launch the app on the local web server and open it in the browser.
