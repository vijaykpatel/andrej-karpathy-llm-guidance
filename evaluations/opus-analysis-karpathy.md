## Verdict: **karpathy-coding-discipline** (Skill 2) is the better skill.

Here's why, broken down:

---

### Where Skill 2 wins

**It practices what it preaches.** Karpathy's core complaint is that LLMs overcomplicate things — they build 1000 lines when 100 will do. Skill 1 has a 70-line SKILL.md *plus* a 179-line philosophy reference doc with an anti-patterns gallery, code examples, and a table of contents. Skill 2 is 86 lines, single file, no extras. There's a real irony in a "minimize complexity" skill being itself bloated with supporting material.

**It captures the "Leverage" concept directly from the tweet.** Karpathy's leverage section is one of the most distinctive and actionable parts of the tweet — give success criteria not instructions, write tests first then pass them, naive algorithm first then optimize. Skill 2 has an explicit "Leverage Loop" section (lines 66-69) that maps directly to this. Skill 1 buries some of this in Principle 4 but misses the "naive first, then optimize" pattern entirely and doesn't use the leverage framing at all.

**It has an Execution Loop.** Karpathy talks about plan mode, about agents looping until they meet goals, about declarative over imperative. Skill 2's step-by-step execution loop (lines 58-63) — restate task, list criteria, list assumptions, inspect code, implement, verify — is exactly the kind of structured process Karpathy would endorse. Skill 1 has no equivalent.

**Its tone matches Karpathy.** Karpathy writes in terse, direct, no-nonsense prose. Skill 2 mirrors this — short headers, bullet points, no elaboration beyond what's needed. Skill 1 reads more like a teaching document with detailed explanations and examples, which is useful but not how Karpathy communicates.

---

### Where Skill 1 wins

**Dead code cleanup.** The tweet explicitly says LLMs "don't clean up dead code after themselves" — this is a criticism, meaning they *should*. Skill 1 correctly says "Delete what you don't need" (line 29). Skill 2 takes the opposite position: "If you notice unrelated dead code, mention it. Do not delete it unless asked" (line 47). This is more conservative than what Karpathy advocates.

**The philosophy doc is genuinely good context.** The anti-patterns gallery (Enterprise Astronaut, Silent Guesser, Diff Bomber, etc.) and the "What Good Looks Like" section are excellent reference material. If you're trying to *teach* the concepts, Skill 1 does this far better.

**The "Elevation Principle" framing.** Skill 1's articulation of "elevate what you touch, stay focused on the task" (philosophy.md lines 107-125) is a nuanced take that Skill 2 also captures ("Local elevation rule") but Skill 1 explains *why* — that being too conservative locks in existing quality. This matches Karpathy's pragmatism.

---

### Where Skill 1 goes wrong

**It introduces concepts not in the tweet.** The "taste" framing (philosophy.md line 21: "LLMs Don't Have Taste") comes from a different Karpathy talk/context, not this tweet. Attributing it here muddies the source material. The tweet is about observable failure modes, not an abstract "taste" concept.

**The philosophy.md is scope creep.** A reference document explaining *why* each principle exists is exactly the kind of "wouldn't it be nice to have" addition that Karpathy warns about. The skill should be the instructions, not a teaching curriculum.

---

### Summary table

| Aspect | Skill 1 (code-guidelines) | Skill 2 (coding-discipline) |
|---|---|---|
| Conciseness | Over-elaborate | Matches Karpathy's style |
| Leverage concept | Missed | Captured directly |
| Naive-first-then-optimize | Missing | Present |
| Execution loop | None | Explicit 6-step process |
| Dead code handling | Correct (delete it) | Wrong (don't delete) |
| Philosophy/context | Excellent depth | Minimal |
| Faithful to tweet | Adds external concepts | Stays closer to source |

Skill 2 is the better operational skill — it's tighter, more actionable, and more faithful to the tweet. Its one notable error is the dead code stance. Skill 1 is better as educational material but ironically violates the principles it teaches by being overcomplicated.
