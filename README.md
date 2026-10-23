# 🔷 EPIC-MN — AI in IT, built by hand

**Mission: get students excited about AI in IT.** Everything in this repo is
hand-built — zero frameworks, zero plugins, zero internet calls — and
designed so a **student drives** the building process, with the engineer
(Claude) executing and narrating every step.

This is the public showcase for the pod I was in for  **https://epic-mn.com/**. Every example,
playbook, and script here is meant to be run live, in front of a class, on
a laptop with nothing but a browser.

**Made with Claude Code** — the first two examples (the Clubhouse,
Bubblegum Zap) were made with **Mercury**; every example from #3 onward
was made with **NeuralWatt**.

---

## 🎯 Why this repo exists

Software isn't born as code. It starts as a thought, becomes a plan, and
only then becomes code. We make all three visible:

- kids say **what they imagine**, in their own words
- the engineer turns that into a **real spec** (OpenSpec), asking targeted
  questions along the way — *reverse prompting*
- they see the whole journey: blueprint → design → tasks → build → ship

They leave having **made something real**, not just watched a demo.

## 🚀 Run the examples

```bash
# option A — just open them
open index.html        # macOS — Example #1, the Clubhouse
open bubblegum.html    # Example #2, Bubblegum Zap (the game)
open study.html        # Example #3, Study Quest (the study arcade)
open art.html          # Example #4, Art Arcade (pixel studio)
open dress.html        # Example #5, Dress Studio (the fashion arcade)
open time.html         # Example #6, Time Monster (the friendly day-tracker)
open typing.html       # Example #7, Typing Rockets (the typing time-trial)
open maze.html         # Example #8, Maze Maker (the maze workshop)
open pet.html          # Example #9, Pet Hatchery (the pet training game)
open chalk.html        # Example #10, Chalk Rush (the chalkboard RTS)
open neon.html         # Example #11, Neon Delivery (the retro-neon runner)
open snow.html         # Example #12, Powder Tricks (the cartoon snowboard trick game)
open chase.html        # Example #13, Cop Chase (the neon-pixel getaway racer)
open train.html        # Example #14, Harvest Haunt (the autumn ghost-train shooter)
open hoops.html        # Example #15, Street Hoops (the blacktop streetball arcade)
open football.html     # Example #16, Gridiron Rush (the retro football arcade)
open backyard.html     # Example #17, Backyard Bastion (the golden-hour siege game)
open beats.html        # Example #18, Beat Booth (the CRT-synth rhythm game)
open candy.html        # Example #19, Candy Beat (the candy-80s rhythm auto-runner)
open sunstone.html     # Example #20, Sunstone Vale (the stained-glass adventure)
xdg-open index.html    # Linux same files

# option B — serve everything
python3 -m http.server 8123
# then visit http://localhost:8123/ (clubhouse),
#         http://localhost:8123/bubblegum.html (game),
#         http://localhost:8123/study.html (study arcade),
#         http://localhost:8123/art.html (pixel studio), and
#         http://localhost:8123/dress.html (fashion arcade), and
#         http://localhost:8123/time.html (friendly day-tracker), and
#         http://localhost:8123/typing.html (typing time-trial), and
#         http://localhost:8123/maze.html (maze workshop), and
#         http://localhost:8123/pet.html (pet training game), and
#         http://localhost:8123/chalk.html (chalkboard RTS), and
#         http://localhost:8123/neon.html (retro-neon runner), and
#         http://localhost:8123/snow.html (cartoon snowboard tricks), and
#         http://localhost:8123/chase.html (neon-pixel cop chase), and
#         http://localhost:8123/train.html (autumn ghost-train shooter), and
#         http://localhost:8123/hoops.html (blacktop streetball arcade), and
#         http://localhost:8123/football.html (retro football arcade), and
#         http://localhost:8123/backyard.html (golden-hour siege game), and
#         http://localhost:8123/beats.html (CRT-synth rhythm game), and
#         http://localhost:8123/candy.html (candy-80s rhythm auto-runner), and
#         http://localhost:8123/sunstone.html (stained-glass adventure)
```

Everything is local-only, invented data, no accounts, no installs.

## 📦 What's inside

