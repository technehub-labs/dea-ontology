# Charter — Enterprise Ontology

This document is the canonical grounding of **Enterprise Ontology (EO)** within the OpenDEA federation. It defines EO's core meaning, scope, and the boundary with its sibling discipline (Enterprise Semantic Architecture).

> **Status:** Phase 1 of [CR-EO-01](./change-requests/CR-EO-01.md). Full prose; derived from the Enterprise Concept Framework ([ECF](https://github.com/technehub-labs/dea-metaframework)).

## 1. Core meaning

**Enterprise Ontology (EO)** is the discipline of how an enterprise **formally models its domain** — the choice and integration of upper ontologies (BFO, DOLCE, SUMO, EMMO, custom), ontology-engineering practice (naming, axiomatisation depth, modularisation, reasoning profiles), ontology lifecycle (versioning, deprecation, retirement), and the sector-specific formal ontologies that ground an enterprise's business and technology vocabularies in reasoned logic.

EO is *not* a data-modelling discipline (that is a data-engineering concern). It is *not* a semantic-architecture discipline (that is [Enterprise Semantic Architecture](https://github.com/technehub-labs/dea-semantic-architecture) — ESA's domain). It is *not* a knowledge-graph runtime concern (that is the [OpenDEA runtime](https://github.com/technehub-labs/dea-metamodel)'s domain). It is the **formal-modelling discipline** that decides *what is asserted as true and why* — leaving *how meaning is organised architecturally* to ESA and *how it is executed* to the runtime.

EO is the answer to the question: **when an enterprise has decades of accumulated domain knowledge spread across documents, code, regulatory mandates, and tribal lore — how does it express what is actually true, in a form that machines can reason over, so that conclusions can be checked and contracts can be enforced?**

## 2. Position in OpenDEA

EO sits as one of two conceptual pillars between the OpenDEAM root (`technehub-labs/dea-architecture-framework`) and the conceptual layer (`technehub-labs/dea-concepts-model`). Its sibling is Enterprise Semantic Architecture (ESA). The two pillars instantiate specific dimensions of the architecture:

```
OpenDEAM (root authority)
   │
   ├── ECF (dea-metaframework) — 7×7 axiom-derived matrix
   ├── ESA (dea-semantic-architecture) ← semantic dimension: HOW meaning is organised
   ├── EO (this repo) ← ontological dimension: WHAT is formally asserted
   │
   ├── Concepts Model (dea-concepts-model, CR-CM-001) — the concept graph
   │       │
   │   Metamodel (dea-metamodel, CR-8; 1.0.0) — entity + relationship types
   │       │
   │   Catalog repos (dea-catalog-*) — L1 typed content
   │       │
   │       └── dea-catalog-ontologies ← EO umbrella content (Phase 4 promotion)
   │
   └── Assessment-Models/assessment-registry — registers all OpenDEA-compatible assets
```

EO's outputs reference ESA's patterns (for organisation) and the concepts model's graph (for vocabulary). ESA's patterns cite EO's axioms (for what the patterns must respect). The cycle is intentional and cyclic — each discipline owns one layer of the meaning stack.

## 3. Scope and non-scope

### 3.1 In scope

- **Upper-ontology conventions.** The choice and integration of upper ontologies (BFO, DOLCE, SUMO, EMMO, custom) that ground sector ontologies. EO governs *how* the choice is made and *how* upper-ontology commitments are declared — not which one to pick.
- **Ontology-engineering practice.** Naming conventions, axiomatisation depth (the balance between expressivity and reasoning cost), modularisation (when to split, when to import), reasoning-profile declarations (OWL 2 EL / QL / RL), and profile-conformance tests.
- **Ontology lifecycle.** Versioning (semver vs custom), deprecation (mapping-to-replacement), retirement (archive policy), and the mapping declarations that make lifecycle transitions lossless.
- **Sector ontology patterns.** The structural template by which Enterprise Business Ontology, Enterprise Technology Ontology, and sector-specific ontologies (telecom, cloud, banking, etc.) are derived. Each sector ontology declares its tenet extensions and the ECF cells it populates.
- **Cross-ontology mappings.** Declared mappings between EO assets and external ontologies (schema.org, FIBO, HL7 FHIR-RDF, GS1, ISO 20022, etc.). EO owns the *discipline* of declaring mappings; specific mappings ship as sector content.

### 3.2 Out of scope

- **Architectural patterns for organising meaning** (semantic layers, vocabulary governance, concept graphs) — owned by [ESA](https://github.com/technehub-labs/dea-semantic-architecture).
- **Operational data models** (database schemas, ETL pipelines, table layouts) — data-engineering concern.
- **AI / agent knowledge bases at runtime** — governed by [CR-012 Enterprise Intelligence](https://github.com/technehub-labs/dea-metamodel/blob/main/change-requests/CR-012.md).
- **Knowledge-graph query, traversal, mutation** — the OpenDEA runtime's domain.
- **Specific vocabulary content** — the concepts model's domain (CR-CM-001).
- **Reasoner implementations** (HermiT, Pellet, ELK, etc.) — tooling concern; EO governs *which profile is declared*, not *which reasoner runs it*.

## 4. Relationship to sibling disciplines

| Discipline | Owner | Boundary with EO |
|---|---|---|
| Enterprise Semantic Architecture (ESA) | [`technehub-labs/dea-semantic-architecture`](https://github.com/technehub-labs/dea-semantic-architecture) | EO asserts; ESA organises. EO axioms cite ESA patterns; ESA patterns cite EO axioms. |
| Concepts Model (CM-001) | [`technehub-labs/dea-concepts-model`](https://github.com/technehub-labs/dea-concepts-model) | EO ontology classes reference Concept entries; Concept entries cite EO ontology uses. |
| Metamodel (CR-8) | [`technehub-labs/dea-metamodel`](https://github.com/technehub-labs/dea-metamodel) | EO assets conform to metamodel entity/relationship types (via CM-001). |
| OpenDEAM (root) | [`technehub-labs/dea-architecture-framework`](https://github.com/technehub-labs/dea-architecture-framework) | OpenDEAM cites EO as the authority for the ontological dimension of architecture. |
| Assessment Registry (CR-AR-01) | [`Assessment-Models/assessment-registry`](https://github.com/Assessment-Models/assessment-registry) | EO assets register with the registry under `asset_class: ontological`. |
| Existing ontology content (Phase 4 promotion) | [`technehub-labs/dea-catalog-ontologies`](https://github.com/technehub-labs/dea-catalog-ontologies) | Promoted under EO umbrella as the first sector pair (fintech + healthcare). |

## 5. Authority boundaries

This repository (`technehub-labs/dea-ontology`) is **the** canonical authority for EO within the OpenDEA federation. Concretely:

- **What this repo owns.** The grounding documents (CHARTER, TENETS, axioms), the upper-ontology convention document (Phase 5), the ontology-engineering playbook, the sector content (under sector-content CRs), and the lifecycle governance rules for EO assets.
- **What this repo defers.**
  - Architectural patterns for semantic layers / vocabularies / concept graphs → ESA (referenced, not owned).
  - Concrete concept definitions → Concepts Model (referenced, not owned).
  - Specific OWL/RDF implementation files for sector ontologies → sector-content repos under EO's governance (Phase 2 onward).
  - EO Maturity Assessment → `Assessment-Models/dea-catalog-assessment-tools` (CR-EO-05).

## 6. Reversibility

EO assets are designed for **reversible** evolution. Every asset declares:

- Its **lifecycle status** (`proposed` → `candidate` → `active` → `legacy` → `deprecated` → `retired`).
- Its **deprecation path** — what asset replaces it when retired, and what mapping-to-replacement makes the transition lossless.
- Its **upper-ontology commitment** — which upper ontology (if any) the asset commits to, and what version of that upper ontology it imports.
- Its **reasoning-profile declaration** — which OWL 2 profile (EL / QL / RL / Full) the asset conforms to.

Reversibility is non-negotiable. An ontology that cannot be deprecated losslessly is a liability, not an asset. See [TENETS.md](./TENETS.md) §3 for the operational rule.

## 7. Naming taste

EO vocabulary follows the user's standing preference: **digital-native nomenclature over archaic CMMI-era vocabulary**. Examples:

- **Use** *ontology*, *upper ontology*, *axiom*, *class*, *property*, *restriction*, *reasoning profile*. **Avoid** *knowledge structure*, *taxonomy of concepts* (when describing formal axioms), *vocabulary of terms*.
- **Use** *axiom-derived*, *axiomatisation depth*, *reasoning cost*. **Avoid** *semantic richness*, *inferential power* — these are unmeasurable marketing terms.
- **Use** *sector*, *industry*, *sub-sector* as the three-level sector taxonomy. **Avoid** *vertical*, *domain*, *LOB* (line of business) — these have ambiguous meanings.
- **Use** *activate*, *retire*, *migrate*, *sunset* (the ECF stage names) when describing lifecycle transitions. **Avoid** *decommission*, *deprecate without replacement*, *kill* — these are imprecise.
- **Use** *OWL 2 EL / QL / RL / Full* for reasoning-profile declarations. **Avoid** *lightweight ontology*, *full ontology* — these have no formal meaning.

The full naming glossary lives in [CR-EO-01](./change-requests/CR-EO-01.md) and is refined as sector content lands.

## 8. ECF derivation

EO is axiom-derived from the Enterprise Concept Framework. The derivation chain:

1. **The ECF grounding axiom** — "An enterprise is any bounded entity that persists by exchanging value with its environment." — generates the 7 domains and 7 stages of the ECF matrix.
2. **EO's three tenets** ([TENETS.md](./TENETS.md)) each derive from one or more ECF cells. The derivation tables are in the axiom files.
3. **EO's sector assets** derive from sector tenet extensions (CR-EO-02 onward) and cite the ECF matrix cells they populate.
4. **EO's upper-ontology convention document** (Phase 5) cites the ECF matrix as the structural backbone for sector ontology derivation.

The ECF axiom-derived bottom-up methodology is the reason EO can be **universal** — it fits any enterprise because it derives from what an enterprise is, not from a specific industry's practices.

---

*Phase 1 of [CR-EO-01 — Enterprise Ontology](./change-requests/CR-EO-01.md).*
