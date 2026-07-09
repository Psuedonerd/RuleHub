# Model Explanation: Hlavacek2018Egg

## 1. One-sentence summary

This model represents end of permute change log using BNGL rules for the molecules and interactions encoded in `egg.bngl`.

## 2. Biological meaning

The metadata describes this model as **End of permute change log** and places it in the `other` category. Tags provided by the repository are: `a0__free`, `a1__free`, `a2__free`, `b1__free`, `b2__free`, `c0__free`, `c1__free`, `c2__free`, `d1__free`, `d2__free`, `a0`, `a1`, `a2`, `b1`, `b2`, `c0`, `c1`, `c2`, `d1`, `d2`, `period`, `t`, `species`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `t`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `t 0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `a0__FREE 9.99318747e+01`
- `a1__FREE 1.00606018e+00`
- `a2__FREE -7.52962956e-01`
- `b1__FREE -3.08973913e+01`
- `b2__FREE 1.26208508e+00`
- `c0__FREE 1.39738978e+02`
- `c1__FREE -3.91791542e+01`
- `c2__FREE -1.56811184e+00`
- `d1__FREE -1.21914775e+00`
- `d2__FREE 1.28080122e+00`
- `a0 a0__FREE`
- `a1 a1__FREE`
- `a2 a2__FREE`
- `b1 b1__FREE`
- `b2 b2__FREE`
- `c0 c0__FREE`
- `c1 c1__FREE`
- `c2 c2__FREE`
- `d1 d1__FREE`
- `d2 d2__FREE`

Additional functions or formulas parsed from the model:

- `X()=a0\`
- `+a1*cos(m*1*t)+b1*sin(m*1*t)\`
- `+a2*cos(m*2*t)+b2*sin(m*2*t)`
- `Y()=c0\`
- `+c1*cos(m*1*t)+d1*sin(m*1*t)\`
- `+c2*cos(m*2*t)+d2*sin(m*2*t)`

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `t`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Species t t`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek2018Egg_egg`
- Title/name: `Hlavacek2018Egg`
- Category: `other`
- Source origin: `published`
- Original repository: `missing`
- Original format: `missing`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Hlavacek2018Egg/egg.bngl`
- YAML file used locally: `Published/Hlavacek2018Egg/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
