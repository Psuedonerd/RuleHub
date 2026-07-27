# Detailed Model Explanation: McMillan 2021 trivalent TNF–receptor occupancy model

## 1. Model overview

This model isolates sequential binding of three receptors to the three sites of a trivalent TNF molecule. The first, second, and third receptor additions use progressively weaker equilibrium constants, allowing the model to resolve ligand occupancy without including downstream TNF signaling.

## 2. BNGL block inventory

The file contains 17 parameters, 2 molecule types, 2 seed species, 5 active observables, 12 active reversible rules, and 2 active actions. It has no compartments, anchors, or functions; two receptor-dimerization rules and several aggregate observables are commented out.

## 3. Parameters, functions, and rate laws

Concentrations and macroscopic equilibrium constants are converted to molecule counts and microscopic association rates for a one-femtoliter volume. Every binding step shares `koff = 0.01`, while the association rate decreases with occupancy because `K1 < K2 < K3`.

| Parameter group or names | Function in this model |
| --- | --- |
| `Na`, `Vol` | Avogadro conversion and the modeled volume used to translate nanomolar inputs into molecule counts and microscopic association rates. |
| `R0_conc`, `T0_conc`; derived `R0_tot`, `T0_tot` | Initial receptor and TNF concentrations and their converted molecule totals. |
| `K1`, `K2`, `K3` | Macroscopic constants for the first, second, and third receptor-binding events. Values 10, 100, and 1000 encode decreasing affinity as TNF occupancy rises. |
| `k1`, `k2`, `k3` | Corresponding microscopic on-rates derived as `koff/(K*Na*Vol)` with unit conversion; therefore `k1 > k2 > k3`. |
| `Kp`, `Ka`; derived `kp`, `ka` | Parallel/antiparallel receptor-dimerization constants and on-rates. Their rules are commented out, so these parameters do not affect the active model. |
| `koff` | Shared reverse rate for every active TNF–receptor bond. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `R` | 2 | `p`, `a` | None | None | Receptor with potential parallel (`p`) and antiparallel (`a`) interfaces; only `a` binds TNF in active rules because receptor-dimerization rules are disabled. |
| `T` | 3 | `1`, `2`, `3` | None | None | Trivalent TNF ligand with three equivalent-in-form binding sites whose occupancy is tracked explicitly. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial. Free receptor and free TNF are initialized from 20,000 nM and 6,250 nM, respectively, after conversion to molecule counts in a one-femtoliter volume. No complexes are seeded, and the active system contains no receptor dimers independent of TNF.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 3–5 add the first receptor to any TNF site, rules 6–11 add a second receptor to either remaining site for each singly occupied ligand, and rules 12–14 complete occupancy of each doubly bound topology.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 3–5 | Reversible | Free receptor `R.a`; unoccupied TNF site `1`, `2`, or `3`, respectively | Creates/releases one `T.site–R.a` bond using first-binding on-rate `k1` and shared `koff`. | Generates all three singly occupied TNF topologies without privileging a ligand site. |
| 6–7 | Reversible | TNF with site 1 occupied; free receptor `a`; TNF site 2 or 3 | Adds/removes the second receptor at site 2 (rule 6) or site 3 (rule 7) using `k2`/`koff`. | Extends the site-1-bound ligand to either possible doubly occupied form. |
| 8–9 | Reversible | TNF with site 2 occupied; free receptor `a`; TNF site 1 or 3 | Adds/removes the second receptor at site 1 (rule 8) or site 3 (rule 9), again with `k2`/`koff`. | Covers the two extensions of the site-2-bound ligand. |
| 10–11 | Reversible | TNF with site 3 occupied; free receptor `a`; TNF site 1 or 2 | Adds/removes the second receptor at site 1 (rule 10) or site 2 (rule 11), using `k2`/`koff`. | Completes the six ordered routes into the three doubly occupied TNF topologies. |
| 12–14 | Reversible | Doubly occupied TNF missing site 3, 2, or 1, respectively; free receptor `a` | Fills/releases the final open site using the weakest on-rate `k3` and shared `koff`. | Produces fully occupied TNF and makes the third recruitment step less favorable than the first two. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `MonomerReceptor` | Molecule count | Receptors with both `p` and `a` free | Truly unbound receptor, since active rules use `a` and no active rule uses `p`. |
| `freeTNF` | Molecule count | TNF with sites 1–3 all free | Unoccupied ligand pool. |
| `TNF1R` | Molecule count | Sum of the three singly occupied TNF site patterns | Total ligand carrying exactly one receptor, independent of which site is occupied. |
| `TNF2R` | Molecule count | Sum of the three doubly occupied TNF patterns | Total ligand carrying exactly two receptors. |
| `TNF3R` | Molecule count | TNF with all three sites occupied | Fully saturated ligand and endpoint of rules 12–14. |

## 8. Actions and simulation workflow

The active workflow generates the complete network and runs a five-output-step ODE simulation to time 10,000. A truncated-network action and an NFsim command remain commented out, so despite NFsim-oriented metadata the checked-in workflow executes ODEs.

## 9. Technical caveats and ambiguities

- The metadata calls this “TNF signaling,” but the BNGL stops at receptor occupancy and contains no downstream signaling species.
- `K1`, `K2`, and `K3` are described as constants in nM, while their ordering is implemented through derived on-rates with a common off-rate; interpretation as dissociation constants should follow the source's conversion formula.
- Parallel and antiparallel receptor dimerization parameters are inactive because both corresponding rules are commented out.
- Active observables report ligand occupancy, not the size of receptor aggregates beyond one trivalent TNF.
