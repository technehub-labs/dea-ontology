# EO Axiom 01 — Ontological commitments are explicit

**Tenet:** See [../TENETS.md#tenet-1--ontological-commitments-are-explicit](../TENETS.md#tenet-1--ontological-commitments-are-explicit).

**Status:** Phase 1 of [../../change-requests/CR-EO-01.md](../../change-requests/CR-EO-01.md). Full ECF derivation.

## Statement

Every ontology declares, in the ontology itself and in its registry entry, its ontological commitments — upper-ontology choice (if any), axiomatisation depth, reasoning-profile conformance, and the namespace and versioning policy it follows. Implicit assumptions are not permitted; they are flagged for review and either declared or removed.

## ECF derivation

**Principle:** Traceability (every cell traces to an owner, a state, and a set of dependencies) — from [dea-metaframework/framework/principles.md §6](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Construct:** Entity (a bounded, persistent, identifiable unit) — from [dea-metaframework/framework/constructs.md §Entity](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/constructs.md).

**Domain rationale:** The Commitments domain (row 2) is the structural owner of this discipline. Commitments are the precondition for any reasoned assertion — without declared commitments, an ontology cannot be reasoned over reliably (different reasoners will make different assumptions about upper-ontology semantics).

| Stage | Commitment declaration activity | ECF cell |
|-------|--------------------------------|----------|
| Conceive | Identify the ontology's commitments (which upper ontology; which profile; which namespace policy) | Commitments × Conceive (2×1) |
| Design | Specify the `oecc:` header schema (the five declaration fields) | Commitments × Design (2×2) |
| Build | Write the `oecc:` header into the ontology file; declare it in the registry entry | Commitments × Build (2×3) |
| Activate | Enforce the `oecc:` header — promote from `candidate` to `active` only if all five fields are present | Commitments × Activate (2×4) |
| Operate | Continuous commitment audits — silent changes to upper-ontology imports or profile declarations are non-conformant | Commitments × Operate (2×5) |
| Improve | Review commitment fitness — has the chosen upper ontology remained appropriate? Has the profile remained appropriate? | Commitments × Improve (2×6) |
| Retire | Last commit: declaration of the mapping-to-replacement that handles the retire transition | Commitments × Retire (2×7) |

**Cross-cutting guarantee:** Governance × Operate (1×5) — the commitment audit is the continuous-assurance cell that ensures the `oecc:` header remains truthful as the ontology evolves.

## Operational rule

Every EO asset ships an `oecc:` (Ontology Explicit Commitment Contract) header declaring, at minimum:

1. **Upper-ontology declaration** — which upper ontology (BFO / DOLCE / SUMO / EMMO / custom / none), and which version.
2. **Reasoning-profile declaration** — `OWL 2 EL` / `OWL 2 QL` / `OWL 2 RL` / `OWL 2 Full`.
3. **Namespace policy** — the URI prefix the asset uses; the resolver that serves it.
4. **Versioning policy** — semver by default; sector-specific overrides declared in sector-tenets.
5. **Owner** — an actor (per the ECF Actor construct) with the authority to declare commitment changes.

Assets without all five declarations are non-conformant. The `oecc:` header is auditable via the [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) under `asset_class: ontological` (per CR-AR-01 Phase 1).

## Anti-patterns

- **Implicit upper ontology** — an OWL file that imports BFO transitively but never declares it. (Commitments × Build failed.)
- **Undeclared profile** — an ontology whose reasoning cost is unknown because no profile was declared. (Commitments × Activate enforcement failed.)
- **Silent commitment change** — an ontology that switches from OWL 2 EL to OWL 2 RL between versions without a CHANGELOG entry. (Commitments × Operate audit failed.)
- **Ownerless ontology** — an asset without a declared owner is commitment-failed by definition. (Traceability principle violated.)

## Cross-references

- [../TENETS.md §1](../TENETS.md#tenet-1--ontological-commitments-are-explicit) — the tenet.
- [../CHARTER.md §3.1](../CHARTER.md#31-in-scope) — upper-ontology conventions and ontology-engineering practice are in scope.
- [CR-EO-05](../../change-requests/CR-EO-01.md#phase-plan) — Pattern family 1 (`oecc:` header schema) expands this axiom into a reusable pattern.
