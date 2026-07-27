# Detailed Model Explanation: Dushek 2014 biosensor oligomerization model

## 1. Model identity and scope

`Dushek_2014` is described by its metadata as a T-cell receptor signaling-dynamics model, while the BNGL itself deliberately abstracts the mechanism to kinase `E`, phosphatase `F`, and biosensor `B`. The model couples reversible enzyme engagement and phosphorylation to intra- and intermolecular biosensor binding. Sources: `Published/Dushek2014/Dushek_2014.bngl` and `Published/Dushek2014/Dushek_2014_metadata.yaml`.

## 2. BNGL block inventory

The file has 10 parameters, 3 molecule types, 3 seed-species declarations, 6 reaction rules, 17 observables, and 3 actions. It has no model wrapper, compartments, anchors, functions, or energy patterns. A reaction network is generated twice with different aggregate limits before MATLAB export.

## 3. Parameters, functions, and rate laws

- Kinase engagement uses `Ekf=10`, `Ekb=1`, and catalytic `Ekc=1`; phosphatase engagement analogously uses `Fkf=10`, `Fkb=1`, and `Fkc=1`.
- Intramolecular biosensor closure uses `kon1=1000`, `koff1=1`; intermolecular biosensor association uses `kon2=10`, `koff2=1`.
- There are no functions. All rates are direct parameter references.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `E` | 1 | `b` | None | None | `b` binds phosphorylatable `B.Y` during kinase engagement | Abstract kinase |
| `F` | 1 | `b` | None | None | `b` binds phosphorylated `B.Y` during phosphatase engagement | Abstract phosphatase |
| `B` | 3 | `e`, `b`, `Y` | `e: 0,1`; `Y: U,P` | None | `Y` is the modification/binding site; `b` supports intra- or intermolecular links; `e` marks enzyme-bound (`1`) versus free (`0`) sensor | Abstract biosensor |

## 5. Compartments, anchors, initial species, and setup

There are no compartments or anchors. Initial pools are one free `E(b)`, one free `F(b)`, and 100 unbound, unphosphorylated sensors `B(e~0,b,Y~U)`. No phosphorylated or oligomerized biosensor is seeded.

## 6. Complete reaction-rule inventory

The six rules form three reversible/catalytic modules: kinase processing, phosphatase processing, and phosphorylation-dependent sensor closure/oligomerization. The `e` state is an engagement flag, whereas `Y` carries the biochemical phosphorylation state.

| # | Direction | Participants and required context | Bond or state change | Rate(s) | Implementation consequence |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | kinase `E.b`; unphosphorylated sensor `B.Y~U` with `e~0` | Create/remove `E.b–B.Y`; `B.e` follows `0↔1` | `Ekf`; `Ekb` | Captures kinase on an unmodified sensor and records enzyme engagement in `e`. |
| 2 | One-way | the kinase–sensor complex from rule 1 | Break `E.b–B.Y`; `B.Y`: `U→P`; `B.e`: `1→0` | `Ekc` | Completes catalysis, releases kinase, and leaves a phosphorylated sensor. |
| 3 | Reversible | phosphatase `F.b`; phosphorylated sensor `B.Y~P` with `e~0` | Create/remove `F.b–B.Y`; `B.e` follows `0↔1` | `Fkf`; `Fkb` | Captures phosphatase specifically on the phosphorylated sensor. |
| 4 | One-way | the phosphatase–sensor complex from rule 3 | Break `F.b–B.Y`; `B.Y`: `P→U`; `B.e`: `1→0` | `Fkc` | Completes dephosphorylation and releases phosphatase. |
| 5 | Reversible | one enzyme-free phosphorylated sensor | Create/remove an internal `B.b–B.Y` bond | `kon1`; `koff1` | Moves a single sensor between open and self-closed conformations. |
| 6 | Reversible | two enzyme-free sensors, one exposing `Y~P` and the other `b` | Create/remove an intermolecular `Y–b` bond | `kon2`; `koff2` | Extends or shortens sensor oligomers through phosphotyrosine-dependent crosslinks. |

## 7. Observables and technical readouts

- Molecules `W` sums free phosphorylated `B(e~0,b,Y~P)`, free unphosphorylated `B(e~0,b,Y~U)`, and enzyme-engaged `B(e~1,b)` patterns (comma-separated alternatives).
- Molecules `U` counts intramolecularly closed `B(e~0,b!1,Y~P!1)`.
- Species `V2` through `V15` separately count complete species containing exactly 2 through 15 `B` molecules (`B==N`).
- Molecules `E` counts kinase whose `b` site is bound (`E(b!+)`), i.e. sequestered kinase.

## 8. Actions and simulation workflow

The first `generate network` requests overwrite and `max agg=>15`; the second immediately regenerates with overwrite and `max agg=>2`. `writeMfile({})` then exports the current network as MATLAB code. No simulation action is present in the file.

## 9. Technical caveats and ambiguities

The biological mapping of `E`, `F`, and `B` is intentionally abstract and is not resolved by local comments. The `B==N` syntax and spaced action keys (`generate network`, `max agg`) are parser-sensitive extensions, consistent with the metadata's reported VCell/action parsing issues. Because the second overwrite generation follows the 15-mer generation, tooling should verify which aggregate limit governs the exported MATLAB network.
