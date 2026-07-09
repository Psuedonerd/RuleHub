# Model Explanation: Chylek 2014 (TCR)

## 1. One-sentence summary

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation.

## 2. Biological meaning

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation. The local model comments and metadata give this context: Supplementary File A in File S1 "Phosphorylation site dynamics of early T-cell receptor signaling" L.A. Chylek, V. Akimov, J. Dengjel, K.T.G. Rigbolt, B. Hu, W.S. Hlavacek, B. Blagoev This file is an encoding of the TCR signaling model in BNGL. For a description of BNGL, see: Faeder JR, Blinov ML, Hlavacek WS, Rule-based modeling of biochemical systems with BioNetGen. Methods Mol. Biol. 500, 113-167 (2009). This file can be processed by BNGL-compatible tools, such as BioNetGen (http://bionetgen.org/) and NFsim (http://emonet.biology.yale.edu/nfsim/). This file is meant to be used in conjunction with Supplementary File B in File S1, which is a simulation protocol for NFsim in the form of an RNF (Run NFsim) script. This file should be named FileA.bngl (to ensure proper processing by BioNetGen and subsequent processing of the output by NFsim) Use of a subvolume speeds simulation, see Faeder et al. (2009) Units and descriptions of parameters below are given in Supplementary Table S2 (Excel spreadsheet of parameter values) Protein copy numbers are given on a per cell basis Descriptions of molecule types can be found in the Supplementary Text (model guide, File S3) Seed species are used to initialize a simulation. Following each molecule is parameter that specifies copy number To simulate PTPN6 knockdown, the copy number of PTPN6 was set to 0.. The explanation below is therefore based on the local BNGL model file `Published/ChylekTCR2014/ChylekTCR_2014.bngl` and metadata file `Published/ChylekTCR2014/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Lig1`: Lig1. It has binding or interaction sites `aCD28`, `aCD28`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lig2`: Lig2. It has binding or interaction sites `aCD28`, `aCD3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Lig3`: Lig3. It has binding or interaction sites `aCD3`, `aCD3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TCR`: TCR. It has binding/interaction sites `epitope`, `fynbind`, `PRS_E` and regulated state sites `Y149_D~0~P`, `Y171_G~0~P`, `Y111~0~P`, `Y123~0~P`, `Y188_E~0~P`, `Y199_E~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `CD28`: CD28. It has binding or interaction sites `epitope`, `PRS1`, `PRS2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `LCK`: LCK. It has binding/interaction sites `SH2`, `SH3` and regulated state sites `Y192~0~P`, `Y424~0~P`, `Y505~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `ITK`: ITK. It has binding/interaction sites `SH3`, `SH2`, `PTK` and regulated state sites `Y512~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `ZAP70`: ZAP70. It has binding/interaction sites `SH2`, `PTK` and regulated state sites `Y493~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PTPN6`: PTPN6. It has binding/interaction sites `SH2`, `PTP` and regulated state sites `Y566~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PAG1`: PAG1. It has state sites `Y163~0~P`, `Y317~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `CSK`: CSK. It has binding or interaction sites `SH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `DOK1`: DOK1. It has state sites `Y449~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `DOK2`: DOK2. It has state sites `Y299~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `FYN`: FYN. It has binding or interaction sites `unique`, `PTK`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `NCK`: NCK. It has binding or interaction sites `SH3_1`, `SH3_3`, `SH2`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `WAS`: WAS. It has binding/interaction sites `PRS` and regulated state sites `Y291~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `LAT`: LAT. It has state sites `Y132~0~P`, `Y191~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PLCG1`: PLCG1. It has binding/interaction sites `SH2`, `SH3` and regulated state sites `Y783~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `GRAP2`: GRAP2. It has binding or interaction sites `SH2`, `SH3`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `LCP2`: LCP2. It has binding/interaction sites `RxxK`, `PRS` and regulated state sites `Y113_Y128~0~P`, `Y145~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `Lig1(aCD28,aCD28) Ligtot`
- `Lig2(aCD28,aCD3) Ligtot`
- `Lig3(aCD3,aCD3) Ligtot`
- `CD28(epitope,PRS1,PRS2) CD28tot`
- `TCR(epitope,Y149_D~0,Y171_G~0,Y111~0,Y123~0,fynbind,PRS_E,Y188_E~0,Y199_E~0) TCRtot`
- `LCK(SH2,SH3,Y192~0,Y424~0,Y505~0) Proteintot`
- `ITK(SH3,SH2,PTK,Y512~0) Proteintot`
- `ZAP70(SH2,PTK,Y493~0) Proteintot`
- `PAG1(Y163~0,Y317~0) Proteintot`
- `CSK(SH2) Proteintot`
- `DOK1(Y449~0) Proteintot`
- `DOK2(Y299~0) Proteintot`
- `FYN(unique,PTK) Proteintot`
- `NCK(SH3_1,SH3_3,SH2) Proteintot`
- `WAS(PRS,Y291~0) Proteintot`
- `LAT(Y132~0,Y191~0) Proteintot`
- `PLCG1(SH2,SH3,Y783~0) Proteintot`
- `GRAP2(SH2,SH3) Proteintot`
- `PTPN6(SH2,PTP,Y566~0) Proteintot`
- `LCP2(RxxK,Y113_Y128~0,PRS,Y145~0) Proteintot`

Important parameters include:

- `NA		6.022e23`
- `celldensity     9.7e10`
- `Fx     		0.02`
- `ECFvol          1/(celldensity)`
- `simECFvol       ECFvol*Fx`
- `Cellvol         1.0e-12`
- `simCellvol	Cellvol*Fx`
- `kfLckCd28	 2.5e7/(NA*simCellvol)`
- `krLckCd28 	 36`
- `kfItkCd28 	 kfLckCd28`
- `krItkCd28 	 0.002`
- `act		 2`
- `kpLckLck1 	 10`
- `kpLckLck2 	 act*kpLckLck1`
- `kpLckItk1 	 3`
- `kpLckItk2 	 act*kpLckItk1`
- `kpLckTcrz1 	 2`
- `kpLckTcrz2 	 2`
- `kpLckCd3e1 	 2`
- `kpLckCd3e2 	 2`
- `kpLckCd3g 	 6`
- `kpLckCd3d 	 6`
- `kfZapTcr 	 4.5e7/(NA*simCellvol)`
- `krZapTcr 	 0.25`
- `kfZapCd3e 	 kfZapTcr`

Functions and simulation/action commands:

- `writeXML();`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Rule 1a**: Reversible binding/release. The nearby model comment says: “Rule 1a”. The rule involves `CD28`, `Lig1` and produces `CD28`, `Lig1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl, krl`.
- **Rule 1b**: Reversible binding/release. The nearby model comment says: “Rule 1b”. The rule involves `CD28`, `Lig1` and produces `CD28`, `Lig1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl_m, krl`.
- **Rule 2a**: Reversible binding/release. The nearby model comment says: “Rule 2a”. The rule involves `Lig3`, `TCR` and produces `Lig3`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl, krl`.
- **Rule 2b**: Reversible binding/release. The nearby model comment says: “Rule 2b”. The rule involves `Lig3`, `TCR` and produces `Lig3`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl_m, krl`.
- **Rule 3a**: Reversible binding/release. The nearby model comment says: “Rule 3a”. The rule involves `CD28`, `Lig2` and produces `CD28`, `Lig2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl, krl`.
- **Rule 3b**: Reversible binding/release. The nearby model comment says: “Rule 3b”. The rule involves `CD28`, `Lig2`, `TCR` and produces `CD28`, `Lig2`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl_m, krl`.
- **Rule 3c**: Reversible binding/release. The nearby model comment says: “Rule 3c”. The rule involves `Lig2`, `TCR` and produces `Lig2`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl, krl`.
- **Rule 3d**: Reversible binding/release. The nearby model comment says: “Rule 3d”. The rule involves `CD28`, `Lig2`, `TCR` and produces `CD28`, `Lig2`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfl_m, krl`.
- **Rule 4**: Reversible binding/release. The nearby model comment says: “Rule 4”. The rule involves `CD28`, `LCK` and produces `CD28`, `LCK`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfLckCd28, krLckCd28`.
- **Rule 5**: Reversible binding/release. The nearby model comment says: “Rule 5”. The rule involves `CD28`, `ITK` and produces `CD28`, `ITK`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfItkCd28,  krItkCd28`.
- **Rule 6**: Reversible binding/release. The nearby model comment says: “Rule 6”. The rule involves `FYN`, `TCR` and produces `FYN`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfTcrFyn, krTcrFyn`.
- **Rule 7a**: Reversible binding/release. The nearby model comment says: “Rule 7a”. The rule involves `NCK`, `TCR` and produces `NCK`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfWasNck, krWasNck`.
- **Rule 7b**: Unbinding or disassembly. The nearby model comment says: “Rule 7b”. The rule involves `NCK`, `TCR` and produces `NCK`, `TCR`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `1e5*krWasNck`.
- **Rule 8**: Reversible binding/release. The nearby model comment says: “Rule 8”. The rule involves `TCR`, `ZAP70` and produces `TCR`, `ZAP70`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfZapTcr, krZapTcr`.
- **Rule 9**: Reversible binding/release. The nearby model comment says: “Rule 9”. The rule involves `TCR`, `ZAP70` and produces `TCR`, `ZAP70`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfZapTcr, krZapTcr`.
- **Rule 10**: Reversible binding/release. The nearby model comment says: “Rule 10”. The rule involves `TCR`, `ZAP70` and produces `TCR`, `ZAP70`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfZapCd3e, krZapCd3e`.
- **Rule 11**: Reversible binding/release. The nearby model comment says: “Rule 11”. The rule involves `TCR`, `ZAP70` and produces `TCR`, `ZAP70`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfZapCd3e, krZapCd3e`.
- **Rule 12**: Reversible binding/release. The nearby model comment says: “Rule 12”. The rule involves `PTPN6`, `TCR` and produces `PTPN6`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfPtpTcr, krPtpTcr`.
- **Rule 13**: Reversible binding/release. The nearby model comment says: “Rule 13”. The rule involves `PTPN6`, `TCR` and produces `PTPN6`, `TCR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfPtpTcr, krPtpTcr`.
- **Rule 14**: Unbinding or disassembly. The nearby model comment says: “Rule 14”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 14**: Unbinding or disassembly. The nearby model comment says: “Rule 14”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 15**: Unbinding or disassembly. The nearby model comment says: “Rule 15”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 15**: Unbinding or disassembly. The nearby model comment says: “Rule 15”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 16**: Unbinding or disassembly. The nearby model comment says: “Rule 16”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 16**: Unbinding or disassembly. The nearby model comment says: “Rule 16”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 17**: Unbinding or disassembly. The nearby model comment says: “Rule 17”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 17**: Unbinding or disassembly. The nearby model comment says: “Rule 17”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 18**: Unbinding or disassembly. The nearby model comment says: “Rule 18”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 18**: Unbinding or disassembly. The nearby model comment says: “Rule 18”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 19**: Unbinding or disassembly. The nearby model comment says: “Rule 19”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 19**: Unbinding or disassembly. The nearby model comment says: “Rule 19”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 20a**: Unbinding or disassembly. The nearby model comment says: “Rule 20a”. The rule involves `CD28`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 20a**: Unbinding or disassembly. The nearby model comment says: “Rule 20a”. The rule involves `CD28`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 20b**: Unbinding or disassembly. The nearby model comment says: “Rule 20b”. The rule involves `CD28`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 20b**: Unbinding or disassembly. The nearby model comment says: “Rule 20b”. The rule involves `CD28`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 21a**: Unbinding or disassembly. The nearby model comment says: “Rule 21a”. The rule involves `CD28`, `ITK`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 21a**: Unbinding or disassembly. The nearby model comment says: “Rule 21a”. The rule involves `CD28`, `ITK`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 21b**: Unbinding or disassembly. The nearby model comment says: “Rule 21b”. The rule involves `CD28`, `ITK`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 21b**: Unbinding or disassembly. The nearby model comment says: “Rule 21b”. The rule involves `CD28`, `ITK`, `LCK`, `Lig1` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22a**: Unbinding or disassembly. The nearby model comment says: “Rule 22a”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22a**: Unbinding or disassembly. The nearby model comment says: “Rule 22a”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22b**: Unbinding or disassembly. The nearby model comment says: “Rule 22b”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22b**: Unbinding or disassembly. The nearby model comment says: “Rule 22b”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22c**: Unbinding or disassembly. The nearby model comment says: “Rule 22c”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22c**: Unbinding or disassembly. The nearby model comment says: “Rule 22c”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22d**: Unbinding or disassembly. The nearby model comment says: “Rule 22d”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 22d**: Unbinding or disassembly. The nearby model comment says: “Rule 22d”. The rule involves `CD28`, `LCK`, `Lig2`, `TCR`, `ZAP70` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23a**: Unbinding or disassembly. The nearby model comment says: “Rule 23a”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23a**: Unbinding or disassembly. The nearby model comment says: “Rule 23a”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23b**: Unbinding or disassembly. The nearby model comment says: “Rule 23b”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23b**: Unbinding or disassembly. The nearby model comment says: “Rule 23b”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23c**: Unbinding or disassembly. The nearby model comment says: “Rule 23c”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23c**: Unbinding or disassembly. The nearby model comment says: “Rule 23c”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23d**: Unbinding or disassembly. The nearby model comment says: “Rule 23d”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 23d**: Unbinding or disassembly. The nearby model comment says: “Rule 23d”. The rule involves `CD28`, `LCK`, `Lig2`, `PTPN6`, `TCR` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. 
- **Rule 24a**: Reversible binding/release. The nearby model comment says: “Rule 24a”. The rule involves `LCK`, `PTPN6` and produces `LCK`, `PTPN6`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfLckPtp, krLckPtp`.
- **Rule 24b**: Reversible binding/release. The nearby model comment says: “Rule 24b”. The rule involves `LCK`, `PTPN6` and produces `LCK`, `PTPN6`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfLckPtp2, krLckPtp2`.
- **Rule 25**: Reversible binding/release. The nearby model comment says: “Rule 25”. The rule involves `CSK`, `PAG1` and produces `CSK`, `PAG1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfPagCsk, krPagCsk`.
- **Rule 26**: Reversible binding/release. The nearby model comment says: “Rule 26”. The rule involves `LCK`, `PAG1` and produces `LCK`, `PAG1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kfPagLck, krPagLck`.
- **Rule 27**: State change or catalytic conversion. The nearby model comment says: “Rule 27”. The rule involves `LCK`, `PAG1` and produces `LCK`, `PAG1`. The encoded molecular change is `PAG1` site `Y317` changes from `0` to `P`; site `Y317` changes from `0` to `P`. Rate parameter(s): `kpLckPag`.
- Additional rules are present after these 60 entries; they are mostly continuations of the same rule families above and should be read in the BNGL file for exhaustive curation.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `TCR_pY149_D` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y149_D~P!?)`.
- `TCR_pY171_G` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y171_G~P!?)`.
- `TCR_pY111` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y111~P!?)`.
- `TCR_pY123` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y123~P!?)`.
- `TCR_pY188_E` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y188_E~P!?)`.
- `TCR_pY199_E` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `TCR(Y199_E~P!?)`.
- `ZAP70_pY493` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `ZAP70(Y493~P!?)`.
- `LCK_pY424` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `LCK(Y424~P!?)`.
- `LCK_pY192` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `LCK(Y192~P!?)`.
- `ITK_pY512` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `ITK(Y512~P!?)`.
- `PTPN6_pY566` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `PTPN6(Y566~P!?)`.
- `WAS_pY291` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `WAS(Y291~P!?)`.
- `PAG1_pY163` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `PAG1(Y163~P!?)`.
- `DOK2_pY299` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `DOK2(Y299~P!?)`.
- `DOK1_pY449` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `DOK1(Y449~P!?)`.
- `PLCG1_pY783` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `PLCG1(Y783~P!?)`.
- `LAT_pY191` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `LAT(Y191~P!?)`.
- `LCK_pY505` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `LCK(Y505~P!?)`.
- `NCK_TCR` (Molecules) tracks bound complexes. Pattern: `TCR(PRS_E!1).NCK(SH3_1!1)`.
- `NCK_LCP2` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `LCP2(Y113_Y128~P!3).NCK(SH2!3)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `ChylekTCR_2014`
- Title/name: `Chylek 2014 (TCR)`
- Category: `immunology`
- Tags: `['published', 'immunology', 'chylektcr', '2014', 'lig1', 'lig2', 'lig3', 'tcr', 'cd28', 'lck', 'itk', 'zap70']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/immune-signaling/ChylekTCR_2014.bngl`
- Local BNGL file used: `Published/ChylekTCR2014/ChylekTCR_2014.bngl`
- Local YAML file used: `Published/ChylekTCR2014/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `true`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
