# Detailed Model Explanation: An 2009 TLR4 Signaling

## 1. Model overview

This model represents lipopolysaccharide (LPS) assembly with CD14, MD2, and Toll-like receptor 4 (TLR4), followed by parallel TRIF- and MyD88-associated routes to TAK1, IKK, and NF-κB activation. Nuclear NF-κB drives TNF, A20, and IκB expression; A20 dismantles upstream signaling complexes, while IκB recaptures NF-κB and terminates promoter occupancy.

## 2. BNGL block inventory

The model has 97 parameters, 31 molecule types, 19 seed species, 41 active reaction rules, 19 molecule-count observables, and 7 actions. It contains no functions, compartments, or anchors; localization and activity are represented by internal states.

## 3. Parameters, functions, and rate laws

The parameter namespace is largely process-descriptive: association/dissociation pairs build receptor and adaptor complexes, catalytic constants change activation or transcription states, and `*_Init` names define starting pools. Active rules use mass-action rate laws; several declared zero-valued degradation rates intentionally make activated intermediates persistent except where a separate deactivation rule exists.

| Parameter group or names | Function in this model |
| --- | --- |
| `LPS_MD2_*`, `LPS_CD14_*`, `CD14_MD2_*`, `LPS_TLR4_*`, `CD14_TLR4_*`, `MD2_TLR4_*`, `TLR4_Complex_Dimer_*` | Association/dissociation constants for ordered construction and dimerization of the ligand-loaded receptor assembly. Only the binding members used by rules contribute to the active forward assembly. |
| `TLR4_TRAM_*`, `TLR4TRAM_TRIF_*`, `RP1_TRIF_*`, `TRIF_TRAF6_*`, `RP1_TRAF6_*`, `TRAF6_TRIF_*` | Control recruitment in the TRAM–TRIF–RIP1/TRAF6 branch downstream of the receptor dimer. |
| `TLR4_MAL_*`, `TLR4MAL_MyD88_*`, `MyD88_IRAK4_*`, `MyD88_IRAK1_*`, `IRAK1_IRAK4_*`, `MyD88IRAK1_TRAF6_*`, `TRAF6_MyD88IRAK1_*` | Define assembly of the MAL–MyD88–IRAK–TRAF6 branch. The active rules build a preassembled MyD88/IRAK complex before receptor recruitment. |
| `TRAF6TRIF_TAK1_Activate`, `MyD88IRAK1TRAF6_TAK1_Activate`, `TAK1_Ikk_Complex_Activate` | Catalytic rates connecting either adaptor branch to TAK1 and then to the IKK complex. |
| `TAK1_Deactivation`, `Ikk_Deactivation`, `TAK1_Degradation`, `Ikk_Degradation_Rate` | Control termination of kinase activity. The two degradation parameters are zero, and `Ikk_Deactivation` is also zero in the supplied parameterization. |
| `Ikk_complex_IkB_Phos`, `IkB_Proteasome23_Degrade`, `IkB_DegradeNFkB`, `NFkB_IkB_Bind`, `NFkB_IkB_Unbind` | Govern IKK-dependent phosphorylation of complexed IκB, proteasome recruitment/release, and cytoplasmic NF-κB inhibition. |
| `NFkB_Translocation_Nucleus`, `NFkB_DNA_A20_*`, `NFkB_DNA_TNF_*`, `NFkB_DNA_IkB_*` | Control nuclear entry and NF-κB engagement of the three explicitly active promoters. |
| `A20_Transcription_Execute`, `TNF_Transcription_Execute`, `IkB_Transcription_Execute`; corresponding `*_Translation_Execute` | Create the three mRNAs from promoter-bound NF-κB and their protein products from translation-enabled transcripts. |
| `A20_MyD88IRAK1TRAF6_Degrade`, `A20_TRAF6TRIFRP1_Degrade`, `A20_IkkAct_Deactivate` | Implement catalytic A20 feedback by breaking either upstream adaptor complex or changing active IKK to inactive. The declared `A20_TRAF6_Bind/Unbind` pair is not used by an active rule. |
| `TNF_Degrade`, `A20_Degrade` | Set output and feedback-protein turnover. |
| `CD14_Init` through `p50_Init`, `IkB_Init`, `NFkB_Inactive_Cytoplasm`, `DNA`, `LPS_Init`, `A20_Init`, `A20_Preconditioned` | Establish receptor/adaptor/enzyme pools, the initial inhibited NF-κB pool, two DNA templates, the post-equilibration LPS dose, and initial A20 status. |
| `p65_p50_Bind`, `p65_p50_Unbind` | Declared but unused: p65 and p50 are represented as sites on NF-κB/IκB rather than separate molecule types. |

