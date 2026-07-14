# Coder Model Explanation: Kocieniewski 2012

## 1. Model identity and scope

- **Model id:** `Kocieniewski_2012`
- **Title:** Kocieniewski 2012
- **BNGL path:** `Published/Kocieniewski2012/Kocieniewski_2012.bngl`
- **YAML path:** `Published/Kocieniewski2012/metadata.yaml`
- **Metadata description:** The YAML says “Actin dynamics,” but the BNGL file is a scaffolded MAPK cascade.
- **Scope:** This model encodes a minimal MAP3K/MAP2K/MAPK cascade organized by a scaffold. `Scaff` has three independent docking sites (`map3k`, `map2k`, `mapk`). The kinases bind through their `s` docking sites. `MAP3K.S` switches between inactive `I` and active `A`; `MAP2K.R1/R2` and `MAPK.R1/R2` switch between unphosphorylated `Y` and phosphorylated `Yp`. Scaffold-bound active MAP3K phosphorylates scaffold-bound MAP2K, and fully phosphorylated scaffold-bound MAP2K phosphorylates scaffold-bound MAPK.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 10 parameters: four initial totals and six kinetic/control rates. |
| Compartments | No | No compartment block. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 4 molecule types: `MAP3K`, `MAP2K`, `MAPK`, `Scaff`. |
| Seed/species | Yes | 4 initial free species. |
| Observables | Yes | 2 scaffold-complex observables. |
| Functions | No | No functions block. |
| Reaction rules | Yes | 20 rules. |
| Actions | No | No action block or inline simulation command. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `Atot` | `1e5` | Initial MAP3K count. |
| `Btot` | `1e5` | Initial MAP2K count. |
| `Ctot` | `5e5` | Initial MAPK count. |
| `Stot` | `1e5` | Initial scaffold count. |
| `a` | `1e-6` | Forward scaffold docking rate for MAP3K, MAP2K, and MAPK binding rules. |
| `d1` | `0.1` | Reverse rate for reversible scaffold docking. |
| `d2` | `100` | One-way scaffold release for inactive MAP3K and doubly phosphorylated MAPK. |
| `pscaff` | `100` | Scaffold-local phosphorylation rate. |
| `u` | `0.1` | Global deactivation/dephosphorylation rate. |
| `S` | `1` | Basal MAP3K activation rate. |

