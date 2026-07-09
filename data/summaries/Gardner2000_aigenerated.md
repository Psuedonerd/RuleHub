# Model Explanation: Gardner 2000

## 1. One-sentence summary

This model represents a bistable genetic toggle switch in which two gene products mutually repress each other and degrade over time.

## 2. Biological meaning

This model represents a bistable genetic toggle switch in which two gene products mutually repress each other and degrade over time. The local model comments and metadata give this context: De-dimensionalized model of two mutually repressive gene products with Hill-type repression and first-order degradation, forming a bistable genetic toggle switch. ODE only — dimensionless variables are incompatible with stochastic simulation. Equations (Eq. 1 in Gardner et al., 2000): du/dt = alpha_1 / (1 + v^beta) - u dv/dt = alpha_2 / (1 + u^gamma) - v where u, v are concentrations normalized by the repression threshold (dissociation constant K_d), and time is in units of protein lifetime (1/k_deg). All parameters and variables are therefore dimensionless. Steady-state analysis: at steady state, du/dt = dv/dt = 0, giving: u* = alpha_1 / (1 + v*^beta)     (u-nullcline) v* = alpha_2 / (1 + u*^gamma)    (v-nullcline) These nullclines intersect at three points for the default. The explanation below is therefore based on the local BNGL model file `Published/Gardner2000/genetic_switch_gardner2000.bngl` and metadata file `Published/Gardner2000/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `R1`: R1. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R2`: R2. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `R1()  0`
- `R2()  0`

Important parameters include:

- `alpha_1  156.25`
- `alpha_2  15.6`
- `beta     2.5`
- `gamma    1.0`
- `k_deg    1.0`

Functions and simulation/action commands:

- `syn_R1() = alpha_1 / (1 + Obs_Tot_R2^beta)`
- `syn_R2() = alpha_2 / (1 + Obs_Tot_R1^gamma)`
- `generate_network({overwrite=>1})`
- `simulate({method=>"ode",suffix=>"ode",t_start=>0,t_end=>8,n_steps=>400})`
- `setParameter("alpha_2",600.0)`
- `simulate({method=>"ode",suffix=>"ode",t_start=>8,t_end=>12,n_steps=>200,continue=>1})`
- `setParameter("alpha_2",15.6)`
- `simulate({method=>"ode",suffix=>"ode",t_start=>12,t_end=>20,n_steps=>400,continue=>1})`
- `parameter_scan({method=>"ode",parameter=>"alpha_2",\`
- `par_min=>1,par_max=>500,n_scan_pts=>100,\`
- `t_start=>0,t_end=>20,n_steps=>200,suffix=>"scan"})`
- `generate_network({overwrite=>1})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Synthesis with Hill-type mutual repression**: Production, removal, or biochemical conversion. The nearby model comment says: “Synthesis with Hill-type mutual repression”. The rule involves the listed reactant pattern and produces `R1`. Rate parameter(s): `syn_R1()`.
- **Synthesis with Hill-type mutual repression**: Production, removal, or biochemical conversion. The nearby model comment says: “Synthesis with Hill-type mutual repression”. The rule involves the listed reactant pattern and produces `R2`. Rate parameter(s): `syn_R2()`.
- **First-order degradation (k_deg = 1 by nondimensionalization)**: Production, removal, or biochemical conversion. The nearby model comment says: “First-order degradation (k_deg = 1 by nondimensionalization)”. The rule involves `R1` and produces the listed product pattern. Rate parameter(s): `k_deg`.
- **First-order degradation (k_deg = 1 by nondimensionalization)**: Production, removal, or biochemical conversion. The nearby model comment says: “First-order degradation (k_deg = 1 by nondimensionalization)”. The rule involves `R2` and produces the listed product pattern. Rate parameter(s): `k_deg`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_Tot_R1` (Molecules) tracks patterns containing R1. Pattern: `R1()`.
- `Obs_Tot_R2` (Molecules) tracks patterns containing R2. Pattern: `R2()`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Gardner_2000`
- Title/name: `Gardner 2000`
- Category: `synthetic-biology`
- Tags: `['published', 'synthetic-biology', 'gardner', '2000']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Gardner2000/genetic_switch_gardner2000.bngl`
- Local YAML file used: `Published/Gardner2000/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
