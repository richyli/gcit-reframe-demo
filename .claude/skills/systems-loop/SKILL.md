---
name: systems-loop
description: Systems thinking loop. Takes one social phenomenon and draws a full causal loop diagram with three intervention points on it. Fully automatic, no human steps: combines three prompts (Intervention Lister, Link Lister, Intervention Drafter) with AI-run checks - write the problem as people say it, sort what has been tried on the five-step ladder (numbers, rules, information, structure, goals), name one step up and who pushes back, list variables, check every link's sign against a fact, find two loops (R or B) and one delay, and choose three intervention points on three different steps. Ends with one Mermaid diagram. Use for "systems thinking", "causal loop", "draw the loop", "why does this problem keep coming back", "where should we intervene", "leverage points".
---

# systems-loop — one phenomenon in, a causal loop with three intervention points out

**One line:** a social problem that comes back after the fix was a symptom, not the problem. The AI runs every step itself, from the phenomenon to the diagram.

**No human steps.** This skill never stops to ask, has no coach mode, and does not use `[AI judged]` marks or a "Rewrite these yourself" list; it overrides the two modes in `CLAUDE.md`. Every checkpoint is still checked, by the AI, and a failed checkpoint still means going back one step.

**Built from 3 prompts:** `prompts/12`, `prompts/13`, `prompts/14` (optional). Source: Guide 4, steps 1–9.

```
phenomenon → 1 problem → 2 eight tries → 3 ladder → 4 one step up
           → 5 variables → 6 ten links → 7 signs vs facts → 8 two loops + delay
           → 9 three intervention points → diagram
```

| Step | Move | Who | You get |
|---|---|---|---|
| 1 | Problem as people say it | AI | one "How can we" sentence |
| 2 | Intervention lister | fresh agent, `prompts/12` | eight interventions, each labelled |
| 3 | Sort on the ladder | AI | each on a step, at least two labels corrected |
| 4 | One step up | AI | one line for the step above, and who pushes back |
| 5 | Variables | AI | five to eight nouns that go up or down |
| 6 | Link lister | fresh agent, `prompts/13` | ten links with signs |
| 7 | Check the signs | fresh agent (checker) | about five links, each with a fact |
| 8 | Loops and delay | AI | two loops marked R or B, one delay |
| 9 | Three intervention points | AI, with `prompts/14` per step | three points on three steps, the strongest named |
| 10 | Diagram | AI | one Mermaid causal loop diagram |

**The ladder** (weakest → strongest): **numbers** → **rules** → **information** (who can see what) → **structure** (who is connected to whom) → **goals** (what the whole system is for).

## Steps

### 1 · Write the problem the way people say it

Turn the phenomenon into one sentence, as the people who complain about it say it, starting with "How can we".
**Checkpoint:** the problem is the right size: a town, a campus, a street, a service. "Climate change" is too big; "the recycling truck comes when working people are not home" is right. If the sentence already contains a solution ("How can we build more shelters"), write it again without it. If the phenomenon is too big, narrow it to one place yourself and say which place in one line.

### 2 · List what has been tried — fresh agent

Run `prompts/12-intervention-lister.md` with the step 1 sentence.
**Checkpoint:** eight lines, at least three voices, each with a label at the end, no recommendation. If it recommended, reply *No solutions. Only the list.* and run again. Keep the labels; step 3 corrects them.

### 3 · Sort the eight on the ladder

Put each line on one of the five steps. Do not trust the lister's labels: it labels by how a proposal sounds, not by what it changes.
**Checkpoint:** every line has a step, and for at least two of them you wrote whether the lister's label was right or wrong, and why. The test for a doubtful line: say it without the money or the quantity; if nothing is left, it is a number. Count how many sit on the bottom two steps; most should.

### 4 · Name one step up and who pushes back

Find the highest step any of the eight reaches. Write one line for the step above it, and one line naming who would push back.
**Checkpoint:** the step up changes a different kind of thing, not a bigger amount of the same. You can name a person or an office that would object. If nobody would object, you have written a bigger number; try again.

### 5 · List the variables (before step 6, so the lister's adjectives can be caught)

Five to eight variables: nouns that can go up or down. Also write three or four facts about the problem for step 6.
**Checkpoint:** put "more" in front of each; it still makes sense. "Dogs on the street" passes; "people are irresponsible" does not. Each is something somebody could count at one moment.

### 6 · List the links — fresh agent

Run `prompts/13-link-lister.md` with the step 1 problem, the facts and the variables.
**Checkpoint:** ten lines in the `A → B, sign` form, no explanations, no solutions. If it explained, reply *No explanations. Only A → B and the sign.* If it added variables, check them with the "more" test (*Each variable must be a noun I could count. Rewrite them.*). Expect some signs to be guessed; that is what step 7 is for.

### 7 · Check every sign against a fact — fresh agent (checker)

The lister would defend its own arrows, so give the check to a new agent that sees only the problem, the step 5 facts and the ten links, with this instruction: *Next to each link, write the fact that gives it its sign, in a few words, or cross the link out and say why. Keep a link only if you can point to a fact. Do not add links and do not suggest solutions.*
**Checkpoint:** every kept link has a fact beside it: something seen, read or counted, in a few words. About half of the ten survive; ten survivors means you did not check. A sign is a direction, not a judgement. Never invent a number, a date or a source; a fact that cannot be pointed to is written as `(to check: …)`, and a link resting only on such a fact is crossed out.

