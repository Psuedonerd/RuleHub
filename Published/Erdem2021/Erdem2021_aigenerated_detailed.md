# Detailed Model Explanation: Erdem 2021 InsR/IGF1R signaling model

## 1. Model overview

This model represents shared signaling from insulin and IGF1 receptors into Ras–RAF–MEK–ERK and IRS–PI3K–PDK1–AKT–TSC2–mTOR–RPS6K cascades. It emphasizes cross-pathway negative feedback, recovery from inhibited states, and ligand-driven receptor internalization and recycling rather than explicit multiprotein complex assembly.

## 2. BNGL block inventory

The model contains 66 parameters, 16 molecule types, 16 seed species, 48 reaction rules, four species-count observables, and three actions: network generation, ODE simulation, and LaTeX export. It has no functions, compartments, or anchors.

## 3. Parameters, functions, and rate laws

Sixteen `_0` parameters specify initial molecular populations. The remaining `kf` values are base-10 logarithms: every reaction rate is evaluated as `10^kf...`, so differences of one parameter unit represent tenfold kinetic changes rather than additive changes.

| Parameter group or names | Function in this model |
| --- | --- |
| `IGF1_0`, `INS_0`; `IGF1R_0`, `INSR_0` | Set ligand and receptor pools. IGF1 is present initially at 100,000 molecules, whereas insulin starts at zero, making the encoded run an IGF1-only stimulation unless parameters are changed. |
| `IRS_0`, `SOS_0`, `RAS_0`, `RAF_0`, `MEK_0`, `ERK_0` | Initialize the adaptor and MAPK branch in inactive, uninhibited states. |
| `PI3K_0`, `PDK1_0`, `AKT_0`, `TSC2_0`, `MTOR_0`, `RPS6K_0` | Initialize the PI3K/AKT/mTOR branch; TSC2 begins unphosphorylated and mTOR inactive. |
| `kf1`, `kf1b`, `kf1c`, `kf1d` | Control IGF1–IGF1R association/dissociation, receptor phosphorylation, and ligand-loss/receptor-reset. |
| `kf2`, `kf2b`, `kf2c`, `kf2d` | Provide the analogous four rates for insulin and InsR. |
| `kf3`–`kf6` | Set receptor-specific catalytic activation of IRS and SOS by phosphorylated IGF1R or InsR. |
| `kf7`–`kf11` | Propagate the MAPK arm from IRS-to-SOS and SOS-to-Ras, then through Raf, MEK, and ERK. |
| `kf12`–`kf17` | Propagate the metabolic arm from IRS through PI3K, PDK1, Akt, inhibitory phosphorylation of TSC2, mTOR, and RPS6K. |
| `kf101`–`kf112` | Reset activated pathway nodes. The sequence covers IRS, SOS, Ras, Raf, MEK, PI3K, PDK1, TSC2, mTOR, Akt, RPS6K, and ERK, but not receptor states. |
| `kf201`–`kf204`, `kf206`–`kf208` | Set seven feedback processes: ERK inhibits SOS, MEK, IRS, and Akt; RPS6K and Akt inhibit IRS; Akt also inhibits Raf. |
| `kf301`–`kf304` | Restore IRS, SOS, Raf, and MEK from inhibited to responsive states. |
| `kf401`–`kf404` | Control internalization and recycling of ligand-bound phosphorylated IGF1R and InsR. |

