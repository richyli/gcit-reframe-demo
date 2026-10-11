---
name: reframe
description: The skill set. Takes one question and runs the whole reframing workflow by chaining four skills - /assumption-challenge (list and break an assumption) → /jtbd (find the real job) → /hidden-assumption (six whys and a one-week test) → /triz (turn the strongest objection into a contradiction and an idea). Decides which stages to run, passes each stage's output to the next, and ends with one summary and a list of sentences a human must rewrite. Use for "/reframe", "reframe this problem", "is this the right question", "from problem to idea".
---

# reframe — one question in, a testable idea out

**This is a skill set.** It writes no prompts of its own. It decides the order, carries outputs from one skill to the next, and keeps the human sentences visible.

```
question → /assumption-challenge → /jtbd → /hidden-assumption → /triz → idea + one-week test
             prompts 01–04          05        06–07               08–11
```

## Stages

| Stage | Skill | Takes | Gives |
|---|---|---|---|
| 1 | `/assumption-challenge` | The question someone handed you | One assumption worth breaking + a row-3 question |
| 2 | `/jtbd` | 3–4 facts about the place | One real job + "The problem is not ___; it is ___" |
| 3 | `/hidden-assumption` | A place you know + its old problem | A three-part assumption sentence + How-might-we + one-week test |
| 4 | `/triz` | The reframed problem + a first idea | P-and-not-P + separation + ideas + who is worse off + test |

## Which stages to run

- **Someone else gave you the problem** (a boss, a client, a club president) → 1 → 2 → 4
- **The problem is in a place you have been in for years** → 3 → 4 (stage 1's list is a good warm-up)
- **You only want to know what people need** → 2 only
- **You already have a new question and an idea, and want it attacked** → 4 only
- **Not stated** → run all four: 1 → 2 → 3 → 4, with stage 3 using the place from stage 1

## How to run

1. Say in one line which stages you will run and why.
2. For each stage, invoke that skill (with the Skill tool if you have one, otherwise read `.claude/skills/<name>/SKILL.md`) and follow it step by step, in the mode set by `CLAUDE.md`.
3. Before each stage, print one line: `Stage N · /skill-name · input: …` so the hand-off is visible.
4. Hand-offs:
   - stage 1's row-3 question → stage 4's problem;
   - stage 2's job → the progress stage 3's How-might-we aims at;
   - stage 3's How-might-we (if run) replaces stage 1's question as stage 4's problem;
   - stage 4's first idea: in autopilot, take the most obvious idea a team in that place would try first, marked `[AI judged]`.
5. End with the summary below, then save the record (see `CLAUDE.md`).

## Summary to end with

```
Old question:        …
Assumption broken:   …
Reframed question:   …   (row 3 because first action changed from … to …)
Real job:            When …, I want to …, so I can …
Hidden assumption:   People here assume …
Contradiction:       [thing] must be P so that A, and not P so that B
Separation:          time / place / case / parts and whole, because …
Idea:                …
Who is worse off:    …
One-week test:       do …, with … people, count …; wrong if …

Rewrite these yourself:
- … [AI judged]
```

## When this workflow is the wrong tool

- **The question was right all along.** If stage 1 step 7 never gets past row 1 or 2, say so instead of forcing a row 3.
- **No place you can see.** With only an abstract issue ("climate change") every checkpoint lacks facts. Narrow it to one town, one campus, one service first.
- **In autopilot the lister and the judge are the same model.** Crossing out loses its point when the AI does it, because only a human knows which line is a fact in that place. Treat an autopilot run as a draft.
