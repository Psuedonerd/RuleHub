# Model Explanation: Gardner 2000

## 1. One-sentence summary

This model represents genetic toggle switch using BNGL rules for the molecules and interactions encoded in `genetic_switch_gardner2000.bngl`.

## 2. Biological meaning

The metadata describes this model as **Genetic toggle switch** and places it in the `synthetic-biology` category. Tags provided by the repository are: `published`, `synthetic-biology`, `gardner`, `2000`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `R1()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R2()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `R1()  0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R2()  0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `alpha_1  156.25`
- `alpha_2  15.6`
- `beta     2.5`
- `gamma    1.0`
- `k_deg    1.0`

Additional functions or formulas parsed from the model:

- `syn_R1() = alpha_1 / (1 + Obs_Tot_R2^beta)`
- `syn_R2() = alpha_2 / (1 + Obs_Tot_R1^gamma)`

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `R1()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `syn_R1()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `R2()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `syn_R2()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `R1()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `k_deg`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `R2()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `k_deg`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  Obs_Tot_R1  R1()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Tot_R2  R2()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Gardner_2000`
- Title/name: `Gardner 2000`
- Category: `synthetic-biology`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Gardner2000/genetic_switch_gardner2000.bngl`
- YAML file used locally: `Published/Gardner2000/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
