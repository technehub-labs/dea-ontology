# CR-EO-01 — Enterprise Ontology

## Status

- **State:** Proposed — awaiting explicit "Merge" approval.
- **Series tag:** `CR-EO` (Enterprise Ontology). New umbrella series.
- **Numbering convention:** subsequent EO CRs use compliant numbering (e.g. `CR-EO-02` for sector ontologies, `CR-EO-03` for ontology-engineering governance).
- **Primary repo:** `technehub-labs/dea-ontology` *(new, created in this proposal)*
- **Visibility:** Private at land; promoted to public after Phase 1 ships.
- **Sibling CRs:** `CR-ESA-01` (Enterprise Semantic Architecture — complementary discipline); `CR-AR-01` (assessment-registry scope extension — parallel proposal, different repo).
- **Predecessors:** none — this is a foundational pillar CR.
- **Predecessor (existing content):** `technehub-labs/dea-catalog-ontologies` *(private; fintech + healthcare OWL/RDF ontologies)* — Phase 4 of this CR promotes this repo under EO's umbrella.
- **Successors (parked):** CR-EO-02 (sector ontologies — telecom + cloud service providers, first pair); CR-EO-03 (upper-ontology conventions); CR-EO-04 (ontology lifecycle governance — versioning, deprecation, retirement); CR-EO-05 (EO maturity assessment, lands in `Assessment-Models/dea-catalog-assessment-tools`).

## Primary objective

Establish `technehub-labs/dea-ontology` as the **canonical grounding repository for Enterprise Ontology (EO)** in the OpenDEA federation — defining its core meaning, tenets, axioms, and the means by which sector-, industry-, and sub-sector-specific Enterprise Ontologies (e.g. Enterprise Business Ontology, Enterprise Technology Ontology) are authored and offered.

## Why now

OpenDEAM (the root authority in `technehub-labs/dea-architecture-framework`) governs architecture *layers and building blocks* but is silent on formal ontology practice — the discipline of building, governing, and consuming formal OWL/RDF models with explicit ontological commitments. Three consequences:

1. The existing `dea-catalog-ontologies` (fintech + healthcare) ships raw OWL/RDF with no federation-wide tenet set, no sector-derivation conventions, and no peer-review governance. Adding a new sector ontology requires every author to re-derive conventions.
2. Sector organisations (telecom operators, cloud service providers, banks, healthcare providers) want a *governed* ontology pattern — not free-form OWL. The federation currently lacks it.
3. The "Enterprise Semantic Architecture" discipline (CR-ESA-01) needs a sibling that owns *what is formally asserted* (classes, properties, axioms, reasoning) while ESA owns *how meaning is architecturally organised*. Without this split, the two collapse into one repo and neither is grounded properly.

CR-EO-01 creates the pillar that complements CR-ESA-01; together they replace ad-hoc ontology practice with a single, federated, grounded discipline. Phase 4 of this CR also absorbs `dea-catalog-ontologies` into EO's umbrella — the existing fintech + healthcare content becomes the first sector pair under EO's governance.

## Architectural principle

**EO is a discipline of formal modelling, not a sub-discipline of data engineering.**

EO governs:

- **Upper-ontology conventions** — the choice and integration of upper ontologies (BFO, DOLCE, SUMO, EMMO, custom) that ground sector ontologies.
- **Ontology-engineering practice** — naming conventions, axiomatisation depth, modularisation, reasoning profiles, profile declarations.
- **Ontology lifecycle** — versioning, deprecation, retirement, mapping-to-replacement, archive policy.
- **Sector ontology patterns** — the structural template by which Enterprise Business Ontology, Enterprise Technology Ontology, and sector-specific ontologies are derived.
- **Cross-ontology mappings** — declared mappings between EO assets and external ontologies (e.g. schema.org, FIBO, HL7 FHIR-RDF).

EO does **not** govern:

- **Architectural patterns for organising meaning** (semantic layers, vocabulary governance, concept graphs) — that is ESA's domain.
- **Operational data models** (schemas, tables, ETL pipelines) — that is a data-engineering concern.
- **Knowledge graph runtime** (query, traversal, mutation) — that is the OpenDEA runtime's domain.

The boundary with ESA is sharp: ESA owns *how meaning is organised architecturally*; EO owns *what is formally asserted*. EO's outputs cite ESA's patterns; ESA's outputs reference EO's axioms.

## Scope

In scope:

- Repository scaffold + grounding documents (CHARTER, TENETS, axioms).
- Ontology engineering playbook (`BUILD-A-SPECIALIZED-ONTOLOGY.md`) — the playbook for authoring sector- or industry-specific Enterprise Ontologies.
- Sector ontology index (`sectors/`) with the first two sector entries: `telecom-operator` and `cloud-service-providers`.
- Cross-references to OpenDEAM, ECF (`dea-metaframework`), concepts model (`dea-concepts-model`), metamodel (`dea-metamodel`), the sibling ESA repo, and `dea-catalog-ontologies` (Phase 4 promotion target).
- A `registry-manifest.yaml` declaring registration with `Assessment-Models/assessment-registry` (subject to CR-AR-01 landing).
- Phase 4: promotion of `dea-catalog-ontologies` (fintech + healthcare content) into EO's umbrella as the first sector pair under governed ontology practice.

