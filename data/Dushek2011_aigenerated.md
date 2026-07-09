# Model Explanation: Dushek 2011

## 1. One-sentence summary

This model represents tcr signaling using BNGL rules for the molecules and interactions encoded in `Dushek_2011.bngl`.

## 2. Biological meaning

The metadata describes this model as **TCR signaling** and places it in the `signaling` category. Tags provided by the repository are: `published`, `dushek`, `2011`, `s`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `S(E~0~1,F~0~1,A~0~1,Y~U~P~2P~3P~4P~5P~6P~7P~8P~9P~10P~11P~12P~13P~14P~15P~16P~17P~18P~19P~20P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `S(E~0,F~0,A~0,Y~U) tS`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `A 0.0001`
- `tS 1`
- `Ekp 0.1`
- `Fkp 0.1`
- `Ekm 0.1/A`
- `Fkm 0.1/A`
- `Ekf1 20 * 10/A`
- `Ekf2 19 * 10/A`
- `Ekf3 18 * 10/A`
- `Ekf4 17 * 10/A`
- `Ekf5 16 * 10/A`
- `Ekf6 15 * 10/A`
- `Ekf7 14 * 10/A`
- `Ekf8 13 * 10/A`
- `Ekf9 12 * 10/A`
- `Ekf10 11 * 10/A`
- `Ekf11 10 * 10/A`
- `Ekf12 9 * 10/A`
- `Ekf13 8 * 10/A`
- `Ekf14 7 * 10/A`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>500000,n_steps=>30,sparse=>1,steady_state=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S(E~0,F~0,A~0)` is converted to `S(E~1,F~0,A~0)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekp, Ekm`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S(E~0,F~0,A~0)` is converted to `S(E~0,F~1,A~0)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkp, Fkm`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S(E~1,F~0,A~1)` is converted to `S(E~0,F~0,A~0)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekm`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S(E~0,F~1,A~1)` is converted to `S(E~0,F~0,A~0)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkm`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~U)` is converted to `S(E~1!1,A~0,Y~U!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf1, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~P)` is converted to `S(E~1!1,A~0,Y~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf2, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~2P)` is converted to `S(E~1!1,A~0,Y~2P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf3, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~3P)` is converted to `S(E~1!1,A~0,Y~3P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf4, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~4P)` is converted to `S(E~1!1,A~0,Y~4P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf5, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~5P)` is converted to `S(E~1!1,A~0,Y~5P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf6, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~6P)` is converted to `S(E~1!1,A~0,Y~6P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf7, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~7P)` is converted to `S(E~1!1,A~0,Y~7P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf8, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~8P)` is converted to `S(E~1!1,A~0,Y~8P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf9, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~9P)` is converted to `S(E~1!1,A~0,Y~9P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf10, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~10P)` is converted to `S(E~1!1,A~0,Y~10P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf11, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~11P)` is converted to `S(E~1!1,A~0,Y~11P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf12, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~12P)` is converted to `S(E~1!1,A~0,Y~12P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf13, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~13P)` is converted to `S(E~1!1,A~0,Y~13P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf14, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~14P)` is converted to `S(E~1!1,A~0,Y~14P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf15, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~15P)` is converted to `S(E~1!1,A~0,Y~15P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf16, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~16P)` is converted to `S(E~1!1,A~0,Y~16P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf17, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~17P)` is converted to `S(E~1!1,A~0,Y~17P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf18, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~18P)` is converted to `S(E~1!1,A~0,Y~18P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf19, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(E~1,A~0,Y~19P)` is converted to `S(E~1!1,A~0,Y~19P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekf20, Ekb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~P)` is converted to `S(F~1!1,A~0,Y~P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf1, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~2P)` is converted to `S(F~1!1,A~0,Y~2P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf2, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~3P)` is converted to `S(F~1!1,A~0,Y~3P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf3, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~4P)` is converted to `S(F~1!1,A~0,Y~4P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf4, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~5P)` is converted to `S(F~1!1,A~0,Y~5P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf5, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~6P)` is converted to `S(F~1!1,A~0,Y~6P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf6, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~7P)` is converted to `S(F~1!1,A~0,Y~7P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf7, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~8P)` is converted to `S(F~1!1,A~0,Y~8P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf8, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~9P)` is converted to `S(F~1!1,A~0,Y~9P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf9, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~10P)` is converted to `S(F~1!1,A~0,Y~10P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf10, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~11P)` is converted to `S(F~1!1,A~0,Y~11P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf11, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~12P)` is converted to `S(F~1!1,A~0,Y~12P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf12, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~13P)` is converted to `S(F~1!1,A~0,Y~13P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf13, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~14P)` is converted to `S(F~1!1,A~0,Y~14P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf14, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~15P)` is converted to `S(F~1!1,A~0,Y~15P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf15, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~16P)` is converted to `S(F~1!1,A~0,Y~16P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf16, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~17P)` is converted to `S(F~1!1,A~0,Y~17P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf17, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~18P)` is converted to `S(F~1!1,A~0,Y~18P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf18, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~19P)` is converted to `S(F~1!1,A~0,Y~19P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf19, Fkb`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `S(F~1,A~0,Y~20P)` is converted to `S(F~1!1,A~0,Y~20P!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkf20, Fkb`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~U!1)` is converted to `S(E~1,A~1,Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~P!1)` is converted to `S(E~1,A~1,Y~2P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~2P!1)` is converted to `S(E~1,A~1,Y~3P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~3P!1)` is converted to `S(E~1,A~1,Y~4P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~4P!1)` is converted to `S(E~1,A~1,Y~5P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~5P!1)` is converted to `S(E~1,A~1,Y~6P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~6P!1)` is converted to `S(E~1,A~1,Y~7P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~7P!1)` is converted to `S(E~1,A~1,Y~8P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~8P!1)` is converted to `S(E~1,A~1,Y~9P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~9P!1)` is converted to `S(E~1,A~1,Y~10P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~10P!1)` is converted to `S(E~1,A~1,Y~11P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~11P!1)` is converted to `S(E~1,A~1,Y~12P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~12P!1)` is converted to `S(E~1,A~1,Y~13P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~13P!1)` is converted to `S(E~1,A~1,Y~14P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~14P!1)` is converted to `S(E~1,A~1,Y~15P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~15P!1)` is converted to `S(E~1,A~1,Y~16P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~16P!1)` is converted to `S(E~1,A~1,Y~17P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~17P!1)` is converted to `S(E~1,A~1,Y~18P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~18P!1)` is converted to `S(E~1,A~1,Y~19P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(E~1!1,A~0,Y~19P!1)` is converted to `S(E~1,A~1,Y~20P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Ekc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~20P!1)` is converted to `S(F~1,A~1,Y~19P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~19P!1)` is converted to `S(F~1,A~1,Y~18P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~18P!1)` is converted to `S(F~1,A~1,Y~17P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~17P!1)` is converted to `S(F~1,A~1,Y~16P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~16P!1)` is converted to `S(F~1,A~1,Y~15P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~15P!1)` is converted to `S(F~1,A~1,Y~14P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~14P!1)` is converted to `S(F~1,A~1,Y~13P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~13P!1)` is converted to `S(F~1,A~1,Y~12P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~12P!1)` is converted to `S(F~1,A~1,Y~11P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~11P!1)` is converted to `S(F~1,A~1,Y~10P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~10P!1)` is converted to `S(F~1,A~1,Y~9P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~9P!1)` is converted to `S(F~1,A~1,Y~8P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~8P!1)` is converted to `S(F~1,A~1,Y~7P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~7P!1)` is converted to `S(F~1,A~1,Y~6P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~6P!1)` is converted to `S(F~1,A~1,Y~5P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `S(F~1!1,A~0,Y~5P!1)` is converted to `S(F~1,A~1,Y~4P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `Fkc`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules S0 S(Y~U!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S1 S(Y~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S2 S(Y~2P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S3 S(Y~3P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S4 S(Y~4P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S5 S(Y~5P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S6 S(Y~6P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S7 S(Y~7P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S8 S(Y~8P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S9 S(Y~9P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S10 S(Y~10P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S11 S(Y~11P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S12 S(Y~12P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S13 S(Y~13P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S14 S(Y~14P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S15 S(Y~15P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S16 S(Y~16P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S17 S(Y~17P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S18 S(Y~18P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S19 S(Y~19P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules S20 S(Y~20P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Dushek_2011`
- Title/name: `Dushek 2011`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Dushek_2011.bngl`
- BNGL file used locally: `Published/Dushek2011/Dushek_2011.bngl`
- YAML file used locally: `Published/Dushek2011/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- Only the first 80 parsed reaction-rule lines are expanded individually here; the BNGL file should be consulted for any additional repetitive rules.
- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
