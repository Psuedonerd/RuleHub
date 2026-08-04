# Detailed Model Explanation: Chylek 2014 TCR signaling model

## 1. Model overview

This model follows early T-cell receptor signaling initiated by three bivalent ligands that crosslink TCR, CD28, or one of each. It connects receptor-proximal LCK/FYN activity to ZAP70, LAT–LCP2 signalosome assembly, PLCG1 and WAS phosphorylation, while PTPN6 and the PAG1–CSK module provide opposing phosphatase and inhibitory-kinase control.

## 2. BNGL block inventory

The model contains 99 parameters, 20 molecule types, 20 seed species, 129 reaction rules, and 20 molecule-count observables. It has no functions, compartments, anchors, or embedded simulation actions.

## 3. Parameters, functions, and rate laws

Association constants are converted from concentration-based units using Avogadro's number and a simulated cell or extracellular volume representing 2% of a cell. Most rules use mass-action rates; paired `kf`/`kr` names govern binding, `kp` names govern phosphorylation, and `kdp` names govern dephosphorylation.

| Parameter group or names | Function in this model |
| --- | --- |
| `NA`, `celldensity`, `Fx`, `ECFvol`, `simECFvol`, `Cellvol`, `simCellvol` | Establish the molecule-number and volume scaling used to convert bimolecular rate constants and initial copy numbers into the simulated 2% cell fraction. |
| `Ligtot`, `Proteintot`, `TCRtot`, `CD28tot` | Set the initial pools: each ligand class receives `Ligtot`, most signaling proteins receive `Proteintot`, and TCR and CD28 have distinct receptor totals. |
| `kfl`, `kfl_m`, `krl` | Control first-arm ligand capture, second-arm crosslinking, and ligand release. Both association rates are zero in this file because the accompanying RNF protocol is expected to set them when stimulation begins. |
| `kfLckCd28`/`krLckCd28`, `kfItkCd28`/`krItkCd28`, `kfTcrFyn`/`krTcrFyn`, `kfTcrNck`, `kfWasNck`/`krWasNck` | Govern constitutive or receptor-supported recruitment of LCK and ITK to CD28, FYN and NCK to TCR, and WAS to NCK. |
| `kfZapTcr`, `krZapTcr`, `kfZapCd3e`, `krZapCd3e`, `kfPtpTcr`, `krPtpTcr` | Set binding of ZAP70 and PTPN6 to phosphorylated TCR-chain sites; ZAP70 leaves the CD3ε-like sites forty times faster than the ζ-like sites. |
| `kpLckTcrz1`, `kpLckTcrz2`, `kpLckCd3e1`, `kpLckCd3e2`, `kpLckCd3g`, `kpLckCd3d` | Specify site-resolved LCK phosphorylation of the six TCR tyrosine variables exposed by a TCR–CD28 crosslink. |
| `act`, `kpLckLck1/2`, `kpLckItk1/2`, `kpLckPtp1/2`, `kpLckZap` | Control LCK-dependent phosphorylation of another LCK, ITK, PTPN6, and receptor-bound ZAP70. The `*2` variants are multiplied by `act`, representing enhanced catalysis by LCK lacking inhibitory Y505 phosphorylation. |
| `kfLckPtp`/`krLckPtp`, `kfLckPtp2`/`krLckPtp2`, `kdpLck192`, `kdpLck394` | Govern PTPN6 association with the two LCK phosphoforms and removal of phosphorylation from LCK Y192 and Y424. |
| `kfPagCsk`/`krPagCsk`, `kfPagLck`/`krPagLck`, `kpLckPag`, `kpCskLck` | Build the PAG1–LCK–CSK inhibitory module: LCK creates the CSK docking site and CSK phosphorylates inhibitory LCK Y505. |
| `kfPagPtp`, `kfPagPtp_cyt`, `cyt`, `krPagPtp`, `kdpPag` | Control PTPN6 capture by PAG1 and PAG1 dephosphorylation. The cytosolic encounter rate is reduced by the factor `cyt`; TCR-tethered encounters use the full rate. |
| `kfDok1Ptp`/`krDok1Ptp`, `kdpDok1`, `kfDok2Ptp`/`krDok2Ptp`, `kdpDok2` | Set recruitment of PTPN6 to the DOK adaptors and catalytic removal of their phosphotyrosines. |
| `kpWas`, `kfWasFyn`/`krWasFyn` | Control FYN access to NCK-bound WAS and phosphorylation of WAS Y291 in receptor- or LAT/LCP2-associated assemblies. |
| `kfZapLat132`, `kfZapLat191`, `krZapLat`, `kpZapLat2` | Describe transient ZAP70–LAT enzyme/substrate encounters and phosphorylation of LAT Y132 and Y191; Y191 capture is threefold faster. |
| `kfPlcgLat`/`krPlcgLat`, `kfLatGrap`/`krLatGrap`, `kfGrapLcp`/`krGrapLcp`, `kfNckLcp`/`krNckLcp` | Assemble the LAT–PLCG1 branch and the LAT–GRAP2–LCP2–NCK branch through phosphotyrosine and adaptor interactions. |
| `kfZapLcp`/`krZapLcp`, `kpZapLcp2`, `kfPlcgLcp`/`krPlcgLcp`, `kfLcpItk`/`krLcpItk`, `kpPlcg` | Control ZAP70 phosphorylation of the two LCP2 sites, LCP2 recruitment of PLCG1 and ITK, and ITK-mediated phosphorylation of PLCG1 Y783. |
| `kp1`–`kp4`, `kdp1`–`kdp5` | Provide low-level site-specific basal phosphorylation and dephosphorylation for receptors, kinases, adaptors, and effectors, allowing nonzero resting-state phosphoprotein populations. |

