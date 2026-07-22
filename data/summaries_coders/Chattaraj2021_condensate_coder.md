# Coder Model Explanation: Chattaraj 2021

## 1. Model identity and scope

- **Model id:** `Chattaraj_2021`
- **Title:** Chattaraj 2021
- **BNGL path:** `Published/Chattaraj2021/Chattaraj_2021.bngl`
- **YAML path:** `Published/Chattaraj2021/metadata.yaml`
- **Metadata description:** The YAML says “NFkB oscillations,” but the BNGL comments and model body describe Nephrin/Nck/NWASP multivalent clustering.
- **Scope:** This file is a heterotypic condensate/clustering model with three molecule types. Nephrin contributes three phosphotyrosine-like sites (`pY1`, `pY2`, `pY3`) that bind the Nck `Sh2` site. Nck also contributes three SH3-like sites (`S1`, `S2`, `S3`) that each bind NWASP proline sites (`p1` through `p6`). The entire behavior is encoded as 21 reversible site-to-site binding rules; there are no internal state changes, compartments, anchors, or functions.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 6 parameters: two dissociation constants, two off-rates, and two derived on-rates for Nephrin-Nck and Nck-NWASP binding. |
| Compartments | No | No compartment block. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 3 molecule types: `Nephrin`, `Nck`, and `NWASP`. |
| Seed/species | Yes | 3 initial pools: 300 Nephrin, 900 Nck, 450 NWASP. |
| Observables | Yes | 11 observables for total/free molecules, fully bound molecules, and mixed clusters. |
| Functions | No | No functions block; rate laws are direct parameters. |
| Reaction rules | Yes | 21 reversible binding rules. |
| Actions | Yes | One inline `writeXML()` command after the model. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `kd_12` | `3500` | Nephrin-Nck equilibrium scale for rules binding `Nephrin.pY*` to `Nck.Sh2`. |
| `kd_23` | `3500` | Nck-NWASP equilibrium scale for rules binding `Nck.S*` to `NWASP.p*`. |
| `koff_23` | `1000` | Reverse rate for all Nck SH3-site/NWASP proline-site rules. |
| `kon_23` | `koff_23/kd_23` | Forward rate for all Nck SH3-site/NWASP proline-site rules. |
| `koff_12` | `1000` | Reverse rate for all Nephrin phosphotyrosine/Nck SH2 rules. |
| `kon_12` | `koff_12/kd_12` | Forward rate for all Nephrin phosphotyrosine/Nck SH2 rules. |

