# Model Explanation: Cheemalavagu 2024

## 1. One-sentence summary

This compact model shows how SH2B dimerization can scaffold JAK2 molecules so that JAK2 becomes phosphorylated more efficiently inside a multimeric complex.

## 2. Biological meaning

This compact model shows how SH2B dimerization can scaffold JAK2 molecules so that JAK2 becomes phosphorylated more efficiently inside a multimeric complex. The local model comments and metadata give this context: reaction rules: 29 unknown parameters: 44 IL-6 constants IL-10 constants common constants STAT parameters initial ligand concentrations initial receptor concentrations initial jak concentrations negtaive regulators initial unphosphorylated STAT3 IL-6 binds to receptor IL-6 receptor complex forms IL-6 receptor complex binds jak1 (this can happen before/after jak2). The explanation below is therefore based on the local BNGL model file `Published/CheemalavaguJAKSTAT/Cheemalavagu_JAK_STAT.bngl` and metadata file `Published/CheemalavaguJAKSTAT/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L1`: L1. It has binding or interaction sites `il6r`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IL6R`: IL6R. It has binding or interaction sites `l1`, `gp130`, `jak1`, `socs3`, `stat`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `GP130`: GP130. It has binding or interaction sites `il6r`, `jak2`, `socs3`, `stat`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `L2`: L2. It has binding or interaction sites `il10r1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IL10R1`: IL10R1. It has binding or interaction sites `l2`, `il10r2`, `jak1`, `stat`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IL10R2`: IL10R2. It has binding or interaction sites `il10r1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `JAK1`: JAK1. It has binding or interaction sites `rec`, `socs1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `JAK2`: JAK2. It has binding or interaction sites `gp130`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `SOCS3`: SOCS3. It has binding or interaction sites `il6r`, `gp130`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `SOCS1`: SOCS1. It has binding or interaction sites `jak1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PTP3`: PTP3. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PTP1`: PTP1. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `S3`: S3. It has state sites `Y~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `S1`: S1. It has state sites `Y~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L1(il6r) L1_0`
- `IL6R(l1,gp130,jak1,socs3,stat) IL6R_0`
- `GP130(il6r,jak2,socs3,stat) GP130_0`
- `L2(il10r1) L2_0`
- `IL10R1(l2,il10r2,jak1,stat) IL10R1_0`
- `IL10R2(il10r1) IL10R2_0`
- `JAK1(rec,socs1) JAK1_0`
- `JAK2(gp130) JAK2_0`
- `SOCS3(il6r,gp130) SOCS3_0`
- `SOCS1(jak1) SOCS1_0`
- `PTP3() PTP3_0`
- `PTP1() PTP1_0`
- `S3(Y~0) S3_0`
- `S1(Y~0) S1_0`

Important parameters include:

- `il6_il6r_binding 1`
- `il6_il6r_unbinding 1`
- `il6r_gp130_binding 1`
- `il6r_gp130_unbinding 1`
- `il6_complex_jak1_binding 1`
- `il6_complex_jak1_unbinding 1`
- `il6_complex_jak2_binding 1`
- `il6_complex_jak2_unbinding 1`
- `SOCS3_il6r_binding 1`
- `SOCS3_il6r_unbinding 1`
- `SOCS3_gp130_binding 1`
- `SOCS3_gp130_unbinding 1`
- `il6_jak1_med_STAT3_act 1`
- `il6_jak1_med_STAT1_act 1`
- `il6_jak2_med_STAT3_act 1`
- `il6_jak2_med_STAT1_act 1`
- `il10_il10r1_binding 1`
- `il10_il10r1_unbinding 1`
- `il10r1_il10r2_binding 1`
- `il10r1_il10r2_unbinding 1`
- `il10_complex_jak1_binding 1`
- `il10_complex_jak1_unbinding 1`
- `il10_jak1_med_STAT3_act 1`
- `il10_jak1_med_STAT1_act 1`
- `SOCS1_jak1_binding 1`

Functions and simulation/action commands:

