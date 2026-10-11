---
name: assumption-challenge
description: List and challenge the hidden assumptions inside a problem. Combines four prompts (Assumption Lister, Outsider Consultant, Frame Borrower, Assumption Breaker) with human checkpoints - cross out facts and goals, keep up to three assumptions, pick one with two tests, rewrite the question, and check with a three-row table that the rewrite is really new. Use when someone says "what does this question assume", "is this the wrong question", "challenge the assumptions".
---

# assumption-challenge

**One line:** the AI lists, the human crosses out, picks one and rewrites, then we check the rewrite is really new.

**Built from 4 prompts:** `prompts/01` `02` `03` `04`.

## Steps

### 1 · Write the old question (human)

Start with "How can we…", in the words people in that place use when they complain. Also note 3–5 facts about the place (numbers, times, rules, money). Every later test must quote one of them.
**Checkpoint:** if the question already names a product or feature ("How can we build an app to…"), remove it and rewrite.
*Autopilot:* if the user gave no facts, write 3–5 plausible ones and mark them `[AI judged]`.

### 2 · List 8 assumptions (AI) — fresh agent

Run `prompts/01-assumption-lister.md`.
**Checkpoint:** 8 lines, each starts with "It assumes", no solutions, no ranking.

### 3 · What looks strange to an outsider (AI) — fresh agent

Run `prompts/02-outsider-consultant.md`.
**Checkpoint:** all three lines are about the question itself ("Why Wednesday?"), not about how to fix it. If one points at a belief not on the list, add it as another "It assumes".

### 4 · Borrow three frames (AI) — fresh agent

Run `prompts/03-frame-borrower.md`.
**Checkpoint:** each frame names a different real problem. If all three just restate the question with new nouns, skip this step.

Steps 2–4 do not depend on each other. Run them at the same time if you can.

### 5 · Cross out what is not an assumption (human)

Sort every line from steps 2–4 into **fact**, **goal**, **the question said again**, or **hidden assumption**. Keep at most 3.
**Checkpoint:** each crossed-out line has a two-word reason ("7: goal"). Each kept line completes:
`The problem assumes [a belief]. I can see this in [words of the problem or what people do]. It could be otherwise, because [another possible version].`
If the last part cannot be filled, it is a fact or a goal: cross it out.

### 6 · Pick one with two tests (human; AI may give a lead)

- **Test 1:** pretend it is false. What is the first thing you would actually do on Monday?
- **Test 2:** pretend you broke it and it was true after all. What do you lose?

For a lead, run `prompts/04-assumption-breaker.md`. The human still chooses.
**Checkpoint:** both tests quote a fact from step 1; the Monday action is a *different kind* of action, not more of the same; the loss is not only money.

### 7 · Rewrite and check with three rows (human)

Write a new question without that assumption. Go down the rows and stop at the first that fits:

| Row | Situation | Verdict |
|---|---|---|
| 1 | The assumption is still in the new question | Same question, new words |
| 2 | The assumption is gone, but the first action is the old one, only more or faster | Same question, new words |
| 3 | The first action changed kind | **Reframed** |

**Checkpoint:** you can say "My rewrite is row 3, because my first action changed from ___ to ___". On row 1 or 2, go back to step 6.
Example: tenants say the lift is slow. A faster motor is row 2. "Waiting is annoying" leads to a mirror beside the lift: row 3 (Wedell-Wedellsborg, 2017, HBR).

## Pull-back lines

| The AI drifts | Say |
|---|---|
| Gives solutions | `No solutions. Only the list.` |
| Ranks or picks for you | Ignore the ranking and run the two tests |

## Hands on

The row-3 question goes to `/jtbd` and `/triz`.
