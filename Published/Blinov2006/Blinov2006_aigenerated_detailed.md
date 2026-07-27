# Coder Model Explanation: Blinov 2006 phosphotyrosine signaling model

## 1. Model identity and scope

`Blinov_2006` implements EGF–EGFR binding and dimerization, two-site receptor phosphorylation, and assembly of Shc–Grb2–Sos signaling complexes. Sources: `Published/Blinov2006/Blinov_2006.bngl` and `Published/Blinov2006/Blinov_2006_metadata.yaml`.

## 2. BNGL block inventory

Inside `begin model`/`end model`, the file has 48 parameters (including five derived detailed-balance diagnostics), 5 molecule types, 6 seed species, 23 rules, and 15 observables. Six executable commands follow the model. There are no compartments, anchors, or functions.

## 3. Parameters, functions, and rate laws

Initial totals are `egf_tot=1.2e6`, `egfr_tot=1.8e5`, `Grb2_tot=1.0e5`, `Shc_tot=2.7e5`, `Sos_tot=1.3e4`, and precomplexed `Grb2_Sos_tot=4.9e4`. Reversible pairs are ligand binding `kp1=1.667e-06`/`km1=0.06`, receptor aggregation `kp2=5.556e-06`/`km2=0.1`, receptor phosphorylation/dephosphorylation `kp3=0.5`/`km3=4.505`, bound-Shc phosphorylation/dephosphorylation `kp14=3`/`km14=0.03`, receptor–Grb2 `kp9=8.333e-07`/`km9=0.05`, receptor-bound Grb2–Sos `kp10=5.556e-06`/`km10=0.06`, receptor–Grb2-Sos `kp11=1.25e-06`/`km11=0.03`, receptor–Shc `kp13=2.5e-05`/`km13=0.6`, receptor–ShcP `kp15=2.5e-07`/`km15=0.3`, receptor-ShcP–Grb2 `kp17=1.667e-06`/`km17=0.1`, receptor–ShcP-Grb2 `kp18=2.5e-07`/`km18=0.3`, Sos addition to bound ShcP-Grb2 `kp19=5.556e-06`/`km19=0.0214`, receptor–ShcP-Grb2-Sos `kp20=6.667e-08`/`km20=0.12`, Grb2-Sos addition to bound ShcP `kp24=5e-06`/`km24=0.0429`, cytosolic ShcP–Grb2 `kp21=1.667e-06`/`km21=0.01`, cytosolic ShcP–Grb2-Sos `kp23=1.167e-05`/`km23=0.1`, Grb2–Sos `kp12=5.556e-08`/`km12=0.0015`, and Sos addition to cytosolic ShcP-Grb2 `kp22=1.667e-05`/`km22=0.064`. Free ShcP dephosphorylates at `km16=0.005`. `loop1`–`loop5` are algebraic equilibrium-cycle ratios; no rule uses them and there is no functions block.

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

**Rule-family orientation.** Rules 1–8 establish ligand-driven receptor phosphorylation and Shc phosphorylation. Rules 9–18 assemble receptor-proximal Grb2/Sos routes at `Y1068` or Shc at `Y1148`. Rules 19–24 assemble and regulate the same adaptor combinations away from receptor.

