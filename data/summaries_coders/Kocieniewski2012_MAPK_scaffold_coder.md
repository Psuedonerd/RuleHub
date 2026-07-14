# Coder Model Explanation: Kocieniewski 2012

## 1. Model identity and scope

- **Model id:** `Kocieniewski_2012`
- **Title:** Kocieniewski 2012
- **BNGL path:** `Published/Kocieniewski2012/Kocieniewski_2012.bngl`
- **YAML path:** `Published/Kocieniewski2012/metadata.yaml`
- **Metadata description:** Actin dynamics
- **Scope:** A scaffolded MAPK cascade model where MAP3K activation, scaffold binding, scaffold-localized phosphorylation of MAP2K and MAPK, and global dephosphorylation determine how signaling complexes form on Scaff.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 10 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 4 molecule type entries. |
| Seed/species | Yes | 4 initial species entries. |
| Observables | Yes | 2 observable entries. |
| Functions | No | 0 function entries. |
| Reaction rules | Yes | 20 reaction rules. |
| Actions | No | 0 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `Atot` | `1e5` | Molecule Numbers |
| `Btot` | `1e5` | kinetic or model-control parameter |
| `Ctot` | `5e5` | kinetic or model-control parameter |
| `Stot` | `1e5` | kinetic or model-control parameter |
| `a` | `1e-6` | Rates |
| `d1` | `0.1` | kinetic or model-control parameter |
| `d2` | `100` | kinetic or model-control parameter |
| `pscaff` | `100` | kinetic or model-control parameter |
| `u` | `0.1` | kinetic or model-control parameter |
| `S` | `1` | kinetic or model-control parameter |

No separate functions block is declared; rates are direct parameters or expressions in rule rows.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `MAP3K` | 2 | s, S~I~A | S: I, A | none | no explicit binding/modification site role beyond whole-molecule abundance |  |
| `MAP2K` | 3 | s, R1~Y~Yp, R2~Y~Yp | R1: Y, Yp; R2: Y, Yp | none | binding/modification candidate sites: R1, R2 |  |
| `MAPK` | 3 | s, R1~Y~Yp, R2~Y~Yp | R1: Y, Yp; R2: Y, Yp | none | binding/modification candidate sites: R1, R2 |  |
| `Scaff` | 3 | map3k, map2k, mapk | none declared | none | binding/modification candidate sites: map3k, map2k, mapk |  |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `MAP3K(s,S~I)` | `Atot` | starting species pool for this pattern |
| `MAP2K(s,R1~Y,R2~Y)` | `Btot` | starting species pool for this pattern |
| `MAPK(s,R1~Y,R2~Y)` | `Ctot` | starting species pool for this pattern |
| `Scaff(map3k,map2k,mapk)` | `Stot` | starting species pool for this pattern |

## 6. Complete reaction-rule inventory

