# Design

## Context

Candy Beat (`candy.html`) already owns a complete beat engine: Web
Audio oscillators for kick/snare/hat/bass on the 120 BPM clock plus
jump/orb/stumble blips. What it never does is **unlock** the browser
speaker. Real browsers create every `AudioContext` in the `suspended`
state and only flip it to `running` when `resume()` is called from
inside a user-gesture handler. The shipped game schedules perfect
beats into a muted context — verified `suspended` in a real browser
even mid-run. This change is the missing key in the ignition.

## Goals / Non-Goals

**Goals**
- The first input (any key, canvas tap, or button) turns the speaker
  on; from then on the groove and blips are audible.
- Rock-solid safety: unlocking can never throw, never double-fires
  into an error, and changes nothing when audio is missing.
- Keep the existing sound design — this change unlocks it, it does
  not rewrite it.

**Non-Goals**
- No new melodies or tracks (`candy-beat-tunes` stays parked).
- No volume UI, mute button, or settings (not asked for).
- No fix to Beat Booth's likely same bug (`beat-booth-sound` parked).

## Decisions

1. **`unlockAudio()` helper**: one tiny top-level function —
   `try { if (actx && actx.resume) actx.resume(); } catch (e) {}` —
   guarded twice (existence check + try/catch) so it can never break
   the game, matching the house "audio hiccup" style already used by
   `blip()`.
2. **Where it fires**: at the top of every input path — the document
   `keydown` handler, `tap()` (canvas click + JUMP button), and
   `startRun()` (PRESS START / PLAY AGAIN / Enter). Firing on every
   input is fine: `resume()` is idempotent and cheap once running.
3. **Keep eager creation**: `actx` stays created at load (harness
   stubs depend on it); only the resume is new. Lazy creation would
   break the existing oscillator-counting tests for no player gain.
4. **Harness stub grows a counter**: the stub `AudioContext` gains
   `state: "suspended"` and `resume()` flipping it to `"running"` and
   counting calls — so tests can assert the unlock actually happens,
   and the old oscillator tests keep working unchanged.
5. **Proof in a real browser**: a CDP check reloads `candy.html`,
   confirms `actx.state === "suspended"` before input and
   `"running"` after the first key — the exact failure mode that
   shipped, now impossible to miss.

## Risks / Tradeoffs

- Some browsers auto-resume on their own — harmless: our resume call
  then does nothing visible. Accepted: one code path for all
  browsers.
- Unlocking on *any* input (even CLEAR RECORDS) is slightly broad —
  accepted: it is still a user gesture, and a player clicking around
  the cabinet expects to hear it.

## Migration

None — additive change inside `candy.html`; the archived `candy-beat`
spec keeps its 7 requirements untouched.

## Open Questions

None — the student asked for sound; the diagnosis is verified.
