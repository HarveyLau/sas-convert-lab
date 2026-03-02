# Stage Question Pack

Use these as default high-impact questions. Each stage should ask 3-5 questions,
not all questions at once.

## Question Quality Rules

- Prefer decisions over data collection.
- Ask only what changes implementation direction.
- Use both business and technical language.
- Convert open-ended discussions into explicit choices.

## Discover Questions

- Which folders/jobs are in scope for wave 1?
- Which upstream datasets are the source of truth?
- Which jobs are business-critical by SLA?
- Are there excluded legacy scripts or archive pipelines?
- Which environments must this migration support first?

## Analyze Questions

- Which metrics require strict parity versus tolerance-based parity?
- Are dynamic macro behaviors acceptable to simplify in target code?
- Which lineage gaps are blockers vs known technical debt?
- What data freshness and cutoff assumptions are non-negotiable?
- Which implicit SAS behaviors must be preserved exactly?

## Plan Questions

- What is the priority order of migration waves?
- Is timeline or correctness the stronger constraint for wave 1?
- Do you prefer parallel run or direct cutover?
- Who must sign off each stage gate?
- What are hard no-go conditions for release?

## Design Questions

- Do you prefer SQL-first or Python-first transformation ownership?
- What project structure conventions must be followed?
- How should environment config and secrets be managed?
- What observability signals are mandatory (logs, DQ checks, lineage)?
- Which contracts are externally consumed and cannot break?

## Convert Questions

- Does the restated developer vision match your intent?
- Which naming or boundary decisions should be changed before generation?
- Which complex module should be converted manually in first pass?
- Which known deviations are acceptable in this iteration?
- Which generated artifacts need deeper review before validation?

## Validate Questions

- What parity thresholds define go-live readiness?
- Which mismatches are blocking vs deferrable?
- Is rollback strategy defined and tested?
- Who owns post-cutover monitoring and incident response?
- Should unresolved low-risk gaps move to a follow-up sprint?
