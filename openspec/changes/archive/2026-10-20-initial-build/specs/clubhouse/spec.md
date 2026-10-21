# Spec Delta

## Purpose

A local-only member hub for a fictional clubhouse: upcoming events, member profiles, house announcements, and room bookings on one playful page.

## ADDED Requirements

### Requirement: App shell & navigation
The app SHALL be a single static page that opens with no server or network and SHALL provide navigation among five views: Home, Events, Members, Board, and Room Bookings. The UI SHALL adapt to phone and desktop widths in a playful, colorful style.

#### Scenario: Open and navigate
- **WHEN** a member opens the app
- **THEN** the Home view appears with tabs for all five views, and clicking each tab shows that view without reloading

#### Scenario: Works offline
- **WHEN** a member opens the page straight from local files
- **THEN** all views render without any network request

### Requirement: Events & schedule
The app SHALL list upcoming events sorted by start time, each with title, date/time, room, host, and tag. Selecting an event SHALL show its full details. A member SHALL be able to mark interest in an event, which persists across reloads and updates the event's attendee count.

#### Scenario: Browse upcoming events
- **WHEN** a member opens the Events view
- **THEN** upcoming events appear in date order with title, date/time, room, host, and tag, and clicking an event shows its details

#### Scenario: Mark event interest
- **WHEN** a member clicks "I'm going" on an event
- **THEN** the button becomes "Going", the attendee count increments, and the choice survives a reload; clicking again unmarks and decrements

### Requirement: Member roster
The app SHALL show members as cards with name, role, fun fact, and an avatar initial, and SHALL support live search by name and filtering by role, with a friendly message when nothing matches.

#### Scenario: Find members by name or role
- **WHEN** a member types in the search box or selects a role filter
- **THEN** the roster narrows live to matching cards, combined filters apply together, and a friendly empty state appears when nothing matches

### Requirement: Board announcements
The app SHALL show house announcements newest-first, with pinned announcements kept above newer posts. A member SHALL be able to post a notice as the simulated signed-in member, which persists across reloads.

#### Scenario: Post a house notice
- **WHEN** a member writes a notice and clicks Post
- **THEN** the notice appears at the top of the feed, stamped with the simulated member's name and a time, and survives a reload

#### Scenario: Pinned announcement stays on top
- **WHEN** new posts are added after a pinned announcement exists
- **THEN** the pinned announcement remains above all newer posts

### Requirement: Room bookings
The app SHALL list rooms with capacity and weekly time slots, SHALL let a member reserve a room for a slot, SHALL show that member's own bookings with a cancel control, and SHALL refuse any attempt to double-book the same room+slot.

#### Scenario: Reserve a room slot
- **WHEN** a member picks a free room+slot and confirms
- **THEN** the slot shows the booking with the simulated member as booker, appears in "My bookings", and survives a reload

#### Scenario: Cancel a booking
- **WHEN** a member cancels one of their bookings
- **THEN** the slot becomes free again and the booking leaves "My bookings"

#### Scenario: Refuse a conflicting reservation
- **WHEN** a member tries to reserve a room+slot that is already booked
- **THEN** the app shows a friendly "already taken" message and does not change any state

### Requirement: Local-only persistence & demo reset
All user changes SHALL persist only in browser local storage. A reset control SHALL restore the original seeded demo data, clearing all changes.

#### Scenario: Changes survive reload
- **WHEN** a member makes changes and reloads the page
- **THEN** all event interest, posts, and bookings remain

#### Scenario: Reset restores demo data
- **WHEN** a member confirms the reset control
- **THEN** all changes are cleared and the original demo data is restored

### Requirement: Empty states
Every view SHALL render a friendly message instead of a blank screen when its content is empty or filtered to nothing.

#### Scenario: Friendly empty messages
- **WHEN** search results, the board, or the upcoming list are empty
- **THEN** a friendly, styled message explains that there is nothing to show
