# Detailed Model Explanation: Barua 2012 B-Cell Receptor Signaling

## 1. Model overview

This model resolves early B-cell receptor (BCR) phosphorylation by the Src-family kinases Lyn and Fyn, recruitment and activation of Syk, and negative regulation through the PAG–Csk scaffold. Its central competition is between antigen-strength-scaled kinase amplification and Csk-driven phosphorylation of the inhibitory C-terminal sites of Lyn and Fyn.

## 2. BNGL block inventory

The model contains 118 parameters, 6 molecule types, 6 seed species, 76 logical reaction rules (108 physical source lines because continuations are used), 9 molecule-count observables, and 1 network-generation action. It contains no functions, compartments, or anchors.

## 3. Parameters, functions, and rate laws

The base constants `p1`–`p25` supply copy numbers and kinetic scales; descriptive aliases then map them to particular binding, phosphorylation, or dephosphorylation processes. Most rules use mass action. The dimensionless signal parameter `c` multiplies antigen-dependent phosphorylation rates and is zero in the supplied file, whereas free-kinase phosphorylation terms remain active.

| Parameter group or names | Function in this model |
| --- | --- |
| `p1`; `BT`, `LT`, `FT`, `PT`, `CT`, `ST` | Initialize equal total pools of BCR, Lyn, Fyn, PAG, Csk, and Syk from the common copy-number scale. |
| `c`, `p19`, `p20`, `p22`, `p23`, `p25` | Set signal-dependent phosphorylation. `c` gates receptor-associated Lyn/Fyn and Syk reactions; `p25` reduces Fyn catalytic rates relative to the corresponding Lyn rates. |
| `kf1/kr1`, `kf2a,b/kr2a,b`; `kf9/kr9`, `kf10a,b/kr10a,b` | Control Lyn or Fyn binding to unphosphorylated BCR through the unique domain and to singly/doubly phosphorylated Ig-alpha through SH2. |
| `kf3/kr3`, `kf11/kr11` | Close or open intramolecular SH2 contacts with phosphorylated Lyn Y508 or Fyn Y531, creating the autoinhibited conformations. |
| `kp4a`–`kp8c` | Lyn-catalyzed BCR ITAM phosphorylation, Lyn/Fyn activation-loop phosphorylation, and PAG-site phosphorylation in receptor-bound or free contexts. |
| `kp12a`–`kp16c` | Parallel Fyn-catalyzed reactions; `kp16b` is exactly zero, disabling direct Fyn phosphorylation of PAG Y163/Y181 in that context. |
| `kf17/kr17`, `kp18a,b` | Recruit Syk tandem SH2 to doubly phosphorylated Ig-beta and activate receptor-bound Syk by trans-phosphorylation. |
| `kf19*`, `kr19a`, `kf20*`, `kr20b`; `kf21*`, `kr21a`, `kf22*`, `kr22b` | Build one- or two-point Lyn–PAG and Fyn–PAG contacts through SH3–proline-rich and SH2–phosphotyrosine interactions. |
| `kf23/kr23`, `kp24`, `kp25` | Recruit Csk to PAG Y317 and let scaffolded Csk phosphorylate the Lyn/Fyn inhibitory tails. |
| `kdp26a,b`–`kdp31` | Remove phosphate stepwise from BCR ITAMs and from Lyn, Fyn, PAG, and Syk regulatory sites. |

There are no active functions; algebraic behavior is confined to parameter aliases such as `c*p19` and `c*p19/p25`.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `BCR` | 2 | `Y188_Y199`, `Y196_Y207` | each `0`, `P`, `PP` | None | Represents paired Ig-alpha and Ig-beta ITAM tyrosines; their phosphorylation states select kinase and Syk docking. |
| `Lyn` | 5 | `unique`, `SH3`, `SH2`, `Y397`, `Y508` | Y397/Y508: `0/P` | None | Src-family kinase with receptor/PAG binding domains, an activating loop site, and an inhibitory tail site. |
| `Fyn` | 5 | `unique`, `SH3`, `SH2`, `Y420`, `Y531` | Y420/Y531: `0/P` | None | Parallel Src-family kinase with analogous domains but distinct catalytic scaling and PAG specificity. |
| `PAG` | 5 | `PRS1`, `PRS2`, `Y317`, `Y163_Y181`, `Y387_Y417` | three tyrosine groups: `0/P` | None | Scaffold: PRS1/Y163-Y181 favor Fyn, PRS2/Y387-Y417 favor Lyn, and Y317 recruits Csk. |
| `Csk` | 1 | `SH2` | None | None | Inhibitory kinase recruited by phosphorylated PAG Y317. |
| `Syk` | 2 | `tSH2`, `Y525_Y526` | activation loop `0/P` | None | Binds doubly phosphorylated Ig-beta and becomes activated by trans-phosphorylation. |

