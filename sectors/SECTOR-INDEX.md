# Sectors — Index

> **Status:** placeholder. Sector content lands in Phase 2–3 (telecom operator + cloud service provider), Phase 4 (`dea-catalog-ontologies` promotion — fintech + healthcare), Phase 7 (banking, healthcare, government).

## Queued sectors

| Sector | Status | Phase |
|---|---|---|
| `telecom-operator/` | queued | Phase 2 (paired with CR-ESA-02) |
| `cloud-service-providers/` | queued | Phase 3 (paired with CR-ESA-03) |
| `fintech/` | queued | Phase 4 (promoted from `dea-catalog-ontologies`) |
| `healthcare/` | queued | Phase 4 (promoted from `dea-catalog-ontologies`) |
| `banking/` | queued | Phase 7 |
| `government/` | queued | Phase 7 |

Each sector sub-folder (when content lands) will contain:

- `README.md` — sector scope, audience, design partners.
- `tenets/` — sector-specific tenets (the base tenets + sector extensions; upper-ontology choice declared here).
- `ontology/` — formal OWL/RDF axiom files for the sector.
- `mappings/` — declared mappings to external ontologies.
- `registry-entry.yaml` — registration record (subject to CR-AR-01 landing).

Sector content is **authored via a sector-content CR** (e.g. `CR-EO-02` for telecom operator), not directly into this repo without a CR.