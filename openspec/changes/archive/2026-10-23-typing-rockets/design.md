# Design

## Context

The showcase is a set of single-file vanilla HTML/CSS/JS apps with shared
house machinery (CSS vars, localStorage try/catch + seed/load/save/reset +
toast, `flourish()`/`sparkBurst()` helpers, canvas draw pipelines, stub-DOM
test harness). Typing Rockets joins as a keyboard-driven arcade game — the
first typing game in the showcase — with a retro-neon look chosen by the
student (over the soft-candy default).

## Goals / Non-Goals

**Goals**
- A complete-feeling time trial: pick track → race → results → fly again.
- Typing that feels like fuel: every correct letter visibly moves the rocket.
- Forgiving mistakes: typos sputter, never erase progress.
- Per-track best times as the replay loop.
- Zero image assets; all neon drawn in code.

**Non-Goals**
- Sound effects (`rocket-skins`/`rocket-sounds` parked).
- Multiplayer or online leaderboards.
- Mobile soft-keyboard perfection (letter keys via `keydown` are enough).
- Multiple rocket art styles.

## Decisions

1. **Single-file `typing.html`** in house style: vanilla JS, CSS vars
   (`--ink`, `--pink`, `--cyan`, `--yellow`, `--mint`, `--mono`,
   `--hard:6px 6px 0`) remapped to neon glow values on a deep-indigo page.
2. **Typing engine** — top-level `onKey(e)` bound to `keydown` for letter
   keys `a–z` (case-insensitive). No backspace; wrong letters only sputter.
   Top-level functions (`handleChar`, `pickWord`, `tick`, …) so the stub-DOM
   harness can call them directly.
3. **Progress model** — `speed` (0–1.5) is the engine: correct letter
   `+0.08`, word complete `+0.25` burst, each 100 ms tick decays `*0.992`
   toward 0.3; typo sets `sputterUntil = now + 600 ms` and drops speed to
   `*0.55` once (progress never decreases). `progress += speed * dt /
   trackSeconds` per tick; finish at `progress >= 1`.
4. **Difficulty ramp** — `targetLen = 3 + floor(progress * 5.5)` clamped
   3–8; `pickWord` chooses a word within ±1 letter of target from the
   current pool. Final stretch is automatically boss-rush long words.
5. **Word pools** — three arrays (SPACE / SCHOOL / SILLY), ~12 invented
   words each; `poolIdx = (poolIdx + 1) % 3` per word so the rotation is
   space → school → silly → …
6. **Three tracks** — `launch-loop` (38 s target), `comet-sprint` (25 s),
   `nebula-night` (55 s); each is just a `trackSeconds` value + label +
   accent color. Best times keyed by track id.
7. **Clock** — 100 ms `setInterval` tick accumulates `elapsedMs` and calls
   `tick(dt)`; harness captures the interval and steps a fake clock. Race
   starts on START (screen `ready → racing`), ends in `tick` when
   `progress >= 1` (screen `finished`).
8. **Persistence** — `GKEY = "typing-rockets:v1"` holding
   `{ best: { trackId: ms } }` via house `seed/load/save/reset` with
   try/catch; updated only when a finished race beats the saved ms; toast
   on save and on reset. Corrupt/missing data falls back to seed (all null).
9. **Rendering** — one `<canvas>` pipeline in `draw()`: sky gradient →
   parallax starfield (3 layers, drifting) → synthwave sun (striped circle)
   → perspective grid horizon → track strip with launchpad/finish marks →
   rocket (neon triangle + fins) → flickering flame + trail → spark bursts.
   DOM holds the arcade HUD (TIME / BEST / WORDS / speed bar), the big neon
   word with caret, and screen overlays (ready / finish / NEW BEST).
10. **Verification** — extract inline `<script>` → `node --check`; stub-DOM
    harness in `vm.runInNewContext` (makeEl, localStorage stub, interval
    capture, canvas op recorder) exercising pools, typing fuel, sputter,
    ramp, finish, best-time save/skip/reload, reset; headless Chromium CDP
    screenshots for visual review (ready, mid-race, finish).

## Risks / Tradeoffs

- **Key handling in headless browsers** — harness calls `handleChar`
  directly so logic tests never depend on synthetic key events; CDP only
  needed for visuals.
- **Timer granularity (100 ms)** — displayed times land on 0.1 s steps;
  fine for a kids' arcade, keeps the harness deterministic. (Shown with 2
  decimals as `12.34s`.)
- **Typing feel** — fixed `+0.08` per letter favors steady typing over
  burst-and-idle; decay keeps pressure without punishing beginners.
- **localStorage blocked** — try/catch everywhere; game still runs with
  in-memory bests for the session.

## Migration Plan

New file `typing.html` only; existing apps untouched. README row + specs
bullet + run instructions land at ship. No data migration needed.

## Open Questions

( none — the student answered the four product decisions: Typing Rockets,
time trial, mixed word pools, retro-neon arcade )
