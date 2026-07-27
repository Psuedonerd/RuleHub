# Detailed Model Explanation: Blinov 2006 EGFR phosphotyrosine signaling model

## 1. Model overview

This model follows EGF-driven EGFR dimerization and phosphorylation at Y1068 and Y1148, then resolves two routes for recruiting the Sos effector. Sos can arrive directly through Grb2 bound to receptor Y1068 or indirectly through phosphorylated Shc bound at Y1148, with adaptor complexes also able to preassemble in cytosol.

## 2. BNGL block inventory

The model contains 48 parameters, 5 molecule types, 6 seed species, 23 rules, 15 observables, and 6 active commands. It has no compartments, anchors, or functions; five derived parameters diagnose detailed-balance cycles but do not drive rules.

## 3. Parameters, functions, and rate laws

Most interactions use paired microscopic association/dissociation constants, with separate pairs for different assembly orders even when the final complex is the same. Receptor and adaptor phosphorylation are one-way rules balanced by independent dephosphorylation.

| Parameter group or names | Function in this model |
| --- | --- |
| `egf_tot`, `egfr_tot`, `Grb2_tot`, `Shc_tot`, `Sos_tot`, `Grb2_Sos_tot` | Initial free molecular pools plus a separately seeded Grb2–Sos pool. |
| `kp1/km1`, `kp2/km2` | EGF–EGFR binding and dimerization of ligand-occupied receptors. |
| `kp3`, `km3` | Phosphorylation of dimerized EGFR at either Y1068 or Y1148 and site-independent receptor dephosphorylation. |
| `kp14`, `km14`, `km16` | Phosphorylation of receptor-bound Shc Y317, dephosphorylation while receptor-bound, and slower cytosolic ShcP dephosphorylation. |
| `kp9/km9`, `kp11/km11`, `kp10/km10` | Direct Y1068 route: recruitment of free Grb2, recruitment of prebound Grb2–Sos, or addition of Sos after Grb2 is receptor-bound. |
| `kp13/km13`, `kp15/km15` | Y1148 binding by unphosphorylated or Y317-phosphorylated Shc. |
| `kp17/km17`, `kp18/km18`, `kp19/km19`, `kp20/km20`, `kp24/km24` | Alternative orders for assembling receptor–ShcP–Grb2 and receptor–ShcP–Grb2–Sos complexes. |
| `kp21/km21`, `kp23/km23`, `kp12/km12`, `kp22/km22` | Cytosolic ShcP/Grb2/Sos preassembly before receptor recruitment. |
| `loop1`–`loop5` | Ratios of equilibrium constants used to check closed thermodynamic cycles; no active rule uses them as rates. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `egf` | 1 | `r` | None | None | Ligand that occupies EGFR `l`. |
| `egfr` | 4 | `l`, `r`, `Y1068`, `Y1148` | `Y1068: Y, pY`; `Y1148: Y, pY` | None | Receptor whose `r` site dimerizes; Y1068 recruits Grb2 directly and Y1148 recruits Shc. |
| `Shc` | 2 | `PTB`, `Y317` | `Y317: Y, pY` | None | Adaptor that binds receptor through PTB and, after Y317 phosphorylation, recruits Grb2 through its SH2 site. |
| `Grb2` | 2 | `SH2`, `SH3` | None | None | Bifunctional adaptor: SH2 binds phospho-EGFR or phospho-Shc, while SH3 binds Sos. |
| `Sos` | 1 | `dom` | None | None | Effector recruited exclusively through Grb2 SH3. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial. Free EGF, unphosphorylated EGFR, unphosphorylated Shc, free Grb2, and free Sos are seeded, together with a substantial preassembled Grb2–Sos pool. The active workflow first removes EGF to equilibrate adaptor binding, then restores the ligand before the kinetic phase.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–8 create receptor phosphotyrosines and phosphorylated Shc. Rules 9–18 assemble direct Y1068 and indirect Y1148 routes to Sos at receptor, while rules 19–23 form and turn over the same adaptor combinations away from receptor.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–2 | Reversible | EGF `r`, EGFR `l`, and then two ligand-occupied EGFR `r` sites | Rule 1 creates/releases the ligand bond at `kp1/km1`; rule 2 creates/releases the receptor dimer bond at `kp2/km2`. | Builds the ligand-bound dimer required for receptor transphosphorylation. |
| 3–6 | One-way | Dimerized EGFR Y1068 or Y1148 (rules 3–4), and any phosphorylated receptor site (rules 5–6) | Rules 3/4 change Y1068/Y1148 `Y → pY` at `kp3`; rules 5/6 reverse the respective site at `km3`. | Independently opens and closes the direct Grb2 and Shc docking routes. |
| 7–8 | One-way | Shc PTB-bound to receptor Y1148~pY | Rule 7 changes Shc Y317 `Y → pY` at `kp14`; rule 8 changes receptor-bound Y317 `pY → Y` at `km14`, preserving PTB binding. | Makes receptor-bound Shc competent for Grb2 recruitment and permits local reversal. |
| 9–11 | Reversible | EGFR Y1068~pY, Grb2 SH2/SH3, and Sos | Rule 9 recruits Grb2 with free SH3 (`kp9/km9`); rule 10 recruits prebound Grb2–Sos (`kp11/km11`); rule 11 adds Sos to receptor-bound Grb2 (`kp10/km10`). | Provides two assembly orders for the direct receptor–Grb2–Sos route. |
| 12–13 | Reversible | EGFR Y1148~pY and Shc PTB; Shc Y317 is unphosphorylated in rule 12 or phosphorylated in rule 13 | Creates/releases the receptor–PTB bond using `kp13/km13` or `kp15/km15`. | Allows Shc to arrive before or after Y317 phosphorylation. |
| 14–15 | Reversible | Preformed ShcP–Grb2 or ShcP–Grb2–Sos and receptor Y1148~pY | Adds/removes the receptor–Shc PTB bond at `kp18/km18` or `kp20/km20`, retaining internal adaptor bonds. | Recruits partially or fully assembled indirect signaling complexes as units. |
| 16–18 | Reversible | Receptor-bound ShcP, Grb2 SH2, and Sos/Grb2 SH3 | Rule 16 adds free Grb2 (`kp17/km17`); rule 17 adds prebound Grb2–Sos (`kp24/km24`); rule 18 adds Sos after Grb2 (`kp19/km19`). | Completes the indirect Y1148–Shc–Grb2–Sos route through every modeled assembly order. |
| 19–20 | Reversible | Cytosolic ShcP Y317 and Grb2 SH2, with Grb2 SH3 free or already occupied | Forms ShcP–Grb2 at `kp21/km21` or ShcP–Grb2–Sos at `kp23/km23`. | Creates receptor-free adaptor pools available for rules 14–15. |
| 21 | One-way | Cytosolic ShcP with free PTB | Changes Y317 `pY → Y` at `km16`. | Removes the Grb2 docking state after Shc leaves receptor. |
| 22–23 | Reversible | Grb2 SH3 and Sos, either free (rule 22) or within ShcP–Grb2 (rule 23) | Creates/releases SH3–Sos at `kp12/km12` or `kp22/km22`. | Maintains free Grb2–Sos and completes cytosolic ShcP–Grb2–Sos by an alternative order. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Dimers` | Molecule count | EGFR–EGFR complexes | Receptor dimer abundance; pattern matches may scale with embeddings in larger complexes. |
| `RP` | Molecule count | Sum of Y1068~pY and Y1148~pY receptor patterns | Total phosphotyrosine-site signal; a receptor phosphorylated at both sites can contribute twice. |
| `R_Grb2`, `R_G_S` | Molecule count | Direct Y1068 complexes with Grb2 alone or Grb2–Sos | Occupancy of the direct Sos-recruitment branch. |
| `R_Shc`, `R_ShcP` | Molecule count | Y1148-bound unphosphorylated or phosphorylated Shc | Progress through receptor recruitment and Shc activation. |
| `Shc_Grb`, `Shc_Grb_Sos`, `ShcP` | Molecule count | Phospho-Shc complexes or total phospho-Shc, without requiring receptor | Cytosolic plus receptor-associated adaptor assembly state. |
| `R_S_G_S`, `Sos_act` | Molecule count | Complete indirect receptor–ShcP–Grb2–Sos complex; `Sos_act` sums direct and indirect receptor-bound Sos | Detailed indirect endpoint and combined receptor-associated Sos output. |
| `Efgr_total`, `Shc_total`, `Sos_total`, `Grb2_total` | Molecule count | All molecules of each named type | Pool-conservation checks; `Efgr_total` retains the source spelling. |

## 8. Actions and simulation workflow

The workflow generates a network, removes free EGF, and performs a long sparse ODE steady-state equilibration. It then restores EGF, writes SBML, and runs a 120-time-unit kinetic ODE simulation with 120 output steps and tight tolerances.

## 9. Technical caveats and ambiguities

- Metadata immunology/BCR tags conflict with the EGFR–Shc–Grb2–Sos source model.
- `RP` sums two site patterns and can double-count doubly phosphorylated receptors.
- `loop1`–`loop5` diagnose detailed-balance consistency but do not enforce or alter rates.
- Pattern observables can count multiple embeddings in one complex.
- Sparse-solver options are reported as parser-sensitive in local compatibility notes.
