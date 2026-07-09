# Model Explanation: Barua 2009

## 1. One-sentence summary

This model represents jak2-sh2b signaling using BNGL rules for the molecules and interactions encoded in `Barua_2009.bngl`.

## 2. Biological meaning

The metadata describes this model as **JAK2-SH2B signaling** and places it in the `signaling` category. Tags provided by the repository are: `published`, `barua`, `2009`, `s`, `j`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `S(SH2,DD)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `J(Y1~P,Y~U~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `S(SH2,DD)       Stot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `J(Y1~P,Y~U)     Jtot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `kon_dimer	1.0`
- `koff_dimer	0.1`
- `kon_SH2		1.0`
- `koff_SH2	0.1`
- `kphos_slow	0.1`
- `kphos_fast	1.0`
- `Jtot            0.000014`
- `Stot            0.1`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1, max_stoich=>{J=>2}});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>10000, n_steps=>10000,atoll=>1e-08,rtol=>1e-08,sparse=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `J(Y1~P) + S(SH2)` is converted to `J(Y1~P!1).S(SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_SH2,  koff_SH2`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(DD) + S(DD)` is converted to `S(DD!1).S(DD!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_dimer,  koff_dimer`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `J(Y~U,Y1!1).S(SH2!1,DD!2).S(DD!2,SH2!3).J(Y1!3,Y~U)` is converted to `J(Y~P,Y1!1).S(SH2!1,DD!2).S(DD!2,SH2!3).J(Y1!3,Y~U)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kphos_slow`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `J(Y~U,Y1!1).S(SH2!1,DD!2).S(DD!2,SH2!3).J(Y1!3,Y~P)` is converted to `J(Y~P,Y1!1).S(SH2!1,DD!2).S(DD!2,SH2!3).J(Y1!3,Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kphos_fast`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules 	J_mono    J(Y1~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules 	JS       J(Y1~P!1).S(SH2!1,DD)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules 	JSS    J(Y1~P!1).S(SH2!1,DD!2).S(SH2,DD!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules 	JSSJ      J.J`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules 	J_active    J(Y~P)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules 	J_inactive   J(Y~U)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2009`
- Title/name: `Barua 2009`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Barua_2009.bngl`
- BNGL file used locally: `Published/Barua2009/Barua_2009.bngl`
- YAML file used locally: `Published/Barua2009/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
