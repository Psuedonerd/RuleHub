# Model Explanation: Blinov 2006

## 1. One-sentence summary

This model represents EGF receptor activation, receptor aggregation, receptor and Shc phosphorylation, and downstream adaptor complex formation.

## 2. Biological meaning

This model represents EGF receptor activation, receptor aggregation, receptor and Shc phosphorylation, and downstream adaptor complex formation. The local model comments and metadata give this context: check detailed balanced Ligand-receptor binding Note changed multiplicity Receptor-aggregation Transphosphorylation of egfr by RTK Dephosphorylayion Shc transphosph Y1068 activity Y1148 activity Cytosolic Strong differences are seen for R_G_S in comparison with path model # actions ## Equilibration Kinetics. The explanation below is therefore based on the local BNGL model file `Published/Blinov2006/Blinov_2006.bngl` and metadata file `Published/Blinov2006/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `egf`: egf. It has binding or interaction sites `r`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `egfr`: egfr. It has binding/interaction sites `l`, `r` and regulated state sites `Y1068~Y~pY`, `Y1148~Y~pY`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Shc`: Shc. It has binding/interaction sites `PTB` and regulated state sites `Y317~Y~pY`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Grb2`: Grb2. It has binding or interaction sites `SH2`, `SH3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Sos`: Sos. It has binding or interaction sites `dom`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `egf(r)                        egf_tot`
- `Grb2(SH2,SH3)                 Grb2_tot`
- `Shc(PTB,Y317~Y)               Shc_tot`
- `Sos(dom)                      Sos_tot`
- `egfr(l,r,Y1068~Y,Y1148~Y)     egfr_tot`
- `Grb2(SH2,SH3!1).Sos(dom!1)    Grb2_Sos_tot`

Important parameters include:

- `egf_tot       1.2e6`
- `egfr_tot      1.8e5`
- `Grb2_tot      1.0e5`
- `Shc_tot       2.7e5`
- `Sos_tot       1.3e4`
- `Grb2_Sos_tot  4.9e4`
- `kp1      1.667e-06`
- `km1           0.06`
- `kp2      5.556e-06`
- `km2            0.1`
- `kp3            0.5`
- `km3          4.505`
- `kp14             3`
- `km14          0.03`
- `km16         0.005`
- `kp9      8.333e-07`
- `km9           0.05`
- `kp10     5.556e-06`
- `km10          0.06`
- `kp11      1.25e-06`
- `km11          0.03`
- `kp13       2.5e-05`
- `km13           0.6`
- `kp15       2.5e-07`
- `km15           0.3`

Functions and simulation/action commands:

