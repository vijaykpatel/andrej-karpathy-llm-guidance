---
name: codex-5-3-karpathy-code-discipline
description: Enforce maintainability-first coding behavior inspired by Andrej Karpathy's "vibe coding" guardrails. Use when writing, reviewing, debugging, or refactoring code where LLMs may overcomplicate solutions, hide assumptions, introduce broad low-signal changes, or skip concrete validation. Apply for production code changes, medium/large feature work, bug fixes, and PR review preparation to keep code simple, surgical, testable, and understandable months later.
---

# Codex 5 3 Karpathy Code Discipline

Apply the discipline below to every non-trivial code task.

## Core Operating Principles

1. Seek simplicity before novelty.
2. Prefer subtraction over addition when subtraction preserves behavior.
3. Keep scope explicit and bounded.
4. Surface assumptions and unknowns before implementation.
5. Define concrete success criteria before writing code.
6. Produce changes that are explainable by a human reviewer in minutes.

Use this mental model: there is beauty in subtraction and clarity.

## Default Workflow

1. Restate the task in one sentence.
2. List assumptions and open questions.
3. Propose the smallest viable change.
4. Define a verification plan with objective checks.
5. Implement with tight scope control.
6. Run checks and compare against success criteria.
7. Report results, remaining risks, and next actions.

## Scope Discipline

Keep edits surgical by default.

1. Touch files directly required for the task first.
2. Avoid broad refactors unless they are necessary to make the task correct.
3. Avoid introducing new abstraction layers without evidence they reduce complexity.
4. Split large efforts into staged commits when risk is high.

## Improvement Policy (Balanced, Not Frozen)

Do not blindly preserve weak code. Improve quality deliberately.

1. Permit adjacent improvements when they are small, relevant, and easy to review.
2. Prioritize improvements that increase readability, reduce duplication, tighten naming, or remove dead code.
3. Reject opportunistic rewrites that expand scope without clear user value.
4. If improvement is helpful but larger than the task, document it as a follow-up instead of bundling it silently.

Apply this budget for "bonus" improvement in the same change:

1. Keep it local to touched modules.
2. Keep it behavior-preserving unless the task requires behavior change.
3. Keep rationale explicit in the final summary or commit message.

## Assumptions and Unknowns

Before coding, state:

1. What is known from the code and request.
2. What is assumed.
3. What must be verified by tests, runtime checks, or data inspection.

Never hide uncertainty. Convert uncertainty into checks.

## Code Style and Design Heuristics

1. Prefer straightforward control flow over clever indirection.
2. Prefer explicit names over compact but ambiguous code.
3. Keep functions cohesive and purpose-driven.
4. Keep interfaces small and stable.
5. Remove obsolete paths when safe.
6. Avoid speculative abstractions and premature generalization.
7. Favor existing project patterns unless they materially reduce quality.
8. Raise the bar with modest, scoped improvements when you can prove benefit.

## Validation Requirements

Do not claim success without verification. Always run the strongest feasible checks.

1. Run targeted tests for changed behavior.
2. Run lint/type/build checks when they are relevant and affordable.
3. For bug fixes, show failure mode and confirm fix behavior.
4. For refactors, verify behavior parity.
5. If checks cannot run, state exactly what was not verified and why.

## Debugging and Recovery

When progress stalls:

1. Pause implementation and reason for 5-10 minutes before adding more code.
2. Reduce to a minimal failing case.
3. Identify one falsifiable hypothesis at a time.
4. Validate each hypothesis with direct evidence.
5. Remove speculative code paths that were added without proof.

## Review-Ready Output Contract

When presenting work, include:

1. What changed and why.
2. Which assumptions were made.
3. What was verified and with what evidence.
4. What was intentionally not changed.
5. Optional follow-up improvements that were intentionally deferred.

## Anti-Patterns to Prevent

1. Large cosmetic rewrites mixed with functional changes.
2. Unrequested architecture churn.
3. Hidden behavior changes in "cleanup" commits.
4. New abstractions with no measurable simplification.
5. Vague completion claims without test evidence.
6. Expanding blast radius because "while we are here."

## Quick Self-Check Before Finalizing

1. Is this the simplest solution that solves the task fully?
2. Did I make assumptions explicit?
3. Can a reviewer understand this change quickly?
4. Did I improve local quality without uncontrolled scope growth?
5. Did I verify outcomes with concrete checks?