Out of scope (handled by sibling CRs):

- Architectural patterns for semantic layers / vocabularies / concept graphs (CR-ESA-01).
- Registry scope extension (CR-AR-01).
- Sector ontology *content* (CR-EO-02 and later).
- EO Maturity Assessment (CR-EO-05, lands in `dea-catalog-assessment-tools`).
- Ontology consumer-side tooling (deferred — likely a future CR after Phase 5).

## Boundaries with sibling CRs

| Concern | Owner | Cross-ref |
|---|---|---|
| Formal OWL/RDF axioms (classes, properties, restrictions, reasoning) | EO | — |
| Upper-ontology choice and integration | EO | — |
| Ontology lifecycle (versioning, deprecation, retirement) | EO | — |
| Sector ontology patterns (Enterprise Business Ontology, Enterprise Technology Ontology) | EO | ESA vocabulary-governance pattern applies to ontology terminology |
| Semantic layer architecture (patterns) | ESA | EO axioms implement ESA patterns |
| Vocabulary governance patterns | ESA | EO vocabularies conform to ESA governance rules |
| Concept-graph topology patterns | ESA | EO ontology hierarchies realise ESA concept-graph patterns |
| Registry scope extension (semantic + ontological) | AR | ESA + EO both register through AR |
| Concept definition (CR-CM-001, `dea-concepts-model`) | CM-001 | EO ontology classes reference Concept entries; Concept entries cite EO ontology uses |
| Metamodel entities (CR-8, `dea-metamodel`) | CR-8 | EO assets conform to `dea-metamodel.yaml` entity/relationship types |
| Existing ontology content (fintech, healthcare) | EO absorbs via Phase 4 | `dea-catalog-ontologies` promoted to EO umbrella |

The non-overlap table prevents future phases from duplicating or contradicting ESA, AR, CM-001, or the existing `dea-catalog-ontologies`.

## Design constraints

1. **Grounding is the deliverable, not the ontologies.** The proposal PR ships CHARTER + TENETS + axioms as the "grounding documents." Sector ontology content ships in Phase 2–3. Existing fintech + healthcare ontologies ship into EO's umbrella via Phase 4 (promotion of `dea-catalog-ontologies`).
2. **No dependency on CR-ESA-01 or CR-AR-01 for landing.** This proposal is independently shippable. Cross-references are forward-pointing only; if ESA or AR PRs land first, EO updates its cross-references post-merge.
3. **No architectural patterns.** EO never ships semantic-layer architectures, vocabulary governance rules, or concept-graph topologies — those are ESA's domain. If a phase needs to assert a pattern, it routes to CR-ESA-01.
4. **Tenets are axiom-derived, not invented.** Every EO tenet traces to the ECF 7×7 axiom grid (`dea-metaframework`) or is explicitly flagged as a sector-specific extension (deferred to CR-EO-02).
5. **Sectors are referenced, not authored.** The first two sectors (telecom operator, cloud service provider) appear as **index entries** in Phase 1 with placeholder `sectors/<name>/` sub-folders. Authoring sector ontology content is CR-EO-02.
6. **`dea-catalog-ontologies` is a promotion candidate, not an asset we copy.** Phase 4 of this CR promotes `dea-catalog-ontologies` under EO's umbrella — the existing repo becomes EO's first sector pair without copy/move churn. Promotion mechanics: rename + cross-link + governance hand-over (analogous to how CR-AM-01 paired with the assessment-CI repo).
7. **Registry manifest ships but registration is conditional.** `registry-manifest.yaml` is present at land; actual registration through `Assessment-Models/assessment-registry` waits on CR-AR-01 landing.
8. **Land-as-authored.** This CR doc ships verbatim into `change-requests/CR-EO-01.md`. No silent re-writes.

## Phase plan

Each phase is one future PR. The user picks the first phase after this proposal merges; later phases may shift but the boundaries hold.

