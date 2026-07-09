# Model Explanation: Barua 2009

## 1. One-sentence summary

This compact model shows how SH2B dimerization can scaffold JAK2 molecules so that JAK2 becomes phosphorylated more efficiently inside a multimeric complex.

## 2. Biological meaning

This compact model shows how SH2B dimerization can scaffold JAK2 molecules so that JAK2 becomes phosphorylated more efficiently inside a multimeric complex. The local model comments and metadata give this context: JAK2-SH2B interaction SH2B dimerization JAK2 phosphorylation. The explanation below is therefore based on the local BNGL model file `Published/Barua2009/Barua_2009.bngl` and metadata file `Published/Barua2009/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `S`: S. It has binding or interaction sites `SH2`, `DD`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `J`: J. It has state sites `Y1~P`, `Y~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `S(SH2,DD)       Stot`
- `J(Y1~P,Y~U)     Jtot`

Important parameters include:

- `kon_dimer	1.0`
- `koff_dimer	0.1`
- `kon_SH2		1.0`
- `koff_SH2	0.1`
- `kphos_slow	0.1`
- `kphos_fast	1.0`
- `Jtot            0.000014`
- `Stot            0.1`

Functions and simulation/action commands:

- `generate_network({overwrite=>1, max_stoich=>{J=>2}});`
- `simulate_ode({t_end=>10000, n_steps=>10000,atoll=>1e-08,rtol=>1e-08,sparse=>1});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **JAK2-SH2B interaction**: Reversible binding/release. The nearby model comment says: “JAK2-SH2B interaction”. The rule involves `J`, `S` and produces `J`, `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_SH2,  koff_SH2`.
- **SH2B dimerization**: Reversible binding/release. The nearby model comment says: “SH2B dimerization”. The rule involves `S` and produces `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_dimer,  koff_dimer`.
- **JAK2 phosphorylation**: State change or catalytic conversion. The nearby model comment says: “JAK2 phosphorylation”. The rule involves `J`, `S` and produces `J`, `S`. The encoded molecular change is `J` site `Y` changes from `P` to `U`; site `Y` changes from `U` to `P`. Rate parameter(s): `kphos_slow`.
- **JAK2 phosphorylation**: State change or catalytic conversion. The nearby model comment says: “JAK2 phosphorylation”. The rule involves `J`, `S` and produces `J`, `S`. The encoded molecular change is `J` site `Y` changes from `U` to `P`; site `Y` changes from `U` to `P`. Rate parameter(s): `kphos_fast`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `J_mono` (Molecules) tracks phosphorylated/modified molecules. Pattern: `J(Y1~P)`.
- `JS` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `J(Y1~P!1).S(SH2!1,DD)`.
- `JSS` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `J(Y1~P!1).S(SH2!1,DD!2).S(SH2,DD!2)`.
- `JSSJ` (Molecules) tracks patterns containing J.J. Pattern: `J.J`.
- `J_active` (Molecules) tracks phosphorylated/modified molecules. Pattern: `J(Y~P)`.
- `J_inactive` (Molecules) tracks patterns containing J. Pattern: `J(Y~U)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2009`
- Title/name: `Barua 2009`
- Category: `signaling`
- Tags: `['published', 'barua', '2009', 's', 'j']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Barua_2009.bngl`
- Local BNGL file used: `Published/Barua2009/Barua_2009.bngl`
- Local YAML file used: `Published/Barua2009/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
