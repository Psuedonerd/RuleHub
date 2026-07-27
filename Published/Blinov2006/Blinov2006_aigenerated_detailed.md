# Detailed Model Explanation: Blinov 2006 phosphotyrosine signaling model

## 1. Model identity and scope

`Blinov_2006` implements EGF–EGFR binding and dimerization, two-site receptor phosphorylation, and assembly of Shc–Grb2–Sos signaling complexes. Sources: `Published/Blinov2006/Blinov_2006.bngl` and `Published/Blinov2006/Blinov_2006_metadata.yaml`.

## 2. BNGL block inventory

Inside `begin model`/`end model`, the file has 48 parameters (including five derived detailed-balance diagnostics), 5 molecule types, 6 seed species, 23 rules, and 15 observables. Six executable commands follow the model. There are no compartments, anchors, or functions.

## 3. Parameters, functions, and rate laws

The model uses paired association/dissociation constants. Grouping them by mechanism makes the alternative assembly paths easier to compare:

- **Initial molecular pools:** `egf_tot = 1.2e6`, `egfr_tot = 1.8e5`, `Grb2_tot = 1.0e5`, `Shc_tot = 2.7e5`, `Sos_tot = 1.3e4`, and preassembled `Grb2_Sos_tot = 4.9e4`.
- **Receptor activation:** EGF–EGFR binding uses `kp1 = 1.667e-06`, `km1 = 0.06`; ligand-bound receptor dimerization uses `kp2 = 5.556e-06`, `km2 = 0.1`; receptor phosphorylation/dephosphorylation uses `kp3 = 0.5`, `km3 = 4.505`.
- **Shc modification:** receptor-bound Shc phosphorylation/dephosphorylation uses `kp14 = 3`, `km14 = 0.03`; free ShcP dephosphorylation uses `km16 = 0.005`.
- **Direct Y1068 route:** receptor–Grb2 uses `kp9 = 8.333e-07`, `km9 = 0.05`; receptor recruitment of prebound Grb2–Sos uses `kp11 = 1.25e-06`, `km11 = 0.03`; Sos addition to receptor-bound Grb2 uses `kp10 = 5.556e-06`, `km10 = 0.06`.
- **Y1148/Shc route:** receptor–Shc uses `kp13 = 2.5e-05`, `km13 = 0.6`; receptor–ShcP uses `kp15 = 2.5e-07`, `km15 = 0.3`; Grb2 addition to receptor-bound ShcP uses `kp17 = 1.667e-06`, `km17 = 0.1`; preformed ShcP–Grb2 recruitment uses `kp18 = 2.5e-07`, `km18 = 0.3`.
- **Sos-containing Shc complexes:** Sos addition to receptor-associated ShcP–Grb2 uses `kp19 = 5.556e-06`, `km19 = 0.0214`; preformed ShcP–Grb2–Sos recruitment uses `kp20 = 6.667e-08`, `km20 = 0.12`; preformed Grb2–Sos addition to receptor-bound ShcP uses `kp24 = 5e-06`, `km24 = 0.0429`.
- **Cytosolic preassembly:** ShcP–Grb2 uses `kp21 = 1.667e-06`, `km21 = 0.01`; ShcP binding to Grb2–Sos uses `kp23 = 1.167e-05`, `km23 = 0.1`; Grb2–Sos uses `kp12 = 5.556e-08`, `km12 = 0.0015`; Sos addition to ShcP–Grb2 uses `kp22 = 1.667e-05`, `km22 = 0.064`.
- **Detailed-balance diagnostics:** `loop1` through `loop5` are algebraic ratios of the relevant equilibrium constants. They are calculated for checking closed assembly cycles but are not used as rule rates.

