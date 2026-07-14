# Coder Model Explanation: Jaruszewicz 2023

## 1. Model identity and scope

- **Model id:** `Jaruszewicz-Blonska_2023`
- **Title:** Jaruszewicz 2023
- **BNGL path:** `Published/JaruszewiczBlonska2023/Jaruszewicz-Blonska_2023.bngl`
- **YAML path:** `Published/JaruszewiczBlonska2023/metadata.yaml`
- **Metadata description:** T-cell discrimination
- **Scope:** A canonical NF-kappaB signaling ODE model with active/neutral IKK, IkBa mRNA/protein, A20, and nuclear NFkB. The rules encode TNF-controlled IKK activation, turnover, NFkB-driven transcription/translation, A20 feedback, NFkB import/export, and IkBa-mediated removal.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 14 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 5 molecule type entries. |
| Seed/species | Yes | 6 initial species entries. |
| Observables | Yes | 6 observable entries. |
| Functions | Yes | 3 function entries. |
| Reaction rules | Yes | 14 reaction rules. |
| Actions | Yes | 4 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `k_deg` | `0.000107` | kinetic or model-control parameter |
| `k_1` | `0.00195` | kinetic or model-control parameter |
| `k_3` | `0.00145` | kinetic or model-control parameter |
| `k_2` | `0.0357` | kinetic or model-control parameter |
| `a_3` | `0.0946` | kinetic or model-control parameter |
| `delta` | `0.1083` | kinetic or model-control parameter |
| `epsilon` | `0.0428` | kinetic or model-control parameter |
| `c_deg` | `0.000106` | kinetic or model-control parameter |
| `c_4a` | `0.00313` | kinetic or model-control parameter |
| `a_2` | `0.0763` | kinetic or model-control parameter |
| `c_5a` | `0.0000578` | kinetic or model-control parameter |
| `i_1a` | `0.000595` | kinetic or model-control parameter |
| `c_3a` | `0.000372` | kinetic or model-control parameter |
| `TR` | `0` | TNF on(1)/off(0) |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `k_NFkBimport() a_3*delta*(1-NFkB_n)/(IkBa+ delta)` | derived rate/readout expression used by rules, observables, or simulation output |
| `k_NFkBexport() i_1a/(NFkB_n+epsilon)` | derived rate/readout expression used by rules, observables, or simulation output |
| `k_IkBatransport() a_2+(a_3*(1-NFkB_n))/((IkBa+delta))` | derived rate/readout expression used by rules, observables, or simulation output |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `IKK` | 1 | st~n~a | st: n, a | none | no explicit binding/modification site role beyond whole-molecule abundance | neutral/active form of IKK kinase |
| `IkBa` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | cytoplasmic, IkB |
| `IkBa_mRNA` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | IkBa transcript |
| `A20` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | cytoplasmic A20 |
| `NFkB` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | nuclear NFkB |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `IKK(st~n)` | `1` | neutral/active form of IKK kinase |
| `IKK(st~a)` | `0` | neutral/active form of IKK kinase |
| `IkBa()` | `0` | cytoplasmic, IkB |
| `IkBa_mRNA()` | `0` | IkBa transcript |
| `A20()` | `0` | cytoplasmic A20 |
| `NFkB()` | `0` | nuclear NFkB |

## 6. Complete reaction-rule inventory

