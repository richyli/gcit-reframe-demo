---
name: jtbd
description: Find the job people are really hiring a product or routine to do (Jobs to Be Done). Combines one prompt (Job Lister) with three human checks that separate real jobs from features in disguise, then restates the problem as "The problem is not ___; it is ___." Use when someone asks "what do people actually need", "is this a job or a feature", "jobs to be done".
---

# jtbd

**One line:** people hire a product to make progress in a situation. The AI widens the list of jobs; the human checks each one.

**Built from 1 prompt:** `prompts/05`.

## Steps

### 1 · Describe the place (human)

Three or four facts: who is there, what they do, when, and what they use now.
**Checkpoint:** if a solution is already in the description ("How can we build an app…"), take it out. This step looks for the problem.

### 2 · List six jobs (AI) — fresh agent

Run `prompts/05-job-lister.md`.
**Checkpoint:** six "When…, I want to…, so I can…" sentences, each labelled functional, emotional or social, no features. Expect one or two to be features in disguise. Step 3 catches them.

### 3 · Three checks (human — the AI will defend its own sentences, so do not ask it)

For each job:
1. **Say it with no product in it.** Does it still make sense?
2. **Can you find a time and a place** for it?
3. **Can you name a rival outside the category?** (A milkshake competes with a bagel, a banana and a boring commute, not with another milkshake.)

Mark each J (job) or F (feature). Keep one J, ideally one that a "faster, cheaper" proposal would miss.
**Checkpoint:** at least one line is marked F with the check it failed; the job you keep still holds if the product disappears.

### 4 · Restate the problem (human)

`The problem is not ___; it is ___.` No app, feature or price in the second half.

## Watch out

Calling a feature a job ("I want one-click ordering"). Looking only at the functional side and missing the emotional and social ones. The "When… I want to… so I can…" form is the product-team *job story*, not Christensen's original wording; the three checks are a classroom test.

## Hands on

The job sentence is often the progress that `/hidden-assumption` step 4 aims at. The restated problem can also go straight to `/triz`.
