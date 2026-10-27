---
name: ears-acceptance-criteria
description: Use when writing or reviewing user stories, specs or task lists — turns vague requirements into testable acceptance criteria in EARS form ("When X, the system shall Y") and gives every task a verification command. Use before planning or implementing a feature.
---

# EARS acceptance criteria

EARS (Easy Approach to Requirements Syntax) forces each requirement into a shape a tester can turn into a test without asking the author what they meant.

## The five patterns

| Pattern | Template | Example |
|---|---|---|
| Ubiquitous | The `<system>` shall `<response>`. | The API shall return amounts in minor units. |
| Event-driven | **When** `<trigger>`, the `<system>` shall `<response>`. | When a payment webhook arrives with an invalid signature, the API shall reject it with 401 and not change the order. |
| State-driven | **While** `<state>`, the `<system>` shall `<response>`. | While the user is in the free trial, the app shall show the trial days left on the home screen. |
| Unwanted behavior | **If** `<condition>`, **then** the `<system>` shall `<response>`. | If the stock service does not answer within 2 s, then the checkout shall show "try again" and keep the cart. |
| Optional feature | **Where** `<feature is included>`, the `<system>` shall `<response>`. | Where the store has multi-branch enabled, the report shall group sales by branch. |

Patterns can combine: *While offline, when the user saves a widget, the app shall queue the change and sync it on reconnect.*

## Rules for each criterion

- One trigger and one observable response. Split anything with "and also".
- Observable means a tester can see it: a status code, a stored value, a message, an event. "Handles errors gracefully" is not observable.
- Use concrete numbers for limits (time, size, count) and the glossary's terms for domain concepts.
- Cover the unhappy paths: invalid input, missing permission, dependency down, duplicate request, concurrent edit.
- Mark anything you had to assume with `[NEEDS CLARIFICATION: question]`. Do not invent the answer.

## Tasks get a verification command

When the criteria are broken into tasks, every task states the command that proves it is done, for example `./gradlew test --tests "*CheckoutTimeoutTest"` or `npm run e2e -- checkout.spec.ts`. The implementing agent runs it before opening a PR.

## Gate

The spec is not ready for planning while it contains `[NEEDS CLARIFICATION]` markers. Resolve them with the human (see `grill-the-plan`) or record that the human accepted the risk.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
