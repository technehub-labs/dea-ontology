# CR-EO-02 — Telecom-Operator Enterprise Ontology (Phase 2)

> **Paired with [CR-ESA-02](./CR-ESA-02.md)** — telecom-operator sector content lands in lock-step across both pillars. The two CRs share Phase boundaries and a single phase-pick menu; review both before proceeding.

## Status

- **State:** Proposed — awaiting explicit Proceed / numbered picks.
- **Series tag:** `CR-EO` (Enterprise Ontology).
- **Sibling CR:** `CR-ESA-02` (telecom-operator semantic architecture asset) — same phase boundaries.
- **Predecessors:** `CR-EO-01` (Phase 1 MERGED — `802c183` on `technehub-labs/dea-ontology`); `CR-AR-01` (Phase 1 MERGED — assessment-registry scope extension runtime enables `asset_class: ontological` registration).
- **Successors (parked):** CR-EO-03 (cloud service provider sector — paired with CR-ESA-03); CR-EO-04 (Phase 4 promotion of `dea-catalog-ontologies` — fintech + healthcare); CR-EO-05 (Phase 6 EO Maturity Assessment on `Assessment-Models/dea-catalog-assessment-tools`).
- **Visibility target:** Private at land; promoted to public after this Phase ships (mirroring ESA-1 / EO-1 promotion pattern).

## Primary objective

