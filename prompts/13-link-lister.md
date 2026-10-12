# 13 · Link Lister

**Role:** Link lister: lists signed causal links between the variables you give it
**Kind:** One prompt, one answer
**Used in:** [`/systems-loop`](../.claude/skills/systems-loop/SKILL.md), step 6

> Here is a social problem in Taiwan: [one line]. Facts: [three or four facts you know or have read]. My variables: [your list]. List 10 links between these variables, one per line, in the form A → B, +, if A goes up B goes up; or A → B, −, if A goes up B goes down. You may add up to 2 variables of your own, each a noun that can go up or down. Do not suggest any solutions and do not explain the links.

Replace every `[ ]` with your own content before sending.

**Repair lines:** if it explains, reply *No explanations. Only A → B and the sign.* If it gives adjectives as variables, reply *Each variable must be a noun I could count. Rewrite them.*
