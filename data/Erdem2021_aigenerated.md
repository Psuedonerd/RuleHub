# Model Explanation: Erdem 2021

## 1. One-sentence summary

This model represents insr/igf1r signaling using BNGL rules for the molecules and interactions encoded in `Erdem_2021.bngl`.

## 2. Biological meaning

The metadata describes this model as **InsR/IGF1R signaling** and places it in the `signaling` category. Tags provided by the repository are: `published`, `erdem`, `2021`, `igf1`, `ins`, `igf1r`, `insr`, `irs`, `sos`, `ras`, `raf`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `IGF1(rec)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Ins(rec)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IGF1R(lig,phos~U~P,int~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `InsR(lig,phos~U~P,int~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IRS(phos~U~P,inh~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `SOS(act~N~Y,inh~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Ras(gtp~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Raf(phos~U~P,inh~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `MEK(phos~U~P,inh~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PI3K(act~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PDK1(act~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `TSC2(phos~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `mTOR(act~N~Y)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Akt(phos~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `RPS6K(phos~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `ERK(phos~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `IGF1(rec) IGF1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Ins(rec) INS_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `IGF1R(lig,phos~U,int~N) IGF1R_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `InsR(lig,phos~U,int~N) INSR_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `IRS(phos~U,inh~N) IRS_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `SOS(act~N,inh~N) SOS_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Ras(gtp~N) RAS_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Raf(phos~U,inh~N) RAF_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `MEK(phos~U,inh~N) MEK_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PI3K(act~N) PI3K_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PDK1(act~N) PDK1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `TSC2(phos~U) TSC2_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `mTOR(act~N) MTOR_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Akt(phos~U) AKT_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `RPS6K(phos~U) RPS6K_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `ERK(phos~U) ERK_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `IGF1_0 1e5`
- `INS_0 0`
- `IGF1R_0 25000.0`
- `INSR_0 25000.0`
- `IRS_0 92766.0`
- `SOS_0 90075.0`
- `RAS_0 230642.0`
- `RAF_0 126069.0`
- `MEK_0 1098164.0`
- `ERK_0 763172.0`
- `PI3K_0 64009.0`
- `PDK1_0 186081.0`
- `AKT_0 432907.0`
- `TSC2_0 131339.0`
- `MTOR_0 83469.0`
- `RPS6K_0 121978.0`
- `kf1		0.4837`
- `kf1b	-2.9153`
- `kf1c	2.9865`
- `kf1d	1.2052`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `writeLatex()`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `IGF1(rec) + IGF1R(lig,int~N,phos~U)` is converted to `IGF1(rec!1).IGF1R(lig!1,int~N,phos~U)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf1, 10^kf1b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IGF1R(lig!+,int~N,phos~U)` is converted to `IGF1R(lig!+,int~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf1c`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `IGF1R(lig!+,int~N,phos~P)` is converted to `IGF1R(lig,int~N,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf1d`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Ins(rec) + InsR(lig,int~N,phos~U)` is converted to `Ins(rec!1).InsR(lig!1,int~N,phos~U)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf2, 10^kf2b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `InsR(lig!+,int~N,phos~U)` is converted to `InsR(lig!+,int~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf2c`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `InsR(lig!+,int~N,phos~P)` is converted to `InsR(lig,int~N,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf2d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IGF1R(int~N,phos~P) + IRS(inh~N,phos~U)` is converted to `IGF1R(int~N,phos~P) + IRS(inh~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `InsR(int~N,phos~P) + IRS(inh~N,phos~U)` is converted to `InsR(int~N,phos~P) + IRS(inh~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf4`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IGF1R(int~N,phos~P) + SOS(inh~N,act~N)` is converted to `IGF1R(int~N,phos~P) + SOS(inh~N,act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf5`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `InsR(int~N,phos~P) + SOS(inh~N,act~N)` is converted to `InsR(int~N,phos~P) + SOS(inh~N,act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf6`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IRS(inh~N,phos~P) + SOS(inh~N,act~N)` is converted to `IRS(inh~N,phos~P) + SOS(inh~N,act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf7`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `SOS(inh~N,act~Y) + Ras(gtp~N)` is converted to `SOS(inh~N,act~Y) + Ras(gtp~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf8`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Ras(gtp~Y) + Raf(inh~N,phos~U)` is converted to `Ras(gtp~Y) + Raf(inh~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf9`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Raf(inh~N,phos~P) + MEK(inh~N,phos~U)` is converted to `Raf(inh~N,phos~P) + MEK(inh~N,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf10`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `MEK(inh~N,phos~P) + ERK(phos~U)` is converted to `MEK(inh~N,phos~P) + ERK(phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf11`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IRS(inh~N,phos~P) + PI3K(act~N)` is converted to `IRS(inh~N,phos~P) + PI3K(act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf12`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PI3K(act~Y) + PDK1(act~N)` is converted to `PI3K(act~Y) + PDK1(act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf13`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PDK1(act~Y) + Akt(phos~U)` is converted to `PDK1(act~Y) + Akt(phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf14`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Akt(phos~P) + TSC2(phos~U)` is converted to `Akt(phos~P) + TSC2(phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf15`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `TSC2(phos~P) + mTOR(act~N)` is converted to `TSC2(phos~P) + mTOR(act~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf16`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `mTOR(act~Y) + RPS6K(phos~U)` is converted to `mTOR(act~Y) + RPS6K(phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf17`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IRS(phos~P)` is converted to `IRS(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf101`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `SOS(act~Y)` is converted to `SOS(act~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf102`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Ras(gtp~Y)` is converted to `Ras(gtp~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf103`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Raf(phos~P)` is converted to `Raf(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf104`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `MEK(phos~P)` is converted to `MEK(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf105`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PI3K(act~Y)` is converted to `PI3K(act~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf106`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PDK1(act~Y)` is converted to `PDK1(act~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf107`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `TSC2(phos~P)` is converted to `TSC2(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf108`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `mTOR(act~Y)` is converted to `mTOR(act~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf109`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Akt(phos~P)` is converted to `Akt(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf110`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `RPS6K(phos~P)` is converted to `RPS6K(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf111`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `ERK(phos~P)` is converted to `ERK(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf112`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `ERK(phos~P) + SOS(inh~N,act~N)` is converted to `ERK(phos~P) + SOS(inh~Y,act~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf201`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `ERK(phos~P) + MEK(inh~N,phos~U)` is converted to `ERK(phos~P) + MEK(inh~Y,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf202`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `RPS6K(phos~P) + IRS(inh~N,phos~U)` is converted to `RPS6K(phos~P) + IRS(inh~Y,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf203`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Akt(phos~P) + Raf(inh~N,phos~U)` is converted to `Akt(phos~P) + Raf(inh~Y,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf204`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `ERK(phos~P) + IRS(inh~N,phos~U)` is converted to `ERK(phos~P) + IRS(inh~Y,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf206`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `ERK(phos~P) + Akt(phos~P)` is converted to `ERK(phos~P) + Akt(phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf207`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Akt(phos~P) + IRS(inh~N,phos~U)` is converted to `Akt(phos~P) + IRS(inh~Y,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf208`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IRS(inh~Y)` is converted to `IRS(inh~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf301`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `SOS(inh~Y)` is converted to `SOS(inh~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf302`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Raf(inh~Y)` is converted to `Raf(inh~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf303`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `MEK(inh~Y)` is converted to `MEK(inh~N)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf304`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IGF1R(lig!+,int~N,phos~P)` is converted to `IGF1R(lig!+,int~Y,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf401`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `IGF1(rec!1).IGF1R(lig!1,int~Y,phos~P)` is converted to `IGF1R(lig,int~N,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf402`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `InsR(lig!+,int~N,phos~P)` is converted to `InsR(lig!+,int~Y,phos~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf403`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Ins(rec!1).InsR(lig!1,int~Y,phos~P)` is converted to `InsR(lig,int~N,phos~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10^kf404`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Species		pRecTot_free		IGF1R(int~N,phos~P),InsR(int~N,phos~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species		pAkt308_free		Akt(phos~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species		pRPS6K_free			RPS6K(phos~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species		pERK_free			ERK(phos~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Erdem_2021`
- Title/name: `Erdem 2021`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Erdem_2021.bngl`
- BNGL file used locally: `Published/Erdem2021/Erdem_2021.bngl`
- YAML file used locally: `Published/Erdem2021/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
