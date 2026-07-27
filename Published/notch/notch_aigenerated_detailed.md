# Coder Model Explanation: Notch

## 1. Model identity and scope

- **Metadata id/title:** `notch` / Notch.
- **Paths:** `Published/notch/notch.bngl` and `Published/notch/metadata.yaml`.
- **Purpose:** sketch of Notch maturation, ligand-triggered intracellular-domain release, nuclear import, and ICN–CSL–MAML complex assembly, based on Figure 2 of Grabner et al.

ICN denotes intracellular Notch, DSL denotes the Delta/Serrate/LAG-2 ligand family, CSL denotes the DNA-binding transcription factor family, and MAML denotes Mastermind-like coactivator.

## 2. BNGL block inventory

The source uses legacy `begin molecules` and `begin species` syntax and has no outer model wrapper.

| Construct | Count | Contribution |
| --- | ---: | --- |
| Parameters | 10 | Eight initial totals and shared `kp1`/`km1`. |
| Molecule declarations | 8 | Notch, ICN, OFUT1, Fringe, Furin, DSL, CSL, MAML. |
| Initial species | 8 | ER-localized receptor/ICN plus free processing and nuclear factors. |
| Reaction rules | 6 | Two maturation steps, ligand binding, cleavage/import, and two nuclear binding steps. |
| Observables | 2 | Precursor Notch–ICN and nuclear ternary complex. |
| Inline actions | 1 | Network generation only. |
| Compartments / anchors / functions | 0 / 0 / 0 | Localization is encoded as internal states, not spatial grammar. |

## 3. Parameters, functions, and rate laws

