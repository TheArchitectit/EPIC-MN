# Design

## Context

See proposal.md — Why. This is the first build of the `clubhouse` capability for a fictional venue. It must run with zero setup: open a file, click around. No accounts, no backend, no online services; every user change stays in the browser.

## Goals / Non-Goals

**Goals:**
- A static app that runs from the filesystem (`file://`) in any modern browser.
- All demo content invented and swappable via one seed module.
- Every user change survives reloads and is fully removable via reset.
- Playful, colorful visual identity that stays usable at phone width.

**Non-Goals:**
- No real backend, accounts, auth, sync, or multi-device state.
- No build tooling, bundlers, frameworks, or dependencies.
- No production deployment or data migration.

## Decisions

**D1 — Plain static files, no tooling.** `app/index.html`, `app/styles.css`, `app/app.js`, opened directly or over a trivial static server. Rationale: zero-install prototype that matches the "no downloads, no online services" constraint. Alternatives considered: a framework SPA (rejected: needs build/serve), a single self-contained HTML file (rejected: harder to read and iterate).

**D2 — localStorage as the only store.** All changes live under one namespaced key (e.g. `zz.clubhouse.v1`). Reads/writes are wrapped in try/catch with in-memory fallback so the app still renders if storage is blocked (private mode, file:// restrictions). Rationale: simplest persistence that survives reloads.

**D3 — Seed data as a versioned module.** A `seed` object (members, events, rooms, slots, announcements) with a `SEED_VERSION` constant. Reset restores it by rewriting the store key. Events use dates computed relative to the current week so the demo always has upcoming events. Rationale: the app always demos well and reset is trivially correct.

**D4 — Simulated signed-in member.** A single invented member constant (name, role, avatar) acts as "you" for posting and booking. Rationale: no accounts, but actions still need an identity to display.

**D5 — Booking identity is a compound key.** `roomId + day + slot` is unique; a reservation is stored as one object per key, so conflict refusal is a lookup, not a scan. "My bookings" filters by the simulated member.

## Risks / Trade-offs

- localStorage can be unavailable or cleared by the browser → mitigated by try/catch fallback and the reset control.
- `file://` behavior differs slightly across browsers (localStorage is generally available) → mitigation: test in the main target browser; fallback keeps the app usable.
- All data is invented and local, so nothing is shared between devices → accepted: this is the point of a local prototype.

## Open Questions

None — remaining unknowns (copy, colors, exact seed roster) are cosmetic and safe to refine after the draft is visible.