- `generate_network({overwrite=>1})`
- `simulate_ode({t_end=>100000,n_steps=>10,sparse=>1,steady_state=>1})`
- `writeSBML({})`
- `simulate_ode({t_end=>120,n_steps=>120,atol=>1e-8,rtol=>1e-8,sparse=>1})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Ligand-receptor binding**: Reversible binding/release. The nearby model comment says: “Ligand-receptor binding”. The rule involves `egf`, `egfr` and produces `egf`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp1,  km1`.
- **Receptor-aggregation**: Reversible binding/release. The nearby model comment says: “Receptor-aggregation”. The rule involves `egfr` and produces `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp2, km2`.
- **Transphosphorylation of egfr by RTK**: State change or catalytic conversion. The nearby model comment says: “Transphosphorylation of egfr by RTK”. The rule involves `egfr` and produces `egfr`. The encoded molecular change is `egfr` site `Y1068` changes from `Y` to `pY`; site `Y1068` changes from `Y` to `pY`. Rate parameter(s): `kp3`.
- **Transphosphorylation of egfr by RTK**: State change or catalytic conversion. The nearby model comment says: “Transphosphorylation of egfr by RTK”. The rule involves `egfr` and produces `egfr`. The encoded molecular change is `egfr` site `Y1148` changes from `Y` to `pY`; site `Y1148` changes from `Y` to `pY`. Rate parameter(s): `kp3`.
- **Dephosphorylayion**: State change or catalytic conversion. The nearby model comment says: “Dephosphorylayion”. The rule involves `egfr` and produces `egfr`. The encoded molecular change is `egfr` site `Y1068` changes from `pY` to `Y`; site `Y1068` changes from `pY` to `Y`. Rate parameter(s): `km3`.
- **Dephosphorylayion**: State change or catalytic conversion. The nearby model comment says: “Dephosphorylayion”. The rule involves `egfr` and produces `egfr`. The encoded molecular change is `egfr` site `Y1148` changes from `pY` to `Y`; site `Y1148` changes from `pY` to `Y`. Rate parameter(s): `km3`.
- **Shc transphosph**: State change or catalytic conversion. The nearby model comment says: “Shc transphosph”. The rule involves `Shc`, `egfr` and produces `Shc`, `egfr`. The encoded molecular change is site `Y317` changes from `Y` to `pY`. Rate parameter(s): `kp14`.
- **Shc transphosph**: State change or catalytic conversion. The nearby model comment says: “Shc transphosph”. The rule involves `Shc` and produces `Shc`. The encoded molecular change is `Shc` site `Y317` changes from `pY` to `Y`; site `Y317` changes from `pY` to `Y`. Rate parameter(s): `km14`.
- **Y1068 activity**: Reversible binding/release. The nearby model comment says: “Y1068 activity”. The rule involves `Grb2`, `egfr` and produces `Grb2`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp9, km9`.
- **Y1068 activity**: Reversible binding/release. The nearby model comment says: “Y1068 activity”. The rule involves `Grb2`, `egfr` and produces `Grb2`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp11, km11`.
- **Y1068 activity**: Reversible binding/release. The nearby model comment says: “Y1068 activity”. The rule involves `Grb2`, `Sos`, `egfr` and produces `Grb2`, `Sos`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp10, km10`.
- **Y1148 activity**: Reversible binding/release. The nearby model comment says: “Y1148 activity”. The rule involves `Shc`, `egfr` and produces `Shc`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp13, km13`.
- **Y1148 activity**: Reversible binding/release. The nearby model comment says: “Y1148 activity”. The rule involves `Shc`, `egfr` and produces `Shc`, `egfr`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp15, km15`.
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos`, `egfr` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Y1148 activity**: Unbinding or disassembly. The nearby model comment says: “Y1148 activity”. The rule involves `Grb2`, `Shc`, `Sos` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Cytosolic**: Reversible binding/release. The nearby model comment says: “Cytosolic”. The rule involves `Grb2`, `Shc` and produces `Grb2`, `Shc`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp21, km21`.
- **Cytosolic**: Reversible binding/release. The nearby model comment says: “Cytosolic”. The rule involves `Grb2`, `Shc` and produces `Grb2`, `Shc`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp23, km23`.
- **Cytosolic**: State change or catalytic conversion. The nearby model comment says: “Cytosolic”. The rule involves `Shc` and produces `Shc`. The encoded molecular change is `Shc` site `Y317` changes from `pY` to `Y`; site `Y317` changes from `pY` to `Y`. Rate parameter(s): `km16`.
- **Cytosolic**: Reversible binding/release. The nearby model comment says: “Cytosolic”. The rule involves `Grb2`, `Sos` and produces `Grb2`, `Sos`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp12, km12`.
- **Cytosolic**: Unbinding or disassembly. The nearby model comment says: “Cytosolic”. The rule involves `Grb2`, `Shc`, `Sos` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Cytosolic**: Unbinding or disassembly. The nearby model comment says: “Cytosolic”. The rule involves `Grb2`, `Shc`, `Sos` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Dimers` (Molecules) tracks patterns containing egfr.egfr. Pattern: `egfr.egfr`.
- `Sos_act` (Molecules) tracks bound complexes. Pattern: `Shc(PTB!+,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3), egfr(Y1068~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`.
- `RP` (Molecules) tracks bound complexes. Pattern: `egfr(Y1068~pY!?), egfr(Y1148~pY!?)`.
- `Shc_Grb` (Molecules) tracks bound complexes. Pattern: `Shc(Y317~pY!1).Grb2(SH2!1)`.
- `Shc_Grb_Sos` (Molecules) tracks bound complexes. Pattern: `Shc(Y317~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`.
- `R_Grb2` (Molecules) tracks bound complexes. Pattern: `egfr(Y1068~pY!1).Grb2(SH2!1)`.
- `R_Shc` (Molecules) tracks bound complexes. Pattern: `egfr(Y1148~pY!1).Shc(PTB!1,Y317~Y)`.
- `R_ShcP` (Molecules) tracks bound complexes. Pattern: `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!?)`.
- `ShcP` (Molecules) tracks bound complexes. Pattern: `Shc(Y317~pY!?)`.
- `R_G_S` (Molecules) tracks bound complexes. Pattern: `egfr(Y1068~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`.
- `R_S_G_S` (Molecules) tracks bound complexes. Pattern: `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3)`.
- `Efgr_total` (Molecules) tracks patterns containing egfr. Pattern: `egfr`.
- `Shc_total` (Molecules) tracks patterns containing Shc. Pattern: `Shc`.
- `Sos_total` (Molecules) tracks patterns containing Sos. Pattern: `Sos`.
- `Grb2_total` (Molecules) tracks patterns containing Grb2. Pattern: `Grb2`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_2006`
- Title/name: `Blinov 2006`
- Category: `signaling`
- Tags: `['published', 'blinov', '2006', 'egf', 'egfr', 'shc', 'grb2', 'sos']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Blinov_2006.bngl`
- Local BNGL file used: `Published/Blinov2006/Blinov_2006.bngl`
- Local YAML file used: `Published/Blinov2006/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
