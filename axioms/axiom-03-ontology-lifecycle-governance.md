# EO Axiom 03 — Ontology lifecycle is a first-class discipline

**Tenet:** See [../TENETS.md#tenet-3--ontology-lifecycle-is-governed](../TENETS.md#tenet-3--ontology-lifecycle-is-governed).

**Status:** Phase 1 of [../../change-requests/CR-EO-01.md](../../change-requests/CR-EO-01.md). Full ECF derivation.

## Statement

Ontologies are versioned, deprecated, mapped-to-replacement, and retired; they are never silently evolved. The lifecycle policy is explicit, owned, and auditable; lifecycle transitions are mapped-not-broken so that reasoning continuity is preserved across transitions.

## ECF derivation

**Principle:** Lifecycle continuity (every business object passes through every stage) — from [dea-metaframework/framework/principles.md §3](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Principle:** Reversibility (every object can be deprecated and replaced without loss) — from [dea-metaframework/framework/principles.md §5](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Construct:** Event (a state transition with a timestamp and an actor) — from [dea-metaframework/framework/constructs.md §Event](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/constructs.md).

**Domain rationale:** The Governance domain (row 1) is the structural owner of the lifecycle policy because governance is the precondition for boundedness — and an ontology without a bounded lifecycle is not an ontology, it is a soup that drifts.

| Stage | Lifecycle-governance activity | ECF cell |
|-------|-------------------------------|----------|
| Conceive | Policy intent: declare the ontology's purpose + ownership + lifecycle policy (semver, deprecation window, mapping-to-replacement rules) | Governance × Conceive (1×1) |
| Design | Controls design: versioning rules (what constitutes a breaking change), deprecation policy (mapping declaration rules, advance-notice windows), retirement policy (archive location, retention period) | Governance × Design (1×2) |
| Build | Compliance build: authoring the ontology's first `candidate` version, with the lifecycle policy declared | Governance × Build (1×3) |
| Activate | Enforce: the ontology's lifecycle policy goes live; ontology assets without active lifecycle enforcement are not governed | Governance × Activate (1×4) |
| Operate | Assurance: ongoing audits for silent evolution (axioms added or removed without a version bump — the most common lifecycle failure mode) | Governance × Operate (1×5) |
| Improve | Risk review: detect silent evolution; flag ontology lifecycle failures; review deprecation windows | Governance × Improve (1×6) |
| Retire | Policy retire: mapping-to-replacement is mandatory before the retire transition; archive policy is declared | Governance × Retire (1×7) |

**The retire high-risk handoff:** Operations × Retire (cell 6×7, ★) — the moment an ontology is retired is a high-risk handoff. Consumers that import the retired ontology without a mapping-to-replacement will fail at reasoning time. The mapping ontology must be published in parallel with the `deprecated` status change, so consumers have time to migrate before the `retired` transition.

**State values** (from [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) CR-AM-11 §26 + CR-AR-01 Phase 1):
`proposed` → `candidate` → `active` → `legacy` → `deprecated` → `retired`.

## Operational rule

Every EO asset declares:

1. **Lifecycle policy** — the path through the six state values, with explicit transitions and who can declare each transition (the actor with lifecycle authority).
2. **Versioning policy** — semver by default; breaking axiom changes require a major version bump; reasoning-affecting changes (axiom additions or removals) require a major version bump; documentation-only changes require a patch bump.
3. **Deprecation path** — what asset replaces it when retired; what mapping-to-replacement makes the transition lossless for consumers.
4. **Mapping-to-replacement declaration** — when an ontology is deprecated or retired, a mapping ontology is published in parallel declaring how each class/property in the deprecated ontology maps to the replacement.
5. **Owner** — an actor with the authority to declare lifecycle transitions.

The asset's lifecycle status is auditable via the assessment-registry's `status` field. The asset's deprecation path is in its `notes` block. The asset's owner is declared in its `components` or `notes` block.

## Anti-patterns

- **Silent axiom evolution** — adding or removing axioms without a version bump. (Lifecycle continuity principle violated; Governance × Operate assurance failed.)
- **Silent deprecation** — marking an ontology deprecated without a mapping-to-replacement. (Operations × Retire high-risk handoff failed.)
- **Unversioned ontology** — an ontology without a declared version is lifecycle-failed by definition. (Governance × Conceive policy intent failed.)
- **Ownerless ontology** — an asset without a declared owner cannot have its lifecycle transitions governed. (Traceability principle violated.)
- **Retire-without-archive** — retiring an ontology without declaring its archive location and retention period. (Reversibility principle violated.)

## Cross-references

- [../TENETS.md §3](../TENETS.md#tenet-3--ontology-lifecycle-is-governed) — the tenet.
- [../CHARTER.md §6](../CHARTER.md#6-reversibility) — reversibility (ontology lifecycle enables asset reversibility).
- [CR-EO-05](../../change-requests/CR-EO-01.md#phase-plan) — Pattern family 3 (lifecycle governance patterns) expands this axiom.
