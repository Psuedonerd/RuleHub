# Coder Model Explanation: Chattaraj 2021

## 1. Model identity and scope

- **Model id:** `Chattaraj_2021`
- **Title:** Chattaraj 2021
- **BNGL path:** `Published/Chattaraj2021/Chattaraj_2021.bngl`
- **YAML path:** `Published/Chattaraj2021/metadata.yaml`
- **Metadata description:** NFkB oscillations
- **Scope:** A multivalent binding/condensation model for Nephrin, Nck, and NWASP: three Nephrin phosphotyrosines bind Nck SH2, while three Nck SH3 sites bind six NWASP proline-rich motifs to generate heterotypic clusters.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 6 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 3 molecule type entries. |
| Seed/species | Yes | 3 initial species entries. |
| Observables | Yes | 11 observable entries. |
| Functions | No | 0 function entries. |
| Reaction rules | Yes | 21 reaction rules. |
| Actions | Yes | 1 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `kd_12` | `3500` | Kd: binding affinity, kon: binding rate constant, koff: unbinding rate constant |
| `kd_23` | `3500` | kinetic or model-control parameter |
| `koff_23` | `1000` | kinetic or model-control parameter |
| `kon_23` | `koff_23/kd_23` | kinetic or model-control parameter |
| `koff_12` | `1000` | kinetic or model-control parameter |
| `kon_12` | `koff_12/kd_12` | kinetic or model-control parameter |

