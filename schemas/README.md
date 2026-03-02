# Artifact Schemas

JSON schemas for stage artifacts in `artifacts/{runId}/`.

## Core Intent Artifacts

- `vision-brief.schema.json`
- `decision-log.schema.json`
- `open-questions.schema.json`

## Stage Artifacts

- `discovery.schema.json`
- `analysis.schema.json`
- `migration-plan.schema.json`
- `design-spec.schema.json`
- `conversion-manifest.schema.json`
- `validation-report.schema.json`

## Stage Gate Contract

Every stage artifact must include:

- `questions_for_user` (3-5 items recommended)
- `assumptions`
- `alignment_score` (1-5)
