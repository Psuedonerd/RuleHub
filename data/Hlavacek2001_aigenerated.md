# Model Explanation: Hlavacek 2001

## 1. One-sentence summary

This model represents kinetic proofreading using BNGL rules for the molecules and interactions encoded in `kinetic_proofreading_hlavacek2001.bngl`.

## 2. Biological meaning

The metadata describes this model as **Kinetic proofreading** and places it in the `physics` category. Tags provided by the repository are: `published`, `physics`, `hlavacek`, `2001`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L(r,r,mod~0~1~2~3~4~5)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R(l)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L(r,r,mod~0)  NL`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R(l)          NR`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `NA  6.02214076e23`
- `V_ref  1e-9`
- `NR  300000`
- `NL  602`
- `kon1  1.661e-8`
- `kon2  3.333e-6`
- `koff  0.1`
- `kp  0.4`

Additional functions or formulas parsed from the model:

- `alpha() = kp / (kp + 2 * koff)`
- `frac_dimers() = 2 * Obs_Tot_Dimers / NR`
- `frac_term() = Obs_D5 / (Obs_Tot_Dimers + 1e-30)`
- `frac_R_term() = 2 * Obs_D5 / NR`

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `saveConcentrations()`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r,r,mod~0) + R(l)` is converted to `L(r!1,r,mod~0).R(l!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r,mod~0) + R(l)` is converted to `L(r!+,r!1,mod~0).R(l!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~0).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~1).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~2).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~3).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~4).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1,mod~5).R(l!1)` is converted to `L(r,mod~0) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r!+,mod~0)` is converted to `L(r!+,r!+,mod~1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r!+,mod~1)` is converted to `L(r!+,r!+,mod~2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r!+,mod~2)` is converted to `L(r!+,r!+,mod~3)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r!+,mod~3)` is converted to `L(r!+,r!+,mod~4)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r!+,mod~4)` is converted to `L(r!+,r!+,mod~5)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Species    Obs_Free_L       L(r,r,mod~0)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_Free_R       R(l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_Singly_Bound L(r!+,r,mod~0)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_Tot_Dimers   L(r!+,r!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D0  L(r!+,r!+,mod~0)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D1  L(r!+,r!+,mod~1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D2  L(r!+,r!+,mod~2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D3  L(r!+,r!+,mod~3)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D4  L(r!+,r!+,mod~4)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_D5  L(r!+,r!+,mod~5)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek_2001`
- Title/name: `Hlavacek 2001`
- Category: `physics`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- YAML file used locally: `Published/Hlavacek2001/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
