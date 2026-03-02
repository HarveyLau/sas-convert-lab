# 工件 Schema 说明

本目录定义阶段工件的 JSON Schema，适用于 `artifacts/{runId}/`。

## 核心意图工件

- `vision-brief.schema.json`
- `decision-log.schema.json`
- `open-questions.schema.json`

## 阶段工件

- `discovery.schema.json`
- `analysis.schema.json`
- `migration-plan.schema.json`
- `design-spec.schema.json`
- `conversion-manifest.schema.json`
- `validation-report.schema.json`

## 阶段闸门契约

每个阶段工件必须包含：

- `questions_for_user`（建议 3-5 条）
- `assumptions`
- `alignment_score`（1-5）
