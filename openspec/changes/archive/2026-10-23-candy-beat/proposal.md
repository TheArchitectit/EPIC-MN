# Proposal

## Why

Remember feeding coins into a cabinet and feeling the whole machine
flash when you nailed it? **Candy Beat** is that feeling as a game:
a rhythm auto-runner inside a pixel arcade-cabinet world. Your hero
runs to the music and **one tap = jump** — leap the gaps, grab the
pop-up beat-orbs before they vanish, and land your taps on the beat
so the dance-floor crowd grades your groove. Perfect hits explode in
candy-80s flash — hot pink, electric blue, lemon yellow — and miss
the beat long enough and the lights go out.
(Original name, tunes, and art in the coin-op spirit — the feeling
is free, real game marks aren't, like every smart studio does.)

## What Changes

- New single-file HTML app `candy.html`, working title **Candy Beat**,
  in the house showcase style (vanilla HTML/CSS/JS, invented data)
  wearing a **candy-80s** skin: star bursts, rainbows, and chunky
  pixel mountains/pipes/star fields inside an arcade-cabinet frame —
  zero image assets, all drawn in code.
- **The run**: the hero auto-runs left-to-right through the cabinet
  world while the track scrolls to the music; the only control is
  TAP (space/click/on-screen JUMP) to hop gaps, spikes, and pipes.
- **Pop-up beat-orbs**: candy orbs pop up along the route and vanish
  if ungrabbed — jumping through one scores bonus and flash.
- **On-beat judgment**: each tap is graded against the beat clock —
  ON BEAT fills the dance-floor crowd meter and multiplies the score;
  sloppy taps dim the flash; the meter empty ends the run early.
- **Score & records**: the board keeps the top score and the longest
  on-beat streak in one run, with the house seed/load/save/reset +
  toast machinery.
- README updated at ship with run instructions.

## Capabilities

### New Capabilities
- `candy-beat`: the candy-80s rhythm auto-runner — one-tap jumping
  through the arcade-cabinet world, pop-up beat-orbs, on-beat groove
  judgment with the dance-floor crowd, candy-80s presentation, and
  best-run records.

### Modified Capabilities

( none — the existing showcase apps stay exactly as they are )

## Impact

- Adds `candy.html` and `openspec/specs/candy-beat/spec.md` (new).
- No new dependencies — plain HTML like the other showcase apps; the
  beat comes from the browser's built-in Web Audio, no audio files.
- README gains a `candy-beat` row and specs bullet at ship time.
- **Parked later changes** (named aloud, not built today):
  `candy-beat-tunes` (more original tracks), `candy-beat-costumes`
  (hero skins and trails), `candy-beat-worlds` (new cabinet lands).

## Compliance note

Real game titles, series names, and studio marks are protected —
like the Frogger-inspired and football builds, we keep the *feeling*
(not protected) and invent our own name, art, and tunes (protected):
no real game or studio marks anywhere in the app or the README.
