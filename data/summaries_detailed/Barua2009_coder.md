# Coder Model Explanation: Barua 2009

## 1. Model identity and scope

- **Model id:** `Barua_2009`
- **Title:** Barua 2009
- **BNGL path:** `Published/Barua2009/Barua_2009.bngl`
- **YAML path:** `Published/Barua2009/metadata.yaml`
- **Scope:** This signaling model represents JAK2-SH2B complex assembly. It focuses on SH2-mediated recruitment of SH2B to phosphorylated JAK2, SH2B dimerization through a dimerization domain, and JAK2 phosphorylation within a two-JAK2 scaffolded complex.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 8 kinetic/abundance parameters. |
| Compartments | No | No compartment declarations. |
| Molecule types | Yes | 2 molecule types: `S` and `J`. |
| Seed species | Yes | 2 initial species: free SH2B and singly phosphorylated JAK2. |
| Observables | Yes | 6 molecule-count readouts. |
| Functions | No | No function block. |
| Reaction rules | Yes | 4 reaction rules. |
| Actions | Inline commands | Network generation plus ODE simulation. |

## 3. Parameters, functions, and rate laws

| Parameter | Value | Role |
| --- | ---: | --- |
| `kon_dimer` | 1.0 | Association rate for SH2B dimerization through `DD`. |
| `koff_dimer` | 0.1 | Dissociation rate for the SH2B dimer. |
| `kon_SH2` | 1.0 | Association rate for SH2B `SH2` binding to JAK2 `Y1`. |
| `koff_SH2` | 0.1 | Dissociation rate for the JAK2-SH2B SH2 interaction. |
| `kphos_slow` | 0.1 | Slow phosphorylation rate when the opposite JAK2 in the dimer scaffold remains unphosphorylated at `Y`. |
| `kphos_fast` | 1.0 | Fast phosphorylation rate when the opposite JAK2 is already phosphorylated at `Y`. |
| `Jtot` | 0.000014 | Initial total JAK2 concentration. |
| `Stot` | 0.1 | Initial total SH2B concentration. |

There are no BNGL functions. All rules use direct mass-action constants. The two phosphorylation rules differ only in the phosphorylation state of the partner JAK2, making the second JAK2 phosphorylation faster once one JAK2 in the SH2B dimer assembly is already active.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- |
| `S` | 2 | `SH2`, `DD` | None | `SH2` binds the `Y1` site of JAK2; `DD` dimerizes two SH2B molecules. | Metadata describes this as SH2B. |
| `J` | 2 | `Y1`, `Y` | `Y1`: `P`; `Y`: `U`, `P` | `Y1` is the SH2B docking site and is initialized phosphorylated; `Y` is the regulated JAK2 activation/phosphorylation site. | `Y1` is declared only with state `P`, so the model does not represent unphosphorylated `Y1`. |

## 5. Initial species, compartments, and setup

The model starts with free SH2B, `S(SH2,DD)`, at `Stot`, and JAK2 with `Y1` phosphorylated and `Y` unphosphorylated at `Jtot`. There are no compartments. The initial setup therefore assumes that the JAK2 docking tyrosine is already in the state that can recruit SH2B, while the second JAK2 phosphorylation site is initially inactive.

## 6. Complete reaction-rule inventory

| # | Rule label/name | Direction | Participants and sites | Rate | Modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | JAK2-SH2B interaction | Reversible | `J.Y1` in state `P` binds `S.SH2` | `kon_SH2`, `koff_SH2` | Adds or removes a JAK2-SH2B bond | SH2B can dock onto phosphorylated JAK2 through its SH2 domain. |
| 2 | SH2B dimerization | Reversible | `S.DD` binds another `S.DD` | `kon_dimer`, `koff_dimer` | Adds or removes an SH2B-SH2B dimer bond | Two SH2B molecules can form a dimeric scaffold through their dimerization domains. |
| 3 | JAK2 phosphorylation, slow | One-way | In a JAK2-SH2B-SH2B-JAK2 complex, one JAK2 has `Y~U`; the partner JAK2 also has `Y~U` | `kphos_slow` | Converts one JAK2 `Y` site from `U` to `P` | A fully scaffolded but not-yet-activated two-JAK2 complex can slowly phosphorylate one JAK2 activation site. |
| 4 | JAK2 phosphorylation, fast | One-way | Same scaffolded complex, but the partner JAK2 already has `Y~P` | `kphos_fast` | Converts the remaining JAK2 `Y` site from `U` to `P` | Once one JAK2 in the scaffold is phosphorylated, phosphorylation of the second JAK2 is accelerated. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `J_mono` | `Molecules` | JAK2 with phosphorylated `Y1` | Counts JAK2 molecules that retain the SH2B docking state, regardless of whether they are bound. |
| `JS` | `Molecules` | JAK2 bound to one SH2B through `Y1`/`SH2`, with SH2B `DD` free | Reports the singly recruited JAK2-SH2B complex before SH2B dimerization. |
| `JSS` | `Molecules` | JAK2-SH2B-SH2B complex with one JAK2 | Reports the scaffold after SH2B dimerization but before the second JAK2 is necessarily recruited. |
| `JSSJ` | `Molecules` | Any complex containing two `J` molecules | Reports two-JAK2 assemblies, the structural context required by the phosphorylation rules. |
| `J_active` | `Molecules` | JAK2 with `Y~P` | Counts activated/phosphorylated JAK2 at the regulated `Y` site. |
| `J_inactive` | `Molecules` | JAK2 with `Y~U` | Counts inactive/unphosphorylated JAK2 at the regulated `Y` site. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1, max_stoich=>{J=>2}})` generates a reaction network while limiting generated species to at most two JAK2 molecules per complex.
2. `simulate_ode({t_end=>10000, n_steps=>10000, atoll=>1e-08, rtol=>1e-08, sparse=>1})` runs a long ODE simulation with tight tolerances and sparse linear algebra.

## 9. Technical caveats and ambiguities

- The model assumes JAK2 `Y1` is always phosphorylated; no rule creates or removes that state.
- `JSSJ` is a broad two-JAK2 observable and does not specify which JAK2 activation states are present.
- The YAML marks the model as not BNG2-compatible even though the source uses standard BNGL blocks plus inline actions.
