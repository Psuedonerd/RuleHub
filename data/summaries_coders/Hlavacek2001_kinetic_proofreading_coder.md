# Coder Model Explanation: Hlavacek 2001

## 1. Model identity and scope

- **Model id:** `Hlavacek_2001`
- **Title:** Hlavacek 2001
- **BNGL path:** `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- **YAML path:** `Published/Hlavacek2001/metadata.yaml`
- **Metadata description:** Kinetic proofreading
- **Scope:** A compact kinetic-proofreading receptor signaling model: bivalent ligand captures receptors, forms receptor dimers, advances through five ligand-centered modification states, and resets modification to zero when ligand-receptor bonds dissociate.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 8 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 2 molecule type entries. |
| Seed/species | Yes | 2 initial species entries. |
| Observables | Yes | 10 observable entries. |
| Functions | Yes | 4 function entries. |
| Reaction rules | Yes | 13 reaction rules. |
| Actions | Yes | 6 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `NA` | `6.02214076e23` | @note: \|; Parameters estimated for bispecific IgE interacting with a; bivalent antigen and FcepsilonRI on RBL-2H3 cells.; See Table 1 in Hlavacek et al. (2002). Bimolecular rate; constants converted from concentration-based (M^-1 s^-1) to; population-based (per molecule pair per second) using NA and; V_ref. First-order rate constants are unchanged.; Avogadro constant; /mol |
| `V_ref` | `1e-9` | Extracellular volume per cell; 10^6 cells/ml => V_ref = 10^-9 L/cell; L/cell |
| `NR` | `300000` | Receptors per cell; see Erickson et al. (1987); molecules |
| `NL` | `602` | Ligand at 1 nM: NL = LT * NA * V_ref; molecules |
| `kon1` | `1.661e-8` | Single-site forward rate constant for ligand capture; k_p1 = 1e7 /M/s; kon1 = k_p1 / (NA * V_ref); /(molecule*s) |
| `kon2` | `3.333e-6` | Single-site forward rate constant for crosslinking; k_p2*RT = 1 /s (surface); kon2 = 1/NR; /(molecule*s) |
| `koff` | `0.1` | Single-site dissociation rate constant (k_m1 = k_m2); /s |
| `kp` | `0.4` | Modification rate constant; see Eq. 5-7; in Hlavacek et al. (2002); /s |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `alpha() = kp / (kp + 2 * koff)` | Proofreading parameter alpha (Eq. 15 in; Hlavacek et al., 2002): probability that; the next modification occurs before dimer; dissociation |
| `frac_dimers() = 2 * Obs_Tot_Dimers / NR` | Fraction of receptors in dimers |
| `frac_term() = Obs_D5 / (Obs_Tot_Dimers + 1e-30)` | Fraction of dimers terminally modified |
| `frac_R_term() = 2 * Obs_D5 / NR` | Fraction of all receptors terminally modified |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `L` | 3 | r, r, mod~0~1~2~3~4~5 | mod: 0, 1, 2, 3, 4, 5 | none | binding/modification candidate sites: r, r | Bivalent ligand with two identical receptor-binding sites; and a modification counter (0-5) tracking dimer state |
| `R` | 1 | l | none declared | none | binding/modification candidate sites: l | Monovalent receptor with one ligand-binding site |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `L(r,r,mod~0)` | `NL` | molecules |
| `R(l)` | `NR` | molecules |

## 6. Complete reaction-rule inventory

The source contains **13** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | L, R | `kon1` | binding-pattern rewrite | `L(r,r,mod~0) + R(l) -> L(r!1,r,mod~0).R(l!1)` | Ligand capture: free ligand binds a free receptor.; BioNetGen applies the factor of 2 for the two; equivalent r sites on L automatically.; See Fig. 1(a) in Hlavacek et al. (2002). Forms binding contacts among L, R through L.r, R.l. Rate/expression: kon1. |
| 2 | `Unlabeled` | one-way | L, R | `kon2` | binding-pattern rewrite | `L(r!+,r,mod~0) + R(l) -> L(r!+,r!1,mod~0).R(l!1)` | Receptor crosslinking: singly-bound ligand engages; a second free receptor, forming a dimer.; See Fig. 1(a) in Hlavacek et al. (2002). Forms binding contacts among L, R through R.l. Rate/expression: kon2. |
| 3 | `Unlabeled` | one-way | L, R | `koff` | binding-pattern rewrite | `L(r!1,mod~0).R(l!1) -> L(r,mod~0) + R(l)` | Dimer dissociation with modification reset.; Any L-R bond can break. When a dimer bond opens,; the modification counter resets to 0, implementing; the assumption that receptor modifications are; reversed upon loss of aggregation. For dimers, each; of 2 bonds can break at rate koff, giving total; dimer dissociation rate 2*koff (the factor of 2 is; applied by BioNetGen). For singly-bound ligand,; only the mod~0 rule applies (singly-bound L always; has mod=0). See Eq. 1-7 in Hlavacek et al. (2002). Releases binding contacts among L, R by freeing L.r, R.l. Rate/expression: koff. |
| 4 | `Unlabeled` | one-way | L, R | `koff` | internal-state conversion/modification | `L(r!1,mod~1).R(l!1) -> L(r,mod~0) + R(l)` | Couples state updates (L.mod 1→0) with binding changes; formed sites: none; released sites: L.r, R.l. Rate/expression: koff. |
| 5 | `Unlabeled` | one-way | L, R | `koff` | internal-state conversion/modification | `L(r!1,mod~2).R(l!1) -> L(r,mod~0) + R(l)` | Couples state updates (L.mod 2→0) with binding changes; formed sites: none; released sites: L.r, R.l. Rate/expression: koff. |
| 6 | `Unlabeled` | one-way | L, R | `koff` | internal-state conversion/modification | `L(r!1,mod~3).R(l!1) -> L(r,mod~0) + R(l)` | Couples state updates (L.mod 3→0) with binding changes; formed sites: none; released sites: L.r, R.l. Rate/expression: koff. |
| 7 | `Unlabeled` | one-way | L, R | `koff` | internal-state conversion/modification | `L(r!1,mod~4).R(l!1) -> L(r,mod~0) + R(l)` | Couples state updates (L.mod 4→0) with binding changes; formed sites: none; released sites: L.r, R.l. Rate/expression: koff. |
| 8 | `Unlabeled` | one-way | L, R | `koff` | internal-state conversion/modification | `L(r!1,mod~5).R(l!1) -> L(r,mod~0) + R(l)` | Couples state updates (L.mod 5→0) with binding changes; formed sites: none; released sites: L.r, R.l. Rate/expression: koff. |
| 9 | `Unlabeled` | one-way | L | `kp` | internal-state conversion/modification | `L(r!+,r!+,mod~0) -> L(r!+,r!+,mod~1)` | Sequential modification of dimers (unidirectional).; bound (dimers). Each step proceeds at rate kp.; See Fig. 1(b) in Hlavacek et al. (2002). Updates internal state(s) on L: L.mod 0→1. Rate/expression: kp. |
| 10 | `Unlabeled` | one-way | L | `kp` | internal-state conversion/modification | `L(r!+,r!+,mod~1) -> L(r!+,r!+,mod~2)` | Updates internal state(s) on L: L.mod 1→2. Rate/expression: kp. |
| 11 | `Unlabeled` | one-way | L | `kp` | internal-state conversion/modification | `L(r!+,r!+,mod~2) -> L(r!+,r!+,mod~3)` | Updates internal state(s) on L: L.mod 2→3. Rate/expression: kp. |
| 12 | `Unlabeled` | one-way | L | `kp` | internal-state conversion/modification | `L(r!+,r!+,mod~3) -> L(r!+,r!+,mod~4)` | Updates internal state(s) on L: L.mod 3→4. Rate/expression: kp. |
| 13 | `Unlabeled` | one-way | L | `kp` | internal-state conversion/modification | `L(r!+,r!+,mod~4) -> L(r!+,r!+,mod~5)` | Updates internal state(s) on L: L.mod 4→5. Rate/expression: kp. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Free_L` | `Species` | `L(r,r,mod~0)` | Free ligand (both sites unbound) |
| `Obs_Free_R` | `Species` | `R(l)` | Free receptor |
| `Obs_Singly_Bound` | `Species` | `L(r!+,r,mod~0)` | Singly-bound ligand (one site bound, one free) |
| `Obs_Tot_Dimers` | `Species` | `L(r!+,r!+)` | Total dimers (ligand with both sites bound) |
| `Obs_D0` | `Species` | `L(r!+,r!+,mod~0)` | Dimers by modification state |
| `Obs_D1` | `Species` | `L(r!+,r!+,mod~1)` | counts species-level matches |
| `Obs_D2` | `Species` | `L(r!+,r!+,mod~2)` | counts species-level matches |
| `Obs_D3` | `Species` | `L(r!+,r!+,mod~3)` | counts species-level matches |
| `Obs_D4` | `Species` | `L(r!+,r!+,mod~4)` | counts species-level matches |
| `Obs_D5` | `Species` | `L(r!+,r!+,mod~5)` | Terminally modified dimers (fully activated) |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` — 9 species, 14 reactions

2. `saveConcentrations()` — @note: \|; Network is small (9 species, ~14 reactions). ODE is; the preferred method. SSA is feasible but slow at; NR=300000; reduce NR and NL proportionally if SSA; performance is needed.

3. `resetConcentrations()` — Kinetic proofreading time course; @protocol: \|; Simulate from all-free initial conditions to; steady state (600 s). Binding equilibrates on; the timescale 1/(2*kon1*NR) ~ 100 s. Dimer; modification is faster (~1/kp = 2.5 s) but; depends on dimer availability. The time course; shows progressive dimer formation followed by; sequential population of modification states,; with early states populated transiently before; the terminal state D5 accumulates. At steady; state, D5/D_total should approach alpha^5 ~ 13%.

4. `simulate({method=>"ode",suffix=>"ode", t_start=>0,t_end=>600,n_steps=>300})` — active execution command in the actions block

5. `resetConcentrations()` — t_start=>0,t_end=>600,n_steps=>300}); Kinetic proofreading demonstration: koff scan; @protocol: \|; Scan koff from 0.001 to 1/s (log scale) at fixed; ligand concentration, showing how the steady-state; fraction of terminally modified dimers decreases; sharply with increasing koff. This demonstrates; kinetic proofreading: small changes in the ligand; dissociation rate produce large changes in terminal; modification.; Note: this scan varies koff alone at fixed LT.; The controlled comparison in Hlavacek et al. (2002); Fig. 3(b) simultaneously adjusts LT to hold; 2D/RT = const. Despite this difference, the scan; qualitatively demonstrates the exponential; sensitivity of terminal modification to koff.; @figure: Fig. 3(b) in Hlavacek et al. (2002)

6. `parameter_scan({method=>"ode",parameter=>"koff", par_min=>0.001,par_max=>1.0,n_scan_pts=>30, log_scale=>1, t_start=>0,t_end=>1000,n_steps=>100, suffix=>"scan_koff"})` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- The modification counter is stored on ligand L rather than receptor R, so L.mod is the implementation state for dimer progress.

- The two repeated L.r sites are intentionally equivalent; BioNetGen symmetry factors matter for ligand capture and dimer breakage.

- No compartments or anchors are declared; receptor surface context is represented by molecule patterns and rate constants rather than an explicit membrane compartment.
