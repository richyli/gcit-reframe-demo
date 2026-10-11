---
name: triz
description: Turn the strongest objection to an idea into a contradiction, then separate it with TRIZ instead of compromising. Combines four prompts (Strongest Objector, Contradiction Drafter, Four Separations, Principle Ideator) with human steps - write the P-and-not-P sentence, check the four separations against facts, pick one of eight service principles, and name who is worse off plus a one-week test. Use for "someone will object", "trade-off", "we want both", "TRIZ", "contradiction".
---

# triz

**One line:** an objection is a contradiction someone gives you for free. TRIZ does not accept a compromise; it looks for a split that gives both sides all of what they need.

**Built from 4 prompts:** `prompts/08` `09` `10` `11`.

## Steps

### 1 · Problem and first idea (human)

A reframed problem (from `/assumption-challenge`, `/hidden-assumption` or the user) plus a one-line first idea.

### 2 · The strongest objector (AI) — fresh agent

Run `prompts/08-strongest-objector.md`.
**Checkpoint:** the objection names who objects and gives a reason from this place (a number, a rule, someone's time or cost), not "too expensive"; A and B in the trade-off are two different things. If two problems are raised, pick one as B.

### 3 · P and not P (human — one of the three human sentences)

Find **the one thing that drives both A and B** and write:
`[The thing] must be [P], so that [A], and not [P], so that [B].`
For a draft to correct, run `prompts/09-contradiction-drafter.md`. The human rewrites it and says in one line what changed.
**Checkpoint:** both halves are about the **same thing, same property**. The thing is a resource or setting (a space, a time slot, a label, a note, a booking), **not a value** (money, fun) and **not a rule** ("the rule must be strict and not strict" sounds right but is wrong: the rule is not what fills the space or carries the message).
Example: the space at the building door must be full of bikes (so students get to class on time) and must be empty (so the fire exit is clear).

### 4 · Four separations (AI answers, human checks the facts)

Run `prompts/10-four-separations.md`.

| Separate by | Ask | Example |
|---|---|---|
| Time | When is it needed, when not? | Landing gear: down to land, up to fly |
| Place | Where is it needed, where not? | Diving pool: bubbles only where divers land |
| Case | In which case is it needed? | Colander: a wall to pasta, a hole to water |
| Parts and whole | Needed by the parts or the whole? | Bike chain: every link rigid, the chain flexible |

**Checkpoint:** at least one answer is yes, backed by a quoted fact. All four no → wrong thing, go back to step 3. If the only difference is "later", check that the need really flips at that moment and is not just pain moved to later.

### 5 · Principle and ideas (AI proposes, human picks)

Eight TRIZ principles that work best for services (from Altshuller's 40):

| Principle | In a service | Example |
|---|---|---|
| 1 Segmentation | Split customers or the service and treat each part differently | An insurer for military families only |
| 2 Taking out | Remove the troublesome part, or take the needed part to where people are | ATM, blood-donation bus |
| 10 Prior action | Do part of it in advance so the service starts at the easy end | Bill slipped under the hotel door the night before checkout |
| 13 The other way round | Bring the service to the customer | Home repair, ambulance |
| 21 Skipping | Make waiting shorter, or feel shorter | Mirror beside the lift, street performers in a queue |
| 22 Blessing in disguise | Use a mistake or complaint to change how people see you | Free drinks when a flight is delayed |
| 25 Self-service | Let customers do part of the work | Salad bar, flat-pack furniture |
| 26 Copying | Replace an expensive service with a cheap copy | Audio guide instead of a human guide |

Pick the principle that fits the separation, then run `prompts/11-principle-ideator.md`.
**Checkpoint (human):**
- Each side gets *all* of what it needs, not half ("one slot per person per week" is a compromise: go back to the separation that said yes).
- **Who is worse off** names a real person or group, never "nobody".
- A **one-week test** can be written (counts behaviour, the "wrong" result written first). If it cannot, the idea is too big.

## Pull-back lines

| The AI drifts | Say |
|---|---|
| Gives solutions | `No solutions. Only the objection.` |
| Vague objection | `Too expensive for whom, compared with what? Give one concrete reason.` |
| P and not P are two different things | Do not reply; rewrite it yourself and note what you changed |

## Not covered

The contradiction matrix and the 39 engineering parameters (they do not help with service problems). Sources: Altshuller (2005), Gadd (2011), Kim et al. (2012) service principles, Haines-Gadd (2016).
