# Coder Model Explanation: Three-step signaling cascade

## 1. Model identity and scope

- **Metadata id:** `05_threestep_m1`.
- **Purpose:** toy irreversible three-step cascade for fitting or workflow demonstrations.
- **Paths:** `Published/Mitra2019/05-threestep/m1.bngl` and same-directory `metadata.yaml`.

The implementation transfers a conserved population from A through B and C to D. The letters have no locally documented biological expansion.

## 2. BNGL block inventory

| Construct | Count | Contribution |
| --- | ---: | --- |
| Parameters | 4 | Three externally substituted rates and `Ainit`. |
| Molecule types | 4 | Site-free `A`, `B`, `C`, `D`. |
| Initial species | 1 | A-only starting pool. |
| Observables | 4 | Total count of each type. |
| Reaction rules | 3 | Irreversible A→B→C→D transfers. |
| Actions | 2 | Network generation and ODE integration. |
| Compartments / anchors / functions | 0 / 0 / 0 | No spatial or derived logic. |

## 3. Parameters, functions, and rate laws

`k1`, `k2`, and `k3` receive placeholder tokens `k1__FREE`, `k2__FREE`, and `k3__FREE`. They must be replaced or supplied by the fitting workflow before ordinary execution. Each is used as a first-order mass-action rate for its corresponding transfer. `Ainit=100` initializes A. There are no algebraic functions.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `A` | 0 | None | None | None | Source stage for rule 1. | Abstract. |
| `B` | 0 | None | None | None | Product of rule 1 and source for rule 2. | Abstract intermediate. |
| `C` | 0 | None | None | None | Product of rule 2 and source for rule 3. | Abstract intermediate. |
| `D` | 0 | None | None | None | Terminal product. | No outgoing rule. |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial and has no anchors. `A()` starts at 100; B, C, and D are absent initially and appear only through conversion. Total A+B+C+D is conserved because each rule consumes one upstream molecule and creates one downstream molecule.

## 6. Complete reaction-rule inventory

| # | Direction and participants | Exact modeled change | Rate | Technical meaning |
| ---: | --- | --- | --- | --- |
| 1 | One-way; A and B | Removes one site-free `A()` and creates one site-free `B()`; no state or bond edit exists. | `k1` | First-stage population transfer. |
| 2 | One-way; B and C | Removes `B()` and creates `C()`. | `k2` | Second-stage transfer and B turnover. |
| 3 | One-way; C and D | Removes `C()` and creates terminal `D()`. | `k3` | Final-stage transfer and D accumulation. |

## 7. Observables and technical readouts

All four are `Molecules` observables: `A` counts `A()`, `B` counts `B()`, `C` counts `C()`, and `D` counts `D()`. With no sites or complexes, each readout is also the complete population of that type. Their sum should remain 100 subject to numerical tolerance.

## 8. Actions and simulation workflow

`generate_network({overwrite=>1})` replaces any prior network. `simulate({method=>"ode",t_start=>0,t_end=>200,n_steps=>40,suffix=>"d1"})` runs deterministic ODE integration over 200 time units and requests 40 intervals; the suffix distinguishes its output files.

## 9. Technical caveats and ambiguities

The metadata title is grammatically incomplete, and A–D have no biological definitions. The `__FREE` tokens are fitting placeholders rather than numeric BNGL values, so standalone execution requires substitution. Because all transitions are irreversible and there are no source/sink terms, D necessarily becomes the terminal reservoir whenever all three rates are positive.