- `generate_network({overwrite=>1})`
- `writeMexfile({t_start=>0,t_end=>90,n_steps=>91,atol=>1e-10})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **IL-6 binds to receptor**: Reversible binding/release. The nearby model comment says: “IL-6 binds to receptor”. The rule involves `IL6R`, `L1` and produces `IL6R`, `L1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il6_il6r_binding, il6_il6r_unbinding`.
- **IL-6 receptor complex forms**: Reversible binding/release. The nearby model comment says: “IL-6 receptor complex forms”. The rule involves `GP130`, `IL6R`, `L1` and produces `GP130`, `IL6R`, `L1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il6r_gp130_binding, il6r_gp130_unbinding`.
- **IL-6 receptor complex binds jak1 (this can happen before/after jak2)**: Reversible binding/release. The nearby model comment says: “IL-6 receptor complex binds jak1 (this can happen before/after jak2)”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1` and produces `GP130`, `IL6R`, `JAK1`, `L1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il6_complex_jak1_binding, il6_complex_jak1_unbinding`.
- **IL-6 receptor complex binds jak2 (this can happen before/after jak1)**: Reversible binding/release. The nearby model comment says: “IL-6 receptor complex binds jak2 (this can happen before/after jak1)”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1` and produces `GP130`, `IL6R`, `JAK2`, `L1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il6_complex_jak2_binding, il6_complex_jak2_unbinding`.
- **SOCS3-mediated Jak1 inhibition**: Reversible binding/release. The nearby model comment says: “SOCS3-mediated Jak1 inhibition”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `SOCS3` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `SOCS3`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `SOCS3_il6r_binding, SOCS3_il6r_unbinding`.
- **SOCS3-mediated Jak2 inhibition**: Reversible binding/release. The nearby model comment says: “SOCS3-mediated Jak2 inhibition”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1`, `SOCS3` and produces `GP130`, `IL6R`, `JAK2`, `L1`, `SOCS3`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `SOCS3_gp130_binding, SOCS3_gp130_unbinding`.
- **SOCS1-mediated IL-6-Jak1 inhibition**: Reversible binding/release. The nearby model comment says: “SOCS1-mediated IL-6-Jak1 inhibition”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `SOCS1` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `SOCS1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `SOCS1_jak1_binding, SOCS1_jak1_unbinding`.
- **this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS**: Binding or assembly. The nearby model comment says: “this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `S3` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `S3`. The encoded molecular change is `S3` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il6_jak1_med_STAT3_act`.
- **IL-6/Jak1 activated pSTAT3 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-6/Jak1 activated pSTAT3 unbinding”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `S3` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `S3`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT3_rec_dissoc`.
- **this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS**: Binding or assembly. The nearby model comment says: “this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `S1` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `S1`. The encoded molecular change is `S1` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il6_jak1_med_STAT1_act`.
- **IL-6/Jak1 activated pSTAT1 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-6/Jak1 activated pSTAT1 unbinding”. The rule involves `GP130`, `IL6R`, `JAK1`, `L1`, `S1` and produces `GP130`, `IL6R`, `JAK1`, `L1`, `S1`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT1_rec_dissoc`.
- **this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS**: Binding or assembly. The nearby model comment says: “this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1`, `S3` and produces `GP130`, `IL6R`, `JAK2`, `L1`, `S3`. The encoded molecular change is `S3` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il6_jak2_med_STAT3_act`.
- **IL-6/Jak2 activated pSTAT3 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-6/Jak2 activated pSTAT3 unbinding”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1`, `S3` and produces `GP130`, `IL6R`, `JAK2`, `L1`, `S3`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT3_rec_dissoc`.
- **this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS**: Binding or assembly. The nearby model comment says: “this rule means that STAT will always get phosphorylated when it binds; only dissociates to induce SOCS”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1`, `S1` and produces `GP130`, `IL6R`, `JAK2`, `L1`, `S1`. The encoded molecular change is `S1` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il6_jak2_med_STAT1_act`.
- **IL-6/Jak2 activated pSTAT1 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-6/Jak2 activated pSTAT1 unbinding”. The rule involves `GP130`, `IL6R`, `JAK2`, `L1`, `S1` and produces `GP130`, `IL6R`, `JAK2`, `L1`, `S1`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT1_rec_dissoc`.
- **IL-10 binds to receptor**: Reversible binding/release. The nearby model comment says: “IL-10 binds to receptor”. The rule involves `IL10R1`, `L2` and produces `IL10R1`, `L2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il10_il10r1_binding, il10_il10r1_unbinding`.
- **IL-10 receptor complex forms**: Reversible binding/release. The nearby model comment says: “IL-10 receptor complex forms”. The rule involves `IL10R1`, `IL10R2`, `L2` and produces `IL10R1`, `IL10R2`, `L2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il10r1_il10r2_binding, il10r1_il10r2_unbinding`.
- **IL-10 receptor complex binds jak1**: Reversible binding/release. The nearby model comment says: “IL-10 receptor complex binds jak1”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `il10_complex_jak1_binding, il10_complex_jak1_unbinding`.
- **SOCS1-mediated IL-10-Jak1 inhibition**: Reversible binding/release. The nearby model comment says: “SOCS1-mediated IL-10-Jak1 inhibition”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2`, `SOCS1` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`, `SOCS1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `SOCS1_jak1_binding, SOCS1_jak1_unbinding`.
- **IL-10/Jak1-mediated STAT3 activation**: Binding or assembly. The nearby model comment says: “IL-10/Jak1-mediated STAT3 activation”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S3` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S3`. The encoded molecular change is `S3` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il10_jak1_med_STAT3_act`.
- **IL-10/Jak1 activated pSTAT3 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-10/Jak1 activated pSTAT3 unbinding”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S3` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S3`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT3_rec_dissoc`.
- **IL-10/Jak1-mediated STAT1 activation**: Binding or assembly. The nearby model comment says: “IL-10/Jak1-mediated STAT1 activation”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S1` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S1`. The encoded molecular change is `S1` site `Y` changes from `0` to `P`; site `Y` changes from `0` to `P`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `il10_jak1_med_STAT1_act`.
- **IL-10/Jak1 activated pSTAT1 unbinding**: Unbinding or disassembly. The nearby model comment says: “IL-10/Jak1 activated pSTAT1 unbinding”. The rule involves `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S1` and produces `IL10R1`, `IL10R2`, `JAK1`, `L2`, `S1`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `pSTAT1_rec_dissoc`.
- **PTP3-mediated STAT3 deactivation**: State change or catalytic conversion. The nearby model comment says: “PTP3-mediated STAT3 deactivation”. The rule involves `PTP3`, `S3` and produces `PTP3`, `S3`. The encoded molecular change is `S3` site `Y` changes from `P` to `0`; site `Y` changes from `P` to `0`. Rate parameter(s): `PTP_med_STAT3_deact`.
- **PTP1-mediated STAT1 deactivation**: State change or catalytic conversion. The nearby model comment says: “PTP1-mediated STAT1 deactivation”. The rule involves `PTP1`, `S1` and produces `PTP1`, `S1`. The encoded molecular change is `S1` site `Y` changes from `P` to `0`; site `Y` changes from `P` to `0`. Rate parameter(s): `PTP_med_STAT1_deact`.
- **STAT3 SOCS3 protein production**: Production, removal, or biochemical conversion. The nearby model comment says: “STAT3 SOCS3 protein production”. The rule involves `S3` and produces `S3`, `SOCS3`. Rate parameter(s): `STAT3_SOCS3_ind`.
- **STAT3 SOCS1 protein production**: Production, removal, or biochemical conversion. The nearby model comment says: “STAT3 SOCS1 protein production”. The rule involves `S3` and produces `S3`, `SOCS1`. Rate parameter(s): `STAT3_SOCS1_ind`.
- **STAT1 SOCS3 protein production**: Production, removal, or biochemical conversion. The nearby model comment says: “STAT1 SOCS3 protein production”. The rule involves `S1` and produces `S1`, `SOCS3`. Rate parameter(s): `STAT1_SOCS3_ind`.
- **STAT1 SOCS1 protein production**: Production, removal, or biochemical conversion. The nearby model comment says: “STAT1 SOCS1 protein production”. The rule involves `S1` and produces `S1`, `SOCS1`. Rate parameter(s): `STAT1_SOCS1_ind`.
- **SOCS3 protein degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “SOCS3 protein degradation”. The rule involves `SOCS3` and produces the listed product pattern. Rate parameter(s): `SOCS3_degrad`.
- **SOCS1 protein degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “SOCS1 protein degradation”. The rule involves `SOCS1` and produces the listed product pattern. Rate parameter(s): `SOCS1_degrad`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `total_pS3` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!8).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S3(Y~P!8),S3(Y~P),IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!10).JAK2(gp130!4).S3(Y~P!10),IL10R1(l2!1,il10r2!2,jak1!3,stat!5).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S3(Y~P!5)`.
- `total_pS1` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!9).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S1(Y~P!9),S1(Y~P),IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!11).JAK2(gp130!4).S1(Y~P!11),IL10R1(l2!1,il10r2!2,jak1!3,stat!6).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S1(Y~P!6)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Cheemalavagu_JAK_STAT`
- Title/name: `Cheemalavagu 2024`
- Category: `other`
- Tags: `['published', 'literature', 'signaling', 'cheemalavagu', 'jak', 'stat', 'l1', 'il6r', 'gp130', 'l2', 'il10r1', 'il10r2', 'jak1', 'jak2']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/literature/Cheemalavagu_JAK_STAT.bngl`
- Local BNGL file used: `Published/CheemalavaguJAKSTAT/Cheemalavagu_JAK_STAT.bngl`
- Local YAML file used: `Published/CheemalavaguJAKSTAT/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
