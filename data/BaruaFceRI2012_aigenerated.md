# Model Explanation: BaruaFceRI 2012

## 1. One-sentence summary

This model represents fcãƒå½ã‚âµri signaling using BNGL rules for the molecules and interactions encoded in `BaruaFceRI_2012.bngl`.

## 2. Biological meaning

The metadata describes this model as **FcÃƒÅ½Ã‚ÂµRI signaling** and places it in the `immunology` category. Tags provided by the repository are: `published`, `immunology`, `baruafceri`, `2012`, `r_o`, `rdimer_o`, `l_o`, `t_o`, `l`, `fcr`, `lyn`, `syk`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L(l,l)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `FCR(s~d~o,a,b~Y~pY,g~Y~pY)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Lyn(s~d~o,U,SH2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Syk(tSH2,a~Y~pY)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `LAT(s~d~o,p~Y~pY)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Grb2(SH2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L(l,l)                   LigT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `FCR(s~o,a,b~Y,g~Y)       RecT*r_o/(r_o + r_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `FCR(s~d,a,b~Y,g~Y)       RecT*r_d/(r_o + r_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lyn(s~o,U,SH2)           LynT*l_o/(l_o + l_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Lyn(s~d,U,SH2)           LynT*l_d/(l_o + l_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Syk(tSH2,a~Y)            SykT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `LAT(s~o,p~Y)             LATT*t_o/(t_o + t_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `LAT(s~d,p~Y)             LATT*t_d/(t_o + t_d)`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Grb2(SH2)                GrbT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `LigT      6.0e5`
- `RecT      400000/N`
- `LynT      28000/N`
- `SykT      400000/N`
- `LATT      1000000/N`
- `GrbT      400000/N`
- `kon       8.125e-8`
- `kx        N*5e-6`
- `koff      0.5`
- `kon_h     4.3e-8`
- `koff_h    0.019`
- `lf         N*5e-5`
- `lr1        20`
- `lr2        0.12`
- `sf         N*6e-5`
- `sr         0.20`
- `gf         N*1.25e-6`
- `gr         0.30`
- `plb1_o     30`
- `plb1_d     6`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>3600, n_steps=>3600,atoll=>1e-08,rtol=>1e-08,sparse=>1});`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `FCR(a) + L(l,l)` is converted to `FCR(a!1).L(l!1,l)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a) + L(l,l!1).FCR(s~d,a!1)` is converted to `FCR(s~d,a!2).L(l!2,l!1).FCR(s~d,a!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kx,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~o,a) + L(l,l!1).FCR(s~o,a!1)` is converted to `FCR(s~o,a!2).L(l!2,l!1).FCR(s~o,a!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kx,  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `FCR(s~d,b~Y) + Lyn(s~d,U,SH2)` is converted to `FCR(s~d,b~Y!1).Lyn(s~d,U!1,SH2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `lf,  lr1`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `FCR(s~d,b~pY) + Lyn(s~d,U,SH2)` is converted to `FCR(s~d,b~pY!1).Lyn(s~d,U,SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `lf,  lr2`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `FCR(s~o,b~Y) + Lyn(s~o,U,SH2)` is converted to `FCR(s~o,b~Y!1).Lyn(s~o,U!1,SH2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `lf,  lr1`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `FCR(s~o,b~pY) + Lyn(s~o,U,SH2)` is converted to `FCR(s~o,b~pY!1).Lyn(s~o,U,SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `lf,  lr2`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Syk(tSH2) + FCR(g~pY)` is converted to `Syk(tSH2!1).FCR(g~pY!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `sf,  sr`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `LAT(p~pY) + Grb2(SH2)` is converted to `LAT(p~pY!1).Grb2(SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `gf,  gr`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~o,U!1,SH2).FCR(s~o,b~Y!1).FCR(s~o,b~Y)` is converted to `Lyn(s~o,U!1,SH2).FCR(s~o,b~Y!1).FCR(s~o,b~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plb1_o`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~o,U,SH2!1).FCR(s~o,b~pY!1).FCR(s~o,b~Y)` is converted to `Lyn(s~o,U,SH2!1).FCR(s~o,b~pY!1).FCR(s~o,b~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plb2_o`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~o,U!1,SH2).FCR(s~o,b~Y!1).FCR(s~o,g~Y)` is converted to `Lyn(s~o,U!1,SH2).FCR(s~o,b~Y!1).FCR(s~o,g~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plg1_o`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~o,U,SH2!1).FCR(s~o,b~pY!1).FCR(s~o,g~Y)` is converted to `Lyn(s~o,U,SH2!1).FCR(s~o,b~pY!1).FCR(s~o,g~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plg2_o`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~d,U!1,SH2).FCR(s~d,b~Y!1).FCR(s~d,b~Y)` is converted to `Lyn(s~d,U!1,SH2).FCR(s~d,b~Y!1).FCR(s~d,b~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plb1_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~d,U,SH2!1).FCR(s~d,b~pY!1).FCR(s~d,b~Y)` is converted to `Lyn(s~d,U,SH2!1).FCR(s~d,b~pY!1).FCR(s~d,b~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plb2_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~d,U!1,SH2).FCR(s~d,b~Y!1).FCR(s~d,g~Y)` is converted to `Lyn(s~d,U!1,SH2).FCR(s~d,b~Y!1).FCR(s~d,g~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plg1_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~d,U,SH2!1).FCR(s~d,b~pY!1).FCR(s~d,g~Y)` is converted to `Lyn(s~d,U,SH2!1).FCR(s~d,b~pY!1).FCR(s~d,g~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `plg2_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(a~Y).Syk(a~Y)` is converted to `Syk(a~Y).Syk(a~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pss1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(a~pY).Syk(a~Y)` is converted to `Syk(a~pY).Syk(a~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pss2`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(tSH2!1).FCR(s~d,g~pY!1) + LAT(s~d,p~Y)` is converted to `Syk(tSH2!1).FCR(s~d,g~pY!1) + LAT(s~d,p~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `psl`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(tSH2!1).FCR(s~o,g~pY!1) + LAT(s~o,p~Y)` is converted to `Syk(tSH2!1).FCR(s~o,g~pY!1) + LAT(s~o,p~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `psl`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,b~pY)` is converted to `FCR(s~d,b~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `db`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,g~pY)` is converted to `FCR(s~d,g~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `dg`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~o,b~pY)` is converted to `FCR(s~o,b~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `z*db`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~o,g~pY)` is converted to `FCR(s~o,g~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `z*dg`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,g~pY!1).Syk(tSH2!1,a~pY)` is converted to `FCR(s~d,g~pY!1).Syk(tSH2!1,a~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `ds`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~o,g~pY!1).Syk(tSH2!1,a~pY)` is converted to `FCR(s~o,g~pY!1).Syk(tSH2!1,a~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `z*ds`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(tSH2,a~pY)` is converted to `Syk(tSH2,a~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `ds`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `LAT(s~d,p~pY)` is converted to `LAT(s~d,p~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `dl`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `LAT(s~o,p~pY)` is converted to `LAT(s~o,p~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `z*dl`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a,b~Y)` is converted to `FCR(s~o,a,b~Y)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `r_o,  r_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a,b~pY)` is converted to `FCR(s~o,a,b~pY)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `r_o,  r_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~Y).L(l!1,l)` is converted to `FCR(s~o,a!1,b~Y).L(l!1,l)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `r_o,  r_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~pY).L(l!1,l)` is converted to `FCR(s~o,a!1,b~pY).L(l!1,l)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `r_o,  r_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lyn(s~d,U,SH2)` is converted to `Lyn(s~o,U,SH2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `l_o,  l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a,b~Y!1).Lyn(s~d,U!1)` is converted to `FCR(s~o,a,b~Y!1).Lyn(s~o,U!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `l_o,  l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a,b~pY!1).Lyn(s~d,SH2!1)` is converted to `FCR(s~o,a,b~pY!1).Lyn(s~o,SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `l_o,  l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~Y!2).L(l!1,l).Lyn(s~d,U!2)` is converted to `FCR(s~o,a!1,b~Y!2).L(l!1,l).Lyn(s~o,U!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `l_o,  l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~pY!2).L(l!1,l).Lyn(s~d,SH2!2)` is converted to `FCR(s~o,a!1,b~pY!2).L(l!1,l).Lyn(s~o,SH2!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `l_o,  l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~Y).L(l!1,l!2).FCR(s~d,a!2,b~Y)` is converted to `FCR(s~o,a!1,b~Y).L(l!1,l!2).FCR(s~o,a!2,b~Y)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `rdimer_o,  rdimer_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~pY).L(l!1,l!2).FCR(s~d,a!2,b~Y)` is converted to `FCR(s~o,a!1,b~pY).L(l!1,l!2).FCR(s~o,a!2,b~Y)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `rdimer_o,  rdimer_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `FCR(s~d,a!1,b~pY).L(l!1,l!2).FCR(s~d,a!2,b~pY)` is converted to `FCR(s~o,a!1,b~pY).L(l!1,l!2).FCR(s~o,a!2,b~pY)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `rdimer_o,  rdimer_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~Y!3).L(l!1,l!2).FCR(s~d,a!2,b~Y).Lyn(s~d,U!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~Y!3).L(l!1,l!2).FCR(s~o,a!2,b~Y).Lyn(s~o,U!3) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~Y!3).L(l!1,l!2).FCR(s~d,a!2,b~pY).Lyn(s~d,U!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~Y!3).L(l!1,l!2).FCR(s~o,a!2,b~pY).Lyn(s~o,U!3) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~pY!3).L(l!1,l!2).FCR(s~d,a!2,b~Y).Lyn(s~d,SH2!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~pY!3).L(l!1,l!2).FCR(s~o,a!2,b~Y).Lyn(s~o,SH2!3) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~pY!3).L(l!1,l!2).FCR(s~d,a!2,b~pY).Lyn(s~d,SH2!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~pY!3).L(l!1,l!2).FCR(s~o,a!2,b~pY).Lyn(s~o,SH2!3) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~Y!3).L(l!1,l!2).FCR(s~d,a!2,b~Y!4).Lyn(s~d,U!3).Lyn(s~d,U!4)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~Y!3).L(l!1,l!2).FCR(s~o,a!2,b~Y!4).Lyn(s~o,U!3).Lyn(s~o,U!4) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~pY!3).L(l!1,l!2).FCR(s~d,a!2,b~Y!4).Lyn(s~d,SH2!3).Lyn(s~d,U!4)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~pY!3).L(l!1,l!2).FCR(s~o,a!2,b~Y!4).Lyn(s~o,SH2!3).Lyn(s~o,U!4) l_o, l_d`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `FCR(s~d,a!1,b~pY!3).L(l!1,l!2).FCR(s~d,a!2,b~pY!4).Lyn(s~d,SH2!3).Lyn(s~d,SH2!4)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `FCR(s~o,a!1,b~pY!3).L(l!1,l!2).FCR(s~o,a!2,b~pY!4).Lyn(s~o,SH2!3).Lyn(s~o,SH2!4) l_o, l_d`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `LAT(s~d)` is converted to `LAT(s~o)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `t_o,  t_d`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules pBeta       FCR(b~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules pGamma      FCR(g~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules pSyk        Syk(tSH2!+,a~pY)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules pLAT        LAT(p~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `BaruaFceRI_2012`
- Title/name: `BaruaFceRI 2012`
- Category: `immunology`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/immune-signaling/BaruaFceRI_2012.bngl`
- BNGL file used locally: `Published/BaruaFceRI2012/BaruaFceRI_2012.bngl`
- YAML file used locally: `Published/BaruaFceRI2012/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
