# Model Explanation: Chattaraj 2021

## 1. One-sentence summary

This model represents nfkb oscillations using BNGL rules for the molecules and interactions encoded in `Chattaraj_2021.bngl`.

## 2. Biological meaning

The metadata describes this model as **NFkB oscillations** and places it in the `signaling` category. Tags provided by the repository are: `published`, `chattaraj`, `2021`, `nephrin`, `nck`, `nwasp`, `writexml`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `Nephrin(pY1,pY2,pY3)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `Nck(S1,S2,S3,Sh2)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `NWASP(p1,p2,p3,p4,p5,p6)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `1 Nephrin(pY1,pY2,pY3) 300`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `2 Nck(S1,S2,S3,Sh2) 900`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `3 NWASP(p1,p2,p3,p4,p5,p6)	450`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `kd_12	3500`
- `kd_23	3500`
- `koff_23	1000`
- `kon_23	koff_23/kd_23`
- `koff_12	1000`
- `kon_12	koff_12/kd_12`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `writeXML()`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `_01_S1_P1`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p1)` is converted to `Nck(S1!1).NWASP(p1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_02_S2_P1`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p1)` is converted to `Nck(S2!1).NWASP(p1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_03_S3_P1`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p1)` is converted to `Nck(S3!1).NWASP(p1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_06_S3_P2`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p2)` is converted to `Nck(S3!1).NWASP(p2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_05_S2_P2`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p2)` is converted to `Nck(S2!1).NWASP(p2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_04_S1_P2`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p2)` is converted to `Nck(S1!1).NWASP(p2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_08_S2_P3`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p3)` is converted to `Nck(S2!1).NWASP(p3!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_07_S1_P3`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p3)` is converted to `Nck(S1!1).NWASP(p3!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_09_S3_P3`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p3)` is converted to `Nck(S3!1).NWASP(p3!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_10_S1_P4`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p4)` is converted to `Nck(S1!1).NWASP(p4!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_11_S2_P4`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p4)` is converted to `Nck(S2!1).NWASP(p4!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_12_S3_P4`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p4)` is converted to `Nck(S3!1).NWASP(p4!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_13_S1_P5`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p5)` is converted to `Nck(S1!1).NWASP(p5!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_14_S2_P5`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p5)` is converted to `Nck(S2!1).NWASP(p5!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_15_S3_P5`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p5)` is converted to `Nck(S3!1).NWASP(p5!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_16_S1_P6`: Binding or complex formation. In words, the reactant pattern `Nck(S1) + NWASP(p6)` is converted to `Nck(S1!1).NWASP(p6!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_17_S3_P6`: Binding or complex formation. In words, the reactant pattern `Nck(S3) + NWASP(p6)` is converted to `Nck(S3!1).NWASP(p6!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_18_S2_P6`: Binding or complex formation. In words, the reactant pattern `Nck(S2) + NWASP(p6)` is converted to `Nck(S2!1).NWASP(p6!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_23,  koff_23`.
- `_19_pY1_sh2`: Binding or complex formation. In words, the reactant pattern `Nephrin(pY1) + Nck(Sh2)` is converted to `Nephrin(pY1!1).Nck(Sh2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_12,  koff_12`.
- `_20_pY2_sh2`: Binding or complex formation. In words, the reactant pattern `Nephrin(pY2) + Nck(Sh2)` is converted to `Nephrin(pY2!1).Nck(Sh2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_12,  koff_12`.
- `_21_pY3_sh2`: Binding or complex formation. In words, the reactant pattern `Nephrin(pY3) + Nck(Sh2)` is converted to `Nephrin(pY3!1).Nck(Sh2!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `kon_12,  koff_12`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules tot_Nck Nck()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules free_Nck Nck(S1,S2,S3,Sh2)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules tot_NWASP NWASP()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules free_NWASP NWASP(p1,p2,p3,p4,p5,p6)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules tot_Nephrin Nephrin()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules free_Nephrin Nephrin(pY1,pY2,pY3)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules fully_bound_Nephrin Nephrin(pY1!+,pY2!+,pY3!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules fully_bound_Nck Nck(S1!+,S2!+,S3!+,Sh2!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules fully_bound_NWASP NWASP(p1!+,p2!+,p3!+,p4!+,p5!+,p6!+)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules cluster_neph_nck_nw Nephrin().Nck().NWASP()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules cluster_nck_nw Nck().NWASP()`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Chattaraj_2021`
- Title/name: `Chattaraj 2021`
- Category: `signaling`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/complex-models/Chattaraj_2021.bngl`
- BNGL file used locally: `Published/Chattaraj2021/Chattaraj_2021.bngl`
- YAML file used locally: `Published/Chattaraj2021/metadata.yaml`
- Compatibility: bng2 compatible = `false`, NFsim compatible = `true`, simulation methods = `['ode']`
- Playground visibility: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
