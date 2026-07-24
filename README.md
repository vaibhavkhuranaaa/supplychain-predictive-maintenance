# Supply Chain Predictive Maintenance

Status: **building**. This is a pending engineering project, not a production maintenance recommendation system.

The intended workflow uses NASA C-MAPSS turbofan degradation data to build repeatable telemetry ingestion, remaining-useful-life features, a baseline and model comparison, and an equipment-at-risk view tied to operational error trade-offs.

## Data boundary

- Source: NASA C-MAPSS public benchmark data under its published terms.
- Classification: public benchmark telemetry.
- Excluded: customer equipment, proprietary sensor streams, and real maintenance records.
- Record source URL, terms, checksum, split policy, and derived artifacts before publishing evidence.

## Planned architecture

```mermaid
flowchart LR
  A[Versioned C-MAPSS files] --> B[Validated telemetry ingestion]
  B --> C[Unit and regime features]
  C --> D[Baseline and RUL model]
  D --> E[Unit-held-out evaluation]
  E --> F[Equipment-at-risk monitoring view]
```

## Current gate

The draft contract is structurally valid, but first-demo readiness is blocked on provenance, implemented ingestion/modeling, unit-safe evaluation, baseline comparison, tests/CI evidence, monitoring behavior, and deployment evidence. See `docs/STATE.md`, `docs/HANDOFF.md`, and `portfolio/project.json`.

No RUL metric, avoided-downtime claim, deployment URL, or production claim should be added before that evidence exists.
