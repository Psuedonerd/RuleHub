# Coder Model Explanation: Jaruszewicz 2023

## 1. Model identity and scope

- **Model id:** `Jaruszewicz-Blonska_2023`
- **Title:** Jaruszewicz 2023
- **BNGL path:** `Published/JaruszewiczBlonska2023/Jaruszewicz-Blonska_2023.bngl`
- **YAML path:** `Published/JaruszewiczBlonska2023/metadata.yaml`
- **Metadata description:** T-cell discrimination
- **Scope:** The BNGL file implements a compact canonical NF-kappaB ODE model. `IKK` has a real internal state site `st~n~a`; the other species (`IkBa`, `IkBa_mRNA`, `A20`, `NFkB`) are site-free pools. TNF input is represented by parameter `TR`, which gates IKK activation and A20-mediated IKK removal.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 14 fitted/control parameters, including `TR` as TNF off/on switch. |
| Compartments | No | No formal BNGL compartments. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 5 molecule types; only `IKK` has a site/state. |
| Seed/species | Yes | 6 initial species: neutral IKK starts at 1; all other pools start at 0. |
| Observables | Yes | 6 species observables for active/neutral IKK, IkBa mRNA/protein, A20, and NFkB. |
| Functions | Yes | 3 rate functions for NFkB import/export and IkBa transport/removal. |
| Reaction rules | Yes | 14 ODE-style rules. |
| Actions | Yes | Network generation, `TR=0`, long steady-state ODE run, and concentration saving. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `k_1` | `0.00195` | TNF-gated activation rate for `IKK.st n→a`. |
| `k_deg` | `0.000107` | Basal IKK production/degradation rate. |
| `k_3` | `0.00145` | Extra loss term for active IKK. |
| `k_2` | `0.0357` | TNF-gated A20-mediated removal rate for active IKK. |
| `c_deg` | `0.000106` | A20 synthesis/degradation rate in this implementation. |
| `c_3a` | `0.000372` | IkBa mRNA transcription/degradation rate. |
| `c_4a` | `0.00313` | IkBa protein translation rate from IkBa mRNA. |
| `c_5a` | `0.0000578` | IkBa degradation rate. |
| `a_3`, `delta`, `epsilon`, `i_1a`, `a_2` | fitted values | Parameters used inside NFkB import/export and IkBa transport functions. |
| `TR` | `0` | TNF input switch; active actions set it to 0 before steady-state simulation. |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `k_NFkBimport() = a_3*delta*(1-NFkB_n)/(IkBa+delta)` | Produces/imports `NFkB()` from active IKK; decreases as observable `NFkB_n` approaches 1 and depends inversely on `IkBa`. |
| `k_NFkBexport() = i_1a/(NFkB_n+epsilon)` | Removes the `NFkB()+IkBa()` pair; depends on current nuclear NFkB observable. |
| `k_IkBatransport() = a_2+(a_3*(1-NFkB_n))/(IkBa+delta)` | Removes `IkBa()` in the presence of active IKK; combines basal and NFkB/IkBa-dependent terms. |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `IKK` | 1 | `st` | `st~n~a` | none | `st` is the neutral/active switch. | This is the only declared site/state in the model. |
| `IkBa` | 0 | none | none | none | Whole-pool inhibitor species. | Comments label it cytoplasmic, but no compartment syntax is used. |
| `IkBa_mRNA` | 0 | none | none | none | Whole-pool transcript species. | Produced by NFkB and translated to IkBa. |
| `A20` | 0 | none | none | none | Whole-pool feedback species. | Removes active IKK in rule 11 while being preserved. |
| `NFkB` | 0 | none | none | none | Whole-pool nuclear NFkB readout. | Comments call it nuclear, but this is not a BNGL compartment. |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.
- Anchors: none declared.
- Initial setup: neutral IKK starts present; active IKK, IkBa, IkBa mRNA, A20, and NFkB start at zero.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `IKK(st~n)` | `1` | Initial neutral IKK pool. |
| `IKK(st~a)` | `0` | No active IKK initially. |
| `IkBa()` | `0` | No inhibitor protein initially. |
| `IkBa_mRNA()` | `0` | No transcript initially. |
| `A20()` | `0` | No feedback species initially. |
| `NFkB()` | `0` | No nuclear NFkB pool initially. |

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rule 1 is the only site-state conversion (`IKK.st n→a`). The remaining rules are source/sink or catalytic carry-through ODE terms for site-free pools. Rules with a species on both sides, such as `NFkB() -> NFkB() + A20()`, preserve the catalyst/readout species while producing another pool.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | `IKK.st` | `k_1*TR` | `IKK.st n→a`. | TNF-gated IKK activation; if `TR=0`, this activation term is zero. |
| 2 | `Unlabeled` | one-way | product `IKK.st~n` | `k_deg` | Source `0 → IKK(st~n)`. | Basal replenishment of neutral IKK. |
| 3 | `Unlabeled` | one-way | `IKK.st~a` | `k_deg+k_3` | Sink `IKK(st~a) → 0`. | Removes active IKK by basal plus active-specific degradation. |
| 4 | `Unlabeled` | one-way | `IKK.st~n` | `k_deg` | Sink `IKK(st~n) → 0`. | Basal neutral IKK degradation. |
| 5 | `Unlabeled` | one-way | `NFkB` preserved, `A20` produced | `c_deg` | `NFkB() → NFkB() + A20()`. | NFkB-driven A20 synthesis; `NFkB` is catalytic/preserved in the rule pattern. |
| 6 | `Unlabeled` | one-way | `A20` | `c_deg` | Sink `A20() → 0`. | A20 degradation. |
| 7 | `Unlabeled` | one-way | `NFkB` preserved, `IkBa_mRNA` produced | `c_3a` | `NFkB() → NFkB() + IkBa_mRNA()`. | NFkB-driven IkBa transcript production. |
| 8 | `Unlabeled` | one-way | `IkBa_mRNA` | `c_3a` | Sink `IkBa_mRNA() → 0`. | IkBa transcript degradation. |
| 9 | `Unlabeled` | one-way | `IkBa_mRNA` preserved, `IkBa` produced | `c_4a` | `IkBa_mRNA() → IkBa_mRNA() + IkBa()`. | Translation of IkBa protein from its mRNA. |
| 10 | `Unlabeled` | one-way | `IkBa` | `c_5a` | Sink `IkBa() → 0`. | IkBa protein degradation. |
| 11 | `Unlabeled` | one-way | `A20` preserved, `IKK.st~a` consumed | `k_2*TR` | `A20() + IKK(st~a) → A20()`. | A20-mediated active IKK removal; gated by TNF switch `TR`. |
| 12 | `Unlabeled` | one-way | `IKK.st~a` preserved, `NFkB` produced | `k_NFkBimport()` | `IKK(st~a) → IKK(st~a) + NFkB()`. | Active IKK drives NFkB production/import using a rate dependent on `NFkB_n` and `IkBa`. |
| 13 | `Unlabeled` | one-way | `NFkB` + `IkBa` | `k_NFkBexport()` | Sink `NFkB() + IkBa() → 0`. | IkBa-associated NFkB export/removal; both pools are removed by this pattern. |
| 14 | `Unlabeled` | one-way | `IKK.st~a` preserved, `IkBa` consumed | `k_IkBatransport()` | `IKK(st~a)+IkBa() → IKK(st~a)`. | Active IKK-associated IkBa removal/transport using the model’s combined basal/NFkB-dependent function. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `IKK_a` | `Species` | `IKK(st~a)` | Active IKK pool. |
| `tIkBa` | `Species` | `IkBa_mRNA()` | IkBa transcript pool. |
| `A20` | `Species` | `A20()` | A20 feedback species. |
| `NFkB_n` | `Species` | `NFkB()` | Nuclear NFkB pool used by functions. |
| `IkBa` | `Species` | `IkBa()` | IkBa inhibitor protein pool used by functions. |
| `IKK_n` | `Species` | `IKK(st~n)` | Neutral IKK pool. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1});` builds the reaction network.
2. `setParameter("TR",0);` explicitly keeps TNF input off for the active simulation.
3. `simulate_ode({suffix=>"continuous", t_end=>30*24*3600, ... steady_state=>1});` runs a long ODE simulation to steady state.
4. `saveConcentrations()` writes concentration outputs.

## 9. Technical caveats and ambiguities

- The YAML description says T-cell discrimination, but the BNGL file text describes canonical NF-kappaB signaling; this summary follows the BNGL file.
- Comments label NFkB as nuclear and IkBa/A20 as cytoplasmic, but there are no BNGL compartments or anchors.
- Many pulse protocols are commented/auto-disabled; the active workflow is the continuous steady-state run with `TR=0`.