| Path | What it is |
|---|---|
| `index.html` | **Example #1 — the Clubhouse**: a hand-built app with living canvas, live console, events, members, board, bookings |
| `bubblegum.html` | **Example #2 — Bubblegum Zap**: the arcade game — retro chiptune, aim-assist laser/missiles, random gum objects, escalating 1-minute rounds |
| `study.html` | **Example #3 — Study Quest**: the retro study arcade — flashcard decks by subject (Math, Vocab, History), flip/mark drilling, missed cards come back until the deck is clear |
| `art.html` | **Example #4 — Art Arcade**: the retro pixel studio — paint/erase/fill/undo on a chunky grid, a gallery wall of saved drawings, and PNG export to take art home |
| `dress.html` | **Example #5 — Dress Studio**: the retro fashion arcade — dress a paper-doll model from a mix-and-match closet (tops, dresses, shoes, hats, bags, jewelry), save looks to a lookbook, export PNGs |
| `time.html` | **Example #6 — Time Monster**: the friendly day-tracker — a cute monster grows with your screen time and wears colorful fur patches for the apps you used, with a happiness meter and kind 1–3 star days |
| `typing.html` | **Example #7 — Typing Rockets**: the retro-neon typing time-trial — type space/school/silly fuel words to fly a rocket to the finish line, beat the clock on three tracks, and chase new best times |
| `maze.html` | **Example #8 — Maze Maker**: the neon build-and-solve maze workshop — paint glowing walls, hide treasures, then steer a light-cycle ball to the goal with arrows or clicks and chase best runs per maze |
| `pet.html` | **Example #9 — Pet Hatchery**: the storybook pixel pet game — hatch an egg, train a wiggly pet with tap-timing and memory tricks, then star in a talent show scored with hand-drawn stars |
| `chalk.html` | **Example #10 — Chalk Rush**: the chalkboard real-time strategy game — hire workers for energy, hatch auto-battling chalk soldiers, pull the big RUSH lever, and smash the rival general's castle |
| `neon.html` | **Example #11 — Neon Delivery**: the retro-neon delivery runner — auto-run up a synthwave highway, steer through glowing traffic, and keep the wobbly pizza on the box until the customer |
| `snow.html` | **Example #12 — Powder Tricks**: the cartoon snowboard trick game — carve between the lanes, pop off candy ramps, stack grabs and flips in the air, and stick clean landings before three tumbles end the run |
| `chase.html` | **Example #13 — Cop Chase**: the retro-neon arcade cop chase — gas and brake set your speed, weave through pixel traffic, hit checkpoint gates for more time, and brake hard to make the cops overshoot before they box you in |
| `train.html` | **Example #14 — Harvest Haunt**: the autumn ghost-train rail shooter — the train rolls through golden corn rows while frights pop out to spook you, pan along the cars and splat them before they duck away, and chain hits into combo glory before the barn |
| `hoops.html` | **Example #15 — Street Hoops**: the blacktop streetball arcade — drive the ball handler around the sunset court, shake the defender for the open look, fire from deep for three, and sink free-throw streaks before the buzzer |
| `football.html` | **Example #16 — Gridiron Rush**: the retro football arcade — call the play and hike the ball, steer the run or fire to your streaking receivers, juke past tacklers, and make the tackle on defense before the final whistle |
| `backyard.html` | **Example #17 — Backyard Bastion**: the golden-hour siege game — build spike traps, pebble turrets, and stick walls around your fort, zap waves of bugs as a tiny hero, and rescue friendly bugs to fight beside you before the fort falls |
| `beats.html` | **Example #18 — Beat Booth**: the CRT-synth rhythm game — you're the DJ at the neon club, notes rush four glowing lanes to the hit line, strike D F J K on the beat to feed the streak, and keep the crowd roaring until the set drops |
| `candy.html` | **Example #19 — Candy Beat**: the candy-80s rhythm auto-runner — tap to jump your hero through a pixel arcade-cabinet world, grab the pop-up beat-orbs, and land every tap on the beat before the dance-floor crowd walks out |
| `sunstone.html` | **Example #20 — Sunstone Vale**: the stained-glass adventure — walk the golden-hour kingdom, sword the monsters, crack the chest for the key, unlock the ruin's golden door, and claim the Sunstone before the light fades |
| `docs/reverse-prompt-guide.md` | **The playbook** — how students reverse-prompt with OpenSpec, with examples and drills |
| `docs/runbook.md` | The 10-minute demo session script for the teacher/host (with troubleshooting) |
| `docs/event-card.md` | A printable one-page journey card for the booth |
| `LICENSE` | BSD 3-Clause — free to reuse, share, and remix |
| `.claude/CLAUDE.md` | The exact contract that keeps Claude in **student-driver mode** |
| `openspec/` | Real OpenSpec artifacts — both examples were built as archived changes, so the specs show the full journey end-to-end |

