# Tasks

## 1. Scaffold & Theme

- [ ] 1.1 Create `app/index.html`, `app/styles.css`, `app/app.js` and verify the page opens from the filesystem with no console errors
- [ ] 1.2 Define playful theme tokens (palette, type scale, spacing, radii) and verify they visibly style the header and primary buttons
- [ ] 1.3 Build the five-tab navigation shell (Home, Events, Members, Board, Bookings) and verify each tab swaps views without reloading

## 2. Demo Data

- [ ] 2.1 Add the seed module with invented members, events, rooms, slots, and announcements and verify each dataset is loadable and renders into its view
- [ ] 2.2 Make event dates relative to the current week and verify the upcoming list is never empty on a fresh seed

## 3. Home & Events

- [ ] 3.1 Build the Home view: greeting, next-event highlight, and quick links, and verify the highlight is the earliest upcoming event
- [ ] 3.2 Build the Events list (sorted, cards with tag chips, detail view) and verify order and details match the seed
- [ ] 3.3 Implement the "I'm going" toggle persisted to localStorage and verify reload keeps the choice and the attendee count adjusts both ways

## 4. Members

- [ ] 4.1 Build the roster card grid (avatar initial, name, role, fun fact) and verify every seeded member appears
- [ ] 4.2 Implement live search, role filter, and the friendly empty state and verify combined filters narrow correctly and the empty state shows when nothing matches

## 5. Board

- [ ] 5.1 Build the announcement feed, newest-first with a pinned banner, and verify pinned content stays above newer posts
- [ ] 5.2 Implement the composer posting as the simulated member with a timestamp, persisted to localStorage, and verify the post survives a reload

## 6. Bookings

- [ ] 6.1 Build the room+slot availability grid with capacities and verify all rooms and slots display
- [ ] 6.2 Implement reserve flow, "My bookings" list, and cancel, and verify a booking persists, shows under "My bookings", and cancel frees the slot
- [ ] 6.3 Implement conflict refusal and verify an already-booked room+slot cannot be double-booked and shows the friendly message

## 7. Reset & Polish

- [ ] 7.1 Implement the footer reset control with confirmation and verify it restores seed data and clears all changes
- [ ] 7.2 Wrap all localStorage access in try/catch with in-memory fallback and verify the app still renders when storage is blocked
- [ ] 7.3 Run the visual polish pass and verify at 400px width there is no horizontal scroll and the playful vibe is consistent

## Workflow follow-up

- Archive this change once the built app passes all clubhouse scenarios (view/mark events, roster, board, bookings, reset).
- After archive, verify `openspec/specs/clubhouse/spec.md` exists with the requirements merged.
