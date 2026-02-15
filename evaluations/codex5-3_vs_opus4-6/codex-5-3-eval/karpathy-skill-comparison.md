# Evaluation: `codex-5-3-karpathy-code-discipline` vs `opus-4-6-karpathy-code-guidelines`

## Decision

`opus-4-6-karpathy-code-guidelines` is the better match overall for both:

1. what the tweet explicitly says, and
2. what Karpathy likely values based on his background (pragmatic engineering, clarity, iteration, and strong verification discipline).

## Why `opus-4-6` is better

- It mirrors key tweet points more directly: silent assumptions, missing clarifications, no tradeoff discussion, weak pushback, and sycophancy.
- It strongly targets overcomplication and abstraction bloat, which is one of the tweet's main complaints.
- It includes explicit "tests first" and concrete verification framing, which aligns with the tweet's leverage section.
- It pushes for readable, maintainable code that survives handoff, which fits Karpathy's long-term engineering lens.

## What `opus-4-6` does worse

- The added philosophy reference can feel heavier than needed for a practical skill and risks becoming instructional overhead.
- It is less procedural than `codex-5-3` in day to day execution flow, so operator consistency may depend more on model judgment.
- It does not capture the full leverage pattern from the tweet (for example, explicit naive-first-then-optimize wording).

## What `codex-5-3` does better

- It gives a tighter execution loop (restate task, assumptions, smallest change, verification, report), which is very usable in real coding sessions.
- It has strong scope control and anti-pattern checks, which helps prevent noisy diffs and unrelated changes.
- It is disciplined about explicit assumptions and objective checks, which fits Karpathy's practical style.

## What `codex-5-3` does worse

- It misses several tweet-specific failure modes that `opus-4-6` captures more clearly (tradeoff surfacing, pushback behavior, sycophancy).
- It does not emphasize "tests first" as strongly.
- It is more generic maintainability guidance and less tightly mapped to the exact wording and concerns in the tweet.

## Bottom line

If your target is highest fidelity to this specific tweet plus Karpathy's observed engineering stance, pick `opus-4-6-karpathy-code-guidelines`.

If your target is a stricter day to day operating checklist with lower variance in execution, `codex-5-3-karpathy-code-discipline` is still very strong, but slightly less faithful to the tweet itself.
