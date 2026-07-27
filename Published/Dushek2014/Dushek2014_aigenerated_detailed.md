# Coder Model Explanation: Dushek 2014 biosensor oligomerization model

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

| # | Direction | Participants and exact edit | Rate(s) | Technical meaning |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | `E.b` binds `B.Y~U`, creating `E.b!1-B.Y!1`, while `B.e 0→1`; reverse removes that bond and restores the free pattern | `Ekf`, `Ekb` | Forms the kinase–unphosphorylated-sensor complex. |
| 2 | One-way | Bound `E.b!1-B.Y~U!1` separates; `B.Y U→P` and `B.e 1→0`, with `E.b` released | `Ekc` | Catalytic phosphorylation and kinase release. |
| 3 | Reversible | `F.b` binds `B.Y~P`, creating `F.b!1-B.Y!1`, while `B.e 0→1` | `Fkf`, `Fkb` | Forms the phosphatase–phosphorylated-sensor complex. |
| 4 | One-way | Bound `F.b!1-B.Y~P!1` separates; `B.Y P→U` and `B.e 1→0`, with `F.b` released | `Fkc` | Catalytic dephosphorylation and phosphatase release. |
| 5 | Reversible | Within one `B(e~0,b,Y~P)`, `B.b` binds its own `B.Y~P` as bond `!1`; no state changes occur | `kon1`, `koff1` | Intramolecular closure of a phosphorylated biosensor. |
| 6 | Reversible | `Y~P` of one `B(e~0)` binds `b` of another `B(e~0)` as bond `!1` | `kon2`, `koff2` | Extends or breaks intermolecular sensor oligomers. |

## 7. Observables and technical readouts

- Molecules `W` sums free phosphorylated `B(e~0,b,Y~P)`, free unphosphorylated `B(e~0,b,Y~U)`, and enzyme-engaged `B(e~1,b)` patterns (comma-separated alternatives).
- Molecules `U` counts intramolecularly closed `B(e~0,b!1,Y~P!1)`.
- Species `V2` through `V15` separately count complete species containing exactly 2 through 15 `B` molecules (`B==N`).
- Molecules `E` counts kinase whose `b` site is bound (`E(b!+)`), i.e. sequestered kinase.

## 8. Actions and simulation workflow

The first `generate network` requests overwrite and `max agg=>15`; the second immediately regenerates with overwrite and `max agg=>2`. `writeMfile({})` then exports the current network as MATLAB code. No simulation action is present in the file.

## 9. Technical caveats and ambiguities

The biological mapping of `E`, `F`, and `B` is intentionally abstract and is not resolved by local comments. The `B==N` syntax and spaced action keys (`generate network`, `max agg`) are parser-sensitive extensions, consistent with the metadata's reported VCell/action parsing issues. Because the second overwrite generation follows the 15-mer generation, tooling should verify which aggregate limit governs the exported MATLAB network.
