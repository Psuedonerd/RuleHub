# Model Explanation: Harmon 2017

## 1. One-sentence summary

This model represents antigen pulses using BNGL rules for the molecules and interactions encoded in `antigen_pulses_harmon2017.bngl`.

## 2. Biological meaning

The metadata describes this model as **Antigen pulses** and places it in the `immunology` category. Tags provided by the repository are: `published`, `immunology`, `harmon`, `2017`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `Ag(DNP)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R(IgE,Yb~0~P,Yg~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Syk(tSH2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Ship1(SH2,x)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `X(s~on~off)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PIP3()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `H(loc~in~out)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `$Ag(DNP)            Ag_tot_1`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R(IgE,Yb~0,Yg~0)   R_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Syk(tSH2)           Syk_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `Ship1(SH2,x)        Ship1_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `X(s~off)            X_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PIP3()              0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `H(loc~in)           H_tot`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `X_tot__FREE__     6.13331088e+00`
- `k_Xoff__FREE__    1.91394890e-06`
- `k_Xon__FREE__     9.39816993e+04`
- `kase__FREE__      3.76143208e+00`
- `kdegX__FREE__     3.19130252e-04`
- `kdegran__FREE__   1.88893284e+05`
- `km_Ship1__FREE__  1.43154204e-03`
- `km_Syk__FREE__    2.87783197e-01`
- `km_x__FREE__      1.12185442e-01`
- `koff__FREE__      4.45671503e-03`
- `kp_Ship1__FREE__  1.10810534e+04`
- `kp_Syk__FREE__    2.65462642e+05`
- `kp_x__FREE__      7.81553987e+05`
- `kpten__FREE__     9.95093271e-03`
- `ksynth1__FREE__   1.84930114e-02`
- `pase__FREE__      1.60206452e-01`
- `f  1`
- `NA  6.02214076e23`
- `T  60`
- `Vchannel  500e-9`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `saveConcentrations()`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `Ag(DNP) + R(IgE)` is converted to `Ag(DNP!1).R(IgE!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `R(IgE!+,Yb~0,Yg~0)` is converted to `R(IgE!+,Yb~P,Yg~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kase`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `R(Yb~P,Yg~P)` is converted to `R(Yb~0,Yg~0)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pase`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R(Yg~P) + Syk(tSH2)` is converted to `R(Yg~P!1).Syk(tSH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `\`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `kp_Syk, km_Syk`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R(Yb~P) + Ship1(SH2)` is converted to `R(Yb~P!1).Ship1(SH2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `\`.
- `unnamed rule`: This rule/pattern is present but its event type is not obvious from the syntax: `kp_Ship1, km_Ship1`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `R(Yb~P!?) + X(s~off)` is converted to `R(Yb~P!?) + X(s~on)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `k_Xon`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `X(s~on)` is converted to `X(s~off)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `k_Xoff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Syk(tSH2!+)` is converted to `Syk(tSH2!+) + PIP3()`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `ksynth1`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `X(s~on) + Ship1(x)` is converted to `X(s~on!1).Ship1(x!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kp_x,  km_x`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Ship1(SH2!+,x!+) + PIP3()` is converted to `Ship1(SH2!+,x!+)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdeg1`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `PIP3()` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kpten`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `X(s~on)` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdegX`.
- `unnamed rule`: Unbinding or complex dissociation. In words, the reactant pattern `X(s~on!1).Ship1(x!1)` is converted to `Ship1(x)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdegX`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PIP3() + H(loc~in)` is converted to `PIP3() + H(loc~out)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kdegran`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  Ag_total              Ag()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Ag_free               Ag(DNP)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  R_bound               R(IgE!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  R_free                R(IgE)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  RP                    R(Yg~P!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  R0                    R(Yg~0)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  actSyk                Syk(tSH2!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  actShip1              Ship1(SH2!+,x!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Ship1_total           Ship1()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  PIP3_total            PIP3()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Xall                  X()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  X_on_free             X(s~on)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  X_on_free_or_bound    X(s~on!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  XShip1                X(s~on!1).Ship1(x!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  degranulation         H(loc~out)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Harmon_2017`
- Title/name: `Harmon 2017`
- Category: `immunology`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Harmon2017/antigen_pulses_harmon2017.bngl`
- YAML file used locally: `Published/Harmon2017/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