No separate functions block is declared; rates are direct parameters or expressions in rule rows.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Nephrin` | 3 | pY1, pY2, pY3 | none declared | none | binding/modification candidate sites: pY1, pY2, pY3 |  |
| `Nck` | 4 | S1, S2, S3, Sh2 | none declared | none | binding/modification candidate sites: S1, S2, S3, Sh2 |  |
| `NWASP` | 6 | p1, p2, p3, p4, p5, p6 | none declared | none | binding/modification candidate sites: p1, p2, p3, p4, p5, p6 |  |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `1 Nephrin(pY1,pY2,pY3)` | `300` | starting species pool for this pattern |
| `2 Nck(S1,S2,S3,Sh2)` | `900` | starting species pool for this pattern |
| `3 NWASP(p1,p2,p3,p4,p5,p6)` | `450` | starting species pool for this pattern |

## 6. Complete reaction-rule inventory

The source contains **21** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `_01_S1_P1` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p1) <-> Nck(S1!1).NWASP(p1!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p1, Nck.S1. Rate/expression: kon_23, koff_23. |
| 2 | `_02_S2_P1` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p1) <-> Nck(S2!1).NWASP(p1!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p1, Nck.S2. Rate/expression: kon_23, koff_23. |
| 3 | `_03_S3_P1` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p1) <-> Nck(S3!1).NWASP(p1!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p1, Nck.S3. Rate/expression: kon_23, koff_23. |
| 4 | `_06_S3_P2` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p2) <-> Nck(S3!1).NWASP(p2!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p2, Nck.S3. Rate/expression: kon_23, koff_23. |
| 5 | `_05_S2_P2` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p2) <-> Nck(S2!1).NWASP(p2!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p2, Nck.S2. Rate/expression: kon_23, koff_23. |
| 6 | `_04_S1_P2` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p2) <-> Nck(S1!1).NWASP(p2!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p2, Nck.S1. Rate/expression: kon_23, koff_23. |
| 7 | `_08_S2_P3` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p3) <-> Nck(S2!1).NWASP(p3!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p3, Nck.S2. Rate/expression: kon_23, koff_23. |
| 8 | `_07_S1_P3` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p3) <-> Nck(S1!1).NWASP(p3!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p3, Nck.S1. Rate/expression: kon_23, koff_23. |
| 9 | `_09_S3_P3` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p3) <-> Nck(S3!1).NWASP(p3!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p3, Nck.S3. Rate/expression: kon_23, koff_23. |
| 10 | `_10_S1_P4` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p4) <-> Nck(S1!1).NWASP(p4!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p4, Nck.S1. Rate/expression: kon_23, koff_23. |
| 11 | `_11_S2_P4` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p4) <-> Nck(S2!1).NWASP(p4!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p4, Nck.S2. Rate/expression: kon_23, koff_23. |
| 12 | `_12_S3_P4` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p4) <-> Nck(S3!1).NWASP(p4!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p4, Nck.S3. Rate/expression: kon_23, koff_23. |
| 13 | `_13_S1_P5` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p5) <-> Nck(S1!1).NWASP(p5!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p5, Nck.S1. Rate/expression: kon_23, koff_23. |
| 14 | `_14_S2_P5` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p5) <-> Nck(S2!1).NWASP(p5!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p5, Nck.S2. Rate/expression: kon_23, koff_23. |
| 15 | `_15_S3_P5` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p5) <-> Nck(S3!1).NWASP(p5!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p5, Nck.S3. Rate/expression: kon_23, koff_23. |
| 16 | `_16_S1_P6` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S1) + NWASP(p6) <-> Nck(S1!1).NWASP(p6!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p6, Nck.S1. Rate/expression: kon_23, koff_23. |
| 17 | `_17_S3_P6` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S3) + NWASP(p6) <-> Nck(S3!1).NWASP(p6!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p6, Nck.S3. Rate/expression: kon_23, koff_23. |
| 18 | `_18_S2_P6` | reversible | NWASP, Nck | `kon_23, koff_23` | binding-pattern rewrite | `Nck(S2) + NWASP(p6) <-> Nck(S2!1).NWASP(p6!1)` | Reversibly forms binding contacts among NWASP, Nck through NWASP.p6, Nck.S2. Rate/expression: kon_23, koff_23. |
| 19 | `_19_pY1_sh2` | reversible | Nck, Nephrin | `kon_12, koff_12` | binding-pattern rewrite | `Nephrin(pY1) + Nck(Sh2) <-> Nephrin(pY1!1).Nck(Sh2!1)` | Reversibly forms binding contacts among Nck, Nephrin through Nck.Sh2, Nephrin.pY1. Rate/expression: kon_12, koff_12. |
| 20 | `_20_pY2_sh2` | reversible | Nck, Nephrin | `kon_12, koff_12` | binding-pattern rewrite | `Nephrin(pY2) + Nck(Sh2) <-> Nephrin(pY2!1).Nck(Sh2!1)` | Reversibly forms binding contacts among Nck, Nephrin through Nck.Sh2, Nephrin.pY2. Rate/expression: kon_12, koff_12. |
| 21 | `_21_pY3_sh2` | reversible | Nck, Nephrin | `kon_12, koff_12` | binding-pattern rewrite | `Nephrin(pY3) + Nck(Sh2) <-> Nephrin(pY3!1).Nck(Sh2!1)` | Reversibly forms binding contacts among Nck, Nephrin through Nck.Sh2, Nephrin.pY3. Rate/expression: kon_12, koff_12. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `tot_Nck` | `Molecules` | `Nck()` | counts molecule-pattern matches |
| `free_Nck` | `Molecules` | `Nck(S1,S2,S3,Sh2)` | counts molecule-pattern matches |
| `tot_NWASP` | `Molecules` | `NWASP()` | counts molecule-pattern matches |
| `free_NWASP` | `Molecules` | `NWASP(p1,p2,p3,p4,p5,p6)` | counts molecule-pattern matches |
| `tot_Nephrin` | `Molecules` | `Nephrin()` | counts molecule-pattern matches |
| `free_Nephrin` | `Molecules` | `Nephrin(pY1,pY2,pY3)` | counts molecule-pattern matches |
| `fully_bound_Nephrin` | `Molecules` | `Nephrin(pY1!+,pY2!+,pY3!+)` | counts molecule-pattern matches |
| `fully_bound_Nck` | `Molecules` | `Nck(S1!+,S2!+,S3!+,Sh2!+)` | counts molecule-pattern matches |
| `fully_bound_NWASP` | `Molecules` | `NWASP(p1!+,p2!+,p3!+,p4!+,p5!+,p6!+)` | counts molecule-pattern matches |
| `cluster_neph_nck_nw` | `Molecules` | `Nephrin().Nck().NWASP()` | counts molecule-pattern matches |
| `cluster_nck_nw` | `Molecules` | `Nck().NWASP()` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

1. `writeXML()` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- The YAML description says NFkB oscillations, but the BNGL comments and molecule names identify a Nephrin/Nck/NWASP condensate model; the summary follows the BNGL source.

- All 21 rules are reversible binding rules; there are no explicit synthesis, degradation, state-change, or compartmental transport rules.

- The model uses multivalent sites to represent condensate-forming connectivity, not explicit liquid-phase compartments or anchors.
