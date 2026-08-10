# Coder Model Explanation: Gardner 2000

## 1. Model identity and scope

- **Model id:** `Gardner_2000`
- **Title:** Gardner 2000
- **BNGL path:** `Published/Gardner2000/genetic_switch_gardner2000.bngl`
- **YAML path:** `Published/Gardner2000/metadata.yaml`
- **Scope:** This is a dimensionless ODE implementation of the Gardner-Cantor-Collins genetic toggle switch. It represents two mutually repressing gene products, not explicit promoter binding. The comments map the model to the two ODEs from Gardner et al. 2000.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 5 dimensionless parameters. |
| Compartments | No | No compartments. |
| Molecule types | Yes | 2 zero-site molecule types: `R1` and `R2`. |
| Seed species | Yes | 2 initial species, both initialized to 0. |
| Observables | Yes | 2 molecule-count readouts for total repressor levels. |
| Functions | Yes | 2 Hill-repressed synthesis functions. |
| Reaction rules | Yes | 4 rules: two synthesis and two degradation rules. |
| Actions | Yes | Network generation, sequential ODE simulations, parameter changes, and a parameter scan. |

## 3. Parameters, functions, and rate laws

| Parameter | Value | Role |
| --- | ---: | --- |
| `alpha_1` | 156.25 | Maximum dimensionless synthesis rate for `R1`. |
| `alpha_2` | 15.6 | Maximum dimensionless synthesis rate for `R2`; later temporarily changed to 600 by an action. |
| `beta` | 2.5 | Hill coefficient for repression of `R1` synthesis by `R2`. |
| `gamma` | 1.0 | Hill coefficient for repression of `R2` synthesis by `R1`. |
| `k_deg` | 1.0 | First-order degradation rate for both repressors, fixed by nondimensionalization. |

`Obs_Tot_R1` and `Obs_Tot_R2` feed the functions. `syn_R1()` computes `alpha_1 / (1 + Obs_Tot_R2^beta)`, so high `R2` suppresses `R1` synthesis. `syn_R2()` computes `alpha_2 / (1 + Obs_Tot_R1^gamma)`, so high `R1` suppresses `R2` synthesis. The rule rates therefore encode mutual repression through functions rather than through explicit promoter-bound species.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- |
| `R1` | 0 | None | None | None | Represents the first normalized repressor concentration, called `u` in the comments. |
| `R2` | 0 | None | None | None | Represents the second normalized repressor concentration, called `v` in the comments. |

## 5. Initial species, compartments, and setup

Both repressors start at zero. There are no compartments, complexes, binding sites, or explicit gene states. The ODE behavior is controlled by synthesis from the null source, degradation to the null sink, and Hill functions that use current total repressor levels.

## 6. Complete reaction-rule inventory

| # | Rule label/name | Direction | Participants and sites | Rate | Modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | Synthesis of `R1` | One-way source | No reactant; product `R1` has no sites | `syn_R1()` | Creates `R1` | Produces repressor 1 at a rate suppressed by the current `R2` level. |
| 2 | Synthesis of `R2` | One-way source | No reactant; product `R2` has no sites | `syn_R2()` | Creates `R2` | Produces repressor 2 at a rate suppressed by the current `R1` level. |
| 3 | Degradation of `R1` | One-way sink | `R1` with no sites | `k_deg` | Removes `R1` | Implements first-order loss of repressor 1 in dimensionless time. |
| 4 | Degradation of `R2` | One-way sink | `R2` with no sites | `k_deg` | Removes `R2` | Implements first-order loss of repressor 2 in dimensionless time. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Tot_R1` | `Molecules` | `R1()` | Dimensionless total level of the first repressor; also the feedback variable used in `syn_R2()`. |
| `Obs_Tot_R2` | `Molecules` | `R2()` | Dimensionless total level of the second repressor; also the feedback variable used in `syn_R1()`. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` creates a two-species, four-reaction ODE network.
2. First ODE simulation runs from 0 to 8 to relax from the origin toward the `R1`-dominant steady state.
3. `setParameter("alpha_2",600.0)` temporarily raises `R2` production, modeling induction that can push the system across the separatrix.
4. A continued ODE simulation runs from 8 to 12 under high `alpha_2`.
5. `setParameter("alpha_2",15.6)` restores the default `R2` synthesis strength.
6. A continued ODE simulation runs from 12 to 20, testing whether the model remains in the `R2`-dominant basin.
7. `parameter_scan` scans `alpha_2` from 1 to 500 at fixed `alpha_1` to explore the bistable-to-monostable boundary.

## 9. Technical caveats and ambiguities

- This model is intentionally nondimensional; molecule counts should not be interpreted as stochastic copy numbers.
- Mutual repression is encoded through algebraic functions of observables, not explicit promoter occupancy rules.
- The comments explicitly mark ODE as the appropriate method; stochastic simulation would not match the dimensionless formulation.
