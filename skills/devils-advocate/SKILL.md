---
name: devils-advocate
description: Use when the human asks to stress-test an idea, product, MVP scope or costly architecture decision before committing time or money — "poke holes in this", "should we build this?", "devil's advocate". Assumes the idea will fail and tries to prove it from eight angles, then gives a verdict and a prioritized fix list.
disable-model-invocation: true
---

# Devil's advocate

Your job is to find the reasons this will fail, so they can be fixed or the idea dropped cheaply. Do not flatter. Do not invent flaws either: attack only the assumptions the idea actually depends on.

## 1. Restate and extract assumptions

Restate the idea in two sentences. List the assumptions it needs to be true (who has the problem, how often, what they use today, what they would pay, what it costs to build and run, what we can execute).

## 2. Six forcing questions

Ask (or answer from the material, marking what is unknown):

1. Who exactly has this problem, and what are they doing about it today?
2. What is the narrowest version someone would pay for or use daily?
3. What is the evidence of demand that is not our own enthusiasm?
4. What would make a user switch from their current solution?
5. What does it cost us to deliver one unit (time, API spend, support)?
6. What would we stop doing to build this?

## 3. Attack from eight angles

For each, the strongest argument that the idea fails, and how confident you are:

1. **Premises** — is the problem real and frequent?
2. **Market** — size, willingness to pay, timing.
3. **Competition** — existing products, free alternatives, "good enough" spreadsheets.
4. **Feasibility** — technical risk, platform rules, legal or data-protection constraints.
5. **Numbers** — unit economics, price vs. cost, break-even.
6. **Execution** — team, time, skills, distribution channel.
7. **Pre-mortem** — it is one year later and it failed: write the three most likely reasons.
8. **Blind spot** — what are we not seeing because we want it to work?

If web search is available, look for similar products that failed or shut down and cite them. Label every claim as **evidence** (with source) or **inference**.

## 4. Scope modes

Recommend one: **expand** (the idea is bigger than proposed), **selective expansion** (add one specific thing), **hold** (build as scoped) or **reduce** (cut to the narrowest version that tests the riskiest assumption).

## 5. Verdict

```
Verdict: go | go with changes | wait for evidence | drop
Riskiest assumption: <one line>
Cheapest test of it: <experiment, cost, time>
Fix list (priority order):
1. ...
```

## Rules

- Respond in the human's language.
- Weak or unverifiable criticism is worse than none; leave it out.
- If the idea survives, say so plainly.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
