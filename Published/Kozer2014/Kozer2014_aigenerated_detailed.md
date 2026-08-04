# Detailed Model Explanation: Kozer 2014 EGFR tetramer and Grb2 recruitment model

## 1. Model overview

This model links EGF occupancy to EGFR ectodomain crosslinking, opening and association of cytosolic tails, receptor phosphorylation, and Grb2 recruitment. It explicitly represents alternative ligand states and ring-closing steps within four-receptor assemblies so tetramer topology changes the effective association rate.

## 2. BNGL block inventory

The file contains 36 parameters, 3 molecule types, 3 free seed species, 16 rules, 15 observables, and 2 actions. It has no enclosing model block, compartments, anchors, or functions; network generation caps EGF and EGFR stoichiometry at four.

## 3. Parameters, functions, and rate laws

Concentration and cell-volume parameters convert experimental pool sizes and bimolecular rates into molecular units. Binding rates are separated by ligand/oligomer context, while `chi_r` boosts only ring-closing events whose partners are already held in one assembly.

| Parameter group or names | Function in this model |
| --- | --- |
| `NA`, `f`, `V`, `cellDen`, `Vo`; `LT`, `RT`, `GT` | Unit/volume conversion and initial EGF, EGFR, and Grb2 pools. |
| `K11`, `k11f`, `k11r` | EGF binding to EGFR not ectodomain-crosslinked to another receptor. |
| `K21`, `k21f`, `k21r`; `K22`, `k22f`, `k22r` | First and second EGF-binding events on an ectodomain-linked receptor pair; the second ligand has a distinct, weaker context. |
| `L20`, `l20f`, `l20r`; `L21`, `l21f`, `l21r`; `L22`, `l22f`, `l22r` | Ectodomain crosslinking for zero, one, or two EGF-occupied receptors, respectively. |
| `k_o`, `k_c` | Ligand-dependent cytosolic-tail opening and ligand-independent closing. |
| `kaf`, `kar` | Association/dissociation of two open EGFR cytosolic tails. |
| `chi_r` | Effective-concentration multiplier for closing an ectodomain or tail edge inside a preassembled four-receptor topology. |
| `kp`, `kdp` | EGFR phosphorylation across a tail pair and global dephosphorylation. |
| `KDg`, `kmg`; derived `kpg` | Grb2–phospho-EGFR affinity, dissociation, and volume-scaled association. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `EGF` | 1 | `rec` | None | None | Ligand whose receptor-facing site occupies EGFR `lig`. |
| `EGFR` | 4 | `back`, `lig`, `cd`, `Y` | `cd: c, o`; `Y: u, p` | None | Receptor combining ectodomain crosslinking (`back`), ligand binding, tail conformation/association (`cd`), and a phosphorylatable Grb2 docking site (`Y`). |
| `Grb2` | 1 | `SH2` | None | None | Adaptor recruited specifically to phosphorylated EGFR `Y~p`. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and starts with free EGF, closed unphosphorylated EGFR, and free Grb2. Pool expressions correspond to the modeled fraction of a cell and its surrounding fluid; no receptor dimers, tetramers, phospho-EGFR, or Grb2 complexes are seeded.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–9 couple EGF occupancy to ectodomain edges, including closure inside tetramers. Rules 10–13 open and connect cytosolic tails, and rules 14–16 turn tail association into phosphorylation and Grb2 loading.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–3 | Reversible | EGF `rec` and EGFR `lig`; rule 1 uses non-crosslinked EGFR, rule 2 the first ligand on an unliganded `back` dimer, rule 3 the second ligand | Creates/releases `rec–lig` using `k11f/k11r`, `k21f/k21r`, or `k22f/k22r`, respectively. | Makes ligand affinity depend on ectodomain assembly and prior occupancy rather than treating all sites identically. |
| 4–6 | Reversible | Two EGFR `back` sites with zero, one, or two bound EGF molecules, respectively | Creates/releases the ectodomain `back–back` edge using the matching `l20`, `l21`, or `l22` forward/reverse pair. | Produces the three ligand-defined ectodomain dimer classes from freely encountering receptors. |
| 7–9 | Reversible | Two still-free `back` sites inside a four-EGFR assembly already tethered by tail and ectodomain edges; zero, one, or two target receptors are liganded | Closes/opens the remaining ectodomain edge with `chi_r*l20f`, `chi_r*l21f`, or `chi_r*l22f`; reverse rates are unchanged. | Converts open four-receptor chains into rings and represents their high intracomplex encounter probability. |
| 10–11 | One-way | EGFR `cd`; rule 10 additionally requires bound ligand | Rule 10 changes `cd: c → o` at `k_o`; rule 11 changes any `o → c` at `k_c`. | Couples ligand to tail exposure while allowing spontaneous closure to oppose activation. |
| 12–13 | Reversible | Two open EGFR `cd` sites; rule 13 places the free pair inside a four-receptor assembly | Creates/releases a `cd–cd` tail edge at `kaf/kar`; intratetramer closure multiplies only the forward rate by `chi_r`. | Builds tail dimers in free encounters or closes the second tail edge within a tetramer. |
| 14 | One-way | Two EGFR molecules joined through open tails; one receptor has `Y~u` | Changes that receptor `Y: u → p` at `kp`, preserving the tail bond. | Implements transphosphorylation only in the associated-tail context. |
| 15 | One-way | Any EGFR `Y~p` | Changes `Y: p → u` at `kdp`, without requiring oligomer dissociation. | Erases the adaptor docking state throughout the receptor population. |
| 16 | Reversible | EGFR `Y~p` and Grb2 `SH2` | Creates/releases the phosphotyrosine–SH2 bond at `kpg/kmg`. | Converts receptor phosphorylation into measurable Grb2 recruitment. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `EGFfree`, `EGFRfree`, `Grb2Free` | Molecule count | Free ligand site, free receptor ligand site, or free Grb2 SH2 site | Unoccupied pools; `EGFRfree` concerns ligand occupancy, not whether the receptor is oligomerized. |
| `Clusters`; `monomer`, `dimer`, `trimer`, `tetramer` | Species count | EGFR-containing species grouped by receptor count | Assembly-size distribution. `Clusters` combines sizes 1–4, while `tetramer` uses a greater-than-three cardinality condition. |
| `pEGFR` | Molecule count | EGFR with phosphorylated `Y`, whether free or Grb2-bound | Total receptor phosphorylation output. |
| `Grb2_pEGFR` | Molecule count | Explicit phospho-EGFR–Grb2 bond | Total recruited adaptor, independent of receptor oligomer size. |
| `Grb2EGFRMonomer` | Species count | Grb2-bound phospho-EGFR with free `back` and `cd` | Recruited adaptor on a receptor not crosslinked through either receptor–receptor interface. |
| `Grb2EGFRDimer1`–`4` | Species count | Back-linked or tail-linked EGFR dimers carrying one or two Grb2 molecules | Resolves adaptor occupancy and whether the dimer is joined through ectodomain (`1`, `3`) or open tails (`2`, `4`). |

## 8. Actions and simulation workflow

The file generates a network capped at four EGF and four EGFR molecules per species, preventing assemblies larger than the modeled tetramer. It then runs an ODE simulation to time 120 with 100 output steps.

## 9. Technical caveats and ambiguities

- Ring-closure rules match a specific four-receptor topology; `chi_r` is not a general multiplier for all oligomerization.
- `Clusters` lists several cardinality patterns compactly, and `EGFR>3` support may depend on parser version.
- Species-pattern observables may count embeddings rather than unique physical assemblies.
- The model has no explicit membrane or cytosolic compartments despite describing ectodomain and tail processes.
