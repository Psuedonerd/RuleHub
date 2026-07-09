# Model Explanation: Hlavacek 1999

## 1. One-sentence summary

This model represents steric effects using BNGL rules for the molecules and interactions encoded in `steric_effects_hlavacek1999.bngl`.

## 2. Biological meaning

The metadata describes this model as **Steric effects** and places it in the `physics` category. Tags provided by the repository are: `published`, `physics`, `hlavacek`, `1999`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `Lig(b~1~2~3~4~5~6~7~8~9~10~11~12~13~14~15~16~17~18~19~20)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `Lig(b~1)  0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `n  20`
- `vKLT  1`
- `KxRT  10`
- `CRT_LT  10`
- `kr_kmx  1`
- `aA  0.01`
- `nu_1   (n-1)*(1-1*aA)*(1-3*aA/(1-1*aA))^1`
- `nu_2   (n-2)*(1-2*aA)*(1-3*aA/(1-2*aA))^2`
- `nu_3   (n-3)*(1-3*aA)*(1-3*aA/(1-3*aA))^3`
- `nu_4   (n-4)*(1-4*aA)*(1-3*aA/(1-4*aA))^4`
- `nu_5   (n-5)*(1-5*aA)*(1-3*aA/(1-5*aA))^5`
- `nu_6   (n-6)*(1-6*aA)*(1-3*aA/(1-6*aA))^6`
- `nu_7   (n-7)*(1-7*aA)*(1-3*aA/(1-7*aA))^7`
- `nu_8   (n-8)*(1-8*aA)*(1-3*aA/(1-8*aA))^8`
- `nu_9   (n-9)*(1-9*aA)*(1-3*aA/(1-9*aA))^9`
- `nu_10  (n-10)*(1-10*aA)*(1-3*aA/(1-10*aA))^10`
- `nu_11  (n-11)*(1-11*aA)*(1-3*aA/(1-11*aA))^11`
- `nu_12  (n-12)*(1-12*aA)*(1-3*aA/(1-12*aA))^12`
- `nu_13  (n-13)*(1-13*aA)*(1-3*aA/(1-13*aA))^13`
- `nu_14  (n-14)*(1-14*aA)*(1-3*aA/(1-14*aA))^14`

Additional functions or formulas parsed from the model:

- `r_b_lo() = Obs_L1 + 2*Obs_L2 + 3*Obs_L3 + 4*Obs_L4 + 5*Obs_L5`
- `r_b_md() = 6*Obs_L6 + 7*Obs_L7 + 8*Obs_L8 + 9*Obs_L9 + 10*Obs_L10`
- `r_b_hi() = 11*Obs_L11 + 12*Obs_L12 + 13*Obs_L13 + 14*Obs_L14`
- `r_b_vh() = 15*Obs_L15 + 16*Obs_L16 + 17*Obs_L17 + 18*Obs_L18`
- `r_b_xx() = 19*Obs_L19 + 20*Obs_L20`
- `r_free() = 1 - r_b_lo() - r_b_md() - r_b_hi() - r_b_vh() - r_b_xx()`
- `l_free() = 1 - CRT_LT*Obs_L_tot`
- `fn_bind() = kr_kmx*vKLT*r_free()*l_free()`
- `alpha_2() = 1 - r_free() - Obs_L1`
- `alpha_10() = 10*Obs_L10 + r_b_hi() + r_b_vh() + r_b_xx()`

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `0` is converted to `Lig(b~1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `fn_bind()`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `Lig(b~1)` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kr_kmx`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~1)` is converted to `Lig(b~2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_1*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~2)` is converted to `Lig(b~3)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_2*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~3)` is converted to `Lig(b~4)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_3*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~4)` is converted to `Lig(b~5)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_4*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~5)` is converted to `Lig(b~6)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_5*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~6)` is converted to `Lig(b~7)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_6*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~7)` is converted to `Lig(b~8)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_7*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~8)` is converted to `Lig(b~9)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_8*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~9)` is converted to `Lig(b~10)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_9*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~10)` is converted to `Lig(b~11)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_10*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~11)` is converted to `Lig(b~12)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_11*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~12)` is converted to `Lig(b~13)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_12*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~13)` is converted to `Lig(b~14)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_13*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~14)` is converted to `Lig(b~15)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_14*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~15)` is converted to `Lig(b~16)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_15*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~16)` is converted to `Lig(b~17)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_16*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~17)` is converted to `Lig(b~18)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_17*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~18)` is converted to `Lig(b~19)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_18*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~19)` is converted to `Lig(b~20)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `nu_19*KxRT*r_free()`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~2)` is converted to `Lig(b~1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `2`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~3)` is converted to `Lig(b~2)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `3`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~4)` is converted to `Lig(b~3)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `4`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~5)` is converted to `Lig(b~4)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `5`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~6)` is converted to `Lig(b~5)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `6`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~7)` is converted to `Lig(b~6)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `7`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~8)` is converted to `Lig(b~7)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `8`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~9)` is converted to `Lig(b~8)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `9`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~10)` is converted to `Lig(b~9)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `10`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~11)` is converted to `Lig(b~10)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `11`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~12)` is converted to `Lig(b~11)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `12`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~13)` is converted to `Lig(b~12)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `13`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~14)` is converted to `Lig(b~13)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `14`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~15)` is converted to `Lig(b~14)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `15`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~16)` is converted to `Lig(b~15)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `16`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~17)` is converted to `Lig(b~16)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `17`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~18)` is converted to `Lig(b~17)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `18`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~19)` is converted to `Lig(b~18)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `19`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `Lig(b~20)` is converted to `Lig(b~19)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `20`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules  Obs_L1   Lig(b~1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L2   Lig(b~2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L3   Lig(b~3)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L4   Lig(b~4)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L5   Lig(b~5)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L6   Lig(b~6)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L7   Lig(b~7)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L8   Lig(b~8)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L9   Lig(b~9)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L10  Lig(b~10)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L11  Lig(b~11)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L12  Lig(b~12)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L13  Lig(b~13)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L14  Lig(b~14)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L15  Lig(b~15)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L16  Lig(b~16)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L17  Lig(b~17)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L18  Lig(b~18)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L19  Lig(b~19)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L20  Lig(b~20)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_L_tot  Lig()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek_1999`
- Title/name: `Hlavacek 1999`
- Category: `physics`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Hlavacek1999/steric_effects_hlavacek1999.bngl`
- YAML file used locally: `Published/Hlavacek1999/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
