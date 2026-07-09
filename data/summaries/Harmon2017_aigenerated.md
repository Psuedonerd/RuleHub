# Model Explanation: Harmon 2017

## 1. One-sentence summary

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output.

## 2. Biological meaning

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output. The local model comments and metadata give this context: IgE receptor signaling with history-dependent responses (Harmon et al., 2017) ODE model of FcεRI signaling in mast cells under pulsed antigen stimulation, from Harmon et al. (2017) Supplementary Data S1. Multivalent antigen (DF3) binds IgE-FcεRI, triggering receptor phosphorylation, Syk recruitment (positive signal), Ship1 recruitment with cofactor X (negative signal), PIP3 dynamics, and degranulation. Timescale separation between fast Syk activation/deactivation and slow Ship1/X dynamics produces history-dependent responses: short quiescence intervals yield desensitization; long intervals yield priming (hyperdegranulation). Parameters were fit to on-device degranulation data (Fig. 4) using BioNetFit.. The explanation below is therefore based on the local BNGL model file `Published/Harmon2017/antigen_pulses_harmon2017.bngl` and metadata file `Published/Harmon2017/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Ag`: Ag. It has binding or interaction sites `DNP`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `R`: receptor. It has binding/interaction sites `IgE` and regulated state sites `Yb~0~P`, `Yg~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Syk`: Syk kinase. It has binding or interaction sites `tSH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Ship1`: Ship1. It has binding or interaction sites `SH2`, `x`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `X`: X. It has state sites `s~on~off`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PIP3`: PIP3. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `H`: H. It has state sites `loc~in~out`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `$Ag(DNP)            Ag_tot_1`
- `R(IgE,Yb~0,Yg~0)   R_tot`
- `Syk(tSH2)           Syk_tot`
- `Ship1(SH2,x)        Ship1_tot`
- `X(s~off)            X_tot`
- `PIP3()              0`
- `H(loc~in)           H_tot`

Important parameters include:

- `X_tot__FREE__     6.13331088e+00`
- `k_Xoff__FREE__    1.91394890e-06`
- `k_Xon__FREE__     9.39816993e+04`
- `kase__FREE__      3.76143208e+00`
- `kdegX__FREE__     3.19130252e-04`
- `kdegran__FREE__   1.88893284e+05`
- `km_Ship1__FREE__  1.43154204e-03`
- `km_Syk__FREE__    2.87783197e-01`
- `km_x__FREE__      1.12185442e-01`
- `koff__FREE__      4.45671503e-03`
- `kp_Ship1__FREE__  1.10810534e+04`
- `kp_Syk__FREE__    2.65462642e+05`
- `kp_x__FREE__      7.81553987e+05`
- `kpten__FREE__     9.95093271e-03`
- `ksynth1__FREE__   1.84930114e-02`
- `pase__FREE__      1.60206452e-01`
- `f  1`
- `NA  6.02214076e23`
- `T  60`
- `Vchannel  500e-9`
- `Nchannel  1000`
- `Vecf  f*(Vchannel/Nchannel)`
- `Vcyt  f*3e-12`
- `Ag_tot_0  0`
- `Ag_conc1  10e-9`

Functions and simulation/action commands:

- `generate_network({overwrite=>1})`
- `setConcentration("Ag(DNP)","Ag_tot_1")`
- `simulate({suffix=>"p1_5",method=>"ode",\`
- `t_end=>5,n_steps=>50})`
- `saveConcentrations()`
- `setConcentration("Ag(DNP)","Ag_tot_0")`
- `simulate({suffix=>"p2_5",method=>"ode",\`
- `t_end=>5,n_steps=>50})`
- `setConcentration("Ag(DNP)","Ag_tot_1")`
- `setConcentration("H(loc~out)",0)`
- `simulate({suffix=>"p3_5",method=>"ode",\`
- `t_end=>5,n_steps=>50})`
- `resetConcentrations()`
- `setConcentration("Ag(DNP)","Ag_tot_0")`
- `simulate({suffix=>"p2_30",method=>"ode",\`
- `t_end=>30,n_steps=>300})`
- `setConcentration("Ag(DNP)","Ag_tot_1")`
- `setConcentration("H(loc~out)",0)`
- `simulate({suffix=>"p3_30",method=>"ode",\`
- `t_end=>5,n_steps=>50})`
- `resetConcentrations()`
- `setConcentration("Ag(DNP)","Ag_tot_0")`
- `simulate({suffix=>"p2_60",method=>"ode",\`
- `t_end=>60,n_steps=>600})`
- `setConcentration("Ag(DNP)","Ag_tot_1")`
- `setConcentration("H(loc~out)",0)`
- `simulate({suffix=>"p3_60",method=>"ode",\`
- `t_end=>5,n_steps=>50})`
- `resetConcentrations()`
- `setConcentration("Ag(DNP)","Ag_tot_0")`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Antigen-receptor binding (one-step effective mechanism)**: Reversible binding/release. The nearby model comment says: “Antigen-receptor binding (one-step effective mechanism)”. The rule involves `Ag`, `R` and produces `Ag`, `R`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon,  koff`.
- **Receptor phosphorylation (Lyn-mediated, requires Ag)**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation (Lyn-mediated, requires Ag)”. The rule involves `R` and produces `R`. The encoded molecular change is `R` site `Yb` changes from `0` to `P`; site `Yb` changes from `0` to `P`; site `Yg` changes from `0` to `P`. Rate parameter(s): `kase`.
- **Receptor dephosphorylation (pseudo-first-order)**: State change or catalytic conversion. The nearby model comment says: “Receptor dephosphorylation (pseudo-first-order)”. The rule involves `R` and produces `R`. The encoded molecular change is `R` site `Yb` changes from `P` to `0`; site `Yb` changes from `P` to `0`; site `Yg` changes from `P` to `0`. Rate parameter(s): `pase`.
- **Syk recruitment to γ-chain phospho-ITAM**: Reversible binding/release. The nearby model comment says: “Syk recruitment to γ-chain phospho-ITAM”. The rule involves `R`, `Syk` and produces `R`, `Syk`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `\`.
- **Syk recruitment to γ-chain phospho-ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “Syk recruitment to γ-chain phospho-ITAM”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **Ship1 recruitment to β-chain phospho-ITAM**: Reversible binding/release. The nearby model comment says: “Ship1 recruitment to β-chain phospho-ITAM”. The rule involves `R`, `Ship1` and produces `R`, `Ship1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `\`.
- **Ship1 recruitment to β-chain phospho-ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “Ship1 recruitment to β-chain phospho-ITAM”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **Receptor-mediated activation of cofactor X**: State change or catalytic conversion. The nearby model comment says: “Receptor-mediated activation of cofactor X”. The rule involves `R`, `X` and produces `R`, `X`. The encoded molecular change is site `s` changes from `off` to `on`. Rate parameter(s): `k_Xon`.
- **Deactivation of cofactor X**: State change or catalytic conversion. The nearby model comment says: “Deactivation of cofactor X”. The rule involves `X` and produces `X`. The encoded molecular change is `X` site `s` changes from `on` to `off`; site `s` changes from `on` to `off`. Rate parameter(s): `k_Xoff`.
- **PIP3 synthesis by receptor-recruited Syk**: Production, removal, or biochemical conversion. The nearby model comment says: “PIP3 synthesis by receptor-recruited Syk”. The rule involves `Syk` and produces `PIP3`, `Syk`. Rate parameter(s): `ksynth1`.
- **Activated X binds Ship1**: Reversible binding/release. The nearby model comment says: “Activated X binds Ship1”. The rule involves `Ship1`, `X` and produces `Ship1`, `X`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kp_x,  km_x`.
- **PIP3 clearance by membrane-associated Ship1-X complex**: Production, removal, or biochemical conversion. The nearby model comment says: “PIP3 clearance by membrane-associated Ship1-X complex”. The rule involves `PIP3`, `Ship1` and produces `Ship1`. Rate parameter(s): `kdeg1`.
- **Basal PIP3 degradation (PTEN)**: Production, removal, or biochemical conversion. The nearby model comment says: “Basal PIP3 degradation (PTEN)”. The rule involves `PIP3` and produces the listed product pattern. Rate parameter(s): `kpten`.
- **Proteasomal degradation of activated X (free)**: Production, removal, or biochemical conversion. The nearby model comment says: “Proteasomal degradation of activated X (free)”. The rule involves `X` and produces the listed product pattern. Rate parameter(s): `kdegX`.
- **Proteasomal degradation of activated X (Ship1-bound)**: Unbinding or disassembly. The nearby model comment says: “Proteasomal degradation of activated X (Ship1-bound)”. The rule involves `Ship1`, `X` and produces `Ship1`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `kdegX`.
- **PIP3-driven degranulation**: State change or catalytic conversion. The nearby model comment says: “PIP3-driven degranulation”. The rule involves `H`, `PIP3` and produces `H`, `PIP3`. The encoded molecular change is `H` site `loc` changes from `in` to `out`; site `loc` changes from `in` to `out`. Rate parameter(s): `kdegran`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Ag_total` (Molecules) tracks patterns containing Ag. Pattern: `Ag()`.
- `Ag_free` (Molecules) tracks patterns containing Ag. Pattern: `Ag(DNP)`.
- `R_bound` (Molecules) tracks bound complexes. Pattern: `R(IgE!+)`.
- `R_free` (Molecules) tracks patterns containing R. Pattern: `R(IgE)`.
- `RP` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `R(Yg~P!?)`.
- `R0` (Molecules) tracks patterns containing R. Pattern: `R(Yg~0)`.
- `actSyk` (Molecules) tracks bound complexes. Pattern: `Syk(tSH2!+)`.
- `actShip1` (Molecules) tracks bound complexes. Pattern: `Ship1(SH2!+,x!+)`.
- `Ship1_total` (Molecules) tracks patterns containing Ship1. Pattern: `Ship1()`.
- `PIP3_total` (Molecules) tracks patterns containing PIP3. Pattern: `PIP3()`.
- `Xall` (Molecules) tracks patterns containing X. Pattern: `X()`.
- `X_on_free` (Molecules) tracks patterns containing X. Pattern: `X(s~on)`.
- `X_on_free_or_bound` (Molecules) tracks bound complexes. Pattern: `X(s~on!?)`.
- `XShip1` (Molecules) tracks bound complexes. Pattern: `X(s~on!1).Ship1(x!1)`.
- `degranulation` (Molecules) tracks patterns containing H. Pattern: `H(loc~out)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Harmon_2017`
- Title/name: `Harmon 2017`
- Category: `immunology`
- Tags: `['published', 'immunology', 'harmon', '2017']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Harmon2017/antigen_pulses_harmon2017.bngl`
- Local YAML file used: `Published/Harmon2017/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
