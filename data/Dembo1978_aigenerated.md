# Model Explanation: Dembo 1978

## 1. One-sentence summary

This model represents blbr dembo 1978 using BNGL rules for the molecules and interactions encoded in `blbr_dembo1978.bngl`.

## 2. Biological meaning

The metadata describes this model as **BLBR dembo 1978** and places it in the `physics` category. Tags provided by the repository are: `published`, `physics`, `dembo`, `1978`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L(r,r)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `R(l,l)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L(r,r)  LT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `R(l,l)  RT`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `NA  6.02214076e23`
- `V_cell  1e-9`
- `R_per_cell  3e5`
- `f  0.01`
- `V_sim  V_cell*f`
- `RT  R_per_cell*f`
- `LT_per_cell  3e6`
- `LT  LT_per_cell*f`
- `kon  1e6`
- `koff  0.01`
- `KxRT  5`
- `kf  kon/(NA*V_sim)`
- `kxf  KxRT/RT*koff`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- No explicit BNGL action or simulation command was parsed.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `R_capture`: Binding or complex formation. In words, the reactant pattern `L(r,r) + R(l)` is converted to `L(r!1,r).R(l!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kf`.
- `R_crosslink`: Biochemical transformation or interaction. In words, the reactant pattern `L(r!+,r) + R(l)` is converted to `L(r!+,r!1).R(l!1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kxf`.
- `R_dissoc`: Unbinding or complex dissociation. In words, the reactant pattern `L(r!1).R(l!1)` is converted to `L(r) + R(l)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `koff`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Species    Obs_Free_L        L(r,r)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Species    Obs_Free_R        R(l,l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Bonds         L(r!1).R(l!1)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Free_L_sites  L(r)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules  Obs_Free_R_sites  R(l)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Dembo_1978`
- Title/name: `Dembo 1978`
- Category: `physics`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Source path in metadata: `missing`
- BNGL file used locally: `Published/Dembo1978/blbr_dembo1978.bngl`
- YAML file used locally: `Published/Dembo1978/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
