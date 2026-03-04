---
name: s2t-artifact-contract
description: Enforces JSON artifact field contracts for each migration stage using repository schemas. Use when creating or reviewing stage artifacts in artifacts/{runId}/.
---

# S2T Artifact Contract

Use this skill before finalizing any JSON artifact.

## Artifact-to-Schema Map

- `vision_brief.json` -> `schemas/vision-brief.schema.json`
- `decision_log.json` -> `schemas/decision-log.schema.json`
- `open_questions.json` -> `schemas/open-questions.schema.json`
- `discovery.json` -> `schemas/discovery.schema.json`
- `analysis.json` -> `schemas/analysis.schema.json`
- `migration_plan.json` -> `schemas/migration-plan.schema.json`
- `design_spec.json` -> `schemas/design-spec.schema.json`
- `conversion_manifest.json` -> `schemas/conversion-manifest.schema.json`
- `validation_report.json` -> `schemas/validation-report.schema.json`

## Contract Checks

1. Ensure required fields from schema are present.
2. Respect type constraints and enum values.
3. If schema uses `additionalProperties: false`, do not add extra keys.
4. For stage artifacts, always include:
   - `questions_for_user`
   - `assumptions`
   - `alignment_score` (1-5 integer)

## Stage Gate Strength

- `questions_for_user` must have at least 1 item by schema.
- Preferred output quality is 3-5 items.

## Output

Return a compact contract check summary:

```markdown
## Artifact Contract Check
- artifact: ...
- schema: ...
- required_fields: pass|fail
- types_and_enums: pass|fail
- stage_gate_fields: pass|fail
- notes:
  - ...
```
