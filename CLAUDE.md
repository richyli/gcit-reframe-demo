# House rules for this repo

This repo is a classroom demo: single **prompts** (`prompts/`) are combined into **skills** (`.claude/skills/`), and the skills are chained into one **skill set** (`/reframe`). Every skill follows these rules.

## Language

Reply in English. Keep the prompt sentences exactly as written in `prompts/`.

## Two modes

- **Autopilot (default).** The user gives one question and nothing else, or says "run it all", "don't stop". Run every step to the end without asking. Do the human steps too, but put `[AI judged]` after every sentence that should have been a human decision.
- **Coach mode.** The user says "coach me", "step by step" or "let me decide". Stop at every human step, show the checkpoint, and wait.

## Roles stay locked

When a step says "Run `prompts/NN-....md`", read that file, fill in the brackets from what is already known, and answer *as that role*, obeying its last line. The Lister only lists. The Outsider only asks. The Objector only objects. If you feel like giving a solution while in one of these roles, you are breaking the rule.

Where a step says **fresh agent**, and an Agent or Task tool is available, give the filled-in prompt to a subagent that sees only that prompt, not this conversation. This is the same as "one prompt, one new chat" in class: the role cannot agree with ideas it has never seen. With no such tool, answer inline.

## Checkpoints

Every step ends with a checkpoint. If it fails, go back one step instead of pushing through. If the same step fails three times, stop and say where it is stuck.

## Three sentences always belong to a human

The three-part hidden-assumption sentence, the P-and-not-P sentence, and the one-week test. In autopilot you may draft them, but mark them `[AI judged]` and list them at the end under **Rewrite these yourself**.

## Record

At the end of a full `/reframe` run, save `runs/YYYY-MM-DD-<short-name>.md` with each step's output, what was crossed out and why, and every `[AI judged]` sentence. Then commit that one file and push it to the current branch, so the record can be opened on GitHub. Do not change any other file.
