---
name: s2t-target-mapping
description: Applies target-profile mapping rules for python-pandas and python-bigquery during design and conversion. Use when deciding project layout, pattern translation, and validation hints for a target stack.
---

# S2T Target Mapping

Use this skill in Design and Convert stages.

## Target Templates

- `templates/python-pandas/mapping.yaml`
- `templates/python-bigquery/mapping.yaml`

## Required Process

1. Detect `target_profile`.
2. Load the matching mapping template.
3. Apply:
   - `principles`
   - `runtime_defaults`
   - `project_layout`
   - `pattern_mappings`
   - `validation_hints`
4. If user intent conflicts with template defaults, ask for explicit decision.
5. Record major source-to-target pattern choices in conversion notes.

## Guardrails

- Do not invent unsupported target profiles without user confirmation.
- Keep SQL-first or Python-first decisions explicit.
- Preserve traceability for macro-heavy or dynamic SQL logic.

## Output Format

```markdown
## Target Mapping Decision
- target_profile: ...
- selected_template: ...
- adopted_layout:
  - ...
- critical_pattern_mappings:
  - sas_pattern: ...
    target_pattern: ...
    reason: ...
- validation_focus:
  - ...
```