Deliver the first sector-specific **Enterprise Ontology** under [`technehub-labs/dea-ontology`](https://github.com/technehub-labs/dea-ontology) — for the **telecom operator** sector — with a structural separation between the **business-area** and the **technology-area** of the sector, and within the technology-area an explicit subset of **natively-reusable big topics** that are factored out as cross-sector candidates.

The deliverable establishes the pattern every future sector ontology follows; the telecom choice is the proving ground for the business/tech split.

## Why now

EO-01 Phase 1 grounded the discipline (CHARTER + TENETS + three axioms with ECF derivation). Without a first sector, the discipline has no concrete instantiation. Telecom was chosen as the first pair because it is one of the two sectors with the deepest existing semantic-asset ecosystem in industry (TMForum SID/ODA, GSMA, ONF, 3GPP, MEF, ETSI ZSM) — the reuse-from-existing is highest here, and the cross-sector reuse case for the technology-area is strongest here (telecom radio/RAN, OSS/BSS, charging, identity, network-as-a-service primitives are reused by other sectors).

The user's 2026-08-27 directive specified the architectural split:
> "For the telecom ontology we need to separate business-area from technology-area in order to manage the evolution. Also within technology area there will be the key big topics that are natively reusable, and those that are technology type and domain specific."

This CR implements that directive.

## Architectural principle

**The telecom-operator Enterprise Ontology is organised along two orthogonal axes that cross-cut every tenet extension, every axiom, and every ontology file.**

### Axis 1 — area (business / technology)

| Area | Scope | Audience | Evolution cadence |
|---|---|---|---|
| **business-area** | What the telecom operator *does*: customer-facing products (mobile plans, fixed broadband, enterprise connectivity, IoT, content), commercial relationships (B2C subscribers, B2B enterprises, B2B2X partners), commercial processes (order-to-activate, bill-to-pay, retention), regulatory compliance (telecom licensing, lawful intercept, data sovereignty). | Product managers, commercial architects, regulatory affairs, customer-experience designers. | Slower (months to quarters). Driven by market shifts, regulatory changes, M&A. |
| **technology-area** | How the operator *delivers*: network domains (RAN, transport, core, OSS/BSS), service platforms (charging, identity, policy, messaging), data platforms (CDR/data-lake, real-time analytics), integration patterns (TMForum Open Digital Architecture, ONF SDN controllers), operational concerns (observability, AIOps, assurance). | Network architects, platform engineers, SRE/Ops, integration engineers. | Faster (weeks to months). Driven by vendor releases, standards evolution, technology refresh. |

### Axis 2 — reusability (within technology-area only)

| Subset | Definition | Cross-sector reuse |
|---|---|---|
| **natively-reusable big topics** | Subject matter that is **the same** across multiple sectors and therefore should be authored once and imported (not redefined). Examples: charging / billing primitives, identity / authentication primitives, observability / AIOps primitives, network-as-a-service primitives, message-bus / event-stream primitives. | Strong candidates for promotion to `technehub-labs/eo-shared-technology-primitives` (a sibling repo) or to the parent EO repo's `axioms/` extension. |
| **technology-type** | Subject matter that is **telecom-specific** but reusable within the telecom sector across multiple operators / vendors. Examples: 3GPP-defined network functions (AMF, SMF, UPF), TMForum SID entities (Customer, Service, Resource), GSMA-defined identifiers (IMSI, MSISDN, ICCID). | Sector-internal reuse. Not promoted to cross-sector. |
| **domain-specific** | Single-operator or single-deployment concerns (vendor-specific configuration, deployment-instance identifiers, internal-only topology). | Not reused. Lives only in operator-private extensions. |

### Why the split

1. **Evolution management.** Business-area axioms change on the order of months (new product, regulatory change); technology-area axioms change on the order of weeks (vendor release, standards update). Conflating them creates noisy change logs and forces every business-domain expert to review every technology change. Separating them lets each area evolve at its own cadence.
2. **Reuse factoring.** The natively-reusable subset is the *prime candidate* for cross-sector promotion. Until you explicitly separate it from the technology-type and domain-specific subsets, you cannot factor it out without rewriting. The split is the precondition for reuse.
3. **Cross-discipline discipline.** ESA owns *how meaning is organised*; EO owns *what is formally asserted*. Both pillars must honour the same area + reusability axes — otherwise semantic-layer architecture drifts from formal ontology. CR-ESA-02 mirrors this split.

## Scope

### In scope

- **Phase 2.1 — `sectors/telecom-operator/` directory tree.** Per the `SECTOR-INDEX.md` convention, the directory contains `README.md`, `tenets/`, `ontology/`, `mappings/`, `registry-entry.yaml`. Empty stubs are *not* acceptable: the Phase 2 deliverable is content, not scaffolding.
- **Phase 2.2 — `tenets/` content.** Sector-specific tenet extensions to all three base EO tenets, with full ECF derivation tables mirroring the base-axiom derivation style. The sector tenet extensions explicitly declare:
  - The area + reusability classification of every axiom the sector adds.
  - The upper-ontology choice (or `none`) for the sector.
  - The reasoning-profile declaration for the sector.
  - The cross-sector mapping declarations for natively-reusable big topics.
- **Phase 2.3 — `ontology/` content.** Formal OWL/RDF axiom files, organised by area:
  - `ontology/business/` — business-area axioms (Customer, Product, Service, Order, Bill, Regulatory Obligation, …).
  - `ontology/technology/reusable/` — natively-reusable big topics (charging primitives, identity primitives, observability primitives, …).
  - `ontology/technology/type/` — telecom-type axioms (3GPP NFs, TMForum SID entities, GSMA identifiers, …).
  - `ontology/technology/domain/` — domain-specific stubs (intentionally minimal; placeholder namespace + README only; populated by operator-private extensions).
- **Phase 2.4 — `mappings/` content.** Declared mappings to:
  - TMForum SID / ODA (Information Framework v6+).
  - 3GPP TS 28.x (management / orchestration).
  - GSMA identifiers.
  - (Per the Pick 3 decision below — see Design Constraints.)
- **Phase 2.5 — `oecc:` header.** Every ontology file ships an `oecc:` header declaring upper ontology, profile, namespace, versioning, owner (per Axiom 1).
- **Phase 2.6 — `registry-entry.yaml`.** Registration record for `Assessment-Models/assessment-registry` under `asset_class: ontological`, with `compatibility` block declaring axes per `axes/catalog.yaml` (CR-AR-01 Phase 1).
- **Phase 2.7 — paired ESA sector content.** ESA-02 (CR-ESA-02) ships the parallel semantic-layer architecture for the same sector, with the same area + reusability split reflected in its semantic-layer stack and vocabulary governance.

### Out of scope (handled by sibling CRs)

- ESA-side semantic assets for the same sector → CR-ESA-02 (paired).
- Cloud service provider sector → CR-EO-03 / CR-ESA-03 (next pair).
- `dea-catalog-ontologies` promotion (fintech + healthcare) → CR-EO-04 / CR-ESA-04 (Phase 4).
- Upper-ontology convention document (`patterns/UPPER-ONTOLOGY-CONVENTIONS.md`) → EO-01 Phase 5.
- Ontology-engineering playbook (`BUILD-A-SPECIALIZED-ONTOLOGY.md` full prose) → EO-01 Phase 5.
- EO Maturity Assessment → CR-EO-05 (Phase 6).
- Additional sectors (banking, healthcare, government) → Phase 7.

## Boundaries with sibling CRs

| Concern | Owner | Cross-ref |
|---|---|---|
| Telecom semantic-layer architecture (vocabularies, taxonomy, thesaurus, ontology-as-layer, KG) | ESA-02 | EO-02 axioms implement ESA-02 semantic-layer architecture |
| Telecom formal OWL/RDF axioms + area + reusability split | EO-02 | ESA-02 semantic-layer architecture references EO-02 area split |
| Sector upper-ontology choice + reasoning profile | EO-02 | ESA-02 vocabulary governance respects EO-02 profile |
| Sector lifecycle policy (semver + mapping-to-replacement) | EO-02 | ESA-02 vocabulary lifecycle policy aligns with EO-02 ontology lifecycle |
| Cross-sector reusable technology primitives | EO-02 (extracted to `eo-shared-technology-primitives` or EO `axioms/reusable/` per Pick 4) | ESA-02 vocabulary governance for shared primitives |
| Cross-ontology mappings (TMForum SID, 3GPP, GSMA, …) | EO-02 | Mappings are EO assets (formal); ESA references them in concept-graph topology |
| Registry entry for telecom sector | EO-02 + ESA-02 (paired) | Both register through AR (CR-AR-01) |
| Phase 4 promotion of `dea-catalog-ontologies` | CR-EO-04 / CR-ESA-04 | Telecom patterns inform promotion mechanics |

## Design constraints

1. **Two-axis split is non-negotiable.** Per the 2026-08-27 directive. Every axiom file declares its area (`business-area` or `technology-area`) and its reusability classification (`reusable` / `type` / `domain`) in the `oecc:` header. Violations are non-conformant by definition.
2. **No conflation across the split.** Business-area axioms must not import technology-area axioms; technology-area axioms may import business-area axioms only when the technology serves the business (e.g. a charging-service axiom may reference the Product entity in business-area). The directionality is one-way: business-area is upstream.
3. **Reusable subset is minimal at first.** The initial telecom sector declares at most 5–8 natively-reusable big topics. The selection criteria are explicit (see Phase 2.2 below) — every topic must clear the "used in at least one other sector candidate" bar, or be on a documented roadmap for cross-sector use.
4. **`oecc:` header on every axiom file.** Per Axiom 1 of EO-01 — this is structural, not optional. The `oecc:` header includes the area + reusability classification per Constraint 1.
5. **Lifecycle policy per Axiom 3 of EO-01.** Semver (breaking axiom change = major bump); mapping-to-replacement declared for any deprecation.
6. **Methodical + incremental.** Per the 2026-08-27 directive. Each phase lands in a single PR with full scorecard + verification; no big-bang rollouts.
7. **No content outside the telecom sector.** This CR ships telecom content only. Cloud-service-provider and other sectors are deferred to CR-EO-03+.
8. **Land-as-authored.** This CR doc ships verbatim into `change-requests/CR-EO-02.md`. Sector content lands in paired ESA/EO sector folders; both go through a phase-pick review before any Phase 2.x PR is opened.

## Phasing rule (per the 2026-08-27 directive)

Every Phase 2.x PR for the telecom-operator sector MUST satisfy four explicit, visible conditions before it can be merged. These conditions are non-negotiable; they exist to ensure the area + reusability split and the evolution path are *demonstrable* in every PR, not merely declared in the CR doc.

| # | Condition | What it produces (visible artifact) | Why |
|---|---|---|---|
| **PR-1** | **Visible deliverable.** Each PR ships a checked-in artifact (file, manifest, registry entry, diagram) — not merely a doc or plan. | The diff for the PR is the deliverable; reading the diff shows the split in action. | Splits that live only in docs drift. The artifact is the proof. |
| **PR-2** | **Visible evolution path.** Each PR's `CHANGELOG.md` entry in `sectors/telecom-operator/` shows the prior state → new state delta in tabular form, naming every class / property / vocabulary / axiom that changed. | A row per PR with columns `what`, `where` (ECF cell / axiom / edge kind), `area` (business / technology-reusable / technology-type / technology-domain), `why`, `impact on reusable subset` (none / added / reclassified / deprecated). | Evolution cannot be managed if it is not visible. The table makes the split auditable. |
| **PR-3** | **Visible split.** The PR diff must demonstrate the area + reusability classification for every new artifact: the `oecc:` header on every axiom file; the frontmatter / metadata block on every semantic-layer file; the directory placement under `ontology/{business,technology/{reusable,type,domain}}/`. | One PR cannot add a business-area axiom that *also* declares itself technology-reusable — the split is enforced by the directory + the header, not by convention. | Conflation across the split is the failure mode the directive targets; making it visible prevents it. |
| **PR-4** | **Visible evolution path before content lands.** Phase 2.1 (sector README + sector declaration tenet) explicitly shows the evolution path of the sector: the order in which subsequent phases add content, the reusability-subset boundary that gates Phase 2.3b, the cross-sector candidate list. Phase 2.2 (tenet extensions) explicitly shows the evolution path of each tenet extension: which base axiom it extends, which ECF cells it populates, what triggers a reclassification. | A reader of `sectors/telecom-operator/README.md` + `tenets/` files can answer "what changes next, and why" without reading the CR doc. | Evolution managed visibly is evolution managed. The CR is a planning artifact; the sector folder is the running record. |

### PR-gate checklist (every Phase 2.x PR)

Each PR's description MUST include:

```
## PR-gate checklist (CR-EO-02 / CR-ESA-02 Phasing rule)

- [ ] PR-1 — Visible deliverable: list every new file under `sectors/telecom-operator/...` with a one-line summary
- [ ] PR-2 — Visible evolution path: include a CHANGELOG.md delta table (what / where / area / why / impact on reusable subset)
- [ ] PR-3 — Visible split: confirm every new artifact has its area + reusability classification declared in header / frontmatter / directory placement
- [ ] PR-4 — Visible evolution path before content lands: confirm the previous phase's evolution-path declaration is updated by this PR (cite the file + line)
```

A PR that fails any of the four conditions is non-conformant; review is blocked until the conditions are met. The CR-ESA-02 paired CR applies the same rule to the ESA-side semantic-layer stack.

### Reclassification protocol (Constraint 6 + Phasing rule)

When a sector artifact moves between reusability classifications (e.g. an axiom originally in `technology/type/` is later identified as cross-sector reusable and moves to `technology/reusable/`), the move is itself a Phase. It triggers:

1. A sector-tenet amendment citing the new ECF cells populated.
2. A CHANGELOG.md delta row with `impact on reusable subset: reclassified`.
3. A mapping-to-replacement declaration (Axiom 3 of EO-01) on the original location, so consumers that referenced the old location continue to resolve.
4. A registry entry update (CR-AR-01 §Phase 1 axes coherence).

Reclassification is **not** a silent rename; it is a first-class lifecycle event under the phasing rule.



## Phase plan

Each phase is one future PR. Phase 2.1 lands first; Phase 2.7 (paired ESA content) lands last in this CR cycle.

| Phase | Scope | First deliverable |
|---|---|---|
| **2.1** | `sectors/telecom-operator/` directory + `README.md` declaring the area + reusability split, the upper-ontology choice, and the reasoning-profile declaration | Sector README + `tenets/01-sector-declaration.md` |
| **2.2** | Sector tenet extensions (extensions to base Tenets 1, 2, 3 of EO-01 with ECF derivation, area + reusability classification per tenet) | `tenets/02-tenet-extensions.md` + `tenets/03-upper-ontology-declaration.md` |
| **2.3a** | Business-area ontology axioms (Customer, Product, Service, Order, Bill, Regulatory Obligation) | `ontology/business/*.owl` with `oecc:` headers |
| **2.3b** | Technology-area: reusable big topics (charging primitives, identity primitives, observability primitives, network-as-a-service primitives) | `ontology/technology/reusable/*.owl` with `oecc:` headers |
| **2.3c** | Technology-area: telecom-type axioms (3GPP NFs, TMForum SID entities, GSMA identifiers) | `ontology/technology/type/*.owl` with `oecc:` headers |
| **2.3d** | Technology-area: domain-specific stubs (namespace + README only; populated by operator-private extensions) | `ontology/technology/domain/README.md` + empty stub files |
| **2.4** | Cross-ontology mappings (TMForum SID, 3GPP TS 28.x, GSMA — per Pick 3) | `mappings/*.ttl` (Turtle mappings) |
| **2.5** | Per-file `oecc:` headers across all axiom files (incremental; included in 2.3a–2.3d) | Headers + `oecc-schema.md` reference |
| **2.6** | `registry-entry.yaml` + sector entry on `Assessment-Models/assessment-registry` under `asset_class: ontological` | PR on AR repo (cross-repo) |
| **2.7** | **Paired CR-ESA-02 deliverable** — telecom-operator semantic-layer architecture (vocabularies, taxonomy, thesaurus, concept-graph edges), area + reusability split reflected | Cross-repo PR on `technehub-labs/dea-semantic-architecture` |

**Recommended first phase:** Phase 2.1 (sector README + sector-declaration tenet) — establishes the area + reusability classification framework without committing to specific axiom content yet. Subsequent phases layer content on top.

## Definition of Done for this proposal PR

This proposal PR ships ONLY:

1. Repository state — `technehub-labs/dea-ontology` at Phase 1 merged state (currently `802c183`).
2. `change-requests/CR-EO-02.md` (this doc, verbatim).
3. `change-requests/README.md` row linking this CR.

**Not shipped in this PR:** sector content (lives in Phase 2.1–2.7); mapping declarations (Phase 2.4); registry entry (Phase 2.6); ESA-side sector content (CR-ESA-02, parallel).

## Risks

1. **Over-decomposition of the reusable subset.** Risk: the natively-reusable set becomes so large it is no longer "minimal at first." Mitigation: hard cap of 5–8 topics for Phase 2.3b; selection criteria must clear "used in at least one other sector candidate" bar or be on a documented cross-sector roadmap.
2. **Upper-ontology choice contention.** Risk: the telecom community debates BFO vs DOLCE vs SUMO vs TMForum's own foundational model. Mitigation: sector-tenet `03-upper-ontology-declaration.md` cites the choice and the rationale; federation does not override.
3. **Reusable-extraction thrash.** Risk: as more sectors land, the reusable subset needs re-classification. Mitigation: lifecycle policy (Axiom 3) governs re-classification as a deprecation event with mapping-to-replacement.
4. **Cross-sector mapping scope creep.** Risk: TMForum SID, 3GPP, GSMA, ONF, MEF, ETSI ZSM, ODA — too many to map in one cycle. Mitigation: Phase 2.4 maps the three Pick-3 selections only; additional mappings ship in Phase 7+ per sector.
5. **Drift from ESA side.** Risk: EO-02 area + reusability split diverges from ESA-02 area + reusability split. Mitigation: paired CRs with shared Pick 1 (area + reusability classification scheme); the two sectors mirror each other in concept-graph edges vs formal axioms.
6. **Empty Phase 2.1 perception.** Risk: Phase 2.1 (sector README + sector declaration tenet) looks trivial. Mitigation: the sector README carries the area + reusability classification framework, which is the structural foundation — every subsequent axiom file inherits from it.

## Decision points deferred to later phases

- Specific reusable big topics (Phase 2.3b).
- Upper-ontology choice rationale (Phase 2.2 — `tenets/03-upper-ontology-declaration.md`).
- Mapping-target selection (Phase 2.4 — restricted to Pick 3 picks).
- Owner of the telecom sector ontology (Phase 2.1 — needs a design partner; placeholder `tbd` until a partner is identified).
- Reasoning-profile choice (Phase 2.3a — likely `OWL 2 EL` for telecom-scale; rationale in sector-tenet).

## References

- [CR-EO-01 — Enterprise Ontology umbrella](https://github.com/technehub-labs/dea-ontology/blob/main/change-requests/CR-EO-01.md) (MERGED Phase 1).
- [CR-ESA-02 — Telecom-Operator Semantic Architecture (paired)](./CR-ESA-02.md).
- ECF: [`technehub-labs/dea-metaframework`](https://github.com/technehub-labs/dea-metaframework).
- Concepts Model: [`technehub-labs/dea-concepts-model`](https://github.com/technehub-labs/dea-concepts-model).
- Metamodel: [`technehub-labs/dea-metamodel`](https://github.com/technehub-labs/dea-metamodel) (CR-8; 1.0.0).
- Sibling: CR-EO-01 (Enterprise Ontology grounding — MERGED Phase 1).
- Parallel: CR-AR-01 (assessment-registry scope extension runtime — MERGED Phase 1).
- Predecessor (Phase 4 promotion target): [`technehub-labs/dea-catalog-ontologies`](https://github.com/technehub-labs/dea-catalog-ontologies).