| # | Direction | Exact modeled edit | Rate(s) |
| ---: | --- | --- | --- |
| 1 | Reversible | `egfr.l` binds `egf.r` as bond `!1` | `kp1`, `km1` |
| 2 | Reversible | Two ligand-bound receptors (`l!+`) connect `egfr.r-egfr.r` as bond `!3` | `kp2`, `km2` |
| 3 | One-way | Dimerized `egfr.r!+` changes `Y1068 Y→pY` | `kp3` |
| 4 | One-way | Dimerized `egfr.r!+` changes `Y1148 Y→pY` | `kp3` |
| 5 | One-way | `egfr.Y1068 pY→Y`, irrespective of binding | `km3` |
| 6 | One-way | `egfr.Y1148 pY→Y`, irrespective of binding | `km3` |
| 7 | One-way | In the `egfr.Y1148~pY!1-Shc.PTB!1` complex, `Shc.Y317 Y→pY` | `kp14` |
| 8 | One-way | Receptor-bound `Shc.PTB!+` changes `Y317 pY→Y` | `km14` |
| 9 | Reversible | Free `Grb2.SH2` binds `egfr.Y1068~pY` as `!1`; `SH3` remains free | `kp9`, `km9` |
| 10 | Reversible | Grb2 already bound through `SH3!+` binds `egfr.Y1068~pY` through `SH2!1` | `kp11`, `km11` |
| 11 | Reversible | Sos `dom` binds `SH3` of receptor-bound `egfr.Y1068!1-Grb2.SH2!1`, forming `SH3!2-dom!2` | `kp10`, `km10` |
| 12 | Reversible | Unphosphorylated `Shc.PTB` binds `egfr.Y1148~pY` as `!1` | `kp13`, `km13` |
| 13 | Reversible | Phosphorylated `Shc.PTB` binds `egfr.Y1148~pY` as `!1` | `kp15`, `km15` |
| 14 | Reversible | Preformed `Shc.Y317~pY!1-Grb2.SH2!1` binds receptor through `Shc.PTB!2-egfr.Y1148~pY!2` | `kp18`, `km18` |
| 15 | Reversible | Preformed `ShcP-Grb2-Sos` binds receptor through `Shc.PTB!2-egfr.Y1148~pY!2`; internal `Y317-SH2` and `SH3-dom` bonds persist | `kp20`, `km20` |
| 16 | Reversible | Free `Grb2.SH2` binds `Y317~pY` of receptor-bound Shc as bond `!2` | `kp17`, `km17` |
| 17 | Reversible | A preformed `Grb2.SH3!3-Sos.dom!3` complex binds receptor-bound `Shc.Y317~pY` through `Grb2.SH2!2` | `kp24`, `km24` |
| 18 | Reversible | Sos binds `Grb2.SH3` in a receptor-associated `Shc.Y317~pY!2-Grb2.SH2!2` complex, forming `!3` | `kp19`, `km19` |
| 19 | Reversible | Cytosolic `Shc.Y317~pY` binds free `Grb2.SH2` as `!1` | `kp21`, `km21` |
| 20 | Reversible | Cytosolic `Shc.Y317~pY` binds `SH2` of Grb2 whose `SH3` is already bound | `kp23`, `km23` |
| 21 | One-way | Free-PTB Shc changes `Y317 pY→Y` | `km16` |
| 22 | Reversible | Free `Grb2.SH3` binds `Sos.dom` as `!1` | `kp12`, `km12` |
| 23 | Reversible | Sos binds `SH3` in cytosolic `Shc.Y317~pY!2-Grb2.SH2!2`, forming `!3` | `kp22`, `km22` |

The source contains 23 concrete rule statements; its parameter numbering skips several historical reaction numbers.

## 7. Observables and technical readouts

Molecules `Dimers` counts EGFR–EGFR complexes. `Sos_act` sums Sos in either receptor-bound ShcP–Grb2–Sos or direct EGFR–Grb2–Sos patterns. `RP` sums `Y1068~pY` and `Y1148~pY` receptor patterns. `Shc_Grb` and `Shc_Grb_Sos` count phospho-Shc–Grb2 assemblies without requiring receptor; `R_Grb2`, `R_Shc`, `R_ShcP`, `R_G_S`, and `R_S_G_S` count the named receptor-associated complexes. `ShcP` counts phosphorylated Shc. `Efgr_total` (spelling retained), `Shc_total`, `Sos_total`, and `Grb2_total` count all molecules of each type.

## 8. Actions and simulation workflow

The file generates the network, sets free `egf(r)` to zero, and performs a 100000-time-unit, 10-step sparse ODE steady-state equilibration. It restores EGF to `egf_tot`, writes SBML, then runs a 120-time-unit, 120-step sparse ODE kinetic simulation with `atol=rtol=1e-8`.

## 9. Technical caveats and ambiguities

The metadata's immunology/BCR tags conflict with the local EGFR/Shc/Grb2/Sos model and should not drive interpretation. Molecule observables may count multiple matching embeddings. `RP` is a sum of two patterns and can count a doubly phosphorylated receptor twice. The comment says “check detailed balanced,” but `loop1`–`loop5` are diagnostics only. The metadata records parser trouble associated with the sparse action option.
