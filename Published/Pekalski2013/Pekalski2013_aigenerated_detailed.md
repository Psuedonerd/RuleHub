# Detailed Model Explanation: Pekalski 2013 Spontaneous TNF–NF-κB Signaling

## 1. Model overview

This model couples tumor necrosis factor (TNF) receptor activation to an IKKK–IKK kinase relay and nuclear factor κB (NF-κB) control of TNF, A20, and IκBα gene expression. Its feedback architecture combines self-amplifying TNF production with A20-mediated signal restraint and IκBα-mediated sequestration and export of NF-κB.

## 2. BNGL block inventory

The file contains 42 parameters, 14 molecule types, 29 seed species, 4 functions, 40 reaction rules, 29 observables, and 4 actions. There are no explicit compartments or anchors; localization is encoded by internal `loc` states.

## 3. Parameters, functions, and rate laws

The namespace separates receptor/kinase activation, binary gene switching, expression and turnover, binding/phosphorylation, and nucleocytoplasmic transport. Most rules are one-way mass-action transitions; four observable-dependent functions make receptor and kinase activation state dependent, and two derived rates combine base parameters algebraically.

| Parameter group or names | Function in this model |
| --- | --- |
| `R`, `K_N`, `K_NN`, `NFkB_tot`, `k_v` | Define initial receptor, kinase, and NF-κB pools plus the nuclear/cytoplasmic volume scaling used in nuclear NF-κB–IκBα association. |
| `c_deg`, `k_b`, `c_sec`, `c_b`, `k_f` | Control extracellular TNF removal, external or internal TNF-driven receptor activation, and receptor return to the inactive state. |
| `k_a`, `k_A20`, `k_i`, `k_1`–`k_4` | Drive the IKKK–IKK relay and its recovery cycle; A20 enters the calculated IKKK and IKK transition rates. |
| `q_1`, `q_2`, `q_1t`, `q_2t`, `q_2tt` | Switch A20, IκBα, and TNF gene copies on or off in response to nuclear NF-κB or IκBα, including autonomous TNF-gene shutoff. |
| `lambda`, `c_1`, `c_3`, `c_3t`, `c_4`, `c_4t` | Set transcription, transcript decay, and translation for the three feedback products. |
| `a_1`, `a_2`, `a_3`, `k_NFkBIkB`, `t_p`, `c_6a` | Govern NF-κB–IκBα association, IKK-catalyzed IκBα phosphorylation, and loss of free or NF-κB-bound IκBα. |
| `c_5`, `c_5a`, `c_5t`, `k_TNFdeg` | Set turnover of A20, unphosphorylated IκBα, and internal TNF; `k_TNFdeg` combines secretion and intracellular loss. |
| `i_1`, `i_1a`, `e_1a`, `e_2a` | Control nuclear import of free NF-κB and IκBα, export of free IκBα, and export of the nuclear NF-κB–IκBα complex. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `k_Ractivation` | Inactive-receptor observable `TNFR_i`; `c_sec`, `c_b` | Makes internal-TNF receptor activation inversely dependent on the current inactive receptor pool. |
| `k_IKKKactivation` | Active receptor `TNFR_a`, A20; `k_a`, `k_A20` | Converts receptor activity into IKKK activation while applying an A20-dependent saturating factor. |
| `k_IKKactivation` | Active IKKK `IKKK_a`; `k_1` | Uses the square of active IKKK, making IKK activation strongly nonlinear. |
| `k_IKKintermetiation` | A20; `k_2`, `k_3` | Sets active IKK entry into its inactive intermediate and increases that transition with A20 abundance. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `TNFR` | 1 | `st` | active (`a`), inactive (`i`) | None | Lumped TNF receptor whose activity feeds the kinase cascade. |
| `IKKK` | 1 | `st` | neutral (`n`), active (`a`) | None | Upstream kinase activated from the receptor/A20-dependent function. |
| `IKK` | 1 | `st` | neutral (`n`), active (`a`), inactive (`i`), inactive intermediate (`ii`) | None | Kinase that phosphorylates IκBα and then traverses a two-step refractory cycle. |
| `NFkB` | 2 | `loc`, `bin` | `loc`: nuclear (`n`) or cytoplasmic (`c`) | None | Transcriptional regulator whose free nuclear form switches feedback genes on. |
| `IkBa` | 3 | `loc`, `pho`, `bin` | `loc`: `n`/`c`; `pho`: unphosphorylated (`0`) or phosphorylated (`p`) | None | NF-κB inhibitor; binding, phosphorylation, and transport determine NF-κB availability. |
| `TNF` | 1 | `loc` | extracellular (`e`), intracellular (`i`) | None | Secreted stimulus and transcriptional feedback product. |
| `GA20`, `GIkBa`, `GTNF` | 1 each | `st` | off (`0`), on (`1`) | None | Two-state gene copies that gate production of their respective transcripts. |
| `A20_mRNA`, `IkBa_mRNA`, `TNF_mRNA` | 0 each | None | None | None | Transcript pools connecting gene state to protein production. |
| `A20` | 0 | None | None | None | Negative-feedback regulator of the receptor-to-IKK relay. |
| `Trash` | 0 | None | None | None | Sink for extracellular ligand, transcripts, and degraded proteins. |

