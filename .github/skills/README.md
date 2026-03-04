# Copilot Agent Skills

Project-level skills for `sas-convert-lab`.

These skills are the primary reusable capability layer for the migration
workflow. Agents keep orchestration and stage sequencing lightweight, while
skills provide consistent execution patterns.

## Skill Catalog

- `s2t-stage-gate`
  - Unifies stage gate output structure and alignment decisions.
- `s2t-question-pack`
  - Generates high-impact stage questions based on the current phase.
- `s2t-artifact-contract`
  - Enforces required artifact fields from `schemas/*.schema.json`.
- `s2t-target-mapping`
  - Applies target profile mapping from `templates/*/mapping.yaml`.

## Usage Notes

- Keep `@sas-orchestrator` as the default entrypoint.
- Stage agents should call relevant skills before finalizing stage outputs.
- If a skill output conflicts with explicit user intent, user intent wins.
