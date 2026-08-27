# Changelog

## [Unreleased]

### Phase 1 (CR-EO-01) — Grounding docs

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
