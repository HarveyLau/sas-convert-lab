---
name: s2t-stage-gate
description: Standardizes stage gate output and alignment decisions across Discover, Analyze, Plan, Design, Convert, and Validate. Use when finalizing any stage result or deciding whether the workflow can proceed.
---

# S2T Stage Gate

Use this skill at the end of every stage.

## Goal

Produce a consistent gate review so users can approve, correct, or loop the
stage before the workflow continues.

## Required Process

1. Summarize the stage output in 2-5 bullets.
2. Ask 3-5 high-impact questions in `questions_for_user`.
3. List explicit assumptions in `assumptions`.
4. Score alignment from 1-5 in `alignment_score`.
5. Set `next_action` to `wait_for_user_confirmation`.

## Alignment Rules

- If `alignment_score >= 4`, stage may proceed only after explicit user approval.
- If `alignment_score < 4`, do not proceed. Ask follow-up questions and refine.
- Never skip the user confirmation gate.

## Convert-Specific Rule

Before conversion generation, include `Pre-Convert Intent Check`:

- `restated_developer_vision`
- `must_preserve_behaviors`
- `accepted_deviations`
- `unresolved_questions`

Wait for explicit approval.

## Output Template

```markdown
## Stage Gate: {StageName}

### stage_output_summary
- ...

### questions_for_user
1. ...
2. ...
3. ...

### assumptions
- ...

### alignment_score
- score: {1-5}
- reason: ...

### next_action
- wait_for_user_confirmation
```
