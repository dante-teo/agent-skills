---
name: reshape
description: Rework current uncommitted changes into one coherent implementation after iterative patches, preserving the intended final behavior. Use only when explicitly asked to apply reshape.
disable-model-invocation: true
---

# Reshape

Make the pending work read as though it was designed for the final requirements from the start. Treat the existing implementation as evidence of intent, not a structure that must survive. Perform the rework, rather than stopping at a review or a list of suggestions.

## Understand the whole change

- Inventory staged, unstaged, and untracked changes. Read the complete diffs and relevant new files, then the surrounding implementation, direct callers, tests, and documentation needed to understand them. Account for deletions and renames; do not inspect only the last patch or only the unstaged diff. Do not execute unknown untracked files or dump secrets while inspecting them.
- Establish the intended final behavior from the user's latest requirements, accepted corrections, tests, and current code. Earlier approaches may have been superseded. Preserve useful edge-case handling introduced during iteration; awkward code is not evidence that its behavior is unnecessary. Ask only if a material conflict cannot be resolved from context.
- Identify which changes belong to the same feature or fix. Read all pending changes to establish scope, but preserve unrelated user work and keep independent changes independent. If there is no pending work, report that there is nothing to reshape rather than searching for a new task.
- Record enough of the starting state to distinguish your rework from pre-existing edits and retain any staged/unstaged distinction. Do not reset, discard, stage, or commit the user's work as part of reshaping.

## Rebuild a coherent implementation

Before editing, form a concise design for how the final behavior should fit the existing codebase. Briefly explain the main structural change, then carry it out without waiting for approval of routine implementation choices.

- Reconsider the complete affected flow: responsibilities, data representation, state ownership, control flow, interfaces, naming, and error handling. Consolidate successive patches into a direct expression of the final requirements.
- Replace awkward structure when it improves the whole implementation. Remove superseded paths, duplicated logic, compensating workarounds, and abstractions that only exist to support abandoned approaches. Do not merely add another helper or conditional around the same underlying problem.
- Choose the simplest design that fits the requirements and repository conventions. Reuse established utilities and suitable maintained dependencies where they fit; avoid speculative frameworks, generic extension points, or new dependencies without a concrete benefit.
- Preserve intended observable behavior and explicit user choices, including compatibility and data contracts. Reshaping authorizes internal redesign, not new features or silently dropping accepted requirements. Correct a demonstrated defect when the intended behavior is clear and verify that correction.
- Follow the affected behavior across files when necessary; the current diff is the starting scope, not a restriction to its exact lines. Keep changes outside that scope limited to what the coherent implementation requires. Do not turn this into a repository-wide rewrite or unrelated formatting pass.
- Rewrite as much as the design warrants, but retain code that already fits. Optimize for clarity, consistency, and maintainability rather than deletion counts, wholesale replacement, or clever compression. A coherent implementation may be larger, smaller, or already good enough.
- Align affected tests and documentation with the final design. Preserve behavioral coverage and add regression coverage for concrete risks; do not weaken assertions merely to make the rewrite pass.

## Verify the result as a whole

Run the relevant tests and repository checks for the affected behavior. Review the complete resulting diff against the intended final requirements, not just your latest edits. Check that the implementation has one consistent approach, obsolete paths are gone, accepted edge cases still work, and unrelated work remains intact. Stop when the design is coherent and verification supports it; do not churn through stylistic alternatives.

Briefly report the structural improvements, any intentional behavior correction, checks actually run and their outcomes, and remaining limitations. Distinguish the reshaping work from changes that already existed. Do not claim verification that was not performed, or commit or publish unless separately requested.