No functions are declared. Every rule uses either `kon_23, koff_23` or `kon_12, koff_12`.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Nephrin` | 3 | `pY1`, `pY2`, `pY3` | none | none | All three sites bind `Nck.Sh2`. | Multivalent upstream scaffold; no phosphorylation state is modeled even though names contain `pY`. |
| `Nck` | 4 | `S1`, `S2`, `S3`, `Sh2` | none | none | `Sh2` binds Nephrin; `S1`, `S2`, `S3` bind NWASP. | Central adaptor connecting Nephrin and NWASP. |
| `NWASP` | 6 | `p1`, `p2`, `p3`, `p4`, `p5`, `p6` | none | none | Every `p*` site can bind Nck `S1`, `S2`, or `S3`. | Six-site multivalent ligand for Nck SH3 sites. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. The initial condition starts all three molecules free: `Nephrin(pY1,pY2,pY3)` at 300, `Nck(S1,S2,S3,Sh2)` at 900, and `NWASP(p1,p2,p3,p4,p5,p6)` at 450. Because all rules are reversible and do not change internal states, cluster composition is controlled by multivalent site occupancy and the two affinity classes.

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rules 1-18 enumerate every allowed Nck SH3-site/NWASP proline-site contact, one Nck site at a time. Rules 19-21 enumerate the three Nephrin/Nck contacts through Nck `Sh2`. Every row below forms or releases exactly one bond and leaves all other sites unchanged.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `_01_S1_P1` | reversible | `Nck.S1` + `NWASP.p1` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p1!1`. | Allows Nck SH3 site `S1` to occupy NWASP proline site `p1`. |
| 2 | `_02_S2_P1` | reversible | `Nck.S2` + `NWASP.p1` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p1!1`. | Allows Nck `S2` to bind the same NWASP `p1` class as an alternative SH3 contact. |
| 3 | `_03_S3_P1` | reversible | `Nck.S3` + `NWASP.p1` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p1!1`. | Allows Nck `S3` to bind NWASP `p1`. |
| 4 | `_06_S3_P2` | reversible | `Nck.S3` + `NWASP.p2` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p2!1`. | Adds the `S3`/`p2` edge to the SH3-proline interaction graph. |
| 5 | `_05_S2_P2` | reversible | `Nck.S2` + `NWASP.p2` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p2!1`. | Adds the `S2`/`p2` edge. |
| 6 | `_04_S1_P2` | reversible | `Nck.S1` + `NWASP.p2` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p2!1`. | Adds the `S1`/`p2` edge. |
| 7 | `_08_S2_P3` | reversible | `Nck.S2` + `NWASP.p3` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p3!1`. | Adds the `S2`/`p3` edge. |
| 8 | `_07_S1_P3` | reversible | `Nck.S1` + `NWASP.p3` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p3!1`. | Adds the `S1`/`p3` edge. |
| 9 | `_09_S3_P3` | reversible | `Nck.S3` + `NWASP.p3` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p3!1`. | Adds the `S3`/`p3` edge. |
| 10 | `_10_S1_P4` | reversible | `Nck.S1` + `NWASP.p4` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p4!1`. | Adds the `S1`/`p4` edge. |
| 11 | `_11_S2_P4` | reversible | `Nck.S2` + `NWASP.p4` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p4!1`. | Adds the `S2`/`p4` edge. |
| 12 | `_12_S3_P4` | reversible | `Nck.S3` + `NWASP.p4` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p4!1`. | Adds the `S3`/`p4` edge. |
| 13 | `_13_S1_P5` | reversible | `Nck.S1` + `NWASP.p5` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p5!1`. | Adds the `S1`/`p5` edge. |
| 14 | `_14_S2_P5` | reversible | `Nck.S2` + `NWASP.p5` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p5!1`. | Adds the `S2`/`p5` edge. |
| 15 | `_15_S3_P5` | reversible | `Nck.S3` + `NWASP.p5` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p5!1`. | Adds the `S3`/`p5` edge. |
| 16 | `_16_S1_P6` | reversible | `Nck.S1` + `NWASP.p6` | `kon_23, koff_23` | Forms/releases `Nck.S1!1`–`NWASP.p6!1`. | Adds the `S1`/`p6` edge. |
| 17 | `_17_S3_P6` | reversible | `Nck.S3` + `NWASP.p6` | `kon_23, koff_23` | Forms/releases `Nck.S3!1`–`NWASP.p6!1`. | Adds the `S3`/`p6` edge. |
| 18 | `_18_S2_P6` | reversible | `Nck.S2` + `NWASP.p6` | `kon_23, koff_23` | Forms/releases `Nck.S2!1`–`NWASP.p6!1`. | Adds the `S2`/`p6` edge; ordering in source places it after `S3`/`p6`. |
| 19 | `_19_pY1_sh2` | reversible | `Nephrin.pY1` + `Nck.Sh2` | `kon_12, koff_12` | Forms/releases `Nephrin.pY1!1`–`Nck.Sh2!1`. | Connects Nephrin site `pY1` to the Nck adaptor through SH2 binding. |
| 20 | `_20_pY2_sh2` | reversible | `Nephrin.pY2` + `Nck.Sh2` | `kon_12, koff_12` | Forms/releases `Nephrin.pY2!1`–`Nck.Sh2!1`. | Connects Nephrin site `pY2` to Nck. |
| 21 | `_21_pY3_sh2` | reversible | `Nephrin.pY3` + `Nck.Sh2` | `kon_12, koff_12` | Forms/releases `Nephrin.pY3!1`–`Nck.Sh2!1`. | Connects Nephrin site `pY3` to Nck, completing the 3-site Nephrin/Nck binding family. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `tot_Nck` | `Molecules` | `Nck()` | Counts all Nck molecules regardless of site occupancy. |
| `free_Nck` | `Molecules` | `Nck(S1,S2,S3,Sh2)` | Counts Nck with all four sites unbound. |
| `tot_NWASP` | `Molecules` | `NWASP()` | Counts all NWASP molecules. |
| `free_NWASP` | `Molecules` | `NWASP(p1,p2,p3,p4,p5,p6)` | Counts NWASP with all six proline sites free. |
| `tot_Nephrin` | `Molecules` | `Nephrin()` | Counts all Nephrin molecules. |
| `free_Nephrin` | `Molecules` | `Nephrin(pY1,pY2,pY3)` | Counts Nephrin with no Nck bound. |
| `fully_bound_Nephrin` | `Molecules` | `Nephrin(pY1!+,pY2!+,pY3!+)` | Counts Nephrin molecules with all three pY sites occupied. |
| `fully_bound_Nck` | `Molecules` | `Nck(S1!+,S2!+,S3!+,Sh2!+)` | Counts Nck molecules whose three SH3 sites and SH2 site are all occupied. |
| `fully_bound_NWASP` | `Molecules` | `NWASP(p1!+,p2!+,p3!+,p4!+,p5!+,p6!+)` | Counts NWASP molecules with all six proline sites occupied. |
| `cluster_neph_nck_nw` | `Molecules` | `Nephrin().Nck().NWASP()` | Counts complexes containing at least one Nephrin, Nck, and NWASP molecule. |
| `cluster_nck_nw` | `Molecules` | `Nck().NWASP()` | Counts Nck/NWASP-containing complexes with or without Nephrin. |

## 8. Actions and simulation workflow

`writeXML()` is called after `end model`, so the file is set up to export the model to XML rather than run a simulation inside the BNGL file.

## 9. Technical caveats and ambiguities

- The YAML description does not match the BNGL content; the BNGL comments and molecules clearly describe Nephrin/Nck/NWASP clustering.
- Site names such as `pY` and `p` imply biological motifs, but the model contains no internal phosphorylation states; they are binding sites only.
- The 18 Nck/NWASP rules are explicit individual edges, not one wildcard rule, so site-specific occupancy is preserved in generated complexes.