The source contains **20** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | MAP3K | `S` | internal-state conversion/modification | `MAP3K(s,S~I) -> MAP3K(s,S~A)` | Updates internal state(s) on MAP3K: MAP3K.S I→A. Rate/expression: S. |
| 2 | `Unlabeled` | reversible | MAP3K, Scaff | `a, d1` | binding-pattern rewrite | `MAP3K(s,S~A) + Scaff(map3k) <-> MAP3K(s!1,S~A).Scaff(map3k!1)` | Reversibly forms binding contacts among MAP3K, Scaff through MAP3K.s, Scaff.map3k. Rate/expression: a, d1. |
| 3 | `Unlabeled` | one-way | MAP3K, Scaff | `d2` | binding-pattern rewrite | `MAP3K(s!1,S~I).Scaff(map3k!1) -> MAP3K(s,S~I) + Scaff(map3k)` | Releases binding contacts among MAP3K, Scaff by freeing MAP3K.s, Scaff.map3k. Rate/expression: d2. |
| 4 | `Unlabeled` | reversible | MAP2K, Scaff | `a, d1` | binding-pattern rewrite | `MAP2K(s,R1~Y,R2~Y) + Scaff(map2k) <-> MAP2K(s!1,R1~Y,R2~Y).Scaff(map2k!1)` | Reversibly forms binding contacts among MAP2K, Scaff through MAP2K.s, Scaff.map2k. Rate/expression: a, d1. |
| 5 | `Unlabeled` | reversible | MAP2K, Scaff | `a, d1` | binding-pattern rewrite | `MAP2K(s,R1~Yp,R2~Y) + Scaff(map2k) <-> MAP2K(s!1,R1~Yp,R2~Y).Scaff(map2k!1)` | Reversibly forms binding contacts among MAP2K, Scaff through MAP2K.s, Scaff.map2k. Rate/expression: a, d1. |
| 6 | `Unlabeled` | reversible | MAP2K, Scaff | `a, d1` | binding-pattern rewrite | `MAP2K(s,R1~Y,R2~Yp) + Scaff(map2k) <-> MAP2K(s!1,R1~Y,R2~Yp).Scaff(map2k!1)` | Reversibly forms binding contacts among MAP2K, Scaff through MAP2K.s, Scaff.map2k. Rate/expression: a, d1. |
| 7 | `Unlabeled` | reversible | MAP2K, Scaff | `a, d1` | binding-pattern rewrite | `MAP2K(s,R1~Yp,R2~Yp) + Scaff(map2k) <-> MAP2K(s!1,R1~Yp,R2~Yp).Scaff(map2k!1)` | Reversibly forms binding contacts among MAP2K, Scaff through MAP2K.s, Scaff.map2k. Rate/expression: a, d1. |
| 8 | `Unlabeled` | reversible | MAPK, Scaff | `a, d1` | binding-pattern rewrite | `MAPK(s,R1~Y,R2~Y) + Scaff(mapk) <-> MAPK(s!1,R1~Y,R2~Y).Scaff(mapk!1)` | Reversibly forms binding contacts among MAPK, Scaff through MAPK.s, Scaff.mapk. Rate/expression: a, d1. |
| 9 | `Unlabeled` | reversible | MAPK, Scaff | `a, d1` | binding-pattern rewrite | `MAPK(s,R1~Yp,R2~Y) + Scaff(mapk) <-> MAPK(s!1,R1~Yp,R2~Y).Scaff(mapk!1)` | Reversibly forms binding contacts among MAPK, Scaff through MAPK.s, Scaff.mapk. Rate/expression: a, d1. |
| 10 | `Unlabeled` | reversible | MAPK, Scaff | `a, d1` | binding-pattern rewrite | `MAPK(s,R1~Y,R2~Yp) + Scaff(mapk) <-> MAPK(s!1,R1~Y,R2~Yp).Scaff(mapk!1)` | Reversibly forms binding contacts among MAPK, Scaff through MAPK.s, Scaff.mapk. Rate/expression: a, d1. |
| 11 | `Unlabeled` | one-way | MAPK, Scaff | `d2` | binding-pattern rewrite | `MAPK(s!1,R1~Yp,R2~Yp).Scaff(mapk!1) -> MAPK(s,R1~Yp,R2~Yp) + Scaff(mapk)` | Releases binding contacts among MAPK, Scaff by freeing MAPK.s, Scaff.mapk. Rate/expression: d2. |
| 12 | `Unlabeled` | one-way | MAP2K, MAP3K, Scaff | `pscaff` | internal-state conversion/modification | `MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R1~Y) -> MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R1~Yp)` | Updates internal state(s) on MAP2K, MAP3K, Scaff: MAP2K.R1 Y→Yp. Rate/expression: pscaff. |
| 13 | `Unlabeled` | one-way | MAP2K, MAP3K, Scaff | `pscaff` | internal-state conversion/modification | `MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R2~Y) -> MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R2~Yp)` | Updates internal state(s) on MAP2K, MAP3K, Scaff: MAP2K.R2 Y→Yp. Rate/expression: pscaff. |
| 14 | `Unlabeled` | one-way | MAP2K, MAPK, Scaff | `pscaff` | internal-state conversion/modification | `MAPK(s!1,R1~Y).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp) -> MAPK(s!1,R1~Yp).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | Updates internal state(s) on MAP2K, MAPK, Scaff: MAPK.R1 Y→Yp. Rate/expression: pscaff. |
| 15 | `Unlabeled` | one-way | MAP2K, MAPK, Scaff | `pscaff` | internal-state conversion/modification | `MAPK(s!1,R2~Y).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp) -> MAPK(s!1,R2~Yp).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | Updates internal state(s) on MAP2K, MAPK, Scaff: MAPK.R2 Y→Yp. Rate/expression: pscaff. |
| 16 | `Unlabeled` | one-way | MAP3K | `u` | internal-state conversion/modification | `MAP3K(S~A) -> MAP3K(S~I)` | Updates internal state(s) on MAP3K: MAP3K.S A→I. Rate/expression: u. |
| 17 | `Unlabeled` | one-way | MAP2K | `u` | internal-state conversion/modification | `MAP2K(R1~Yp) -> MAP2K(R1~Y)` | Updates internal state(s) on MAP2K: MAP2K.R1 Yp→Y. Rate/expression: u. |
| 18 | `Unlabeled` | one-way | MAP2K | `u` | internal-state conversion/modification | `MAP2K(R2~Yp) -> MAP2K(R2~Y)` | Updates internal state(s) on MAP2K: MAP2K.R2 Yp→Y. Rate/expression: u. |
| 19 | `Unlabeled` | one-way | MAPK | `u` | internal-state conversion/modification | `MAPK(R1~Yp) -> MAPK(R1~Y)` | Updates internal state(s) on MAPK: MAPK.R1 Yp→Y. Rate/expression: u. |
| 20 | `Unlabeled` | one-way | MAPK | `u` | internal-state conversion/modification | `MAPK(R2~Yp) -> MAPK(R2~Y)` | Updates internal state(s) on MAPK: MAPK.R2 Yp→Y. Rate/expression: u. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `MAPKchainone` | `Molecules` | `MAPK(s!1,R1~Yp).Scaff(mapk!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | counts molecule-pattern matches |
| `MAPKchaintwo` | `Molecules` | `MAP3K(s!1,S~A).Scaff(map3k!1,map2k!2).MAP2K(s!2,R1~Yp,R2~Yp)` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

No active action block commands are declared.

## 9. Technical caveats and ambiguities

- The YAML description says actin dynamics, but the BNGL file is a MAP3K/MAP2K/MAPK scaffold model; the summary follows the BNGL content.

- MAP2K and MAPK each have two phosphorylation-state sites, so several rules enumerate singly and doubly phosphorylated scaffold-bound forms.

- The model has no actions block, so it defines the network logic but leaves execution workflow to the caller.