There is no functions block.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `egf` | 1 | `r` | None | None | Binds `egfr.l` | Ligand |
| `egfr` | 4 | `l`, `r`, `Y1068`, `Y1148` | `Y1068: Y,pY`; `Y1148: Y,pY` | None | `l` binds ligand; `r` dimerizes; phosphotyrosines recruit Grb2 or Shc | Receptor |
| `Shc` | 2 | `PTB`, `Y317` | `Y317: Y,pY` | None | `PTB` binds `egfr.Y1148~pY`; `Y317~pY` binds `Grb2.SH2` | Adaptor |
| `Grb2` | 2 | `SH2`, `SH3` | None | None | `SH2` binds phospho-EGFR or phospho-Shc; `SH3` binds Sos | Adaptor |
| `Sos` | 1 | `dom` | None | None | Binds `Grb2.SH3` | Effector |

## 5. Compartments, anchors, initial species, and setup

There are no compartments or anchors. Free EGF, EGFR (`Y1068~Y,Y1148~Y`), Shc (`Y317~Y`), Grb2, and Sos are seeded from their totals; an additional Grb2–Sos bond `Grb2.SH3!1-Sos.dom!1` is seeded at `Grb2_Sos_tot`. The workflow subsequently removes EGF for equilibration and restores it for kinetics.

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules 1–8 create the two phosphotyrosine docking routes. Rules 9–18 assemble Sos at receptor either directly through Y1068–Grb2 or indirectly through Y1148–Shc–Grb2. Rules 19–23 allow the same adaptor complexes to preassemble and turn over in cytosol.

| # | Direction | Participants and required context | Bond or state change | Rate(s) | Implementation consequence |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | EGF `r`; EGFR `l` | Create/remove the ligand–receptor bond | `kp1`; `km1` | Produces ligand-occupied receptor monomers. |
| 2 | Reversible | two EGF-occupied EGFR molecules with free `r` sites | Create/remove the EGFR `r–r` dimer bond | `kp2`; `km2` | Dimerizes ligand-bound receptors, enabling the phosphorylation rules. |
| 3 | One-way | EGFR in an `r`-linked dimer | `Y1068`: `Y→pY` | `kp3` | Creates the direct Grb2 docking site. |
| 4 | One-way | EGFR in an `r`-linked dimer | `Y1148`: `Y→pY` | `kp3` | Creates the Shc PTB docking site. |
| 5 | One-way | any EGFR with `Y1068~pY` | `Y1068`: `pY→Y` | `km3` | Erases the direct Grb2 recruitment site. |
| 6 | One-way | any EGFR with `Y1148~pY` | `Y1148`: `pY→Y` | `km3` | Erases the Shc recruitment site. |
| 7 | One-way | Shc bound by `PTB` to receptor `Y1148~pY` | `Shc.Y317`: `Y→pY`; receptor bond retained | `kp14` | Converts receptor-bound Shc into a Grb2-binding adaptor. |
| 8 | One-way | receptor-bound phospho-Shc | `Shc.Y317`: `pY→Y` | `km14` | Removes the Grb2 docking site while Shc remains receptor-associated. |
| 9 | Reversible | free Grb2; EGFR `Y1068~pY`; Grb2 `SH3` free | Create/remove `Y1068–SH2` | `kp9`; `km9` | Recruits empty Grb2 directly to phospho-EGFR. |
| 10 | Reversible | Grb2 whose `SH3` is already occupied; EGFR `Y1068~pY` | Create/remove `Y1068–SH2` | `kp11`; `km11` | Recruits a preassembled Grb2–Sos unit directly to receptor. |
| 11 | Reversible | Sos; receptor-bound Grb2 with free `SH3` | Create/remove `Grb2.SH3–Sos.dom` | `kp10`; `km10` | Completes the direct EGFR–Grb2–Sos signaling complex. |
| 12 | Reversible | unphosphorylated Shc; EGFR `Y1148~pY` | Create/remove `Y1148–PTB` | `kp13`; `km13` | Recruits Shc before its Y317 phosphorylation. |
| 13 | Reversible | Y317-phosphorylated Shc; EGFR `Y1148~pY` | Create/remove `Y1148–PTB` | `kp15`; `km15` | Recruits already phosphorylated Shc. |
| 14 | Reversible | preformed ShcP–Grb2; EGFR `Y1148~pY` | Create/remove `Y1148–PTB`; preserve `Y317–SH2` | `kp18`; `km18` | Attaches the two-adaptor complex to receptor as a unit. |
| 15 | Reversible | preformed ShcP–Grb2–Sos; EGFR `Y1148~pY` | Create/remove `Y1148–PTB`; preserve both adaptor bonds | `kp20`; `km20` | Attaches the complete indirect Sos-recruitment complex to receptor. |
| 16 | Reversible | free Grb2; receptor-bound ShcP | Create/remove `Shc.Y317–Grb2.SH2` | `kp17`; `km17` | Builds the indirect receptor–Shc–Grb2 route stepwise. |
| 17 | Reversible | preformed Grb2–Sos; receptor-bound ShcP | Create/remove `Shc.Y317–Grb2.SH2`; preserve `SH3–Sos` | `kp24`; `km24` | Adds a Grb2–Sos unit to receptor-bound ShcP. |
| 18 | Reversible | Sos; receptor-associated ShcP–Grb2 with free `SH3` | Create/remove `SH3–Sos.dom` | `kp19`; `km19` | Completes indirect Sos recruitment after Grb2 is already bound. |
| 19 | Reversible | cytosolic ShcP and free Grb2 | Create/remove `Y317–SH2` | `kp21`; `km21` | Forms a receptor-free ShcP–Grb2 complex. |
| 20 | Reversible | cytosolic ShcP and Grb2 with occupied `SH3` | Create/remove `Y317–SH2` | `kp23`; `km23` | Forms receptor-free ShcP–Grb2–Sos from prebound Grb2–Sos. |
| 21 | One-way | cytosolic ShcP with free `PTB` | `Y317`: `pY→Y` | `km16` | Deactivates Shc after it leaves receptor. |
| 22 | Reversible | free Grb2 and Sos | Create/remove `SH3–dom` | `kp12`; `km12` | Maintains the cytosolic Grb2–Sos pool. |
| 23 | Reversible | Sos and cytosolic ShcP–Grb2 | Create/remove `Grb2.SH3–Sos.dom` | `kp22`; `km22` | Completes receptor-free ShcP–Grb2–Sos by adding Sos last. |

