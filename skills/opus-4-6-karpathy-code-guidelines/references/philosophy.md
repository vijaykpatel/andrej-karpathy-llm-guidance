# The Philosophy Behind These Guidelines

## Table of Contents
- Why These Rules Exist
- The Core Problem: LLMs Don't Have Taste
- Failure Mode 1: Silent Assumptions
- Failure Mode 2: Complexity Addiction
- Failure Mode 3: Scope Creep Without Awareness
- Failure Mode 4: No Definition of Done
- Failure Mode 5: Write-Only Code
- The Elevation Principle
- Anti-Patterns Gallery
- What Good Looks Like

## Why These Rules Exist

Andrej Karpathy — founding member of OpenAI, former Sr. Director of AI at Tesla where he led Autopilot, Stanford PhD in deep learning under Fei-Fei Li — observed a consistent pattern after heavy AI-assisted coding: LLMs produce code that works in the moment but creates maintenance nightmares over months. The problem isn't capability. The problem is taste.

Karpathy went from 80% manual coding to 80% AI-assisted coding in the span of weeks. The productivity gain was real. But so was the quality gap. These guidelines are the corrective — the behavioral guardrails that bridge the gap between "it works" and "it's production-grade."

## The Core Problem: LLMs Don't Have Taste

Karpathy's central observation: AI assistants "basically don't have a sense of taste." They can write syntactically correct, functionally valid code that a senior engineer would immediately flag as wrong — not because it doesn't work, but because it's overcomplicated, fragile, or unmaintainable.

Taste in software engineering means:
- Knowing when 50 lines is enough and 200 is too many
- Choosing the boring solution over the clever one
- Recognizing when an abstraction is premature
- Understanding that code that's easy to delete is better than code that's "flexible"
- Feeling the difference between a clean diff and a noisy one

LLMs don't feel these things. They optimize for completion, not for the long-term health of a codebase. These guidelines are a proxy for taste.

## Failure Mode 1: Silent Assumptions

**What happens:** The model receives an ambiguous request. Instead of asking for clarification, it picks an interpretation and runs with it. Sometimes it picks right. When it picks wrong, you discover the mistake 200 lines of code later.

**Why it happens:** LLMs are trained to be helpful. Asking a clarifying question feels like failing to be helpful. So they guess.

**The fix:** Surface assumptions before writing code. State what you're about to do and why. If there are two valid interpretations, present both. Let the human choose.

**Example:**
```
Bad:  User says "add auth." Model adds JWT auth with refresh tokens, role-based
      access control, and session management.
Good: User says "add auth." Model responds: "Auth can mean several things here.
      Options: (1) Simple API key validation — fast, good for internal services.
      (2) JWT with refresh tokens — standard for user-facing apps.
      (3) OAuth integration — if you need third-party login.
      Which fits your use case?"
```

## Failure Mode 2: Complexity Addiction

**What happens:** Simple problems get complicated solutions. A function that should be 20 lines becomes 100. A single-use utility gets wrapped in a class with configuration options. Error handling covers cases that can't happen.

**Why it happens:** LLMs have seen a lot of enterprise code. They pattern-match toward "robust" solutions that handle every edge case, even when the context doesn't warrant it. They also can't tell the difference between a prototype and a production system.

**The fix:** Write the minimum viable implementation first. Then ask: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

**Example:**
```
Bad:  class ValidationPipeline:
          def __init__(self, validators=None, strict_mode=True,
                       error_handler=None, logger=None):
              self.validators = validators or []
              self.strict_mode = strict_mode
              ...
      # 150 lines of framework for validating one form

Good: def validate_signup(email, password):
          errors = []
          if not email or "@" not in email:
              errors.append("Valid email required")
          if len(password) < 8:
              errors.append("Password must be 8+ characters")
          return errors
```

## Failure Mode 3: Scope Creep Without Awareness

**What happens:** Asked to fix a bug in function A, the model also refactors function B, updates the comments in function C, and renames a variable in function D. The diff is 400 lines when it should be 15.

**Why it happens:** LLMs see opportunities for improvement everywhere (because there usually are opportunities). They don't have a sense of "this change is outside the scope of what was asked." They don't think about PR reviewability.