## 5. Compartments, anchors, initial species, and setup

No spatial structure is declared. All six proteins start as free, unbound pools at the same nominal abundance; both BCR ITAM groups, kinase activation and inhibitory sites, PAG tyrosines, and Syk are initially unphosphorylated. Thus activity must emerge from the enabled phosphorylation reactions, but the default `c=0` suppresses the antigen-scaled receptor-associated pathways.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–23 cover Lyn recruitment, catalytic cross-talk, and PAG phosphorylation; 24–46 provide the corresponding Fyn arm; 47–49 activate Syk; 50–64 assemble the PAG scaffold and Csk inhibition; 65–76 reset all phosphosites.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–3 | Reversible | `BCR.Y188_Y199`; Lyn `unique` or `SH2` | Rule 1 binds unique domain to state `0`; rules 2–3 bind SH2 to `P` and `PP`, respectively, with state-specific off rates. | Recruits Lyn before phosphorylation and stabilizes it on phosphorylated Ig-alpha. |
| 4 | Reversible | Lyn `SH2`, `Y508=P` | Creates an intramolecular SH2–tail bond and reverses it at `kr3`. | Converts inhibitory-tail phosphorylation into physical Lyn autoinhibition. |
| 5–12 | One-way | BCR-bound Lyn `Y397=0/P`; BCR Ig-alpha or Ig-beta ITAM | Rules 5–8 phosphorylate Ig-alpha `0→P→PP`; 9–12 do the same for Ig-beta. Each pair distinguishes inactive versus active Lyn and doubles the first-step rate for two equivalent tyrosines. | Builds Syk docking sites and reinforces receptor signaling; all eight rates are proportional to `c`. |
| 13–16 | One-way | Receptor-bound or free Lyn `Y397` | Rules 13–14 activate BCR-bound Lyn; 15–16 activate free Lyn. In each context inactive or already active Lyn can catalyze `Y397:0→P`. | Supplies both antigen-scaled and basal Lyn activation routes. |
| 17–20 | One-way | Lyn `Y397`; Fyn `Y420`; BCR-bound or free context | Lyn changes Fyn `Y420:0→P`; rules 17–18 require receptor association, whereas 19–20 operate on free kinases. | Couples the two Src-family kinase pools. |
| 21–23 | One-way | Active Lyn; PAG `Y387_Y417`, `Y163_Y181`, `Y317` | Phosphorylates the Lyn docking group first, then the Fyn and Csk docking groups in SH2-tethered contexts. | Lets Lyn construct the PAG platform that eventually recruits its inhibitor. |
| 24–26 | Reversible | `BCR.Y188_Y199`; Fyn `unique` or `SH2` | Mirrors rules 1–3 for Fyn, binding state `0` through `unique` and `P/PP` through SH2. | Recruits Fyn to Ig-alpha across the receptor phosphorylation cycle. |
| 27 | Reversible | Fyn `SH2`, `Y531=P` | Creates or releases the intramolecular inhibitory-tail contact. | Implements Fyn autoinhibition. |
| 28–35 | One-way | BCR-bound Fyn `Y420=0/P`; both BCR ITAM groups | Rules 28–31 phosphorylate Ig-beta and 32–35 phosphorylate Ig-alpha, each `0→P→PP`; rates are antigen-scaled and divided by `p25`. | Provides the weaker parallel Fyn contribution to receptor phosphorylation. |
| 36–39 | One-way | Receptor-bound or free Fyn `Y420` | Activates Fyn `0→P` in receptor-bound (36–37) or free (38–39) contexts. | Combines signal-dependent and basal Fyn activation. |
| 40–43 | One-way | Fyn `Y420`; Lyn `Y397`; receptor-bound or free context | Active or inactive Fyn catalyzes Lyn `Y397:0→P`, with receptor variants proportional to `c`. | Makes Lyn–Fyn cross-activation bidirectional. |
| 44–46 | One-way | Active Fyn; PAG tyrosine groups | Phosphorylates PAG Y387/Y417 (44), Y163/Y181 (45), or Y317 (46); rule 45 uses disabled `kp16b=0`. | Allows Fyn to help construct PAG, except for the explicitly silent middle reaction. |
| 47 | Reversible | Syk `tSH2`; `BCR.Y196_Y207=PP` | Creates the tandem-SH2/Ig-beta bond and releases it at `kr17`. | Selectively recruits Syk to fully phosphorylated Ig-beta. |
| 48–49 | One-way | Receptor-bound Syk `Y525_Y526=0/P` | A neighboring bound Syk changes the target activation loop `0→P`; inactive or active Syk can serve as catalyst. | Amplifies Syk activity on phosphorylated receptor clusters. |
| 50–55 | One-way elementary steps | Lyn `SH3/SH2`; PAG `PRS2/Y387_Y417` | Add or release SH3–PRS2 and SH2–pY387/417 contacts from free or singly tethered states; rule 55 releases the doubly attached complex to free partners. | Resolves cooperative two-point Lyn docking rather than treating PAG binding as one event. |
| 56–61 | One-way elementary steps | Fyn `SH3/SH2`; PAG `PRS1/Y163_Y181` | Analogous steps form and dismantle the two-point Fyn–PAG interaction through PRS1 and phosphorylated Y163/Y181. | Positions Fyn on its preferred region of PAG. |
| 62 | Reversible | Csk `SH2`; `PAG.Y317=P` | Creates the Csk–PAG phosphotyrosine bond. | Recruits the negative-regulatory kinase to the scaffold. |
| 63–64 | One-way | PAG-associated Csk; Lyn `Y508` or Fyn `Y531` | Csk changes the kinase inhibitory tail `0→P` while the scaffold complex is retained. | Closes feedback by promoting the autoinhibited states in rules 4 and 27. |
| 65–68 | One-way | BCR Ig-alpha and Ig-beta ITAM states | Removes phosphate stepwise: `P→0` and `PP→P`; the second transitions use a factor of two. | Resets receptor docking and catalytic states. |
| 69–72 | One-way | Lyn `Y397/Y508`; Fyn `Y420/Y531` | Returns each activation-loop or inhibitory-tail site from `P→0`. | Balances kinase activation and Csk-dependent inhibition. |
| 73–75 | One-way | PAG `Y317`, `Y387_Y417`, `Y163_Y181` | Dephosphorylates each docking-site group independently. | Dismantles Csk and Src-family phosphotyrosine docking opportunities. |
| 76 | One-way | Syk `Y525_Y526` | Changes active Syk `P→0` at `kdp31`. | Terminates the downstream kinase signal. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Ig_alpha_P`, `Ig_alpha_PP`, `Ig_beta_PP` | Molecule count | Singly/doubly phosphorylated BCR ITAM groups. | Report receptor signal progression; no observable is provided for singly phosphorylated Ig-beta. |
| `Activated_Lyn`, `Activated_Fyn`, `Activated_Syk` | Molecule count | Kinases with phosphorylated activation-loop sites. | Measure catalytic-state abundance regardless of binding context. |
| `Autoinhibited_Lyn`, `Autoinhibited_Fyn` | Molecule count | Inhibitory-tail-phosphorylated kinase whose tail is bonded to SH2. | Require both phosphorylation and the intramolecular closed conformation, not tail phosphorylation alone. |
| `PAG1_Csk` | Molecule count | PAG with phosphorylated Y317 engaged in a bond. | Serves as the readout of assembled Csk negative feedback, although the partner is inferred by the rule set rather than named in the pattern. |

## 8. Actions and simulation workflow

The file generates and overwrites the reaction network with textual reaction output enabled; it does not run an ODE trajectory despite the metadata listing ODE compatibility. Because the default antigen-strength parameter is zero, users must change `c` before network generation to enable the receptor-associated phosphorylation and Syk amplification terms.

## 9. Technical caveats and ambiguities

- The source uses continued lines, so 108 active physical lines correspond to 76 logical rules; rule numbering here follows complete reactions, not line count.
- `c=0` makes all `c`-scaled phosphorylation rules kinetically silent, leaving basal free-kinase routes and dephosphorylation active.
- `kp16b` is independently zero, so one Fyn-to-PAG phosphorylation route remains disabled even if antigen strength is increased.
- `Autoinhibited_*` requires an internal SH2–tail bond; it is narrower than the total inhibitory-tail-phosphorylated pool.
- Wildcards and omitted components deliberately permit multiple surrounding complexes, so molecule-count observables can include many topologies.
