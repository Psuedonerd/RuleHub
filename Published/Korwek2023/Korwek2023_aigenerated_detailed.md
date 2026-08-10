# Detailed Model Explanation: Korwek 2023 Antiviral Innate-Immune Signaling

## 1. Model overview

This model follows cytosolic poly(I:C) recognition through RIG-I/MAVS and couples it to PKR–eIF2α translational inhibition, OAS3–RNase L RNA decay, NF-κB and IRF3 activation, interferon-β production, and IFNAR–STAT1/STAT2 feedback. The resulting network contains both antiviral amplification—through interferon-stimulated gene expression—and self-limitation through A20, IκBα, transcript degradation, and protein turnover.

## 2. BNGL block inventory

The model contains 93 parameters, 29 molecule types, 30 seed species, 83 logical reaction rules, 42 declared observables (53 physical lines because several patterns continue), and 7 actions. There are no functions, compartments, or anchors; extracellular, cytoplasmic, and nuclear locations are encoded as molecule states.

## 3. Parameters, functions, and rate laws

Parameter prefixes form a deliberate namespace: `a/d` activate or deactivate, `b/u` bind or unbind, `i/e` import or export, `p/q` phosphorylate or dephosphorylate, `t/s/g` control transcription, translation, or degradation, and `m` denotes saturation constants. Rules combine mass action with observable-dependent rational expressions; RNase L accelerates transcript loss, phosphorylated eIF2α suppresses translation, and STAT1/2 dimers, NF-κB, and IRF3 provide saturating transcriptional inputs.

| Parameter group or names | Function in this model |
| --- | --- |
| Cell and pool parameters (`n_*`, volume/scaling terms) | Establish initial antiviral proteins, NF-κB components, interferon machinery, and extracellular/cytoplasmic stimulus pools. |
| `n_IFNb_stimulation`, `n_polyIC_stimulation` | Define the two sequential experimental perturbations applied by actions after equilibration. |
| Poly(I:C)/RIG-I/MAVS rates (`i_Polyic`, `b_Rigi_Polyic`, `b_RigiPolyic_Mavs`, `sg_Rigi`) | Import poly(I:C), assemble the sensing complex, and turn over RIG-I while releasing ligand and MAVS. |
| `a_Pkr_by_Polyic`, `d_Pkr`, `a_Oas3_by_Polyic`, `d_Oas3`, `a_Rnasel_by_Oas3`, `d_Rnasel` | Activate and reset the PKR and OAS3/RNase L antiviral effector branches. |
| `p_Eif2a_by_Pkr`, `p_Eif2a_basal`, `q_Eif2a`, `m_Eif2a` | Set eIF2α phosphorylation and its inhibitory effect on translation rates. |
| ISG transcription/turnover terms (`tg_Isg_mrna`, `ma_*_gene_basal`, `a_gene_by_Stat12dim`, `m_Rnasel`, `h_*`) | Produce RIG-I, PKR, OAS3, and RNase L transcripts from basal and STAT-dimer inputs, apply knockout switches, and accelerate their decay through active RNase L. |
| TAK1/IKK terms (`a_Tak1_by_*`, `d_Tak1`, `a_Ikk`, `d_Ikk_1`–`d_Ikk_3`) | Connect RIG-I/MAVS or TNFα to nonlinear IKK activation and an A20-sensitive refractory cycle. |
| NF-κB/IκBα/A20 terms (`b_Nfkb_Ikba_*`, `p_Ikba_by_Ikk`, `g_Ikba_*`, `i_Nfkb`, `e_Nfkb_with_Ikba`, `i/e_Ikba`, `tg_*_mrna`, `a/d_*_gene`, `s_Ikba`, `sg_A20`) | Control sequestration, IκBα phosphorylation/removal, transport, feedback-gene expression, and A20 turnover. |
| TBK1/IRF3 terms (`p_Tbk1_by_RigiMavs`, `q_Tbk1`, `q_Tbk1_by_A20`, `p_Irf3_by_Tbk1`, `q_Irf3`) | Drive and restrain the second transcription-factor arm downstream of RIG-I/MAVS. |
| IFNβ/IFNAR terms (`b_Ifnar_Ifnb_*`, `tg_Ifnar_mrna`, `s/g_Ifnar*`, `tg_Ifnb_mrna`, `sg_Ifnb`, `m_Ifnb_mrna_NfkbIrf3`) | Implement receptor binding, receptor synthesis/turnover, cooperative NF-κB–IRF3 interferon transcription, and interferon production/removal. |
| STAT terms (`p_Stat`, `q_Stat`, `m_Ifnar_a`, `b/qu_Stat1_Stat2`, `tg_Stat_mrna`, `sg_Stat`, `ma_Stat*_gene_basal`) | Phosphorylate STAT1/2 in response to occupied IFNAR, form and reset the heterodimer, and induce STAT expression. |

