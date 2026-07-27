# Detailed Model Explanation: Barua 2007 multivalent receptor–SHP2 engagement model

## 1. Model overview

This model examines how a pre-dimerized phosphoreceptor recruits an SHP2-like protein through its N-terminal SH2, C-terminal SH2, and catalytic PTP domains. Opening of SHP2 enables multiple same-receptor and cross-dimer contacts, which stabilize distinct binding topologies while allowing the PTP domain to dephosphorylate receptor Y1.

## 2. BNGL block inventory

The file contains 24 parameters, 2 molecule types, 2 initial species, 23 rules, 1 observable, and 2 actions. It has no model wrapper, compartments, anchors, or functions; the rules use `exclude_reactants` filters on cytosolic recruitment.

## 3. Parameters, functions, and rate laws

Free-solution recruitment uses domain-specific on/off pairs, whereas intracomplex binding multiplies the appropriate on-rate by a topology-specific `chi_r` effective-concentration factor. Catalysis and receptor phosphorylation are one-way processes.

| Parameter group or names | Function in this model |
| --- | --- |
| `kdim`, `R_dim`, `S_tot` | `kdim` is declared but unused by active rules; `R_dim` and `S_tot` initialize pre-dimerized receptor and free SHP2-like protein. |
| `kopen`, `kclose` | Concerted transition between closed NSH2/PTP and open NSH2/PTP conformations. Closing is much faster than opening. |
| `kon_CSH2/koff_CSH2`, `kon_NSH2/koff_NSH2`, `kon_PTP/koff_PTP` | Cytosolic and intracomplex association/dissociation of each S domain with its receptor target. PTP dissociation is faster than either SH2 dissociation. |
| `kkin_Y1`, `kcat_PTP` | Receptor Y1 phosphorylation within a dimer and PTP-catalyzed Y1 dephosphorylation. |
| `chi_r1`–`chi_r11` | Topology-specific multipliers for second or third contacts made after S is already tethered to the receptor dimer; values distinguish same-receptor from cross-dimer geometries. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `R` | 3 | `DD`, `Y1`, `Y2` | `Y1: U, P`; `Y2: P` only | None | Pre-dimerized receptor: `DD` holds the receptor pair, Y2 recruits either SH2 domain, and Y1 is phosphorylated and contacted/dephosphorylated by the PTP domain. |
| `S` | 3 | `NSH2`, `CSH2`, `PTP` | `NSH2: C, O`; `PTP: C, O` | None | SHP2-like regulator whose NSH2 and PTP open together; its three domains can simultaneously engage sites across one or both receptors. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial. Receptor begins as a Y1-unphosphorylated, Y2-phosphorylated dimer at `R_dim`, while S begins free with closed NSH2 and PTP domains at `S_tot`. Thus Y2 docking sites are initially available, but NSH2/PTP recruitment requires the reversible opening transition; receptor Y1 must be phosphorylated by rule 1 before PTP engagement.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–7 create phospho-Y1, open S, recruit individual domains, and catalyze dephosphorylation. Rules 8–17 add a second S–receptor contact, and rules 18–23 close a third contact in already bidentate complexes.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | Receptor `Y1~U` within a `DD`-linked dimer | Changes `Y1: U → P` at `kkin_Y1`. | Creates the PTP substrate/interaction site while requiring receptor dimerization. |
| 2 | Reversible | Free S `NSH2` and `PTP` | Concertedly changes `NSH2: C ↔ O` and `PTP: C ↔ O` at `kopen/kclose`. | Controls access to the N-terminal SH2 and catalytic domains; CSH2 has no conformational state. |
| 3–5 | Reversible | Receptor Y2 with S CSH2 (rule 3), receptor Y2 with open NSH2 (rule 4), or receptor Y1~P with open PTP (rule 5) | Creates/releases the named single contact at its `kon/koff` pair; `exclude_reactants(2,R)` restricts the incoming S reactant from already containing another receptor. | Supplies three alternative first contacts from cytosol without conflating them with intracomplex closure. |
| 6–7 | One-way | PTP-bound receptor Y1~P | Both change `Y1: P → U` and release the PTP–Y1 bond at `kcat_PTP`; rule 6 yields separate R and S, whereas rule 7 keeps them in one complex through other unspecified bonds. | Catalytically removes phospho-Y1 while preserving multivalent complexes when another receptor contact still connects S. |
| 8, 11 | Reversible | S already tethered through CSH2 (rule 8) or NSH2 (rule 11); the other open SH2 domain and the partner receptor Y2 | Adds/releases the second SH2–Y2 contact using `chi_r1*kon_NSH2` or `chi_r1*kon_CSH2`, with the standard off-rate. | Bridges the two receptor subunits symmetrically through both SH2 domains. |
| 9–10, 12–13 | Reversible | S tethered by CSH2 or NSH2; open PTP; receptor Y1~P on the same receptor or its partner | Adds/releases PTP–Y1 using `chi_r2`/`chi_r3` after CSH2 or `chi_r5`/`chi_r4` after NSH2. | Makes catalytic-domain recruitment sensitive to whether PTP folds back onto the same receptor or spans the dimer. |
| 14–17 | Reversible | S tethered by PTP; free CSH2 or open NSH2; receptor Y2 on the same or partner receptor | Adds/releases the selected SH2–Y2 contact; `chi_r2/3` apply to CSH2 and `chi_r5/4` to NSH2 for same/other receptor geometry. | Builds the same bidentate topologies from a PTP-first route, preserving assembly-order alternatives. |
| 18–19 | Reversible | Both SH2 domains already occupy the two Y2 sites; open PTP and either receptor Y1~P | Adds/releases the third PTP contact with `chi_r6` when Y1 shares the CSH2-bound receptor or `chi_r7` when it shares the NSH2-bound receptor. | Completes tridentate engagement and distinguishes which side of the dimer carries the catalytic contact. |
| 20–23 | Reversible | PTP plus one SH2 already bound; the remaining SH2 domain and open receptor Y2 | Rules 20/21 add NSH2 with `chi_r8/9` when CSH2 and PTP are on the same/different receptors; rules 22/23 add CSH2 with `chi_r10/11` when NSH2 and PTP are on different/same receptors. | Closes the final SH2 contact in every remaining tridentate topology and enforces the thermodynamic geometry relations encoded by the `chi_r` values. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `pYR` | Molecule count | Receptor Y1 in state `P`, whether free or domain-bound | Total PTP-substrate phosphorylation; it reports the balance between rule 1 and rules 6–7 but does not distinguish S-binding topology. |

## 8. Actions and simulation workflow

The file generates the full network and runs a non-sparse ODE steady-state simulation to time 1,000 with 100 output steps. No stimulus change or separate equilibration phase is defined.

## 9. Technical caveats and ambiguities

- `R` and `S` are abstract names; the SHP2-like interpretation follows domain names and local model context.
- Y2 is permanently phosphorylated, and receptor dimerization is fixed in the seed rather than governed by active rules.
- Several product patterns remain connected without displaying the alternative bond that supplies connectivity; their meaning depends on the surrounding complex match.
- `exclude_reactants` and multiline rule modifiers may be parser-sensitive.
- `kdim` is declared but not used by active rules.
