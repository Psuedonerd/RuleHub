# Model Explanation: Blinov egfr

## 1. One-sentence summary

This model represents egfr signaling model using BNGL rules for the molecules and interactions encoded in `Blinov_egfr.bngl`.

## 2. Biological meaning

The metadata describes this model as **EGFR signaling model** and places it in the `signaling` category. Tags provided by the repository are: `published`, `nfsim`, `blinov`, `egfr`, `egf`, `grb2`, `shc`, `simulate_nf`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `EGFR(ecd,tmd,y1068~u~p,y1173~u~p)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `EGF(rb)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Grb2(sh2,sos)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Shc(sh3,Y773~p~u)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `1 @EC:EGF(rb) 680.0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `2 @M:EGFR(ecd,tmd,y1068~u,y1173~u) 602.0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `3 @Cyt:Shc(sh3,Y773~u) 150.0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- No entries were found in this block.

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `simulate_nf({t_end=>120.0,n_steps=>240})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `r00_lig_bind`: Binding or complex formation. In words, the reactant pattern `@EC:EGF(rb) + @M:EGFR(ecd,tmd)` is converted to `@M:EGF(rb!1).EGFR(ecd!1,tmd)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.003,  0.06`.
- `r01_dimer`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(ecd!+,tmd)%1 + @M:EGFR(ecd!+,tmd)%2` is converted to `@M:EGFR(ecd!+,tmd!1)%1.EGFR(ecd!+,tmd!1)%2`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.001,  0.01`.
- `r04_dephosp`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(y1173~p)` is converted to `@M:EGFR(y1173~u)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `4.505`.
- `r03_phosp`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(tmd!+,y1068~u)` is converted to `@M:EGFR(tmd!+,y1068~p)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.01`.
- `r02_phosp`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(tmd!+,y1173~u)` is converted to `@M:EGFR(tmd!+,y1173~p)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.01`.
- `r05_deposp`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(y1068~p)` is converted to `@M:EGFR(y1068~u)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `4.505`.
- `r08_shcU_bind`: Binding or complex formation. In words, the reactant pattern `@M:EGFR(y1173~p) + @Cyt:Shc(sh3,Y773~u)` is converted to `@M:EGFR(y1173~p!1).Shc(sh3!1,Y773~u)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.045,  0.6`.
- `r09_shc_phosp`: Biochemical transformation or interaction. In words, the reactant pattern `@M:EGFR(y1173~p!1).Shc(sh3!1,Y773~u)` is converted to `@M:EGFR(y1173~p!1).Shc(sh3!1,Y773~p)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `3.0,  0.03`.
- `r14_shc_dephosp`: Biochemical transformation or interaction. In words, the reactant pattern `@Cyt:Shc(sh3,Y773~p)` is converted to `@Cyt:Shc(sh3,Y773~u)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `0.005`.
- `r08_shcP_bind`: Binding or complex formation. In words, the reactant pattern `@M:EGFR(y1173~p) + @Cyt:Shc(sh3,Y773~p)` is converted to `@M:EGFR(y1173~p!1).Shc(sh3!1,Y773~p)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `4.5E-4,  0.3`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules EGFR_tot @M:EGFR()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules EGF_EC @EC:EGF()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Shc_cyt @Cyt:Shc()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Dimers @M:EGFR(tmd!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Y1068_phosp @M:EGFR(y1068~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Y1173_phosp @M:EGFR(y1173~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules Total_phosp @M:EGFR(y1068~p!?) @M:EGFR(y1173~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules ShcP_Cyt @Cyt:Shc(Y773~p!?)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Blinov_egfr`
- Title/name: `Blinov egfr`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/growth-factor-signaling/Blinov_egfr.bngl`
- BNGL file used locally: `Published/Blinovegfr/Blinov_egfr.bngl`
- YAML file used locally: `Published/Blinovegfr/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `true`, simulation methods = `['nf']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
