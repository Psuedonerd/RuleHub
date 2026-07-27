# Detailed Model Explanation: Chattaraj 2021 multivalent Nephrin–Nck–NWASP clustering model

## 1. Model overview

This model studies heterotypic clustering of a trivalent Nephrin scaffold, a four-interface Nck adaptor, and a hexavalent NWASP partner. Condensate-like connectivity emerges solely from reversible, equal-affinity site binding, allowing valency and starting stoichiometry to determine cluster formation.

## 2. BNGL block inventory

The model contains 6 parameters, 3 molecule types, 3 free seed species, 11 molecule-count observables, and 21 reversible rules. It has no compartments, anchors, functions, or simulation actions; one XML-export action follows the model block.

## 3. Parameters, functions, and rate laws

The namespace separates the Nephrin–Nck interface (`12`) from the Nck–NWASP interface (`23`). Both interfaces are assigned the same dissociation constant and off-rate, so their derived on-rates are also equal.

| Parameter group or names | Function in this model |
| --- | --- |
| `kd_12`, `kd_23` | Dissociation constants for Nephrin-pY/Nck-SH2 and Nck-S/NWASP-p binding, respectively; both are set to 3500, eliminating affinity as a difference between the two edge types. |
| `koff_12`, `koff_23` | Unbinding rates for the two edge types; both are 1000. |
| `kon_12 = koff_12/kd_12`, `kon_23 = koff_23/kd_23` | Derived association rates. The same ratio for both families makes site count, concentration, and network topology—not kinetic asymmetry—the source of different clustering behavior. |

There are no functions or conditional rate laws.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `Nephrin` | 3 | `pY1`, `pY2`, `pY3` | None | None | Trivalent upstream scaffold; each phosphotyrosine-like site can bind one Nck SH2 domain. |
| `Nck` | 4 | `S1`, `S2`, `S3`, `Sh2` | None | None | Central adaptor: `Sh2` binds Nephrin, while three S sites independently bind NWASP, allowing Nck to bridge the other two molecule classes. |
| `NWASP` | 6 | `p1`–`p6` | None | None | Hexavalent downstream partner whose six proline-rich sites can each bind any Nck S site, providing the greatest branching capacity. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and begins with only free molecules: 300 Nephrin, 900 Nck, and 450 NWASP. This 1:3:1.5 ratio supplies exactly three Nck molecules per Nephrin and two Nck molecules per NWASP on average, while the available sites permit much larger crosslinked assemblies. No phosphorylation reactions occur; the `pY` and `p` names denote already available binding sites.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–18 enumerate the complete 3-by-6 matrix of Nck S-site/NWASP p-site contacts. Rules 19–21 connect each Nephrin pY site to the single Nck SH2 site, making Nck the bridge between Nephrin-rich and NWASP-rich portions of a cluster.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–3 | Reversible | Nck `S1`, `S2`, or `S3`, respectively; NWASP `p1` | Creates or releases one Nck-S–NWASP-p1 bond using `kon_23`/`koff_23`. | Gives NWASP site p1 access to all three equivalent Nck S interfaces. |
| 4–6 | Reversible | Nck `S3`, `S2`, or `S1`, respectively; NWASP `p2` | Creates/releases the corresponding bond with the same `kon_23`/`koff_23` pair. | Completes the three Nck choices for NWASP p2; source numbering orders the S variants differently but does not change their kinetics. |
| 7–9 | Reversible | NWASP `p3`; Nck `S2`, `S1`, or `S3` in rules 7, 8, and 9, respectively | Adds/removes one p3 contact at `kon_23`/`koff_23`. | Extends the identical-affinity interaction matrix to the third NWASP site while preserving the source's nonnumerical S-site ordering. |
| 10–12 | Reversible | Nck `S1`–`S3`, respectively; NWASP `p4` | Adds/removes one Nck–p4 bond at the shared rates. | Provides the fourth independently occupiable NWASP branch. |
| 13–15 | Reversible | Nck `S1`–`S3`, respectively; NWASP `p5` | Adds/removes one Nck–p5 bond at the shared rates. | Provides the fifth branch and increases the number of possible cluster topologies. |
| 16–18 | Reversible | NWASP `p6`; Nck `S1`, `S3`, and `S2`, respectively | Adds/removes one p6 contact using `kon_23`/`koff_23`. | Completes the 18-rule Nck–NWASP interaction matrix; all 6 NWASP sites can bind all 3 Nck S sites. |
| 19–21 | Reversible | Nephrin `pY1`, `pY2`, or `pY3`, respectively; Nck `Sh2` | Creates/releases one pY–SH2 bond using `kon_12`/`koff_12`. | Recruits Nck to any of Nephrin's three sites, enabling an Nck molecule to connect Nephrin to NWASP through its still-independent S sites. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `tot_Nephrin`, `tot_Nck`, `tot_NWASP` | Molecule count | Every molecule of each type | Conservation checks for the three fixed pools. |
| `free_Nephrin`, `free_Nck`, `free_NWASP` | Molecule count | Molecules with all declared sites unbound | Strict monomer/free-pool readouts; partial occupancy excludes a molecule from the corresponding free count. |
| `fully_bound_Nephrin`, `fully_bound_Nck`, `fully_bound_NWASP` | Molecule count | Molecules with every site occupied | Measures saturation of each valency class rather than cluster size. Fully bound Nck requires all three S sites and Sh2 to be occupied. |
| `cluster_neph_nck_nw` | Molecule count | Connected complexes containing Nephrin, Nck, and NWASP | Reports ternary network formation, but pattern embeddings may count a large complex more than once when it contains multiple matching molecules. |
| `cluster_nck_nw` | Molecule count | Connected complexes containing Nck and NWASP, whether or not Nephrin is also present | Broader Nck–NWASP association readout; ternary clusters can contribute because Nephrin is not excluded. |

## 8. Actions and simulation workflow

The source does not generate a network or run ODE, stochastic, or network-free simulation. Its only action writes an XML representation, so quantitative time courses or equilibrium scans must be supplied by an external workflow.

## 9. Technical caveats and ambiguities

- The metadata description says “NFkB oscillations,” but the BNGL and comments unambiguously describe Nephrin–Nck–NWASP clustering; the metadata description is inconsistent.
- All sites within an interface family share identical rates, so the model intentionally omits site-specific affinity or cooperativity.
- Molecule-count cluster observables count pattern matches, not necessarily unique physical condensates.
- The rules model reversible connectivity but no explicit phase, volume, diffusion, or excluded-volume physics; “condensation” is inferred from multivalent cluster behavior.
- The active file exports XML only despite metadata listing ODE compatibility.
