# Cross-Reference: CR-EO-01 ↔ dea-catalog-ontologies

> **Status:** cross-reference stub — full content lands in Phase 4 of [CR-EO-01](./CR-EO-01.md).

This is a **cross-reference** file documenting the relationship between the EO umbrella repo and the existing `technehub-labs/dea-catalog-ontologies` repo (fintech + healthcare OWL/RDF).

## Primary CR

The full CR lives at: [`change-requests/CR-EO-01.md`](./CR-EO-01.md) in this repo (`technehub-labs/dea-ontology`).

## Sections of CR-EO-01 that affect `dea-catalog-ontologies`

| CR-EO-01 § | Effect on `dea-catalog-ontologies` |
|---|---|
| §Scope | EO umbrella governs ontology practice across the federation; `dea-catalog-ontologies` is the first L1 catalog repo under that governance. |
| §Boundaries with sibling CRs | EO owns formal ontology axioms; `dea-catalog-ontologies` is the *content* repo, not the *governance* repo. |
| §Design constraints §6 | `dea-catalog-ontologies` is a **promotion candidate**, not an asset to copy. Phase 4 promotes it under EO's umbrella via rename + cross-link + governance hand-over. |
| §Phase plan Phase 4 | Promote `dea-catalog-ontologies` under EO umbrella (cross-repo PR). |
| §Definition of Done §10 | This xref file ships in Phase 0; full promotion mechanics ship in Phase 4. |
| §Risks §2 | Overlap-with-catalog-ontologies risk is mitigated by Phase 4 promotion mechanics being explicit (rename + cross-link + governance hand-over, not copy). |

## What this PR does NOT do

- No ontology files in `dea-catalog-ontologies` are touched.
- No rename happens in this PR.
- No governance hand-over happens in this PR.
- No file moves between repos.

## Parking lot (Phase 4 + beyond)

- Phase 4 (cross-repo PR): rename `dea-catalog-ontologies` → `eo-catalog-ontologies-fintech-healthcare` (or chosen name); cross-link from EO + from the renamed repo; declare fintech + healthcare as the first EO sector pair under governed practice.
- Phase 5: governance policy applied to the promoted repo (lifecycle status, review cadence).
- Phase 7: additional sectors (banking, healthcare-oncology, government) ship as new sub-folders in `dea-ontology/sectors/` (or new sibling repos when mature).

## Coordination with the existing repo

Until Phase 4 promotes `dea-catalog-ontologies` under EO, that repo operates unchanged. Its content (fintech + healthcare OWL/RDF) is the natural first-sector pair candidate but is not formally adopted as EO-governed until Phase 4 lands.