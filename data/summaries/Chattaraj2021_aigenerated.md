# Model Explanation: Chattaraj 2021

## 1. One-sentence summary

This model represents multivalent Nephrin–Nck–NWASP clustering, using repeated binding sites to study formation and dissolution of signaling condensate-like complexes.

## 2. Biological meaning

This model represents multivalent Nephrin–Nck–NWASP clustering, using repeated binding sites to study formation and dissolution of signaling condensate-like complexes. The local model comments and metadata give this context: Clustering of three signaling molecules - Nephrin, Nck and NWASP 1. A. Chattaraj, M. L. Blinov and L. M. Loew. "The solubility product extends the buffering concept to heterotypic biomolecular condensates." eLife 2021, Vol. 10 Pages e67176, DOI: 10.7554/eLife.67176 (Figure 6) 2. A. Chattaraj and L. M. Loew. "The maximum solubility product marks the threshold for condensation of multivalent biomolecules". bioRxiv 2022, DOI: 10.1101/2022.10.04.510809 (Figure 6B). The explanation below is therefore based on the local BNGL model file `Published/Chattaraj2021/Chattaraj_2021.bngl` and metadata file `Published/Chattaraj2021/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Nephrin`: Nephrin. It has binding or interaction sites `pY1`, `pY2`, `pY3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Nck`: Nck. It has binding or interaction sites `S1`, `S2`, `S3`, `Sh2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `NWASP`: NWASP. It has binding or interaction sites `p1`, `p2`, `p3`, `p4`, `p5`, `p6`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `1 Nephrin(pY1,pY2,pY3) 300`
- `2 Nck(S1,S2,S3,Sh2) 900`
- `3 NWASP(p1,p2,p3,p4,p5,p6)	450`

Important parameters include:

- `kd_12	3500`
- `kd_23	3500`
- `koff_23	1000`
- `kon_23	koff_23/kd_23`
- `koff_12	1000`
- `kon_12	koff_12/kd_12`

Functions and simulation/action commands:

- `writeXML()`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **_01_S1_P1**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_02_S2_P1**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_03_S3_P1**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_06_S3_P2**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_05_S2_P2**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_04_S1_P2**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_08_S2_P3**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_07_S1_P3**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_09_S3_P3**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_10_S1_P4**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_11_S2_P4**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_12_S3_P4**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_13_S1_P5**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_14_S2_P5**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_15_S3_P5**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_16_S1_P6**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_17_S3_P6**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_18_S2_P6**: Reversible binding/release. The rule involves `NWASP`, `Nck` and produces `NWASP`, `Nck`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_23,  koff_23`.
- **_19_pY1_sh2**: Reversible binding/release. The rule involves `Nck`, `Nephrin` and produces `Nck`, `Nephrin`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_12,  koff_12`.
- **_20_pY2_sh2**: Reversible binding/release. The rule involves `Nck`, `Nephrin` and produces `Nck`, `Nephrin`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_12,  koff_12`.
- **_21_pY3_sh2**: Reversible binding/release. The rule involves `Nck`, `Nephrin` and produces `Nck`, `Nephrin`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_12,  koff_12`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `tot_Nck` (Molecules) tracks patterns containing Nck. Pattern: `Nck()`.
- `free_Nck` (Molecules) tracks patterns containing Nck. Pattern: `Nck(S1,S2,S3,Sh2)`.
- `tot_NWASP` (Molecules) tracks patterns containing NWASP. Pattern: `NWASP()`.
- `free_NWASP` (Molecules) tracks patterns containing NWASP. Pattern: `NWASP(p1,p2,p3,p4,p5,p6)`.
- `tot_Nephrin` (Molecules) tracks patterns containing Nephrin. Pattern: `Nephrin()`.
- `free_Nephrin` (Molecules) tracks patterns containing Nephrin. Pattern: `Nephrin(pY1,pY2,pY3)`.
- `fully_bound_Nephrin` (Molecules) tracks bound complexes. Pattern: `Nephrin(pY1!+,pY2!+,pY3!+)`.
- `fully_bound_Nck` (Molecules) tracks bound complexes. Pattern: `Nck(S1!+,S2!+,S3!+,Sh2!+)`.
- `fully_bound_NWASP` (Molecules) tracks bound complexes. Pattern: `NWASP(p1!+,p2!+,p3!+,p4!+,p5!+,p6!+)`.
- `cluster_neph_nck_nw` (Molecules) tracks patterns containing NWASP, Nck, Nephrin. Pattern: `Nephrin().Nck().NWASP()`.
- `cluster_nck_nw` (Molecules) tracks patterns containing NWASP, Nck. Pattern: `Nck().NWASP()`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Chattaraj_2021`
- Title/name: `Chattaraj 2021`
- Category: `signaling`
- Tags: `['published', 'chattaraj', '2021', 'nephrin', 'nck', 'nwasp', 'writexml']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Chattaraj_2021.bngl`
- Local BNGL file used: `Published/Chattaraj2021/Chattaraj_2021.bngl`
- Local YAML file used: `Published/Chattaraj2021/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `true`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
