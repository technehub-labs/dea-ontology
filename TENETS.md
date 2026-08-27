# Tenets — Enterprise Ontology

EO tenets are **axiom-derived**, not invented. Every tenet traces to one or more cells of the [ECF](https://github.com/technehub-labs/dea-metaframework) 7×7 matrix, or is explicitly flagged as a sector-specific extension (deferred to [CR-EO-02](./change-requests/CR-EO-01.md#phase-plan) onward).

> **Status:** Phase 1 of [CR-EO-01](./change-requests/CR-EO-01.md). Three tenets with full ECF derivation.

---

## Tenet 1 — Ontological commitments are explicit

**Statement.** Every ontology declares, in the ontology itself and in its registry entry, its ontological commitments — upper-ontology choice (if any), axiomatisation depth, reasoning-profile conformance, and the namespace and versioning policy it follows. Implicit assumptions are not permitted; they are flagged for review and either declared or removed.

**Axiom source.** This tenet derives from the **ECF design principle of Traceability** (every cell traces to an owner, a state, and a set of dependencies) plus the **formal Construct of Entity** (a bounded, persistent, identifiable unit). An ontology is a collection of entities (classes, properties, restrictions); every entity's commitments must be traceable to a declared upper ontology, a declared reasoning profile, and a declared lifecycle status. The Commitments domain (row 2) is the structural owner of this discipline — commitments are the precondition for any reasoned assertion.

| ECF cell | Contribution to Tenet 1 |
|---|---|
| Commitments × Design (cell 2×2) | The commitments for an ontology are designed — upper-ontology choice, profile declaration, namespace policy are explicit decisions, not defaults. |
| Commitments × Build (cell 2×3) | The commitments are built into the ontology header (every EO asset ships an `oecc:` header declaring upper ontology + profile + namespace + version). |
| Commitments × Activate (cell 2×4) | Commitments become enforceable at the activate stage — ontology assets without an `oecc:` header cannot be promoted from `candidate` to `active`. |
| Commitments × Operate (cell 2×5) | Continuous operation requires ongoing commitment audits — silent changes to upper-ontology imports or profile declarations are non-conformant. |
| Governance × Operate (cell 1×5) | Cross-cutting guarantee: the commitments are auditable via the assessment-registry's `status` field and `notes` block. |

**Operational rule.** Every EO asset ships an `oecc:` (Ontology Explicit Commitment Contract) header declaring, at minimum:

1. **Upper-ontology declaration** — which upper ontology (BFO / DOLCE / SUMO / EMMO / custom / none), and which version.
2. **Reasoning-profile declaration** — `OWL 2 EL` / `OWL 2 QL` / `OWL 2 RL` / `OWL 2 Full`.
3. **Namespace policy** — the URI prefix the asset uses; the resolver that serves it.
4. **Versioning policy** — semver by default; sector-specific overrides declared in sector-tenets.
5. **Owner** — an actor (per the ECF Actor construct) with the authority to declare commitment changes.

Assets without all five declarations are non-conformant. The `oecc:` header is auditable via the [Assessment-Models/assessment-registry](https://github.com/Assessment-Models/assessment-registry) under `asset_class: ontological` (per CR-AR-01 Phase 1).

**Anti-pattern.** Implicit upper ontology (an OWL file that imports BFO transitively but never declares it). Undeclared profile (an ontology whose reasoning cost is unknown because no profile was declared). Silent commitment change (an ontology that switches from OWL 2 EL to OWL 2 RL between versions without a CHANGELOG entry). Ownerless ontology (an asset without a declared owner is commitment-failed by definition).

---

## Tenet 2 — Upper-ontology choice is sector-specific, not federation-mandated

**Statement.** The choice of upper ontology (whether to use BFO, DOLCE, SUMO, EMMO, or a custom upper ontology) is a sector decision, not an EO federation mandate. Each sector ontology declares its choice in its sector-tenets; EO provides the convention by which the choice is made and documented, not the choice itself.

**Axiom source.** This tenet derives from the **ECF design principle of Orthogonality** (the two axes are independent) plus the **ECF design principle of Contextual Locality** (every cell is meaningful in its local context; federation-wide mandates that ignore local context collapse diversity). The upper-ontology question is the most contested in the ontology community — the principled position is to refuse to impose federation-wide and instead govern *how the choice is declared*.

| ECF cell | Contribution to Tenet 2 |
|---|---|
| Customer × Design (cell 4×2) | The sector's customers (domain experts, regulators, integration partners) inform the upper-ontology choice — BFO for biomedical, DOLCE for cognitive/perceptual, SUMO for general-purpose, custom for sectors with no fit. |
| Product × Design (cell 5×2) | The catalog & specs stage is where the upper-ontology choice is declared in the sector's tenet extensions. |
| Product × Build (cell 5×3) | The choice becomes structural — the sector ontology's axioms are written in terms of the chosen upper ontology's primitives. |
| Operations × Improve (cell 6×6) | Operational improvement is the cell where upper-ontology fit is reviewed — if a sector finds its upper-ontology choice no longer fits, the sector-tenet declares a migration plan (not a federation-wide mandate reversal). |
| Governance × Activate (cell 1×4) | Cross-cutting: the choice is enforceable via the sector-tenet; federations do not override sector choices. |

**Operational rule.** Every sector ontology ships a `sectors/<name>/tenets/` directory whose first tenet is the **upper-ontology declaration**. The declaration cites the ECF cells the sector populates, names the upper ontology (or `none` if no upper ontology is used), and names the version pinned. The federation never overrides a sector's declared choice; cross-sector mapping is the place where choice-differences are reconciled (and that itself is an explicit EO asset — see Tenet 3 lifecycle and the cross-ontology mappings concern).

**Anti-pattern.** Federation-imposed upper ontology (EO declaring "all ontologies MUST use BFO" — collapses sector autonomy; violates Contextual Locality). Undeclared upper ontology (an OWL file that uses primitives from multiple upper ontologies without declaring which one it commits to — the worst of both worlds). Hidden upper-ontology drift (a sector that silently swaps SUMO for BFO between versions without a sector-tenet amendment).

---

## Tenet 3 — Ontology lifecycle is governed

**Statement.** Ontologies are versioned, deprecated, mapped-to-replacement, and retired; they are never silently evolved. The lifecycle policy is explicit, owned, and auditable; lifecycle transitions are mapped-not-broken so that reasoning continuity is preserved across transitions.

**Axiom source.** This tenet derives from the **ECF design principle of Lifecycle continuity** (every business object passes through every stage) plus the **ECF design principle of Reversibility** (every object can be deprecated and replaced without loss). Ontology lifecycle is the application of these principles to formal axioms specifically — when an ontology is deprecated, every consumer that imports it must have a mapping-to-replacement so that reasoning over the new ontology produces equivalent conclusions.

| ECF cell | Contribution to Tenet 3 |
|---|---|
| Governance × Conceive (cell 1×1) | The policy intent for ontology lifecycle is set here — an ontology owner commits to a lifecycle policy (semver, deprecation window, mapping-to-replacement rules) before adoption. |
| Governance × Design (cell 1×2) | The controls design specifies versioning rules (major.minor.patch; what constitutes a breaking change), deprecation policy (mapping declaration rules, advance-notice windows), retirement policy (archive location, retention period). |
| Governance × Activate (cell 1×4) | The enforce step is when an ontology's lifecycle policy goes live — ontologies without active lifecycle enforcement are not governed. |
| Governance × Improve (cell 1×6) | Risk review includes auditing ontologies for silent evolution (the most common lifecycle failure mode — axioms added without a version bump). |
| Governance × Retire (cell 1×7) | Retirement of an ontology follows the same lifecycle discipline as retirement of any other enterprise object — mapping-to-replacement is mandatory; archive policy is declared. |
| Operations × Retire (cell 6×7, ★ high-risk handoff) | The moment an ontology is retired is a high-risk handoff — consumers that import the retired ontology without a mapping-to-replacement will fail at reasoning time. |

**Operational rule.** Every EO asset declares:

1. **Lifecycle policy** — the path through the six state values (`proposed` → `candidate` → `active` → `legacy` → `deprecated` → `retired`), with explicit transitions and who can declare each transition.
2. **Versioning policy** — semver by default; breaking axiom changes require a major version bump; reasoning-affecting changes (axiom additions or removals) require a major version bump; documentation-only changes require a patch bump.
3. **Deprecation path** — what asset replaces it when retired; what mapping-to-replacement makes the transition lossless for consumers.
4. **Mapping-to-replacement declaration** — when an ontology is deprecated or retired, a mapping ontology is published in parallel declaring how each class/property in the deprecated ontology maps to the replacement.
5. **Owner** — an actor with the authority to declare lifecycle transitions.

The asset's lifecycle status is auditable via the assessment-registry's `status` field. The asset's deprecation path is in its `notes` block. The asset's owner is declared in its `components` or `notes` block.

**Anti-pattern.** Silent axiom evolution (adding or removing axioms without a version bump — Lifecycle continuity violated). Silent deprecation (marking an ontology deprecated without a mapping-to-replacement — Operations × Retire high-risk handoff failed). Unversioned ontology (an ontology without a declared version is lifecycle-failed by definition). Ownerless ontology (an asset without a declared owner cannot have its lifecycle transitions governed).

---

## Sector extensions (forward pointer)

Sector-specific tenets are added in [CR-EO-02](./change-requests/CR-EO-01.md#phase-plan) (telecom operator) and [CR-EO-03](./change-requests/CR-EO-01.md#phase-plan) (cloud service provider), then [CR-EO-04](./change-requests/CR-EO-01.md#phase-plan)+ for additional sectors (banking, healthcare, government). Each sector tenet extends one or more of the three base tenets with explicit ECF derivation (mirroring the table structure above) and flags the cell it populates.

---

*Phase 1 of [CR-EO-01 — Enterprise Ontology](./change-requests/CR-EO-01.md).*
