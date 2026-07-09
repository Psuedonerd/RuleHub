# Model Explanation: Blinov ran

## 1. One-sentence summary

This model represents ran gtpase cycle using BNGL rules for the molecules and interactions encoded in `Blinov_ran.bngl`.

## 2. Biological meaning

The metadata describes this model as **Ran GTPase cycle** and places it in the `regulation` category. Tags provided by the repository are: `published`, `nfsim`, `blinov`, `ran`, `c`, `rcc1`, `simulate_nf`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `Ran(cargo)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `C(site,Y1~u~p,Y2~u~p,Y3~u~p)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `RCC1(site)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `1 @nuc:Ran(cargo!1).C(site!1,Y1~u,Y2~u,Y3~u) 1000.0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `2 @nuc:RCC1(site) 1000.0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- No entries were found in this block.

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `simulate_nf({t_end=>10.0,n_steps=>200})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `Transport`: Biochemical transformation or interaction. In words, the reactant pattern `@nuc:Ran(cargo!+)` is converted to `@cyt:Ran(cargo!+) 2.0 *`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `602.0,  0.0`.
- `Ran_C_bind_cyt`: Unbinding or complex dissociation. In words, the reactant pattern `@cyt:Ran(cargo!1).C(site!1)` is converted to `@cyt:Ran(cargo) + @cyt:C(site)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1.0,  100.0`.
- `C_p1`: Biochemical transformation or interaction. In words, the reactant pattern `@cyt:C(Y3~u!?)` is converted to `@cyt:C(Y3~p!?)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10.0,  1.0`.
- `C_p2`: Biochemical transformation or interaction. In words, the reactant pattern `@cyt:C(Y2~u!?)` is converted to `@cyt:C(Y2~p!?)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10.0,  1.0`.
- `C_p3`: Biochemical transformation or interaction. In words, the reactant pattern `@cyt:C(Y1~u!?)` is converted to `@cyt:C(Y1~p!?)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10.0,  1.0`.
- `Ran_RCC1_bind`: Binding or complex formation. In words, the reactant pattern `@nuc:Ran(cargo) + @nuc:RCC1(site)` is converted to `@nuc:Ran(cargo!1).RCC1(site!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1.0,  100.0`.
- `Ran_C_bind_nuc`: Unbinding or complex dissociation. In words, the reactant pattern `@nuc:Ran(cargo!1).C(site!1)` is converted to `@nuc:Ran(cargo) + @nuc:C(site)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `1.0,  100.0`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules Ran_cyt @cyt:Ran()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Cargo_cyt @cyt:C()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules RCC1_nuc @nuc:RCC1()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Cargo_phosp_cyt_total @nuc:C(Y1~p!?) @nuc:C(Y2~p!?) @nuc:C(Y3~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Cargo_nuc @nuc:C()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Cargo_phosp_cyt @cyt:C(Y1~p!?,Y2~p!?,Y3~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Ran_bound_cyt @cyt:Ran(cargo!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_ran`
- Title/name: `Blinov ran`
- Category: `regulation`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/cell-regulation/Blinov_ran.bngl`
- BNGL file used locally: `Published/Blinovran/Blinov_ran.bngl`
- YAML file used locally: `Published/Blinovran/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `true`, simulation methods = `['nf']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
