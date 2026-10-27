---
name: test-driven-development
description: Use when implementing a feature, fixing a bug or changing behavior in code that has (or should have) automated tests. Drives the work as red-green-refactor cycles at the module's public boundary. Not for spikes, throwaway prototypes or pure config changes.
---

# Test-driven development

Write the test that proves the behavior before writing the code that provides it. The test is the specification the next agent (or human) can trust.

## The cycle

1. **Red.** Write one test for the next smallest behavior. Run it and watch it fail for the *expected* reason (an assertion, not a compile error or a typo). A test you never saw fail proves nothing.
2. **Green.** Write the least code that makes it pass. No speculative branches, no "while I'm here".
3. **Refactor.** With the suite green, remove duplication and improve names. Run the suite again.
4. Repeat until the acceptance criteria are covered, then run the full suite once.

## Where to test

- Test through the **public boundary** that was agreed for the module (its API, use case, controller, view model), not its private helpers. Tests that mirror the implementation break on every refactor and protect nothing.
- One behavior per test. The test name states the behavior in domain language: `rejects_order_when_stock_is_insufficient`, not `test1`.
- Prefer real collaborators inside the module; replace only what is slow, nondeterministic or external (network, clock, payment provider). For databases, prefer a real engine in a container over mocks when the project already supports it.
- When acceptance criteria are written in EARS form (see the `ears-acceptance-criteria` skill), each criterion maps to at least one test.

## Rules

- Never change a test to make it pass unless the test itself was wrong; if so, say so explicitly in the summary.
- Never weaken an assertion, widen a timeout, add a retry or skip a test to get green. If you believe one of these is justified, stop and report it by name.
- A bug fix starts with a test that reproduces the bug and fails. It is fixed when that same test passes.
- Keep the suite fast. If a test needs more than a few seconds, it belongs to an integration tier, not the unit tier.

## Anti-patterns

- Writing all tests first, then all code (that is a test plan, not TDD).
- Asserting on mocks' call counts instead of on observable results.
- Snapshot tests used as a substitute for thinking about the expected output.
- Testing getters, framework wiring or generated code.
- One giant test that covers five behaviors and fails for any of them.

## Output

When you finish, report: the behaviors covered (one line each), the command used to run the tests, and its result.

## Known failures

_Record here, with a date, real mistakes agents made while using this skill, and the rule that prevents them. This section is the most valuable part of the skill._
