# Model Explanation: Goldstein 1980

## 1. One-sentence summary

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output.

## 2. Biological meaning

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output. The local model comments and metadata give this context: Heterogeneous bivalent hapten-receptor cross-linking (Goldstein and Wofsy, 1980) Network-free (NFsim) kinetic model of symmetric bivalent hapten binding to a HETEROGENEOUS population of bivalent cell-surface antibody (IgE). Two antibody subpopulations (R1, R2) with distinct single-site affinities K1, K2 share the same cross-linking geometry (kappa). Three processes per receptor type: (1) hapten capture from solution, (2) inter-complex cross-linking, (3) bond dissociation. No intra-complex rings. Heterogeneity breaks the symmetry of the cross-linking single A_max, and the position of the peak shifts with total antibody concentration X_T. The default parameterization (K1 = 5e6 /M, K2 = 5e8 /M, r1 = r2. The explanation below is therefore based on the local BNGL model file `Published/Goldstein1980/blbr_heterogeneity_goldstein1980.bngl` and metadata file `Published/Goldstein1980/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L`: ligand. It has binding or interaction sites `r1`, `r2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R1`: R1. It has binding or interaction sites `l1`, `l2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R2`: R2. It has binding or interaction sites `l1`, `l2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L(r1,r2)   Lfree_init`
- `R1(l1,l2)  RT_1`
- `R2(l1,l2)  RT_2`

Important parameters include:

- `NA  6.02214076e23`
- `V_cell  1e-9`
- `S_cell  4.7e-6`
- `X_T_per_cell  500`
- `r1  0.5`
- `r2  0.5`
- `f  0.1`
- `V_sim  V_cell*f`
- `RT  X_T_per_cell*f`
- `RT_1  r1*RT`
- `RT_2  r2*RT`
- `Ka_1  5e6`
- `Ka_2  5e8`
- `kappa  4e-15`
- `Kx_1  kappa*Ka_1`
- `Kx_2  kappa*Ka_2`
- `KxRT_1  Kx_1*X_T_per_cell/S_cell`
- `KxRT_2  Kx_2*X_T_per_cell/S_cell`
- `koff  10`
- `kf1  Ka_1*koff/(NA*V_sim)`
- `kf2  Ka_2*koff/(NA*V_sim)`
- `kxf1  KxRT_1/RT*koff`
- `kxf2  KxRT_2/RT*koff`
- `LT_conc_M  1e-8`
- `LT  LT_conc_M*NA*V_sim`

Functions and simulation/action commands:

- `w1() = Obs_NCL_R1 / RT_1`
- `w2() = Obs_NCL_R2 / RT_2`
- `x_poly() = 1 - (Obs_NCL_R1 + Obs_NCL_R2) / RT`
- `parameter_scan({method=>"nf",parameter=>"LT_conc_M",\`
- `par_min=>1e-12,par_max=>1e-4,n_scan_pts=>18,\`
- `log_scale=>1,t_start=>0,t_end=>10,n_steps=>1,\`
- `suffix=>"scan",gml=>2147483647,\`
- `print_functions=>1,param=>"-bscb"})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **--- Explicit capture by R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf1*(1-use_excess),  koff`.
- **--- Explicit capture by R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf1*(1-use_excess),  koff`.
- **--- Explicit capture by R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf1*(1-use_excess),  koff`.
- **--- Explicit capture by R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf1*(1-use_excess),  koff`.
- **--- Explicit capture by R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf2*(1-use_excess),  koff`.
- **--- Explicit capture by R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf2*(1-use_excess),  koff`.
- **--- Explicit capture by R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf2*(1-use_excess),  koff`.
- **--- Explicit capture by R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Explicit capture by R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf2*(1-use_excess),  koff`.
- **--- Pseudo capture by R1 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R1 ---”. The rule involves `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf1_pseudo*use_excess`.
- **--- Pseudo capture by R1 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R1 ---”. The rule involves `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf1_pseudo*use_excess`.
- **--- Pseudo capture by R1 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R1 ---”. The rule involves `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf1_pseudo*use_excess`.
- **--- Pseudo capture by R1 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R1 ---”. The rule involves `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf1_pseudo*use_excess`.
- **--- Pseudo capture by R2 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R2 ---”. The rule involves `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf2_pseudo*use_excess`.
- **--- Pseudo capture by R2 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R2 ---”. The rule involves `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf2_pseudo*use_excess`.
- **--- Pseudo capture by R2 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R2 ---”. The rule involves `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf2_pseudo*use_excess`.
- **--- Pseudo capture by R2 ---**: Binding or assembly. The nearby model comment says: “--- Pseudo capture by R2 ---”. The rule involves `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf2_pseudo*use_excess`.
- **--- Cross-link to R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf1,  koff`.
- **--- Cross-link to R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf1,  koff`.
- **--- Cross-link to R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf1,  koff`.
- **--- Cross-link to R1 (low affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R1 (low affinity) ---”. The rule involves `L`, `R1` and produces `L`, `R1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf1,  koff`.
- **--- Cross-link to R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf2,  koff`.
- **--- Cross-link to R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf2,  koff`.
- **--- Cross-link to R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf2,  koff`.
- **--- Cross-link to R2 (high affinity) ---**: Reversible binding/release. The nearby model comment says: “--- Cross-link to R2 (high affinity) ---”. The rule involves `L`, `R2` and produces `L`, `R2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kxf2,  koff`.
- **maintains constant free ligand concentration.**: Production, removal, or biochemical conversion. The nearby model comment says: “maintains constant free ligand concentration.”. The rule involves `L` and produces the listed product pattern. Rate parameter(s): `DeleteMolecules`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_Free_R1` (Molecules) tracks patterns containing R1. Pattern: `R1(l1,l2)`.
- `Obs_Free_R2` (Molecules) tracks patterns containing R2. Pattern: `R2(l1,l2)`.
- `Obs_NCL_R1` (Molecules) tracks patterns containing R1. Pattern: `R1(l1,l2) \`.
- `R1(l1!1,l2).L(r1!1,r2) \` tracks the matching BNGL pattern.
- `R1(l1!1,l2).L(r1,r2!1) \` tracks the matching BNGL pattern.
- `R1(l1,l2!1).L(r1!1,r2) \` tracks the matching BNGL pattern.
- `R1(l1,l2!1).L(r1,r2!1) \` tracks the matching BNGL pattern.
- `L(r1!1,r2).R1(l1!1,l2!2).L(r1!2,r2) \` tracks the matching BNGL pattern.
- `L(r1!1,r2).R1(l1!1,l2!2).L(r1,r2!2) \` tracks the matching BNGL pattern.
- `L(r1,r2!1).R1(l1!1,l2!2).L(r1!2,r2) \` tracks the matching BNGL pattern.
- `L(r1,r2!1).R1(l1!1,l2!2).L(r1,r2!2)` tracks the matching BNGL pattern.
- `Obs_NCL_R2` (Molecules) tracks patterns containing R2. Pattern: `R2(l1,l2) \`.
- `R2(l1!1,l2).L(r1!1,r2) \` tracks the matching BNGL pattern.
- `R2(l1!1,l2).L(r1,r2!1) \` tracks the matching BNGL pattern.
- `R2(l1,l2!1).L(r1!1,r2) \` tracks the matching BNGL pattern.
- `R2(l1,l2!1).L(r1,r2!1) \` tracks the matching BNGL pattern.
- `L(r1!1,r2).R2(l1!1,l2!2).L(r1!2,r2) \` tracks the matching BNGL pattern.
- `L(r1!1,r2).R2(l1!1,l2!2).L(r1,r2!2) \` tracks the matching BNGL pattern.
- `L(r1,r2!1).R2(l1!1,l2!2).L(r1!2,r2) \` tracks the matching BNGL pattern.
- `L(r1,r2!1).R2(l1!1,l2!2).L(r1,r2!2)` tracks the matching BNGL pattern.
- `Obs_Xlinks` (Molecules) tracks bound complexes. Pattern: `L(r1!+,r2!+)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Goldstein_1980`
- Title/name: `Goldstein 1980`
- Category: `physics`
- Tags: `['published', 'physics', 'goldstein', '1980']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Goldstein1980/blbr_heterogeneity_goldstein1980.bngl`
- Local YAML file used: `Published/Goldstein1980/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
