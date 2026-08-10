# Coder Model Explanation: Dreisigmeyer 2008

## 1. Model identity and scope

- **Model id:** `Dreisigmeyer_2008`
- **Title:** Dreisigmeyer 2008
- **BNGL path:** `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- **YAML path:** `Published/Dreisigmeyer2008/metadata.yaml`
- **Metadata description:** Lac operon
- **Scope:** This is a concentration-based ODE implementation of lac operon lactose induction. It has three explicit dynamic species: internal lactose `L`, allolactose `A`, and beta-galactosidase `Z`. The BNGL rules are intentionally site-free source/sink rules; the biological specificity lives in the algebraic functions that compute lactose import, lactose/allolactose metabolism, allolactose-driven beta-gal expression, and growth dilution.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 18 parameters covering units/conversion constants, external lactose, growth dilution, transport constants, metabolism constants, and Hill-expression constants. |
| Compartments | No | No BNGL compartment block; concentrations are implicit ODE state variables. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 3 site-free molecule types: `L`, `A`, `Z`. |
| Seed/species | Yes | 3 initial concentration-like species: `L=0`, `A=0`, `Z=c_basal`. |
| Observables | Yes | 3 concentration readouts: `Obs_Tot_L`, `Obs_Tot_A`, `Obs_Tot_Z`. |
| Functions | Yes | 5 functions; these are the actual mechanistic rate laws. |
| Reaction rules | Yes | 8 source/sink ODE rules. |
| Actions | Yes | Network generation, concentration saving, time-course ODE simulation, and lactose-scan ODE simulation. |

## 3. Parameters, functions, and rate laws

The model uses BNGL rules as ODE terms. There are no molecule sites, bonds, or internal states, so rate-law interpretation depends on the functions and observables.

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `NA` | `6.02214076e23` | Avogadro constant kept for possible population conversion; not used by the active concentration ODE rules. |
| `V_ref` | `1e-15` | Reference E. coli volume for possible concentration/population conversion. |
| `f` | `1.0` | Subvolume scale factor; present but not used in active rules. |
| `l_ext` | `1000.0` | Constant extracellular lactose concentration used by `transport_L()`. |
| `growth_rate` | `0.0231` | First-order dilution rate applied separately to `L`, `A`, and `Z`; also scales `syn_Z()`. |
| `alpha` | `600.0` | Import turnover factor in the permease-dependent lactose transport function. |
| `phi` | `0.5` | Export/import asymmetry factor in `transport_L()`. |
| `rho` | `0.1` | Michaelis asymmetry factor in `transport_L()`. |
| `K_i` | `500.0` | Permease Michaelis constant in the transport denominator. |
| `beta` | `2.85e4` | Lactose metabolism turnover constant in `metab_L()` and `prod_A()`. |
| `nu` | `0.468` | Branching fraction from lactose metabolism into allolactose production. |
| `K_m_l` | `2530.0` | Lactose Michaelis constant in the shared competitive-inhibition denominator. |
| `delta` | `2.30e4` | Allolactose metabolism turnover constant in `metab_A()`. |
| `K_m_a` | `1200.0` | Allolactose Michaelis constant in the shared competitive-inhibition denominator. |
| `eps` | `34.285` | Fully induced beta-gal level in `syn_Z()`. |
| `c_basal` | `0.0343` | Initial and basal beta-gal level. |
| `K_z` | `105.0` | Half-maximal allolactose level in the Hill induction term. |
| `n_Hill` | `2.0` | Hill coefficient for allolactose-dependent beta-gal induction. |

**Functions and derived rates**

| Function | Inputs used | Technical interpretation |
| --- | --- | --- |
| `transport_L()` | `Obs_Tot_Z`, `l_ext`, `Obs_Tot_L`, `alpha`, `phi`, `rho`, `K_i` | Net lactose import source term. It increases `L` and is proportional to beta-gal/permease proxy `Z`; the numerator subtracts an export-like term from external lactose. |
| `metab_L()` | `Obs_Tot_Z`, `Obs_Tot_A`, `Obs_Tot_L`, `beta`, `K_m_l`, `K_m_a` | Effective first-order lactose-removal coefficient. BNGL multiplies this function by the matched `L()` amount in rule 2. |
| `prod_A()` | `Obs_Tot_Z`, `Obs_Tot_L`, `Obs_Tot_A`, `nu`, `beta`, `K_m_l`, `K_m_a` | Allolactose source term produced from lactose metabolism; unlike `metab_L()`, it already includes `Obs_Tot_L` in the expression because the rule source is `0`. |
| `metab_A()` | `Obs_Tot_Z`, `Obs_Tot_A`, `Obs_Tot_L`, `delta`, `K_m_a`, `K_m_l` | Effective first-order allolactose-removal coefficient. BNGL multiplies it by matched `A()`. |
| `syn_Z()` | `Obs_Tot_A`, `growth_rate`, `c_basal`, `eps`, `K_z`, `n_Hill` | Beta-gal synthesis source term: basal expression plus Hill induction by allolactose, scaled by growth/dilution rate. |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `L` | 0 | none | none | none | Whole-species ODE state for intracellular lactose. | No site-level interactions; all regulation is in rate functions. |
| `A` | 0 | none | none | none | Whole-species ODE state for allolactose. | Drives `syn_Z()` through `Obs_Tot_A`. |
| `Z` | 0 | none | none | none | Whole-species ODE state for beta-galactosidase/permease proxy. | Appears in transport and metabolism functions through `Obs_Tot_Z`. |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.
- Anchors: none declared.
- Initial setup: `L()` and `A()` start at zero, while `Z()` starts at `c_basal`, allowing lactose import and allolactose feedback to develop from an initially basal induced state.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `L()` | `0` | No internal lactose initially. |
| `A()` | `0` | No allolactose initially. |
| `Z()` | `c_basal` | Basal beta-gal/permease proxy level. |

## 6. Complete reaction-rule inventory

**Rule-family orientation:** This model has no binding sites or internal states. Every rule is a source/sink ODE term for one of the three concentration variables. The site-level statement for each rule is therefore explicitly “none”; the meaningful implementation detail is whether the rule is a source term, a first-order sink term, or growth dilution.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | Product: `L`; no sites/components | `transport_L()` | Source `0 → L()`; no sites or states. | Adds internal lactose according to the permease-dependent transport function. The term depends on `Z`, external lactose, and current internal lactose. |
| 2 | `Unlabeled` | one-way | Reactant: `L`; no sites/components | `metab_L()` | Sink `L() → 0`; no sites or states. | Removes internal lactose by beta-gal-catalyzed metabolism. Because the rule matches `L()`, the function acts as an effective first-order coefficient for lactose. |
| 3 | `Unlabeled` | one-way | Reactant: `L`; no sites/components | `growth_rate` | Sink `L() → 0`; no sites or states. | Dilutes internal lactose by cell growth independently of enzymatic metabolism. |
| 4 | `Unlabeled` | one-way | Product: `A`; no sites/components | `prod_A()` | Source `0 → A()`; no sites or states. | Produces allolactose from lactose metabolism; the lactose dependence is inside `prod_A()` rather than in the reactant pattern. |
| 5 | `Unlabeled` | one-way | Reactant: `A`; no sites/components | `metab_A()` | Sink `A() → 0`; no sites or states. | Removes allolactose by beta-gal-catalyzed metabolism with competitive inhibition by lactose/allolactose encoded in the function. |
| 6 | `Unlabeled` | one-way | Reactant: `A`; no sites/components | `growth_rate` | Sink `A() → 0`; no sites or states. | Dilutes allolactose through growth. |
| 7 | `Unlabeled` | one-way | Product: `Z`; no sites/components | `syn_Z()` | Source `0 → Z()`; no sites or states. | Synthesizes beta-galactosidase/permease proxy from a basal-plus-Hill function of allolactose. |
| 8 | `Unlabeled` | one-way | Reactant: `Z`; no sites/components | `growth_rate` | Sink `Z() → 0`; no sites or states. | Dilutes beta-galactosidase by growth, balancing the allolactose-induced synthesis term. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Tot_L` | `Molecules` | `L()` | Current intracellular lactose concentration-like state; used by `transport_L()`, `metab_L()`, and `prod_A()`. |
| `Obs_Tot_A` | `Molecules` | `A()` | Current allolactose state; used in competitive metabolism and the Hill expression for `Z` synthesis. |
| `Obs_Tot_Z` | `Molecules` | `Z()` | Current beta-gal/permease proxy; controls lactose import and metabolism rates. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` creates the three-species/eight-reaction ODE network.
2. `saveConcentrations()` requests concentration-style output.
3. `resetConcentrations()` restores the basal initial condition before simulation.
4. `simulate({method=>"ode", suffix=>"ode", t_start=>0, t_end=>500, n_steps=>500})` integrates the lactose induction time course.
5. `parameter_scan({method=>"ode", parameter=>"l_ext", ...})` scans external lactose over a log range to produce an induction curve.

## 9. Technical caveats and ambiguities

- The source comments explicitly state that these are concentration-based ODE rate expressions; SSA/NFsim would require population-based conversion.
- The BNGL molecule declarations are site-free, so a coder should not look for binding-site or phosphorylation-site mechanisms here.
- `Z` is named beta-galactosidase in comments, but it also functions as the transport/metabolism activity proxy in the equations.
