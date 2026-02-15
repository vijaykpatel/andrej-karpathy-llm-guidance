# Andrej Karpathy LLM Guidance

This repo captures a comparative study of three LLM-generated skills based on a single prompt and the same skill creator. Each model (Codex 5.2, Codex 5.3, and Opus 4.6) used the same skill creator to produce a skill from Andrej Karpathy's tweet, and then each agent compared its own skill against the other model's skill. The repo includes the generated skills and the cross-model evaluations.

## Naming Convention

- **karpathy-coding-discipline** — skill produced by Codex 5.2
- **karpathy-code-guidelines** — skill produced by Opus 4.6

## Source Prompt

- Tweet prompt: https://x.com/karpathy/status/2015883857489522876
- Skill creator: https://skills.sh/anthropics/skills/skill-creator

## Contents

### Skills (3 total)

- `skills/codex-5-2-karpathy-code-discipline` — Codex 5.2
- `skills/codex-5-3-karpathy-code-discipline` — Codex 5.3
- `skills/opus-4-6-karpathy-code-guidelines` — Opus 4.6

### Evaluations (2 subfolders, 4 evaluations total)

Each competition pits one Codex model vs Opus 4.6. Each model evaluated both skills, so there are 2 evaluations per competition.

- `evaluations/codex5-2_vs_opus4-6/`
  - Codex 5.2's comparison of its skill vs Opus 4.6's skill
  - Opus 4.6's comparison of both skills
- `evaluations/codex5-3_vs_opus4-6/`
  - Codex 5.3's comparison of its skill vs Opus 4.6's skill
  - Opus 4.6's comparison of both skills

## Method Summary

The same skill creator was used in Codex and Opus. The Karpathy tweet was provided as the prompt, and each model (Codex 5.2, Codex 5.3, Opus 4.6) generated a skill. Then each agent compared its own skill with the other model's skill in separate chats. The two Codex models were each run head-to-head against the single Opus model, producing two subfolders of evaluations and four comparative analyses in total.
