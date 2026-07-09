# Model Explanation: Dreisigmeyer 2008

## 1. One-sentence summary

This model represents lac operon using BNGL rules for the molecules and interactions encoded in `lac_operon_dreisigmeyer2008.bngl`.

## 2. Biological meaning

The metadata describes this model as **Lac operon** and places it in the `gene-expression` category. Tags provided by the repository are: `published`, `gene-expression`, `dreisigmeyer`, `2008`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `A()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Z()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L()  0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `A()  0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Z()  c_basal`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `NA  6.02214076e23`
- `V_ref  1e-15`
- `f  1.0`
- `l_ext  1000.0`
- `growth_rate  0.0231`
- `alpha  600.0`
- `phi  0.5`
- `rho  0.1`
- `K_i  500.0`
- `beta  2.85e4`
- `nu  0.468`
- `K_m_l  2530.0`
- `delta  2.30e4`
- `K_m_a  1200.0`
- `eps  34.285`
- `c_basal  0.0343`
- `K_z  105.0`
- `n_Hill  2.0`

Additional functions or formulas parsed from the model:

- `transport_L() = alpha * Obs_Tot_Z \`
- `* (l_ext - phi * rho * Obs_Tot_L) \`
- `/ (K_i + l_ext + rho * Obs_Tot_L)`
- `metab_L() = (beta / K_m_l) * Obs_Tot_Z \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `prod_A() = nu * (beta / K_m_l) * Obs_Tot_Z * Obs_Tot_L \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `metab_A() = (delta / K_m_a) * Obs_Tot_Z \`
- `/ (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)`
- `syn_Z() = growth_rate * (c_basal \`
- `+ eps * Obs_Tot_A^n_Hill \`
- `/ (K_z^n_Hill + Obs_Tot_A^n_Hill))`

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `saveConcentrations()`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `L()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `transport_L()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `L()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `metab_L()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `L()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `growth_rate`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `A()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `prod_A()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `A()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `metab_A()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `A()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `growth_rate`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `Z()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `syn_Z()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `Z()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `growth_rate`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  Obs_Tot_L  L()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Tot_A  A()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Tot_Z  Z()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Dreisigmeyer_2008`
- Title/name: `Dreisigmeyer 2008`
- Category: `gene-expression`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- YAML file used locally: `Published/Dreisigmeyer2008/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
