# Model Explanation: Blinov ran

## 1. One-sentence summary

This model represents Ran GTPase cycle, using the encoded molecules and rules to track the named process.

## 2. Biological meaning

This model represents Ran GTPase cycle, using the encoded molecules and rules to track the named process. The local model comments and metadata give this context: Ran GTPase cycle. The explanation below is therefore based on the local BNGL model file `Published/Blinovran/Blinov_ran.bngl` and metadata file `Published/Blinovran/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Ran`: Ran. It has binding or interaction sites `cargo`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `C`: C. It has binding/interaction sites `site` and regulated state sites `Y1~u~p`, `Y2~u~p`, `Y3~u~p`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `RCC1`: RCC1. It has binding or interaction sites `site`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `1 @nuc:Ran(cargo!1).C(site!1,Y1~u,Y2~u,Y3~u) 1000.0`
- `2 @nuc:RCC1(site) 1000.0`

Important parameters include:

- `No parameters were found.`

Functions and simulation/action commands:

- `simulate_nf({t_end=>10.0,n_steps=>200})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Transport**: Reversible binding/release. The rule involves `Ran` and produces `Ran`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `602.0,  0.0`.
- **Ran_C_bind_cyt**: Unbinding or disassembly. The rule involves `C`, `Ran` and produces `C`, `Ran`. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `1.0,  100.0`.
- **C_p1**: Reversible binding/release. The rule involves `C` and produces `C`. The encoded molecular change is `C` site `Y3` changes from `u` to `p`; site `Y3` changes from `u` to `p`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `10.0,  1.0`.
- **C_p2**: Reversible binding/release. The rule involves `C` and produces `C`. The encoded molecular change is `C` site `Y2` changes from `u` to `p`; site `Y2` changes from `u` to `p`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `10.0,  1.0`.
- **C_p3**: Reversible binding/release. The rule involves `C` and produces `C`. The encoded molecular change is `C` site `Y1` changes from `u` to `p`; site `Y1` changes from `u` to `p`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `10.0,  1.0`.
- **Ran_RCC1_bind**: Reversible binding/release. The rule involves `RCC1`, `Ran` and produces `RCC1`, `Ran`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `1.0,  100.0`.
- **Ran_C_bind_nuc**: Unbinding or disassembly. The rule involves `C`, `Ran` and produces `C`, `Ran`. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `1.0,  100.0`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Ran_cyt` (Molecules) tracks patterns containing Ran. Pattern: `@cyt:Ran()`.
- `Cargo_cyt` (Molecules) tracks patterns containing C. Pattern: `@cyt:C()`.
- `RCC1_nuc` (Molecules) tracks patterns containing RCC1. Pattern: `@nuc:RCC1()`.
- `Cargo_phosp_cyt_total` (Molecules) tracks bound complexes. Pattern: `@nuc:C(Y1~p!?) @nuc:C(Y2~p!?) @nuc:C(Y3~p!?)`.
- `Cargo_nuc` (Molecules) tracks patterns containing C. Pattern: `@nuc:C()`.
- `Cargo_phosp_cyt` (Molecules) tracks bound complexes. Pattern: `@cyt:C(Y1~p!?,Y2~p!?,Y3~p!?)`.
- `Ran_bound_cyt` (Molecules) tracks bound complexes. Pattern: `@cyt:Ran(cargo!+)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_ran`
- Title/name: `Blinov ran`
- Category: `regulation`
- Tags: `['published', 'nfsim', 'blinov', 'ran', 'c', 'rcc1', 'simulate_nf']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/cell-regulation/Blinov_ran.bngl`
- Local BNGL file used: `Published/Blinovran/Blinov_ran.bngl`
- Local YAML file used: `Published/Blinovran/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `true`, methods = `['nf']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