There are no active functions; exponentiation is written directly in every rule's rate expression.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `IGF1`, `Ins` | 1 each | `rec` | None | None | Alternative extracellular inputs that bind their cognate receptors; only IGF1 is initially present. |
| `IGF1R`, `InsR` | 3 each | `lig`, `phos`, `int` | `phos`: `U`, `P`; `int`: surface/not internalized `N`, internalized `Y` | None | Cognate receptors with explicit ligand binding, phosphorylation, and internalization state. |
| `IRS` | 2 | `phos`, `inh` | `phos`: `U`, `P`; `inh`: `N`, `Y` | None | Shared receptor substrate that activates both SOS and PI3K and receives three feedback inputs. |
| `SOS` | 2 | `act`, `inh` | Both: `N`, `Y` | None | Ras exchange-factor abstraction activated by receptors or IRS and inhibited by ERK. |
| `Ras` | 1 | `gtp` | `N`, `Y` | None | Binary Ras switch activated by SOS and reset by intrinsic/background turnover. |
| `Raf`, `MEK` | 2 each | `phos`, `inh` | `phos`: `U`, `P`; `inh`: `N`, `Y` | None | Sequential MAPK kinases whose activation is phosphorylation-like and whose inhibition is tracked separately. |
| `ERK` | 1 | `phos` | `U`, `P` | None | Terminal MAPK output and feedback regulator of SOS, MEK, IRS, and Akt. |
| `PI3K`, `PDK1`, `mTOR` | 1 each | `act` | `N`, `Y` | None | Binary active/inactive intermediates transmitting IRS input toward Akt and mTOR output. |
| `Akt`, `TSC2`, `RPS6K` | 1 each | `phos` | `U`, `P` | None | Akt transmits PDK1 input, phosphorylated TSC2 permits mTOR activation, and phosphorylated RPS6K is the branch output and an IRS feedback regulator. |

## 5. Compartments, anchors, initial species, and setup

