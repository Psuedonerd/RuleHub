# Model Explanation: BaruaFceRI 2012

## 1. One-sentence summary

This model represents bivalent hapten binding to bivalent cell-surface antibody/receptor sites and the formation or loss of crosslinked receptor chains.

## 2. Biological meaning

This model represents bivalent hapten binding to bivalent cell-surface antibody/receptor sites and the formation or loss of crosslinked receptor chains. The local model comments and metadata give this context: The model represents (1/N) of a cell, where N=8,000, number of rafts per cell. To make it represent the entire cell, replace N with 1, wherever it is used to scale the parameter values. State (s~o) represents raft-localized state of a protein, and state (s~d) represents nonraft state of a protein. Concentrations HapT    60000000000    #  Monovalent hapten; cell membrane area=8e-6 cm2 cell; z=(Rate of protein dephosphorylation inside rafts)/(Rate of protein dephosphorylation outside rafts) Hap(l) Hap(l)                   HapT; Ligand binding and receptor crosslinking Hapten binding FCR(a) + Hap(l) <-> FCR(a!1).Hap(l!1) kon_h, koff_h Receptor - Lyn interaction. The explanation below is therefore based on the local BNGL model file `Published/BaruaFceRI2012/BaruaFceRI_2012.bngl` and metadata file `Published/BaruaFceRI2012/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `L`: ligand. It has binding or interaction sites `l`, `l`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `FCR`: FCR. It has binding/interaction sites `a` and regulated state sites `s~d~o`, `b~Y~pY`, `g~Y~pY`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lyn`: Lyn kinase. It has binding/interaction sites `U`, `SH2` and regulated state sites `s~d~o`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Syk`: Syk kinase. It has binding/interaction sites `tSH2` and regulated state sites `a~Y~pY`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `LAT`: LAT. It has state sites `s~d~o`, `p~Y~pY`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Grb2`: Grb2. It has binding or interaction sites `SH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `L(l,l)                   LigT`
- `FCR(s~o,a,b~Y,g~Y)       RecT*r_o/(r_o + r_d)`
- `FCR(s~d,a,b~Y,g~Y)       RecT*r_d/(r_o + r_d)`
- `Lyn(s~o,U,SH2)           LynT*l_o/(l_o + l_d)`
- `Lyn(s~d,U,SH2)           LynT*l_d/(l_o + l_d)`
- `Syk(tSH2,a~Y)            SykT`
- `LAT(s~o,p~Y)             LATT*t_o/(t_o + t_d)`
- `LAT(s~d,p~Y)             LATT*t_d/(t_o + t_d)`
- `Grb2(SH2)                GrbT`

Important parameters include:

- `LigT      6.0e5`
- `RecT      400000/N`
- `LynT      28000/N`
- `SykT      400000/N`
- `LATT      1000000/N`
- `GrbT      400000/N`
- `kon       8.125e-8`
- `kx        N*5e-6`
- `koff      0.5`
- `kon_h     4.3e-8`
- `koff_h    0.019`
- `lf         N*5e-5`
- `lr1        20`
- `lr2        0.12`
- `sf         N*6e-5`
- `sr         0.20`
- `gf         N*1.25e-6`
- `gr         0.30`
- `plb1_o     30`
- `plb1_d     6`
- `plb2_o     100`
- `plb2_d     20`
- `plg1_o     1`
- `plg1_d     0.2`
- `plg2_o     3`

Functions and simulation/action commands:

- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>3600, n_steps=>3600,atoll=>1e-08,rtol=>1e-08,sparse=>1});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Ligand binding and receptor crosslinking**: Reversible binding/release. The nearby model comment says: “Ligand binding and receptor crosslinking”. The rule involves `FCR`, `L` and produces `FCR`, `L`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon,  koff`.
- **Ligand binding and receptor crosslinking**: Reversible binding/release. The nearby model comment says: “Ligand binding and receptor crosslinking”. The rule involves `FCR`, `L` and produces `FCR`, `L`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kx,  koff`.
- **Ligand binding and receptor crosslinking**: Reversible binding/release. The nearby model comment says: “Ligand binding and receptor crosslinking”. The rule involves `FCR`, `L` and produces `FCR`, `L`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kx,  koff`.
- **Receptor - Lyn interaction**: Reversible binding/release. The nearby model comment says: “Receptor - Lyn interaction”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `lf,  lr1`.
- **Receptor - Lyn interaction**: Reversible binding/release. The nearby model comment says: “Receptor - Lyn interaction”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `lf,  lr2`.
- **Receptor - Lyn interaction**: Reversible binding/release. The nearby model comment says: “Receptor - Lyn interaction”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `lf,  lr1`.
- **Receptor - Lyn interaction**: Reversible binding/release. The nearby model comment says: “Receptor - Lyn interaction”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `lf,  lr2`.
- **Receptor-Syk binding**: Reversible binding/release. The nearby model comment says: “Receptor-Syk binding”. The rule involves `FCR`, `Syk` and produces `FCR`, `Syk`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `sf,  sr`.
- **LAT-Grb2 binding**: Reversible binding/release. The nearby model comment says: “LAT-Grb2 binding”. The rule involves `Grb2`, `LAT` and produces `Grb2`, `LAT`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `gf,  gr`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `b` changes from `Y` to `pY`. Rate parameter(s): `plb1_o`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `b` changes from `Y` to `pY`. Rate parameter(s): `plb2_o`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `g` changes from `Y` to `pY`. Rate parameter(s): `plg1_o`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `g` changes from `Y` to `pY`. Rate parameter(s): `plg2_o`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `b` changes from `Y` to `pY`. Rate parameter(s): `plb1_d`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `b` changes from `Y` to `pY`. Rate parameter(s): `plb2_d`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `g` changes from `Y` to `pY`. Rate parameter(s): `plg1_d`.
- **Receptor phosphorylation by Lyn:**: State change or catalytic conversion. The nearby model comment says: “Receptor phosphorylation by Lyn:”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is site `g` changes from `Y` to `pY`. Rate parameter(s): `plg2_d`.
- **Syk autophosphorylation**: State change or catalytic conversion. The nearby model comment says: “Syk autophosphorylation”. The rule involves `Syk` and produces `Syk`. The encoded molecular change is `Syk` site `a` changes from `Y` to `pY`; site `a` changes from `Y` to `pY`. Rate parameter(s): `pss1`.
- **Syk autophosphorylation**: State change or catalytic conversion. The nearby model comment says: “Syk autophosphorylation”. The rule involves `Syk` and produces `Syk`. The encoded molecular change is `Syk` site `a` changes from `pY` to `Y`; site `a` changes from `Y` to `pY`. Rate parameter(s): `pss2`.
- **LAT phosphorylation by Syk**: State change or catalytic conversion. The nearby model comment says: “LAT phosphorylation by Syk”. The rule involves `FCR`, `LAT`, `Syk` and produces `FCR`, `LAT`, `Syk`. The encoded molecular change is site `p` changes from `Y` to `pY`. Rate parameter(s): `psl`.
- **LAT phosphorylation by Syk**: State change or catalytic conversion. The nearby model comment says: “LAT phosphorylation by Syk”. The rule involves `FCR`, `LAT`, `Syk` and produces `FCR`, `LAT`, `Syk`. The encoded molecular change is site `p` changes from `Y` to `pY`. Rate parameter(s): `psl`.
- **Receptor dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “Receptor dephosphorylation”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is site `b` changes from `pY` to `Y`. Rate parameter(s): `db`.
- **Receptor dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “Receptor dephosphorylation”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is site `g` changes from `pY` to `Y`. Rate parameter(s): `dg`.
- **Receptor dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “Receptor dephosphorylation”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is site `b` changes from `pY` to `Y`. Rate parameter(s): `z*db`.
- **Receptor dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “Receptor dephosphorylation”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is site `g` changes from `pY` to `Y`. Rate parameter(s): `z*dg`.
- **Syk dephosphorylation (at membrane)**: State change or catalytic conversion. The nearby model comment says: “Syk dephosphorylation (at membrane)”. The rule involves `FCR`, `Syk` and produces `FCR`, `Syk`. The encoded molecular change is site `a` changes from `pY` to `Y`. Rate parameter(s): `ds`.
- **Syk dephosphorylation (at membrane)**: State change or catalytic conversion. The nearby model comment says: “Syk dephosphorylation (at membrane)”. The rule involves `FCR`, `Syk` and produces `FCR`, `Syk`. The encoded molecular change is site `a` changes from `pY` to `Y`. Rate parameter(s): `z*ds`.
- **Syk dephosphorylation (at cytosol)**: State change or catalytic conversion. The nearby model comment says: “Syk dephosphorylation (at cytosol)”. The rule involves `Syk` and produces `Syk`. The encoded molecular change is `Syk` site `a` changes from `pY` to `Y`; site `a` changes from `pY` to `Y`. Rate parameter(s): `ds`.
- **LAT dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “LAT dephosphorylation”. The rule involves `LAT` and produces `LAT`. The encoded molecular change is site `p` changes from `pY` to `Y`. Rate parameter(s): `dl`.
- **LAT dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “LAT dephosphorylation”. The rule involves `LAT` and produces `LAT`. The encoded molecular change is site `p` changes from `pY` to `Y`. Rate parameter(s): `z*dl`.
- **Raft - non-raft transition**: State change or catalytic conversion. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `r_o,  r_d`.
- **Raft - non-raft transition**: State change or catalytic conversion. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR` and produces `FCR`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `r_o,  r_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L` and produces `FCR`, `L`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `r_o,  r_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L` and produces `FCR`, `L`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `r_o,  r_d`.
- **Raft - non-raft transition**: State change or catalytic conversion. The nearby model comment says: “Raft - non-raft transition”. The rule involves `Lyn` and produces `Lyn`. The encoded molecular change is `Lyn` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `l_o,  l_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `l_o,  l_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `Lyn` and produces `FCR`, `Lyn`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `l_o,  l_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces `FCR`, `L`, `Lyn`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `l_o,  l_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces `FCR`, `L`, `Lyn`. The encoded molecular change is `FCR` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `l_o,  l_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L` and produces `FCR`, `L`. The encoded molecular change is site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `rdimer_o,  rdimer_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L` and produces `FCR`, `L`. The encoded molecular change is site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `rdimer_o,  rdimer_d`.
- **Raft - non-raft transition**: Reversible binding/release. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L` and produces `FCR`, `L`. The encoded molecular change is site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `rdimer_o,  rdimer_d`.
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **Raft - non-raft transition**: Unbinding or disassembly. The nearby model comment says: “Raft - non-raft transition”. The rule involves `FCR`, `L`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Raft - non-raft transition**: State change or catalytic conversion. The nearby model comment says: “Raft - non-raft transition”. The rule involves `LAT` and produces `LAT`. The encoded molecular change is `LAT` site `s` changes from `d` to `o`; site `s` changes from `d` to `o`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `t_o,  t_d`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `pBeta` (Molecules) tracks bound complexes. Pattern: `FCR(b~pY!?)`.
- `pGamma` (Molecules) tracks bound complexes. Pattern: `FCR(g~pY!?)`.
- `pSyk` (Molecules) tracks bound complexes. Pattern: `Syk(tSH2!+,a~pY)`.
- `pLAT` (Molecules) tracks bound complexes. Pattern: `LAT(p~pY!?)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `BaruaFceRI_2012`
- Title/name: `BaruaFceRI 2012`
- Category: `immunology`
- Tags: `['published', 'immunology', 'baruafceri', '2012', 'r_o', 'rdimer_o', 'l_o', 't_o', 'l', 'fcr', 'lyn', 'syk']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/immune-signaling/BaruaFceRI_2012.bngl`
- Local BNGL file used: `Published/BaruaFceRI2012/BaruaFceRI_2012.bngl`
- Local YAML file used: `Published/BaruaFceRI2012/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
