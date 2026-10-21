# Demo Session Runbook — The 10-Minute Ride

> Part of **EPIC-MN** (epic-mn.com) — getting students excited about AI in IT.

A script for the teacher or booth host. The student is the driver; you're
the narrator keeping the ride on the rails. Time totals ~10–12 minutes —
comfortable for a career fair rotation.

---

## 0. Before the student sits down (60 seconds)

- [ ] Open a terminal in this repo: `cd ~/epic-app01` (or wherever it lives).
- [ ] Run `openspec doctor` — expect `OpenSpec root: ok`.
- [ ] Run `openspec list` — expect the existing change history.
- [ ] Start a Claude session in this folder. The `.claude/CLAUDE.md`
      contract is now active: the AI stays in student-driver mode automatically.
- [ ] Have `index.html` open in a browser tab (double-click or serve it) as
      the "before" artifact — *we're going to make one of these from scratch.*

## 1. Hook (1 min)

> "We're going to build a real web app in the next ten minutes — and *you're*
> the boss. I'm the engineer. You describe the idea; I ask you questions,
> write the plan, show it to you, and only then build. That's called
> **reverse prompting**, and it's how real product teams work."

Ask the student the opening question (from the playbook):

> "What should our app do? One sentence, your words."

## 2. Brainstorm → Blueprint (2 min)

Let the AI run the phase. The student answers its clarifying questions
(one decision at a time). Don't help them answer — that's the point.

After the spec appears, the AI shows it and asks the review gate. **You,
the narrator, repeat it loudly:**

> "The blueprint is the contract. Does it match what you meant?"

- If **yes** → on.
- If **change** → "Say 'change X' — it updates the spec in seconds."

## 3. Floor plan → To-do → Check (2 min)

The AI writes the design, then tasks, then runs validation. Narrate:

> "Floor plan — how we build it. To-do — the checklist. Check — validation.
> Green means the plan is sound."

## 4. Build (3–4 min)

The AI implements task by task. Point at the screen as things happen:

> "Watch — every checkbox that fills in is a real step of building.
> This is what engineers do all day, just usually with more coffee."

When the app is up, hand the student the controls:

> "Now break it. Click things. Type a command in the playground.
> Breaking it is testing, and testing is part of the job."

## 5. Ship (1 min)

After the student tries it, prompt:

> "Want to ship it? Say 'ship it'."

The AI archives the change and shows the final merged spec. Narrate:

> "Done. The spec is saved forever, and you can prove every step.
> You just did the whole software career in ten minutes."

---

## Trouble-shooting (keep it moving)

| If… | Then… |
|---|---|
| Student says "I don't know" | "A guess you can change beats no answer. What's the first thing that comes to mind?" |
| Validation fails | "That's the check catching a hole in the plan — real teams hit this. We fix it in front of you, now." |
| Student wants something huge | "Great idea. We build the first piece now; the rest becomes 'later changes' — the engineer names them out loud." |
| Session interrupted | All work is saved in `openspec/changes/`. Resume anytime: open the folder, tell the AI "keep going". |
| No internet | Everything is local. The repo, the CLI, the app, this script — all work offline. |

## After the event

- The `docs/event-card.md` is the printable takeaway.
- Students can clone or download the repo and redo the ride with their own
  idea — same contract, same seven phases.
