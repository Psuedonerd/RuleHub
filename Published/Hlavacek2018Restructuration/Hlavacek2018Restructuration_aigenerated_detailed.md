# Coder Model Explanation: Hlavacek2018Restructuration after decoupling

## 1. Model identity and scope

- **Selected pair:** `Published/Hlavacek2018Restructuration/after_decoupling.bngl` with the same-directory `metadata.yaml`.
- **Metadata id/title:** `Hlavacek2018Restructuration_after_bunching` / Hlavacek2018Restructuration.
- **Scope:** three independent binary-state populations and a function that reconstructs their expected joint-active abundance under factorization.

The metadata names `after_bunching`, not the selected `after_decoupling.bngl`; that mismatch is recorded rather than silently treated as model identity.

## 2. BNGL block inventory

| Construct | Count | Contribution |
| --- | ---: | --- |
| Parameters | 7 | Six transition rates plus common total `RTOT`. |
| Molecule types | 3 | Binary-state `X`, `Y`, and `Z`. |
| Initial species | 3 | One inactive pool per type. |
| Observables | 3 | Active-state species counts `X1`, `Y1`, `Z1`. |
| Functions | 1 | Factorized joint-active estimate `R111()`. |
| Reaction rules | 3 | One reversible switch per molecule. |
| Actions | 2 | Network generation and ODE simulation. |
| Compartments / anchors | 0 / 0 | Nonspatial. |

## 3. Parameters, functions, and rate laws

| Name | Value | Use |
| --- | ---: | --- |
| `kpX`, `kmX` | 1, 1 | X `0→1` and `1→0` rates. |
| `kpY`, `kmY` | 1, 1 | Y forward and reverse rates. |
| `kpZ`, `kmZ` | 1, 1 | Z forward and reverse rates. |
| `RTOT` | 100 | Initial amount of each type and normalization in `R111`. |

`R111()=(X1/RTOT)*(Y1/RTOT)*(Z1/RTOT)*RTOT`. It multiplies the three active fractions and rescales by `RTOT`; it is a derived independence estimate, not an explicitly represented X–Y–Z complex. It is printed during simulation and is not used as a reaction rate.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `X` | 1 | `S` | `S~0~1` | None | Abstract binary switch. | No bonds. |
| `Y` | 1 | `S` | `S~0~1` | None | Independent binary switch. | No bonds. |
| `Z` | 1 | `S` | `S~0~1` | None | Independent binary switch. | No bonds. |

## 5. Compartments, anchors, initial species, and setup

There are no compartments, anchors, or binding sites. `X(S~0)`, `Y(S~0)`, and `Z(S~0)` each start at `RTOT=100`; active states start at zero. The three pools are conserved independently because every rule only flips `S` and neither creates nor destroys a molecule.

## 6. Complete reaction-rule inventory

| # | Direction and participants | Exact modeled change | Rates | Technical meaning |
| ---: | --- | --- | --- | --- |
| 1 | Reversible; `X` only | `X.S 0↔1`; no bond edit. | `kpX`, `kmX` | Independent X activation/deactivation. |
| 2 | Reversible; `Y` only | `Y.S 0↔1`; no bond edit. | `kpY`, `kmY` | Independent Y activation/deactivation. |
| 3 | Reversible; `Z` only | `Z.S 0↔1`; no bond edit. | `kpZ`, `kmZ` | Independent Z activation/deactivation. |

No rule couples X, Y, or Z. Their only joint quantity is computed by `R111()`.

## 7. Observables and technical readouts

| Name | Type | Counted target | Interpretation |
| --- | --- | --- | --- |
| `X1` | `Species` | Exact `X(S~1)` species | Active X abundance. |
| `Y1` | `Species` | Exact `Y(S~1)` species | Active Y abundance. |
| `Z1` | `Species` | Exact `Z(S~1)` species | Active Z abundance. |

The additional printed function `R111` reports `X1*Y1*Z1/RTOT^2`, the expected triple-active count if the three switches are statistically independent.

## 8. Actions and simulation workflow

`generate_network({overwrite=>1})` regenerates the finite network. `simulate({method=>"ode",t_end=>10,n_steps=>100,print_functions=>1})` performs deterministic ODE integration from 0 to 10 with 100 output intervals and includes `R111` with the three observables.

## 9. Technical caveats and ambiguities

X, Y, Z, and state `S` are intentionally abstract. The metadata points to a different variant (`after_bunching`) and incorrectly reports `uses_functions: false` despite active `R111()`. Because `R111` assumes factorization, it would stop representing a true joint population if later rules introduced coupling or correlations.
