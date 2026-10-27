---
name: git-worktrees
description: Use when two or more agents (or an agent and a human) need to work on the same repository at the same time, or when starting isolated work on a feature branch without disturbing the current checkout. Creates, uses and cleans up git worktrees safely.
---

# Git worktrees for parallel work

A worktree is a second checkout of the same repository in another folder, on its own branch. Two agents in two worktrees cannot overwrite each other's files.

## Create

```bash
git fetch origin
git worktree add ../<repo>-<short-task> -b <type>/<short-task> origin/main
cd ../<repo>-<short-task>
```

- One worktree per task, one branch per worktree. Branch names follow the project convention (`feat/…`, `fix/…`, `chore/…`).
- Put worktrees next to the repo (or in a folder the project ignores), never inside the repo tree.
- Run the project's setup in the new worktree (dependency install, pre-commit hooks); hooks and local config files do not always carry over.
- Never copy `.env` files or credentials between worktrees from an agent session; the human sets them up if needed.

## Work

- Each agent stays inside its own worktree path. Do not edit files in another worktree.
- Commit often on the worktree's branch. Rebase on `origin/main` before opening the PR, not in the middle of the task.
- Two tasks that must change the same file at the same time are one task, or need an agreed contract first (for example, an API schema) so each side can work against it.

## Clean up

After the branch is merged or abandoned:

```bash
git worktree list
git worktree remove ../<repo>-<short-task>   # refuses if there are uncommitted changes
git branch -d <type>/<short-task>             # -d, not -D: refuses if unmerged
git worktree prune
```

Never use `--force` on `worktree remove` or `-D` on the branch without the human's approval: both discard work.

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