`ICN_tot`, `Notch_tot`, `Fringe_tot`, `Furin_tot`, `OFUT1_tot`, `DSL_tot`, `CSL_tot`, and `MAML_tot` are each 100. `kp1=0.1` drives all one-way maturation/cleavage events and every forward association. `km1=0.1` drives the three reverse binding directions (DSL, CSL, and MAML binding). No functions or time-dependent rate laws occur.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Notch` | 3 | `location`, `DSLbind`, `Ibind` | `location~ER~G~M` | None | `DSLbind` captures DSL; `Ibind` binds ICN; location state encodes ER/Golgi/membrane. | Localization is not a true compartment. |
| `ICN` | 4 | `location`, `Nbind`, `CSLbind`, `MAMLbind` | `location~ER~G~M~N` | None | `Nbind` binds Notch; `CSLbind` binds CSL; `MAMLbind` binds MAML; `N` means nucleus. | Separate molecule from Notch. |
| `OFUT1` | 0 | None | None | None | Catalyst in rule 1. | Carried through unchanged. |
| `Fringe` | 0 | None | None | None | Catalyst in rule 2. | No explicit glycan state. |
| `Furin` | 0 | None | None | None | Catalyst in rule 2. | No explicit cleavage state. |
| `DSL` | 1 | `Nbind` | None | None | Binds `Notch.DSLbind`. | Ligand family abstraction. |
| `CSL` | 2 | `Ibind`, `MAMLbind` | None | None | `Ibind` binds `ICN.CSLbind`; `MAMLbind` binds `MAML.Cbind`. | Nuclear location is only implied by ICN state. |
| `MAML` | 2 | `Cbind`, `Ibind` | None | None | `Cbind` binds `CSL.MAMLbind`; `Ibind` binds `ICN.MAMLbind`. | Makes two bonds in the ternary complex. |

## 5. Compartments, anchors, initial species, and setup

No compartment or anchor block exists. Instead, `location` states stand for endoplasmic reticulum (`ER`), Golgi (`G`), membrane (`M`), and nucleus (`N`). Notch and ICN each start as separate unbound pools at `location~ER`, both abundance 100. OFUT1, Fringe, Furin, DSL, CSL, and MAML each start free at 100. Thus the initial Notch and ICN are not pre-bound even though rule 1 creates their first bond.

## 6. Complete reaction-rule inventory

### Rule-family orientation

The first two rules collapse processing and movement into state rewrites. Rule 3 is ordinary reversible ligand binding. Rule 4 removes the Notch–ICN bond while changing ICN location. Rules 5 and 6 assemble the nuclear complex; the source labels both as rule “5,” so table numbering below follows file order.

| # | Source label | Direction and participants | Exact site/state/bond edit | Rate(s) | Technical meaning |
| ---: | --- | --- | --- | --- | --- |
| 1 | `1 Fucosylation...` | One-way; Notch, ICN, catalytic OFUT1 | Changes `Notch.location ER→G` and `ICN.location ER→G`; forms `Notch.Ibind–ICN.Nbind`; OFUT1 appears unchanged on both sides. | `kp1` | Lumps fucosylation, ER-to-Golgi movement, and precursor heterodimerization. |
| 2 | `2 Glycosylation...` | One-way; bound Notch–ICN plus catalytic Furin and Fringe | Changes both locations `G→M`; retains the existing Notch–ICN bond; Furin and Fringe are unchanged. | `kp1` | Lumps glycosylation, S1 cleavage, membrane movement, and mature heterodimer formation. |
| 3 | `3 DSL binding` | Reversible; Notch and DSL | Forms/releases `Notch.DSLbind–DSL.Nbind`; requires `Notch.location~M`. | `kp1`, `km1` | Reversible ligand occupancy of membrane-state Notch. |
| 4 | `4 S2, S3 cleavage...` | One-way; ligand-bound Notch–ICN complex | Releases `Notch.Ibind–ICN.Nbind`; preserves the unspecified existing DSL bond; changes `ICN.location M→N`; Notch remains `M`. | `kp1` | Lumps proteolysis, ICN dissociation, and nuclear entry. |
| 5 | first source `5` | Reversible; nuclear ICN and CSL | Forms/releases `ICN.CSLbind–CSL.Ibind`; requires `ICN.location~N`; leaves `ICN.MAMLbind` and `CSL.MAMLbind` free. | `kp1`, `km1` | Binary nuclear ICN–CSL assembly. |
| 6 | second source `5` | Reversible; ICN–CSL complex and MAML | Simultaneously forms `ICN.MAMLbind–MAML.Ibind` and `CSL.MAMLbind–MAML.Cbind`; preserves the ICN–CSL bond. Reverse direction releases both MAML bonds together. | `kp1`, `km1` | Cooperative-looking ternary-complex completion encoded as one two-bond event. |

## 7. Observables and technical readouts

The legacy declarations omit an explicit `Molecules` or `Species` keyword.

| Name | Declared target | Technical interpretation |
| --- | --- | --- |
| `Notch_ICN_Complex` | Connected `Notch.ICN` pattern without site constraints | Counts matches containing a Notch–ICN bond, chiefly the Golgi/membrane precursor generated by rules 1–2. |
| `Nucleus_complex` | Connected `ICN.CSL.MAML` pattern | Counts ternary ICN–CSL–MAML assemblies; the location is not written in the readout but rule 6 derives from nuclear ICN. |

## 8. Actions and simulation workflow

`generate_network({overwrite=>1})` is the sole inline action. It regenerates the network but does not simulate it, export SBML, or specify output times. A caller must add an ODE/SSA action or use the generated network externally.

## 9. Technical caveats and ambiguities

The source comments explicitly describe the signaling steps as sketchy. Localization is encoded as molecule state, so there are no volumes, transport rates tied to compartment geometry, or anchor constraints. Rules 1–2 treat OFUT1, Furin, and Fringe as unchanged catalysts while lumping several biological events. Rule 6 forms or removes two MAML bonds in one elementary event. Duplicate source label `5`, untyped observables, legacy syntax, and the metadata's `bng2_compatible: false` all merit parser-specific testing.
