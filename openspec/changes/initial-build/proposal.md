# Proposal

## Why

Zigzag Clubhouse (fictional) has no single place for members to see what's on, know who's who, share house notices, and claim rooms. Members currently piece this together from physical corkboards and word of mouth. This change builds the first working prototype: a tiny, local-only web app that runs entirely in the browser, with invented demo data.

## What Changes

- Adds a single static web app (vanilla HTML/CSS/JS, no build step, no server) with five views: Home, Events, Members, Board, and Room Bookings.
- Seeds fully invented demo data: members, events, rooms, time slots, and announcements.
- Persists user changes (event interest, posts, bookings) in browser local storage only — no accounts, no backend, no online services.
- Provides a reset control to restore the original demo data.

## Capabilities

### New Capabilities

- `clubhouse`: member-facing behavior of the clubhouse app — event browsing and interest, the member roster, house announcements, and room bookings, plus local-only persistence and reset.

### Modified Capabilities

None.

## Impact

- Code: a small static app directory (HTML/CSS/JS) — no dependencies, no build, no deployment.
- Data: all demo content is invented; anything a member changes lives only in their browser.
- Operations: none (local prototype).
