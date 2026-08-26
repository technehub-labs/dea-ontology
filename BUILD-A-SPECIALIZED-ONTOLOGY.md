# Build a Specialized Ontology

> **Status:** outline only. Full playbook lands in Phase 5 of [CR-EO-01](./change-requests/CR-EO-01.md).

## Outline

1. **Choose the sector** — name it; scope it; identify the design partners.
2. **Derive sector tenets** — start from the three base tenets + ECF axioms; add sector-specific tenets with explicit ECF derivation; declare the upper-ontology choice.
3. **Choose the ontology profile** — OWL 2 EL / QL / RL based on use-case characteristics (reasoning cost vs expressivity).
4. **Author the sector ontology** — formal OWL/RDF axioms conforming to the EO axiom-naming conventions.
5. **Author cross-ontology mappings** — declared mappings to schema.org / FIBO / HL7 FHIR-RDF / etc.
6. **Author sector content modules** — modularise per the modularisation pattern.
7. **Register** — `registry-entry.yaml` + submit a sector-content CR (e.g. `CR-EO-02`).
8. **Review** — peer review per `GOVERNANCE.md` (Phase 5).

Phase 5 ships the full prose for all 8 steps with worked examples from the telecom operator sector (Phase 2).