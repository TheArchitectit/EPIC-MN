# Tasks

## 1. Scaffold & game shell

- [x] 1.1 Create `bubblegum.html` with canvas + DOM overlay, gooey candy
      theme (palette, glossy bubbles, playful type), and verify it opens
      from the filesystem with zero console errors
- [x] 1.2 Implement the game state machine (playing → over → restart) and
      verify the page auto-starts into play on load
- [x] 1.3 Add responsive layout + mouse/touch zapping and verify both input
      types pop bubbles

## 2. Core gameplay

- [x] 2.1 Implement bubble spawning, wobbling ascent, per-bubble speed, and
      off-screen miss tracking; verify bubbles rise and are clickable
- [x] 2.2 Implement zap hit-testing, pop bursts, score increment, and the
      special bubbles (gold bonus, sour penalty); verify each behaves
- [x] 2.3 Implement the combo chain counter with bonus scaling and verify a
      rapid chain increases score visibly
- [x] 2.4 Implement score milestones escalating spawn rate/speed and verify
      the game gets visibly harder

## 3. Chaos events

- [x] 3.1 Build the event engine (timer, banner, duration, revert, one
      event at a time); verify events fire during play
- [x] 3.2 Implement at least five distinct events (Gum Tsunami, Gravity
      Flip, All Gold, Slow-Mo, Bubble Storm) and verify each changes play
      and reverts

## 4. Juice & polish

- [x] 4.1 Add burst particles, floating score text, and combo pulse; verify
      they render and don't tank fps on a weak machine
- [x] 4.2 Add screen shake on sour events and synthesized pop sounds via
      WebAudio (all guarded); verify sound works after first click
- [x] 4.3 Implement game-over screen with final score and instant restart;
      verify restart begins a new game cleanly

## 5. Persistence & final checks

- [x] 5.1 Implement localStorage high score (guarded) and "start fresh"
      reset; verify reload keeps best score and reset clears it
- [x] 5.2 Run `openspec validate --all` and fix any findings; verify the
      change validates cleanly
- [x] 5.3 Final wow-pass: verify the page amazes (candy glow, smooth
      frenzy) at 400px width with no horizontal scroll

## Workflow follow-up

- Archive this change after the owner says "ship it".
- Verify the merged spec at `openspec/specs/bubblegum-zap/spec.md` exists
  after archive.
