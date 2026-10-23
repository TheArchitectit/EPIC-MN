# Proposal

## Why

Remember the thrill of a drop landing right when you expect it — the
kick drum in your chest, the light show snapping on every beat, and
your hands keeping time like you were born in the booth? **Beat Booth**
is that feeling as a game: you are the DJ at a CRT-lit neon club, and
the crowd roars when your timing is tight. Notes rush the hit line,
you strike on the beat, and every perfect hit feeds the streak — miss,
and the glow dims until you find the groove again.
(All tunes are original synthesized beats — the feeling of a club is
free, real songs aren't, like every smart studio does.)

## What Changes

- New single-file HTML app `beats.html`, working title **Beat Booth**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **CRT synth** skin: neon glow under scanlines and CRT
  flicker, like the whole club runs on one giant old television —
  zero image assets, all drawn in code.
- **The drop**: notes travel down glowing lanes toward a hit line at
  the bottom; press the matching key (or on-screen pad) when a note
  crosses the line. Clean hits light the crowd, misses dim the room.
- **Original beats**: each round is an invented synth track generated
  in code (Web Audio) — kick, snare, and bass patterns with no real
  songs anywhere.
- **Streaks and the crowd meter**: consecutive clean hits build a
  perfect streak and fill the crowd meter; big streaks multiply the
  score and push the light show harder.
- **Score & records**: the board keeps the top score and the longest
  perfect streak in one set, with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `beat-booth`: the neon rhythm game — lanes and the hit line, beat-
  locked note patterns from original synth tunes, streak/crowd
  scoring, CRT-synth presentation, and best-set records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `beats.html` and `openspec/specs/beat-booth/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps; sound
  comes from the browser's built-in Web Audio, no audio files.
- README gains a `beat-booth` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `beat-booth-playlist` (a jukebox of more original tracks),
  `beat-booth-battle` (two DJs, one stage), `beat-booth-lightshow`
  (custom light rigs and crowd props).

## Compliance note

Real songs, artist names, and label marks are protected — like the
Frogger-inspired and football builds, we keep the *feeling* (not
protected) and invent our own tunes, name, and art (protected): no
real songs or artist marks anywhere in the app or the README.
