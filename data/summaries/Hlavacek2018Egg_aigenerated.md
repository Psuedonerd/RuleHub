# Model Explanation: Hlavacek2018Egg

## 1. One-sentence summary

This model represents End of permute change log, using the encoded molecules and rules to track the named process.

## 2. Biological meaning

This model represents End of permute change log, using the encoded molecules and rules to track the named process. The local model comments and metadata give this context: a0__FREE changed to 9.99318747e+01 a1__FREE changed to 1.00606018e+00 a2__FREE changed to -7.52962956e-01 b1__FREE changed to -3.08973913e+01 b2__FREE changed to 1.26208508e+00 c0__FREE changed to 1.39738978e+02 c1__FREE changed to -3.91791542e+01 c2__FREE changed to -1.56811184e+00 d1__FREE changed to -1.21914775e+00 d2__FREE changed to 1.28080122e+00 End of permute change log. The explanation below is therefore based on the local BNGL model file `Published/Hlavacek2018Egg/egg.bngl` and metadata file `Published/Hlavacek2018Egg/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `t`: t. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `t 0`

Important parameters include:

- `a0__FREE 9.99318747e+01`
- `a1__FREE 1.00606018e+00`
- `a2__FREE -7.52962956e-01`
- `b1__FREE -3.08973913e+01`
- `b2__FREE 1.26208508e+00`
- `c0__FREE 1.39738978e+02`
- `c1__FREE -3.91791542e+01`
- `c2__FREE -1.56811184e+00`
- `d1__FREE -1.21914775e+00`
- `d2__FREE 1.28080122e+00`
- `a0 a0__FREE`
- `a1 a1__FREE`
- `a2 a2__FREE`
- `b1 b1__FREE`
- `b2 b2__FREE`
- `c0 c0__FREE`
- `c1 c1__FREE`
- `c2 c2__FREE`
- `d1 d1__FREE`
- `d2 d2__FREE`
- `pi=2*asin(1)`
- `period 180`
- `m=2*pi/period`

Functions and simulation/action commands:

- `X()=a0\`
- `+a1*cos(m*1*t)+b1*sin(m*1*t)\`
- `+a2*cos(m*2*t)+b2*sin(m*2*t)`
- `Y()=c0\`
- `+c1*cos(m*1*t)+d1*sin(m*1*t)\`
- `+c2*cos(m*2*t)+d2*sin(m*2*t)`
- `generate_network({overwrite=>1})`
- `simulate({suffix=>"egg",method=>"ode",\`
- `t_start=>0,t_end=>180,n_steps=>180,\`
- `print_functions=>1})`
- `generate_network({overwrite=>1})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **reaction rule**: Production, removal, or biochemical conversion. The rule involves the listed reactant pattern and produces the listed product pattern. Rate parameter(s): `1`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `t` (Species) tracks patterns containing t. Pattern: `t`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek2018Egg_egg`
- Title/name: `Hlavacek2018Egg`
- Category: `other`
- Tags: `['a0__free', 'a1__free', 'a2__free', 'b1__free', 'b2__free', 'c0__free', 'c1__free', 'c2__free', 'd1__free', 'd2__free', 'a0', 'a1', 'a2', 'b1', 'b2', 'c0', 'c1', 'c2', 'd1', 'd2', 'period', 't', 'species']`
- Source origin: `published`
- Original repository: `missing`
- Original format: `missing`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Hlavacek2018Egg/egg.bngl`
- Local YAML file used: `Published/Hlavacek2018Egg/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
