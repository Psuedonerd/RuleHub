# Detailed Model Explanation: Dushek 2014 phosphorylation-coupled biosensor oligomerization model

## 1. Model overview

This abstract model couples a kinase–phosphatase cycle to the assembly state of a biosensor. Phosphorylation creates a site that can close against the sensor's own binding site or crosslink another sensor, while enzyme engagement temporarily marks the sensor as unavailable for those assembly reactions.

## 2. BNGL block inventory

The file contains 10 parameters, 3 molecule types, 3 seed species, 6 rules, 17 observables, and 3 actions. It has no enclosing model block, compartments, anchors, or functions.

## 3. Parameters, functions, and rate laws

The rate namespace is divided into enzyme binding/catalysis and biosensor closure. All rates are direct mass-action constants; no function or concentration-dependent expression modifies them.

| Parameter group or names | Function in this model |
| --- | --- |
| `Ekf`, `Ekb`, `Ekc` | Kinase capture, release, and catalytic phosphorylation. Binding is reversible; catalysis releases the kinase and leaves the sensor phosphorylated. |
| `Fkf`, `Fkb`, `Fkc` | Matching phosphatase capture, release, and catalytic dephosphorylation. |
| `kon1`, `koff1` | Intramolecular closure/opening of one phosphorylated biosensor. The forward value (1000) is much larger than the intermolecular association rate. |
| `kon2`, `koff2` | Intermolecular association/dissociation between a phosphorylated sensor site and another sensor's binding site. |

There are no active functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `E` | 1 | `b` | None | None | Abstract kinase whose sole site binds the sensor's `Y` site during phosphorylation. |
| `F` | 1 | `b` | None | None | Abstract phosphatase that binds the same `Y` site after phosphorylation. |
| `B` | 3 | `e`, `b`, `Y` | `e: 0, 1`; `Y: U, P` | None | Biosensor: `e` records enzyme engagement, `Y` carries phosphorylation and accepts a bond, and `b` supports self-closure or sensor–sensor crosslinking. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and begins with one free kinase, one free phosphatase, and 100 biosensors in the enzyme-free, unphosphorylated state. No closed or oligomerized sensors are seeded, so assembly requires kinase-driven production of `Y~P` first.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–2 form the kinase catalytic cycle, rules 3–4 mirror it for the phosphatase, and rules 5–6 compete for phosphorylated sensors through intra- versus intermolecular bonding.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | Kinase `E.b`; sensor `B.Y~U` with `e~0` | `E.b` binds `B.Y`, and sensor engagement changes `e: 0 ↔ 1`; `Ekf`/`Ekb`. | Captures an unphosphorylated sensor in the kinase-bound intermediate required for rule 2. |
| 2 | One-way | Kinase-bound sensor with `Y~U` and `e~1` | Releases the E–B bond, changes `Y: U → P` and `e: 1 → 0`, and uses `Ekc`. | Completes phosphorylation while recycling kinase and exposing the phosphotyrosine-like assembly site. |
| 3 | Reversible | Phosphatase `F.b`; sensor `B.Y~P` with `e~0` | `F.b` binds `B.Y`, with `e: 0 ↔ 1`; `Fkf`/`Fkb`. | Selects phosphorylated sensors for reversal of the kinase output. |
| 4 | One-way | Phosphatase-bound sensor with `Y~P` and `e~1` | Releases F, changes `Y: P → U` and `e: 1 → 0`, and uses `Fkc`. | Dephosphorylates the sensor and removes its ability to close or crosslink. |
| 5 | Reversible | One enzyme-free sensor; its own `Y~P` and `b` sites | Creates/releases an intramolecular `Y–b` bond at `kon1`/`koff1`; phosphorylation is retained. | Sequesters the phosphorylated site in a closed monomer, competing with oligomer growth. |
| 6 | Reversible | Two enzyme-free sensors; one `Y~P`, the other free `b` | Creates/releases an intermolecular `Y–b` bond at `kon2`/`koff2`. | Builds chains or larger sensor assemblies whose size distribution is reported by `V2`–`V15`. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `W` | Molecule count | Open sensors plus enzyme-engaged sensors, across the listed phosphorylation/engagement alternatives | Composite “state 1” pool; because it sums alternatives, it should not be interpreted as phosphorylation alone. |
| `U` | Molecule count | Sensors closed through their own `b–Y~P` bond | Intramolecularly closed “state 2” sensors. |
| `V2`–`V15` | Species count | Complete species containing exactly 2 through 15 B molecules, respectively | Oligomer-size distribution; each observable isolates one aggregate stoichiometry. |
| `E` | Molecule count | Kinase whose `b` site is occupied | Sequestered enzyme in the phosphorylation intermediate. |

## 8. Actions and simulation workflow

The file generates a network with a maximum aggregate of 15, then overwrites it with a second network capped at aggregate size 2, and finally writes a MATLAB model file. No simulation is run, so an external caller must decide which generated network is intended and execute it.

## 9. Technical caveats and ambiguities

- `E`, `F`, and `B` are deliberately abstract; metadata associates the model with T-cell receptor signaling but does not map these symbols to named proteins.
- The two consecutive overwrite operations use conflicting aggregate limits, making the final exported network dependent on action semantics.
- `B==N` species-count syntax and spaced action names/keys may be parser-sensitive.
- Molecule-count observables can count pattern matches, whereas `V2`–`V15` count complete species by stoichiometry.