No functions are declared; all rule rates are direct parameters.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `MAP3K` | 2 | `s`, `S` | `S`: `I`, `A` | none | `s` docks to `Scaff.map3k`; `S` is activation state. | Only active `S~A` drives MAP2K phosphorylation on scaffold. |
| `MAP2K` | 3 | `s`, `R1`, `R2` | `R1`: `Y`, `Yp`; `R2`: `Y`, `Yp` | none | `s` docks to `Scaff.map2k`; `R1/R2` are phosphorylation sites. | Must have both `R1~Yp` and `R2~Yp` to phosphorylate MAPK in this file. |
| `MAPK` | 3 | `s`, `R1`, `R2` | `R1`: `Y`, `Yp`; `R2`: `Y`, `Yp` | none | `s` docks to `Scaff.mapk`; `R1/R2` are phosphorylation sites. | Doubly phosphorylated scaffold-bound MAPK has a special one-way release rule. |
| `Scaff` | 3 | `map3k`, `map2k`, `mapk` | none | none | Docking platform for one MAP3K, one MAP2K, and one MAPK. | Sites are distinct and typed by kinase layer. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are present. Initial species are all free: inactive `MAP3K(s,S~I)` at `Atot`, unphosphorylated `MAP2K(s,R1~Y,R2~Y)` at `Btot`, unphosphorylated `MAPK(s,R1~Y,R2~Y)` at `Ctot`, and empty `Scaff(map3k,map2k,mapk)` at `Stot`.

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rules 2-11 are scaffold docking/release rules using kinase `s` sites and matching scaffold sites. Rules 12-15 are scaffold-local phosphorylation rules where an upstream active kinase remains scaffold-bound while the downstream kinase’s `R1` or `R2` state changes. Rules 16-20 globally reverse activation/phosphorylation without requiring scaffold binding.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | `MAP3K.S` | `S` | `MAP3K.S I→A`; `MAP3K.s` remains free. | Basally activates MAP3K before or independent of scaffold docking. |
| 2 | `Unlabeled` | reversible | `MAP3K.s` + `Scaff.map3k` | `a, d1` | Forms/releases `MAP3K.s!1`–`Scaff.map3k!1` for active `MAP3K.S~A`. | Docks active MAP3K onto the scaffold’s MAP3K slot. |
| 3 | `Unlabeled` | one-way | `MAP3K.s!1` + `Scaff.map3k!1` | `d2` | Releases `MAP3K.s!1`–`Scaff.map3k!1` for inactive `MAP3K.S~I`. | Forces inactive scaffold-bound MAP3K off the scaffold. |
| 4 | `Unlabeled` | reversible | `MAP2K.s` + `Scaff.map2k`; `MAP2K.R1~Y,R2~Y` | `a, d1` | Forms/releases `MAP2K.s!1`–`Scaff.map2k!1`. | Docks completely unphosphorylated MAP2K. |
| 5 | `Unlabeled` | reversible | `MAP2K.s` + `Scaff.map2k`; `MAP2K.R1~Yp,R2~Y` | `a, d1` | Forms/releases `MAP2K.s!1`–`Scaff.map2k!1`. | Docks MAP2K already phosphorylated at `R1` only. |
| 6 | `Unlabeled` | reversible | `MAP2K.s` + `Scaff.map2k`; `MAP2K.R1~Y,R2~Yp` | `a, d1` | Forms/releases `MAP2K.s!1`–`Scaff.map2k!1`. | Docks MAP2K already phosphorylated at `R2` only. |
| 7 | `Unlabeled` | reversible | `MAP2K.s` + `Scaff.map2k`; `MAP2K.R1~Yp,R2~Yp` | `a, d1` | Forms/releases `MAP2K.s!1`–`Scaff.map2k!1`. | Docks doubly phosphorylated MAP2K, which can support MAPK phosphorylation in rules 14-15. |
| 8 | `Unlabeled` | reversible | `MAPK.s` + `Scaff.mapk`; `MAPK.R1~Y,R2~Y` | `a, d1` | Forms/releases `MAPK.s!1`–`Scaff.mapk!1`. | Docks unphosphorylated MAPK. |
| 9 | `Unlabeled` | reversible | `MAPK.s` + `Scaff.mapk`; `MAPK.R1~Yp,R2~Y` | `a, d1` | Forms/releases `MAPK.s!1`–`Scaff.mapk!1`. | Docks MAPK phosphorylated at `R1` only. |
| 10 | `Unlabeled` | reversible | `MAPK.s` + `Scaff.mapk`; `MAPK.R1~Y,R2~Yp` | `a, d1` | Forms/releases `MAPK.s!1`–`Scaff.mapk!1`. | Docks MAPK phosphorylated at `R2` only. |
| 11 | `Unlabeled` | one-way | `MAPK.s!1` + `Scaff.mapk!1`; `MAPK.R1~Yp,R2~Yp` | `d2` | Releases doubly phosphorylated `MAPK.s!1`–`Scaff.mapk!1`. | Removes fully phosphorylated MAPK from the scaffold after signal completion. |
| 12 | `Unlabeled` | one-way | `MAP3K.S~A`, `MAP3K.s!1`–`Scaff.map3k!1`, `MAP2K.s!2`–`Scaff.map2k!2`, `MAP2K.R1~Y` | `pscaff` | `MAP2K.R1 Y→Yp`; all scaffold bonds remain. | Active scaffold-bound MAP3K phosphorylates scaffold-bound MAP2K site `R1`. |
| 13 | `Unlabeled` | one-way | Same scaffolded MAP3K/MAP2K complex, `MAP2K.R2~Y` | `pscaff` | `MAP2K.R2 Y→Yp`; all scaffold bonds remain. | Active scaffold-bound MAP3K phosphorylates MAP2K site `R2`. |
| 14 | `Unlabeled` | one-way | `MAP2K.R1~Yp,R2~Yp`, `MAP2K.s!2`–`Scaff.map2k!2`, `MAPK.s!1`–`Scaff.mapk!1`, `MAPK.R1~Y` | `pscaff` | `MAPK.R1 Y→Yp`; scaffold bonds remain. | Fully phosphorylated scaffold-bound MAP2K phosphorylates scaffold-bound MAPK site `R1`. |
| 15 | `Unlabeled` | one-way | Same scaffolded MAP2K/MAPK complex, `MAPK.R2~Y` | `pscaff` | `MAPK.R2 Y→Yp`; scaffold bonds remain. | Fully phosphorylated scaffold-bound MAP2K phosphorylates MAPK site `R2`. |
| 16 | `Unlabeled` | one-way | `MAP3K.S~A` | `u` | `MAP3K.S A→I`. | Global MAP3K deactivation; pattern does not require a scaffold bond. |
| 17 | `Unlabeled` | one-way | `MAP2K.R1~Yp` | `u` | `MAP2K.R1 Yp→Y`. | Global dephosphorylation of MAP2K site `R1`. |
| 18 | `Unlabeled` | one-way | `MAP2K.R2~Yp` | `u` | `MAP2K.R2 Yp→Y`. | Global dephosphorylation of MAP2K site `R2`. |
| 19 | `Unlabeled` | one-way | `MAPK.R1~Yp` | `u` | `MAPK.R1 Yp→Y`. | Global dephosphorylation of MAPK site `R1`. |
| 20 | `Unlabeled` | one-way | `MAPK.R2~Yp` | `u` | `MAPK.R2 Yp→Y`. | Global dephosphorylation of MAPK site `R2`. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `MAPKchainone` | `Molecules` | `MAPK(s!1,R1~Yp).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | Counts scaffold complexes containing scaffold-bound MAPK phosphorylated at `R1` and scaffold-bound doubly phosphorylated MAP2K. |
| `MAPKchaintwo` | `Molecules` | `MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | Counts scaffold complexes containing active scaffold-bound MAP3K and scaffold-bound doubly phosphorylated MAP2K. |

## 8. Actions and simulation workflow

No action block or inline simulation command is declared. The BNGL file defines the network logic; the caller must choose generation and simulation settings externally.

## 9. Technical caveats and ambiguities

- The YAML description does not match the BNGL cascade; this summary follows the BNGL file.
- Rules 12-15 require scaffold colocalization through explicit bonds; they are not free-solution phosphorylation rules.
- Rules 16-20 use partial patterns, so they can dephosphorylate matching molecules whether free or scaffold-bound unless other generated-context constraints apply.