There are no active functions; all rates are parameters or simple parameter products written directly on rules.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `Lig1`, `Lig2`, `Lig3` | 2 each | Lig1: two `aCD28`; Lig2: `aCD28`, `aCD3`; Lig3: two `aCD3` | None | None | Bivalent stimuli that selectively crosslink two CD28 molecules, a CD28–TCR pair, or two TCR molecules. |
| `TCR` | 9 | `epitope`, `Y149_D`, `Y171_G`, `Y111`, `Y123`, `fynbind`, `PRS_E`, `Y188_E`, `Y199_E` | Each named Y site: `0`, `P` | None | Receptor hub carrying six independently tracked phosphotyrosines plus ligand-, FYN-, and NCK-binding sites. |
| `CD28` | 3 | `epitope`, `PRS1`, `PRS2` | None | None | Costimulatory receptor whose two proline-rich sites recruit LCK and ITK. |
| `LCK` | 5 | `SH2`, `SH3`, `Y192`, `Y424`, `Y505` | Y sites: `0`, `P` | None | Receptor-proximal kinase; Y424 reports activation-loop phosphorylation, whereas Y505 supports CSK-mediated inhibition and intracomplex rate asymmetry. |
| `ITK` | 4 | `SH3`, `SH2`, `PTK`, `Y512` | `Y512`: `0`, `P` | None | CD28-recruited kinase that is activated by LCK and phosphorylates PLCG1 when positioned on LCP2. |
| `ZAP70` | 3 | `SH2`, `PTK`, `Y493` | `Y493`: `0`, `P` | None | Binds phosphorylated TCR sites and, when activated, phosphorylates LAT and LCP2. |
| `PTPN6` | 3 | `SH2`, `PTP`, `Y566` | `Y566`: `0`, `P` | None | SH2-recruited phosphatase that removes phosphorylation from LCK, PAG1, DOK1, and DOK2. |
| `PAG1` | 2 | `Y163`, `Y317` | Both: `0`, `P` | None | Scaffold coupling LCK to CSK and PTPN6, thereby linking kinase activity to inhibitory feedback. |
| `CSK` | 1 | `SH2` | None | None | Binds PAG1 pY317 and installs inhibitory LCK Y505 phosphorylation. |
| `DOK1`, `DOK2` | 1 each | `Y449`; `Y299` | Each: `0`, `P` | None | Phosphorylated adaptor substrates used to represent PTPN6-dependent dephosphorylation outputs. |
| `FYN` | 2 | `unique`, `PTK` | None | None | TCR-associated kinase that phosphorylates WAS in NCK-linked receptor or signalosome complexes. |
| `NCK` | 3 | `SH3_1`, `SH3_3`, `SH2` | None | None | Bridges TCR or phosphorylated LCP2 to WAS, connecting receptor signaling to the WAS branch. |
| `WAS` | 2 | `PRS`, `Y291` | `Y291`: `0`, `P` | None | NCK-bound effector phosphorylated by FYN in two alternative signaling assemblies. |
| `LAT` | 2 | `Y132`, `Y191` | Both: `0`, `P` | None | ZAP70 substrate whose phosphosites separately recruit PLCG1 and GRAP2. |
| `PLCG1` | 3 | `SH2`, `SH3`, `Y783` | `Y783`: `0`, `P` | None | Effector recruited to LAT and LCP2 and activated by ITK-dependent Y783 phosphorylation. |
| `GRAP2` | 2 | `SH2`, `SH3` | None | None | Adaptor linking LAT pY191 to LCP2. |
| `LCP2` | 4 | `RxxK`, `Y113_Y128`, `PRS`, `Y145` | Both Y variables: `0`, `P` | None | Signalosome scaffold that recruits NCK, PLCG1, and ITK after ZAP70 phosphorylation. |

