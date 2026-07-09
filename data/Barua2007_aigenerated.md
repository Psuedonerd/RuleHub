# Model Explanation: Barua 2007

## 1. One-sentence summary

This model represents model from haugh (2006) using BNGL rules for the molecules and interactions encoded in `Barua_2007.bngl`.

## 2. Biological meaning

The metadata describes this model as **Model from Haugh (2006)** and places it in the `signaling` category. Tags provided by the repository are: `published`, `barua`, `2007`, `version`, `r`, `s`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `R(DD,Y1~U~P,Y2~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `S(NSH2~C~O,CSH2,PTP~C~O)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `S(NSH2~C,CSH2,PTP~C)				S_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R(DD!1,Y1~U,Y2~P).R(DD!1,Y1~U,Y2~P)             R_dim`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `kdim            1000`
- `kopen           10`
- `kclose          500`
- `kon_CSH2        1`
- `koff_CSH2       1`
- `kon_NSH2        1`
- `koff_NSH2       1`
- `kkin_Y1         0.1`
- `kon_PTP         1`
- `koff_PTP        10`
- `kcat_PTP        1`
- `chi_r1          1000`
- `chi_r2          100`
- `chi_r3          1000`
- `chi_r4          1000`
- `chi_r5          100`
- `chi_r6          100`
- `chi_r7          100`
- `chi_r8          1000`
- `chi_r9          100`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>1000,n_steps=>100,steady_state=>1,atol=>1e-10,rtol=>1e-8,sparse=>0});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `R(DD!+,Y1~U)` is converted to `R(DD!+,Y1~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kkin_Y1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S(NSH2~C,PTP~C)` is converted to `S(NSH2~O,PTP~O)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kopen, kclose`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R(Y2~P) + S(CSH2)` is converted to `R(Y2~P!1).S(CSH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_CSH2, koff_CSH2 \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `exclude_reactants(2,R)`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R(Y2~P) + S(NSH2~O)` is converted to `R(Y2~P!1).S(NSH2~O!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_NSH2, koff_NSH2 \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `exclude_reactants(2,R)`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R(Y1~P) + S(PTP~O)` is converted to `R(Y1~P!1).S(PTP~O!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_PTP, koff_PTP \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `exclude_reactants(2,R)`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1).S(PTP~O!1)` is converted to `R(Y1~U) + S(PTP~O)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kcat_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1).S(PTP~O!1)` is converted to `R(Y1~U).S(PTP~O)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kcat_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y2~P).S(NSH2~O,CSH2!+,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y2~P!1).S(NSH2~O!1,CSH2!+,PTP~O)  chi_r1*kon_NSH2,koff_NSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P,Y2~P!1).S(NSH2~O,CSH2!1,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!2,Y2~P!1).S(NSH2~O,CSH2!1,PTP~O!2)  chi_r2*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P).R(Y2~P!1).S(NSH2~O,CSH2!1,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!2).R(Y2~P!1).S(NSH2~O,CSH2!1,PTP~O!2)  chi_r3*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y2~P).S(NSH2~O!+,CSH2,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y2~P!1).S(NSH2~O!+,CSH2!1,PTP~O)  chi_r1*kon_CSH2,koff_CSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P).R(Y2~P!1).S(NSH2~O!1,CSH2,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!2).R(Y2~P!1).S(NSH2~O!1,CSH2,PTP~O!2)  chi_r4*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P,Y2~P!1).S(NSH2~O!1,CSH2,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!2,Y2~P!1).S(NSH2~O!1,CSH2,PTP~O!2)  chi_r5*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1,Y2~P).S(NSH2~O,CSH2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1,Y2~P!2).S(NSH2~O,CSH2!2,PTP~O!1)  chi_r2*kon_CSH2,koff_CSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1).R(Y2~P).S(NSH2~O,CSH2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1).R(Y2~P!2).S(NSH2~O,CSH2!2,PTP~O!1)  chi_r3*kon_CSH2,koff_CSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1).R(Y2~P).S(NSH2~O,CSH2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2,PTP~O!1)  chi_r4*kon_NSH2,koff_NSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1,Y2~P).S(NSH2~O,CSH2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1,Y2~P!2).S(NSH2~O!2,CSH2,PTP~O!1)  chi_r5*kon_NSH2,koff_NSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P,Y2~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2!1,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!3,Y2~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2!1,PTP~O!3) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r6*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P,Y2~P!1).R(Y2~P!2).S(NSH2~O!1,CSH2!2,PTP~O)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!3,Y2~P!1).R(Y2~P!2).S(NSH2~O!1,CSH2!2,PTP~O!3) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r7*kon_PTP,koff_PTP`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1,Y2~P!2).R(Y2~P).S(NSH2~O,CSH2!2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1,Y2~P!2).R(Y2~P!3).S(NSH2~O!3,CSH2!2,PTP~O!1) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r8*kon_NSH2,koff_NSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y2~P!1).R(Y1~P!2,Y2~P).S(NSH2~O,CSH2!1,PTP~O!2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y2~P!1).R(Y1~P!2,Y2~P!3).S(NSH2~O!3,CSH2!1,PTP~O!2) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r9*kon_NSH2,koff_NSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y2~P!1).R(Y1~P!2,Y2~P).S(NSH2~O!1,CSH2,PTP~O!2)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y2~P!1).R(Y1~P!2,Y2~P!3).S(NSH2~O!1,CSH2!3,PTP~O!2) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r10*kon_CSH2,koff_CSH2`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `R(Y1~P!1,Y2~P!2).R(Y2~P).S(NSH2~O!2,CSH2,PTP~O!1)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `R(Y1~P!1,Y2~P!2).R(Y2~P!3).S(NSH2~O!2,CSH2!3,PTP~O!1) \`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `chi_r11*kon_CSH2,koff_CSH2`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  pYR      R(Y1~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Barua_2007`
- Title/name: `Barua 2007`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Barua_2007.bngl`
- BNGL file used locally: `Published/Barua2007/Barua_2007.bngl`
- YAML file used locally: `Published/Barua2007/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
