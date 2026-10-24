---
name: boy-scout
description: Simplify current uncommitted changes with a deletion-first cleanup that usually reduces code while preserving behavior. Use when explicitly asked for boy-scout cleanup.
disable-model-invocation: true
---

# Boy Scout

Leave less code to maintain. Most runs should remove more lines than they add, while preserving intended behavior and readability. A useful cleanup can also make no changes.

## Scope

Start from current staged, unstaged, and relevant untracked changes (or task-changed files when Git is unavailable). Inspect direct callers, callees, tests, and documentation only as needed to understand and simplify those changes. If there are no changes, report no target; do not search the repo for work. Preserve unrelated user work.

## Simplify

- Prefer deleting dead code, redundant branches, unnecessary wrappers, and obsolete comments; consolidate duplication when it actually makes the code simpler.
- Question abstractions and special cases introduced by the current changes. Prefer existing utilities and straightforward code over new helpers, layers, configuration, or dependencies.
- Keep cleanup behavior-preserving. Do not add features, speculative safeguards, or redesigns. If simplification requires a behavior change, leave it out and explain why.
- Reduce complexity, not just line count: do not compress readable code, remove useful documentation, or weaken tests to meet a deletion target.
- Reuse existing tests. Add coverage only for a concrete risk introduced by the cleanup; if safe cleanup needs disproportionate scaffolding, choose a smaller change.
- Stop when the worthwhile simplifications are done. If the cleanup adds more code than it removes, reconsider it and retain the additions only with a concrete justification.

## Verify

Run relevant tests or checks and inspect the final diff for behavior changes and unrelated churn. Briefly report what became simpler, what was verified, and the cleanup's own added/deleted line counts relative to the starting state, separate from pre-existing changes. Explain any net increase or verification gap.