There are no active functions; all context dependence is expressed by rule patterns and ordinary parameters.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `LPS`, `CD14`, `MD2`, `TLR4` | 4; 3; 3; 6 | LPS: `MD2`, `TLR4`, `CD14`, `LPS`; CD14: `TLR4`, `MD2`, `LPS`; MD2: `CD14`, `TLR4`, `LPS`; TLR4: `MAL`, `TRAM`, `TLR4`, `CD14`, `MD2`, `LPS` | None | None | Form the ligand-recognition complex and receptor dimer that exposes the two downstream adaptor routes. |
| `TRAM`, `TRIF` | 2; 5 | TRAM: `TLR4`, `TRIF`; TRIF: `TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM` | None | None | Receptor-proximal and hub adaptors for the TRIF-side signal. |
| `RP1`, `TRAF6` | 4; 8 | RP1: `TRIF`, `TRAF6`, `TAK1`, `p38`; TRAF6: `IRAK1`, `TRIF`, `RP1`, `TAK1`, `TRAF4`, `A20`, `JNK`, `p38` | None | None | RP1 (used as the RIP1-like participant) and TRAF6 assemble the TRIF activation complex; TRAF6 also links the MyD88 route to TAK1 and receives A20 feedback. |
| `MAL`, `MyD88`, `IRAK4`, `IRAK1` | 3; 4; 3; 4 | MAL: `TLR4`, `MyD88`, `SOCS1`; MyD88: `MAL`, `IRAK1`, `IRAK4`, `MyD88s`; IRAK4: `Myd88`, `IRAKM`, `IRAK1`; IRAK1: `IRAK4`, `MyD88`, `Tollip`, `TRAF6` | None | None | Build the alternative receptor-to-TRAF6 complex; note the differently capitalized `Myd88` site on IRAK4. |
| `SARM`, `TRAF4`, `Tollip`, `IRAKM`, `MyD88s` | 1; 3; 1; 1; 2 | SARM: `TRIF`; TRAF4: `TRAF6`, `TAK1`, `TRIF`; Tollip: `IRAK1`; IRAKM: `IRAK4`; MyD88s: `MyD88`, `IRAK1` | None | None | Declared regulatory alternatives whose sites define possible interactions, but none participates in an active rule. |
| `TAK1`, `Ikk_Complex` | 2; 1 | TAK1: `TRAF6`, `Activation`; IKK: `Activation` | `Activation`: `No`, `Yes` | None | Successive kinase switches that carry either upstream branch into IκB control. |
| `NFkB` | 3 | `Transcription`, `Activation`, `Location` | transcription `No/Yes`; activation `No/Yes`; location `Cytoplasm/Nucleus` | None | Encodes free/inhibited status, nuclear transport, and promoter engagement in one molecule. |
| `IkB` | 4 | `Phos`, `p65`, `p50`, `Degrade` | phosphorylation `No/Yes`; degradation mark `No/Yes` | None | Inhibitor bound to NF-κB through two contacts, phosphorylated by IKK and processed through a proteasome-bound degradation state. |
| `Proteasome26s` | 1 | `IkB` | None | None | Binds phosphorylated IκB and participates in NF-κB release. |
| `DNA` | 7 | `A20`, `TNF`, `iNOS`, `IL10`, `IkB`, `c`, `c` | None | None | Shared promoter scaffold; only A20, TNF, and IκB sites are used by active rules. The repeated `c` sites remain unused. |
| `TNFmRNA`, `A20mRNA`, `iNOSmRNA`, `IkBmRNA` | 1 each | `Translation` | `On`, `Off` | None | Transcript switches; TNF, A20, and IκB transcripts are active, whereas iNOS mRNA is declared but unused. |
| `TNF`, `A20` | 1 each | TNF: `TNFr`; A20: `TRAF6` | None | None | TNF is the modeled output; A20 is the induced negative-feedback effector. |
| `Trash`, `Administer` | 1 each | `c` | None | None | Trash is the degradation sink; Administer is declared but unused. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. Before stimulation, receptor components and most adaptors/kinases are seeded as large free pools, the shared DNA scaffold begins unoccupied, and NF-κB begins in a cytoplasmic IκB-bound complex. A20 and output transcripts start absent. Although `LPS_Init` is 100, the action sequence temporarily sets free LPS to zero for equilibration and restores that dose only before the response simulation.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–7 assemble the LPS receptor and TRIF-side TAK1 trigger, rules 8–17 build the MyD88-side trigger and its A20-sensitive disassembly, rules 18–23 add expression and IKK control, and rules 24–41 form the NF-κB promoter cycle and its induced negative feedback.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–4 | Reversible | `LPS`, `MD2`, `CD14`, `TLR4` recognition sites | Sequentially creates LPS–MD2, adds CD14, adds TLR4 through its LPS/CD14/MD2 sites, then joins two loaded TLR4 complexes through their receptor-dimer sites, using the corresponding bind/unbind pairs. | Constructs the dimeric stimulus receptor required by both adaptor branches. |
| 5–7 | Reversible then one-way | Dimeric `TLR4.TRAM`; `TRAM.TRIF`; `TRIF.TRAF6`; `TAK1.Activation` | TRAM and TRIF bind reversibly (5–6); when TRAF6 is present on TRIF, rule 7 catalytically changes TAK1 `No→Yes`. | Provides the compact TRIF-side route to TAK1 activation. |
| 8–9 | Reversible | `MyD88.IRAK4/IRAK1`, reciprocal IRAK sites | MyD88 first binds IRAK4, then recruits IRAK1 into the same complex with the named association/dissociation rates. | Preassembles the MyD88 signaling unit before receptor engagement. |
| 10–11 | One-way | `TNFmRNA.Translation=On`, `A20mRNA.Translation=On` | Changes the relevant transcript from `On` to `Off` while creating TNF or A20 at its translation rate. | Produces one protein per transcription-created translation opportunity, rather than making each mRNA continuously catalytic. |
| 12 | One-way | Active `TAK1` | Sends active TAK1 to `Trash` at the declared TAK1 degradation rate, which is zero in this parameterization. | Provides a nominal degradation route that is kinetically disabled. |
| 13–15 | Reversible | Dimeric `TLR4.MAL`; `MAL.MyD88`; `IRAK1.TRAF6` | MAL binds the second TLR4, recruits the preassembled MyD88–IRAK complex, and TRAF6 binds IRAK1. | Completes the MyD88-side TAK1 activation platform. |
| 16 | One-way | Free `A20`; TRAF6-bound `IRAK1` | In A20's presence, the IRAK1–TRAF6 connection is lost at `A20_MyD88IRAK1TRAF6_Degrade`; A20 remains free and the other adaptor bonds are retained. | Interrupts the MyD88 branch upstream of TAK1 without consuming or binding the feedback regulator. |
| 17 | One-way | MyD88/IRAK1-bound `TRAF6`; `TAK1.Activation` | Catalytically changes TAK1 `No→Yes` at the MyD88-branch activation rate. | Converges the second receptor branch on the shared kinase. |
| 18 | One-way | `IkBmRNA.Translation=On` | Changes the transcript to `Off` while creating unphosphorylated, undegraded IκB at its translation rate. | Replenishes the inhibitor once per transcription-created translation opportunity. |
| 19–20 | Reversible | `TRIF.RIP1`, `RP1.TRIF/TRAF6`, `TRAF6.TRIF/RP1` | Adds RP1 to TRIF, then creates two coordinated contacts from TRAF6 to TRIF and RP1. | Builds the higher-order TRIF complex used for A20-sensitive feedback. |
| 21–22 | One-way | Free A20; active IKK or TRIF–RP1–TRAF6 complex | A20 changes IKK `Yes→No` (21) or breaks both TRAF6 contacts to TRIF/RP1 (22); in both cases A20 is carried through as a free catalyst. | Applies reusable negative feedback at both kinase and adaptor levels. |
| 23 | One-way | Active `Ikk_Complex`; NF-κB-bound `IkB.Phos` | Catalytically changes IκB phosphorylation `No→Yes` without breaking its two NF-κB contacts. | Marks the inhibitor in the inactive NF-κB complex for proteasomal processing. |
| 24 | Reversible | Active, non-transcribing `NFkB.Location` | Moves free active NF-κB between cytoplasm and nucleus using nuclear translocation and reverse rates. | Makes promoter access contingent on liberation and nuclear entry. |
| 25–28 | Reversible | Nuclear active `NFkB.Transcription`; DNA `A20`, `TNF`, or `IkB`; IκB sites | NF-κB binds A20, TNF, and IκB promoter sites and changes `Transcription No→Yes` (25,27,28). Rule 26 lets unphosphorylated IκB remove NF-κB from the A20 promoter, changes NF-κB to inactive/cytoplasmic, and creates both IκB contacts. | Initiates three feedback genes and demonstrates promoter stripping by newly made inhibitor. |
| 29 | One-way | Phosphorylated NF-κB-bound IκB; `Proteasome26s.IkB` | Proteasome binding changes IκB's degradation mark `No→Yes`, breaks both IκB–NF-κB contacts, and leaves NF-κB active in cytoplasm. | Releases the NF-κB signal carrier after IKK-dependent inhibitor phosphorylation. |
| 30–31 | One-way | Cytoplasmic active NF-κB; unphosphorylated IκB; proteasome-bound marked IκB | Rule 30 forms the two-contact inactive NF-κB–IκB complex; rule 31 releases proteasome from degradation-marked IκB at the proteasome-processing rate. | Closes the inhibition cycle and recycles proteasome. |
| 32–34 | One-way | Promoter-bound transcribing NF-κB; `DNA.IkB/A20/TNF` | Retains each DNA–NF-κB complex and creates the matching translation-enabled mRNA at its transcription-execution rate. | Converts promoter occupancy into inducible feedback/output transcripts. |
| 35–37 | One-way | `TAK1.Activation`, `Ikk_Complex.Activation` | Rules 35–36 change active TAK1 or IKK to inactive at their deactivation rates; rule 37 uses active TAK1 catalytically to change IKK `No→Yes`. | Couples the kinase stages and supplies their explicit off transitions, although IKK deactivation is parameterized at zero. |
| 38–39 | One-way | `TNF`, `A20` | Sends each protein to `Trash` at its degradation rate. | Limits output and feedback persistence. |
| 40–41 | One-way | IκB; NF-κB bound to DNA `IkB` or `TNF` | IκB strips NF-κB from the indicated promoter, changes it to inactive/cytoplasmic, and forms both inhibitor contacts. | Extends the same shutdown mechanism as rule 26 to the IκB and TNF promoters. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Activated_TAK1`, `Activated_Ikk_complex` | Molecule count | TAK1 and IKK in activation state `Yes`. | Report convergence of the two adaptor branches and transmission to the inhibitor-processing stage. |
| `NFkB_Active_Cyto`, `NFkB_Active_Nucleus`, `Unbound_Cyto_NFkB` | Molecule count | Free/non-transcribing active NF-κB by location, plus all unbound cytoplasmic NF-κB activation states. | Separate the signaling-competent nuclear pool from a broader cytoplasmic pool. |
| `NFkB_Inactive`, `Inactive_Cyto_NFkB` | Molecule count | NF-κB with at least one bond and the specifically two-contact cytoplasmic IκB complex. | The broad first pattern can count bound contexts beyond the canonical inactive complex. |
| `Phos_IkB_NFkB`, `IkB_Prot26s`, `IkB_Degraded` | Molecule count | Phosphorylated NF-κB–IκB complex, proteasome-bound marked IκB, and all degradation-marked IκB. | Resolve successive stages of inhibitor processing and NF-κB release. |
| `IkB_active`, `NonBoundNonPhos_IkB`, `IkBmRNA_Off` | Molecule count | Undegraded IκB, free unphosphorylated IκB, and translation-disabled IκB transcript. | Distinguish the total usable inhibitor pool from the immediately binding-competent subset. |
| `NFkB_DNA_IkB`, `TNF_NFkB_DNA`, `A20_NFkB_DNA` | Molecule count | NF-κB bound at each active promoter. | Direct readouts of transcriptionally engaged DNA complexes. |
| `TNFmRNA_Off`, `TNF`, `A20` | Molecule count | Translation-disabled TNF transcript and the two produced proteins. | Track the inflammatory output alongside its induced A20 brake. |

## 8. Actions and simulation workflow

After network generation, the workflow removes free LPS and integrates the ODE system toward a steady state for 50,000 time units. It then restores LPS to `LPS_Init`, exports SBML and MATLAB representations of that stimulated setup, and simulates the response for 100,000 time units with 500 output steps.

## 9. Technical caveats and ambiguities

- Several declared regulators (`SARM`, `TRAF4`, `Tollip`, `IRAKM`, `MyD88s`) and the iNOS/IL10 DNA sites have no active rules, so the executable network is narrower than the molecule declarations suggest.
- The source uses `RP1` while its sites and surrounding labels indicate a RIP1-like role; this explanation preserves the declared molecule name rather than resolving that naming ambiguity.
- `TAK1_Degradation`, `Ikk_Degradation_Rate`, and `Ikk_Deactivation` are zero, making their associated active rules kinetically silent under the supplied parameters.
- NF-κB inhibition is encoded with two IκB contacts. Broad bond-wildcard observables can count any matching bound embedding and should not automatically be equated with unique canonical complexes.
- Nuclear and cytoplasmic labels are NF-κB states rather than BNGL compartments, so transport changes state without spatial volume semantics.
