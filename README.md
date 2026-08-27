# dea-ontology

> **Canonical grounding repository for Enterprise Ontology (EO) in the OpenDEA federation.**
> Status: **Phase 1 landed** — grounding docs (CHARTER + TENETS + three axioms with ECF derivation). See [`change-requests/CR-EO-01.md`](./change-requests/CR-EO-01.md).

This repository grounds **how an enterprise authors, governs, and consumes formal ontologies** — upper-ontology conventions, ontology-engineering practice, ontology lifecycle, and sector-specific Enterprise Ontologies (e.g. Enterprise Business Ontology, Enterprise Technology Ontology). It is the discipline-of-formal-modelling sibling to [`technehub-labs/dea-semantic-architecture`](https://github.com/technehub-labs/dea-semantic-architecture).

> **Scope split (with ESA):**
> - **EO** owns *what is formally asserted* (OWL/RDF classes, properties, axioms, reasoning).
> - **ESA** owns *how meaning is organised architecturally* (patterns, topologies, governance rules).
>
> EO's outputs cite ESA's patterns. ESA's outputs reference EO's axioms.

## What lives here

- `CHARTER.md` — core meaning, scope, and non-scope of EO within OpenDEA. **(Full prose — Phase 1 landed.)**
- `TENETS.md` — numbered axioms of the discipline, derived from the ECF 7×7 axiom grid. **(Full prose — Phase 1 landed.)**
- `axioms/` — three axiom files, each with derivation table to ECF. **(Full prose — Phase 1 landed.)**
- `patterns/` — reusable Ontology Engineering patterns (upper-ontology conventions, profile declarations, axiomatisation depth, lifecycle). **(Stub index; bodies in Phase 5.)**
- `sectors/` — sector-, industry-, and sub-sector-specific Enterprise Ontologies. **(Index only in Phase 1; first pair — telecom operator + cloud service provider — in Phase 2–3; fintech + healthcare via `dea-catalog-ontologies` promotion in Phase 4.)**
- `BUILD-A-SPECIALIZED-ONTOLOGY.md` — playbook for authoring a new sector Enterprise Ontology. **(Outline in Phase 0; full prose in Phase 5.)**
- `change-requests/` — CRs that shape this repo. CR-EO-01 is the umbrella.
- `GOVERNANCE.md` — contribution rules, CR template, version semantics, ontology-lifecycle policy. **(Stub prose in Phase 5.)**

## Relationship to OpenDEA

EO is one of two conceptual pillars introduced by CR-EO-01 (the other being ESA). Both sit between the OpenDEAM root (`technehub-labs/dea-architecture-framework`) and the conceptual layer (`technehub-labs/dea-concepts-model`), instantiating specific dimensions of the architecture:

```
OpenDEAM (root authority)
   │
   ├── ECF (dea-metaframework) — 7×7 axiom grid
   ├── ESA (dea-semantic-architecture) ← semantic dimension
   ├── EO (this repo) ← ontological dimension
   │
   ├── Concepts Model (dea-concepts-model, CR-CM-001)
   │       │
   │   Metamodel (dea-metamodel, CR-8; 1.0.0)
   │       │
   │   Catalog repos (dea-catalog-*) — L1 typed content
   │       │
   │   └── dea-catalog-ontologies ← Phase 4 promotion target (EO umbrella)
   │
   └── Assessment-Models/assessment-registry (CR-AR-01 scope extension)
```

## Status

**Phase 1 (grounding docs) has landed** — CHARTER + TENETS + three axioms with full ECF derivation are present. Phase 2 onward per `change-requests/CR-EO-01.md`.

**Visibility:** private at land; promoted to public after Phase 1 ships.

## How to contribute

1. Read the umbrella CR: [`change-requests/CR-EO-01.md`](./change-requests/CR-EO-01.md).
2. Read the charter (Phase 1+): [`CHARTER.md`](./CHARTER.md).
3. Propose new sector content via a sector-content CR (e.g. `CR-EO-02` for telecom operator).
4. Phase plan lives in the umbrella CR; sectors land in pairs with ESA.

---

*Established under [CR-EO-01 — Enterprise Ontology](./change-requests/CR-EO-01.md).*
*Predecessor (promotion target, Phase 4): [`technehub-labs/dea-catalog-ontologies`](https://github.com/technehub-labs/dea-catalog-ontologies).*