The source contains **14** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | IKK | `k_1*TR` | internal-state conversion/modification | `IKK(st~n) -> IKK(st~a)` | TNFR1 activation and signal transduction cascade. Updates internal state(s) on IKK: IKK.st n→a. Rate/expression: k_1*TR. |
| 2 | `Unlabeled` | one-way | IKK | `k_deg` | source/synthesis or algebraic source term | `0 -> IKK(st~n)` | Produces IKK while retaining or consuming an abstract source. Rate/expression: k_deg. |
| 3 | `Unlabeled` | one-way | IKK | `k_deg+k_3` | sink/degradation/removal | `IKK(st~a) -> 0` | Removes IKK from the dynamic pool through the zero/sink side of the rule. Rate/expression: k_deg+k_3. |
| 4 | `Unlabeled` | one-way | IKK | `k_deg` | sink/degradation/removal | `IKK(st~n) -> 0` | Removes IKK from the dynamic pool through the zero/sink side of the rule. Rate/expression: k_deg. |
| 5 | `Unlabeled` | one-way | A20, NFkB | `c_deg` | stoichiometric pattern rewrite | `NFkB() -> NFkB() + A20()` | A20 synthesis and degradation, IkB transcription, translation, mRNA and protein degradation. Produces A20 while retaining or consuming NFkB. Rate/expression: c_deg. |
| 6 | `Unlabeled` | one-way | A20 | `c_deg` | sink/degradation/removal | `A20() -> 0` | Removes A20 from the dynamic pool through the zero/sink side of the rule. Rate/expression: c_deg. |
| 7 | `Unlabeled` | one-way | IkBa_mRNA, NFkB | `c_3a` | stoichiometric pattern rewrite | `NFkB() -> NFkB() + IkBa_mRNA()` | Produces IkBa_mRNA while retaining or consuming NFkB. Rate/expression: c_3a. |
| 8 | `Unlabeled` | one-way | IkBa_mRNA | `c_3a` | sink/degradation/removal | `IkBa_mRNA() -> 0` | Removes IkBa_mRNA from the dynamic pool through the zero/sink side of the rule. Rate/expression: c_3a. |
| 9 | `Unlabeled` | one-way | IkBa, IkBa_mRNA | `c_4a` | stoichiometric pattern rewrite | `IkBa_mRNA() -> IkBa_mRNA() + IkBa()` | Produces IkBa while retaining or consuming IkBa_mRNA. Rate/expression: c_4a. |
| 10 | `Unlabeled` | one-way | IkBa | `c_5a` | sink/degradation/removal | `IkBa() -> 0` | Removes IkBa from the dynamic pool through the zero/sink side of the rule. Rate/expression: c_5a. |
| 11 | `Unlabeled` | one-way | A20, IKK | `k_2*TR` | stoichiometric pattern rewrite | `A20() + IKK(st~a) -> A20()` | Protein interactions. Consumes IKK while preserving A20. Rate/expression: k_2*TR. |
| 12 | `Unlabeled` | one-way | IKK, NFkB | `k_NFkBimport()` | stoichiometric pattern rewrite | `IKK(st~a) -> IKK(st~a) + NFkB()` | Produces NFkB while retaining or consuming IKK. Rate/expression: k_NFkBimport(). |
| 13 | `Unlabeled` | one-way | IkBa, NFkB | `k_NFkBexport()` | sink/degradation/removal | `NFkB() + IkBa() -> 0` | Removes IkBa, NFkB from the dynamic pool through the zero/sink side of the rule. Rate/expression: k_NFkBexport(). |
| 14 | `Unlabeled` | one-way | IKK, IkBa | `k_IkBatransport()` | stoichiometric pattern rewrite | `IKK(st~a)+IkBa() -> IKK(st~a)` | Consumes IkBa while preserving IKK. Rate/expression: k_IkBatransport(). |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `IKK_a` | `Species` | `IKK(st~a)` | neutral/active form of IKK kinase |
| `tIkBa` | `Species` | `IkBa_mRNA()` | IkBa transcript |
| `A20` | `Species` | `A20()` | cytoplasmic A20 |
| `NFkB_n` | `Species` | `NFkB()` | nuclear NFkB |
| `IkBa` | `Species` | `IkBa()` | cytoplasmic, IkB |
| `IKK_n` | `Species` | `IKK(st~n)` | neutral/active form of IKK kinase |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1});` — active execution command in the actions block

2. `setParameter("TR",0);` — - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -; ########################################################; ##### combination experiment for WT cells #############; #######################################################

3. `simulate_ode({suffix=>"continuous",t_end=>30*24*3600,n_steps=>200,atol=>1e-16,rtol=>1e-16, sparse=>1, sparse=>1, steady_state=>1});` — active execution command in the actions block

4. `saveConcentrations()` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- The YAML description says T-cell discrimination, but the BNGL title/comments describe canonical NF-kappaB signaling; the summary follows the BNGL content and flags the mismatch.

- No compartments are declared even though comments label some species nuclear or cytoplasmic; localization is encoded only in molecule names/comments and rate laws.

- Many pulse protocols are present but auto-disabled as comments; the active workflow is the continuous/steady-state ODE command after TR is set to 0.