### 8 · Find two loops and one delay

Follow the kept links back to where they start. For each loop write the variables in order, count the minus signs, mark **R** (even: feeds itself) or **B** (odd: corrects itself). Mark one delay with `‖` and a rough time.
**Checkpoint:** two loops, each written in order with its count. At least one is B, the system's thermostat; if you cannot find one, ask where the system pushes back (complaints, cost, space) and follow that arrow home, adding a link back in step 6–7 if needed. One arrow carries `‖` with a rough time. You can say which loop currently wins and point at a fact.

### 9 · Choose three intervention points on three steps

For each of three different ladder steps, write the **address** on the loop (the variable you push, the arrow you cut, the path you add) and one line on what it changes. Mark the strongest ★ and name who pushes back.
First pick the three steps (the top one at least as high as step 4's step up). Then, for each step, run `prompts/14-intervention-drafter.md` as a fresh agent with the loop and that step only. It drafts three; you choose one per step and pick the strongest.
**Checkpoint:** three steps, all different; three numbers is one point three times. Each point has an address on the loop, not a slogan. The strongest has a reason and a named opponent; "nobody" means you chose a number. Step 4's step-up line is a good candidate for one of the three.

### 10 · Draw the diagram (from the kept material only)

Draw one Mermaid `flowchart LR` from the **kept** links of step 7, the loops and delay of step 8, and the points of step 9. Nothing crossed out goes in. Use these conventions:

- each variable is a node `V1["Variable name"]`;
- each kept link is `A -->|"+"| B` or `A -->|"−"| B`;
- the delay arrow is dotted and carries its time: `A -.->|"− ‖ ~6 months"| B`;
- each loop gets a round label node, `R1(("R1 · feeds itself"))` or `B1(("B1 · corrects itself"))`, linked with `~~~` to one variable in that loop;
- each intervention point is a node `IP1[["IP1 · step · what it changes"]]` with class `ip`; the strongest also has class `strong`, a ★ and `pushback: …`;
  - **push a variable:** `IP1 -.-> V3`;
  - **cut an arrow:** `IP2 -.->|"cuts V2 → V4"| V4`;
  - **add a path:** draw the new link thick, `V5 ==>|"+ new path (IP3)"| V1`, and `IP3 -.-> V5`.

```mermaid
flowchart LR
  V1["Variable A"] -->|"+"| V2["Variable B"]
  V2 -->|"+"| V1
  V2 -->|"+"| V3["Variable C"]
  V3 -.->|"− ‖ ~6 months"| V1
  R1(("R1 · feeds itself")) ~~~ V1
  B1(("B1 · corrects itself")) ~~~ V3
  IP1[["IP1 · numbers · …"]]:::ip -.-> V2
  IP2[["★ IP2 · structure · …<br/>pushback: …"]]:::strong -.->|"cuts V2 → V3"| V3
  classDef ip fill:#fff4d6,stroke:#b8860b,color:#222
  classDef strong fill:#ffe0e0,stroke:#c0392b,stroke-width:2px,color:#222
```

**Checkpoint:** every arrow in the diagram is a kept link from step 7 (or a path added in step 9, drawn thick); both loops can be traced on it; the delay is visible; every intervention point touches the diagram at its address. If an IP points at nothing, go back to step 9.

## Output

Print each step briefly as it runs (`Step N · …`), then end with this, **diagram first**:

```
## Causal loop: <short name>

<the Mermaid diagram>

Problem:          How can we …
Ladder (step 3):  numbers n · rules n · information n · structure n · goals n   (AI labels corrected: …)
Step up (step 4): … — pushback: …
Loops (step 8):   R1: A → B → A (0 minus) · B1: A → C → A (1 minus); currently winning: … because …
Delay:            X → Y ‖ ~…
Intervention points (step 9):
  IP1 · <step> · <address> · changes …
  IP2 · <step> · <address> · changes …
  ★ IP3 · <step> · <address> · changes … · strongest because … · pushback: …
Crossed out (step 7): A → B (no fact) · …
Facts to check:       (to check: …) · …
```

Then save the record as `runs/YYYY-MM-DD-loop-<short-name>.md` (every step's output, what was crossed out and why, the facts to check, and the diagram), commit that one file and push it to the current branch, as `CLAUDE.md` asks for a full run.

## Watch out

- **Solutions too early.** Steps 2 and 6 forbid them; at any step, reply *No solutions. Only the list.* (or *the links*).
- **Adjectives as variables.** "Awareness is low" is not a variable; "people who know the pickup time" is.
- **Ten kept links.** That means nothing was checked.
- **Three numbers.** Three subsidies of different sizes are one intervention point three times.
- **The facts are only as good as what the model has read.** The step 7 checker runs fresh so it cannot defend the lister's arrows, but it is still a model, not someone who lives there. The "Facts to check" line says where to start.

## Hands on

The strongest point's pushback (step 9) is a ready-made objection for `/triz`. A loop that keeps winning although everyone hates it often hides an assumption for `/hidden-assumption`.
