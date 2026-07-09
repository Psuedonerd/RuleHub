# Model Explanation: Barua 2007

## 1. One-sentence summary

This model examines how phosphorylated receptor dimers recruit and activate SHP2 through SH2-domain binding, conformational opening, intracomplex engagement, and receptor dephosphorylation.

## 2. Biological meaning

This model examines how phosphorylated receptor dimers recruit and activate SHP2 through SH2-domain binding, conformational opening, intracomplex engagement, and receptor dephosphorylation. The local model comments and metadata give this context: Base model of Shp2 regulation from Barua, Faeder, and Haugh (2006). Copyright 2006, North Carolina State University and Los Alamos National Laboratory Concentration units are in micromolar; time units are in seconds. Pre-dimerized receptors Intra-complex phosphorylation Equilibrium between the closed form and open form of S Binding of S(CSH2) from cytosol Binding of S(NSH2~O) from cytosol Binding of S(PTP~O) from cytosol Dephosphorylation of R(Y1~P) 1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor 2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor 3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor. The explanation below is therefore based on the local BNGL model file `Published/Barua2007/Barua_2007.bngl` and metadata file `Published/Barua2007/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `R`: receptor. It has binding/interaction sites `DD` and regulated state sites `Y1~U~P`, `Y2~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `S`: S. It has binding/interaction sites `CSH2` and regulated state sites `NSH2~C~O`, `PTP~C~O`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `S(NSH2~C,CSH2,PTP~C)				S_tot`
- `R(DD!1,Y1~U,Y2~P).R(DD!1,Y1~U,Y2~P)             R_dim`

Important parameters include:

- `kdim            1000`
- `kopen           10`
- `kclose          500`
- `kon_CSH2        1`
- `koff_CSH2       1`
- `kon_NSH2        1`
- `koff_NSH2       1`
- `kkin_Y1         0.1`
- `kon_PTP         1`
- `koff_PTP        10`
- `kcat_PTP        1`
- `chi_r1          1000`
- `chi_r2          100`
- `chi_r3          1000`
- `chi_r4          1000`
- `chi_r5          100`
- `chi_r6          100`
- `chi_r7          100`
- `chi_r8          1000`
- `chi_r9          100`
- `chi_r10         100`
- `chi_r11         1000`
- `R_dim		0.025`
- `S_tot		0.05`

Functions and simulation/action commands:

- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>1000,n_steps=>100,steady_state=>1,atol=>1e-10,rtol=>1e-8,sparse=>0});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Intra-complex phosphorylation**: State change or catalytic conversion. The nearby model comment says: “Intra-complex phosphorylation”. The rule involves `R` and produces `R`. The encoded molecular change is `R` site `Y1` changes from `U` to `P`; site `Y1` changes from `U` to `P`. Rate parameter(s): `kkin_Y1`.
- **Equilibrium between the closed form and open form of S**: State change or catalytic conversion. The nearby model comment says: “Equilibrium between the closed form and open form of S”. The rule involves `S` and produces `S`. The encoded molecular change is `S` site `NSH2` changes from `C` to `O`; site `NSH2` changes from `C` to `O`; site `PTP` changes from `C` to `O`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kopen, kclose`.
- **Binding of S(CSH2) from cytosol**: Reversible binding/release. The nearby model comment says: “Binding of S(CSH2) from cytosol”. The rule involves `R`, `S` and produces `R`, `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_CSH2, koff_CSH2 \`.
- **Binding of S(CSH2) from cytosol**: Production, removal, or biochemical conversion. The nearby model comment says: “Binding of S(CSH2) from cytosol”. The rule involves `exclude_reactants` and produces the listed product pattern. 
- **Binding of S(NSH2~O) from cytosol**: Reversible binding/release. The nearby model comment says: “Binding of S(NSH2~O) from cytosol”. The rule involves `R`, `S` and produces `R`, `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_NSH2, koff_NSH2 \`.
- **Binding of S(NSH2~O) from cytosol**: Production, removal, or biochemical conversion. The nearby model comment says: “Binding of S(NSH2~O) from cytosol”. The rule involves `exclude_reactants` and produces the listed product pattern. 
- **Binding of S(PTP~O) from cytosol**: Reversible binding/release. The nearby model comment says: “Binding of S(PTP~O) from cytosol”. The rule involves `R`, `S` and produces `R`, `S`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon_PTP, koff_PTP \`.
- **Binding of S(PTP~O) from cytosol**: Production, removal, or biochemical conversion. The nearby model comment says: “Binding of S(PTP~O) from cytosol”. The rule involves `exclude_reactants` and produces the listed product pattern. 
- **Dephosphorylation of R(Y1~P)**: Unbinding or disassembly. The nearby model comment says: “Dephosphorylation of R(Y1~P)”. The rule involves `R`, `S` and produces `R`, `S`. The encoded molecular change is `R` site `Y1` changes from `P` to `U`; site `Y1` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `kcat_PTP`.
- **Dephosphorylation of R(Y1~P)**: Unbinding or disassembly. The nearby model comment says: “Dephosphorylation of R(Y1~P)”. The rule involves `R`, `S` and produces `R`, `S`. The encoded molecular change is `R` site `Y1` changes from `P` to `U`; site `Y1` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `kcat_PTP`.
- **1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor**: Unbinding or disassembly. The nearby model comment says: “1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor**: Unbinding or disassembly. The nearby model comment says: “1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor**: Unbinding or disassembly. The nearby model comment says: “2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor**: Unbinding or disassembly. The nearby model comment says: “2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor**: Unbinding or disassembly. The nearby model comment says: “3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor**: Unbinding or disassembly. The nearby model comment says: “3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **5 Intra-complex binding: NSH2 bound, association of PTP with other receptor**: Unbinding or disassembly. The nearby model comment says: “5 Intra-complex binding: NSH2 bound, association of PTP with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **5 Intra-complex binding: NSH2 bound, association of PTP with other receptor**: Unbinding or disassembly. The nearby model comment says: “5 Intra-complex binding: NSH2 bound, association of PTP with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **6 Intracomplex binding: NSH2 bound, association of PTP with same receptor**: Unbinding or disassembly. The nearby model comment says: “6 Intracomplex binding: NSH2 bound, association of PTP with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **6 Intracomplex binding: NSH2 bound, association of PTP with same receptor**: Unbinding or disassembly. The nearby model comment says: “6 Intracomplex binding: NSH2 bound, association of PTP with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **7 Intra-complex binding: PTP bound, association of CSH2 with same receptor**: Unbinding or disassembly. The nearby model comment says: “7 Intra-complex binding: PTP bound, association of CSH2 with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **7 Intra-complex binding: PTP bound, association of CSH2 with same receptor**: Unbinding or disassembly. The nearby model comment says: “7 Intra-complex binding: PTP bound, association of CSH2 with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **8 Intra-complex binding: PTP bound, association of CSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “8 Intra-complex binding: PTP bound, association of CSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **8 Intra-complex binding: PTP bound, association of CSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “8 Intra-complex binding: PTP bound, association of CSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **9 Intra-complex binding: PTP bound, association of NSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “9 Intra-complex binding: PTP bound, association of NSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **9 Intra-complex binding: PTP bound, association of NSH2 with other receptor**: Unbinding or disassembly. The nearby model comment says: “9 Intra-complex binding: PTP bound, association of NSH2 with other receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **10 Intra-complex binding: PTP bound, association of NSH2 with same receptor**: Unbinding or disassembly. The nearby model comment says: “10 Intra-complex binding: PTP bound, association of NSH2 with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **10 Intra-complex binding: PTP bound, association of NSH2 with same receptor**: Unbinding or disassembly. The nearby model comment says: “10 Intra-complex binding: PTP bound, association of NSH2 with same receptor”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2**: Unbinding or disassembly. The nearby model comment says: “11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2**: Unbinding or disassembly. The nearby model comment says: “11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2**: Unbinding or disassembly. The nearby model comment says: “12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2**: Unbinding or disassembly. The nearby model comment says: “12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2**: Unbinding or disassembly. The nearby model comment says: “13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2**: Unbinding or disassembly. The nearby model comment says: “13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2**: Unbinding or disassembly. The nearby model comment says: “14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2**: Unbinding or disassembly. The nearby model comment says: “14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2**: Unbinding or disassembly. The nearby model comment says: “15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2**: Unbinding or disassembly. The nearby model comment says: “15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 
- **16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2**: Unbinding or disassembly. The nearby model comment says: “16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2**: Unbinding or disassembly. The nearby model comment says: “16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2”. The rule involves `R`, `S` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2**: Production, removal, or biochemical conversion. The nearby model comment says: “16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2”. The rule involves the listed reactant pattern and produces the listed product pattern. 

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `pYR` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `R(Y1~P!?)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2007`
- Title/name: `Barua 2007`
- Category: `signaling`
- Tags: `['published', 'barua', '2007', 'version', 'r', 's']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Barua_2007.bngl`
- Local BNGL file used: `Published/Barua2007/Barua_2007.bngl`
- Local YAML file used: `Published/Barua2007/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
