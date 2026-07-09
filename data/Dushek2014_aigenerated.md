# Model Explanation: Dushek 2014

## 1. One-sentence summary

This model represents tcr signaling dynamics using BNGL rules for the molecules and interactions encoded in `Dushek_2014.bngl`.

## 2. Biological meaning

The metadata describes this model as **TCR signaling dynamics** and places it in the `signaling` category. Tags provided by the repository are: `published`, `dushek`, `2014`, `e`, `f`, `b`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `E(b)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `F(b)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `B(e~0~1,b,Y~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `E(b) 1`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `F(b) 1`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `B(e~0,b,Y~U) 100`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `Ekf 10`
- `Ekb 1`
- `Ekc 1`
- `Fkf 10`
- `Fkb 1`
- `Fkc 1`
- `kon1 1000`
- `koff1 1`
- `kon2 10`
- `koff2 1`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `writeMfile ({}) ;`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `E(b) + B(e~0,b,Y~U)` is converted to `E(b!1).B(e~1,b,Y~U!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf, Ekb`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `E(b!1).B(e~1,b,Y~U!1)` is converted to `E(b) + B(e~0,b,Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `F(b) + B(e~0,b,Y~P)` is converted to `F(b!1).B(e~1,b,Y~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf,  Fkb`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `F(b!1).B(e~1,b,Y~P!1)` is converted to `F(b) + B(e~0,b,Y~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `B(e~0,b,Y~P)` is converted to `B(e~0,b!1,Y~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon1, koff1`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `B(e~0,Y~P) + B(e~0,b)` is converted to `B(e~0,Y~P!1).B(e~0,b!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon2, koff2`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules W B(e~0,b,Y~P), B(e~0,b,Y~U), B(e~1,b)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules U B(e~0,b!1,Y~P!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V2 B==2`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V3 B==3`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V4 B==4`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V5 B==5`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V6 B==6`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V7 B==7`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V8 B==8`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V9 B==9`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V10 B==10`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V11 B==11`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V12 B==12`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V13 B==13`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V14 B==14`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species V15 B==15`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules E E(b!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Dushek_2014`
- Title/name: `Dushek 2014`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Dushek_2014.bngl`
- BNGL file used locally: `Published/Dushek2014/Dushek_2014.bngl`
- YAML file used locally: `Published/Dushek2014/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `true`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