## 7. Observables and technical readouts

Molecules `Dimers` counts EGFR–EGFR complexes. `Sos_act` sums Sos in either receptor-bound ShcP–Grb2–Sos or direct EGFR–Grb2–Sos patterns. `RP` sums `Y1068~pY` and `Y1148~pY` receptor patterns. `Shc_Grb` and `Shc_Grb_Sos` count phospho-Shc–Grb2 assemblies without requiring receptor; `R_Grb2`, `R_Shc`, `R_ShcP`, `R_G_S`, and `R_S_G_S` count the named receptor-associated complexes. `ShcP` counts phosphorylated Shc. `Efgr_total` (spelling retained), `Shc_total`, `Sos_total`, and `Grb2_total` count all molecules of each type.

## 8. Actions and simulation workflow

The file generates the network, sets free `egf(r)` to zero, and performs a 100000-time-unit, 10-step sparse ODE steady-state equilibration. It restores EGF to `egf_tot`, writes SBML, then runs a 120-time-unit, 120-step sparse ODE kinetic simulation with `atol=rtol=1e-8`.

## 9. Technical caveats and ambiguities

The metadata's immunology/BCR tags conflict with the local EGFR/Shc/Grb2/Sos model and should not drive interpretation. Molecule observables may count multiple matching embeddings. `RP` is a sum of two patterns and can count a doubly phosphorylated receptor twice. The comment says “check detailed balanced,” but `loop1`–`loop5` are diagnostics only. The metadata records parser trouble associated with the sparse action option.
