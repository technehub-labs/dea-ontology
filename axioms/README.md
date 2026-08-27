# Axioms — Enterprise Ontology

This directory holds the three EO axioms in their own files, each with its full ECF derivation. The axioms are axiom-derived from the [Enterprise Concept Framework](https://github.com/technehub-labs/dea-metaframework); they are not invented.

| # | Axiom | Tenet |
|---|-------|-------|
| 1 | [axiom-01-ontological-commitment.md](./axiom-01-ontological-commitment.md) | Ontological commitments are explicit |
| 2 | [axiom-02-upper-ontology-pluralism.md](./axiom-02-upper-ontology-pluralism.md) | Upper-ontology choice is sector-specific, not federation-mandated |
| 3 | [axiom-03-ontology-lifecycle-governance.md](./axiom-03-ontology-lifecycle-governance.md) | Ontology lifecycle is a first-class discipline |

Each axiom derives from one or more ECF cells (the 7-domain × 7-stage matrix). The derivation is shown explicitly in each axiom file — a sector extension that does not show its ECF derivation is non-conformant by definition.

## How to derive a sector tenet extension

When a sector EO asset (telecom operator, cloud service provider, etc.) needs a sector-specific tenet, the extension MUST:

1. Pick one of the three base axioms to extend.
2. Identify the additional ECF cell(s) the sector populates.
3. Add a sector-specific tenet that derives from those cells, with the same Statement / ECF derivation / Operational rule / Anti-pattern structure as the base axioms.
4. Cite the ECF cells it populates, mirroring the table structure in the base axioms.

Sector extensions live in `sectors/<sector>/tenets/` (Phase 2 onward). They never modify the three base axioms — they extend them.

## How the axioms relate to patterns

The axioms are *what*. The patterns (Phase 5) are *how*. Each axiom file points at the pattern family that operationalises it:

- Axiom 1 → Pattern family 1: `oecc:` header schema (upper-ontology declaration, profile declaration, namespace policy, versioning policy, owner).
- Axiom 2 → Pattern family 2: Upper-ontology convention document (how sector choices are declared, compared, and reconciled via cross-ontology mappings).
- Axiom 3 → Pattern family 3: Lifecycle governance patterns (semver rules, deprecation windows, mapping-to-replacement declaration, archive policy).

Additional pattern families (axiomatisation depth, modularisation, reasoning-profile selection) ship in Phase 5.

## How the axioms relate to the registry

Each sector EO asset registers with the [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) under `asset_class: ontological`. The asset's `compatibility` block (per CR-AR-01 Phase 1) declares the axes it satisfies:

- `governance` (cross-class shared baseline)
- `oecc_header` (Axiom 1 — explicit commitments)
- `upper_ontology_choice` (Axiom 2 — sector-declared)
- `lifecycle_governance` (Axiom 3 — versioned, deprecated, retired)
- `pattern_conformance` (references patterns from `patterns/`)

See [`axes/catalog.yaml`](https://github.com/Assessment-Models/assessment-registry/blob/main/axes/catalog.yaml) for the full per-class axis catalogue.
