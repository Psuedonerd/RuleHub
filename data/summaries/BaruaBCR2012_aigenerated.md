# Model Explanation: Barua 2012

## 1. One-sentence summary

This model represents early B-cell receptor signaling, including antigen input, Src-family kinases, ITAM phosphorylation, Syk recruitment, adaptor regulation, and phosphatase feedback.

## 2. Biological meaning

This model represents early B-cell receptor signaling, including antigen input, Src-family kinases, ITAM phosphorylation, Syk recruitment, adaptor regulation, and phosphatase feedback. The local model comments and metadata give this context: Parameter values of Table 1 see Table 1 and Methods section for additional information Strength of antigen signal c=0, tonic signaling; c>0, antigen-induced signaling Protein copy numbers Rate constants for association, dissociation and phosphorylation reactions these reactions are illustrated in Fig. 1 Rate constants for dephosphorylation reactions these reactions are NOT illustrated in Fig. 1 The molecule types are illustrated by nested boxes in Fig. 1 B cell antigen receptor Y188 and Y199 in the Ig-alpha ITAM are lumped together Y196 and Y207 in the Ig-beta ITAM are lumped together 0, unphosphorylated; P, singly phosphorylated; PP, doubly phosphorylated. The explanation below is therefore based on the local BNGL model file `Published/BaruaBCR2012/BaruaBCR_2012.bngl` and metadata file `Published/BaruaBCR2012/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `BCR`: BCR. It has state sites `Y188_Y199~0~P~PP`, `Y196_Y207~0~P~PP`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lyn`: Lyn kinase. It has binding/interaction sites `unique`, `SH3`, `SH2` and regulated state sites `Y397~0~P`, `Y508~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Fyn`: Fyn kinase. It has binding/interaction sites `unique`, `SH3`, `SH2` and regulated state sites `Y420~0~P`, `Y531~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Csk`: Csk. It has binding or interaction sites `SH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PAG`: PAG. It has binding/interaction sites `PRS1`, `PRS2` and regulated state sites `Y317~0~P`, `Y163_Y181~0~P`, `Y387_Y417~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Syk`: Syk kinase. It has binding/interaction sites `tSH2` and regulated state sites `Y525_Y526~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `BCR(Y188_Y199~0,Y196_Y207~0) BT`
- `Lyn(unique,SH3,SH2,Y397~0,Y508~0) LT`
- `Fyn(unique,SH3,SH2,Y420~0,Y531~0) FT`
- `PAG(PRS1,PRS2,Y317~0,Y163_Y181~0,Y387_Y417~0) PT`
- `Csk(SH2) CT`
- `Syk(tSH2,Y525_Y526~0) ST`

Important parameters include:

- `p1 3.0e5`
- `p2 10.0`
- `p3 3.0e-4`
- `p4 3.0e-7`
- `p5 30.0`
- `p6 3.0e-5`
- `p7 0.3`
- `p8 0.1`
- `p9 3.0e-6`
- `p10 0.3`
- `p11 1.0e-5`
- `p12 1.0e3`
- `p13 30.0`
- `p14 0.1`
- `p15 3.0e-7`
- `p16 3.0e-3`
- `p17 1.0e-10`
- `p18 1.0e-7`
- `p19 1.0e-7`
- `p20 3.0e-5`
- `p21 1.0e3`
- `p22 3.0e-6`
- `p23 3.0e-4`
- `p24 1.0`
- `p25 5.0`

Functions and simulation/action commands:

- `generate_network({overwrite=>'1',TextReaction=>'1'})`
- `generate_network({overwrite=>'1',TextReaction=>'1'})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **unique domain of Lyn binds unphosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “unique domain of Lyn binds unphosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **unique domain of Lyn binds unphosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “unique domain of Lyn binds unphosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **autoinhibition of Lyn, SH2 domain of Lyn binds C-terminal pY**: Reversible binding/release. The nearby model comment says: “autoinhibition of Lyn, SH2 domain of Lyn binds C-terminal pY”. The rule involves `Lyn` and produces `Lyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf3,  kr3`.
- **Lyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y188_Y199` changes from `0` to `P`. Rate parameter(s): `2*kp4a`.
- **Lyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y188_Y199` changes from `P` to `PP`. Rate parameter(s): `kp4b`.
- **Lyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y188_Y199` changes from `0` to `P`. Rate parameter(s): `2*kp4c`.
- **Lyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y188_Y199` changes from `P` to `PP`. Rate parameter(s): `kp4d`.
- **Lyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y196_Y207` changes from `0` to `P`. Rate parameter(s): `2*kp5a`.
- **Lyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y196_Y207` changes from `P` to `PP`. Rate parameter(s): `kp5b`.
- **Lyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y196_Y207` changes from `0` to `P`. Rate parameter(s): `2*kp5c`.
- **Lyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is site `Y196_Y207` changes from `P` to `PP`. Rate parameter(s): `kp5d`.
- **receptor-bound Lyn phosphorylates receptor-bound Lyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Lyn phosphorylates receptor-bound Lyn”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is `Lyn` site `Y397` changes from `0` to `P`; site `Y397` changes from `0` to `P`. Rate parameter(s): `kp6a`.
- **receptor-bound Lyn phosphorylates receptor-bound Lyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Lyn phosphorylates receptor-bound Lyn”. The rule involves `BCR`, `Lyn` and produces `BCR`, `Lyn`. The encoded molecular change is `Lyn` site `Y397` changes from `P` to `0`; site `Y397` changes from `0` to `P`. Rate parameter(s): `kp6b`.
- **free Lyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Lyn”. The rule involves `Lyn` and produces the listed product pattern. 
- **free Lyn phosphorylates free Lyn**: State change or catalytic conversion. The nearby model comment says: “free Lyn phosphorylates free Lyn”. The rule involves `Lyn` and produces the listed product pattern. The encoded molecular change is `Lyn` site `Y397` changes from `0` to `P`. 
- **free Lyn phosphorylates free Lyn**: State change or catalytic conversion. The nearby model comment says: “free Lyn phosphorylates free Lyn”. The rule involves `Lyn` and produces the listed product pattern. The encoded molecular change is `Lyn` site `Y397` changes from `P` to `0`. 
- **free Lyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Lyn”. The rule involves `Lyn` and produces the listed product pattern. 
- **receptor-bound Lyn phosphorylates receptor-bound Fyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Lyn phosphorylates receptor-bound Fyn”. The rule involves `BCR`, `Fyn`, `Lyn` and produces `BCR`, `Fyn`, `Lyn`. The encoded molecular change is site `Y420` changes from `0` to `P`. Rate parameter(s): `kp7a`.
- **receptor-bound Lyn phosphorylates receptor-bound Fyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Lyn phosphorylates receptor-bound Fyn”. The rule involves `BCR`, `Fyn`, `Lyn` and produces `BCR`, `Fyn`, `Lyn`. The encoded molecular change is site `Y420` changes from `0` to `P`. Rate parameter(s): `kp7b`.
- **free Lyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Fyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Lyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Fyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Lyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Fyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Lyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Lyn phosphorylates free Fyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **Lyn phosphorylates PAG**: State change or catalytic conversion. The nearby model comment says: “Lyn phosphorylates PAG”. The rule involves `Lyn`, `PAG` and produces `Lyn`, `PAG`. The encoded molecular change is site `Y387_Y417` changes from `0` to `P`. Rate parameter(s): `kp8a`.
- **Lyn phosphorylates PAG**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates PAG”. The rule involves `Lyn`, `PAG` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates PAG**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates PAG”. The rule involves `Lyn`, `PAG` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates PAG**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates PAG”. The rule involves `Lyn`, `PAG` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates PAG**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates PAG”. The rule involves `Lyn`, `PAG` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **unique domain of Fyn binds unphosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “unique domain of Fyn binds unphosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **unique domain of Fyn binds unphosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “unique domain of Fyn binds unphosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM**: Production, removal, or biochemical conversion. The nearby model comment says: “SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. 
- **SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM**: Unbinding or disassembly. The nearby model comment says: “SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **autoinhibition of Fyn, SH2 domain of Fyn binds C-terminal pY**: Reversible binding/release. The nearby model comment says: “autoinhibition of Fyn, SH2 domain of Fyn binds C-terminal pY”. The rule involves `Fyn` and produces `Fyn`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf11,  kr11`.
- **Fyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y196_Y207` changes from `0` to `P`. Rate parameter(s): `2*kp12a`.
- **Fyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y196_Y207` changes from `P` to `PP`. Rate parameter(s): `kp12b`.
- **Fyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y196_Y207` changes from `0` to `P`. Rate parameter(s): `2*kp12c`.
- **Fyn phosphorylates Ig-beta ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-beta ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y196_Y207` changes from `P` to `PP`. Rate parameter(s): `kp12d`.
- **Fyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y188_Y199` changes from `0` to `P`. Rate parameter(s): `2*kp13a`.
- **Fyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y188_Y199` changes from `P` to `PP`. Rate parameter(s): `kp13b`.
- **Fyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y188_Y199` changes from `0` to `P`. Rate parameter(s): `2*kp13c`.
- **Fyn phosphorylates Ig-alpha ITAM**: State change or catalytic conversion. The nearby model comment says: “Fyn phosphorylates Ig-alpha ITAM”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is site `Y188_Y199` changes from `P` to `PP`. Rate parameter(s): `kp13d`.
- **receptor-bound Fyn phosphorylates receptor-bound Fyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Fyn phosphorylates receptor-bound Fyn”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is `Fyn` site `Y420` changes from `0` to `P`; site `Y420` changes from `0` to `P`. Rate parameter(s): `kp14a`.
- **receptor-bound Fyn phosphorylates receptor-bound Fyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Fyn phosphorylates receptor-bound Fyn”. The rule involves `BCR`, `Fyn` and produces `BCR`, `Fyn`. The encoded molecular change is `Fyn` site `Y420` changes from `P` to `0`; site `Y420` changes from `0` to `P`. Rate parameter(s): `kp14b`.
- **free Fyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Fyn”. The rule involves `Fyn` and produces the listed product pattern. 
- **free Fyn phosphorylates free Fyn**: State change or catalytic conversion. The nearby model comment says: “free Fyn phosphorylates free Fyn”. The rule involves `Fyn` and produces the listed product pattern. The encoded molecular change is `Fyn` site `Y420` changes from `0` to `P`. 
- **free Fyn phosphorylates free Fyn**: State change or catalytic conversion. The nearby model comment says: “free Fyn phosphorylates free Fyn”. The rule involves `Fyn` and produces the listed product pattern. The encoded molecular change is `Fyn` site `Y420` changes from `P` to `0`. 
- **free Fyn phosphorylates free Fyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Fyn”. The rule involves `Fyn` and produces the listed product pattern. 
- **receptor-bound Fyn phosphorylates receptor-bound Lyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Fyn phosphorylates receptor-bound Lyn”. The rule involves `BCR`, `Fyn`, `Lyn` and produces `BCR`, `Fyn`, `Lyn`. The encoded molecular change is site `Y397` changes from `0` to `P`. Rate parameter(s): `kp15a`.
- **receptor-bound Fyn phosphorylates receptor-bound Lyn**: State change or catalytic conversion. The nearby model comment says: “receptor-bound Fyn phosphorylates receptor-bound Lyn”. The rule involves `BCR`, `Fyn`, `Lyn` and produces `BCR`, `Fyn`, `Lyn`. The encoded molecular change is site `Y397` changes from `0` to `P`. Rate parameter(s): `kp15b`.
- **free Fyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Lyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Fyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Lyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Fyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Lyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **free Fyn phosphorylates free Lyn**: Production, removal, or biochemical conversion. The nearby model comment says: “free Fyn phosphorylates free Lyn”. The rule involves `Fyn`, `Lyn` and produces the listed product pattern. 
- **Fyn phosphorylates PAG**: Unbinding or disassembly. The nearby model comment says: “Fyn phosphorylates PAG”. The rule involves `Fyn`, `PAG` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- Additional rules are present after these 60 entries; they are mostly continuations of the same rule families above and should be read in the BNGL file for exhaustive curation.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Activated_Syk` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Syk(Y525_Y526~P)`.
- `Ig_alpha_P` (Molecules) tracks phosphorylated/modified molecules. Pattern: `BCR(Y188_Y199~P)`.
- `Ig_alpha_PP` (Molecules) tracks phosphorylated/modified molecules. Pattern: `BCR(Y188_Y199~PP)`.
- `Ig_beta_PP` (Molecules) tracks phosphorylated/modified molecules. Pattern: `BCR(Y196_Y207~PP)`.
- `Activated_Lyn` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Lyn(Y397~P)`.
- `Autoinhibited_Lyn` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lyn(Y508~P!+)`.
- `Activated_Fyn` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Fyn(Y420~P)`.
- `Autoinhibited_Fyn` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Fyn(Y531~P!+)`.
- `PAG1_Csk` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `PAG(Y317~P!+)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `BaruaBCR_2012`
- Title/name: `Barua 2012`
- Category: `immunology`
- Tags: `['published', 'immunology', 'baruabcr', '2012', 'bcr', 'lyn', 'fyn', 'csk', 'pag', 'syk']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/immune-signaling/BaruaBCR_2012.bngl`
- Local BNGL file used: `Published/BaruaBCR2012/BaruaBCR_2012.bngl`
- Local YAML file used: `Published/BaruaBCR2012/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
