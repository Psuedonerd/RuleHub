# Model Explanation: Blinov 2006

## 1. One-sentence summary

This model represents phosphotyrosine signaling using BNGL rules for the molecules and interactions encoded in `Blinov_2006.bngl`.

## 2. Biological meaning

The metadata describes this model as **Phosphotyrosine signaling** and places it in the `signaling` category. Tags provided by the repository are: `published`, `blinov`, `2006`, `egf`, `egfr`, `shc`, `grb2`, `sos`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `egf(r)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `egfr(l,r,Y1068~Y~pY,Y1148~Y~pY)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Shc(PTB,Y317~Y~pY)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Grb2(SH2,SH3)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Sos(dom)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `egf(r)                        egf_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Grb2(SH2,SH3)                 Grb2_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Shc(PTB,Y317~Y)               Shc_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Sos(dom)                      Sos_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `egfr(l,r,Y1068~Y,Y1148~Y)     egfr_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Grb2(SH2,SH3!1).Sos(dom!1)    Grb2_Sos_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `egf_tot       1.2e6`
- `egfr_tot      1.8e5`
- `Grb2_tot      1.0e5`
- `Shc_tot       2.7e5`
- `Sos_tot       1.3e4`
- `Grb2_Sos_tot  4.9e4`
- `kp1      1.667e-06`
- `km1           0.06`
- `kp2      5.556e-06`
- `km2            0.1`
- `kp3            0.5`
- `km3          4.505`
- `kp14             3`
- `km14          0.03`
- `km16         0.005`
- `kp9      8.333e-07`
- `km9           0.05`
- `kp10     5.556e-06`
- `km10          0.06`
- `kp11      1.25e-06`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>100000,n_steps=>10,sparse=>1,steady_state=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `writeSBML({})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `simulate_ode({t_end=>120,n_steps=>120,atol=>1e-8,rtol=>1e-8,sparse=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `egfr(l,r)   + egf(r)` is converted to `egfr(l!1,r).egf(r!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp1,  km1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(l!+,r) + egfr(l!+,r)` is converted to `egfr(l!+,r!3).egfr(l!+,r!3)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp2, km2`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(r!+,Y1068~Y)` is converted to `egfr(r!+,Y1068~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(r!+,Y1148~Y)` is converted to `egfr(r!+,Y1148~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(Y1068~pY)` is converted to `egfr(Y1068~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `km3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(Y1148~pY)` is converted to `egfr(Y1148~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `km3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(r!+,Y1148~pY!1).Shc(PTB!1,Y317~Y)` is converted to `egfr(r!+,Y1148~pY!1).Shc(PTB!1,Y317~pY)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp14`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Shc(PTB!+,Y317~pY)` is converted to `Shc(PTB!+,Y317~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `km14`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `egfr(Y1068~pY) + Grb2(SH2,SH3)` is converted to `egfr(Y1068~pY!1).Grb2(SH2!1,SH3)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp9, km9`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(Y1068~pY) + Grb2(SH2,SH3!+)` is converted to `egfr(Y1068~pY!1).Grb2(SH2!1,SH3!+)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp11, km11`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `egfr(Y1068~pY!1).Grb2(SH2!1,SH3) + Sos(dom)` is converted to `egfr(Y1068~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp10, km10`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `egfr(Y1148~pY) + Shc(PTB,Y317~Y)` is converted to `egfr(Y1148~pY!1).Shc(PTB!1,Y317~Y)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp13, km13`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `egfr(Y1148~pY) + Shc(PTB,Y317~pY)` is converted to `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp15, km15`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `egfr(Y1148~pY) + Shc(PTB,Y317~pY!1).Grb2(SH2!1,SH3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `egfr(Y1148~pY!2).Shc(PTB!2,Y317~pY!1).Grb2(SH2!1,SH3)  kp18,km18`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `egfr(Y1148~pY) + Shc(PTB,Y317~pY!1).Grb2(SH2!1,SH3!3).Sos(dom!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `egfr(Y1148~pY!2).Shc(PTB!2,Y317~pY!1).Grb2(SH2!1,SH3!3).Sos(dom!3)  kp20,km20`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY) + Grb2(SH2,SH3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!2).Grb2(SH2!2,SH3)  kp17,km17`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY) + Grb2(SH2,SH3!3).Sos(dom!3)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3)  kp24,km24`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Shc(PTB!+,Y317~pY!2).Grb2(SH2!2,SH3) + Sos(dom)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Shc(PTB!+,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3)  kp19,km19`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Shc(PTB,Y317~pY) + Grb2(SH2,SH3)` is converted to `Shc(PTB,Y317~pY!1).Grb2(SH2!1,SH3)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp21, km21`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Shc(PTB,Y317~pY) + Grb2(SH2,SH3!+)` is converted to `Shc(PTB,Y317~pY!1).Grb2(SH2!1,SH3!+)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp23, km23`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Shc(PTB,Y317~pY)` is converted to `Shc(PTB,Y317~Y)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `km16`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Grb2(SH2,SH3) + Sos(dom)` is converted to `Grb2(SH2,SH3!1).Sos(dom!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp12, km12`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `Shc(PTB,Y317~pY!2).Grb2(SH2!2,SH3) + Sos(dom)` is converted to `\`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. No explicit rate parameter was parsed from the rule line.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `Shc(PTB,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3)  kp22,km22`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules    Dimers       egfr.egfr`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Sos_act      Shc(PTB!+,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3), egfr(Y1068~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    RP           egfr(Y1068~pY!?), egfr(Y1148~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Shc_Grb      Shc(Y317~pY!1).Grb2(SH2!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Shc_Grb_Sos  Shc(Y317~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    R_Grb2       egfr(Y1068~pY!1).Grb2(SH2!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    R_Shc        egfr(Y1148~pY!1).Shc(PTB!1,Y317~Y)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    R_ShcP       egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    ShcP         Shc(Y317~pY!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    R_G_S        egfr(Y1068~pY!1).Grb2(SH2!1,SH3!2).Sos(dom!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    R_S_G_S      egfr(Y1148~pY!1).Shc(PTB!1,Y317~pY!2).Grb2(SH2!2,SH3!3).Sos(dom!3)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Efgr_total   egfr`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Shc_total    Shc`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Sos_total    Sos`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules    Grb2_total   Grb2`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_2006`
- Title/name: `Blinov 2006`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Blinov_2006.bngl`
- BNGL file used locally: `Published/Blinov2006/Blinov_2006.bngl`
- YAML file used locally: `Published/Blinov2006/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
