---
name: finishing-a-branch
description: Use when implementation on a branch is complete and it is time to commit, open or update a pull request, or hand the work back for review. Runs the final checks, cleans the history and writes a PR description a reviewer can act on. Never merges or pushes to the main branch.
---

# Finishing a development branch

## 1. Final checks

Run, in this order, and stop at the first failure:

1. Formatter and linter.
2. Type checker / compiler.
3. Tests (the ones touched first, then the full suite, or the project's CI-equivalent command).
4. Secret scanning (for example gitleaks) through the project's pre-commit hooks.

Use the `verification-before-completion` skill for the report. Never bypass hooks (`--no-verify`) to get a commit through; fix the cause or report it.

## 2. Review your own diff

`git diff origin/main...HEAD`, read it as a reviewer would:

- debug output, commented-out code, stray TODOs, local paths;
- test credentials, test IDs or debug flags reachable in release builds;
- files that should not be there (build output, `.env`, IDE folders, large binaries);
- unrelated changes — move them to another branch.

## 3. Commits

- Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`, `test:`, `build:`), imperative mood, in the project's code language.
- One logical change per commit. Squash fix-ups of your own branch before review; do not rewrite history that others have pulled.
- Push only the feature branch. Pushing to `main`/`master`, force-pushing, or deleting remote branches requires the human's explicit approval.

## 4. Pull request description

```markdown
## What
One paragraph: the change and why.

## How it was verified
- <command> — <result>
- Manual checks, with screenshots for UI changes.

## Risk and rollout
Migrations, flags, config, backwards compatibility, how to roll back.

## Not done / follow-ups
- ...

Closes #<issue>
```

## 5. Hand-off

Tell the human: branch name, PR link (if opened), checks run, and anything that still needs a human (device testing, signing, production config). Do not merge; merging is the human's decision unless they delegated it explicitly.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
