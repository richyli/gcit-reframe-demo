---
name: hidden-assumption
description: Find an assumption you cannot see because you have been in a place too long. Combines two prompts (Six-Whys Outsider, Test Critic) with human steps - an outsider asks "why does it have to be that way" six times, one at a time, then quotes back every "this is just how it is"; the human writes a three-part assumption sentence, a How-might-we that survives without the belief, and a one-week test that could say no. Use for "six whys", "we have always done it this way", "hidden assumptions in my team".
---

# hidden-assumption

**One line:** an outsider's "why?" works because it refuses "this is just how it's done". Turning the answers into a belief you can check is the human's job.

**Built from 2 prompts:** `prompts/06` `07`.

## Steps

### 1 · Place, role, old problem (human)

One line: the place and your role. One sentence: the problem people there talk about ("How can we…").

### 2 · Six whys, one at a time (AI)

Run `prompts/06-six-whys-outsider.md`. Ask one question, wait for the answer, then ask the next. Each question picks up something just said. After the sixth answer, quote every "this is just how it is" sentence word for word.
*Autopilot:* there is no user to answer. Answer each question yourself as a plausible insider, using only facts already stated, and mark every answer `[AI judged]`. Say plainly that this step needs a real insider to be worth anything.
**Checkpoint:** compare the quoted list with the answers; add any "just how it is" that was missed, cross out lines that are really new ideas.

### 3 · The three-part sentence (human — one of the three human sentences)

`People here assume [a belief]. I can see it in [something people there actually do]. Nobody has checked it, because [why it feels too obvious to check].`
**Checkpoint:** the middle part points at *behaviour*: where money goes, what gets counted, who gets blamed. A feeling or complaint ("the boss is unreasonable") does not count.

### 4 · How might we (human)

Write a How-might-we that does **not** need that belief, and name one answer the old question ruled out but the new one allows.
**Checkpoint:** it still makes sense if the belief is false. If it already says how ("How might we use a Google Form…"), it is a solution: rewrite. A job from `/jtbd` often names the progress it should aim at.

### 5 · A one-week test (human — one of the three human sentences; the AI only critiques)

Smallest test you can run in a week: what you do, how many people, what you count, and **which result would show the new definition is wrong**. For critique, run `prompts/07-test-critic.md`.
**Checkpoint:** it counts behaviour (buy, sign up, show up, send a message), not intention ("would you want…?"); the "wrong" result is written before the test starts; any "no" from the critic gets fixed by the human, not rewritten by the AI.

## Pull-back lines

| The AI drifts | Say |
|---|---|
| Asks all six at once | `One question at a time. Wait for my answer.` |
| Starts giving advice | `Stop suggesting solutions. Only ask me why.` |

## Hands on

The How-might-we plus a first idea go to `/triz`.
