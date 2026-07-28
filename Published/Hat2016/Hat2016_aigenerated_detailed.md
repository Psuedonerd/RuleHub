# Detailed Model Explanation: Hat 2016 DNA-Damage Response and Cell-Fate Control

## 1. Model overview

This model connects DNA double-strand breaks to ATM-dependent p53 modification and then separates p53 activity into arrest-associated and apoptosis-associated programs. Feedback through Wip1, Mdm2, PTEN–PI3K–AKT, Rb–E2F1, and Bax–BclXL–Bad determines whether damage is repaired, the cell-cycle arm is restrained, or caspase activation reinforces damage.

## 2. BNGL block inventory

The model contains 125 parameters, 30 molecule types, 15 seed species, 5 functions, 58 reaction rules, 58 molecule-count observables, and 2 actions. It has no compartments or anchors; nuclear/cytoplasmic status is carried only by the `Mdm2.loc` state.

## 3. Parameters, functions, and rate laws

The namespace groups irradiation and repair controls, conserved starting pools, p53-responsive gene expression, phosphorylation cycles, complex association, transport, and turnover. Rules combine mass action with observable-dependent Hill, saturation, feedback, and source/sink expressions; the `STOCHASTIC_GENES` switch selects between function-driven continuous transcription and explicit two-state gene switching.

