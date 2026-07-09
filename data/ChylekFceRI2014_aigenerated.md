# Model Explanation: Chylek 2014 (FceRI)

## 1. One-sentence summary

This model represents fceri signaling using BNGL rules for the molecules and interactions encoded in `ChylekFceRI_2014.bngl`.

## 2. Biological meaning

The metadata describes this model as **FceRI signaling** and places it in the `immunology` category. Tags provided by the repository are: `published`, `immunology`, `chylekfceri`, `2014`, `lig`, `rec`, `lyn`, `fyn`, `syk`, `pag1`, `csk`, `lat`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `Lig(hap~b~e,hap~b~e)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Rec(fab,fab,b_Y218~0~P,b_Y224~0~P,g_Y65_Y76~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Lyn(U,SH3,SH2,Y397~0~P,Y508~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Fyn(U,SH3,SH2,PTK,Y420~0~P,Y531~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Syk(tSH2,Y346~0~P,PTK,Y519_Y520~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Pag1(PRS1,Y165_Y183~0~P,PRS2,Y317~0~P,Y386_Y409~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Csk(SH2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Lat(Y136~0~P,Y175~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Plcg1(SH2,SH3,PLC,Y783~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Grb2(SH2,cSH3)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Gab2(PRS,Y441~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Grap2(SH2,SH3)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Lcp2(RxxK,PRS)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Pi3k(p85_SH2,PI3Kc)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Btk(PH,PTK)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Inpp5d(SH2,IPP,C2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PI34P2(bind)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PI45P2(bind)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PI345P3(bind)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IP3()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `DAG()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Sink()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PI4P()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `Lig(hap~b,hap~b) SimLigTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Rec(fab,fab,b_Y218~0,b_Y224~0,g_Y65_Y76~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lyn(U,SH2,SH3,Y397~0,Y508~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Fyn(U,SH2,SH3,Y420~0,PTK,Y531~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Syk(tSH2,Y346~0,PTK,Y519_Y520~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Pag1(PRS1,PRS2,Y317~0,Y165_Y183~0,Y386_Y409~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Csk(SH2) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lat(Y136~0,Y175~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Plcg1(SH2,SH3,PLC,Y783~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Grb2(SH2,cSH3) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Gab2(PRS,Y441~0) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PI45P2(bind) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Pi3k(PI3Kc,p85_SH2) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Btk(PH,PTK) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Inpp5d(SH2,C2,IPP) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Grap2(SH2,SH3) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lcp2(RxxK,PRS) SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PI4P()	       SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Sink()	       SimProteinTot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

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

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `writeXML();`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(hap~b)` is converted to `Lig(hap~e)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `lambda_p, lambda_m`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Lig(hap~e,hap~e) + Rec(fab)` is converted to `Lig(hap~e,hap~e!1).Rec(fab!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kfl`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Lig(hap~b,hap~e) + Rec(fab)` is converted to `Lig(hap~b,hap~e!1).Rec(fab!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kfl`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lig(hap~e,hap~e!1).Rec(fab!1) + Rec(fab)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lig(hap~e!2,hap~e!1).Rec(fab!1).Rec(fab!2) kxl`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lig(hap~e!1).Rec(fab!1)` is converted to `Lig(hap~e) + Rec(fab)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `krl`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Rec(b_Y218~0) + Lyn(U,SH3,SH2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~0!1).Lyn(U!1,SH3,SH2) kfRecLyn1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Rec(b_Y218~0!1).Lyn(U!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~0) + Lyn(U) krRecLyn1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Rec(b_Y218~P) + Lyn(U,SH3,SH2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~P!1).Lyn(U,SH3,SH2!1) kfRecLyn2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Rec(b_Y218~P!1).Lyn(SH2!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~P) + Lyn(SH2) krRecLyn2`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(U,SH3,SH2,Y508~P)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U,SH3,SH2!1,Y508~P!1) kfLynIn`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1,Y508~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2,Y508~P) krLynIn`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y218~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y218~P) kpLynB1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y218~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y218~P) kpLynB2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y224~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y224~P) kpLynB1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y224~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,b_Y224~P) kpLynB2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U!1).Rec(b_Y218~0!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P) kpLynG1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1).Rec(b_Y218~P!1,fab!2).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P) kpLynG2`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Syk(tSH2) + Rec(g_Y65_Y76~P)` is converted to `Syk(tSH2!1).Rec(g_Y65_Y76~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kfRecSyk, krRecSyk`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U!1).Rec(fab!2,b_Y218~0!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y346~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U!1).Rec(fab!2,b_Y218~0!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y346~P)  kpLynSyk1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1).Rec(fab!2,b_Y218~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y346~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1).Rec(fab!2,b_Y218~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y346~P)  kpLynSyk2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Syk(tSH2!1,Y519_Y520~0).Rec(fab!2,g_Y65_Y76~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y519_Y520~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Syk(tSH2!1,Y519_Y520~0).Rec(fab!2,g_Y65_Y76~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y519_Y520~P) kpSykSyk0`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Syk(tSH2!1,Y519_Y520~P).Rec(fab!2,g_Y65_Y76~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y519_Y520~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Syk(tSH2!1,Y519_Y520~P).Rec(fab!2,g_Y65_Y76~P!1).Lig(hap~e!2,hap~e!3).Rec(fab!3,g_Y65_Y76~P!4).Syk(tSH2!4,Y519_Y520~P) kpSykSykP`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(U,SH3,SH2) + Pag1(PRS2,Y386_Y409)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U,SH3!1,SH2).Pag1(PRS2!1,Y386_Y409) kfPagLynSH3`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U,SH3,SH2!2).Pag1(PRS2,Y386_Y409~P!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U,SH3!1,SH2!2).Pag1(PRS2!1,Y386_Y409~P!2) kfPagLynSH3_2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2).Pag1(PRS2!1,Y386_Y409)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3,SH2) + Pag1(PRS2,Y386_Y409)  krPagLynSH3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(U,SH3,SH2) + Pag1(PRS2,Y386_Y409~P)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U,SH3,SH2!2).Pag1(PRS2,Y386_Y409~P!2) kfPagLynSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(U,SH3!1,SH2).Pag1(PRS2!1,Y386_Y409~P)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(U,SH3!1,SH2!2).Pag1(PRS2!1,Y386_Y409~P!2) kfPagLynSH2_2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2!2).Pag1(PRS2!1,Y386_Y409~P!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3,SH2) + Pag1(PRS2,Y386_Y409~P)  krPagLyn2point`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,Y508).Pag1(PRS2!1,Y386_Y409~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!1,Y508).Pag1(PRS2!1,Y386_Y409~P) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3,SH2!1,Y508).Pag1(Y165_Y183~0,Y386_Y409~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3,SH2!1,Y508).Pag1(Y165_Y183~P,Y386_Y409~P!1) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!2,SH2!1,Y508).Pag1(PRS2!2,Y165_Y183~0,Y386_Y409~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!2,SH2!1,Y508).Pag1(PRS2!2,Y165_Y183~P,Y386_Y409~P!1) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2,Y508).Pag1(PRS2!1,Y165_Y183~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!1,SH2,Y508).Pag1(PRS2!1,Y165_Y183~P) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1,Y508).Pag1(Y317~0,Y386_Y409~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1,Y508).Pag1(Y317~P,Y386_Y409~P!1) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3,SH2!1,Y508).Pag1(Y317~0,Y386_Y409~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3,SH2!1,Y508).Pag1(Y317~P,Y386_Y409~P!1) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!2,SH2!1,Y508).Pag1(PRS2!2,Y317~0,Y386_Y409~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!2,SH2!1,Y508).Pag1(PRS2!2,Y317~P,Y386_Y409~P!1) kpLynPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2,Y508).Pag1(PRS2!1,Y317~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!1,SH2,Y508).Pag1(PRS2!1,Y317~P) kpLynPag`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Csk(SH2) + Pag1(Y317~P)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Csk(SH2!3).Pag1(Y317~P!3) kfCskPag,krCskPag`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3,SH2!1,Y508~0).Pag1(Y386_Y409~P!1,Y317~P!2).Csk(SH2!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3,SH2!1,Y508~P).Pag1(Y386_Y409~P!1,Y317~P!2).Csk(SH2!2) kpCskLyn`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2,Y508~0).Pag1(PRS2!1,Y317~P!2).Csk(SH2!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!1,SH2,Y508~P).Pag1(PRS2!1,Y317~P!2).Csk(SH2!2) kpCskLyn`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH3!1,SH2!3,Y508~0).Pag1(PRS2!1,Y386_Y409~P!3,Y317~P!2).Csk(SH2!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH3!1,SH2!3,Y508~P).Pag1(PRS2!1,Y386_Y409~P!3,Y317~P!2).Csk(SH2!2) kpCskLyn`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Rec(b_Y218~0) + Fyn(U,SH3,SH2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~0!1).Fyn(U!1,SH3,SH2) kfRecFyn1`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Rec(b_Y218~0!1).Fyn(U!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Rec(b_Y218~0) + Fyn(U) krRecFyn1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Rec(b_Y218~P) + Fyn(U,SH3,SH2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules Lat_pY136 Lat(Y136~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Lat_pY175 Lat(Y175~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Rec_pY218 Rec(b_Y218~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Rec_pY224 Rec(b_Y224~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Rec_pY65_Y76 Rec(g_Y65_Y76~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Syk_pY346 Syk(Y346~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Gab2_pY441 Gab2(Y441~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules PI3K_recruited Lat(Y175~P!1).Grb2(SH2!1,cSH3!2).Gab2(PRS!2,Y441~P!3).Pi3k(p85_SH2!3)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules PI345P3	PI345P3(bind!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Plcg1_pY783	Plcg1(Y783~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules LynUbound Lyn(U!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules LynSH2bound	Lyn(SH2!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Shipbound Inpp5d(SH2!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Plc_pip2 Plcg1(PLC!1).PI45P2(bind!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Lat_Plc Lat(Y136~P!1).Plcg1(SH2!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules IP3	IP3()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules PI34P2	PI34P2(bind!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules PI45P2	PI45P2(bind!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Pag_Y165 Pag1(Y165_Y183~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Pag_Y409 Pag1(Y386_Y409~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules LynIn	  Lyn(SH2!1,Y508~P!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules FynIn Fyn(SH2!1,Y531~P!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Lyn_pY508 Lyn(Y508~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Fyn_pY508 Fyn(Y531~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Btk_recruited Btk(PH!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules LigFree  Lig(hap,hap)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Crosslinks Lig(hap~e!1,hap~e!2).Rec(fab!1).Rec(fab!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules DNP_exposed_0_of_2	   Lig(hap~b!?,hap~b!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  DNP_exposed_1_of_2	   Lig(hap~b!?,hap~e!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  DNP_exposed_2_of_2	   Lig(hap~e!?,hap~e!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules LigTotal Lig(hap!?,hap!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Syk_pY519_520 Syk(Y519_Y520~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `ChylekFceRI_2014`
- Title/name: `Chylek 2014 (FceRI)`
- Category: `immunology`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/immune-signaling/ChylekFceRI_2014.bngl`
- BNGL file used locally: `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl`
- YAML file used locally: `Published/ChylekFceRI2014/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `true`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- Only the first 80 parsed reaction-rule lines are expanded individually here; the BNGL file should be consulted for any additional repetitive rules.
- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
