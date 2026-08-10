# Coder Model Explanation: Dembo 1978

## 1. Model identity and scope

- **Model id:** `Dembo_1978`
- **Title:** Dembo 1978
- **BNGL path:** `Published/Dembo1978/blbr_dembo1978.bngl`
- **YAML path:** `Published/Dembo1978/metadata.yaml`
- **Scope:** This is a symmetric bivalent ligand-bivalent receptor cross-linking model. It represents bivalent hapten `L` and bivalent receptor/IgE `R`, with free ligand capture, inter-complex cross-linking, and bond dissociation. The comments specify that same-complex ring formation is blocked during NFsim execution.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 13 physical, scaling, abundance, and kinetic parameters. |
| Compartments | No | No compartment declarations. |
| Molecule types | Yes | 2 molecule types: bivalent `L` and bivalent `R`. |
| Seed species | Yes | 2 initial species: free ligand and free receptor. |
| Observables | Yes | 5 readouts for free molecules, bonds, and free sites. |
| Functions | No | No function block. |
| Reaction rules | Yes | 3 labeled rules. |
| Actions | Yes | One NFsim simulation action. |

## 3. Parameters, functions, and rate laws

| Parameter | Value / expression | Role |
| --- | ---: | --- |
| `NA` | 6.02214076e23 | Avogadro constant for concentration-to-molecule scaling. |
| `V_cell` | 1e-9 | Cell volume in liters. |
| `R_per_cell` | 3e5 | Receptor count before simulation down-scaling. |
| `f` | 0.01 | Simulation scaling factor. |
| `V_sim` | `V_cell*f` | Effective simulation volume. |
| `RT` | `R_per_cell*f` | Scaled receptor count, 3000 molecules. |
| `LT_per_cell` | 3e6 | Ligand count before scaling. |
| `LT` | `LT_per_cell*f` | Scaled ligand count. |
| `kon` | 1e6 | Single-site solution association rate. |
| `koff` | 0.01 | Single-bond dissociation rate. |
| `KxRT` | 5 | Dimensionless cross-linking propensity. |
| `kf` | `kon/(NA*V_sim)` | Stochastic ligand-capture rate for two free molecules. |
| `kxf` | `KxRT/RT*koff` | Stochastic cross-linking rate for a tethered ligand arm binding another receptor. |

There are no BNGL functions. Rule 1 uses `kf`, rule 2 uses `kxf`, and rule 3 uses `koff`.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- |
| `L` | 2 | `r`, `r` | None | Each `r` site can bind a receptor `l` site. | The repeated site names encode two identical hapten arms. |
| `R` | 2 | `l`, `l` | None | Each `l` site can bind a ligand `r` site. | The repeated site names encode two identical receptor/IgE binding sites. |

## 5. Initial species, compartments, and setup

The initial condition contains only free bivalent ligand, `L(r,r)`, at `LT`, and free bivalent receptor, `R(l,l)`, at `RT`. There are no compartments. The model starts with no ligand-receptor bonds, and aggregation emerges from the capture and cross-linking rules.

## 6. Complete reaction-rule inventory

| # | Rule label/name | Direction | Participants and sites | Rate | Modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `R_capture` | One-way binding | Free `L` with two free `r` sites plus `R` with a free `l` site | `kf` | Creates one `L.r`-`R.l` bond | A free bivalent hapten is captured from solution by a free receptor site. |
| 2 | `R_crosslink` | One-way binding | Ligand already bound through one `r` site and still free at another `r` site plus a receptor with a free `l` site | `kxf` | Adds a second ligand-receptor bond | A tethered ligand arm binds a receptor site in a different complex, extending a chain and creating receptor cross-links. |
| 3 | `R_dissoc` | One-way unbinding | Any `L.r`-`R.l` bond | `koff` | Breaks one ligand-receptor bond | Any hapten-receptor bond can dissociate, producing one free ligand site and one free receptor site. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Free_L` | `Species` | `L(r,r)` | Counts completely free ligand molecules with both arms unbound. |
| `Obs_Free_R` | `Species` | `R(l,l)` | Counts completely free receptor molecules with both sites unbound. |
| `Obs_Bonds` | `Molecules` | One `L.r`-`R.l` bond | Counts total ligand-receptor bonds. |
| `Obs_Free_L_sites` | `Molecules` | Ligand `r` sites that are free | Counts available hapten arms across all ligand molecules. |
| `Obs_Free_R_sites` | `Molecules` | Receptor `l` sites that are free | Counts available receptor binding sites across all receptor molecules. |

## 8. Actions and simulation workflow

The action block runs `simulate({method=>"nf", suffix=>"nfr", t_start=>0, t_end=>3000, n_steps=>300, gml=>2147483647, param=>"-bscb"})`. This uses NFsim rather than generated-network ODE simulation because bivalent-bivalent cross-linking can generate unbounded chain species. The `-bscb` flag blocks same-complex binding, enforcing inter-complex cross-linking and preventing ring closure.

## 9. Technical caveats and ambiguities

- The YAML says ODE compatibility, but the BNGL action and comments explicitly use NFsim because network generation is infeasible for unbounded chains.
- Repeated site names mean the two ligand arms and two receptor sites are symmetric; the source does not distinguish arm identities.
- The `R_crosslink` rule relies on the NFsim same-complex-binding block to prevent rings; without that execution flag, interpretation of allowed cross-links would differ.
