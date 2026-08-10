# Detailed Model Explanation: Hlavacek 1999 steric-effects model

## 1. Model overview

This dimensionless model describes binding of monovalent cell-surface receptors to a ligand with up to 20 receptor contacts. Rather than representing individual sites and receptors explicitly, it tracks ligand occupancy as a 20-state counter and reduces each next-binding rate according to receptor depletion and an occupancy-dependent steric-exclusion factor.

## 2. BNGL block inventory

The model contains 25 parameters, one molecule type, one zero-valued seed species, 40 reaction rules, 21 molecule-count observables, ten active functions, and actions for network generation and ODE simulation. It has no compartments or anchors and is intentionally a dimensionless deterministic construction.

## 3. Parameters, functions, and rate laws

All quantities are dimensionless: ligand state populations represent surface-bound ligand normalized by total receptor density, and time is scaled by the reverse crosslinking rate. Rule rates combine constant factors with observable-dependent functions enforcing receptor and ligand conservation.

| Parameter group or names | Function in this model |
| --- | --- |
| `n` | Sets the maximum ligand occupancy to 20 receptor contacts and supplies the unoccupied-site factor in the forward rates. |
| `vKLT` | Scaled ligand concentration used in the solution-to-surface first-binding flux. |
| `KxRT` | Scaled crosslinking affinity multiplying every additional receptor-binding transition. |
| `CRT_LT` | Converts total surface-bound ligand into depletion of the normalized free-ligand pool. |
| `kr_kmx` | Ratio of the first-bond and crosslink reverse rates; controls creation of singly bound ligand and its loss back to solution. |
| `aA` | Receptor footprint-to-ligand-area ratio, fixed at 0.01, used to reduce accessible binding area as occupancy grows. |
| `nu_1`–`nu_19` | Occupancy-specific numbers of sterically available sites. Each combines the remaining-site count `n-i` with excluded-area and insertion-probability factors that shrink nonlinearly with occupancy. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `r_b_lo()`, `r_b_md()`, `r_b_hi()`, `r_b_vh()`, `r_b_xx()` | `Obs_L1`–`Obs_L20` in ranges 1–5, 6–10, 11–14, 15–18, and 19–20 | Compute grouped weighted sums `i × x_i`, partitioned only to keep the long receptor-occupancy expression manageable. |
| `r_free()` | All five weighted-sum functions | Computes the normalized free-receptor fraction as one minus receptors committed across every ligand occupancy state. It controls initial binding and every forward crosslinking rule. |
| `l_free()` | `CRT_LT`, `Obs_L_tot` | Computes normalized free ligand as one minus the converted total surface-bound ligand. |
| `fn_bind()` | `kr_kmx`, `vKLT`, `r_free()`, `l_free()` | Computes the source flux that creates singly receptor-bound ligand from implicit free receptor and free ligand pools. |
| `alpha_2()` | `r_free()`, `Obs_L1` | Reports the receptor fraction in ligand aggregates of at least two contacts by excluding free receptors and singly bound ligand. |
| `alpha_10()` | `Obs_L10`, `r_b_hi()`, `r_b_vh()`, `r_b_xx()` | Reports the receptor fraction in aggregates of at least ten contacts, including ten receptors from state 10 and all weighted occupancy above it. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `Lig` | 1 | `b` | Occupancy states `1` through `20` | None | Coarse-grained surface-bound ligand whose internal state records the number of attached receptors; neither receptors nor 20 physical binding components are explicitly represented. |

## 5. Compartments, anchors, initial species, and setup

There are no compartments or anchors. The only explicit seed, singly bound ligand `Lig(b~1)`, starts at zero; free ligand and receptor are implicit conservation pools initialized through `l_free() = 1` and `r_free() = 1`. The source rule then creates the first surface-bound ligand, after which occupancy can grow or shrink along the state chain. Because the species values are normalized densities, their numerical values are not molecule counts despite BNGL's `Molecules` observable keyword.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–2 exchange ligand between the implicit solution pool and the singly bound surface state. Rules 3–21 add receptors with sterically reduced, occupancy-dependent rates, and rules 22–40 remove receptors with rates proportional to current occupancy.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way creation | Implicit free ligand and receptor pools; new ligand state `b~1` | Creates singly bound ligand from source `0` at `fn_bind() = kr_kmx × vKLT × r_free × l_free`. | Couples first binding to depletion of both conserved free pools without explicitly representing their species. |
| 2 | One-way removal | Ligand state `b~1` | Deletes singly bound ligand to sink `0` at `kr_kmx`; mass returns implicitly through the observable-based conservation functions. | Represents complete detachment from the surface. |
| 3–21 | One-way | Ligand occupancy states 1→2 through 19→20; implicit free receptors | Rule `i+2` changes occupancy `i` to `i+1` at `nu_i × KxRT × r_free()`. The `nu_1`–`nu_19` factors map respectively to starting states 1–19 and encode fewer geometrically accessible sites as coverage rises. | Builds multivalent receptor aggregates while combining receptor depletion with steric hindrance. |
| 22–40 | One-way | Ligand occupancy states 2→1 through 20→19 | Rule numbers 22–40 remove one contact from starting occupancies 2–20, respectively; the numeric rates 2–20 make total loss proportional to the number of existing receptor contacts. | Provides the reverse crosslinking flux and lets highly occupied ligands lose contacts more frequently. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_L1`–`Obs_L5` | Molecule count keyword; dimensionless density | Explicit ligand populations with 1–5 attached receptors. | Feed `r_b_lo()` and resolve low-valence aggregates; values represent `x_i = L_i/R_T`, not literal molecules. |
| `Obs_L6`–`Obs_L10` | Molecule count keyword; dimensionless density | Ligand populations with 6–10 attached receptors. | Feed `r_b_md()`; `Obs_L10` also contributes directly to the ≥10-contact receptor fraction. |
| `Obs_L11`–`Obs_L14` | Molecule count keyword; dimensionless density | Ligand populations with 11–14 contacts. | Feed `r_b_hi()` and therefore both free-receptor depletion and `alpha_10()`. |
| `Obs_L15`–`Obs_L18` | Molecule count keyword; dimensionless density | Ligand populations with 15–18 contacts. | Feed the very-high-occupancy weighted sum `r_b_vh()`. |
| `Obs_L19`, `Obs_L20` | Molecule count keyword; dimensionless density | Ligand populations with 19 or 20 contacts. | Feed `r_b_xx()` and report near-saturated or fully saturated ligands. |
| `Obs_L_tot` | Molecule count keyword; dimensionless density | Sum of every explicit surface-bound ligand state. | Drives free-ligand conservation after multiplication by `CRT_LT`; it is not receptor-weighted. |

## 8. Actions and simulation workflow

The model generates a 20-species, 40-reaction network and integrates it with deterministic ODEs from dimensionless time 0 to 2.5 using 500 steps. There is no stochastic run, equilibration phase, parameter scan, or explicit export beyond the standard generated outputs.

## 9. Technical caveats and ambiguities

- `Lig.b` is an occupancy counter, not one physical binding site, and no receptor molecule type exists. The model therefore cannot report receptor-level topology or distinguish arrangements having the same occupancy.
- Source and sink rules exchange mass with implicit free pools whose values are reconstructed from observables; this is a deterministic conservation-law device rather than molecular creation or degradation.
- Although observables use the `Molecules` keyword, all populations and time are dimensionless. Stochastic or molecule-count interpretations are inappropriate.
- The `nu_i` factors are a particular insertion-probability approximation for circular receptor footprints; changing `aA` changes both excluded area and the nonlinear occupancy penalty.
