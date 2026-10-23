# Design

## Context

Beat Booth is a single-file vanilla HTML/CSS/JS rhythm game
(`beats.html`) in the house showcase style. The player is the DJ in
a neon club rendered like a giant CRT television: four glowing lanes
run from the booth down to a hit line, notes ride those lanes on the
beat, and the crowd meter is the house energy. Everything is invented
data, local-only, zero images, and the tunes are synthesized in code.

## Goals / Non-Goals

**Goals**
- A complete rhythm loop: watch the lanes, strike on the beat, ride
  the streak, finish the set (or lose the crowd).
- Timing that feels fair: precise judgment from a real millisecond
  clock, forgiving windows, satisfying flashes and sounds.
- A CRT-synth club look drawn entirely in code.
- House records machinery (seed/load/save/reset + toast).

**Non-Goals**
- No real songs, artist names, or label marks (compliance note in
  the proposal) — every beat is original and synthesized.
- No playlist, two-player battle, or custom light rigs (parked later
  changes).
- No drag-and-drop music editor — one built-in track keeps the code
  classroom-readable.

## Decisions

1. **File & frame**: single `beats.html`; CSS vars themed; canvas
   `draw()` + DOM `render()`; top-level functions for the test
   harness; `TICK_MS = 50` `setInterval` clock (finer than the house
   100 ms because rhythm needs it). Canvas 540×720.
2. **Palette (CRT synth)**: `--void:#0b0518`, `--board:#140b2e`,
   `--ink:#e9e2ff`, `--neon:#ff4fd8`, `--cyan:#41e8ff`,
   `--gold:#ffd24a`, `--lime:#6dff8a`, `--dim:#7a68b8`,
   `--danger:#ff5a6a`, `--scan:rgba(0,0,0,0.28)`.
3. **Phases**: `ready → playing → over → playing → …`. `startSet()`
   arms a fresh set: `songStart` stamps the clock, the chart is
   rebuilt, `streak = 0`, `crowd = 55`, `score = 0`.
4. **The set**: 120 BPM (`BEAT_MS = 500`), 16 bars = 64 beats. Notes
   carry a `hitTime` in ms on the song clock
   (`beat * BEAT_MS + TRAVEL_MS`). Positions are computed from
   `songT = Date.now() - songStart` so movement stays smooth and
   judgment stays precise. The set ends when
   `songT > BEATS * BEAT_MS + TRAVEL_MS + 800` or `crowd <= 0`.
5. **Lanes & keys**: 4 lanes centered at x = 120, 210, 300, 390
   (lane width 90). Keys D/F/J/K and ArrowLeft/Down/Up/Right strike
   lanes 0–3; the on-screen pads (◀ ▼ ▲ ▶ style) do the same; Enter
   or Space starts/restarts. Hit line at `HIT_Y = 600`, notes appear
   at `SPAWN_Y = 90`, travel window `TRAVEL_MS = 1800`.
6. **Judgment**: the nearest unjudged note in the pressed lane within
   `HIT_MS = 120` is judged — `PERFECT_MS = 60` → PERFECT (100 pts),
   else HIT (50 pts). Notes past `hitTime + HIT_MS` unstruck → MISS
   (streak resets, `crowd -= 8`). Empty taps just flash the pad.
7. **Streak & crowd**: after each hit `streak++` and
   `mult = min(4, 1 + floor(streak / 10))`; `score += pts * mult`.
   Crowd meter 0–100: `+4` PERFECT, `+2` HIT, `-8` MISS, start 55,
   cap 100. High crowd brightens the neon glow (light show).
8. **The chart (invented tune "Neon Pulse")**: deterministic 16-bar
   pattern built in code — kick beats 0/2 of every bar (lane 0),
   snare 1/3 from bar 2 (lane 1), hats from bar 1 with off-beat
   extras from bar 4 (lane 2), bass line growing from bar 3 (lane 3).
   No randomness in the notes: every run faces the same song.
9. **Sound (Web Audio, optional)**: `blip(freq, dur, type, gain)`
   helper; kick = sine drop 150→40 Hz, snare = square burst, hat =
   short high square, bass = triangle note, hit blip on strikes.
   Created only if `AudioContext` exists; without it the game runs
   on visual cues alone. No audio files.
10. **Records**: `GKEY = "beat-booth:v1"` holds
    `{ bestScore, bestStreak }` — updated only when improved; NEW
    BEST banner on the result screen; house seed/load/save/reset
    with try/catch; CLEAR RECORDS button resets and toasts.
11. **Screens**: `screen-ready` ("Beat Booth!" + records + DROP THE
    BEAT!), `screen-over` ("The set's over!" or "The crowd went
    home!" + score + best streak + NEW BEST + PLAY AGAIN). Toast
    sits absolute `top: 100px` inside `.boardwrap` — under the HUD
    bar, never over the lanes or the pad strip.
12. **HUD**: canvas bar on top — SCORE, STREAK ×mult, CROWD meter,
    SET progress (bar n of 16) — with judge words (PERFECT!/HIT/MISS)
    as floats near the hit line.
13. **Art**: deep-void background with neon lane strips and borders,
    glowing rounded note bars per lane color (kick gold, snare pink,
    hat cyan, bass lime), bright hit line, pads under the line that
    flash on press, beat pulse on every downbeat, scanline overlay +
    subtle flicker + vignette to sell the CRT.

## Risks / Tradeoffs

- A 50 ms clock is coarser than a pro audio engine — accepted: the
  judgment uses the real millisecond clock at press time (not the
  tick), so fairness doesn't depend on the interval at all.
- One fixed chart could get stale — accepted for the showcase: the
  difficulty lives in the windows and the crowd, and the parked
  `beat-booth-playlist` change is the natural home for more tunes.
- Web Audio scheduling per tick can jitter a few ms — accepted: the
  visual notes are the primary cue and the synth is the vibe layer.

## Migration

None — new capability, new file. Existing showcase apps untouched.

## Open Questions

None — the student locked the shape: hit the beat, neon DJ club,
CRT synth look.
