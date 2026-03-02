# Customer Demo Playbook

This playbook helps you run a reliable 15-25 minute demo of
`sas-convert-lab` for data migration stakeholders.

## Demo Goal

Show that migration is:

- controlled by developers in VS Code
- driven by multi-agent collaboration
- aligned to business intent through staged questions

## Pre-Demo Checklist

- Open repo in VS Code.
- Ensure Copilot Chat is available.
- Prepare a small SAS sample project folder.
- Confirm `.github/agents/*.agent.md` files are visible.
- Keep `examples/sample-run/artifacts/run-001/` open for fallback reference.

## Recommended Demo Script

## 1) Set context (2 min)

Say:

- "This is not one-shot translation."
- "We migrate by workflow stages with explicit approvals."
- "No SAS runtime is required."

## 2) Trigger orchestrator (1 min)

Prompt:

```text
@sas-orchestrator Convert this SAS project to python-bigquery.
Focus on nightly ETL jobs first.
```

Expected:

- orchestrator starts `Discover`
- outputs stage gate with questions + assumptions

## 3) Show human-in-the-loop gating (5 min)

Answer discovery/analyze questions live:

- define scope in/out
- confirm source-of-truth datasets
- define KPI tolerance and SLA priorities

Highlight:

- no next stage without user confirmation
- unresolved items tracked in `open_questions.json`

## 4) Show design and convert alignment (5-8 min)

When reaching convert:

- point out pre-convert intent restatement
- approve or edit assumptions
- ask for refinement if naming or boundaries are off

Highlight:

- conversion is guided, not blind
- source-to-target trace is recorded

## 5) Show validation and decision readiness (3-5 min)

Show final outputs:

- `validation_report.json`
- `conversion_manifest.json`
- summary of must-fix vs accepted deviations

Close with:

- "This output supports a real go/no-go decision."

## Demo Q&A Starters

- "Can we prioritize only high-business-value jobs first?"
- "How do we handle macro-heavy modules with low confidence?"
- "Can we tighten KPI tolerance before production cutover?"

## Common Objections and Responses

- **Objection:** "Can this do full auto migration?"
  - **Response:** "It can automate generation, but approvals stay human by design."
- **Objection:** "Do we need SAS installed?"
  - **Response:** "No, this framework uses static and semantic analysis only."
- **Objection:** "How do we trust converted output?"
  - **Response:** "Traceability + staged validation + explicit risk reporting."

## Demo Success Signals

- Stakeholders understand stage gates and why they reduce risk.
- Audience asks scope/tolerance questions (good sign of engagement).
- Team agrees to a pilot wave with explicit acceptance criteria.