| Phase | Scope | First deliverable |
|---|---|---|
| **1** | Grounding docs + axioms (full CHARTER, full TENETS, three axioms, axiom derivation table to ECF) | `CHARTER.md` + `TENETS.md` + `axioms/` |
| **2** | Sector ontology — telecom operator (paired with CR-ESA-02) | `sectors/telecom-operator/` with ontology axiom files + sector-tenets |
| **3** | Sector ontology — cloud service provider (paired with CR-ESA-03) | `sectors/cloud-service-providers/` |
| **4** | Promote `dea-catalog-ontologies` under EO umbrella | Cross-repo PR — `dea-catalog-ontologies` becomes EO's first sector pair (fintech + healthcare) |
| **5** | Upper-ontology conventions + ontology-engineering playbook | `patterns/UPPER-ONTOLOGY-CONVENTIONS.md` + `BUILD-A-SPECIALIZED-ONTOLOGY.md` |
| **6** | EO Maturity Assessment prototype | Lands in `Assessment-Models/dea-catalog-assessment-tools` (cross-repo PR) |
| **7** | Additional sectors (banking, healthcare, gov — queued from Pick 7) | `sectors/banking/`, `sectors/healthcare/`, `sectors/government/` |

**Recommended first phase:** Phase 1 (Grounding docs). Without the grounding, sector ontology content (Phase 2–3) and the `dea-catalog-ontologies` promotion (Phase 4) would lack the foundational tenets they cite.

## Definition of Done for this proposal PR

The proposal PR ships ONLY:

1. Repository `technehub-labs/dea-ontology` (private, scaffolded).
2. `README.md` (top-level index + pointer to this CR + pointer to CHARTER + xref to `dea-catalog-ontologies`).
3. `CHARTER.md` (placeholder section stubs — full prose in Phase 1).
4. `TENETS.md` (placeholder section stubs — full prose in Phase 1).
5. `axioms/` directory with three placeholder axiom files.
6. `patterns/PATTERN-INDEX.md` (placeholder + structural outline).
7. `sectors/SECTOR-INDEX.md` listing telecom-operator + cloud-service-providers as queued (no content yet); fintech + healthcare queued for Phase 4 promotion.
8. `BUILD-A-SPECIALIZED-ONTOLOGY.md` (high-level outline — full prose in Phase 5).
9. `change-requests/CR-EO-01.md` (this doc, verbatim).
10. `change-requests/CR-EO-01-xref-dea-catalog-ontologies.md` (xref to `dea-catalog-ontologies` per the multi-repo landing pattern).
11. `change-requests/README.md` row linking this CR.
12. `GOVERNANCE.md` (placeholder — full prose in Phase 5).
13. `CHANGELOG.md` (initial entry).
14. `.github/workflows/ci.yml` (manifest + structural lint, no OWL validation).

**Not shipped in this PR:** full CHARTER/TENETS prose, axioms derivation table, ontology axiom files, sector ontology content, `dea-catalog-ontologies` promotion, registry entries, EO Maturity Assessment.

## Risks

1. **Drift from ESA.** EO and ESA must remain complementary; if EO axioms emerge that contradict ESA patterns, federation convergence suffers. Mitigation: Phase 1 in each repo explicitly cross-references the other; CR-EO-02 / CR-ESA-02 are *paired* sector-content CRs.
2. **Overlap with `dea-catalog-ontologies`.** The existing repo already houses fintech + healthcare OWL/RDF. EO must clearly own the governance pattern; `dea-catalog-ontologies` becomes a content repo under that governance. Mitigation: Phase 4 promotion mechanics are explicit; promotion is a rename + cross-link + governance hand-over, not a copy.
3. **Upper-ontology choice politics.** Picking BFO vs DOLCE vs SUMO vs custom is contested in the ontology community. Mitigation: Phase 5 of this CR ships a *convention document*, not a mandate; each sector ontology can declare its upper-ontology choice in its sector-tenets. The CHARTER explicitly does not impose a single upper ontology.
4. **OWL profile ambiguity.** OWL 2 has three profiles (EL, QL, RL) with different reasoning trade-offs. Mitigation: Phase 5 playbook includes a profile-selection guide based on use-case characteristics.
5. **Empty Phase 0 perception.** A proposal PR with placeholders can look like a shell. Mitigation: the README explicitly states "this is the proposal PR; full grounding lands in Phase 1" and points at the CR doc's Definition of Done.

## Decision points deferred to later phases

- Tenet wording and final axiom set (Phase 1).
- Sector partner selection for telecom + cloud (Phase 2–3 — needs design partners).
- Upper-ontology conventions (Phase 5 — needs community input).
- EO Maturity scoring model (Phase 6 — separate CR on `dea-catalog-assessment-tools`).
- Cross-federation ranking of sectors (Phase 7 — needs user input).

## References

- OpenDEAM: `technehub-labs/dea-architecture-framework` (root authority).
- ECF: `technehub-labs/dea-metaframework` (axiom grid source).
- Concepts Model: `technehub-labs/dea-concepts-model` (CR-CM-001).
- Metamodel: `technehub-labs/dea-metamodel` (CR-8; 1.0.0).
- Sibling: CR-ESA-01 (Enterprise Semantic Architecture).
- Predecessor (promotion candidate, Phase 4): `technehub-labs/dea-catalog-ontologies` (fintech + healthcare OWL/RDF).
- Parallel: CR-AR-01 (assessment-registry scope extension).