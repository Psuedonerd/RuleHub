# Model Explanation: Barua 2012

## 1. One-sentence summary

This model represents bcr signaling using BNGL rules for the molecules and interactions encoded in `BaruaBCR_2012.bngl`.

## 2. Biological meaning

The metadata describes this model as **BCR signaling** and places it in the `immunology` category. Tags provided by the repository are: `published`, `immunology`, `baruabcr`, `2012`, `bcr`, `lyn`, `fyn`, `csk`, `pag`, `syk`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `BCR(Y188_Y199~0~P~PP,Y196_Y207~0~P~PP)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Lyn(unique,SH3,SH2,Y397~0~P,Y508~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Fyn(unique,SH3,SH2,Y420~0~P,Y531~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Csk(SH2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PAG(PRS1,PRS2,Y317~0~P,Y163_Y181~0~P,Y387_Y417~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Syk(tSH2,Y525_Y526~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `BCR(Y188_Y199~0,Y196_Y207~0) BT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lyn(unique,SH3,SH2,Y397~0,Y508~0) LT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Fyn(unique,SH3,SH2,Y420~0,Y531~0) FT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PAG(PRS1,PRS2,Y317~0,Y163_Y181~0,Y387_Y417~0) PT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Csk(SH2) CT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Syk(tSH2,Y525_Y526~0) ST`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

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

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>'1',TextReaction=>'1'})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~0) + Lyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~0!1).Lyn(unique!1,SH3,SH2) kf1, kr1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~P) + Lyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~P!1).Lyn(unique,SH3,SH2!1) kf2a, kr2a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~PP) + Lyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~PP!1).Lyn(unique,SH3,SH2!1) kf2b, kr2b`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Lyn(unique,SH3,SH2,Y508~P)` is converted to `Lyn(unique,SH3,SH2!1,Y508~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf3,  kr3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR() + BCR(Y188_Y199~0)` is converted to `Lyn(Y397~0).BCR() + BCR(Y188_Y199~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp4a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR() + BCR(Y188_Y199~P)` is converted to `Lyn(Y397~0).BCR() + BCR(Y188_Y199~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp4b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR() + BCR(Y188_Y199~0)` is converted to `Lyn(Y397~P).BCR() + BCR(Y188_Y199~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp4c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR() + BCR(Y188_Y199~P)` is converted to `Lyn(Y397~P).BCR() + BCR(Y188_Y199~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp4d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR()+BCR(Y196_Y207~0)` is converted to `Lyn(Y397~0).BCR()+BCR(Y196_Y207~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp5a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR()+BCR(Y196_Y207~P)` is converted to `Lyn(Y397~0).BCR()+BCR(Y196_Y207~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp5b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR()+BCR(Y196_Y207~0)` is converted to `Lyn(Y397~P).BCR()+BCR(Y196_Y207~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp5c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR()+BCR(Y196_Y207~P)` is converted to `Lyn(Y397~P).BCR()+BCR(Y196_Y207~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp5d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR() + BCR().Lyn(Y397~0)` is converted to `Lyn(Y397~0).BCR() + BCR().Lyn(Y397~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp6a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR() + BCR().Lyn(Y397~0)` is converted to `Lyn(Y397~P).BCR() + BCR().Lyn(Y397~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp6b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp6c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp6d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~0).BCR() + BCR().Fyn(Y420~0)` is converted to `Lyn(Y397~0).BCR() + BCR().Fyn(Y420~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp7a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P).BCR() + BCR().Fyn(Y420~0)` is converted to `Lyn(Y397~P).BCR() + BCR().Fyn(Y420~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp7b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp7c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp7d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(Y397~P,Y508).PAG(Y387_Y417~0)` is converted to `Lyn(Y397~P,Y508).PAG(Y387_Y417~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp8a`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1,Y397~P,Y508).PAG(Y163_Y181~0,Y387_Y417~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1,Y397~P,Y508).PAG(Y163_Y181~P,Y387_Y417~P!1) kp8b`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(SH2!1,Y397~P,Y508).PAG(Y317~0,Y387_Y417~P!1)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(SH2!1,Y397~P,Y508).PAG(Y317~P,Y387_Y417~P!1) kp8c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~0) + Fyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~0!1).Fyn(unique!1,SH3,SH2) kf9, kr9`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~P) + Fyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~P!1).Fyn(unique,SH3,SH2!1) kf10a, kr10a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `BCR(Y188_Y199~PP) + Fyn(unique,SH3,SH2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `BCR(Y188_Y199~PP!1).Fyn(unique,SH3,SH2!1) kf10b, kr10b`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Fyn(unique,SH3,SH2,Y531~P)` is converted to `Fyn(unique,SH3,SH2!1,Y531~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf11,  kr11`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR(Y196_Y207~0)` is converted to `Fyn(Y420~0).BCR() + BCR(Y196_Y207~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp12a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR(Y196_Y207~P)` is converted to `Fyn(Y420~0).BCR() + BCR(Y196_Y207~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp12b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR(Y196_Y207~0)` is converted to `Fyn(Y420~P).BCR() + BCR(Y196_Y207~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp12c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR(Y196_Y207~P)` is converted to `Fyn(Y420~P).BCR() + BCR(Y196_Y207~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp12d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR(Y188_Y199~0)` is converted to `Fyn(Y420~0).BCR() + BCR(Y188_Y199~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp13a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR(Y188_Y199~P)` is converted to `Fyn(Y420~0).BCR() + BCR(Y188_Y199~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp13b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR(Y188_Y199~0)` is converted to `Fyn(Y420~P).BCR() + BCR(Y188_Y199~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2*kp13c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR(Y188_Y199~P)` is converted to `Fyn(Y420~P).BCR() + BCR(Y188_Y199~PP)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp13d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR().Fyn(Y420~0)` is converted to `Fyn(Y420~0).BCR() + BCR().Fyn(Y420~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp14a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR().Fyn(Y420~0)` is converted to `Fyn(Y420~P).BCR() + BCR().Fyn(Y420~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp14b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp14c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp14d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~0).BCR() + BCR().Lyn(Y397~0)` is converted to `Fyn(Y420~0).BCR() + BCR().Lyn(Y397~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp15a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P).BCR() + BCR().Lyn(Y397~0)` is converted to `Fyn(Y420~P).BCR() + BCR().Lyn(Y397~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp15b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp15c`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp15d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y387_Y417~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y387_Y417~P) kp16a`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Fyn(Y420~P,Y531).PAG(Y163_Y181~0)` is converted to `Fyn(Y420~P,Y531).PAG(Y163_Y181~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp16b`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y317~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y317~P) kp16c`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Syk(tSH2) + BCR(Y196_Y207~PP)` is converted to `Syk(tSH2!1).BCR(Y196_Y207~PP!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf17,  kr17`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Syk(tSH2!+,Y525_Y526~0) + Syk(tSH2!+,Y525_Y526~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Syk(tSH2!+,Y525_Y526~0) + Syk(tSH2!+,Y525_Y526~P) kp18a`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Syk(tSH2!+,Y525_Y526~P) + Syk(tSH2!+,Y525_Y526~0)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Syk(tSH2!+,Y525_Y526~P) + Syk(tSH2!+,Y525_Y526~P) kp18b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417) kf19a`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417) kr19a`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(unique,SH3,SH2!2).PAG(PRS2,Y387_Y417~P!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2) kf19b`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417~P)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3,SH2!2).PAG(PRS2,Y387_Y417~P!2) kf20a`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417~P)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2) kf20b`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2)` is converted to `\`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules Activated_Syk Syk(Y525_Y526~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Ig_alpha_P BCR(Y188_Y199~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Ig_alpha_PP BCR(Y188_Y199~PP)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Ig_beta_PP BCR(Y196_Y207~PP)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Activated_Lyn Lyn(Y397~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Autoinhibited_Lyn Lyn(Y508~P!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Activated_Fyn Fyn(Y420~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Autoinhibited_Fyn Fyn(Y531~P!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules PAG1_Csk PAG(Y317~P!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `BaruaBCR_2012`
- Title/name: `Barua 2012`
- Category: `immunology`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/immune-signaling/BaruaBCR_2012.bngl`
- BNGL file used locally: `Published/BaruaBCR2012/BaruaBCR_2012.bngl`
- YAML file used locally: `Published/BaruaBCR2012/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- Only the first 80 parsed reaction-rule lines are expanded individually here; the BNGL file should be consulted for any additional repetitive rules.
- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
