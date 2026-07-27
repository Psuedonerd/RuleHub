# Coder Model Explanation: MAPK Monomers

## 1. Model identity and scope

- **Metadata id/title:** `mapk-monomers` / MAPK Monomers.
- **Paths:** `Published/mapkmonomers/mapk-monomers.bngl` and `Published/mapkmonomers/metadata.yaml`.
- **Purpose:** minimal Ste5-scaffolded Ste11→Ste7→Fus3 mitogen-activated protein kinase (MAPK) cascade without Ste5 dimerization.

## 2. BNGL block inventory

This file uses legacy top-level `begin molecules` and `begin species` blocks rather than a `begin model` wrapper.

| Construct | Count | Contribution |
| --- | ---: | --- |
| Parameters | 6 | Four initial totals and shared `kp`/`km`. |
| Molecule declarations | 4 | Ste5, Ste11, Ste7, Fus3. |
| Initial species | 4 | Free scaffold and inactive free kinases. |
| Reaction rules | 9 | Three docking, three phosphorylation, three dephosphorylation rules. |
| Observables | 5 | Total/free/scaffold-context phosphorylated Fus3. |
| Inline actions | 3 | Network, SBML export, ODE simulation. |
| Compartments / anchors / functions | 0 / 0 / 0 | Nonspatial, direct mass action. |

## 3. Parameters, functions, and rate laws

`S5_0`, `S11_0`, `S7_0`, and `F3_0` are all 100 and initialize Ste5, Ste11, Ste7, and Fus3. `kp=1` serves as every association rate and every phosphorylation rate. `km=1` serves as every dissociation and dephosphorylation rate. No function modifies these rates, so binding and catalytic processes share values despite representing different dimensions in conventional mass action.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Ste5` | 3 | `s1`, `s2`, `s3` | None | None | Docks Ste11 at `s1`, Ste7 at `s2`, Fus3 at `s3`. | Monomeric scaffold; no dimer site. |
| `Ste11` | 2 | `s1`, `Y` | `Y~U~P` | None | `s1` docks Ste5; `Y` is inactive/unphosphorylated (`U`) or phosphorylated (`P`). | Upstream tier. |
| `Ste7` | 2 | `s2`, `Y` | `Y~U~P` | None | `s2` docks Ste5; `Y` receives phosphorylation from Ste11. | Middle tier. |
| `Fus3` | 2 | `s3`, `Y` | `Y~U~P` | None | `s3` docks Ste5; `Y` receives phosphorylation from Ste7. | Output tier. |

## 5. Compartments, anchors, initial species, and setup

There are no spatial blocks. Free `Ste5(s1,s2,s3)`, inactive `Ste11(Y~U)`, inactive `Ste7(Y~U)`, and inactive `Fus3(Y~U)` each start at 100. Every docking site is initially free. No phosphorylated kinase or preassembled scaffold complex is initialized.

## 6. Complete reaction-rule inventory

### Rule-family orientation

Rules 1–3 load one kinase per dedicated Ste5 site. Rules 4–6 implement ordered phosphorylation and require the relevant kinase pair to share one Ste5. Rules 7–9 remove phosphorylation regardless of scaffold occupancy because their patterns constrain only `Y~P`.

| # | Direction and participants | Exact site/state/bond edit | Rate | Technical meaning |
| ---: | --- | --- | --- | --- |
| 1 | Reversible; Ste5, Ste11 | Forms/releases `Ste5.s1–Ste11.s1`. | `kp`, `km` | Ste11 docking. |
| 2 | Reversible; Ste5, Ste7 | Forms/releases `Ste5.s2–Ste7.s2`. | `kp`, `km` | Ste7 docking. |
| 3 | Reversible; Ste5, Fus3 | Forms/releases `Ste5.s3–Fus3.s3`. | `kp`, `km` | Fus3 docking. |
| 4 | One-way; Ste5-bound Ste11 | Preserves `Ste5.s1–Ste11.s1`; changes `Ste11.Y U→P`. | `kp` | Scaffold occupancy enables Ste11 activation without an explicit upstream catalyst. |
| 5 | One-way; Ste5, Ste11, Ste7 | Preserves `Ste5.s1–Ste11.s1` and `Ste5.s2–Ste7.s2`; requires `Ste11.Y~P`; changes `Ste7.Y U→P`. | `kp` | Active Ste11 phosphorylates colocalized Ste7. |
| 6 | One-way; Ste5, Ste7, Fus3 | Preserves `Ste5.s2–Ste7.s2` and `Ste5.s3–Fus3.s3`; requires `Ste7.Y~P`; changes `Fus3.Y U→P`. | `kp` | Active Ste7 phosphorylates colocalized Fus3. |
| 7 | One-way; Ste11 | Changes `Ste11.Y P→U`; binding state of `s1` is unconstrained. | `km` | Global Ste11 dephosphorylation. |
| 8 | One-way; Ste7 | Changes `Ste7.Y P→U`; `s2` is unconstrained. | `km` | Global Ste7 dephosphorylation. |
| 9 | One-way; Fus3 | Changes `Fus3.Y P→U`; `s3` is unconstrained. | `km` | Global Fus3 dephosphorylation. |

## 7. Observables and technical readouts

| Name | Type | Target | Interpretation |
| --- | --- | --- | --- |
| `Fus3_P_total` | Molecules | Any `Fus3(Y~P)` | Total phosphorylated Fus3. |
| `Fus3_P_cytosol` | Molecules | `Fus3(s3,Y~P)` | Phosphorylated Fus3 with free scaffold site; “cytosol” is a naming convention, not a compartment. |
| `Fus3_P_aggregate` | Molecules | `Fus3(s3!3,Y~P)` | Phosphorylated Fus3 bound through `s3`. |
| `Fus3_P_aggregate_Ste5` | Molecules | Ste5–Fus3 bond | Scaffold-bound phosphorylated Fus3. |
| `Fus3_P_aggregate_Ste7` | Molecules | Ste5-bound Ste7 connected to phosphorylated Fus3 through a bond between Ste7 `Y` and Fus3 `s3` | The pattern's bond topology does not match rule 6, which never forms a Ste7–Fus3 bond. This readout is likely zero or malformed relative to intent. |

## 8. Actions and simulation workflow

`generate_network()` constructs the finite network. `writeSBML()` exports Systems Biology Markup Language (SBML). `simulate_ode({t_end=>50,n_steps=>50})` runs deterministic integration to time 50 with 50 intervals. These are inline commands rather than a `begin actions` block.

## 9. Technical caveats and ambiguities

The legacy `molecules`/`species` syntax and absent model wrapper may affect modern parsers; metadata already marks BNG2 compatibility false. `kp` and `km` are reused across association, catalysis, dissociation, and dephosphorylation. “Cytosol” is not spatially encoded. Most importantly, `Fus3_P_aggregate_Ste7` requests a Ste7–Fus3 bond not created by any rule, so its intended topology should be curated.
