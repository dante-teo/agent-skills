---
name: boy-scout
description: Explicitly invoked workflow for improving current uncommitted code, its direct upstream and downstream call chain, and related tests and documentation. Apply proportional, verified refactoring without changing unrelated behavior, overwriting user work, or expanding into a redesign.
---

# Boy Scout

Leave current uncommitted code, its direct call chain, tests, and related documentation better than you found them. Keep every improvement proportional and verifiable.

## Establish the Scope

- Start with all current Git changes: staged, unstaged, and relevant untracked files. If the task creates new changes, include them as they enter the uncommitted diff.
- If Git metadata is unavailable, use files changed by the current task as the root. If there are no uncommitted or task-created changes, report that there is no target instead of scanning the repository for cleanup.
- Identify the symbols, behavior, and contracts affected by the root changes.
- Extend only as needed to direct callers and callees in the immediate upstream and downstream call chain.
- Include tests that cover affected behavior and comments or documentation made stale by the change.
- Preserve unrelated changes and hunks, including unrelated work in the same file. Never overwrite, revert, or restyle user work merely to satisfy this skill.

## Improve Proportionally

- Complete the requested behavior while preserving existing intent.
- Clarify names and control flow, remove duplication or dead code, correct stale comments, and make local formatting consistent when these changes reduce current friction.
- Permit moderate refactoring when it makes the change more correct, easier to test, or prevents the uncommitted work from adding avoidable complexity.
- Before structural, cross-file, or interface-level refactoring, add or confirm focused automated coverage where practical, then rerun the relevant tests.
- If adequate coverage cannot be added with reasonable effort, reduce the refactor scope and document the remaining risk or follow-up.
- Introduce an abstraction only when the current change reveals a stable concept, repeated responsibility, strategy boundary, adapter boundary, or pure domain-logic boundary.
- Adjust internal APIs with their direct callers when tests cover the behavior. Keep public APIs, persistence schemas, file formats, CLI flags, network protocols, configuration formats, and user-visible behavior compatible unless the user confirms a change.
- Do not turn cleanup into a broad redesign, style migration, dependency change, or unrelated modernization effort. Defer worthwhile out-of-scope work and mention it as a follow-up.

## Manage Tests

- Keep the suite small, high-signal, and proportional to product risk. A code change does not automatically require a new test.
- Prefer reusing or updating existing tests. Add a test when it protects meaningful behavior, an important contract, a realistic regression, or an uncovered edge case.
- Test observable behavior rather than implementation details.
- Use unit or integration tests for business rules and component boundaries. Reserve UI or end-to-end tests for critical user flows or presentation requirements.
- Use TDD when it clarifies non-trivial logic or reproduces a regression; do not apply it mechanically.
- Review affected tests for redundancy, obsolete scenarios, implementation-detail assertions, and duplication of stronger boundary coverage. Remove or consolidate tests only when their protection is clearly preserved; never delete a test merely because it is small or inconvenient.

## Prefer Functional Design When It Helps

- Prefer pure functions for domain logic when they make behavior easier to understand, test, and reuse.
- Prefer immutable data and explicit data flow through parameters and return values over shared mutable state.
- Prefer composition and small functions over inheritance-heavy designs. Use `map`, `filter`, and `reduce` when they improve clarity.
- Use classes, objects, mutation, stateful components, and imperative loops when they best fit the language, framework, performance needs, or existing codebase.
- Do not rewrite clear code merely to make it more functional. Apply functional refactoring only when it supports the scoped change and can be verified.

## Verify and Report

- Run the lightest focused tests or equivalent checks that meaningfully cover the requested behavior and cleanup.
- Inspect the final diff for accidental scope expansion and unrelated churn.
- Report the behavior completed, meaningful cleanup, test changes, verification performed, remaining risk, and anything that could not be verified.
