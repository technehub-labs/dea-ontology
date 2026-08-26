# Change Requests — Enterprise Ontology

| CR | Title | Status | Date | PR |
|----|-------|--------|------|----|
| [CR-EO-01](./CR-EO-01.md) | Enterprise Ontology — umbrella / spec proposal | Proposed | 2026-08-26 | (Phase 0) |
| [CR-EO-01-xref-dea-catalog-ontologies](./CR-EO-01-xref-dea-catalog-ontologies.md) | Cross-ref: CR-EO-01 ↔ dea-catalog-ontologies (Phase 4 promotion candidate) | Proposed | 2026-08-26 | (Phase 0) |

## Pipeline

- **CR-EO-01** — Umbrella / spec proposal. Phase plan lives in the CR doc; each phase is one future PR.
  - Phase 1 — Grounding docs (CHARTER, TENETS, axioms with ECF derivation).
  - Phase 2 — Telecom operator sector (paired with CR-ESA-02).
  - Phase 3 — Cloud service provider sector (paired with CR-ESA-03).
  - Phase 4 — Promote `dea-catalog-ontologies` under EO umbrella (cross-repo PR).
  - Phase 5 — Pattern library + full BUILD-A-SPECIALIZED-ONTOLOGY.md + GOVERNANCE.md.
  - Phase 6 — EO Maturity Assessment (cross-repo PR on `Assessment-Models/dea-catalog-assessment-tools`).
  - Phase 7 — Additional sectors (banking, healthcare, government).

## How to add a CR

1. Author the CR doc following the umbrella CR's structure.
2. Land it in `change-requests/CR-<series>-NN-<slug>.md`.
3. Add a row to the table above.
4. Open a PR.