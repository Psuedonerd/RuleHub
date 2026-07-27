# Detailed Model Explanation: Kocieniewski 2012 scaffolded MAPK cascade

## 1. Model overview

This model represents a three-layer MAP3K–MAP2K–MAPK cascade organized by a scaffold with one docking site for each kinase layer. Activation is passed only between kinases co-bound to the same scaffold, while constitutive deactivation and dephosphorylation act regardless of scaffold occupancy.

## 2. BNGL block inventory

The model contains 10 parameters, 4 molecule types, 4 free seed species, 2 molecule-count observables, and 20 rules. It has no compartments, anchors, functions, or actions.

## 3. Parameters, functions, and rate laws

The model uses one common docking pair, one fast state-dependent release rate, one scaffold-local phosphorylation rate, and one global reversal rate. All kinetics are direct mass action; there are no algebraic or observable-dependent functions.

| Parameter group or names | Function in this model |
| --- | --- |
| `Atot`, `Btot`, `Ctot`, `Stot` | Initial totals for MAP3K, MAP2K, MAPK, and scaffold. MAPK starts fivefold more abundant than each other pool. |
| `a`, `d1` | Shared association and dissociation rates for ordinary kinase docking to the matching scaffold site. |
| `d2` | Fast one-way release of inactive MAP3K or doubly phosphorylated MAPK from scaffold, enforcing state-dependent unloading. |
| `S` | Basal conversion rate from inactive to active MAP3K. |
| `pscaff` | Phosphorylation rate for MAP2K or MAPK when the required upstream/downstream pair is co-docked. |
| `u` | Shared MAP3K deactivation and MAP2K/MAPK site-dephosphorylation rate. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `MAP3K` | 2 | `s`, `S` | `S: I, A` | None | Upstream kinase; `s` docks to the scaffold and active `S~A` phosphorylates co-docked MAP2K. |
| `MAP2K` | 3 | `s`, `R1`, `R2` | `R1: Y, Yp`; `R2: Y, Yp` | None | Middle kinase; both regulatory sites must be phosphorylated before it can modify co-docked MAPK. |
| `MAPK` | 3 | `s`, `R1`, `R2` | `R1: Y, Yp`; `R2: Y, Yp` | None | Output kinase whose two phosphorylation sites are modified on scaffold and reversed globally. |
| `Scaff` | 3 | `map3k`, `map2k`, `mapk` | None | None | Typed docking platform that can hold one kinase from each cascade layer simultaneously. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and starts with empty scaffold plus free inactive MAP3K and fully unphosphorylated MAP2K/MAPK. Initial totals are 100,000 for MAP3K, MAP2K, and scaffold and 500,000 for MAPK; no active or scaffold-bound complexes are seeded.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rule 1 supplies basal upstream activation. Rules 2–11 load and unload kinases according to modification state, rules 12–15 pass phosphorylation down co-occupied scaffold slots, and rules 16–20 erase kinase activation or phosphorylation without requiring scaffold release.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | Free MAP3K `S~I` | Changes `S: I → A` at rate `S`; the docking site remains free. | Creates the active upstream kinase that can enter the scaffolded cascade. |
| 2–3 | Reversible in rule 2; one-way in rule 3 | MAP3K `s` and scaffold `map3k`; rule 2 requires `S~A`, rule 3 requires scaffold-bound `S~I` | Rule 2 docks/releases active MAP3K at `a`/`d1`; rule 3 releases inactive MAP3K at fast rate `d2`. | Retains active MAP3K through ordinary affinity but rapidly clears it after global deactivation. |
| 4–7 | Reversible | MAP2K `s` and scaffold `map2k`; rules 4–7 cover `R1/R2` states `Y/Y`, `Yp/Y`, `Y/Yp`, and `Yp/Yp` | Every phosphorylation state docks with the same `a`/`d1`; no regulatory state changes during binding. | Lets MAP2K remain scaffold-accessible throughout its two-step phosphorylation cycle. |
| 8–11 | Reversible in rules 8–10; one-way in rule 11 | MAPK `s` and scaffold `mapk`; rules 8–10 cover unmodified and singly phosphorylated forms, rule 11 the doubly phosphorylated form | The first three states dock at `a`/`d1`; doubly phosphorylated MAPK is released at `d2`. | Loads substrate MAPK for modification, then rapidly ejects the completed two-site product. |
| 12–13 | One-way | Active scaffold-bound MAP3K and scaffold-bound MAP2K; MAP2K `R1~Y` or `R2~Y` | Changes MAP2K `R1` in rule 12 or `R2` in rule 13 from `Y → Yp` at `pscaff`, preserving both scaffold bonds. | Allows either order of the two MAP2K phosphorylation steps but only under scaffold colocalization. |
| 14–15 | One-way | Doubly phosphorylated scaffold-bound MAP2K and scaffold-bound MAPK; MAPK `R1~Y` or `R2~Y` | Changes MAPK `R1` in rule 14 or `R2` in rule 15 from `Y → Yp` at `pscaff`, retaining the complex. | Passes activity to the output layer; completion of both sites then triggers rule 11 unloading. |
| 16–20 | One-way | Active MAP3K, phospho-MAP2K `R1`/`R2`, or phospho-MAPK `R1`/`R2`, respectively | Rule 16 changes MAP3K `A → I`; rules 17–20 change the named site `Yp → Y`, all at `u` and with no binding constraint. | Provides uniform signal reversal for free and scaffold-bound kinases, allowing shutdown at every layer. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `MAPKchainone` | Molecule count | Scaffold carrying doubly phosphorylated MAP2K and MAPK phosphorylated at `R1` | Captures the lower-cascade complex after one MAPK modification; MAPK `R2` is unconstrained. |
| `MAPKchaintwo` | Molecule count | Scaffold carrying active MAP3K and doubly phosphorylated MAP2K | Captures an upper-cascade signaling complex competent to have completed MAP2K activation. |

## 8. Actions and simulation workflow

The file defines model logic only and includes no network-generation or simulation action. An external workflow must choose the simulator, duration, and output schedule.

## 9. Technical caveats and ambiguities

- Metadata describes “Actin dynamics,” but the BNGL is a scaffolded MAPK cascade.
- Rules 16–20 use partial patterns, so reversal can occur while a kinase remains scaffold-bound.
- The two observables report selected scaffold configurations rather than total active MAP2K or MAPK.
- MAP2K and MAPK sites are abstract `R1`/`R2` states; local files do not identify physical residues.
