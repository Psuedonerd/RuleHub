# Detailed Model Explanation: Barua 2013 beta-catenin destruction-complex model

## 1. Model overview

This model assembles beta-catenin with APC and the AXIN scaffold, recruits CK1a and GSK3b, and applies the ordered phosphorylations that accelerate beta-catenin degradation. Multivalent intracomplex contacts stabilize the destruction complex, while synthesis, dephosphorylation, degradation marking, and rapid partner release control beta-catenin turnover.

## 2. BNGL block inventory

The file contains 25 parameters, 7 molecule types, 7 initial species, 29 rules, 5 observables, and 2 actions. It has no model wrapper, compartments, anchors, or functions and uses `begin species` rather than `begin seed species`.

## 3. Parameters, functions, and rate laws

Free association uses interface-specific on/off pairs; the same interactions receive a large `chi` multiplier when they close within an existing complex. Modification, synthesis, degradation marking, and post-degradation release use direct one-way rates.

| Parameter group or names | Function in this model |
| --- | --- |
| `BCATtot`, `APCtot`, `AXINtot`, `GSKtot`, `CK1atot` | Initial pools. AXIN is tenfold less abundant than APC, GSK3b, or CK1a and therefore acts as the limiting scaffold. |
| `kf1_bap/kr1_bap`, `kf2_bap/kr2_bap` | Beta-catenin binding to APC through ARM59–a15 or ARM34–phospho-a20 interfaces. |
| `kf_ba/kr_ba`, `kf_apa/kr_apa` | Beta-catenin–AXIN and APC–AXIN binding. |
| `kf_ga/kr_ga`, `kf_ca/kr_ca` | Recruitment of GSK3b and CK1a to AXIN. |
| `chi` | Effective-concentration multiplier for association when the candidate sites already occupy one connected complex. |
| `kpb`, `kmpb`; `kp`, `kmp` | Beta-catenin phosphorylation/dephosphorylation and APC a20 phosphorylation/dephosphorylation. |
| `ksb`, `kdb1`, `kdb2` | Constitutive beta-catenin synthesis and slow/fast conversion from live to degraded state; S33/S37 phosphorylation selects the faster route. |
| Literal rate `1000` | Rapid release of APC or AXIN contacts from degradation-marked beta-catenin. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `AXIN` | 4 | `rgs`, `gid`, `b`, `e` | None | None | Central scaffold binding APC, GSK3b, beta-catenin, and CK1a through separate interfaces. |
| `APC` | 3 | `a15`, `a20`, `s` | `a20: U, P` | None | Multivalent beta-catenin partner: a15 binds ARM59, phospho-a20 binds ARM34, and `s` binds AXIN. |
| `bCat` | 5 | `s33s37`, `s45`, `ARM34`, `ARM59`, `ss` | `s33s37: U, P`; `s45: U, P`; `ss: l, d` | None | Beta-catenin substrate carrying ordered phosphosites, APC/AXIN-binding ARM regions, and a live/degraded status flag. |
| `GSK3b` | 1 | `a` | None | None | AXIN-recruited kinase associated with beta-catenin S33/S37 and APC a20 phosphorylation. |
| `CK1a` | 1 | `e` | None | None | AXIN-recruited kinase associated with priming beta-catenin at S45. |
| `I` | 0 | None | None | None | Conserved source marker that produces beta-catenin without being consumed. |
| `dead` | 0 | None | None | None | Zero-seeded marker not used by any active rule. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and begins with free, live beta-catenin unphosphorylated at both regulatory sites, unphosphorylated APC, and free AXIN, GSK3b, and CK1a. A single `I` source marker drives ongoing beta-catenin production; `dead` starts at zero and remains unused. No destruction complexes or degradation-marked beta-catenin are seeded.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–15 assemble free and multivalent destruction-complex contacts. Rules 16–24 carry out ordered phosphorylation, reversal, synthesis, and degradation marking; rules 25–29 rapidly detach partners after beta-catenin enters the degraded state.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–3 | Reversible | Beta-catenin `ARM59` and APC `a15`; rule 1 is free association, rules 2–3 close the contact inside complexes already linked through AXIN or APC a20 | Creates/releases ARM59–a15 at `kf1_bap/kr1_bap`; intracomplex rules multiply only the forward rate by `chi`. | Provides the first APC–beta-catenin interface and lets preassembled complexes gain avidity. |
| 4–5 | Reversible | Beta-catenin `ARM34` and phosphorylated APC `a20`; rule 5 begins from an existing ARM59–a15 contact | Creates/releases ARM34–a20 at `kf2_bap/kr2_bap`, with `chi` on the intracomplex forward step. | Makes APC phosphorylation enable a second, bivalent beta-catenin contact. |
| 6–7 | Reversible | Beta-catenin `ARM34` and AXIN `b`; free in rule 6 and APC-co-confined in rule 7 | Creates/releases ARM34–b at `kf_ba/kr_ba`; rule 7 uses `chi*kf_ba`. | Recruits beta-catenin directly to AXIN and closes APC-mediated loops. |
| 8–10 | Reversible | APC `s` and AXIN `rgs`; APC a20 is unphosphorylated, phosphorylated/free, or phosphorylated/occupied | Creates/releases the scaffold contact at `kf_apa/kr_apa` with no state change. | Allows APC recruitment across every a20 occupancy state rather than coupling scaffold binding to one beta-catenin configuration. |
| 11–13 | Reversible | The same APC–AXIN sites inside preassembled APC–beta-catenin–AXIN complexes with the three a20 states from rules 8–10 | Closes/releases `s–rgs` with `chi*kf_apa/kr_apa`. | Stabilizes multivalent destruction complexes after the components are already co-confined. |
| 14–15 | Reversible | GSK3b `a`–AXIN `gid` or CK1a `e`–AXIN `e` | Creates/releases the kinase–scaffold bond at `kf_ga/kr_ga` or `kf_ca/kr_ca`. | Loads the two kinases onto distinct AXIN sites for local substrate modification. |
| 16–18 | One-way | Beta-catenin plus CK1a (rule 16), S45-phosphorylated beta-catenin plus GSK3b (rule 17), or APC plus GSK3b (rule 18) in the same connected complex | Changes bCat `s45: U → P`, then `s33s37: U → P`, or APC `a20: U → P`; rates `kpb`, `kpb`, and `kp`. Existing bonds persist. | Encodes S45 priming before S33/S37 phosphorylation and creates the phospho-APC binding interface. |
| 19–21 | One-way | Phospho-bCat S45, phospho-bCat S33/S37, or phospho-APC in an AXIN complex | Reverses the respective site `P → U` at `kmpb`, `kmpb`, or `kmp`. | Opposes kinase activity and can destabilize phospho-dependent beta-catenin capture. |
| 22 | One-way | Conserved `I` source marker | Creates free, live, doubly unphosphorylated beta-catenin at `ksb` while retaining `I`. | Maintains constitutive beta-catenin input. |
| 23–24 | One-way | Live beta-catenin with S33/S37 unphosphorylated or phosphorylated | Changes `ss: l → d` at slow `kdb1` or fast `kdb2`. | Makes S33/S37 phosphorylation accelerate entry into the degraded state. |
| 25–27 | One-way | Degraded beta-catenin bound to APC through ARM59–a15 (rules 25–26) or ARM34–phospho-a20 (rule 27) | Breaks the named bond at literal rate `1000`; rule 25/27 separate the displayed partners, while rule 26 leaves them connected through another unspecified contact. | Rapidly strips APC contacts after degradation without always forcing complete complex breakup. |
| 28–29 | One-way | Degraded beta-catenin bound to AXIN through ARM34–b | Breaks ARM34–b at `1000`; rule 28 separates the partners, whereas rule 29 preserves connectivity through another bond. | Releases AXIN for reuse after beta-catenin degradation. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `bcat_tot` | Molecule count | Live beta-catenin (`ss~l`) | Total nondegraded substrate pool. |
| `bCat_pS45`, `bCat_pS33S37` | Molecule count | Live beta-catenin phosphorylated at the named site | Priming and degradation-associated phosphorylation stages. |
| `APC_p20a` | Molecule count | APC with phosphorylated a20, whether free or bound | Availability of the ARM34-binding APC state. |
| `BCat_Axin` | Species count | Complete species containing a live ARM34–AXIN-b bond | Direct beta-catenin recruitment to AXIN; species counting avoids treating a partial pattern as a free molecule count. |

## 8. Actions and simulation workflow

The file generates a network capped at one APC, one AXIN, and one beta-catenin per species, then runs a sparse ODE simulation to time 250,000 with 2,500 output steps. The action uses tight tolerances but spells the absolute-tolerance key as `atoll`.

## 9. Technical caveats and ambiguities

- One local metadata file describes JAK2–SH2B signaling, but the BNGL clearly implements beta-catenin destruction.
- The beta-catenin seed contains a doubled comma, and `atoll` may be an invalid action key.
- Kinases in rules 16–18 are required only as members of the same connected complex; no catalytic-site bond is specified.
- Rules 26 and 29 rely on an unshown alternative bond to keep products connected.
- Nullary `I`/`dead` syntax and the bounded `max_stoich` map may be parser-sensitive.
