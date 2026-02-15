# Skill Comparison: opus-4-6-karpathy-code-guidelines vs codex-5-3-karpathy-code-discipline

## Source Material

Both skills derive from Andrej Karpathy's tweet thread on his experience with LLM-assisted coding (circa late December 2025). The tweet covers workflow shifts, failure modes, leverage strategies, and broader industry implications.

## Evaluator Context on Karpathy

Andrej Karpathy is a founding member of OpenAI, former Sr. Director of AI at Tesla (Autopilot), Stanford PhD under Fei-Fei Li. He is known for valuing clarity, simplicity, and first-principles thinking. His pedagogical work (YouTube lectures, micrograd, nanoGPT, minbpe) consistently demonstrates a preference for minimal, readable implementations over abstraction-heavy designs. He is an engineer who builds things himself, watches them closely, and cares deeply about taste in software.

---

## Overall Verdict

**Winner: codex-5-3-karpathy-code-discipline**

The Codex skill is the more faithful translation of Karpathy's tweet into actionable coding discipline. The Opus skill is more polished and comprehensive as a document, but that polish actually works against it — it over-explains, over-structures, and ironically falls into the very overcomplication trap Karpathy warns about.

---

## Detailed Comparison

### 1. Fidelity to the Tweet's Content

**Codex 5-3: Strong**
The tweet emphasizes watching LLMs "like a hawk," surfacing assumptions, keeping things minimal, and defining success criteria so the agent can loop against them. The Codex skill captures all of these directly and concisely. Its "Default Workflow" (restate task, list assumptions, propose smallest change, define verification, implement, check, report) is a near-direct operationalization of what Karpathy describes as his actual working process.

**Opus 4-6: Good but drifts**
The Opus skill covers the same territory but elaborates significantly beyond what Karpathy actually said. The philosophy.md reference file introduces concepts like "The Elevation Principle," an "Anti-Patterns Gallery" with named archetypes ("The Enterprise Astronaut," "The Silent Guesser"), and a "What Good Looks Like" section with seven properties. These are reasonable extensions, but they are editorial additions — Karpathy didn't name these patterns or frame things this way. The skill reads more like a senior engineering blog post inspired by the tweet than a direct encoding of it.

**Edge: Codex 5-3**

### 2. Tone and Voice

**Codex 5-3: Matches Karpathy's style**
Karpathy writes plainly and directly. "They don't manage their confusion, they don't seek clarifications." The Codex skill mirrors this: terse, imperative, no filler. "Seek simplicity before novelty." "Never hide uncertainty. Convert uncertainty into checks." This is how Karpathy communicates — declarative statements without ceremony. The line "there is beauty in subtraction and clarity" feels authentically Karpathy-adjacent.

**Opus 4-6: More editorial/prescriptive**
The Opus skill uses a more formal, explanatory voice. "LLMs have predictable failure modes: they assume silently, overcomplicate solutions, bloat abstractions..." This is accurate but reads more like a consultant's report than Karpathy's casual, observational style. The philosophy.md doubles down on this with extensive explanations and code examples. Karpathy's tweet is notably example-light — he states observations, not tutorials.

**Edge: Codex 5-3**

### 3. Handling of "Leverage" and "Declarative Over Imperative"

**Codex 5-3: Partially captured**
The tweet's "Leverage" section is one of its most distinctive insights: "Don't tell it what to do, give it success criteria and watch it go. Get it to write tests first and then pass them. Change your approach from imperative to declarative to get the agents looping longer." The Codex skill captures the success-criteria and test-first aspect well (Principles 5 and the validation section), but doesn't explicitly encode the "declarative over imperative" framing or the concept of letting agents loop.

**Opus 4-6: Also partially captured**
The Opus skill's Principle 4 ("Define and Verify Success") covers the test-first idea. But it similarly misses the broader strategic insight about declarative framing and agent looping as a leverage mechanism.

**Edge: Tie — both miss the same key insight**

### 4. Handling of Complexity and Overcomplication

**Codex 5-3: Lean and precise**
Section on "Code Style and Design Heuristics" gives 8 tight rules. "Prefer subtraction over addition when subtraction preserves behavior" is an excellent distillation. The skill practices what it preaches — it's short.

**Opus 4-6: Thorough but ironic**
Principle 2 ("Minimize Complexity Ruthlessly") is well-written and includes the tweet's specific example about 1000 lines vs 100 lines. The philosophy.md's "Complexity Addiction" section with code examples is helpful. But the Opus skill as a whole is ~250 lines across two files, while the Codex skill is ~120 lines in one file. The Opus skill is, in a sense, the overcomplicated version of what the Codex skill does simply. Karpathy would notice this.

**Edge: Codex 5-3** — it embodies the principle, not just describes it

### 5. Scope Discipline / Surgical Changes

**Codex 5-3: Well-handled**
The "Scope Discipline" and "Improvement Policy" sections are cleanly separated. The improvement policy with its explicit "budget" concept (local, behavior-preserving, rationale-explicit) is a practical framework that maps well to Karpathy's observation about models making side-effect changes.

**Opus 4-6: Also well-handled, slightly better nuanced**
Principle 3 ("Make Surgical, Traceable Changes") and the Elevation Principle in philosophy.md provide a more nuanced treatment. The distinction between "don't be timid" and "don't go hunting for improvements" is carefully articulated. The guidance about PR reviewability is practical and specific.