The model is spatially implicit and starts every protein free, inactive or unphosphorylated, uninhibited, and—where applicable—not internalized. IGF1 begins at 100,000 molecules and insulin at zero, while both receptor types begin at 25,000; therefore, the embedded simulation probes IGF1R signaling with an unstimulated insulin receptor pool. Downstream abundances vary substantially, with MEK exceeding one million molecules and PI3K being one of the smaller pools, so depletion and relative pool size can shape the trajectories even though catalysts are carried through rules.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–21 transmit ligand input through the two receptor and downstream kinase branches. Rules 22–33 reset active states, rules 34–40 impose cross-pathway negative feedback, rules 41–44 restore responsiveness, and rules 45–48 internalize and recycle receptors.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–3 | Mixed | IGF1 `rec`; surface IGF1R `lig`, `phos`, `int` | Rule 1 reversibly forms the ligand–receptor bond at `10^kf1`/`10^kf1b`; rule 2 phosphorylates bound receptor at `10^kf1c`; rule 3 removes ligand while resetting receptor phosphorylation at `10^kf1d`. | Converts IGF1 exposure into a transient phosphorylated IGF1R population. |
| 4–6 | Mixed | Ins `rec`; surface InsR `lig`, `phos`, `int` | Repeats binding, bound-receptor phosphorylation, and ligand-loss/reset for insulin using `kf2`, `kf2b`, `kf2c`, and `kf2d`. | Provides a parallel insulin input, dormant under the default zero-insulin setup. |
| 7–8 | One-way | Phosphorylated surface IGF1R or InsR; responsive IRS `phos~U,inh~N` | Catalytically changes IRS phosphorylation from `U` to `P`; IGF1R uses `10^kf3`, InsR `10^kf4`. | Merges both receptor inputs into the IRS branch. |
| 9–10 | One-way | Phosphorylated surface receptor; responsive inactive SOS | Catalytically changes SOS `act` from `N` to `Y`; IGF1R uses `10^kf5`, InsR the much faster `10^kf6`. | Supplies a receptor-direct route into Ras/MAPK signaling. |
| 11–15 | One-way | IRS pY; SOS; Ras; Raf; MEK; ERK | Rule 11 activates SOS through IRS, then rules 12–15 change Ras GTP, Raf phosphorylation, MEK phosphorylation, and ERK phosphorylation to their active states using `kf7`–`kf11`, respectively. | Implements the forward MAPK cascade with catalytic carry-through at every step. |
| 16–21 | One-way | IRS pY; PI3K; PDK1; Akt; TSC2; mTOR; RPS6K | Rules 16–18 activate PI3K, PDK1, and Akt; rule 19 phosphorylates TSC2, rule 20 activates mTOR only from that TSC2 state, and rule 21 phosphorylates RPS6K. Rates use `kf12`–`kf17` in order. | Implements the PI3K/AKT/mTOR branch and produces the pRPS6K output. |
| 22–33 | One-way | IRS, SOS, Ras, Raf, MEK, PI3K, PDK1, TSC2, mTOR, Akt, RPS6K, ERK active sites | Each rule independently returns one active/phosphorylated state to inactive/unphosphorylated using `10^kf101` through `10^kf112` in the listed order. | Provides basal signal termination for every downstream forward-pathway node. |
| 34 | One-way | ERK pY; inactive, responsive SOS | Changes SOS inhibition from `N` to `Y` while leaving its activity `N`. | ERK suppresses renewed Ras activation upstream of itself. |
| 35 | One-way | ERK pY; unphosphorylated responsive MEK | Changes MEK inhibition from `N` to `Y`. | Adds direct terminal-to-intermediate feedback within the MAPK cascade. |
| 36, 38, 40 | One-way | Responsive unphosphorylated IRS; RPS6K pY (36), ERK pY (38), or Akt pY (40) | Each active kinase changes IRS inhibition from `N` to `Y` at its own `kf20...` rate. | Makes IRS a convergence point for negative feedback from both downstream branches. |
| 37 | One-way | Akt pY; unphosphorylated responsive Raf | Changes Raf inhibition from `N` to `Y`. | Allows the PI3K/Akt branch to suppress MAPK transmission. |
| 39 | One-way | ERK pY; Akt pY | Changes Akt from phosphorylated to unphosphorylated at `10^kf207`, with ERK unchanged. | Lets MAPK output directly reduce Akt activity. |
| 41–44 | One-way | Inhibited IRS, SOS, Raf, or MEK | Changes each `inh` state from `Y` back to `N` using `kf301`–`kf304`, respectively, without changing activation/phosphorylation. | Restores pathway responsiveness after feedback inhibition. |
| 45–46 | One-way | Ligand-bound phosphorylated IGF1R `int`; IGF1 | Rule 45 changes receptor internalization from `N` to `Y`; rule 46 removes the internalized ligand–receptor complex and creates a free, surface, unphosphorylated receptor, with no free IGF1 product. | Terminates IGF1 signaling and recycles IGF1R while consuming bound ligand. |
| 47–48 | One-way | Ligand-bound phosphorylated InsR `int`; insulin | Repeats internalization and ligand-consuming receptor reset for InsR using `kf403` and `kf404`. | Applies the same trafficking logic to the insulin input. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `pRecTot_free` | Species count | Sum of noninternalized phosphorylated IGF1R and InsR species, with ligand occupancy unconstrained. | Pools the two receptors into one surface activation readout; as a species observable, it counts matching chemical species rather than molecule embeddings. |
| `pAkt308_free` | Species count | Species containing phosphorylated Akt. | Represents the model's single Akt phosphorylation state; the name suggests T308, but the molecule type does not encode a residue number. |
| `pRPS6K_free` | Species count | Species containing phosphorylated RPS6K. | Terminal readout of the modeled mTOR branch. |
| `pERK_free` | Species count | Species containing phosphorylated ERK. | Terminal MAPK readout and the controller of several negative-feedback rules. |

## 8. Actions and simulation workflow

The model first generates the full reaction network, then integrates it deterministically with ODEs from time 0 to 1800 using 20,000 requested steps. After simulation it writes a LaTeX representation of the generated model; there is no equilibration, dose change, or parameter scan in the embedded workflow.

## 9. Technical caveats and ambiguities

- Every kinetic parameter is a base-10 exponent. Reading the stored negative numbers as direct rates would reverse their intended scale by many orders of magnitude.
- The default experiment contains IGF1 but no insulin, even though both receptor branches are fully encoded; comparing ligands requires changing `INS_0` and likely `IGF1_0` externally.
- The model uses abstract binary state changes and catalytic carry-through rather than explicit recruitment complexes for downstream signaling, so it should not be read as a stoichiometric interaction map.
- Receptor recycling consumes bound ligand because the ligand is omitted from the products of rules 46 and 48. This is a modeled degradation/removal event, not dissociation back to the free ligand pool.
- Metadata marks the model as not BNG2- or NFsim-compatible despite its embedded network-generation and ODE actions; the intended parser/runtime version should be verified before execution.
