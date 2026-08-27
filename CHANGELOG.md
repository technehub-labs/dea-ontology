# Changelog

## [Unreleased]

### Phase 2 proposal (CR-EO-02) — Telecom-Operator Enterprise Ontology

#### Added
- **`change-requests/CR-EO-02.md`** — Telecom-Operator Enterprise Ontology (Phase 2) spec. Implements the 2026-08-27 directive: two-axis split (business-area / technology-area) + technology-area sub-split (natively-reusable big topics / technology-type / domain-specific). Includes the explicit **Phasing rule** (PR-1 visible deliverable, PR-2 visible evolution path, PR-3 visible split, PR-4 visible evolution path before content lands) per the directive's "methodical and incremental" requirement. Paired with CR-ESA-02 (cross-pillar lock-step).

### Pending (per CR-EO-02 phase plan)

- Phase 2.1 — Sector README + sector-declaration tenet (area + reusability framework; no axiom content).
- Phase 2.2 — Sector tenet extensions (extensions to base Tenets 1, 2, 3 with ECF derivation; upper-ontology choice).
- Phase 2.3a — Business-area ontology axioms (Customer, Product, Service, Order, Bill, Regulatory Obligation).
- Phase 2.3b — Technology-area reusable big topics (≤5–8 topics; selection criteria cited).
- Phase 2.3c — Technology-area telecom-type axioms (3GPP NFs, TMForum SID entities, GSMA identifiers).
- Phase 2.3d — Technology-area domain-specific stubs (namespace + README only).
- Phase 2.4 — Cross-ontology mappings (TMForum SID, 3GPP TS 28.x, GSMA — per Pick 3 default).
- Phase 2.5 — Per-file `oecc:` headers (incremental; included in 2.3a–2.3d).
- Phase 2.6 — `registry-entry.yaml` + AR entry (cross-repo PR).
- Phase 2.7 — Paired ESA-02 semantic-layer content (cross-repo PR).

### Phase 1 (CR-EO-01) — Grounding docs — MERGED (`802c183`, PR #1)

#### Added
- **Full `CHARTER.md`** — core meaning, OpenDEA placement, scope and non-scope, sibling relationships, authority boundaries, reversibility, naming taste, ECF derivation (§1–8).
- **Full `TENETS.md`** — three tenets with full ECF derivation tables:
  - Tenet 1 — Ontological commitments are explicit (5 ECF cells; Commitments × {Design, Build, Activate, Operate}, Governance × Operate).
  - Tenet 2 — Upper-ontology choice is sector-specific, not federation-mandated (5 ECF cells; Customer × Design, Product × {Design, Build}, Operations × Improve, Governance × Activate).
  - Tenet 3 — Ontology lifecycle is a first-class discipline (6 ECF cells; Governance × {Conceive, Design, Activate, Improve, Retire}, Operations × Retire ★ high-risk handoff).
- **Three axiom files** with ECF derivation tables + operational rules + anti-patterns:
  - `axioms/axiom-01-ontological-commitment.md`
  - `axioms/axiom-02-upper-ontology-pluralism.md`
  - `axioms/axiom-03-ontology-lifecycle-governance.md`
- **Updated `axioms/README.md`** — derivation table, sector-extension methodology, pattern/registry cross-references.

### Pending (per CR-EO-01 phase plan)

- Phase 2: First sector pair — telecom operator (paired with CR-ESA-02).
- Phase 3: Cloud service provider sector (paired with CR-ESA-03).
- Phase 4: Promote `technehub-labs/dea-catalog-ontologies` (fintech + healthcare OWL/RDF) under EO umbrella (cross-repo PR).
- Phase 5: Pattern library + full `BUILD-A-SPECIALIZED-ONTOLOGY.md` + `GOVERNANCE.md` (incl. upper-ontology convention document, `oecc:` header schema, lifecycle governance rules).
- Phase 6: EO Maturity Assessment (cross-repo PR on `Assessment-Models/dea-catalog-assessment-tools`).
- Phase 7: Additional sectors (banking, healthcare, government).
