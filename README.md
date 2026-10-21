# ⚡ Zigzag Clubhouse — Hand-Built + The Reverse-Prompting Playbook

A tiny, flashy website **built entirely by hand** — zero frameworks, zero
plugins, zero internet calls — plus a complete student-facing playbook for
learning **reverse prompting** with **OpenSpec**.

Built for the Firhaven Career Fair: the idea is that a **student drives** —
they own the idea, I'm the engineer — and every step of making software is
visible, narrated, and documented.

---

## 🚀 Run it

The app is one file. Double-click it, or serve it:

```bash
# option A — just open it
open index.html        # macOS
xdg-open index.html    # Linux
# option B — serve it
python3 -m http.server 8123
# then visit http://localhost:8123
```

Everything is local-only, invented data, no accounts, no installs.

## 📦 What's inside

| Path | What it is |
|---|---|
| `index.html` | The hand-built clubhouse app (canvas particles, live console, events, members, board, bookings) |
| `docs/reverse-prompt-guide.md` | **The playbook** — how students reverse-prompt with OpenSpec, with examples and drills |
| `docs/runbook.md` | The 10-minute demo session script for the teacher/host (with troubleshooting) |
| `docs/event-card.md` | A printable one-page journey card for the booth |
| `LICENSE` | BSD 3-Clause — free to reuse, share, and remix |
| `.claude/CLAUDE.md` | The exact contract that keeps Claude in **student-driver mode** |
| `openspec/` | Real OpenSpec artifacts from building this app — proof the workflow works end-to-end |

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

## 🤝 How reverse prompting works

**You say what you want in your own words. The tool asks you targeted
questions, turns your answers into a real spec, and only then writes code —
stopping at every step to confirm with you.**

You're the boss. The engineer does the typing. Read the full playbook in
`docs/reverse-prompt-guide.md`.

---

_Built with Claude Code · all data invented · made for students, by people
who love making things._
