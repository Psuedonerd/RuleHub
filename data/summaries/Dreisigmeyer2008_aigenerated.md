# Model Explanation: Dreisigmeyer 2008

## 1. One-sentence summary

This model represents lactose induction of the E. coli lac operon through lactose transport, allolactose production, beta-galactosidase expression, metabolism, and dilution.

## 2. Biological meaning

This model represents lactose induction of the E. coli lac operon through lactose transport, allolactose production, beta-galactosidase expression, metabolism, and dilution. The local model comments and metadata give this context: Model of the E. coli lac operon induced by extracellular lactose, based on Eq. (1) in Dreisigmeyer et al. (2008). Three ODE state variables — internal lactose (L), allolactose (A), and beta-galactosidase (Z) — track intracellular concentrations in uM. active-transport asymmetry (phi < 1) and asymmetric Michaelis constants (rho < 1); (2) beta-gal-catalyzed degradation of lactose and allolactose with competitive substrate inhibition; (3) allolactose production as a branching fraction (nu) of lactose metabolism; (4) Hill-function-regulated beta-gal expression with cooperativity n = 2; and (5) first-order growth dilution of all intracellular species. Passive transport (alpha_0) is set to zero. With nominal parameters (Table 1) at l_ext = 1000 uM, the system relaxes to a partially induced steady state (Z ~ 0.34. The explanation below is therefore based on the local BNGL model file `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl` and metadata file `Published/Dreisigmeyer2008/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L`: ligand. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `A`: A. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Z`: Z. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L()  0`
- `A()  0`
- `Z()  c_basal`

Important parameters include:

- `NA  6.02214076e23`
- `V_ref  1e-15`
- `f  1.0`
- `l_ext  1000.0`
- `growth_rate  0.0231`
- `alpha  600.0`
- `phi  0.5`
- `rho  0.1`
- `K_i  500.0`
- `beta  2.85e4`
- `nu  0.468`
- `K_m_l  2530.0`
- `delta  2.30e4`
- `K_m_a  1200.0`
- `eps  34.285`
- `c_basal  0.0343`
- `K_z  105.0`
- `n_Hill  2.0`

Functions and simulation/action commands:

- `transport_L() = alpha * Obs_Tot_Z \`
- `* (l_ext - phi * rho * Obs_Tot_L) \`
- `/ (K_i + l_ext + rho * Obs_Tot_L)`
- `metab_L() = (beta / K_m_l) * Obs_Tot_Z \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `prod_A() = nu * (beta / K_m_l) * Obs_Tot_Z * Obs_Tot_L \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `metab_A() = (delta / K_m_a) * Obs_Tot_Z \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `syn_Z() = growth_rate * (c_basal \`
- `+ eps * Obs_Tot_A^n_Hill \`
- `/ (K_z^n_Hill + Obs_Tot_A^n_Hill))`
- `generate_network({overwrite=>1})`
- `saveConcentrations()`
- `resetConcentrations()`
- `simulate({method=>"ode",suffix=>"ode",\`
- `t_start=>0,t_end=>500,n_steps=>500})`
- `parameter_scan({method=>"ode",parameter=>"l_ext",\`
- `par_min=>0.01,par_max=>1e6,n_scan_pts=>100,\`
- `log_scale=>1,t_start=>0,t_end=>500,n_steps=>200,\`
- `suffix=>"scan"})`
- `generate_network({overwrite=>1})`
- `saveConcentrations()`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Permease-dependent lactose import**: Production, removal, or biochemical conversion. The nearby model comment says: “Permease-dependent lactose import”. The rule involves the listed reactant pattern and produces `L`. Rate parameter(s): `transport_L()`.
- **Beta-gal-catalyzed lactose degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “Beta-gal-catalyzed lactose degradation”. The rule involves `L` and produces the listed product pattern. Rate parameter(s): `metab_L()`.
- **Growth dilution of internal lactose**: Production, removal, or biochemical conversion. The nearby model comment says: “Growth dilution of internal lactose”. The rule involves `L` and produces the listed product pattern. Rate parameter(s): `growth_rate`.
- **Allolactose production from lactose metabolism**: Production, removal, or biochemical conversion. The nearby model comment says: “Allolactose production from lactose metabolism”. The rule involves the listed reactant pattern and produces `A`. Rate parameter(s): `prod_A()`.
- **Beta-gal-catalyzed allolactose degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “Beta-gal-catalyzed allolactose degradation”. The rule involves `A` and produces the listed product pattern. Rate parameter(s): `metab_A()`.
- **Growth dilution of allolactose**: Production, removal, or biochemical conversion. The nearby model comment says: “Growth dilution of allolactose”. The rule involves `A` and produces the listed product pattern. Rate parameter(s): `growth_rate`.
- **Beta-gal synthesis (basal + allolactose-induced Hill function)**: Production, removal, or biochemical conversion. The nearby model comment says: “Beta-gal synthesis (basal + allolactose-induced Hill function)”. The rule involves the listed reactant pattern and produces `Z`. Rate parameter(s): `syn_Z()`.
- **Growth dilution of beta-galactosidase**: Production, removal, or biochemical conversion. The nearby model comment says: “Growth dilution of beta-galactosidase”. The rule involves `Z` and produces the listed product pattern. Rate parameter(s): `growth_rate`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_Tot_L` (Molecules) tracks patterns containing L. Pattern: `L()`.
- `Obs_Tot_A` (Molecules) tracks patterns containing A. Pattern: `A()`.
- `Obs_Tot_Z` (Molecules) tracks patterns containing Z. Pattern: `Z()`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Dreisigmeyer_2008`
- Title/name: `Dreisigmeyer 2008`
- Category: `gene-expression`
- Tags: `['published', 'gene-expression', 'dreisigmeyer', '2008']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- Local YAML file used: `Published/Dreisigmeyer2008/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
