# Model Explanation: Goldstein 1980

## 1. One-sentence summary

This model represents blbr heterogeneity using BNGL rules for the molecules and interactions encoded in `blbr_heterogeneity_goldstein1980.bngl`.

## 2. Biological meaning

The metadata describes this model as **BLBR heterogeneity** and places it in the `physics` category. Tags provided by the repository are: `published`, `physics`, `goldstein`, `1980`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L(r1,r2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R1(l1,l2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R2(l1,l2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L(r1,r2)   Lfree_init`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R1(l1,l2)  RT_1`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R2(l1,l2)  RT_2`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `NA  6.02214076e23`
- `V_cell  1e-9`
- `S_cell  4.7e-6`
- `X_T_per_cell  500`
- `r1  0.5`
- `r2  0.5`
- `f  0.1`
- `V_sim  V_cell*f`
- `RT  X_T_per_cell*f`
- `RT_1  r1*RT`
- `RT_2  r2*RT`
- `Ka_1  5e6`
- `Ka_2  5e8`
- `kappa  4e-15`
- `Kx_1  kappa*Ka_1`
- `Kx_2  kappa*Ka_2`
- `KxRT_1  Kx_1*X_T_per_cell/S_cell`
- `KxRT_2  Kx_2*X_T_per_cell/S_cell`
- `koff  10`
- `kf1  Ka_1*koff/(NA*V_sim)`

Additional functions or formulas parsed from the model:

- `w1() = Obs_NCL_R1 / RT_1`
- `w2() = Obs_NCL_R2 / RT_2`
- `x_poly() = 1 - (Obs_NCL_R1 + Obs_NCL_R2) / RT`

Actions or simulation commands parsed from the model:

- No explicit BNGL action or simulation command was parsed.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R1(l1)` is converted to `L(r1!1,r2).R1(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R1(l2)` is converted to `L(r1!1,r2).R1(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R1(l1)` is converted to `L(r1,r2!1).R1(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R1(l2)` is converted to `L(r1,r2!1).R1(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R2(l1)` is converted to `L(r1!1,r2).R2(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R2(l2)` is converted to `L(r1!1,r2).R2(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R2(l1)` is converted to `L(r1,r2!1).R2(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `L(r1,r2) + R2(l2)` is converted to `L(r1,r2!1).R2(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2*(1-use_excess),  koff`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R1(l1)` is converted to `R1(l1!1).L(r1!1,r2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R1(l2)` is converted to `R1(l2!1).L(r1!1,r2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R1(l1)` is converted to `R1(l1!1).L(r1,r2!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R1(l2)` is converted to `R1(l2!1).L(r1,r2!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf1_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R2(l1)` is converted to `R2(l1!1).L(r1!1,r2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R2(l2)` is converted to `R2(l2!1).L(r1!1,r2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R2(l1)` is converted to `R2(l1!1).L(r1,r2!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2_pseudo*use_excess`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `R2(l2)` is converted to `R2(l2!1).L(r1,r2!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf2_pseudo*use_excess`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1!+,r2) + R1(l1)` is converted to `L(r1!+,r2!1).R1(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf1,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1!+,r2) + R1(l2)` is converted to `L(r1!+,r2!1).R1(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf1,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1,r2!+) + R1(l1)` is converted to `L(r1!1,r2!+).R1(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf1,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1,r2!+) + R1(l2)` is converted to `L(r1!1,r2!+).R1(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf1,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1!+,r2) + R2(l1)` is converted to `L(r1!+,r2!1).R2(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf2,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1!+,r2) + R2(l2)` is converted to `L(r1!+,r2!1).R2(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf2,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1,r2!+) + R2(l1)` is converted to `L(r1!1,r2!+).R2(l1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf2,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1,r2!+) + R2(l2)` is converted to `L(r1!1,r2!+).R2(l2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf2,  koff`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `L(r1,r2)` is converted to `0 fast*use_excess`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `DeleteMolecules`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  Obs_Free_R1  R1(l1,l2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Free_R2  R2(l1,l2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_NCL_R1  R1(l1,l2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R1(l1!1,l2).L(r1!1,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R1(l1!1,l2).L(r1,r2!1) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R1(l1,l2!1).L(r1!1,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R1(l1,l2!1).L(r1,r2!1) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1!1,r2).R1(l1!1,l2!2).L(r1!2,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1!1,r2).R1(l1!1,l2!2).L(r1,r2!2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1,r2!1).R1(l1!1,l2!2).L(r1!2,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1,r2!1).R1(l1!1,l2!2).L(r1,r2!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_NCL_R2  R2(l1,l2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R2(l1!1,l2).L(r1!1,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R2(l1!1,l2).L(r1,r2!1) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R2(l1,l2!1).L(r1!1,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `R2(l1,l2!1).L(r1,r2!1) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1!1,r2).R2(l1!1,l2!2).L(r1!2,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1!1,r2).R2(l1!1,l2!2).L(r1,r2!2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1,r2!1).R2(l1!1,l2!2).L(r1!2,r2) \`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `L(r1,r2!1).R2(l1!1,l2!2).L(r1,r2!2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Xlinks  L(r1!+,r2!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Goldstein_1980`
- Title/name: `Goldstein 1980`
- Category: `physics`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Goldstein1980/blbr_heterogeneity_goldstein1980.bngl`
- YAML file used locally: `Published/Goldstein1980/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
