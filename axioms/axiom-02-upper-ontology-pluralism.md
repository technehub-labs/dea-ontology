# EO Axiom 02 — Upper-ontology choice is sector-specific, not federation-mandated

**Tenet:** See [../TENETS.md#tenet-2--upper-ontology-choice-is-sector-specific-not-federation-mandated](../TENETS.md#tenet-2--upper-ontology-choice-is-sector-specific-not-federation-mandated).

**Status:** Phase 1 of [../../change-requests/CR-EO-01.md](../../change-requests/CR-EO-01.md). Full ECF derivation.

## Statement

The choice of upper ontology (whether to use BFO, DOLCE, SUMO, EMMO, or a custom upper ontology) is a sector decision, not an EO federation mandate. Each sector ontology declares its choice in its sector-tenets; EO provides the convention by which the choice is made and documented, not the choice itself.

## ECF derivation

**Principle:** Orthogonality (the two axes are independent) — from [dea-metaframework/framework/principles.md §4](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Principle:** Contextual Locality (every cell is meaningful in its local context; federation-wide mandates that ignore local context collapse diversity) — from [dea-metaframework/framework/principles.md §7](https://github.com/technehub-labs/dea-metaframework/blob/main/framework/principles.md).

**Cross-construct rationale:** The upper-ontology question is the most contested in the ontology community (BFO for biomedical realism, DOLCE for cognitive/perceptual distinction, SUMO for general-purpose coverage, EMMO for materials science, custom when no fit). The principled position is to refuse to impose federation-wide and instead govern *how the choice is declared* — letting the Customer domain (row 4) and Product domain (row 5) drive the sector-level decision.

| ECF cell | Contribution to Axiom 2 |
|---|---|
| Customer × Design (cell 4×2) | The sector's customers (domain experts, regulators, integration partners) inform the upper-ontology choice. |
| Product × Design (cell 5×2) | The catalog & specs stage is where the upper-ontology choice is declared in the sector's tenet extensions. |
| Product × Build (cell 5×3) | The choice becomes structural — the sector ontology's axioms are written in terms of the chosen upper ontology's primitives. |
| Operations × Improve (cell 6×6) | Operational improvement is the cell where upper-ontology fit is reviewed — if a sector finds its choice no longer fits, the sector-tenet declares a migration plan (not a federation-wide mandate reversal). |
| Governance × Activate (cell 1×4) | Cross-cutting: the choice is enforceable via the sector-tenet; federations do not override sector choices. |

**The federated-pluralism guarantee:** Contextual Locality (§7) is the principle that the federation respects sector-level decisions without imposing federation-wide uniformity. Cross-sector reconciliation happens via *mappings* (declared explicitly between sector ontologies) — not via mandate reversal.

## Operational rule

Every sector ontology ships a `sectors/<name>/tenets/` directory whose first tenet is the **upper-ontology declaration**. The declaration cites the ECF cells the sector populates, names the upper ontology (or `none` if no upper ontology is used), and names the version pinned.

The federation never overrides a sector's declared choice. Cross-sector mapping is the place where choice-differences are reconciled — and that itself is an explicit EO asset:

- **Mapping ontology** — for each pair of sector ontologies with overlapping scope, a third ontology declares the equivalence (`owl:equivalentClass`) or approximation (`skos:relatedMatch`) between concepts.
- **Mapping declaration is bidirectional** — both sectors must declare the mapping in their sector-tenets, citing the mapping ontology URI.
- **Mapping is auditable** — the assessment-registry records which mappings are declared between which sector ontologies, with lifecycle status (`active` / `deprecated`).

## Anti-patterns

- **Federation-imposed upper ontology** — EO declaring "all ontologies MUST use BFO" — collapses sector autonomy and violates Contextual Locality.
- **Undeclared upper ontology** — an OWL file that uses primitives from multiple upper ontologies without declaring which one it commits to — the worst of both worlds (no sector authority, no federation authority).
- **Hidden upper-ontology drift** — a sector that silently swaps SUMO for BFO between versions without a sector-tenet amendment. (Governance × Activate enforcement failed.)
- **Cross-sector imposition** — one sector declaring that other sectors must adopt its upper ontology. The federation has no authority to enforce this; cross-sector mapping is the only federation-blessed reconciliation mechanism.

## Cross-references

- [../TENETS.md §2](../TENETS.md#tenet-2--upper-ontology-choice-is-sector-specific-not-federation-mandated) — the tenet.
- [../CHARTER.md §3.1](../CHARTER.md#31-in-scope) — upper-ontology conventions and cross-ontology mappings are in scope.
- [CR-EO-05](../../change-requests/CR-EO-01.md#phase-plan) — Pattern family 2 (upper-ontology convention document) expands this axiom.
