# Design

## Context

See proposal.md — Why. Extends the existing game audio that already
synthesizes sound-effect blips.

## Goals / Non-Goals

**Goals:**
- A musical retro loop (bass square, lead triangle, noise hat) at ~132 BPM.
- Music is a background layer: quiet, upbeat, and optional.

**Non-Goals:**
- No melody assets, no streaming, no download.

## Decisions

**D1 — Lookahead step sequencer.** A `setInterval` scheduler (every 90ms)
starts notes up to ~120ms ahead of the AudioContext clock. Low latency,
simple, and battle-tested for this scale.

**D2 — Voices.** Bass plays square waves on even 16th steps; lead plays a
triangle pentatonic riff every 4th step; a filtered-noise hat accents every
other bar. All through one music gain node (~0.05).

**D3 — Autoplay handling.** The sequencer is armed on the first `pointerdown`
via the existing audio unlock path. The toggle flips a flag that the
sequencer checks; off pauses scheduling, on resumes seamlessly.

**D4 — UI.** A `🎵 on/off` pill next to the "start fresh" button, styled
the same way.

## Risks / Trade-offs

- Browsers may block audio until a gesture → music simply starts at first
  interaction; the game fully works silent.
- Scheduling drift → the lookahead window keeps timing tight.