| Parameter group or names | Function in this model |
| --- | --- |
| `IR_duration`, `IR_Gy`, `DNA_DSB_per_1Gy`, `DNA_DSB_due_to_IR`, `is_IR_switched_on`, `h1` | Define the irradiation window and convert dose into DNA-break production; the supplied switch is initially off. |
| `has_DNA_DSB_repair`, `rep`, `DNA_DSB_Repair_Cplx_total`, `DNA_DSB_max`; `can_Caspase_make_DNA_DSB`, `h2` | Control saturable break repair, the damage ceiling, and caspase-driven reinforcement of damage. |
| `_total`; `SIAH1_total`, `ATM_total`, `AKT_total`, `PIP_total`, `Rb_total`, `E2F1_total`, `BclXL_total`, `Bad_total`, `Fourteen_3_3_total` | Establish the principal signaling, cell-cycle, and apoptotic pools; several are scaled from a common reference abundance. |
| `STOCHASTIC_GENES`, `q0_*`, `q1_*`, `q2`, `n_*_alleles`, `h` | Set basal and p53-induced switching for Wip1, Mdm2, p21, PTEN, and Bax genes. Arrest-form p53 drives Wip1/Mdm2/p21; S46-phosphorylated killer-form p53 drives PTEN/Bax. |
| `s1`–`s5`, `t1`–`t5`, `g1`–`g5` | Control transcript production, protein translation, and mRNA turnover for the five p53-responsive genes. |
| `s6`–`s10`, `g6`–`g20`, `g101` | Set constitutive synthesis and state-specific degradation of p53, HIPK2, cyclin E, caspases, PTEN, Wip1, Bax, p21, Mdm2, and related complexes. |
| `p1`–`p6`, `d1`–`d6`, `p11`, `d10`, `d11`, `M1` | Govern the ATM–SIAH1–p53–Mdm2 phosphorylation/dephosphorylation cycles, including Wip1-dependent reversal and HIPK2-dependent p53 S46 modification. |
| `p8`, `d7`, `p12`, `d8` | Implement PI3K/PTEN control of PIP2–PIP3 and PIP3-dependent AKT activation. |
| `p9`, `p10`, `d12`, `M2`, `M3`; `b4`, `u5`, `b5`, `u6` | Control cyclin-E/Rb/E2F1 cell-cycle feedback and p21 sequestration of cyclin E. |
| `p7`, `d9`; `b1`–`b3`, `u1`–`u3`; `a1`, `a2` | Govern Bad phosphorylation, Bax/BclXL/Bad/14-3-3 binding, and Bax- plus caspase-dependent procaspase activation. |
| `i1` | Imports doubly phosphorylated cytoplasmic Mdm2 into its nuclear state. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `gene_Wip1_activity`, `gene_Mdm2_activity`, `gene_p21_activity` | Arrest-form p53 observable `p53_arr`, shared Hill exponent `h`, gene-specific `q0/q1`, and `q2` | Return bounded transcriptional activities for the repair/arrest program; rules 12, 23, and 37 use them when deterministic gene expression is selected. |
| `gene_PTEN_activity`, `gene_Bax_activity` | Killer-form p53 observable `p53_kill` and the analogous gene parameters | Compute the apoptosis-associated transcriptional response used by rules 32 and 46. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `DNA_DSB`, `ATM`, `SIAH1`, `HIPK2`, `Wip1` | 0; 1; 1; 0; 0 | ATM: `S1981`; SIAH1: `S19` | ATM/SIAH1: `0`, `P` | None | Damage marker and the kinase/phosphatase feedback core that establishes p53 signaling duration. |
| `p53` | 2 | `S15_S20`, `S46` | `S15_S20`: `0/PP`; `S46`: `0/P` | None | Encodes basal, arrest-associated, and apoptosis-associated p53 forms. |
| `Mdm2` | 3 | `S166_S186`, `S395`, `loc` | paired sites `0/PP`; S395 `0/P`; location `Nuc/Cyt` | None | p53-induced negative regulator whose phosphorylation controls nuclear entry and whose nuclear forms accelerate p53 loss. |
| `gene_Wip1`, `gene_Mdm2`, `gene_p21`, `gene_PTEN`, `gene_Bax` | 1 each | `tf` | off (`0`), on (`1`) | None | Optional discrete gene-state representation of the five p53 outputs. |
| `mRNA_Wip1`, `mRNA_Mdm2`, `mRNA_p21`, `mRNA_PTEN`, `mRNA_Bax` | 0 each | None | None | None | Transcript pools connecting gene activity to feedback, arrest, and apoptotic proteins. |
| `PTEN`, `PI3K` | 0 each | None | None | None | Opposing regulators of phosphoinositide state and therefore AKT activity. |
| `PtdIns`, `AKT` | 1 each | `s`; `T308` | PtdIns `PP/PPP`; AKT `0/P` | None | PIP2/PIP3 and inactive/active AKT states linking p53-induced PTEN to Mdm2 and Bad control. |
| `p21`, `Cyclin_E` | 1 each | `b` | None | None | Inhibitory cell-cycle protein and its cyclin target. |
| `Rb` | 2 | `S567`, `b` | `S567`: `0/P` | None | Sequesters E2F1 when unphosphorylated and releases it after cyclin-E-dependent phosphorylation. |
| `E2F1` | 1 | `b` | None | None | Drives cyclin E synthesis when free, completing the cell-cycle feedback loop. |
| `Bax`, `BclXL` | 1 each | `b` | None | None | Pro- and anti-apoptotic binding partners whose free Bax level controls caspase activation. |
| `Bad` | 2 | `S75_S99`, `b` | `0/PP` | None | AKT-regulated competitor that binds BclXL when unphosphorylated or 14-3-3 when phosphorylated. |
| `Fourteen_3_3` | 1 | `b` | None | None | Sequesters phosphorylated Bad away from BclXL. |
| `Caspase` | 1 | `csp` | proenzyme (`Pro`), active (`Act`) | None | Terminal switch activated by free Bax and positive caspase feedback. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. The model begins with unphosphorylated ATM, SIAH1, AKT, Rb, and Bad; PIP2 is the initial phosphoinositide; E2F1, BclXL, Bad, and 14-3-3 are supplied as free pools. Two initially off copies of each regulated gene are seeded, whereas p53, Mdm2, transcripts, Bax, p21, cyclin E, HIPK2, and caspases are produced dynamically. DNA damage is also generated dynamically and irradiation begins disabled unless the control parameter is changed.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–14 establish gene control and the ATM/Wip1 damage-response loop; 15–31 generate and modify p53 and Mdm2; 32–45 implement PTEN/AKT and p21/Rb arrest control; 46–58 implement Bax/Bad/BclXL competition and the caspase decision.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–5 | Reversible | Five gene `tf` states; arrest-form or killer-form p53 observables | Switch each gene `0↔1`. Wip1/Mdm2/p21 use basal plus `p53_arr^h`; PTEN/Bax use basal plus `p53_kill^h`; all switch off at `q2`. | Supplies the stochastic-gene alternative to the continuous activity functions. |
| 6–8 | One-way | Source/sink `0`, `DNA_DSB`, active caspase | Radiation and active caspase create breaks in proportion to unused damage capacity; repair removes breaks with a load-dependent rate. | Combines external damage, repair saturation, and apoptotic positive feedback. |
| 9–10 | Reversible | `ATM.S1981`, `SIAH1.S19`; damage, Wip1, active ATM | Damage phosphorylates ATM and Wip1 reverses it; active ATM phosphorylates SIAH1, which dephosphorylates spontaneously. | Converts break abundance into the upstream p53-regulatory state. |
| 11 | Reversible source/sink | `HIPK2`; nuclear Mdm2 and unphosphorylated SIAH1 observables | Synthesizes HIPK2 and removes it at a rate proportional to both negative-regulator signals. | Makes the kinase that creates killer-form p53 sensitive to the Mdm2/SIAH1 context. |
| 12–14 | Reversible source/sink | Wip1 gene/function, `mRNA_Wip1`, `Wip1` | Rule 12 provides deterministic function-driven mRNA birth/death; rule 13 provides the `STOCHASTIC_GENES`-weighted allele route; rule 14 translates and degrades Wip1. | Implements alternative transcription modes for the phosphatase feedback loop. |
| 15–20 | One-way | Source `0`; the four p53 modification combinations; nuclear Mdm2 | Creates basal p53 (15), then removes basal/non-killer or modified forms through spontaneous or quadratic Mdm2-dependent rates (16–20). | Sets distinct lifetimes for basal, arrest, and killer p53 populations. |
| 21–22 | Reversible | `p53.S15_S20`, `p53.S46`; active ATM, HIPK2, Wip1 | ATM changes paired sites `0→PP`; HIPK2 changes S46 `0→P`; spontaneous or Wip1-dependent reverse rates restore zero states. | Separates the arrest transcriptional program from the stronger apoptosis-associated p53 form. |
| 23–25 | Reversible source/sink then one-way | Mdm2 gene/function, mRNA, and cytoplasmic unmodified Mdm2 | Rules 23–24 are deterministic/stochastic transcription alternatives; rule 25 creates Mdm2 from mRNA. | Produces the principal p53-induced negative regulator. |
| 26–28 | One-way | Mdm2 phosphorylation/location states | Removes unphosphorylated cytoplasmic, doubly phosphorylated, or S395-phosphorylated nuclear Mdm2 at state-specific rates. | Controls how long each regulatory Mdm2 form persists. |
| 29–31 | Reversible, one-way, reversible | `Mdm2.S166_S186`, `loc`, `S395`; active AKT, ATM, Wip1 | AKT sets paired sites `0→PP`; that cytoplasmic form imports to nucleus; ATM adds S395 phosphorylation and Wip1 removes it. | Connects PI3K–AKT signaling and DNA damage to nuclear Mdm2 activity. |
| 32–34 | Reversible source/sink | PTEN gene/function, mRNA, and PTEN protein | Deterministic or allele-state transcription creates PTEN mRNA, followed by mRNA-dependent translation and protein degradation. | Translates killer-form p53 into inhibition of the survival kinase pathway. |
| 35–36 | Reversible | `PtdIns.s`, `AKT.T308`; PI3K, PTEN, PIP3 | PI3K changes PIP2 `PP→PPP` and PTEN reverses it; PIP3 activates AKT `0→P`, followed by spontaneous deactivation. | Creates the survival signal controlling Mdm2 and Bad. |
| 37–39 | Reversible source/sink | p21 gene/function, mRNA, and p21 | Alternative transcription routes produce mRNA; p21 is translated and degraded. | Converts arrest-form p53 into inhibition of cyclin E. |
| 40 | Reversible source/sink | `Cyclin_E`; free E2F1 | Creates cyclin E through basal and E2F1-dependent synthesis and removes it at `g20`. | Supplies the positive cell-cycle arm restrained by p21 and Rb. |
| 41–42 | Reversible then one-way | `p21.b`, `Cyclin_E.b` | Forms a reversible p21–cyclin E bond; the complex can then be removed together at the cyclin degradation rate. | Sequesters and clears cyclin E. |
| 43 | Reversible | `Rb.S567`; free cyclin E and free phosphorylated Rb observables | Cyclin E phosphorylates Rb `0→P`; a saturating reverse expression restores the unphosphorylated state. | Controls whether Rb can bind and inhibit E2F1. |
| 44–45 | Reversible then one-way | `Rb.b/S567`, `E2F1.b`; free cyclin E | Unphosphorylated Rb binds E2F1; cyclin-E-dependent Rb phosphorylation breaks the bond and releases E2F1. | Couples cyclin activity to E2F1-driven cyclin synthesis. |
| 46–48 | Reversible source/sink | Bax gene/function, mRNA, and `Bax.b` | Deterministic or stochastic transcription creates Bax mRNA; translation creates Bax and degradation removes it. | Converts killer-form p53 into the pro-apoptotic effector pool. |
| 49–50 | Reversible then one-way | `Bax.b`, `BclXL.b` | Bax binds BclXL; bound Bax can be degraded while BclXL is released. | Buffers free Bax and delays caspase activation. |
| 51–52 | Reversible then one-way | Unphosphorylated `Bad.b`, `BclXL.b`; active AKT | Bad competes for BclXL; AKT-dependent Bad phosphorylation breaks that complex. | Allows survival signaling to restore BclXL-mediated Bax sequestration. |
| 53–55 | Reversible plus one-way | `Bad.S75_S99/b`, `Fourteen_3_3.b`; active AKT | AKT and phosphatase activity interconvert Bad `0↔PP`; phosphorylated Bad binds 14-3-3, and dephosphorylation releases it. | Partitions Bad between BclXL-binding and protected 14-3-3-bound forms. |
| 56–58 | One-way | Source/sink `0`, `Caspase.csp`, free Bax and active-caspase observables | Produces procaspase, degrades either caspase state, and changes `Pro→Act` at `a1*Bax_free + a2*Caspase_act^2`. | Implements the terminal apoptotic switch with Bax initiation and autocatalytic reinforcement. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `DNA_DSB_tot`, `ATM_tot`, `ATM_p`, `SIAH1_tot/u/p`, `HIPK2_tot`, `Wip1_tot` | Molecule count | Damage and state-resolved upstream regulators. | Resolve damage accumulation and the ATM/Wip1 feedback timing. |
| `p53_tot`, `p53_0p`, `p53_arr`, `p53_kill` | Molecule count | Total p53 and its basal, paired-site-phosphorylated, and S46-phosphorylated forms. | Distinguish the two p53 transcriptional programs used by the gene functions. |
| Five `gene_*_on` and five `mRNA_*` observables | Molecule count | Active gene copies and corresponding transcripts. | Permit comparison of discrete gene switching with downstream transcript production. |
| `Mdm2_tot`, `Mdm2_cyt_0p`, `Mdm2_cyt_2p`, `Mdm2_nuc_2p`, `Mdm2_nuc_3p` | Molecule count | Mdm2 phosphorylation and encoded location states. | Track progression toward the nuclear p53-degrading forms. |
| `PI3K_tot`, `PTEN_tot`, `PIP2`, `PIP3`, `AKT_p` | Molecule count | Survival-pathway pools and active AKT. | Report the p53/PTEN opposition to PI3K signaling. |
| p21/Cyclin-E/Rb/E2F1 observables | Molecule count | Total/free proteins, p21–cyclin E and Rb–E2F1 complexes, and free phosphorylated Rb. | Resolve sequestration and release events in the arrest module. |
| Bax/BclXL/Bad/14-3-3 observables | Molecule count | Total/free apoptotic regulators plus the three principal complexes and Bad phosphorylation states. | Show how survival signaling changes free Bax availability indirectly through binding competition. |
| `Caspase_tot`, `Caspase_pro`, `Caspase_act` | Molecule count | Total, proenzyme, and active caspase. | Measure entry into the terminal positive-feedback state. |

## 8. Actions and simulation workflow

The file generates the reaction network and exports it as SBML, but it does not launch an ODE or stochastic simulation. The deterministic-versus-stochastic gene choice and irradiation switch therefore must be set before network generation, and downstream software is expected to simulate the exported network.

## 9. Technical caveats and ambiguities

- The metadata advertises ODE and SSA methods, but the active actions only generate and export a network.
- `STOCHASTIC_GENES` is zero in the supplied parameters, so the explicit gene-switching route is kinetically disabled while the function-driven route remains active.
- Spatial labels occur only on Mdm2; there are no physical compartments or nuclear/cytoplasmic volume factors.
- Broad molecule-count patterns may count molecules in complexes and should not be interpreted as unique complex counts.
- Several source comments use shorthand such as “arrester” and “killer”; these refer to modeled p53 phosphorylation classes, not independently declared molecules.
