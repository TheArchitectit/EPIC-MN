# time-monster Specification

## Purpose
A friendly time-tracking monster that shows students where their day went —
size for total time, colored fur patches for the app mix — scored with
kindness (happiness meter and 1–3 stars), never scolding and never scary.

## Requirements

### Requirement: Opens with a pretend day
The app SHALL load instantly with an invented day of multi-app usage already
tracked, so the monster appears mid-growth with no user input required. All
app names and times SHALL be invented demo data.

#### Scenario: First open
- **WHEN** the student opens the app with no saved day
- **THEN** the monster appears already grown, with fur patches from several invented apps, and the day's app times are listed

### Requirement: Live tap-to-use tracking
The app SHALL let the student tap an app button to "use" that app on an
accelerated demo clock so growth is visible within seconds. Tapping another
app SHALL switch the active session; tapping the active app SHALL stop
accruing. Accrued minutes SHALL accumulate per app for the day.

#### Scenario: Start using an app
- **WHEN** the student taps an app button
- **THEN** that app becomes active and its minutes grow while it stays active

#### Scenario: Switch apps
- **WHEN** the student taps a different app button while one is active
- **THEN** the previous app stops accruing and the tapped app becomes active

#### Scenario: Stop using
- **WHEN** the student taps the active app button again
- **THEN** no app is active and time stops accruing

### Requirement: Monster grows with total time
The app SHALL size the monster proportionally to the day's total tracked
minutes, from small at little total time to large at heavy total time.

#### Scenario: Growth over the day
- **WHEN** total tracked minutes increase
- **THEN** the monster renders larger than before

### Requirement: Fur patches show the app mix
The app SHALL give each app a distinct color and draw a fur patch per app
whose size reflects that app's share of the day's tracked time, so the
monster visibly shows which apps were used.

#### Scenario: Patch appears and grows
- **WHEN** the student accrues minutes in an app
- **THEN** a patch in that app's color appears on the monster's fur and grows with the app's time

#### Scenario: Mix is readable
- **WHEN** the day includes time in three or more apps
- **THEN** the monster shows at least three differently colored patches and the app list colors match the patches

### Requirement: Friendly never-scary presentation
The app SHALL present the monster as a rounded, smiling, brightly colored
creature. Every state — small, huge, low happiness, one star — MUST keep the
friendly look; the app MUST NOT show scary or frightening imagery.

#### Scenario: Cute at any size
- **WHEN** the monster renders at any growth level or mood
- **THEN** it keeps a smiling face, rounded body, and bright friendly colors

### Requirement: Happiness meter rewards variety
The app SHALL show a happiness meter that rises as the day's tracked time
spreads across a wider variety of apps. Its mood label SHALL always use kind
words, even at the lowest level.

#### Scenario: Variety raises happiness
- **WHEN** the day's time is spread across four or more apps
- **THEN** the happiness meter shows a high level with an encouraging label

#### Scenario: A narrow day stays kind
- **WHEN** the day's time is almost entirely one app
- **THEN** the meter shows a lower level with a gentle label and no scolding words

### Requirement: End-of-day star summary
The app SHALL offer a "finish my day" action that shows a summary where the
monster awards 1–3 stars for the day's balance and speaks one kind coaching
message. The summary MUST NOT use shame or warning language.

#### Scenario: Balanced day earns three stars
- **WHEN** the student finishes a day with time spread across several apps
- **THEN** the monster awards 3 stars and a celebratory message

#### Scenario: Narrow day earns gentle coaching
- **WHEN** the student finishes a day dominated by one app
- **THEN** the monster awards 1 star and a gentle encouraging message without scolding

### Requirement: Local persistence and reset
The app SHALL save the current day's per-app minutes and state in
localStorage guarded by try/catch, and SHALL offer a visible reset control
that restores the fresh pretend day with a toast confirmation. All behavior
MUST work even when storage is blocked.

#### Scenario: Day survives reload
- **WHEN** the student accrues time and reloads the page
- **THEN** the saved day reappears with the same per-app minutes

#### Scenario: Reset to fresh day
- **WHEN** the student taps the reset control
- **THEN** the day returns to the fresh pretend-day starting point and a toast confirms the restore

#### Scenario: Storage blocked
- **WHEN** localStorage throws on read or write
- **THEN** the app still opens, tracks time, and shows the monster without crashing

### Requirement: Retro arcade presentation
The app SHALL use the house retro-arcade look — bold uppercase mono labels,
hard-shadow cards, bright palette, floating flourish texts and sparkles —
with invented data only and no network or account features.

#### Scenario: House style
- **WHEN** the student opens the app
- **THEN** it renders in the same bold retro-arcade visual language as the other showcase examples and makes no external requests
