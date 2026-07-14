# Coder Model Explanation: McMillan 2021

## 1. Model identity and scope

- **Model id:** `McMillan_2021`
- **Title:** McMillan 2021
- **BNGL path:** `Published/McMillan2021/McMillan_2021.bngl`
- **YAML path:** `Published/McMillan2021/metadata.yaml`
- **Metadata description:** TNF signaling
- **Scope:** A small TNF-receptor binding model in which trivalent TNF has three binding sites and recruits up to three receptor molecules through the receptor a site. The rules enumerate first, second, and third TNF binding events with different microscopic on-rates derived from K1, K2, and K3.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 17 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 2 molecule type entries. |
| Seed/species | Yes | 2 initial species entries. |
| Observables | Yes | 5 observable entries. |
| Functions | No | 0 function entries. |
| Reaction rules | Yes | 12 reaction rules. |
| Actions | Yes | 2 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `Na` | `6.02e23` | Avogadro's number (molecues/mol) |
| `Vol` | `1e-15` | Volume in Litres |
| `R0_conc` | `20000` | Reagents Concentration in nM |
| `T0_conc` | `6250` | initial total/conversion parameter |
| `R0_tot` | `(R0_conc)*(1e-9)*Na*Vol` | Receptor's interactions; Convert from nanomolar to number of molecules in volume Vol; BioNetGen uses number of molecules and NOT concentration |
| `T0_tot` | `(T0_conc)*(1e-9)*Na*Vol` | initial total/conversion parameter |
| `koff` | `0.01` | kinetic or model-control parameter |
| `Kp` | `200` | values of constants in nM |
| `Ka` | `200` | kinetic or model-control parameter |
| `K1` | `10` | kinetic or model-control parameter |
| `K2` | `100` | kinetic or model-control parameter |
| `K3` | `1000` | kinetic or model-control parameter |
| `kp` | `koff /(Kp*1e-9*Na*Vol)` | Convert macroscopic (Molar; volume indenpendent constant) to microscopic (events per second) constant; BioNetGen uses microscopic constants |
| `ka` | `koff /(Ka*1e-9*Na*Vol)` | kinetic or model-control parameter |
| `k1` | `koff /(K1*1e-9*Na*Vol)` | kinetic or model-control parameter |
| `k2` | `koff /(K2*1e-9*Na*Vol)` | kinetic or model-control parameter |
| `k3` | `koff /(K3*1e-9*Na*Vol)` | kinetic or model-control parameter |

No separate functions block is declared; rates are direct parameters or expressions in rule rows.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `R` | 2 | p, a | none declared | none | binding/modification candidate sites: p, a |  |
| `T` | 3 | 1, 2, 3 | none declared | none | binding/modification candidate sites: 1, 2, 3 |  |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `R(p,a)` | `R0_tot` | starting species pool for this pattern |
| `T(1,2,3)` | `T0_tot` | starting species pool for this pattern |

## 6. Complete reaction-rule inventory

The source contains **12** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `3` | reversible | R, T | `k1, koff` | binding-pattern rewrite | `T(1,2,3) + R(a) <-> T(1!1,2,3).R(a!1)` | TNF reactions; First  TNF binding event. Reversibly forms binding contacts among R, T through R.a, T.1. Rate/expression: k1, koff. |
| 2 | `4` | reversible | R, T | `k1, koff` | binding-pattern rewrite | `T(1,2,3) + R(a) <-> T(1,2!1,3).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.2. Rate/expression: k1, koff. |
| 3 | `5` | reversible | R, T | `k1, koff` | binding-pattern rewrite | `T(1,2,3) + R(a) <-> T(1,2,3!1).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.3. Rate/expression: k1, koff. |
| 4 | `6` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1!+,2,3) + R(a) <-> T(1!+,2!1,3).R(a!1)` | Second  TNF binding event. Reversibly forms binding contacts among R, T through R.a, T.2. Rate/expression: k2, koff. |
| 5 | `7` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1!+,2,3) + R(a) <-> T(1!+,2,3!1).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.3. Rate/expression: k2, koff. |
| 6 | `8` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1,2!+,3) + R(a) <-> T(1!1,2!+,3).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.1. Rate/expression: k2, koff. |
| 7 | `9` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1,2!+,3) + R(a) <-> T(1,2!+,3!1).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.3. Rate/expression: k2, koff. |
| 8 | `10` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1,2,3!+) + R(a) <-> T(1!1,2,3!+).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.1. Rate/expression: k2, koff. |
| 9 | `11` | reversible | R, T | `k2, koff` | binding-pattern rewrite | `T(1,2,3!+) + R(a) <-> T(1,2!1,3!+).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.2. Rate/expression: k2, koff. |
| 10 | `12` | reversible | R, T | `k3, koff` | binding-pattern rewrite | `T(1!+,2!+,3) + R(a) <-> T(1!+,2!+,3!1).R(a!1)` | Third  TNF binding event. Reversibly forms binding contacts among R, T through R.a, T.3. Rate/expression: k3, koff. |
| 11 | `13` | reversible | R, T | `k3, koff` | binding-pattern rewrite | `T(1!+,2,3!+) + R(a) <-> T(1!+,2!1,3!+).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.2. Rate/expression: k3, koff. |
| 12 | `14` | reversible | R, T | `k3, koff` | binding-pattern rewrite | `T(1,2!+,3!+) + R(a) <-> T(1!1,2!+,3!+).R(a!1)` | Reversibly forms binding contacts among R, T through R.a, T.1. Rate/expression: k3, koff. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `MonomerReceptor` | `Molecules` | `R(p,a)` | counts molecule-pattern matches |
| `freeTNF` | `Molecules` | `T(1,2,3)` | Molecules DimerReceptor R(p!0,a).R(p!0,a), R(a!0,p).R(a!0,p); Molecules AggregatedReceptor R(p!0,a!0) |
| `TNF1R` | `Molecules` | `T(1!+,2,3),  T(1,2!+,3), T(1,2,3!+)` | counts molecule-pattern matches |
| `TNF2R` | `Molecules` | `T(1!+,2!+,3), T(1!+,2,3!+), T(1,2!+,3!+)` | counts molecule-pattern matches |
| `TNF3R` | `Molecules` | `T(1!+,2!+,3!+)` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1});` — active execution command in the actions block

2. `simulate_ode({suffix=>ode,n_steps=>5,t_end=>10000});` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- Receptor dimerization rules are present only as comments and are not active reaction rules in this file.

- The active model uses one receptor site, a, for TNF binding; receptor site p is declared and initialized but not used by active rules.

- Metadata marks the model NFsim-compatible, but the active commands generate a network and run ODE simulation.
