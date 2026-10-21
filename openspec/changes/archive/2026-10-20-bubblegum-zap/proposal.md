# Proposal

## Why

EPIC-MN exists to get students excited about AI in IT at career events. We
already have Example #1 (the clubhouse). We want a second example that kids
can *feel* immediately — a silly, flashy game. Building it through reverse
prompting + OpenSpec in front of them is the real lesson; the game is the
proof that the process works. Also: bubblegum zapping is fun.

## What Changes

- Adds a new, self-contained game page (`bubblegum.html`), hand-written from
  zero like Example #1: no frameworks, no assets from the internet, no
  accounts, local-only.
- The game is **Bubblegum Zap**: a gooey candy world where bubbles of
  bubblegum float up and you zap them in a fast tap frenzy.
- **Maximum chaos** is a design requirement: random silly events regularly
  hijack the game (gum tsunamis, gravity flips, and worse).
- High score persists in browser storage; a "start fresh" control exists.
- The existing clubhouse page stays untouched — it remains Example #1.

## Capabilities

### New Capabilities

- `bubblegum-zap`: the Bubblegum Zap game itself — spawning, zapping,
  scoring, combo frenzy, chaos events, gooey presentation, and local-only
  persistence.

### Modified Capabilities

None.

## Impact

- Code: one new static file at the repo root (`bubblegum.html`), no
  dependencies, no build step.
- Data: invented; user data (high score) stays in the browser.
- Operations: none. Works offline, double-click or served.
