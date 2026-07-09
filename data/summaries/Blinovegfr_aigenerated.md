# Model Explanation: Blinov egfr

## 1. One-sentence summary

This model represents EGF receptor activation, receptor aggregation, receptor and Shc phosphorylation, and downstream adaptor complex formation.

## 2. Biological meaning

This model represents EGF receptor activation, receptor aggregation, receptor and Shc phosphorylation, and downstream adaptor complex formation. The local model comments and metadata give this context: EGFR signaling model. The explanation below is therefore based on the local BNGL model file `Published/Blinovegfr/Blinov_egfr.bngl` and metadata file `Published/Blinovegfr/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `EGFR`: EGF receptor. It has binding/interaction sites `ecd`, `tmd` and regulated state sites `y1068~u~p`, `y1173~u~p`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `EGF`: epidermal growth factor. It has binding or interaction sites `rb`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Grb2`: Grb2. It has binding or interaction sites `sh2`, `sos`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Shc`: Shc. It has binding/interaction sites `sh3` and regulated state sites `Y773~p~u`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `1 @EC:EGF(rb) 680.0`
- `2 @M:EGFR(ecd,tmd,y1068~u,y1173~u) 602.0`
- `3 @Cyt:Shc(sh3,Y773~u) 150.0`

Important parameters include:

- `No parameters were found.`

Functions and simulation/action commands:

- `simulate_nf({t_end=>120.0,n_steps=>240})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **r00_lig_bind**: Reversible binding/release. The rule involves `EGF`, `EGFR` and produces `EGF`, `EGFR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `0.003,  0.06`.
- **r01_dimer**: Reversible binding/release. The rule involves `EGFR` and produces `EGFR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `0.001,  0.01`.
- **r04_dephosp**: State change or catalytic conversion. The rule involves `EGFR` and produces `EGFR`. The encoded molecular change is `EGFR` site `y1173` changes from `p` to `u`; site `y1173` changes from `p` to `u`. Rate parameter(s): `4.505`.
- **r03_phosp**: State change or catalytic conversion. The rule involves `EGFR` and produces `EGFR`. The encoded molecular change is `EGFR` site `y1068` changes from `u` to `p`; site `y1068` changes from `u` to `p`. Rate parameter(s): `0.01`.
- **r02_phosp**: State change or catalytic conversion. The rule involves `EGFR` and produces `EGFR`. The encoded molecular change is `EGFR` site `y1173` changes from `u` to `p`; site `y1173` changes from `u` to `p`. Rate parameter(s): `0.01`.
- **r05_deposp**: State change or catalytic conversion. The rule involves `EGFR` and produces `EGFR`. The encoded molecular change is `EGFR` site `y1068` changes from `p` to `u`; site `y1068` changes from `p` to `u`. Rate parameter(s): `4.505`.
- **r08_shcU_bind**: Reversible binding/release. The rule involves `EGFR`, `Shc` and produces `EGFR`, `Shc`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `0.045,  0.6`.
- **r09_shc_phosp**: Reversible binding/release. The rule involves `EGFR`, `Shc` and produces `EGFR`, `Shc`. The encoded molecular change is site `Y773` changes from `u` to `p`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `3.0,  0.03`.
- **r14_shc_dephosp**: State change or catalytic conversion. The rule involves `Shc` and produces `Shc`. The encoded molecular change is `Shc` site `Y773` changes from `p` to `u`; site `Y773` changes from `p` to `u`. Rate parameter(s): `0.005`.
- **r08_shcP_bind**: Reversible binding/release. The rule involves `EGFR`, `Shc` and produces `EGFR`, `Shc`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `4.5E-4,  0.3`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `EGFR_tot` (Molecules) tracks patterns containing EGFR. Pattern: `@M:EGFR()`.
- `EGF_EC` (Molecules) tracks patterns containing EGF. Pattern: `@EC:EGF()`.
- `Shc_cyt` (Molecules) tracks patterns containing Shc. Pattern: `@Cyt:Shc()`.
- `Dimers` (Molecules) tracks bound complexes. Pattern: `@M:EGFR(tmd!+)`.
- `Y1068_phosp` (Molecules) tracks bound complexes. Pattern: `@M:EGFR(y1068~p!?)`.
- `Y1173_phosp` (Molecules) tracks bound complexes. Pattern: `@M:EGFR(y1173~p!?)`.
- `Total_phosp` (Molecules) tracks bound complexes. Pattern: `@M:EGFR(y1068~p!?) @M:EGFR(y1173~p!?)`.
- `ShcP_Cyt` (Molecules) tracks bound complexes. Pattern: `@Cyt:Shc(Y773~p!?)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_egfr`
- Title/name: `Blinov egfr`
- Category: `signaling`
- Tags: `['published', 'nfsim', 'blinov', 'egfr', 'egf', 'grb2', 'shc', 'simulate_nf']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/growth-factor-signaling/Blinov_egfr.bngl`
- Local BNGL file used: `Published/Blinovegfr/Blinov_egfr.bngl`
- Local YAML file used: `Published/Blinovegfr/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `true`, methods = `['nf']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
