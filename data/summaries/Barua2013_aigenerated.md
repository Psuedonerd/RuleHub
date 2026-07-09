# Model Explanation: Barua 2013

## 1. One-sentence summary

This model represents beta-catenin destruction-complex control, including Axin/APC/GSK3/CK1 binding, beta-catenin phosphorylation, dephosphorylation, synthesis, and degradation.

## 2. Biological meaning

This model represents beta-catenin destruction-complex control, including Axin/APC/GSK3/CK1 binding, beta-catenin phosphorylation, dephosphorylation, synthesis, and degradation. The local model comments and metadata give this context: Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1) Binding of beta-catenin ARM repeats 3-4 to phosphorylated APC 20-aa repeats (Arrow 2) Binding of beta-Catenin ARM repeats 3 and 4 with Axin (Arrow 3) Binding of APC SAMP repeats to Axin RGS domain (Arrow 4) Binding of GSK-3beta to AXIN GID domain (Arrow 5) Binding of CK1alpha to Axin (Arrow 6) Phosphorylation of S45 of beta-catenin by CK1alpha (Arrow 7) Phosphorylation of S33/S37 of beta-catenin by GSK-3beta (Arrow 8) Phosphorylation of APC 20-aa repeat by CK1epsilon (implicit) and GSK-3beta (Arrows 9 and 10) Dephsophorylation of beta-catenin Dephoshporylation of APC b-catenin synthesis Degradation of beta-catenin not phosphorylated at S33/S37 Degradation of beta-catenin phosphorylated at S33/S37. The explanation below is therefore based on the local BNGL model file `Published/Barua2013/Barua_2013.bngl` and metadata file `Published/Barua2013/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `AXIN`: AXIN. It has binding or interaction sites `rgs`, `gid`, `b`, `e`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `GSK3b`: GSK3b. It has binding or interaction sites `a`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `APC`: APC. It has binding/interaction sites `a15`, `s` and regulated state sites `a20~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `bCat`: bCat. It has binding/interaction sites `ARM34`, `ARM59` and regulated state sites `s33s37~U~P`, `s45~U~P`, `ss~l~d`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `CK1a`: CK1a. It has binding or interaction sites `e`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `dead`: dead. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `I`: I. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `bCat(s33s37~U,s45~U,,ARM34,ARM59,ss~l)  BCATtot`
- `APC(a15,a20~U,s)  APCtot`
- `AXIN(rgs,gid,b,e)  AXINtot`
- `GSK3b(a) GSKtot`
- `CK1a(e)   CK1atot`
- `I    1`
- `dead 0`

Important parameters include:

- `BCATtot   11000`
- `APCtot    31540`
- `AXINtot   3154`
- `GSKtot    31540`
- `CK1atot   31540`
- `kf1_bap   3.17e-6`
- `kr1_bap   0.273`
- `kf2_bap   3.17e-6`
- `kr2_bap   0.0015`
- `kf_ba     3.17e-6`
- `kr_ba     0.227`
- `kf_apa    3.17e-6`
- `kr_apa    0.1`
- `kf_ga     3.17e-6`
- `kr_ga     0.065`
- `kf_ca     3.17e-6`
- `kr_ca     0.1`
- `kpb       0.05`
- `kmpb      0.0012`
- `kp        0.05`
- `kmp       0.05`
- `kdb1      0.0000428`
- `kdb2      0.00428`
- `ksb       4.0`
- `chi       3154000`

Functions and simulation/action commands:

