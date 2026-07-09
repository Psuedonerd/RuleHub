# Model Explanation: Dushek 2011

## 1. One-sentence summary

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation.

## 2. Biological meaning

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation. The local model comments and metadata give this context: Enzymatic modification of a 20-site substrate using the 2-step binding model. Reaction area. Substrate concentration. Encounter reactions (E refers to kinase and F refers to phosphatase). Diffusion-limited on-rate (k+) Local diffusion rate (k-) Local on-rates (k * on) Unbinding rate (koff) Modification rate (kr) Reactivation rate (mu) Attribute E/F indicates if a kinase or phosphatase is within the encounter complex (1 = within encounter complex). Attribute A indicates if the enzyme within the encounter complex is activate (A~0) or inactive (A~1). Attribute Y indicates the number of phosphorylated sites. ENCOUNTER COMPLEX. The explanation below is therefore based on the local BNGL model file `Published/Dushek2011/Dushek_2011.bngl` and metadata file `Published/Dushek2011/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `S`: S. It has state sites `E~0~1`, `F~0~1`, `A~0~1`, `Y~U~P~2P~3P~4P~5P~6P~7P~8P~9P~10P~11P~12P~13P~14P~15P~16P~17P~18P~19P~20P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `S(E~0,F~0,A~0,Y~U) tS`

Important parameters include:

- `A 0.0001`
- `tS 1`
- `Ekp 0.1`
- `Fkp 0.1`
- `Ekm 0.1/A`
- `Fkm 0.1/A`
- `Ekf1 20 * 10/A`
- `Ekf2 19 * 10/A`
- `Ekf3 18 * 10/A`
- `Ekf4 17 * 10/A`
- `Ekf5 16 * 10/A`
- `Ekf6 15 * 10/A`
- `Ekf7 14 * 10/A`
- `Ekf8 13 * 10/A`
- `Ekf9 12 * 10/A`
- `Ekf10 11 * 10/A`
- `Ekf11 10 * 10/A`
- `Ekf12 9 * 10/A`
- `Ekf13 8 * 10/A`
- `Ekf14 7 * 10/A`
- `Ekf15 6 * 10/A`
- `Ekf16 5 * 10/A`
- `Ekf17 4 * 10/A`
- `Ekf18 3 * 10/A`
- `Ekf19 2 * 10/A`

Functions and simulation/action commands:

- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>500000,n_steps=>30,sparse=>1,steady_state=>1});`
- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>500000,n_steps=>30,sparse=>1,steady_state=>1});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **ENCOUNTER COMPLEX**: State change or catalytic conversion. The nearby model comment says: “ENCOUNTER COMPLEX”. The rule involves `S` and produces `S`. The encoded molecular change is `S` site `E` changes from `0` to `1`; site `E` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekp, Ekm`.
- **ENCOUNTER COMPLEX**: State change or catalytic conversion. The nearby model comment says: “ENCOUNTER COMPLEX”. The rule involves `S` and produces `S`. The encoded molecular change is site `F` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkp, Fkm`.
- **ENCOUNTER COMPLEX**: State change or catalytic conversion. The nearby model comment says: “ENCOUNTER COMPLEX”. The rule involves `S` and produces `S`. The encoded molecular change is `S` site `E` changes from `1` to `0`; site `E` changes from `1` to `0`; site `A` changes from `1` to `0`. Rate parameter(s): `Ekm`.
- **ENCOUNTER COMPLEX**: State change or catalytic conversion. The nearby model comment says: “ENCOUNTER COMPLEX”. The rule involves `S` and produces `S`. The encoded molecular change is site `F` changes from `1` to `0`; site `A` changes from `1` to `0`. Rate parameter(s): `Fkm`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf1, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf2, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf3, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf4, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf5, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf6, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf7, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf8, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf9, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf10, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf11, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf12, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf13, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf14, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf15, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf16, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf17, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf18, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf19, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf20, Ekb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf1, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf2, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf3, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf4, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf5, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf6, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf7, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf8, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf9, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf10, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf11, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf12, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf13, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf14, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf15, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf16, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf17, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf18, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf19, Fkb`.
- **BINDING REACTIONS**: Reversible binding/release. The nearby model comment says: “BINDING REACTIONS”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf20, Fkb`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `U` to `P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `P` to `2P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `2P` to `3P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `3P` to `4P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `4P` to `5P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `5P` to `6P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `6P` to `7P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `7P` to `8P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `8P` to `9P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `9P` to `10P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `10P` to `11P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `11P` to `12P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `12P` to `13P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `13P` to `14P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `14P` to `15P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **CATALYSIS + ENZYME INACTIVATION.**: Unbinding or disassembly. The nearby model comment says: “CATALYSIS + ENZYME INACTIVATION.”. The rule involves `S` and produces `S`. The encoded molecular change is site `A` changes from `0` to `1`; site `Y` changes from `15P` to `16P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- Additional rules are present after these 60 entries; they are mostly continuations of the same rule families above and should be read in the BNGL file for exhaustive curation.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `S0` (Molecules) tracks bound complexes. Pattern: `S(Y~U!?)`.
- `S1` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `S(Y~P!?)`.
- `S2` (Molecules) tracks bound complexes. Pattern: `S(Y~2P!?)`.
- `S3` (Molecules) tracks bound complexes. Pattern: `S(Y~3P!?)`.
- `S4` (Molecules) tracks bound complexes. Pattern: `S(Y~4P!?)`.
- `S5` (Molecules) tracks bound complexes. Pattern: `S(Y~5P!?)`.
- `S6` (Molecules) tracks bound complexes. Pattern: `S(Y~6P!?)`.
- `S7` (Molecules) tracks bound complexes. Pattern: `S(Y~7P!?)`.
- `S8` (Molecules) tracks bound complexes. Pattern: `S(Y~8P!?)`.
- `S9` (Molecules) tracks bound complexes. Pattern: `S(Y~9P!?)`.
- `S10` (Molecules) tracks bound complexes. Pattern: `S(Y~10P!?)`.
- `S11` (Molecules) tracks bound complexes. Pattern: `S(Y~11P!?)`.
- `S12` (Molecules) tracks bound complexes. Pattern: `S(Y~12P!?)`.
- `S13` (Molecules) tracks bound complexes. Pattern: `S(Y~13P!?)`.
- `S14` (Molecules) tracks bound complexes. Pattern: `S(Y~14P!?)`.
- `S15` (Molecules) tracks bound complexes. Pattern: `S(Y~15P!?)`.
- `S16` (Molecules) tracks bound complexes. Pattern: `S(Y~16P!?)`.
- `S17` (Molecules) tracks bound complexes. Pattern: `S(Y~17P!?)`.
- `S18` (Molecules) tracks bound complexes. Pattern: `S(Y~18P!?)`.
- `S19` (Molecules) tracks bound complexes. Pattern: `S(Y~19P!?)`.
- `S20` (Molecules) tracks bound complexes. Pattern: `S(Y~20P!?)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Dushek_2011`
- Title/name: `Dushek 2011`
- Category: `signaling`
- Tags: `['published', 'dushek', '2011', 's']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Dushek_2011.bngl`
- Local BNGL file used: `Published/Dushek2011/Dushek_2011.bngl`
- Local YAML file used: `Published/Dushek2011/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
