---
name: writing-adrs
description: Use when a technical decision is costly to reverse — choosing a database, framework, hosting, auth model, data model, integration style, or rejecting an option the team keeps revisiting. Writes a short Architecture Decision Record in docs/adr/ with context, options, decision and consequences.
---

# Writing ADRs

An ADR records **why** a decision was made, so that the next person (or agent) does not reopen it without new information, and does not follow it blindly after the context changed.

## When to write one

Write an ADR when at least one is true:

- reversing the decision later would take more than a few days of work;
- it constrains other teams, services or agents;
- there were real alternatives and the choice was not obvious;
- the same question has been asked twice.

Do not write one for reversible, local choices (a variable name, a library helper).

## Where and how

- File: `docs/adr/NNNN-short-title.md`, numbered sequentially, never renumbered.
- Status: `proposed` → `accepted` (only the human approver changes it) → later `superseded by NNNN` or `deprecated`. Never edit the decision of an accepted ADR; write a new one that supersedes it.
- Language: follow the project's documentation language. Keep technical identifiers as they appear in code.

## Template

```markdown
# ADR-NNNN: <decision in a short sentence>

- **Status:** proposed
- **Date:** YYYY-MM-DD
- **Decides:** <approver> · **Drafted by:** <agent or person>

## Context
What problem forces a decision now, and which constraints matter (cost, team, deadlines, compliance, existing systems).

## Options considered
1. **<Option A>** — pros / cons
2. **<Option B>** — pros / cons
3. **Do nothing** — what happens if we do not decide

## Decision
The chosen option and the main reason, in two or three sentences.

## Consequences
- What becomes easier.
- What becomes harder or more expensive.
- What we must now do (follow-up tasks, monitoring, migrations).
- When to revisit this decision (a trigger, not just a date).
```

## Rules

- Keep it under one page. Link to longer analyses instead of pasting them.
- State the costs of the chosen option honestly; an ADR with only pros is a sales pitch.
- If a decision was made under time pressure or with missing information, say so in Context.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