**Edge: Opus 4-6** — slightly better nuance on the "improve what you touch" balance

### 6. Debugging and Recovery

**Codex 5-3: Has it**
Includes an explicit "Debugging and Recovery" section: pause, reduce to minimal case, one hypothesis at a time, remove speculative code. This maps to Karpathy's "Tenacity" observation and his note that agents relentlessly try things. Having explicit guidance for when things go wrong is practical and important.

**Opus 4-6: Missing**
No equivalent section. The skill assumes a happy path — plan, implement, verify. But Karpathy's tweet explicitly describes watching agents struggle for 30 minutes. Guidance for stalled states is a real gap.

**Edge: Codex 5-3**

### 7. Review-Ready Output

**Codex 5-3: Explicit contract**
The "Review-Ready Output Contract" section specifies exactly what to include when presenting work: what changed, assumptions, verification evidence, what was intentionally not changed, deferred improvements. This directly addresses Karpathy's concern about watching agents like a hawk — it makes the agent's work inspectable.

**Opus 4-6: Implicit**
The Opus skill mentions PR reviewability in Principle 3 but doesn't specify an output format. The human has to extract this information from the code and diff themselves.

**Edge: Codex 5-3**

### 8. Completeness as a Reference Document

**Opus 4-6: Clearly superior**
The philosophy.md file with its failure mode taxonomy, code examples, and anti-patterns gallery makes the Opus skill a much better reference for someone trying to *understand* why these guidelines exist. If you're onboarding a new engineer to these principles, the Opus skill is the better teaching document.

**Codex 5-3: Operational, not educational**
The Codex skill assumes you already understand the "why" and just need the "what." This is fine for an LLM system prompt but weaker as a human-readable guide.

**Edge: Opus 4-6**

---

## Summary Table

| Dimension | Codex 5-3 | Opus 4-6 | Edge |
|---|---|---|---|
| Fidelity to tweet content | High | Good, with drift | Codex |
| Tone match to Karpathy | Strong | More editorial | Codex |
| Leverage/declarative insight | Partial | Partial | Tie |
| Complexity handling | Practices what it preaches | Thorough but ironic | Codex |
| Scope discipline | Clean | Slightly better nuance | Opus |
| Debugging/recovery | Present | Absent | Codex |
| Review-ready output | Explicit contract | Implicit | Codex |
| Reference/teaching quality | Operational only | Excellent | Opus |

---

## What Each Does Better

### Codex 5-3 does better:
- **Brevity as embodiment**: It is itself a demonstration of the principles it teaches. Karpathy would appreciate a skill that doesn't over-explain.
- **Operational workflow**: The 7-step default workflow is immediately actionable. An LLM can follow it step by step.
- **Debugging guidance**: Addresses what to do when things go wrong, which is a real and frequent scenario Karpathy describes.
- **Output contract**: Specifies what the agent should report, making oversight easier — directly supporting Karpathy's "watch them like a hawk" advice.
- **Self-check**: The 5-question checklist at the end is a tight, practical gate before finalizing work.

### Opus 4-6 does better:
- **Educational depth**: The philosophy.md is a genuinely good document for understanding *why* these rules exist. The failure mode taxonomy with examples is useful for humans learning the principles.
- **Nuanced scope guidance**: The "Elevation Principle" articulates the balance between improvement and restraint more carefully than the Codex skill's improvement policy.
- **Code examples**: Concrete good/bad code comparisons make the anti-patterns tangible in a way that abstract rules don't.
- **Contextual application**: The "Applying These Guidelines" section (new code vs modifications vs reviews vs refactoring) provides useful mode-switching guidance.

### What Each Does Worse

### Codex 5-3 weaknesses:
- **No examples**: Entirely abstract. A reader unfamiliar with these failure modes might not recognize them in practice.
- **Misses the "fun" and "expansion" angles**: Karpathy's tweet isn't only about discipline — it's also about how LLM coding is *more fun* and enables doing *more*. The Codex skill is all guardrails, no excitement. This undersells Karpathy's balanced perspective.
- **No reference to Karpathy or context**: Doesn't explain the origin or reasoning. As a standalone document, it could be any generic coding guideline.

### Opus 4-6 weaknesses:
- **Overcomplicated for its purpose**: Two files, ~250 lines, named archetypes, structured taxonomy. As an LLM system prompt, much of this is wasted tokens. As Karpathy himself says: "They will implement an inefficient, bloated, brittle construction over 1000 lines of code and it's up to you to be like 'umm couldn't you just do this instead?'"
- **Missing debugging/recovery**: A significant gap for a practical coding guideline.
- **Missing output contract**: Doesn't specify what the agent should report, leaving the human to do more work extracting information.
- **Editorial drift**: Introduces framing and terminology that Karpathy didn't use, which risks misattributing ideas to him.

---

## Final Assessment

If Karpathy were to review both skills side by side, the Codex 5-3 skill is more likely the one he'd point at and say "yeah, that's what I meant." It's tighter, more operational, and — critically — it doesn't overcomplicate the message about not overcomplicating things.

The Opus 4-6 skill is the better *document* but the worse *skill*. Its strengths (education, examples, nuance) are more valuable in a blog post or team wiki than in an LLM system prompt. Its weaknesses (length, missing operational sections) matter more in the context where these skills actually get used.

**Recommendation**: The Codex 5-3 skill is the better choice for active use. The Opus 4-6 philosophy.md could serve as companion reading for humans who want to understand the reasoning.
