# Model Explanation: Hlavacek 2001

## 1. One-sentence summary

This model represents bivalent hapten binding to bivalent cell-surface antibody/receptor sites and the formation or loss of crosslinked receptor chains.

## 2. Biological meaning

This model represents bivalent hapten binding to bivalent cell-surface antibody/receptor sites and the formation or loss of crosslinked receptor chains. The local model comments and metadata give this context: Kinetic proofreading model for receptor-mediated cell signaling. A symmetric bivalent ligand (two identical receptor-binding sites) interacts with monovalent cell-surface receptors, forming receptor dimers through sequential binding. Dimers undergo a series of N=5 unidirectional modifications (representing phosphorylation, kinase recruitment, adapter association, etc.). If a dimer dissociates before completing all modifications, the receptors revert to their basal unmodified state. This architecture implements kinetic proofreading: the fraction of terminally modified dimers at steady state scales as alpha^N where alpha = kp/(kp + 2*koff), providing exponential discrimination between ligands with different dissociation rate constants. Ligands forming long-lived receptor complexes generate disproportionately more fully modified dimers than ligands forming short-lived. The explanation below is therefore based on the local BNGL model file `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl` and metadata file `Published/Hlavacek2001/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L`: ligand. It has binding/interaction sites `r`, `r` and regulated state sites `mod~0~1~2~3~4~5`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R`: receptor. It has binding or interaction sites `l`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L(r,r,mod~0)  NL`
- `R(l)          NR`

Important parameters include:

- `NA  6.02214076e23`
- `V_ref  1e-9`
- `NR  300000`
- `NL  602`
- `kon1  1.661e-8`
- `kon2  3.333e-6`
- `koff  0.1`
- `kp  0.4`

Functions and simulation/action commands:

- `alpha() = kp / (kp + 2 * koff)`
- `frac_dimers() = 2 * Obs_Tot_Dimers / NR`
- `frac_term() = Obs_D5 / (Obs_Tot_Dimers + 1e-30)`
- `frac_R_term() = 2 * Obs_D5 / NR`
- `generate_network({overwrite=>1})`
- `saveConcentrations()`
- `resetConcentrations()`
- `simulate({method=>"ode",suffix=>"ode",\`
- `t_start=>0,t_end=>600,n_steps=>300})`
- `resetConcentrations()`
- `parameter_scan({method=>"ode",parameter=>"koff",\`
- `par_min=>0.001,par_max=>1.0,n_scan_pts=>30,\`
- `log_scale=>1,\`
- `t_start=>0,t_end=>1000,n_steps=>100,\`
- `suffix=>"scan_koff"})`
- `generate_network({overwrite=>1})`
- `saveConcentrations()`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **See Fig. 1(a) in Hlavacek et al. (2002).**: Binding or assembly. The nearby model comment says: “See Fig. 1(a) in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kon1`.
- **See Fig. 1(a) in Hlavacek et al. (2002).**: Binding or assembly. The nearby model comment says: “See Fig. 1(a) in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kon2`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. The encoded molecular change is `L` site `mod` changes from `1` to `0`; site `mod` changes from `1` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. The encoded molecular change is `L` site `mod` changes from `2` to `0`; site `mod` changes from `2` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. The encoded molecular change is `L` site `mod` changes from `3` to `0`; site `mod` changes from `3` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. The encoded molecular change is `L` site `mod` changes from `4` to `0`; site `mod` changes from `4` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).**: Unbinding or disassembly. The nearby model comment says: “has mod=0). See Eq. 1-7 in Hlavacek et al. (2002).”. The rule involves `L`, `R` and produces `L`, `R`. The encoded molecular change is `L` site `mod` changes from `5` to `0`; site `mod` changes from `5` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `koff`.
- **See Fig. 1(b) in Hlavacek et al. (2002).**: State change or catalytic conversion. The nearby model comment says: “See Fig. 1(b) in Hlavacek et al. (2002).”. The rule involves `L` and produces `L`. The encoded molecular change is `L` site `mod` changes from `0` to `1`; site `mod` changes from `0` to `1`. Rate parameter(s): `kp`.
- **See Fig. 1(b) in Hlavacek et al. (2002).**: State change or catalytic conversion. The nearby model comment says: “See Fig. 1(b) in Hlavacek et al. (2002).”. The rule involves `L` and produces `L`. The encoded molecular change is `L` site `mod` changes from `1` to `2`; site `mod` changes from `1` to `2`. Rate parameter(s): `kp`.
- **See Fig. 1(b) in Hlavacek et al. (2002).**: State change or catalytic conversion. The nearby model comment says: “See Fig. 1(b) in Hlavacek et al. (2002).”. The rule involves `L` and produces `L`. The encoded molecular change is `L` site `mod` changes from `2` to `3`; site `mod` changes from `2` to `3`. Rate parameter(s): `kp`.
- **See Fig. 1(b) in Hlavacek et al. (2002).**: State change or catalytic conversion. The nearby model comment says: “See Fig. 1(b) in Hlavacek et al. (2002).”. The rule involves `L` and produces `L`. The encoded molecular change is `L` site `mod` changes from `3` to `4`; site `mod` changes from `3` to `4`. Rate parameter(s): `kp`.
- **See Fig. 1(b) in Hlavacek et al. (2002).**: State change or catalytic conversion. The nearby model comment says: “See Fig. 1(b) in Hlavacek et al. (2002).”. The rule involves `L` and produces `L`. The encoded molecular change is `L` site `mod` changes from `4` to `5`; site `mod` changes from `4` to `5`. Rate parameter(s): `kp`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_Free_L` (Species) tracks patterns containing L. Pattern: `L(r,r,mod~0)`.
- `Obs_Free_R` (Species) tracks patterns containing R. Pattern: `R(l)`.
- `Obs_Singly_Bound` (Species) tracks bound complexes. Pattern: `L(r!+,r,mod~0)`.
- `Obs_Tot_Dimers` (Species) tracks bound complexes. Pattern: `L(r!+,r!+)`.
- `Obs_D0` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~0)`.
- `Obs_D1` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~1)`.
- `Obs_D2` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~2)`.
- `Obs_D3` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~3)`.
- `Obs_D4` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~4)`.
- `Obs_D5` (Species) tracks bound complexes. Pattern: `L(r!+,r!+,mod~5)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek_2001`
- Title/name: `Hlavacek 2001`
- Category: `physics`
- Tags: `['published', 'physics', 'hlavacek', '2001']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- Local YAML file used: `Published/Hlavacek2001/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