## 🎓 The 7-phase journey

| # | OpenSpec phase | Student-friendly name | Artifact you see |
|---|---|---|---|
| 1 | `new change` | 🧠 Brainstorm | a folder is born |
| 2 | proposal + spec | 📐 Blueprint | the contract of what we'll build |
| 3 | design | 🧱 Floor plan | how we'll build it |
| 4 | tasks | ✅ To-do | the checklist |
| 5 | validate | 🕵️ Check | green checks |
| 6 | apply / build | 🔨 Build | the app comes alive |
| 7 | archive | 🚀 Ship | the final spec is saved forever |

## 📜 Built with the full OpenSpec loop

Every feature here went through the whole student-driver journey — brainstorm →
blueprint → floor plan → to-do → check → build → ship — and each change was
archived into its spec:

- `openspec/specs/clubhouse/spec.md` — the clubhouse (Example #1)
- `openspec/specs/bubblegum-zap/spec.md` — the game, including the tuning,
  weapons, and retro-music changes (Example #2)
- `openspec/specs/study-app/spec.md` — the study arcade (Example #3)
- `openspec/specs/art-studio/spec.md` — the pixel studio (Example #4)
- `openspec/specs/dress-studio/spec.md` — the fashion studio (Example #5)
- `openspec/specs/time-monster/spec.md` — the friendly time monster (Example #6)
- `openspec/specs/typing-rockets/spec.md` — the typing time-trial (Example #7)
- `openspec/specs/maze-maker/spec.md` — the neon maze workshop (Example #8)
- `openspec/specs/pet-hatchery/spec.md` — the storybook pet game (Example #9)
- `openspec/specs/chalk-rush/spec.md` — the chalkboard RTS (Example #10)
- `openspec/specs/neon-delivery/spec.md` — the retro-neon delivery runner (Example #11)
- `openspec/specs/powder-tricks/spec.md` — the cartoon snowboard trick game (Example #12)
- `openspec/specs/cop-chase/spec.md` — the neon-pixel getaway racer (Example #13)
- `openspec/specs/ghost-train/spec.md` — the autumn ghost-train rail shooter (Example #14)
- `openspec/specs/street-hoops/spec.md` — the blacktop streetball arcade (Example #15)
- `openspec/specs/gridiron-rush/spec.md` — the retro football arcade (Example #16)
- `openspec/specs/backyard-bastion/spec.md` — the golden-hour siege game (Example #17)
- `openspec/specs/beat-booth/spec.md` — the CRT-synth rhythm game (Example #18)
- `openspec/specs/candy-beat/spec.md` — the candy-80s rhythm auto-runner (Example #19)
- `openspec/specs/sunstone-vale/spec.md` — the stained-glass adventure (Example #20)

`openspec/changes/archive/` holds the complete history of every change.

## 🤝 How reverse prompting works

**You say what you want in your own words. The tool asks you targeted
questions, turns your answers into a real spec, and only then writes code —
stopping at every step to confirm with you.**

You're the boss. The engineer does the typing. Read the full playbook in
`docs/reverse-prompt-guide.md`.

---

## 🛠️ Made with

| What | Name | Role |
|---|---|---|
| Model | **Mercury 3** | the AI model driving the building |
| App | **Claude Code** | the tool where the model does the work |
| Platform | **[Inception Labs](https://platform.inceptionlabs.ai/)** | where Mercury 3 runs |
| Method | **OpenSpec** | spec-driven delivery (student-driver mode) |

This whole project was **driven by [Mercury 3](https://platform.inceptionlabs.ai/)
running in Claude Code**, with the student as product owner.

---

_EPIC-MN · epic-mn.com · all data invented · made for students, by people
who love making things._
