# sas-convert-lab

Human-in-the-loop multi-agent framework for converting SAS project directories
to target data stacks in VS Code + GitHub Copilot Custom Agents.

## What This Solves

- Converts SAS data-job projects by engineering directory, not by single file.
- Supports iterative migration toward target stacks:
  - `python-pandas`
  - `python-bigquery`
  - extensible to `pyspark` and others
- Keeps developers in control through mandatory question loops at each stage.
- Uses static analysis + LLM semantic extraction only (no SAS runtime, no saspy).

## End-to-End Flow

`Discover -> Analyze -> Plan -> Design -> Convert -> Validate`

Each stage includes:

1. `questions_for_user` (3-5 high-impact questions)
2. `assumptions` (must be accepted or corrected)
3. `alignment_score` (1-5)

If `alignment_score < 4`, orchestrator must loop and refine before proceeding.

## Human-In-The-Loop Principles

- Ask more before generating more.
- Restate developer vision before conversion.
- Capture key decisions in machine-readable artifacts.
- Surface deviations explicitly, never hide them.

## Repository Layout

```text
.github/agents/
  sas-orchestrator.agent.md
  sas-discoverer.agent.md
  sas-analyzer.agent.md
  sas-planner.agent.md
  sas-designer.agent.md
  sas-converter.agent.md
  sas-validator.agent.md
schemas/
templates/
  python-pandas/mapping.yaml
  python-bigquery/mapping.yaml
docs/
  vision.md
  customer-demo-playbook.md
  stage-question-pack.md
examples/sample-run/artifacts/run-001/
```

## Artifact Contracts

Every run writes artifacts under `artifacts/{runId}/`:

- `vision_brief.json`
- `decision_log.json`
- `open_questions.json`
- `discovery.json`
- `analysis.json`
- `migration_plan.json`
- `design_spec.json`
- `conversion_manifest.json`
- `validation_report.json`

Schemas live in `schemas/`.

## Documentation

- Vision and framework intent: `docs/vision.md`
- Customer-facing live demo script: `docs/customer-demo-playbook.md`
- Reusable stage-level question templates: `docs/stage-question-pack.md`

## Quick Start (VS Code + Copilot)

1. Open this repo in VS Code.
2. Open Copilot Chat and select `@sas-orchestrator`.
3. Start with:
   - `@sas-orchestrator Convert this SAS project to python-bigquery`
4. Answer stage questions as they appear.
5. Review stage outputs and approve before next stage.

## Stage-Specific Commands

- `@sas-discoverer Scan current SAS project and build source inventory`
- `@sas-analyzer Build lineage and migration risk report`
- `@sas-planner Propose phased migration backlog`
- `@sas-designer Produce target architecture and module contracts`
- `@sas-converter Generate conversion manifest and code skeleton`
- `@sas-validator Run code+data parity validation checklist`

## Constraints

- No SAS execution.
- No `saspy`.
- No hidden assumptions across stages.
- No stage transition without explicit user alignment.

## Non-Goals (MVP)

- Full automatic migration without user review.
- One-shot perfect semantic parity for all macro-heavy projects.
- Runtime execution of SAS programs.
