# Governance

> **Status:** placeholder. Full prose lands in Phase 5 of [CR-EO-01](./change-requests/CR-EO-01.md).

## Outline (Phase 5)

- Contribution rules — who can contribute, how PRs are reviewed.
- CR template — every change to a sector ontology or pattern lands via a CR.
- Version semantics — semver rules; what counts as a breaking change.
- **Ontology lifecycle policy**:
  - `proposed` → candidate (CI green + peer review)
  - `candidate` → `active` (one sector ship + one reference consumer)
  - `active` → `legacy` (superseding ontology registered)
  - `legacy` → `deprecated` (no active consumers for ≥ 1 release)
  - `deprecated` → `retired` (archive policy applied)
- Cross-federation coordination — how EO interacts with the Assessment-Models registry (CR-AR-01), the concepts model (CR-CM-001), and `dea-catalog-ontologies` (Phase 4 promotion).