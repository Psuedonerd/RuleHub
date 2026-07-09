# Model Explanation: Barua 2013

## 1. One-sentence summary

This model represents beta-catenin destruction using BNGL rules for the molecules and interactions encoded in `Barua_2013.bngl`.

## 2. Biological meaning

The metadata describes this model as **Beta-catenin destruction** and places it in the `regulation` category. Tags provided by the repository are: `published`, `barua`, `2013`, `axin`, `gsk3b`, `apc`, `bcat`, `ck1a`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `AXIN(rgs,gid,b,e)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `GSK3b(a)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `APC(a15,a20~U~P,s)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `bCat(s33s37~U~P,s45~U~P,ARM34,ARM59,ss~l~d)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `CK1a(e)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `dead`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `I`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `bCat(s33s37~U,s45~U,,ARM34,ARM59,ss~l)  BCATtot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `APC(a15,a20~U,s)  APCtot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `AXIN(rgs,gid,b,e)  AXINtot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `GSK3b(a) GSKtot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `CK1a(e)   CK1atot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `I    1`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `dead 0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

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

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1,max_stoich=>{APC=>1,AXIN=>1,bCat=>1}});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>250000, n_steps=>2500,atoll=>1e-08,rtol=>1e-08,sparse=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `bCat(ARM59,ss~l) + APC(a15)` is converted to `bCat(ARM59!1,ss~l).APC(a15!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1_bap,  kr1_bap`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(ARM59,ARM34!1,ss~l).AXIN(b!1,rgs!2).APC(a15,s!2)` is converted to `bCat(ARM59!3,ARM34!1,ss~l).AXIN(b!1,rgs!2).APC(a15!3,s!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf1_bap,  kr1_bap`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(ARM59,ARM34!1).APC(a15,a20~P!1)` is converted to `bCat(ARM59!2,ARM34!1).APC(a15!2,a20~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf1_bap,  kr1_bap`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `bCat(ARM34,ss~l) + APC(a20~P)` is converted to `bCat(ARM34!1,ss~l).APC(a20~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2_bap,  kr2_bap`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(ARM59!1,ARM34).APC(a15!1,a20~P)` is converted to `bCat(ARM59!1,ARM34!2).APC(a15!1,a20~P!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf2_bap,  kr2_bap`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `bCat(ARM34,ss~l) + AXIN(b)` is converted to `bCat(ARM34!1,ss~l).AXIN(b!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_ba,  kr_ba`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(ARM59!1,ARM34,ss~l).AXIN(b,rgs!2).APC(a15!1,s!2)` is converted to `bCat(ARM59!1,ARM34!3,ss~l).AXIN(b!3,rgs!2).APC(a15!1,s!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf_ba,  kr_ba`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `APC(a20~U,s) + AXIN(rgs)` is converted to `APC(a20~U,s!1).AXIN(rgs!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_apa,  kr_apa`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `APC(a20~P,s) + AXIN(rgs)` is converted to `APC(a20~P,s!1).AXIN(rgs!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_apa,  kr_apa`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a20~P!+,s) + AXIN(rgs)` is converted to `APC(a20~P!+,s!1).AXIN(rgs!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_apa,  kr_apa`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a15!1,a20~U,s).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs,b!2)` is converted to `APC(a15!1,a20~U,s!3).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs!3,b!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf_apa,  kr_apa`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a15!1,a20~P,s).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs,b!2)` is converted to `APC(a15!1,a20~P,s!3).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs!3,b!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf_apa,  kr_apa`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a15!1,a20~P!+,s).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs,b!2)` is converted to `APC(a15!1,a20~P!+,s!3).bCat(ARM59!1,ARM34!2,ss~l).AXIN(rgs!3,b!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `chi*kf_apa,  kr_apa`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `GSK3b(a) + AXIN(gid)` is converted to `GSK3b(a!1).AXIN(gid!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_ga,  kr_ga`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `AXIN(e) + CK1a(e)` is converted to `AXIN(e!1).CK1a(e!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf_ca,  kr_ca`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s45~U,ss~l).CK1a` is converted to `bCat(s45~P,ss~l).CK1a`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kpb`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s33s37~U,s45~P,ss~l).GSK3b` is converted to `bCat(s33s37~P,s45~P,ss~l).GSK3b`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kpb`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a20~U).GSK3b` is converted to `APC(a20~P).GSK3b`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s45~P,ss~l)` is converted to `bCat(s45~U,ss~l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kmpb`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s33s37~P,ss~l)` is converted to `bCat(s33s37~U,ss~l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kmpb`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `APC(a20~P).AXIN` is converted to `APC(a20~U).AXIN`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kmp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `I` is converted to `I + bCat(s33s37~U,s45~U,ARM59,ARM34,ss~l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `ksb`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s33s37~U,ss~l)` is converted to `bCat(s33s37~U,ss~d)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdb1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `bCat(s33s37~P,ss~l)` is converted to `bCat(s33s37~P,ss~d)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdb2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `bCat(ARM59!1,ss~d).APC(a15!1)` is converted to `bCat(ARM59,ss~d) + APC(a15)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1000`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `bCat(ARM59!1,ss~d).APC(a15!1)` is converted to `bCat(ARM59,ss~d).APC(a15)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1000`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `bCat(ARM34!1,ss~d).APC(a20~P!1)` is converted to `bCat(ARM34,ss~d) + APC(a20~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1000`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `bCat(ARM34!1,ss~d).AXIN(b!1)` is converted to `bCat(ARM34,ss~d) + AXIN(b)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1000`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `bCat(ARM34!1,ss~d).AXIN(b!1)` is converted to `bCat(ARM34,ss~d).AXIN(b)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1000`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules bcat_tot         bCat(ss~l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules bCat_pS45        bCat(s45~P,ss~l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules bCat_pS33S37     bCat(s33s37~P,ss~l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules APC_p20a         APC(a20~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species   BCat_Axin        bCat(ARM34!1,ss~l).AXIN(b!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2013`
- Title/name: `Barua 2013`
- Category: `regulation`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/cell-regulation/Barua_2013.bngl`
- BNGL file used locally: `Published/Barua2013/Barua_2013.bngl`
- YAML file used locally: `Published/Barua2013/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
