# sas-convert-lab Vision

## Mission

Build a practical, developer-centered framework that converts SAS project
directories into modern target stacks (starting with `python-pandas` and
`python-bigquery`) inside VS Code + Copilot, without requiring SAS runtime.

## Problem Statement

Most SAS migrations fail when they are treated as file-by-file translation.
Data jobs are system workflows with lineage, implicit assumptions, and business
constraints. A useful migration framework must:

- operate at project/directory level
- keep humans in control at decision points
- preserve business intent, not only syntax

## Core Principles

1. **No runtime dependency on SAS**
   - Static analysis + semantic extraction only
   - No `saspy`, no SAS engine execution
2. **Human-in-the-loop by design**
   - Every stage asks targeted questions
   - No stage transition without user confirmation
3. **Intent-first conversion**
   - Convert toward user vision and business outcomes
   - Track assumptions, decisions, and accepted deviations
4. **Traceable outputs**
   - Every generated artifact links back to source context
   - Risks and confidence are explicit

## Framework Lifecycle

`Discover -> Analyze -> Plan -> Design -> Convert -> Validate`

### Discover
- Build source inventory and include/macro map
- Identify quick risks and unknowns

### Analyze
- Build lineage and semantic behavior summary
- Score migration complexity and module-level risk

### Plan
- Define migration waves, dependencies, and acceptance criteria
- Align timeline and quality tradeoffs with stakeholders

### Design
- Define target architecture, module contracts, and config strategy
- Lock implementation boundaries before generation

### Convert
- Generate target artifacts with source-to-target traceability
- Run pre-convert and post-convert intent alignment gates

### Validate
- Verify code structure, data parity, and intent fit
- Produce go/no-go readiness report

## Multi-Agent Operating Model

- `sas-orchestrator`: controls stage flow and alignment gates
- `sas-discoverer`: scans and classifies project assets
- `sas-analyzer`: extracts lineage/behavior and risk
- `sas-planner`: creates phased migration plan
- `sas-designer`: defines implementation contracts
- `sas-converter`: generates mapped target artifacts
- `sas-validator`: validates quality, parity, and readiness

## Intent Alignment Loop

Each stage must output:

- `questions_for_user` (3-5 high-impact questions)
- `assumptions` (must be accepted or corrected)
- `alignment_score` (1-5)

Rule:

- if `alignment_score >= 4`: stage may proceed after confirmation
- if `alignment_score < 4`: refine stage and ask follow-up questions

## Durable Run Memory

Each run preserves intent and decisions in:

- `vision_brief.json`
- `decision_log.json`
- `open_questions.json`

This memory is required input for planner, designer, converter, and validator.

## MVP Success Criteria

- Users can start with one orchestrator prompt in Copilot Chat.
- Framework asks useful stage questions before conversion.
- Generated outputs include clear traceability and known gaps.
- Validation report supports a clear go/no-go discussion.