**The fix:** Stay focused on the task. But — and this is critical — don't be so timid that the codebase never improves. The right boundary is: improve the code you're already touching. If you're in a function fixing a bug and you see a confusing variable name, fix it. If you see a completely unrelated problem in another file, mention it but don't act on it.

The goal is not "change nothing extra." The goal is "every change in this diff makes sense in the context of the stated task, and a reviewer can follow the logic without confusion."

## Failure Mode 4: No Definition of Done

**What happens:** The model writes code, says "here you go," and moves on. No tests. No verification. No confirmation that the code actually does what was asked. Sometimes it doesn't even run.

**Why it happens:** LLMs optimize for generating a response, not for verifying correctness. They're trained on completion, not on validation.

**The fix:** Define success criteria before coding. Write tests when possible. Verify the implementation against the criteria. State explicitly what was verified and how.

## Failure Mode 5: Write-Only Code

**What happens:** The code works today but is incomprehensible in three months. Variables named `d`, `temp`, `result2`. Functions that do six things. Implicit dependencies between modules. No structure to guide a reader through the logic.

**Why it happens:** LLMs generate code token by token. They don't step back and ask "will someone understand this in six months?" They don't experience the pain of reading bad code, so they don't learn to avoid writing it.

**The fix:** Name things for understanding. Structure for scannability. Make the code say what it does. Every function should have a single, clear purpose that's obvious from its name and its first few lines.

## The Elevation Principle

This is where these guidelines diverge from a purely conservative approach. Some coding guidelines tell AI: "Don't improve anything. Match existing style. Don't touch anything you weren't asked to touch."

That's too conservative. It locks in existing quality levels and treats the current codebase as sacred. It isn't. Some existing code is bad. Some naming is confusing. Some duplication is harmful. If AI can't improve these things, you're leaving value on the table.

The right principle is: **elevate what you touch, stay focused on the task.**

- If you're in a function and a variable name is misleading, fix it
- If you're adding a feature and you notice the same logic duplicated across two places in the file you're editing, extract it
- If a conditional is confusingly nested where you're working, flatten it
- If an import is unused in the file you're changing, remove it

But:
- Don't go hunting for improvements in files you're not working in
- Don't refactor an entire module because you noticed one issue
- Don't turn a bug fix PR into a style cleanup PR
- Don't make changes that require the reviewer to understand unrelated context

The bar goes up with every commit. But it goes up *locally*, in the code you're already touching, not globally across the entire codebase at once.

## Anti-Patterns Gallery

### The Enterprise Astronaut
```
# Asked: "Parse this JSON config file"
# Delivered: AbstractConfigParserFactory with plugin system
```
Violation: Principle 2. Single-use code doesn't need abstractions.

### The Silent Guesser
```
# Asked: "Add caching"
# Delivered: Redis integration with TTL management
# Should have asked: "In-memory dict, Redis, or file-based? What's your infra?"
```
Violation: Principle 1. Multiple valid approaches existed; model picked one silently.

### The Diff Bomber
```
# Asked: "Fix the null check in getUserById"
# Delivered: 400-line diff touching 12 files with "improvements"
```
Violation: Principle 3. Fix should have been 5 lines in one file.

### The Optimist
```
# "I've added the validation logic as requested."
# (No tests. Doesn't handle the edge case mentioned in the request.
#  Has a typo in the error message.)
```
Violation: Principle 4. No verification against success criteria.

### The Abbreviator
```
const d = getData();
const r = d.filter(x => x.s === 'a').map(x => ({ ...x, p: calc(x.v, x.q) }));
```
Violation: Principle 5. Unreadable in isolation. What is `d`? What is `s`? What is `a`?

## What Good Looks Like

Good AI-assisted code has these properties:

1. **You can read the diff and understand the intent** without additional context
2. **Every change traces to the stated goal** with occasional, local improvements
3. **The code is simpler than you expected** — never more complicated
4. **Names reveal intent** — you rarely need to look up what something does
5. **Tests exist** for non-trivial logic and they express the expected behavior clearly
6. **The PR is reviewable** — a human can approve it in one pass without confusion
7. **The code is deletable** — when this feature is no longer needed, removing it is straightforward

If the code you're writing doesn't have these properties, pause and ask which principle you're violating.
