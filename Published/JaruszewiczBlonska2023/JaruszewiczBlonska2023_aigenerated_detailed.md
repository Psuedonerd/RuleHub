# Detailed Model Explanation: Jaruszewicz-Blonska 2023 canonical NF-κB feedback model

## 1. Model overview

This reduced canonical NF-κB model converts a binary TNF-receptor input into IKK activation, nuclear NF-κB production, and induction of the inhibitors IκBα and A20. A20 suppresses active IKK, while IκBα removes nuclear NF-κB and is itself degraded by active IKK, creating coupled negative-feedback loops.

## 2. BNGL block inventory

The file contains 14 active parameters, 5 molecule types, 6 seed declarations, 6 species-count observables, 3 functions, 14 one-way rules, and 4 active actions. It has no compartments or anchors; extensive stimulation protocols are present only as disabled comments.

## 3. Parameters, functions, and rate laws

The model uses lumped first-order production/removal constants plus three observable-dependent functions. `TR` is a binary stimulus switch, and the nonlinear transport functions make NF-κB/IκBα turnover depend on their current observable levels.

| Parameter group or names | Function in this model |
| --- | --- |
| `TR`, `k_1`, `k_3`, `k_deg` | TNF input and IKK lifecycle: stimulus-dependent activation, extra loss of active IKK, and basal creation/removal. |
| `k_2` | A20-mediated removal of active IKK, gated by `TR` in the rule rate. |
| `c_deg` | Shared A20 production and degradation rate, making NF-κB-driven synthesis and turnover symmetric in this reduced representation. |
| `c_3a`, `c_4a`, `c_5a` | IκBα mRNA production/decay, translation, and protein decay. The same `c_3a` controls transcript birth and death. |
| `a_3`, `delta`, `epsilon`, `a_2`, `i_1a` | Shape the three nonlinear NF-κB import/export and IκBα-removal functions, including saturation offsets and basal IκBα transport. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `k_NFkBimport` | Nuclear NF-κB `NFkB_n`, cytoplasmic IκBα `IkBa`, plus `a_3` and `delta` | Decreases as nuclear NF-κB approaches its normalized ceiling and as IκBα rises; used by active IKK to produce nuclear NF-κB in rule 12. |
| `k_NFkBexport` | `NFkB_n`, `i_1a`, `epsilon` | Per-pair removal rate for NF-κB plus IκBα; the denominator slows the rate as nuclear NF-κB increases. Used in rule 13. |
| `k_IkBatransport` | `NFkB_n`, `IkBa`, `a_2`, `a_3`, `delta` | Combines basal and NF-κB-dependent removal of IκBα by active IKK. Used in rule 14. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `IKK` | 1 | `st` | `n, a` | None | Kinase pool switching between neutral and active states; active IKK releases NF-κB and removes IκBα. |
| `IkBa` | 0 | None | None | None | Lumped cytoplasmic IκBα inhibitor; binding is not explicit, so its action appears through joint-removal rules and rate functions. |
| `IkBa_mRNA` | 0 | None | None | None | Transcript induced by NF-κB and translated into IκBα. |
| `A20` | 0 | None | None | None | NF-κB-induced negative regulator that catalytically removes active IKK. |
| `NFkB` | 0 | None | None | None | Lumped nuclear NF-κB output; localization is encoded by molecule identity/observable, not a compartment or internal state. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and starts with one neutral IKK molecule; active IKK, NF-κB, IκBα, its transcript, and A20 all start at zero. `TR` is initialized to 0, so the active workflow first seeks the unstimulated steady state. The source normalizes several feedback expressions around unit-scale NF-κB rather than representing explicit molecular binding or transport compartments.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–4 maintain the IKK pool and couple it to TNF input. Rules 5–10 implement NF-κB-dependent A20 and IκBα expression, while rules 11–14 close the feedback loops by removing active IKK, producing NF-κB, and clearing NF-κB/IκBα.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | Neutral `IKK.st~n` | Changes `IKK.st: n → a` at `k_1*TR`. | Converts the binary TNF input into kinase activation; no activation occurs when `TR=0`. |
| 2 | One-way | Source `0` | Creates neutral IKK at `k_deg`. | Replenishes the IKK pool lost through rules 3, 4, and 11. |
| 3 | One-way | Active `IKK.st~a` | Removes active IKK to sink `0` at `k_deg+k_3`. | Gives active IKK both basal and activation-specific turnover. |
| 4 | One-way | Neutral `IKK.st~n` | Removes neutral IKK at `k_deg`. | Balances constitutive neutral-IKK production in the absence of signaling. |
| 5–6 | One-way | Nuclear NF-κB in rule 5; A20 in rule 6 | NF-κB catalytically creates A20, while A20 is independently removed; both rates are `c_deg`. | Establishes an NF-κB-induced A20 pool with matched production and decay scales. |
| 7–8 | One-way | Nuclear NF-κB in rule 7; IκBα mRNA in rule 8 | NF-κB catalytically creates `IkBa_mRNA`, and the transcript decays; both use `c_3a`. | Creates the transcript stage of delayed IκBα feedback. |
| 9–10 | One-way | IκBα mRNA in rule 9; IκBα protein in rule 10 | The transcript is retained while producing IκBα at `c_4a`; IκBα decays at `c_5a`. | Converts transcription into a transient inhibitor pool whose lifetime is independent of its mRNA. |
| 11 | One-way | A20 and active IKK | Removes active IKK while retaining A20, at `k_2*TR`. | Implements catalytic A20 feedback on the stimulus-driven IKK branch. |
| 12 | One-way | Active IKK | Retains active IKK and creates NF-κB at `k_NFkBimport()`. | Represents IKK-dependent release/import of NF-κB with feedback from current NF-κB and IκBα levels. |
| 13 | One-way | NF-κB and IκBα | Removes one of each at `k_NFkBexport()`. | Lumped resequestration/export: newly made IκBα terminates nuclear NF-κB while being consumed in the event. |
| 14 | One-way | Active IKK and IκBα | Removes IκBα while retaining active IKK, at `k_IkBatransport()`. | Represents IKK-driven inhibitor clearance, opposing IκBα feedback and permitting renewed NF-κB production. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `IKK_a`, `IKK_n` | Species count | Active and neutral IKK species | Partition of the kinase pool used to track stimulus response and recovery. |
| `tIkBa` | Species count | IκBα mRNA | Transcriptional-feedback intermediate upstream of IκBα protein. |
| `IkBa` | Species count | IκBα protein | Inhibitor level used directly by all three nonlinear functions. |
| `A20` | Species count | A20 protein | Strength of the IKK-targeting feedback arm. |
| `NFkB_n` | Species count | Nuclear NF-κB | Primary signaling output and input to A20/IκBα production and transport functions. |

## 8. Actions and simulation workflow

The active workflow generates the network, forces `TR=0`, and performs a 30-day sparse ODE steady-state run with 200 output steps before saving concentrations. All continuous-stimulation, pulse, and A20-knockout protocols below that point are commented or auto-disabled, so they describe intended experiments but are not executed by the checked-in file.

## 9. Technical caveats and ambiguities

- Metadata labels the model “T-cell discrimination,” whereas the BNGL header and mechanism describe a reduced canonical NF-κB pathway.
- Localization is conceptual: there are no compartments, and `NFkB` specifically represents the nuclear pool while `IkBa` represents cytoplasmic inhibitor.
- Rules 13 and 14 consume IκBα rather than representing explicit shuttling, binding, phosphorylation, and degradation intermediates.
- `TR` also gates A20-mediated IKK removal, so A20 cannot clear active IKK through rule 11 when stimulus is off.
- The active steady-state action repeats the `sparse` argument and uses extremely tight tolerances, which may be solver- or parser-sensitive.