## 5. Compartments, anchors, initial species, and setup

No geometrical compartments are declared. Nuclear and cytoplasmic location is carried by NF-κB and IκBα states, whereas TNF distinguishes intracellular from extracellular pools. The initial condition places the receptor and kinases predominantly in inactive/neutral states, seeds cytoplasmic NF-κB bound to unphosphorylated IκBα, supplies basal A20 and transcript pools, and initializes two off copies of each regulated gene. Extracellular TNF initially vanishes; it is introduced later by an action.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–10 transmit TNF input through the receptor and kinase relay, 11–26 implement gene-state feedback and expression, 27–36 control NF-κB–IκBα chemistry and protein turnover, and 37–40 move free or inhibited regulators between nuclear and cytoplasmic states.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | Extracellular `TNF.loc=e` | Removes TNF to `Trash` at `c_deg`. | Limits the duration of extracellular stimulation. |
| 2–4 | One-way | `TNFR.st`; external or internal `TNF.loc` | Rules 2 and 3 change inactive receptor to active without consuming TNF, using `k_b` and `k_Ractivation`; rule 4 resets active receptor at `k_f`. | Converts either TNF pool into transient receptor activity. |
| 5–6 | One-way | `IKKK.st` | Neutral IKKK becomes active at receptor/A20-dependent `k_IKKKactivation`, then returns at `k_i`. | Creates the first reversible-in-effect stage of the kinase pulse. |
| 7–10 | One-way | `IKK.st` | Neutral IKK activates at quadratic `k_IKKactivation`; active IKK enters `i` through the A20-sensitive function, then passes `i→ii→n` at `k_4`. | Produces active IKK while enforcing a refractory recovery path. |
| 11–16 | One-way | Free nuclear `NFkB` or IκBα; gene `st` | NF-κB switches A20/IκBα/TNF genes `0→1` (11,12,15); nuclear IκBα switches them `1→0` (13,14,16). Regulators are catalytic and retained. | Opposes NF-κB-driven transcription with an inhibitor-dependent gene shutoff mechanism. |
| 17 | One-way | `GTNF.st=1` | Turns the active TNF gene off at `q_2tt` without requiring IκBα. | Adds an intrinsic limit to the TNF transcriptional episode. |
| 18–20 | One-way | Active TNF, A20, or IκBα gene | Retains the on-state gene and creates its transcript at `lambda` (TNF) or `c_1` (A20/IκBα). | Converts discrete gene activation into continuous transcript production. |
| 21–26 | One-way | Three mRNAs and their protein products | A20 and IκBα transcripts decay at `c_3` and translate at `c_4`; TNF mRNA decays at `c_3t` and creates internal TNF at `c_4t`. | Implements expression kinetics for positive and negative feedback arms. |
| 27–28 | One-way | `NFkB.bin`, unphosphorylated `IkBa.bin`; matched location | Creates the inhibitor bond in cytoplasm at `a_1` or nucleus at volume-scaled `k_NFkBIkB`. | Sequesters free NF-κB in either location. |
| 29–30 | One-way | Active `IKK`; free or NF-κB-bound cytoplasmic `IkBa.pho` | Changes IκBα phosphorylation `0→p` at `a_2` (free) or `a_3` (bound), retaining IKK and any NF-κB bond. | Marks the inhibitor for removal while preserving catalytic IKK. |
| 31–36 | One-way | A20, free/bound IκBα, internal TNF | Removes A20 (31), phosphorylated free IκBα (32), bound phosphorylated IκBα while releasing NF-κB (33), unphosphorylated IκBα (34), internal TNF (35), or bound unphosphorylated IκBα while releasing NF-κB (36), each at its named turnover rate. | Sets feedback lifetimes and regenerates free NF-κB when its inhibitor is lost. |
| 37–39 | One-way | Free `NFkB.loc` or unphosphorylated free `IkBa.loc` | NF-κB imports `c→n` at `i_1`; IκBα imports at `i_1a` and exports at `e_1a`. | Supplies nuclear NF-κB for gene activation and nuclear IκBα for shutoff. |
| 40 | One-way | Nuclear NF-κB–IκBα complex | Changes both partners from nuclear to cytoplasmic while retaining their bond, at `e_2a`. | Removes inhibited NF-κB from the nucleus as a complex. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `TNFR_a`, `TNFR_i`; `IKKK_a`; `IKK_a`, `IKK_n`, `IKK_i` | Species count | Receptor and kinase state-specific species. | Resolve signal propagation and IKK recovery; `IKK_i` does not include the separate `ii` state. |
| `NFkB_nuc`, `NFkB_cyt` | Species count | Free NF-κB in each encoded location. | Measure transcriptionally available versus cytoplasmic NF-κB rather than total NF-κB. |
| `NFkB_IkBa_p_cyt`, `NFkB_IkBa_u_cyt`, `NFkB_IkBa_u_nuc` | Species count | Location- and phosphorylation-specific NF-κB–IκBα complexes. | Distinguish inhibited complexes from the phosphorylated complex poised for IκBα loss. |
| `IkBa_p_cyt`, `IkBa_u_cyt`, `IkBa_u_nuc` | Species count | Free IκBα states and locations. | Track inhibitor availability outside complexes. |
| `TNF_ext`, `TNF_int`, `A20` | Species count | The two TNF pools and A20 protein. | Report the positive feedback signal and its receptor-pathway antagonist. |
| `tA20`, `tIkB`, `tTNF` | Species count | Each feedback transcript. | Separate transcriptional responses from downstream protein abundance. |
| `gA20_a/i`, `gIkBa_a/i`, `gTNF_a/i` | Species count | On and off gene-copy states. | Expose the binary switching layer directly. |
| `IKK_tot_`, `IKKK_tot_`, `NFkB_tot_` | Molecule count | Each molecule across internal states, locations, and binding contexts. | Conservation checks that can be compared with the corresponding state-resolved observables. |

## 8. Actions and simulation workflow

The model first generates a reaction network and integrates its ordinary differential equations for 300 hours to establish an unstimulated trajectory. It then sets extracellular TNF to one unit and continues the same system for 10 hours, producing separate pre-stimulus and post-stimulus output suffixes.

## 9. Technical caveats and ambiguities

- “Spontaneous signaling” is represented by state-dependent activation functions and basal initialized pools; no stochastic simulation is used.
- Localization states substitute for physical compartments, so nuclear/cytoplasmic volume effects enter only where explicitly encoded, notably `k_NFkBIkB`.
- Several observables use `Species`, whereas the three totals use `Molecules`; their numerical meanings differ when complexes are present.
- The two inactive IKK states (`i` and `ii`) form a sequence, but only `i` has a dedicated observable.
