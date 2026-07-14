# Coder Model Explanation: Dreisigmeyer 2008

## 1. Model identity and scope

- **Model id:** `Dreisigmeyer_2008`
- **Title:** Dreisigmeyer 2008
- **BNGL path:** `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- **YAML path:** `Published/Dreisigmeyer2008/metadata.yaml`
- **Metadata description:** Lac operon
- **Scope:** A concentration-based lac operon ODE model with three explicit dynamic species: intracellular lactose, allolactose, and beta-galactosidase. The rules encode lactose import, lactose/allolactose metabolism, beta-gal synthesis from a Hill function of allolactose, and growth dilution.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 18 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 3 molecule type entries. |
| Seed/species | Yes | 3 initial species entries. |
| Observables | Yes | 3 observable entries. |
| Functions | Yes | 5 function entries. |
| Reaction rules | Yes | 8 reaction rules. |
| Actions | Yes | 5 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `NA` | `6.02214076e23` | @note: \|; Concentration units: uM. Time units: min.; Original paper (Table 1) uses nM; the source Antimony model; converted to uM (nM / 1000, mM * 1000).; Avogadro constant (for potential population-based conversion); /mol |
| `V_ref` | `1e-15` | Reference volume: E. coli mean cell volume; (Kubitschek and Friske, 1986; Ref. [30] in; Dreisigmeyer et al., 2008); L/cell |
| `f` | `1.0` | Subvolume scaling factor (single cell); dimensionless |
| `l_ext` | `1000.0` | External lactose (constant boundary condition; 1.0 mM = 1000 uM); uM |
| `growth_rate` | `0.0231` | Growth dilution rate (gamma in paper; ~30 min doubling time); /min |
| `alpha` | `600.0` | Permease transport parameters; Import turnover number; Eq. (1a) in Dreisigmeyer et al. (2008); /min |
| `phi` | `0.5` | Ratio of export-to-import turnover numbers; dimensionless |
| `rho` | `0.1` | Ratio of import-to-export Michaelis constants; dimensionless |
| `K_i` | `500.0` | Permease Michaelis constant (5e5 nM = 500 uM); uM |
| `beta` | `2.85e4` | Beta-gal lactose metabolism parameters; Lactose turnover number; /min |
| `nu` | `0.468` | Lactose -> allolactose branching fraction; dimensionless |
| `K_m_l` | `2530.0` | Beta-gal lactose Michaelis constant (2.53 mM = 2530 uM); uM |
| `delta` | `2.30e4` | Beta-gal allolactose metabolism parameters; Allolactose turnover number; /min |
| `K_m_a` | `1200.0` | Beta-gal allolactose Michaelis constant (1.2 mM = 1200 uM); uM |
| `eps` | `34.285` | Beta-gal expression parameters; Fully induced beta-gal level (34286 nM = 34.285 uM); uM |
| `c_basal` | `0.0343` | Basal beta-gal level (c in paper; 34.3 nM = 0.0343 uM); uM |
| `K_z` | `105.0` | Half-maximal allolactose induction level (1.05e5 nM = 105 uM); uM |
| `n_Hill` | `2.0` | Hill coefficient for lac induction; dimensionless |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `transport_L() = alpha * Obs_Tot_Z * (l_ext - phi * rho * Obs_Tot_L) / (K_i + l_ext + rho * Obs_Tot_L)` | Permease-dependent lactose transport (net import);; Eq. (1a), first term in Dreisigmeyer et al. (2008) |
| `metab_L() = (beta / K_m_l) * Obs_Tot_Z / (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)` | Effective first-order rate constant for beta-gal-catalyzed; lactose degradation; Eq. (1a), second term in; Dreisigmeyer et al. (2008). Competitive inhibition: shared; denominator (1 + a/K_m_a + l/K_m_l). BNG multiplies by [L]. |
| `prod_A() = nu * (beta / K_m_l) * Obs_Tot_Z * Obs_Tot_L / (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)` | Allolactose production (branching fraction of lactose; degradation); Eq. (1b), first term in Dreisigmeyer et al. (2008) |
| `metab_A() = (delta / K_m_a) * Obs_Tot_Z / (1 + Obs_Tot_A / K_m_a + Obs_Tot_L / K_m_l)` | Effective first-order rate constant for beta-gal-catalyzed; allolactose degradation; Eq. (1b), second term in; Dreisigmeyer et al. (2008). BNG multiplies by [A]. |
| `syn_Z() = growth_rate * (c_basal + eps * Obs_Tot_A^n_Hill / (K_z^n_Hill + Obs_Tot_A^n_Hill))` | Beta-gal synthesis: basal + Hill-induced;; Eq. (1c) in Dreisigmeyer et al. (2008) |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `L` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | Internal lactose (l in Dreisigmeyer et al., 2008) |
| `A` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | Allolactose (a in Dreisigmeyer et al., 2008) |
| `Z` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance | Beta-galactosidase (z in Dreisigmeyer et al., 2008) |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `L()` | `0` | uM |
| `A()` | `0` | uM |
| `Z()` | `c_basal` | uM |

## 6. Complete reaction-rule inventory

The source contains **8** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | L | `transport_L()` | source/synthesis or algebraic source term | `0 -> L()` | Permease-dependent lactose import. Produces L while retaining or consuming an abstract source. Rate/expression: transport_L(). |
| 2 | `Unlabeled` | one-way | L | `metab_L()` | sink/degradation/removal | `L() -> 0` | Beta-gal-catalyzed lactose degradation. Removes L from the dynamic pool through the zero/sink side of the rule. Rate/expression: metab_L(). |
| 3 | `Unlabeled` | one-way | L | `growth_rate` | sink/degradation/removal | `L() -> 0` | Growth dilution of internal lactose. Removes L from the dynamic pool through the zero/sink side of the rule. Rate/expression: growth_rate. |
| 4 | `Unlabeled` | one-way | A | `prod_A()` | source/synthesis or algebraic source term | `0 -> A()` | Allolactose production from lactose metabolism. Produces A while retaining or consuming an abstract source. Rate/expression: prod_A(). |
| 5 | `Unlabeled` | one-way | A | `metab_A()` | sink/degradation/removal | `A() -> 0` | Beta-gal-catalyzed allolactose degradation. Removes A from the dynamic pool through the zero/sink side of the rule. Rate/expression: metab_A(). |
| 6 | `Unlabeled` | one-way | A | `growth_rate` | sink/degradation/removal | `A() -> 0` | Growth dilution of allolactose. Removes A from the dynamic pool through the zero/sink side of the rule. Rate/expression: growth_rate. |
| 7 | `Unlabeled` | one-way | Z | `syn_Z()` | source/synthesis or algebraic source term | `0 -> Z()` | Beta-gal synthesis (basal + allolactose-induced Hill function). Produces Z while retaining or consuming an abstract source. Rate/expression: syn_Z(). |
| 8 | `Unlabeled` | one-way | Z | `growth_rate` | sink/degradation/removal | `Z() -> 0` | Growth dilution of beta-galactosidase. Removes Z from the dynamic pool through the zero/sink side of the rule. Rate/expression: growth_rate. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Tot_L` | `Molecules` | `L()` | Intracellular concentrations (uM) |
| `Obs_Tot_A` | `Molecules` | `A()` | counts molecule-pattern matches |
| `Obs_Tot_Z` | `Molecules` | `Z()` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` — 3 species, 8 reactions

2. `saveConcentrations()` — active execution command in the actions block

3. `resetConcentrations()` — @note: \|; Two protocols: (1) time-course relaxation, (2) induction; curve scan. Both are active.; Time-course relaxation to steady state; @protocol: \|; Integrate from uninduced initial conditions (L=0, A=0,; Z=c_basal) with constant external lactose l_ext = 1000 uM.; The system relaxes to a partially induced steady state; (Z ~ 0.33 uM, ~10x basal) over ~200 min.

4. `simulate({method=>"ode",suffix=>"ode", t_start=>0,t_end=>500,n_steps=>500})` — active execution command in the actions block

5. `parameter_scan({method=>"ode",parameter=>"l_ext", par_min=>0.01,par_max=>1e6,n_scan_pts=>100, log_scale=>1,t_start=>0,t_end=>500,n_steps=>200, suffix=>"scan"})` — Induction curve: parameter scan over external lactose; @protocol: \|; Scan l_ext logarithmically from 0.01 to 1e6 uM. Each; scan point runs to t = 500 min (steady state). The; resulting Z-vs-l_ext curve is monostable — no S-shaped; bistable region — consistent with the paper's conclusion.; @figure: Fig. 8 (top, gamma = 0.0231) in Dreisigmeyer et al. (2008)

## 9. Technical caveats and ambiguities

- The source comments explicitly say the rate laws are concentration-based and ODE-only; SSA/NFsim would require population-rate conversion.

- There are no compartments or anchors, so all spatial interpretation is implicit.

- The model uses source/sink rules rather than binding-site combinatorics; most behavior is carried by functions and observables.
