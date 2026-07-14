# Coder Model Explanation: McMillan 2021

## 1. Model identity and scope

- **Model id:** `McMillan_2021`
- **Title:** McMillan 2021
- **BNGL path:** `Published/McMillan2021/McMillan_2021.bngl`
- **YAML path:** `Published/McMillan2021/metadata.yaml`
- **Metadata description:** TNF signaling
- **Scope:** This model enumerates trivalent TNF binding to receptor through the receptor `R.a` site. TNF molecule `T` has three sites, `1`, `2`, and `3`; the active rules explicitly list every first, second, and third receptor-binding event. Receptor site `R.p` is declared but not used by active rules.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 17 parameters for Avogadro/volume conversion, initial concentrations, dissociation, affinity constants, and microscopic rates. |
| Compartments | No | No compartments. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 2 molecule types: receptor `R(p,a)` and TNF `T(1,2,3)`. |
| Seed/species | Yes | 2 initial species: free receptor and free trivalent TNF. |
| Observables | Yes | 5 active observables for free receptor/TNF and TNF bound by 1, 2, or 3 receptors. |
| Functions | No | No functions block. |
| Reaction rules | Yes | 12 active reversible TNF-receptor binding rules. |
| Actions | Yes | Inline `generate_network` and `simulate_ode` commands after the commented `#actions` marker. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `Na` | `6.02e23` | Avogadro conversion. |
| `Vol` | `1e-15` | Volume used for concentration-to-molecule conversion. |
| `R0_conc` | `20000` | Receptor concentration in nM. |
| `T0_conc` | `6250` | TNF concentration in nM. |
| `R0_tot` | `(R0_conc)*(1e-9)*Na*Vol` | Initial receptor molecule count. |
| `T0_tot` | `(T0_conc)*(1e-9)*Na*Vol` | Initial TNF molecule count. |
| `koff` | `0.01` | Reverse rate shared by all TNF-receptor binding rules. |
| `Kp`, `Ka` | `200`, `200` | Affinity constants for commented receptor dimerization rules; not used by active rules. |
| `K1`, `K2`, `K3` | `10`, `100`, `1000` | Macroscopic affinity constants for first, second, third TNF binding classes. |
| `kp`, `ka` | `koff/(Kp...)`, `koff/(Ka...)` | Microscopic rates for commented receptor dimerization; not used by active rules. |
| `k1`, `k2`, `k3` | `koff/(K1...)`, `koff/(K2...)`, `koff/(K3...)` | Microscopic forward rates for first, second, third receptor-binding events. |

No separate functions block is declared.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `R` | 2 | `p`, `a` | none | none | `a` is the active TNF-binding site; `p` is unused by active rules. | Commented rules suggest `p`/`a` could have represented receptor dimerization, but those rules are inactive. |
| `T` | 3 | `1`, `2`, `3` | none | none | `1`, `2`, and `3` are equivalent-looking TNF receptor-binding sites, but the file enumerates them explicitly. | The occupancy of these sites determines whether observables count TNF1R, TNF2R, or TNF3R. |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.
- Anchors: none declared.
- Initial setup: all receptors start as `R(p,a)` and all TNF starts as `T(1,2,3)`.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `R(p,a)` | `R0_tot` | Free receptor with both declared sites unbound; only `a` participates in active rules. |
| `T(1,2,3)` | `T0_tot` | Free trivalent TNF with all three binding sites open. |

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rules 1-3 are first receptor-binding events at TNF sites `1`, `2`, and `3` using `k1`. Rules 4-9 add a second receptor to whichever TNF site remains open, using `k2`. Rules 10-12 add the third receptor, using `k3`. Every rule forms or breaks one specific `T.<site>`–`R.a` bond and uses `koff` as the reverse rate.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `3` | reversible | `T.1` + `R.a` | `k1, koff` | Forms/releases `T.1!1`–`R.a!1`. | First receptor binds TNF site `1`; reverse unbinds that receptor. |
| 2 | `4` | reversible | `T.2` + `R.a` | `k1, koff` | Forms/releases `T.2!1`–`R.a!1`. | First receptor binds TNF site `2`. |
| 3 | `5` | reversible | `T.3` + `R.a` | `k1, koff` | Forms/releases `T.3!1`–`R.a!1`. | First receptor binds TNF site `3`. |
| 4 | `6` | reversible | open `T.2` on a `T.1`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.2!1`–`R.a!1` bond while `T.1` remains occupied. | Second receptor binds site `2` after site `1` is already occupied. |
| 5 | `7` | reversible | open `T.3` on a `T.1`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.3!1`–`R.a!1` bond while `T.1` remains occupied. | Second receptor binds site `3` after site `1` is already occupied. |
| 6 | `8` | reversible | open `T.1` on a `T.2`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.1!1`–`R.a!1` bond while `T.2` remains occupied. | Second receptor binds site `1` after site `2` is already occupied. |
| 7 | `9` | reversible | open `T.3` on a `T.2`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.3!1`–`R.a!1` bond while `T.2` remains occupied. | Second receptor binds site `3` after site `2` is already occupied. |
| 8 | `10` | reversible | open `T.1` on a `T.3`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.1!1`–`R.a!1` bond while `T.3` remains occupied. | Second receptor binds site `1` after site `3` is already occupied. |
| 9 | `11` | reversible | open `T.2` on a `T.3`-bound TNF + `R.a` | `k2, koff` | Adds/removes a `T.2!1`–`R.a!1` bond while `T.3` remains occupied. | Second receptor binds site `2` after site `3` is already occupied. |
| 10 | `12` | reversible | open `T.3` on a `T.1,T.2`-bound TNF + `R.a` | `k3, koff` | Adds/removes the third bond at `T.3!1`–`R.a!1`. | Completes trivalent occupancy for the `T.1/T.2` partial complex. |
| 11 | `13` | reversible | open `T.2` on a `T.1,T.3`-bound TNF + `R.a` | `k3, koff` | Adds/removes the third bond at `T.2!1`–`R.a!1`. | Completes trivalent occupancy for the `T.1/T.3` partial complex. |
| 12 | `14` | reversible | open `T.1` on a `T.2,T.3`-bound TNF + `R.a` | `k3, koff` | Adds/removes the third bond at `T.1!1`–`R.a!1`. | Completes trivalent occupancy for the `T.2/T.3` partial complex. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `MonomerReceptor` | `Molecules` | `R(p,a)` | Free receptor with unbound `a` site. |
| `freeTNF` | `Molecules` | `T(1,2,3)` | TNF with all three sites open. |
| `TNF1R` | `Molecules` | `T(1!+,2,3)`, `T(1,2!+,3)`, `T(1,2,3!+)` | TNF bound by exactly one receptor at any one of the three sites. |
| `TNF2R` | `Molecules` | two occupied TNF sites | TNF bound by exactly two receptors. |
| `TNF3R` | `Molecules` | `T(1!+,2!+,3!+)` | Fully occupied trivalent TNF. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1});` builds the finite network for the trivalent binding system.
2. `simulate_ode({suffix=>ode,n_steps=>5,t_end=>10000});` runs a coarse ODE simulation.

## 9. Technical caveats and ambiguities

- `R.p` is declared and initialized but not used by active rules.
- Receptor dimerization rules are present only as comments; they should not be counted as active model behavior.
- The metadata says simulation method `nf`, but the active command in this file is `simulate_ode`.
