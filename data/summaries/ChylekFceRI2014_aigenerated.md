# Model Explanation: Chylek 2014 (FceRI)

## 1. One-sentence summary

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output.

## 2. Biological meaning

This model represents early FcεRI/IgE receptor signaling, where ligand crosslinking recruits Lyn/Syk and downstream adaptors while phosphorylation, dephosphorylation, and membrane-raft localization regulate output. The local model comments and metadata give this context: Xu K, Goldstein B, Holowka D, Baird B. Kinetics of multivalent antigen DNP-BSA binding to IgE-Fc epsilon RI in relationship to the stimulated tyrosine phosphorylation of Fc epsilon RI. J Immunol. (1998) 160:3225-35. Faeder JR, Hlavacek WS, Reischl I, Blinov ML, Metzger H, Redondo A, Wofsy C, Goldstein B. Investigation of early events in Fc epsilon RI-mediated signaling using a detailed mathematical model. J Immunol. (2003) 170:3769-81. Barua D, Hlavacek WS, Lipniacki T. A computational model for early events in B cell antigen receptor signaling: analysis of the roles of Lyn and Fyn. J Immunol. (2012) 189:646-58. Lenoci L, Duvernay M, Satchell S, DiBenedetto E, Hamm HE. Mathematical model of PAR1-mediated activation of human platelets. Mol Biosyst.7:1129-37. (2011) Residue numbers, where applicable, are given for rat proteins. The ligand is DNP-BSA and is taken to have two virtual haptens. Each hapten has two possible states, buried (b) or exposed (e). The receptor is a complex of FceRI and an IgE antibody. The "fab" components represent the two fab arms of hapten-specific IgE. b_Y218 and b_Y224 are tyrosines in the ITAM of the beta subunit. b_Y224 is non-canonical, located between the two canonical tyrosines of the ITAM. Y65 and Y76 are tyrosines in the ITAM of the gamma subunit and are lumped as a single site. Only one (of the two) gamma chains is considered, as a simplification. Lyn is an SFK with a unique domain (U), an SH2 domain, and an SH3 domain.. The explanation below is therefore based on the local BNGL model file `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl` and metadata file `Published/ChylekFceRI2014/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Lig`: Lig. It has state sites `hap~b~e`, `hap~b~e`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Rec`: Rec. It has binding/interaction sites `fab`, `fab` and regulated state sites `b_Y218~0~P`, `b_Y224~0~P`, `g_Y65_Y76~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lyn`: Lyn kinase. It has binding/interaction sites `U`, `SH3`, `SH2` and regulated state sites `Y397~0~P`, `Y508~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Fyn`: Fyn kinase. It has binding/interaction sites `U`, `SH3`, `SH2`, `PTK` and regulated state sites `Y420~0~P`, `Y531~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Syk`: Syk kinase. It has binding/interaction sites `tSH2`, `PTK` and regulated state sites `Y346~0~P`, `Y519_Y520~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Pag1`: Pag1. It has binding/interaction sites `PRS1`, `PRS2` and regulated state sites `Y165_Y183~0~P`, `Y317~0~P`, `Y386_Y409~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Csk`: Csk. It has binding or interaction sites `SH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lat`: Lat. It has state sites `Y136~0~P`, `Y175~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Plcg1`: Plcg1. It has binding/interaction sites `SH2`, `SH3`, `PLC` and regulated state sites `Y783~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Grb2`: Grb2. It has binding or interaction sites `SH2`, `cSH3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Gab2`: Gab2. It has binding/interaction sites `PRS` and regulated state sites `Y441~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Grap2`: Grap2. It has binding or interaction sites `SH2`, `SH3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lcp2`: Lcp2. It has binding or interaction sites `RxxK`, `PRS`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Pi3k`: Pi3k. It has binding or interaction sites `p85_SH2`, `PI3Kc`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Btk`: Btk. It has binding or interaction sites `PH`, `PTK`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Inpp5d`: Inpp5d. It has binding or interaction sites `SH2`, `IPP`, `C2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI34P2`: PI34P2. It has binding or interaction sites `bind`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI45P2`: PI45P2. It has binding or interaction sites `bind`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI345P3`: PI345P3. It has binding or interaction sites `bind`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IP3`: IP3. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `DAG`: DAG. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Sink`: Sink. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI4P`: PI4P. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `Lig(hap~b,hap~b) SimLigTot`
- `Rec(fab,fab,b_Y218~0,b_Y224~0,g_Y65_Y76~0) SimProteinTot`
- `Lyn(U,SH2,SH3,Y397~0,Y508~0) SimProteinTot`
- `Fyn(U,SH2,SH3,Y420~0,PTK,Y531~0) SimProteinTot`
- `Syk(tSH2,Y346~0,PTK,Y519_Y520~0) SimProteinTot`
- `Pag1(PRS1,PRS2,Y317~0,Y165_Y183~0,Y386_Y409~0) SimProteinTot`
- `Csk(SH2) SimProteinTot`
- `Lat(Y136~0,Y175~0) SimProteinTot`
- `Plcg1(SH2,SH3,PLC,Y783~0) SimProteinTot`
- `Grb2(SH2,cSH3) SimProteinTot`
- `Gab2(PRS,Y441~0) SimProteinTot`
- `PI45P2(bind) SimProteinTot`
- `Pi3k(PI3Kc,p85_SH2) SimProteinTot`
- `Btk(PH,PTK) SimProteinTot`
- `Inpp5d(SH2,C2,IPP) SimProteinTot`
- `Grap2(SH2,SH3) SimProteinTot`
- `Lcp2(RxxK,PRS) SimProteinTot`
- `PI4P()	       SimProteinTot`
- `Sink()	       SimProteinTot`

Important parameters include:

- `NA		6.022e23`
- `celldensity	1e9`
- `Fx     		0.02`
- `ECFvol          1/(celldensity)`
- `simECFvol       ECFvol*Fx`
- `Cellvol         1.4e-12`
- `simCellvol	Cellvol*Fx`
- `ProteinTot	3e5`
- `SimProteinTot	Fx*ProteinTot`
- `LigTot		5e4`
- `SimLigTot	Fx*LigTot`
- `lambda_p	1.7e-2`
- `lambda_m	5.4e-2`
- `kfl	 	0`
- `kxl	        1.3/SimProteinTot`
- `krl		1.4e-1`
- `kfRecLyn1	4.2e7/(NA*simCellvol)`
- `krRecLyn1	20`
- `kfRecLyn2	kfRecLyn1`
- `krRecLyn2	0.12`
- `kpLynB1	   	30`
- `kpLynB2	   	100`
- `kpLynG1	   1`
- `kpLynG2 	3`
- `kfLynIn		10`

Functions and simulation/action commands:

- `writeXML();`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Haptens are transiently exposed.**: State change or catalytic conversion. The nearby model comment says: “Haptens are transiently exposed.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `hap` changes from `b` to `e`; site `hap` changes from `b` to `e`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `lambda_p, lambda_m`.
- **Binding from solution when a hapten is exposed. Does not depend on state of second hapten.**: Binding or assembly. The nearby model comment says: “Binding from solution when a hapten is exposed. Does not depend on state of second hapten.”. The rule involves `Lig`, `Rec` and produces `Lig`, `Rec`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kfl`.
- **Binding from solution when a hapten is exposed. Does not depend on state of second hapten.**: Binding or assembly. The nearby model comment says: “Binding from solution when a hapten is exposed. Does not depend on state of second hapten.”. The rule involves `Lig`, `Rec` and produces `Lig`, `Rec`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `kfl`.
- **Receptor crosslinking when both haptens are exposed.**: Unbinding or disassembly. The nearby model comment says: “Receptor crosslinking when both haptens are exposed.”. The rule involves `Lig`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Receptor crosslinking when both haptens are exposed.**: Unbinding or disassembly. The nearby model comment says: “Receptor crosslinking when both haptens are exposed.”. The rule involves `Lig`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Dissociation of hapten from receptor site**: Unbinding or disassembly. The nearby model comment says: “Dissociation of hapten from receptor site”. The rule involves `Lig`, `Rec` and produces `Lig`, `Rec`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `krl`.
- **Lyn unique domain binds receptor**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn unique domain binds receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. 
- **Lyn unique domain binds receptor**: Unbinding or disassembly. The nearby model comment says: “Lyn unique domain binds receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn unique domain dissociates from receptor**: Unbinding or disassembly. The nearby model comment says: “Lyn unique domain dissociates from receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn unique domain dissociates from receptor**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn unique domain dissociates from receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. 
- **Lyn SH2 domain binds receptor**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn SH2 domain binds receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. 
- **Lyn SH2 domain binds receptor**: Unbinding or disassembly. The nearby model comment says: “Lyn SH2 domain binds receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn SH2 domain dissociates from receptor**: Unbinding or disassembly. The nearby model comment says: “Lyn SH2 domain dissociates from receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn SH2 domain dissociates from receptor**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn SH2 domain dissociates from receptor”. The rule involves `Lyn`, `Rec` and produces the listed product pattern. 
- **Lyn SH2 domain binds Lyn pY508, forming an intramolecular bond**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn SH2 domain binds Lyn pY508, forming an intramolecular bond”. The rule involves `Lyn` and produces the listed product pattern. 
- **Lyn SH2 domain binds Lyn pY508, forming an intramolecular bond**: Unbinding or disassembly. The nearby model comment says: “Lyn SH2 domain binds Lyn pY508, forming an intramolecular bond”. The rule involves `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn SH2 dissociates from Lyn pY508**: Unbinding or disassembly. The nearby model comment says: “Lyn SH2 dissociates from Lyn pY508”. The rule involves `Lyn` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn SH2 dissociates from Lyn pY508**: Production, removal, or biochemical conversion. The nearby model comment says: “Lyn SH2 dissociates from Lyn pY508”. The rule involves `Lyn` and produces the listed product pattern. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. The encoded molecular change is `Rec` site `b_Y218` changes from `0` to `P`. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. The encoded molecular change is `Rec` site `b_Y218` changes from `P` to `0`. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unqiue domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unqiue domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Syk binds the dually phosphorylated gamma subunit of the receptor**: Reversible binding/release. The nearby model comment says: “Syk binds the dually phosphorylated gamma subunit of the receptor”. The rule involves `Rec`, `Syk` and produces `Rec`, `Syk`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfRecSyk, krRecSyk`.
- **Lyn bound by its unique domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unique domain”. The rule involves `Lig`, `Lyn`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its unique domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its unique domain”. The rule involves `Lig`, `Lyn`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn bound by its SH2 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn bound by its SH2 domain”. The rule involves `Lig`, `Lyn`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Syk unphosphorlyated on activation loop**: Unbinding or disassembly. The nearby model comment says: “Syk unphosphorlyated on activation loop”. The rule involves `Lig`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Syk unphosphorlyated on activation loop**: Unbinding or disassembly. The nearby model comment says: “Syk unphosphorlyated on activation loop”. The rule involves `Lig`, `Rec`, `Syk` and produces the listed product pattern. The encoded molecular change is `Syk` site `Y519_Y520` changes from `0` to `P`. Loss of matching `!` labels means a complex separates. 
- **Syk phosphorylated on activation loop**: Unbinding or disassembly. The nearby model comment says: “Syk phosphorylated on activation loop”. The rule involves `Lig`, `Rec`, `Syk` and produces the listed product pattern. The encoded molecular change is `Syk` site `Y519_Y520` changes from `P` to `0`. Loss of matching `!` labels means a complex separates. 
- **Syk phosphorylated on activation loop**: Unbinding or disassembly. The nearby model comment says: “Syk phosphorylated on activation loop”. The rule involves `Lig`, `Rec`, `Syk` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Association when Lyn is free**: Production, removal, or biochemical conversion. The nearby model comment says: “Association when Lyn is free”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. 
- **Association when Lyn is free**: Unbinding or disassembly. The nearby model comment says: “Association when Lyn is free”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn, already tethered in Pag1 by SH2, binds Pag1 via SH3 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn, already tethered in Pag1 by SH2, binds Pag1 via SH3 domain”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn, already tethered in Pag1 by SH2, binds Pag1 via SH3 domain**: Unbinding or disassembly. The nearby model comment says: “Lyn, already tethered in Pag1 by SH2, binds Pag1 via SH3 domain”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Dissociation of Lyn SH3**: Unbinding or disassembly. The nearby model comment says: “Dissociation of Lyn SH3”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Dissociation of Lyn SH3**: Production, removal, or biochemical conversion. The nearby model comment says: “Dissociation of Lyn SH3”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. 
- **Association when Lyn is free**: Production, removal, or biochemical conversion. The nearby model comment says: “Association when Lyn is free”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. 
- **Association when Lyn is free**: Unbinding or disassembly. The nearby model comment says: “Association when Lyn is free”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Association when Lyn is tethered to Pag1 via an SH3 domain-PRS interaction**: Unbinding or disassembly. The nearby model comment says: “Association when Lyn is tethered to Pag1 via an SH3 domain-PRS interaction”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Association when Lyn is tethered to Pag1 via an SH3 domain-PRS interaction**: Unbinding or disassembly. The nearby model comment says: “Association when Lyn is tethered to Pag1 via an SH3 domain-PRS interaction”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **we omit dissociation of the SH2 domain alone, as a simplification.**: Unbinding or disassembly. The nearby model comment says: “we omit dissociation of the SH2 domain alone, as a simplification.”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **we omit dissociation of the SH2 domain alone, as a simplification.**: Production, removal, or biochemical conversion. The nearby model comment says: “we omit dissociation of the SH2 domain alone, as a simplification.”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. 
- **Lyn phosphorylates Y386 and Y409 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y386 and Y409 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y386 and Y409 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y386 and Y409 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Lyn phosphorylates Y165 and Y183 in Pag1**: Unbinding or disassembly. The nearby model comment says: “Lyn phosphorylates Y165 and Y183 in Pag1”. The rule involves `Lyn`, `Pag1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- Additional rules are present after these 60 entries; they are mostly continuations of the same rule families above and should be read in the BNGL file for exhaustive curation.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Lat_pY136` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lat(Y136~P!?)`.
- `Lat_pY175` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lat(Y175~P!?)`.
- `Rec_pY218` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Rec(b_Y218~P!?)`.
- `Rec_pY224` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Rec(b_Y224~P!?)`.
- `Rec_pY65_Y76` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Rec(g_Y65_Y76~P!?)`.
- `Syk_pY346` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Syk(Y346~P!?)`.
- `Gab2_pY441` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Gab2(Y441~P!?)`.
- `PI3K_recruited` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lat(Y175~P!1).Grb2(SH2!1,cSH3!2).Gab2(PRS!2,Y441~P!3).Pi3k(p85_SH2!3)`.
- `PI345P3` (Molecules) tracks bound complexes. Pattern: `PI345P3(bind!?)`.
- `Plcg1_pY783` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Plcg1(Y783~P!?)`.
- `LynUbound` (Molecules) tracks bound complexes. Pattern: `Lyn(U!+)`.
- `LynSH2bound` (Molecules) tracks bound complexes. Pattern: `Lyn(SH2!+)`.
- `Shipbound` (Molecules) tracks bound complexes. Pattern: `Inpp5d(SH2!+)`.
- `Plc_pip2` (Molecules) tracks bound complexes. Pattern: `Plcg1(PLC!1).PI45P2(bind!1)`.
- `Lat_Plc` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lat(Y136~P!1).Plcg1(SH2!1)`.
- `IP3` (Molecules) tracks patterns containing IP3. Pattern: `IP3()`.
- `PI34P2` (Molecules) tracks bound complexes. Pattern: `PI34P2(bind!?)`.
- `PI45P2` (Molecules) tracks bound complexes. Pattern: `PI45P2(bind!?)`.
- `Pag_Y165` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Pag1(Y165_Y183~P!?)`.
- `Pag_Y409` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Pag1(Y386_Y409~P!?)`.
- `LynIn` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lyn(SH2!1,Y508~P!1)`.
- `FynIn` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Fyn(SH2!1,Y531~P!1)`.
- `Lyn_pY508` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Lyn(Y508~P!?)`.
- `Fyn_pY508` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Fyn(Y531~P!?)`.
- `Btk_recruited` (Molecules) tracks bound complexes. Pattern: `Btk(PH!+)`.
- `LigFree` (Molecules) tracks patterns containing Lig. Pattern: `Lig(hap,hap)`.
- `Crosslinks` (Molecules) tracks bound complexes. Pattern: `Lig(hap~e!1,hap~e!2).Rec(fab!1).Rec(fab!2)`.
- `DNP_exposed_0_of_2` (Molecules) tracks bound complexes. Pattern: `Lig(hap~b!?,hap~b!?)`.
- `DNP_exposed_1_of_2` (Molecules) tracks bound complexes. Pattern: `Lig(hap~b!?,hap~e!?)`.
- `DNP_exposed_2_of_2` (Molecules) tracks bound complexes. Pattern: `Lig(hap~e!?,hap~e!?)`.
- `LigTotal` (Molecules) tracks bound complexes. Pattern: `Lig(hap!?,hap!?)`.
- `Syk_pY519_520` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Syk(Y519_Y520~P)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `ChylekFceRI_2014`
- Title/name: `Chylek 2014 (FceRI)`
- Category: `immunology`
- Tags: `['published', 'immunology', 'chylekfceri', '2014', 'lig', 'rec', 'lyn', 'fyn', 'syk', 'pag1', 'csk', 'lat']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/immune-signaling/ChylekFceRI_2014.bngl`
- Local BNGL file used: `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl`
- Local YAML file used: `Published/ChylekFceRI2014/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `true`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