There are no active functions; all nonlinear regulation is written directly in reaction-rate expressions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `PolyIC`, `RIGI`, `MAVS` | 2; 2; 1 | PolyIC: `Rigi`, `loc`; RIGI: `Polyic`, `Mavs`; MAVS: `Rigi` | PolyIC location `ext/cyt` | None | Synthetic RNA input and the two-component recognition scaffold that initiates TAK1 and TBK1 signaling. |
| `PKR`, `OAS3`, `RNaseL`, `eIF2a` | 1 each | `st`; `st`; `st`; `st` | first three `i/a`; eIF2α `0/p` | None | Antiviral effector switches controlling translation and RNase-L-dependent RNA loss. |
| `RIGI_mRNA`, `PKR_mRNA`, `OAS3_mRNA`, `RNaseL_mRNA` | 0 each | None | None | None | Interferon-stimulated transcripts that replenish the four antiviral proteins. |
| `TNFa`, `A20` | 0 each | None | None | None | TNFα provides an alternate TAK1 input; A20 suppresses IKK and TBK1 signaling. |
| `TAK1`, `IKK` | 1 each | `st` | TAK1 `i/a`; IKK `n/a/i/ii` | None | Sequential NF-κB-pathway kinase switches with an explicit IKK refractory cycle. |
| `IkBa`, `NFkB` | 3; 2 | IκBα: `Nfkb`, `loc`, `Ser32_Ser36`; NF-κB: `Ikba`, `loc` | locations `nuc/cyt`; IκBα sites `0/pp` | None | Inhibitor/transcription-factor pair whose binding, phosphorylation, degradation, and shuttling determine nuclear NF-κB. |
| `IkBa_mRNA`, `A20_mRNA` | 0 each | None | None | None | NF-κB feedback transcripts subject to RNase-L-enhanced decay and eIF2α-dependent translation. |
| `TBK1`, `IRF3` | 1 each | `Ser172`; `Ser396` | `0/p` | None | Kinase and transcription factor forming the interferon-induction branch. |
| `IFNAR`, `IFNb` | 1; 2 | IFNAR: `Ifnb`; IFNβ: `Ifnar`, `loc` | IFNβ location `ext/cyt` | None | Receptor/ligand pair coupling secreted or added interferon to STAT phosphorylation. |
| `IFNAR_mRNA`, `IFNb_mRNA` | 0 each | None | None | None | Transcripts for receptor replenishment and induced interferon production. |
| `STAT1`, `STAT2` | 2 each | reciprocal dimer site; Tyr701 or Tyr690 | phosphosite `0/p` | None | IFNAR-responsive factors that form the heterodimer driving antiviral-gene transcription. |
| `STAT1_mRNA`, `STAT2_mRNA` | 0 each | None | None | None | Positively regulated transcripts that reinforce the STAT pool. |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are used. Location states place the initial poly(I:C) and IFNβ stimuli outside the cell and distinguish nuclear from cytoplasmic NF-κB/IκBα; the seeded signaling proteins otherwise begin in inactive, unphosphorylated, or unbound forms. Basal mRNA and protein pools permit equilibration before either stimulus is added, while the staged actions later impose IFNβ first and poly(I:C) second.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–30 implement sensing and antiviral effectors; 31–55 form the NF-κB feedback module; 56–60 activate IRF3; 61–70 produce and sense IFNβ; and 71–83 close the STAT-driven interferon-stimulated-gene loop.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–5 | One-way | `PolyIC.loc/Rigi`, `RIGI.Polyic/Mavs`, `MAVS.Rigi` | Imports ligand `ext→cyt`, binds RIG-I, degrades ligand-bound RIG-I while releasing poly(I:C), recruits MAVS, and then removes RIG-I from the ternary complex while releasing both partners. | Creates a renewable ligand-driven RIG-I/MAVS signaling platform. |
| 6–14 | One-way | Cytoplasmic PolyIC; PKR/OAS3/RNaseL/eIF2α states | Poly(I:C) catalytically changes PKR and OAS3 `i→a`; PKR changes eIF2α `0→p`; OAS3 changes RNase L `i→a`; dedicated rules reset all states and add basal eIF2α phosphorylation. | Activates translational arrest and RNA degradation as parallel antiviral outputs. |
| 15–18 | One-way source | Four ISG mRNAs; `STAT12_dimer` | Creates each transcript with a bounded basal-plus-STAT-dimer expression; PKR and RNase L include gene-presence multipliers. | Converts interferon signaling into increased sensor/effector capacity. |
| 19–22 | One-way sink | Four ISG mRNAs; `RNaseL_a` | Removes every transcript at a common base rate multiplied by `(m_Rnasel+RNaseL_a)/m_Rnasel`. | Makes RNase L globally shorten antiviral-transcript lifetime. |
| 23–30 | One-way | Four mRNAs and proteins | Rules 23–26 retain each mRNA while creating inactive protein; 27–30 remove the corresponding protein at the same `sg_*` scale. | Balances replenishment and turnover of the sensing module. |
| 31–33 | One-way | RIG-I/MAVS complex or TNFα; `TAK1.st` | Either upstream signal changes TAK1 `i→a`; rule 33 returns it to inactive. | Merges RNA sensing and inflammatory input upstream of NF-κB. |
| 34–37 | One-way | `IKK.st`; `TAK1_a`, A20 | Neutral IKK activates with a quadratic TAK1-dependent rate, enters `i` with an A20-increased rate, and traverses `i→ii→n`. | Produces a pulse with an explicit refractory recovery cycle. |
| 38–39 | One-way | Unphosphorylated IκBα and NF-κB binding sites at matched location | Forms cytoplasmic or nuclear IκBα–NF-κB complexes with location-specific association rates. | Sequesters NF-κB and permits inhibitor-mediated nuclear export. |
| 40–45 | One-way | Active IKK; free or NF-κB-bound cytoplasmic IκBα | IKK changes IκBα `0→pp`; phosphorylated IκBα is removed, releasing NF-κB if bound; slower rules remove unphosphorylated free or bound inhibitor. | Liberates NF-κB while defining basal and signal-driven inhibitor turnover. |
| 46–48 | One-way or reversible | NF-κB/IκBα location states | Free NF-κB imports to nucleus; bound complex exports to cytoplasm; free unphosphorylated IκBα shuttles both directions. | Couples feedback-protein abundance to nuclear NF-κB residence. |
| 49–55 | One-way | Nuclear free NF-κB, nuclear free IκBα, feedback mRNAs, eIF2α-p, RNaseL-a | NF-κB and IκBα compete in bounded transcription rates for IκBα/A20; RNase L accelerates mRNA loss; eIF2α-p suppresses translation; A20 is also degraded. | Implements inducible negative feedback under antiviral translation/RNA-decay constraints. |
| 56–60 | One-way | RIG-I/MAVS, TBK1 Ser172, IRF3 Ser396, A20 | Sensor complex phosphorylates TBK1; basal and A20-dependent rules dephosphorylate it; active TBK1 phosphorylates IRF3, which is then reset. | Generates the IRF3 input required jointly with NF-κB for interferon transcription. |
| 61–62 | One-way | IFNAR and cytoplasmic or extracellular IFNβ binding sites | Both ligand pools create an occupied receptor, representing autocrine secretion or external stimulation. | Converts endogenous or experimental interferon into the same receptor signal. |
| 63–66 | Reversible source/sink or one-way | IFNAR mRNA and receptor | Creates/degrades mRNA with RNase-L sensitivity, translates receptor with eIF2α inhibition, and removes free or ligand-bound receptor at distinct rates. | Maintains receptor availability while permitting signal-dependent turnover. |
| 67–70 | One-way | `NFkB_nuc_free`, `IRF3_p`, IFNβ mRNA/protein | Joint NF-κB×IRF3 activity saturably creates IFNβ mRNA; transcript produces cytoplasmic IFNβ; separate rules remove both. | Forms the central interferon output requiring both transcription-factor branches. |
| 71–74 | Reversible or one-way | IFNAR occupancy; STAT1 Tyr701, STAT2 Tyr690, dimer sites | Occupied receptor drives saturable phosphorylation; phospho-STAT1/2 bind; the dimer is reset directly to free unphosphorylated monomers. | Creates the transcriptionally active STAT heterodimer and terminates it in one step. |
| 75–78 | One-way source/sink | STAT1/2 mRNAs; `STAT12_dimer`, RNaseL-a | Bounded basal-plus-dimer rates create transcripts, and RNase L accelerates their loss. | Adds positive feedback to the interferon-response capacity. |
| 79–83 | One-way | STAT mRNAs, monomers, and heterodimer | Each mRNA produces unphosphorylated protein; monomers and the dimer are removed at the common `sg_Stat` rate. | Balances STAT amplification with turnover of every binding state. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `RIG_I_total`, `PKR_total`, `OAS3_total`, `RNaseL_total`, `RNaseL_a`, `eIF2a_total`, `eIF2a_p` | Species or molecule count | Sensor/effector abundance plus active RNase L and phospho-eIF2α. | `RNaseL_a` and `eIF2a_p` are regulatory inputs to multiple rate expressions. |
| `RIGI_mRNA`, `PKR_mRNA`, `OAS3_mRNA`, `RNaseL_mRNA` | Species count | Four antiviral transcripts. | Resolve STAT-driven induction against RNase-L-accelerated loss. |
| `TAK1_a`, `IKK_a`, `NFkB_nuc_free`, `NFkB_nuc_total`, `NFkB_total` | Species count | Kinase activity and free/total nuclear or global NF-κB. | `NFkB_nuc_free` is the transcription-driving pool, not all nuclear NF-κB. |
| `IkBa_total`, `IkBa_nuc_total`, `IkBa_cyt_total`, `IkBa_cyt_free`, `IkBa_p_cyt`, `IkBa_nuc_free` | Species count | Explicit sums over inhibitor location, binding, and phosphorylation states. | These multi-pattern sums intentionally combine distinct molecular contexts; `IkBa_nuc_free` enters gene rates. |
| `A20`, `IkBa_mRNA`, `A20_mRNA` | Species count | Feedback protein and transcripts. | Report the two negative-feedback arms downstream of NF-κB. |
| `IRF3_total`, `IRF3_p` | Species count | Total and Ser396-phosphorylated IRF3. | Separate branch capacity from the active interferon-transcription input. |
| `IFNAR_total`, `IFNAR_a`, `IFNb_ext`, `IFNb_cyt`, `IFNAR_mRNA`, `IFNb_mRNA` | Species count | Receptor, occupied receptor, interferon pools, and their transcripts. | Distinguish experimental/extracellular interferon from newly synthesized cytoplasmic ligand. |
| `STAT1_total`, `STAT2_total`, `STAT1_p`, `STAT2_p`, `STAT1_u`, `STAT2_u`, `STAT12_dimer`, `STAT1_mRNA`, `STAT2_mRNA` | Species or molecule count | STAT abundance, phosphorylation, unbound substrate pools, heterodimer, and transcripts. | The mixed observable types should not be treated as interchangeable counts when complexes are present. |

## 8. Actions and simulation workflow

The file contains two active workflows: a direct 30-day ODE simulation, followed by a staged protocol that first equilibrates to time 100,000 minus 24 hours, adds extracellular IFNβ for 24 hours, then adds extracellular poly(I:C) and continues for 10 hours. Each perturbation uses continuation, so the second stimulus acts on the interferon-preconditioned state rather than restarting the model.

## 9. Technical caveats and ambiguities

- Localization is encoded by states rather than physical compartments, so no volume conversion accompanies nuclear/cytoplasmic or extracellular/cytoplasmic changes unless included explicitly in a rate.
- Several observables use `Species` while others use `Molecules`; complexes therefore affect their numerical interpretation differently.
- Global RNase-L-dependent transcript decay and eIF2α-dependent translation inhibition are broad abstractions applied across multiple gene products.
- The metadata describes this as a validation/test-case model and its description is incomplete; biological scope here is derived from the BNGL comments and constructs.
- Two simulation sequences are active in one file; running all actions produces both the long unperturbed output and the staged stimulation outputs.