## 5. Compartments, anchors, initial species, and setup

The model is spatially implicit: it declares neither compartments nor anchors. All three ligand classes begin free at the same scaled abundance, while TCR and CD28 begin unbound and unphosphorylated; the ligand association switches are initially zero, so these pools cannot crosslink receptors until an external RNF protocol changes `kfl` and `kfl_m`. Every intracellular signaling protein begins free, and all tracked tyrosines start in state `0`; most share a common scaled protein pool, deliberately giving equal starting abundance rather than protein-specific copy numbers.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–25 create ligand-selected receptor assemblies and load or activate proximal enzymes. Rules 26–85 propagate signals through LCK/PTPN6 feedback, WAS, LAT, LCP2, and PLCG1; rules 86–129 superimpose basal phosphosite turnover on that induced network.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–2 | Reversible | Lig1 `aCD28` arms; CD28 `epitope` | Rule 1 captures one CD28 at `kfl`; rule 2 captures a second CD28 with the intracomplex-scaled `kfl_m`; both arms release at `krl`. | Creates CD28 homodimers that juxtapose CD28-bound kinases. |
| 3–4 | Reversible | Lig3 `aCD3` arms; TCR `epitope` | Sequentially binds one then two TCRs, using `kfl` and `kfl_m` for the first and second arms and `krl` for release. | Creates TCR homodimers capable of receptor-proximal signaling. |
| 5–8 | Reversible | Lig2 `aCD28`/`aCD3`; CD28 and TCR `epitope` | Rules 5–6 bind CD28 first and then TCR; rules 7–8 take the reverse order. The first arm uses `kfl`, the crosslinking arm `kfl_m`, and either bond can reverse at `krl`. | Builds the heterotypic TCR–CD28 complex required by the model's LCK-driven TCR phosphorylation rules. |
| 9–11 | Reversible | LCK `SH3`–CD28 `PRS1`; ITK `SH3`–CD28 `PRS2`; FYN `unique`–TCR `fynbind` | Creates or releases each recruitment bond with its named association/dissociation pair. | Prepositions three kinases on the two receptor types before or during crosslinking. |
| 12–13 | Mixed | NCK `SH3_1`; TCR `PRS_E`, conditioned on `Y188_E` | Rule 12 reversibly recruits NCK only while Y188_E is unphosphorylated. Rule 13 forces rapid NCK release after Y188_E becomes phosphorylated, at `1e5 × krWasNck`. | Makes phosphorylation of the adjacent TCR site a switch that disassembles the receptor-bound NCK branch. |
| 14–17 | Reversible | ZAP70 `SH2`; TCR pY111, pY123, pY199_E, or pY188_E | Each phosphotyrosine recruits ZAP70. Rules 14–15 use the slower-off ζ-site pair; rules 16–17 use the faster-off CD3ε-site pair. | Converts individual TCR phosphosites into alternative ZAP70 docking sites with different residence times. |
| 18–19 | Reversible | PTPN6 `SH2`; TCR pY149_D or pY171_G | Forms or releases an SH2–phosphotyrosine bond at the common `kfPtpTcr`/`krPtpTcr` rates. | Recruits the negative-regulatory phosphatase to two receptor-chain sites. |
| 20–25 | One-way | CD28-bound LCK with unphosphorylated Y505; Lig2-linked TCR Y188_E, Y199_E, Y149_D, Y171_G, Y111, or Y123 | Rules 20–25 phosphorylate the six TCR sites, respectively, without consuming or rebinding LCK; each uses its site-specific `kpLck...` rate. | Writes the receptor phosphotyrosine code that recruits ZAP70, PTPN6, and other downstream partners. |
| 26–29 | One-way | Two ligand-crosslinked CD28 molecules bearing LCK or ITK; LCK Y505 and partner LCK Y424 or ITK Y512 | Rules 26/28 use Y505-phosphorylated LCK and the `*1` rate; rules 27/29 use Y505-unphosphorylated LCK and the `act`-enhanced `*2` rate. Targets are LCK Y424 (26–27) and ITK Y512 (28–29). | Allows CD28 clustering to activate LCK in trans and ITK, with stronger catalysis assigned to the uninhibited LCK form. |
| 30–33 | One-way | CD28-bound LCK Y505~0; TCR-bound ZAP70 at pY111, pY123, pY188_E, or pY199_E | LCK changes ZAP70 Y493 from `0` to `P` at `kpLckZap` while both enzymes remain receptor-linked. | Activates ZAP70 at any of its four modeled receptor docking sites. |
| 34–37 | One-way | CD28-bound LCK; TCR-bound PTPN6 at pY149_D or pY171_G | LCK phosphorylates PTPN6 Y566; rules 34/36 use the basal LCK rate and 35/37 the `act`-multiplied rate according to LCK Y505 state. | Activates receptor-recruited PTPN6 as a delayed counterweight to proximal kinase output. |
| 38–39 | Reversible | PTPN6 pY566; LCK `SH2` with Y192~0 or Y192~P | PTPN6 binds LCK through SH2–pY566 recognition; Y192 phosphorylation switches to the lower-association/higher-dissociation parameter pair. | Creates an additional LCK–PTPN6 complex whose stability depends on LCK Y192. |
| 40–43 | Mixed | PAG1 Y163/Y317; LCK `SH2`, Y505; CSK `SH2` | PAG1 pY163 recruits LCK (41), LCK phosphorylates PAG1 Y317 (42), pY317 recruits CSK (40), and assembled CSK phosphorylates LCK Y505 (43). Binding is reversible; phosphorylation is one-way. | Implements PAG1-scaffolded negative feedback that converts LCK recruitment into LCK inhibition. |
| 44–48 | One-way | Active PTPN6 associated through TCR or LCK; LCK Y192/Y424 | Rules 44–45 remove Y192 phosphorylation in the two TCR-docking contexts. Rules 46–47 remove Y424 in those contexts, while rule 48 removes Y424 from an SH2-linked LCK–PTPN6 pair. | Directly suppresses LCK regulatory phosphorylation through receptor-recruited PTPN6. |
| 49–53 | One-way | PTPN6 `PTP`; PAG1 pY163; optionally TCR-bound PTPN6 | Rules 49–51 form the catalytic complex from two TCR-tethered arrangements or a slower cytosolic encounter; rule 52 releases unchanged substrate, whereas rule 53 releases PAG1 with Y163 dephosphorylated. | Lets PTPN6 erase its own PAG1 recruitment site, limiting the inhibitory scaffold. |
| 54–57 | One-way | PTPN6 `PTP`; DOK1 pY449; TCR pY149_D/pY171_G | Two receptor-tethered capture routes (54–55) feed either noncatalytic release (56) or Y449 dephosphorylation (57). | Represents DOK1 as a phosphatase substrate downstream of PTPN6 recruitment. |
| 58–61 | One-way | PTPN6 `PTP`; DOK2 pY299; TCR pY149_D/pY171_G | Mirrors the DOK1 sequence: two tethered capture routes, unchanged release, or catalytic conversion of DOK2 Y299 to `0`. | Extends the PTPN6 substrate branch to DOK2 with its own kinetic constants. |
| 62–66 | Mixed | WAS `PRS`/Y291; NCK `SH3_3`; FYN `PTK`; receptor- or LCP2-bound assemblies | Rule 62 reversibly recruits WAS to NCK. Rule 63 phosphorylates Y291 when FYN and NCK occupy opposite TCRs in a Lig3 crosslink. Rules 64–66 form, catalyze, or abort the analogous FYN–WAS encounter on the LAT–GRAP2–LCP2–NCK scaffold. | Provides two topology-dependent routes from FYN to WAS activation. |
| 67–72 | One-way | Active, receptor-bound ZAP70 `PTK`; LAT Y132 or Y191 | Rules 67–69 bind, release, or phosphorylate Y132; rules 70–72 do the same for Y191. Only ZAP70 pY493 performs the catalytic step. | Transfers receptor activation onto the two LAT docking sites. |
| 73–76 | Reversible | LAT pY132/pY191; PLCG1 `SH2`; GRAP2 `SH2`; GRAP2 `SH3`; LCP2 `RxxK`; LCP2 pY113_Y128; NCK `SH2` | Sequentially recruits PLCG1 to LAT Y132, GRAP2 to LAT Y191, LCP2 to GRAP2, and NCK to phosphorylated LCP2. | Builds the branched LAT signalosome that brings PLCG1 and the NCK/WAS arm into a shared downstream structure. |
| 77–79 | One-way | Receptor-bound ZAP70 `PTK`; GRAP2-linked LCP2 Y113_Y128 | ZAP70 transiently binds LCP2 (77), can dissociate without change (78), or, if Y493 is phosphorylated, releases after changing the lumped Y113/Y128 variable to `P` (79). | Creates the NCK docking site on LCP2. |
| 80–81 | Reversible | PLCG1 `SH3`–LCP2 `PRS`; ITK `SH2`–LCP2 pY145 | Forms the two adaptor-enzyme links using their respective rate pairs. | Positions PLCG1 and ITK together on LCP2 for PLCG1 activation. |
| 82–84 | One-way | Receptor-bound ZAP70 `PTK`; GRAP2-linked LCP2 Y145 | The three-step encounter binds ZAP70, permits unchanged release, or changes Y145 from `0` to `P` when ZAP70 Y493 is phosphorylated. | Generates the ITK docking site needed for the PLCG1 activation complex. |
| 85 | One-way | LCP2-bound PLCG1 Y783 and ITK | ITK changes PLCG1 Y783 from `0` to `P` at `kpPlcg` while both remain attached to LCP2. | Produces the terminal PLCG1 phosphorylation readout of the modeled LAT/LCP2 branch. |
| 86–97 | One-way | Six TCR sites: Y149_D, Y171_G, Y111, Y123, Y199_E, Y188_E | Consecutive pairs add and remove phosphorylation at each site using `kp1` and the assigned `kdp1` or `kdp4`. | Establishes receptor-site turnover even without ligand-driven kinase assemblies. |
| 98–107 | One-way | LCK Y192/Y424/Y505; PTPN6 Y566; ZAP70 Y493 | Consecutive add/remove pairs apply the appropriate `kp2` or `kp1` and site-specific `kdp` values. | Sets resting-state turnover for the proximal enzymes and their activating or inhibitory sites. |
| 108–119 | One-way | LAT Y132/Y191; ITK Y512; PLCG1 Y783; LCP2 Y113_Y128/Y145 | Consecutive add/remove pairs independently turn over each downstream phosphosite. | Prevents these readouts from being exclusively dependent on assembled catalytic complexes and supplies basal occupancy. |
| 120–129 | One-way | PAG1 Y163/Y317; DOK1 Y449; DOK2 Y299; WAS Y291 | Consecutive phosphorylation/dephosphorylation pairs independently turn over the five sites. | Maintains resting flux through the feedback, phosphatase-substrate, and WAS branches. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `TCR_pY149_D`, `TCR_pY171_G`, `TCR_pY111`, `TCR_pY123`, `TCR_pY188_E`, `TCR_pY199_E` | Molecule count | TCR molecules phosphorylated at each of the six named sites, whether the site is bound or free. | Site-resolved receptor activation readouts; a TCR phosphorylated at several sites contributes once to each applicable observable. |
| `ZAP70_pY493`, `LCK_pY424`, `LCK_pY192`, `LCK_pY505`, `ITK_pY512`, `PTPN6_pY566` | Molecule count | Each kinase or phosphatase carrying the indicated phosphotyrosine. | Separates activating and regulatory enzyme states; notably, LCK Y505 is the model's inhibitory-site readout rather than a generic activity measure. |
| `LAT_pY191`, `PLCG1_pY783`, `WAS_pY291` | Molecule count | Phosphorylated downstream scaffold or effector molecules. | Reports transmission into the LAT/PLCG1 and NCK/WAS branches, including both induced and basal phosphorylation. |
| `PAG1_pY163`, `DOK1_pY449`, `DOK2_pY299` | Molecule count | Phosphorylated negative-regulatory scaffold/adaptor sites. | Tracks substrates coupled to PTPN6 and PAG1 feedback rather than direct receptor output. |
| `NCK_TCR` | Molecule count | TCR–NCK bonds between TCR `PRS_E` and NCK `SH3_1`. | Counts matched receptor–NCK embeddings; phosphorylation-driven release at TCR Y188_E reduces this readout. |
| `NCK_LCP2` | Molecule count | LCP2–NCK bonds at phosphorylated LCP2 Y113_Y128 and NCK SH2. | Reports relocation of NCK into the LAT/LCP2 signalosome; complexes with multiple matching embeddings could contribute more than once. |

## 8. Actions and simulation workflow

The BNGL file defines the molecular network but contains no active actions, so it does not generate or simulate that network by itself. Its comments and zero ligand-on rates indicate an external RNF workflow that equilibrates the basal system, changes `kfl` and `kfl_m` to apply ligand, and then performs the intended time course; the metadata identifies ODE as the supported simulation method.

## 9. Technical caveats and ambiguities

- The model represents only a 2% fraction of a cell and assigns one common initial copy-number pool to most signaling proteins; these are scaling choices, not claims of equal full-cell abundance.
- Several variables lump multiple biological residues (`Y113_Y128`) or encode chain identity in abbreviated names (`Y149_D`, `Y171_G`, `Y188_E`, `Y199_E`). Their model roles are explicit, but the summary does not expand those labels beyond the local evidence.
- The stimulus is inert when this file is loaded alone because both ligand association parameters are zero. Reproducing the intended response requires the external parameter-changing protocol described in the comments.
- Molecule-count observables match BNGL patterns and may count embeddings rather than unique physical complexes, especially for multivalent assemblies.
