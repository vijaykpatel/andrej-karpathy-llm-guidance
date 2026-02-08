---
name: codex-5-2-karpathy-code-discipline
description: Behavioral guidelines to reduce common LLM coding mistakes while writing, reviewing, or refactoring code. Use when the task needs surgical changes, explicit success criteria, surfaced assumptions, and long term maintainability. Trigger on requests to avoid overcomplication, keep diffs small, improve readability, reduce duplication, or keep PRs focused while still allowing justified local improvements.
---

# Codex 5.2 Karpathy Coding Discipline

## Intent

Deliver correct, simple, maintainable code with small, reviewable diffs. Prefer clarity and correctness over cleverness. Assume the model can be wrong and require active oversight.

## Think First

- State assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them and ask which to choose.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop and name the confusion.
- Surface inconsistencies and tradeoffs instead of silently choosing.
- Do not edit code you do not understand. Ask or explain first.

## Simplicity First

- Write the minimum code that solves the problem.
- Avoid features beyond what was asked.
- Avoid abstractions for single use code.
- Avoid flexibility or configurability that was not requested.
- Avoid bloated helper layers unless they reduce complexity.
- If 200 lines could be 50, rewrite it.

## Surgical Changes With Local Elevation

Touch only what you must, then clean up only what your changes affected.

Local elevation rule

- Allow small adjacent improvements when they are local, low risk, and clearly beneficial.
- Keep them in the same files and functions you already touched.
- Justify each improvement in the summary.
- Do not change comments or formatting unless required for the task or a local improvement you justify.

Do not without asking first

- Broad refactors or large style cleanups.
- New abstractions that are not required for the task.
- Changes across many files for aesthetic reasons only.

If you notice unrelated dead code, mention it. Do not delete it unless asked.

## Goal Driven Execution

- Define success criteria that can be verified.
- Convert requests into tests or checks when possible.
- Use a short plan with explicit verification steps.
- Prefer a naive, correct solution first, then optimize while preserving correctness.

## Execution Loop

1. Restate task and constraints.
2. List success criteria.
3. List assumptions and open questions.
4. Inspect existing code to align with local style and APIs.
5. Implement the smallest change that meets the criteria.
6. Verify or explain why verification was not run.

## Leverage Loop

- Give the model success criteria, not just instructions.
- Ask for tests first when appropriate, then pass them.
- Use explicit checks to prevent silent incorrect assumptions.

## Output Contract

Provide

- A concise change summary.
- Tests run with results, or "Not run" with reason.
- Assumptions and follow ups.
- Any local improvements with justification.

## Success Signals

- Fewer unnecessary changes in diffs.
- Clarifying questions appear before implementation.
- Fewer rewrites caused by overcomplication.
- Fewer hidden changes to unrelated code or comments.
