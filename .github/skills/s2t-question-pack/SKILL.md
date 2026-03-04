---
name: s2t-question-pack
description: Generates stage-specific, decision-driving user questions for SAS migration. Use when a stage needs high-impact questions instead of generic information gathering.
---

# S2T Question Pack

Use this skill whenever a stage must ask users 3-5 questions.

## Primary Source

- `docs/stage-question-pack.md`
- If the conversation is Chinese-first, also adapt from
  `docs/stage-question-pack.zh-CN.md`.

## Question Quality Rules

- Ask decision-driving questions, not trivia.
- Cover business and technical dimensions together.
- Prefer questions that change scope, priority, quality threshold, or rollout.
- Keep each question concrete and answerable.

## Stage Focus

- Discover: scope boundaries, source-of-truth datasets, priority order.
- Analyze: parity expectations, acceptable semantic approximation, SLA impact.
- Plan: wave sequencing, acceptance criteria, cutover strategy.
- Design: architecture conventions, SQL-vs-Python ownership, environment limits.
- Convert: boundary approval, macro handling direction, deferrable gaps.
- Validate: go-live threshold, must-fix vs defer, post-cutover ownership.

## Output Requirement

- Return exactly 3-5 numbered questions.
- Add 0-3 follow-up options only when the stage is blocked by ambiguity.
- Write unresolved items to `open_questions.json` in the stage output flow.
