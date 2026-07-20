# Coder Model Explanation: Hlavacek2018Egg

## 1. Model identity and scope

- **Model id:** `Hlavacek2018Egg_egg`
- **Title:** Hlavacek2018Egg
- **BNGL path:** `Published/Hlavacek2018Egg/egg.bngl`
- **YAML path:** `Published/Hlavacek2018Egg/metadata.yaml`
- **Scope:** This is a compact published/example model whose metadata describes it as the "End of permute change log." The BNGL is not a named biological pathway; it is an ODE example that advances one abstract species and prints two fitted/trigonometric functions of that species over one period.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 23 parameter definitions: 10 fitted `__FREE` values, 10 aliases, `pi`, `period`, and `m`. |
| Compartments | No | No compartment declarations. |
| Molecule types | Yes | 1 molecule type: `t`. |
| Seed species | Yes | 1 initial species, `t`, initialized to 0. |
| Observables | Yes | 1 species-count observable for `t`. |
| Functions | Yes | 2 functions, `X()` and `Y()`, both Fourier-like expressions of `t`. |
| Reaction rules | Yes | 1 rule that creates `t` at a constant rate. |
| Actions | Yes | Network generation plus one ODE simulation with function printing. |

## 3. Parameters, functions, and rate laws

The parameter set is almost entirely numerical coefficients for the two output functions. The `a*` and `b*` values feed `X()`, while the `c*` and `d*` values feed `Y()`. Each `__FREE` value is copied into a shorter alias, so the function definitions use `a0`, `a1`, `a2`, `b1`, `b2`, `c0`, `c1`, `c2`, `d1`, and `d2` rather than the raw fitted names.

| Parameter | Value / expression | Role |
| --- | ---: | --- |
| `a0__FREE`, `a1__FREE`, `a2__FREE` | 99.9318747, 1.00606018, -0.752962956 | Fitted cosine/offset coefficients for `X()`. |
| `b1__FREE`, `b2__FREE` | -30.8973913, 1.26208508 | Fitted sine coefficients for `X()`. |
| `c0__FREE`, `c1__FREE`, `c2__FREE` | 139.738978, -39.1791542, -1.56811184 | Fitted cosine/offset coefficients for `Y()`. |
| `d1__FREE`, `d2__FREE` | -1.21914775, 1.28080122 | Fitted sine coefficients for `Y()`. |
| `a0`-`d2` aliases | Each aliases the corresponding `__FREE` value | Short names used inside functions. |
| `pi` | `2*asin(1)` | Computes pi for angular frequency. |
| `period` | 180 | Period used for the trigonometric waveforms. |
| `m` | `2*pi/period` | Fundamental angular frequency. |

`X()` computes an offset plus first- and second-harmonic sine/cosine terms using the `a*` and `b*` coefficients. `Y()` uses the same harmonic structure with `c*` and `d*` coefficients. The only reaction-rate expression is the constant `1`, so `t` increases linearly under ODE simulation.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- |
| `t` | 0 | None | None | None | This is an abstract scalar species used as the independent variable for the printed functions, not a biological molecule. |

## 5. Initial species, compartments, and setup

The model starts with `t` at zero. There are no compartments, no complexes, no binding sites, and no molecular states. Because the single rule continuously creates `t`, the ODE trajectory effectively turns `t` into a time-like ramp from 0 over the simulation interval. `X()` and `Y()` are then printed as functions of this ramp.

## 6. Complete reaction-rule inventory

| # | Rule label/name | Direction | Participants and sites | Rate | Modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | Unlabeled `0 -> t` | One-way synthesis/source | No reactant; product is the zero-site species `t` | `1` | Constant creation of `t` | Drives `t` upward at unit rate so the functions `X()` and `Y()` can be evaluated over a 180-step period. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `t` | `Species` | The zero-site species `t` | Reports the amount of the abstract species being accumulated by the source rule. |

`X()` and `Y()` are not observables but are printed functions requested by the simulation action. They are the main numerical outputs of interest.

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` builds the one-species, one-reaction network.
2. `simulate({suffix=>"egg", method=>"ode", t_start=>0, t_end=>180, n_steps=>180, print_functions=>1})` integrates the constant source rule over one 180-unit period and prints `X()` and `Y()` alongside the species trajectory.

## 9. Technical caveats and ambiguities

- The molecule name `t` is abstract; the current files do not support interpreting it as a biological species.
- The useful outputs are the printed functions, not a mechanistic pathway trajectory.
- The comments identify fitted or permuted parameter values but do not explain the biological origin of the coefficients.
