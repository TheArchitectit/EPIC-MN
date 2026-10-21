# Reverse Prompting with OpenSpec — Student Playbook

> You are the **product owner**. The AI is your **engineer**.
> You describe what you imagine. The engineer asks smart questions, writes
> the plan, shows it to you, and only then builds — stopping for your
> approval at every milestone. That loop is called **reverse prompting**,
> and it's exactly how real product teams work.

---

## 1. Why this matters

Software isn't born as code. It starts as a *thought*, becomes a *plan*, and
only then becomes code. Most people never see the middle part — the plan.

OpenSpec makes the plan **visible and real**:

- a **spec** is the contract for what you'll build
- a **design** is the floor plan
- **tasks** are the to-do list
- **validation** checks the plan is sound
- **archive** saves the finished story forever

When you reverse-prompt, you don't just get an app — you get the whole
journey, documented, that you can point at and say *"I made that."*

---

## 2. The loop

```
You (idea)  →  Engineer (clarifying questions)  →  You (answers)
     →  Engineer (proposal + spec)  →  You (review: "yes / change X")
     →  Engineer (design + tasks)  →  You (review again)
     →  Engineer (build, step by step)  →  You (test it)
     →  Engineer (validate + archive)  →  You (ship it 🚀)
```

Two review gates are non-negotiable:

1. after the **spec** — *"does this match what you meant?"*
2. after the **design** — *"is this how we should build it?"*

---

## 3. Starter phrases

Any of these can open a session:

- "I want an app that helps me ______."
- "Make a website for ______ that feels ______."
- "Build a tool for my club that can ______."
- "I have an idea: ______. Ask me questions to make it real."
- "Let's make something that looks amazing and does ______."

Then: **let the engineer ask**. Answer like you're explaining it to a friend.

---

## 4. Mini transcript (what it sounds like)

> **Student:** I want an app for our rock-climbing club. It should feel
> super cool and futuristic.
>
> **Engineer:** Nice — two questions: who uses it, and what's the one thing
> it must do first?
>
> **Student:** Members use it, and they must be able to see when the next
> climb night is.
>
> **Engineer:** Perfect. I'll write that as a spec — a contract that says
> exactly that. Here it is… does it match what you meant?
>
> **Student:** Yes. Add a countdown too.
>
> **Engineer:** Done — added to the spec. I'll plan the build now. …

## 5. Rules of thumb

| Do | Don't |
|---|---|
| Describe the *feeling* and the *purpose* | Don't say "use React and a database" — that's the engineer's job |
| Answer when asked; say "I don't know" freely | Don't let silence stall the loop — a guess you can change beats no answer |
| React to artifacts: "yes" or "change X" | Don't jump to "build it now" before the review gate |
| Try to break what gets built — that's testing | Don't worry about breaking things; that's how you learn |

---

## 6. Classroom drills (10–20 min each)

**Drill A — Two roles.** Pairs: one *owner*, one *engineer*. Owner says one
phrase from section 3. Engineer must ask 3 clarifying questions before
writing anything. Swap roles.

**Drill B — The ghost script.** Students watch a live build. Before each
phase, they predict what artifact comes next ("What do you think the
engineer shows us after the brainstorm?"). A correct guess = they've learned
the loop.

**Drill C — Change one thing.** After a build, the owner says one small
change ("make the background purple"). Watch the loop restart: spec update →
review → rebuild. It shows software is *iterative*, never one-shot.

---

## 7. Glossary (tiny)

- **Prompt** — what you tell the AI.
- **Reverse prompt** — the AI asking *you* questions to sharpen the idea.
- **Spec** — the contract: what the software MUST do.
- **Scenario** — a specific "when X happens, then Y" test.
- **Delta** — the part of the spec that changed.
- **Validate** — checking the plan is complete and consistent.
- **Archive** — closing the change and saving its spec into the project.
- **Change** — one cohesive chunk of work, with its own folder.

---

## 8. After the event

Build your own thing. The repo you saw has the full history of how it was
made. Open it, read it, and on your next session, ask for the same
seven-phase ride. That's the whole career, in miniature.
