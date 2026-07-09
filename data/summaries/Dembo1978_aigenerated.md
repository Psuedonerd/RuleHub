# Model Explanation: Dembo 1978

## 1. One-sentence summary

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output.

## 2. Biological meaning

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output. The local model comments and metadata give this context: Symmetric bivalent hapten-receptor cross-linking (Dembo and Goldstein, 1978) Network-free (NFsim) kinetic model of symmetric bivalent hapten binding to bivalent cell-surface antibody (IgE), forming linear chains. Three processes: (1) hapten capture from solution — a free bivalent hapten binds a receptor site; (2) receptor cross-linking — a tethered hapten arm binds a free receptor site on a DIFFERENT complex (no intra-complex rings); (3) bond dissociation — any hapten-receptor bond breaks. This is the basic model without ring formation (J1 = J2 = 0 in Dembo and Goldstein notation). The equilibrium cross-linking curve (fraction of antibody in polymers, x_poly, vs log hapten concentration) is bell-shaped and. The explanation below is therefore based on the local BNGL model file `Published/Dembo1978/blbr_dembo1978.bngl` and metadata file `Published/Dembo1978/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L`: ligand. It has binding or interaction sites `r`, `r`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R`: receptor. It has binding or interaction sites `l`, `l`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L(r,r)  LT`
- `R(l,l)  RT`

Important parameters include:

- `NA  6.02214076e23`
- `V_cell  1e-9`
- `R_per_cell  3e5`
- `f  0.01`
- `V_sim  V_cell*f`
- `RT  R_per_cell*f`
- `LT_per_cell  3e6`
- `LT  LT_per_cell*f`
- `kon  1e6`
- `koff  0.01`
- `KxRT  5`
- `kf  kon/(NA*V_sim)`
- `kxf  KxRT/RT*koff`

Functions and simulation/action commands:

- `simulate({method=>"nf",suffix=>"nfr",t_start=>0,\`
- `t_end=>3000,n_steps=>300,gml=>2147483647,\`
- `param=>"-bscb"})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **R_capture**: Binding or assembly. The nearby model comment says: “from solution binds a free receptor site with rate constant k1.”. The rule involves `L`, `R` and produces `L`, `R`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kf`.
- **R_crosslink**: Binding or assembly. The nearby model comment says: “inter-complex binding (no intra-complex rings).”. The rule involves `L`, `R` and produces `L`, `R`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kxf`.
- **R_dissoc**: Unbinding or disassembly. The nearby model comment says: “and receptor dissociates with rate constant k_off.”. The rule involves `L`, `R` and produces `L`, `R`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_Free_L` (Species) tracks patterns containing L. Pattern: `L(r,r)`.
- `Obs_Free_R` (Species) tracks patterns containing R. Pattern: `R(l,l)`.
- `Obs_Bonds` (Molecules) tracks bound complexes. Pattern: `L(r!1).R(l!1)`.
- `Obs_Free_L_sites` (Molecules) tracks patterns containing L. Pattern: `L(r)`.
- `Obs_Free_R_sites` (Molecules) tracks patterns containing R. Pattern: `R(l)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Dembo_1978`
- Title/name: `Dembo 1978`
- Category: `physics`
- Tags: `['published', 'physics', 'dembo', '1978']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Dembo1978/blbr_dembo1978.bngl`
- Local YAML file used: `Published/Dembo1978/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