- `generate_network({overwrite=>1,max_stoich=>{APC=>1,AXIN=>1,bCat=>1}});`
- `simulate_ode({t_end=>250000, n_steps=>2500,atoll=>1e-08,rtol=>1e-08,sparse=>1});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)**: Reversible binding/release. The nearby model comment says: “Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf1_bap,  kr1_bap`.
- **Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)**: Reversible binding/release. The nearby model comment says: “Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)”. The rule involves `APC`, `AXIN`, `bCat` and produces `APC`, `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf1_bap,  kr1_bap`.
- **Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)**: Reversible binding/release. The nearby model comment says: “Binding of beta-catenin ARM repeats 5-9 to APC 15-aa repeats (Arrow 1)”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf1_bap,  kr1_bap`.
- **Binding of beta-catenin ARM repeats 3-4 to phosphorylated APC 20-aa repeats (Arrow 2)**: Reversible binding/release. The nearby model comment says: “Binding of beta-catenin ARM repeats 3-4 to phosphorylated APC 20-aa repeats (Arrow 2)”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf2_bap,  kr2_bap`.
- **Binding of beta-catenin ARM repeats 3-4 to phosphorylated APC 20-aa repeats (Arrow 2)**: Reversible binding/release. The nearby model comment says: “Binding of beta-catenin ARM repeats 3-4 to phosphorylated APC 20-aa repeats (Arrow 2)”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf2_bap,  kr2_bap`.
- **Binding of beta-Catenin ARM repeats 3 and 4 with Axin (Arrow 3)**: Reversible binding/release. The nearby model comment says: “Binding of beta-Catenin ARM repeats 3 and 4 with Axin (Arrow 3)”. The rule involves `AXIN`, `bCat` and produces `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_ba,  kr_ba`.
- **Binding of beta-Catenin ARM repeats 3 and 4 with Axin (Arrow 3)**: Reversible binding/release. The nearby model comment says: “Binding of beta-Catenin ARM repeats 3 and 4 with Axin (Arrow 3)”. The rule involves `APC`, `AXIN`, `bCat` and produces `APC`, `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf_ba,  kr_ba`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN` and produces `APC`, `AXIN`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_apa,  kr_apa`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN` and produces `APC`, `AXIN`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_apa,  kr_apa`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN` and produces `APC`, `AXIN`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_apa,  kr_apa`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN`, `bCat` and produces `APC`, `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf_apa,  kr_apa`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN`, `bCat` and produces `APC`, `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf_apa,  kr_apa`.
- **Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)**: Reversible binding/release. The nearby model comment says: “Binding of APC SAMP repeats to Axin RGS domain (Arrow 4)”. The rule involves `APC`, `AXIN`, `bCat` and produces `APC`, `AXIN`, `bCat`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `chi*kf_apa,  kr_apa`.
- **Binding of GSK-3beta to AXIN GID domain (Arrow 5)**: Reversible binding/release. The nearby model comment says: “Binding of GSK-3beta to AXIN GID domain (Arrow 5)”. The rule involves `AXIN`, `GSK3b` and produces `AXIN`, `GSK3b`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_ga,  kr_ga`.
- **Binding of CK1alpha to Axin (Arrow 6)**: Reversible binding/release. The nearby model comment says: “Binding of CK1alpha to Axin (Arrow 6)”. The rule involves `AXIN`, `CK1a` and produces `AXIN`, `CK1a`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kf_ca,  kr_ca`.
- **Phosphorylation of S45 of beta-catenin by CK1alpha (Arrow 7)**: State change or catalytic conversion. The nearby model comment says: “Phosphorylation of S45 of beta-catenin by CK1alpha (Arrow 7)”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is `bCat` site `s45` changes from `U` to `P`; site `s45` changes from `U` to `P`. Rate parameter(s): `kpb`.
- **Phosphorylation of S33/S37 of beta-catenin by GSK-3beta (Arrow 8)**: State change or catalytic conversion. The nearby model comment says: “Phosphorylation of S33/S37 of beta-catenin by GSK-3beta (Arrow 8)”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is `bCat` site `s33s37` changes from `U` to `P`; site `s33s37` changes from `U` to `P`. Rate parameter(s): `kpb`.
- **Phosphorylation of APC 20-aa repeat by CK1epsilon (implicit) and GSK-3beta (Arrows 9 and 10)**: State change or catalytic conversion. The nearby model comment says: “Phosphorylation of APC 20-aa repeat by CK1epsilon (implicit) and GSK-3beta (Arrows 9 and 10)”. The rule involves `APC` and produces `APC`. The encoded molecular change is `APC` site `a20` changes from `U` to `P`; site `a20` changes from `U` to `P`. Rate parameter(s): `kp`.
- **Dephsophorylation of beta-catenin**: State change or catalytic conversion. The nearby model comment says: “Dephsophorylation of beta-catenin”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is `bCat` site `s45` changes from `P` to `U`; site `s45` changes from `P` to `U`. Rate parameter(s): `kmpb`.
- **Dephsophorylation of beta-catenin**: State change or catalytic conversion. The nearby model comment says: “Dephsophorylation of beta-catenin”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is `bCat` site `s33s37` changes from `P` to `U`; site `s33s37` changes from `P` to `U`. Rate parameter(s): `kmpb`.
- **Dephoshporylation of APC**: State change or catalytic conversion. The nearby model comment says: “Dephoshporylation of APC”. The rule involves `APC` and produces `APC`. The encoded molecular change is `APC` site `a20` changes from `P` to `U`; site `a20` changes from `P` to `U`. Rate parameter(s): `kmp`.
- **b-catenin synthesis**: Production, removal, or biochemical conversion. The nearby model comment says: “b-catenin synthesis”. The rule involves the listed reactant pattern and produces `bCat`. Rate parameter(s): `ksb`.
- **Degradation of beta-catenin not phosphorylated at S33/S37**: State change or catalytic conversion. The nearby model comment says: “Degradation of beta-catenin not phosphorylated at S33/S37”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is site `ss` changes from `l` to `d`. Rate parameter(s): `kdb1`.
- **Degradation of beta-catenin phosphorylated at S33/S37**: State change or catalytic conversion. The nearby model comment says: “Degradation of beta-catenin phosphorylated at S33/S37”. The rule involves `bCat` and produces `bCat`. The encoded molecular change is site `ss` changes from `l` to `d`. Rate parameter(s): `kdb2`.
- **(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin**: Unbinding or disassembly. The nearby model comment says: “(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1000`.
- **(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin**: Unbinding or disassembly. The nearby model comment says: “(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1000`.
- **(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin**: Unbinding or disassembly. The nearby model comment says: “(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin”. The rule involves `APC`, `bCat` and produces `APC`, `bCat`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1000`.
- **(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin**: Unbinding or disassembly. The nearby model comment says: “(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin”. The rule involves `AXIN`, `bCat` and produces `AXIN`, `bCat`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1000`.
- **(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin**: Unbinding or disassembly. The nearby model comment says: “(Assumed) rapid dissociation of beta-catenin associated proteins upon degradation of beta-catenin”. The rule involves `AXIN`, `bCat` and produces `AXIN`, `bCat`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1000`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `bcat_tot` (Molecules) tracks patterns containing bCat. Pattern: `bCat(ss~l)`.
- `bCat_pS45` (Molecules) tracks phosphorylated/modified molecules. Pattern: `bCat(s45~P,ss~l)`.
- `bCat_pS33S37` (Molecules) tracks phosphorylated/modified molecules. Pattern: `bCat(s33s37~P,ss~l)`.
- `APC_p20a` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `APC(a20~P!?)`.
- `BCat_Axin` (Species) tracks bound complexes. Pattern: `bCat(ARM34!1,ss~l).AXIN(b!1)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2013`
- Title/name: `Barua 2013`
- Category: `regulation`
- Tags: `['published', 'barua', '2013', 'axin', 'gsk3b', 'apc', 'bcat', 'ck1a']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/cell-regulation/Barua_2013.bngl`
- Local BNGL file used: `Published/Barua2013/Barua_2013.bngl`
- Local YAML file used: `Published/Barua2013/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
