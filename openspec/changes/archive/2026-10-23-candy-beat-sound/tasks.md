# Tasks

## 1. Unlock the speaker
- [x] 1.1 Add the guarded `unlockAudio()` helper to `candy.html`
  (resume the AudioContext, never throw) — verify: `node --check` on
  the extracted script passes
- [x] 1.2 Wire the unlock into every input path (keydown handler,
  `tap()`, `startRun()`) — verify: harness drives each path and the
  stub records `resume()` calls / state `"running"`

## 2. Keep the groove honest
- [x] 2.1 Re-verify beat + blip scheduling with the unlock in place
  (kick/snare/hat/bass on the clock, jump/orb/stumble blips) —
  verify: harness sees oscillators scheduled after a gesture, and
  the silent-browser path still runs clean
- [x] 2.2 Prove it in a real browser — verify: CDP shows `actx.state`
  `suspended` before input and `running` after the first key, mid-run
  the beat keeps scheduling

## 3. Check and ship
- [x] 3.1 Run the full stub-DOM harness (all prior scenarios + the
  new unlock ones) — verify: every test passes (node
  /tmp/candy-test.js)
- [x] 3.2 Run `openspec validate --all` after the build — verify:
  all items green

## Workflow follow-up
- [x] 4.1 Show the student the finished sound fix and wait for
  "ship it" before `openspec archive candy-beat-sound --yes`
- [x] 4.2 Verify the merged spec at
  `openspec/specs/candy-beat/spec.md` after archiving (8
  requirements, sound among them)
