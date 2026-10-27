---
name: issue-triage
description: Use when sorting a backlog, a batch of new issues or bug reports, or an idea inbox — assigns each item a state, asks for missing information, and writes a self-contained brief for items that are ready for an agent to implement.
---

# Issue triage

Move every item to exactly one state, and make the "ready" ones executable by someone who has never seen the conversation.

## States

| State | Meaning | What you do |
|---|---|---|
| `needs-triage` | New, not reviewed | Read it, deduplicate, classify |
| `needs-info` | Cannot act without an answer | Ask the specific question(s); tag the person who can answer |
| `ready-for-agent` | Clear scope, acceptance criteria, low ambiguity | Write the agent brief below |
| `ready-for-human` | Needs judgment, design, credentials, production access or a business decision | Say what decision is needed |
| `wont-do` | Duplicate, out of scope, obsolete | Close with the reason and a link to the duplicate |

## Triage checks

- **Duplicate?** Search open and recently closed items with the key terms; link instead of reopening.
- **Reproducible?** For bugs: steps, expected vs. actual, version, environment. Missing → `needs-info`.
- **Size:** if it would take more than about a day, split it into items that each deliver something verifiable.
- **Risk:** touches auth, payments, personal data, migrations or infrastructure → never `ready-for-agent` without human review of the brief.

## Agent brief (for `ready-for-agent`)

```markdown
## Goal
One sentence: what changes for the user or the system.

## Context
Links to the spec, ADRs and relevant files (paths). What was already tried.

## Acceptance criteria
- When ..., the system shall ... (EARS form)

## Out of scope
- ...

## Verification
Command(s) that prove it is done.

## Constraints
Files or areas that must not change; approvals needed.
```

## Output

A table: item → new state → one-line reason, followed by the briefs and the questions asked.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
