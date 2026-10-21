# 🔷 EPIC-MN — AI in IT, built by hand

**Mission: get students excited about AI in IT.** Everything in this repo is
hand-built — zero frameworks, zero plugins, zero internet calls — and
designed so a **student drives** the building process, with the engineer
(Claude) executing and narrating every step.

This is the public showcase for **https://epic-mn.com/**. Every example,
playbook, and script here is meant to be run live, in front of a class, on
a laptop with nothing but a browser.

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
xdg-open index.html    # Linux same files

# option B — serve everything
python3 -m http.server 8123
# then visit http://localhost:8123/ (clubhouse) and
#         http://localhost:8123/bubblegum.html (game)
```

Everything is local-only, invented data, no accounts, no installs.

## 📦 What's inside

| Path | What it is |
|---|---|
| `index.html` | **Example #1 — the Clubhouse**: a hand-built app with living canvas, live console, events, members, board, bookings |
| `bubblegum.html` | **Example #2 — Bubblegum Zap**: the arcade game — retro chiptune, aim-assist laser/missiles, random gum objects, escalating 1-minute rounds |
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
