# Detailed Model Explanation: Barua 2007 receptor–SHP2 regulation model

## 1. Model identity and scope

`Barua_2007` models how a pre-dimerized phosphoreceptor recruits SHP2 and regulates its autoinhibition and receptor-directed phosphatase activity. Sources: `Published/Barua2007/Barua_2007.bngl` and `Published/Barua2007/metadata.yaml`.

## 2. BNGL block inventory

The file contains 24 active parameter declarations, 2 molecule types, 2 initial-species declarations, 0 functions, 23 concrete reaction rules, 1 observable declaration, and 2 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Parameters fall into receptor phosphorylation, S opening/closing, domain-specific association/dissociation, intracomplex effective-concentration multipliers (`chi_r*`), catalysis, and initial totals. They remain one-per-bullet below so the domain-specific rates are directly comparable.

- `kdim            1000`
- `kopen           10`
- `kclose          500`
- `kon_CSH2        1`
- `koff_CSH2       1`
- `kon_NSH2        1`
- `koff_NSH2       1`
- `kkin_Y1         0.1`
- `kon_PTP         1`
- `koff_PTP        10`
- `kcat_PTP        1`
- `chi_r1          1000`
- `chi_r2          100`
- `chi_r3          1000`
- `chi_r4          1000`
- `chi_r5          100`
- `chi_r6          100`
- `chi_r7          100`
- `chi_r8          1000  # Equals chi_r1*chi_r6/chi_r2`
- `chi_r9          100   # Equals chi_r1*chi_r7/chi_r3`
- `chi_r10         100   # Equals chi_r1*chi_r6/chi_r4`
- `chi_r11         1000  # Equals chi_r1*chi_r7/chi_r5`
- `R_dim		0.025 # R_tot= 2*R_dim`
- `S_tot		0.05`

There is no functions block; rules use parameters or literal expressions directly.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `R` | 3 | `DD, Y1, Y2` | `Y1: U,P; Y2: P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `R(DD,Y1~U~P,Y2~P)` |
| `S` | 3 | `NSH2, CSH2, PTP` | `NSH2: C,O; PTP: C,O` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `S(NSH2~C~O,CSH2,PTP~C~O)` |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are declared. Initial patterns and amounts are exhaustive below:

- `S(NSH2~C,CSH2,PTP~C)				S_tot`
- `R(DD!1,Y1~U,Y2~P).R(DD!1,Y1~U,Y2~P)             R_dim`

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules first establish receptor phosphorylation and SHP2 opening, then enumerate cytosolic recruitment and intracomplex combinations of CSH2, NSH2, and PTP contacts. Separate rows preserve whether a contact is made on the same or partner receptor.

| # | Direction | Required molecules/sites | Net bond, state, or species edit | Rate/expression | Functional interpretation |
| ---: | --- | --- | --- | --- | --- |
| 1 | One-way | `R` (`DD`, `Y1`) | `R.Y1` U→P | kkin_Y1 | Intra-complex phosphorylation. |
| 2 | Reversible | `S` (`NSH2`, `PTP`) | `S.NSH2` C→O; `S.PTP` C→O | kopen,kclose | Equilibrium between the closed form and open form of S. |
| 3 | Reversible | Phosphorylated `R.Y2` and cytosolic `S.CSH2`; the reactant filter excludes a second receptor in the incoming S pattern | Creates/removes the `R.Y2–S.CSH2` bond | `kon_CSH2`; `koff_CSH2` | Recruits SHP2-like `S` through its C-terminal SH2 domain. |
| 4 | Reversible | Phosphorylated `R.Y2` and open cytosolic `S.NSH2`; the same receptor-exclusion filter applies | Creates/removes the `R.Y2–S.NSH2` bond | `kon_NSH2`; `koff_NSH2` | Recruits open S through its N-terminal SH2 domain. |
| 5 | Reversible | Phosphorylated `R.Y1` and open cytosolic `S.PTP`; the same receptor-exclusion filter applies | Creates/removes the `R.Y1–S.PTP` bond | `kon_PTP`; `koff_PTP` | Directly engages the catalytic PTP domain with its receptor substrate site. |
| 6 | One-way | `R` (`Y1`); `S` (`PTP`) | `R.Y1` P→U; releases the explicitly site-matched bond(s) | kcat_PTP | Dephosphorylation of R(Y1~P); this `kcat_PTP` variant requires `R` (`Y1`); `S` (`PTP`) and `R.Y1` P→U; releases the explicitly site-matched bond(s). |
| 7 | One-way | `R` (`Y1`); `S` (`PTP`) | `R.Y1` P→U; releases the explicitly site-matched bond(s) | kcat_PTP | Dephosphorylation of R(Y1~P); this `kcat_PTP` variant requires `R` (`Y1`); `S` (`PTP`) and `R.Y1` P→U; releases the explicitly site-matched bond(s). |
| 8 | Reversible | `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r1*kon_NSH2,koff_NSH2 | 1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor. |
| 9 | Reversible | `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r2*kon_PTP,koff_PTP | 2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor. |
| 10 | Reversible | `R` (`Y1`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r3*kon_PTP,koff_PTP | 3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor. |
| 11 | Reversible | `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r1*kon_CSH2,koff_CSH2 | 4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor. |
| 12 | Reversible | `R` (`Y1`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r4*kon_PTP,koff_PTP | 5 Intra-complex binding: NSH2 bound, association of PTP with other receptor. |
| 13 | Reversible | `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r5*kon_PTP,koff_PTP | 6 Intracomplex binding: NSH2 bound, association of PTP with same receptor. |
| 14 | Reversible | `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r2*kon_CSH2,koff_CSH2 | 7 Intra-complex binding: PTP bound, association of CSH2 with same receptor. |
| 15 | Reversible | `R` (`Y1`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r3*kon_CSH2,koff_CSH2 | 8 Intra-complex binding: PTP bound, association of CSH2 with other receptor. |
| 16 | Reversible | `R` (`Y1`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r4*kon_NSH2,koff_NSH2 | 9 Intra-complex binding: PTP bound, association of NSH2 with other receptor. |
| 17 | Reversible | `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r5*kon_NSH2,koff_NSH2 | 10 Intra-complex binding: PTP bound, association of NSH2 with same receptor. |
| 18 | Reversible | `R` (`Y1`, `Y2`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r6*kon_PTP,koff_PTP | 11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2. |
| 19 | Reversible | `R` (`Y1`, `Y2`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r7*kon_PTP,koff_PTP | 12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2. |
| 20 | Reversible | `R` (`Y1`, `Y2`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r8*kon_NSH2,koff_NSH2 | 13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2. |
| 21 | Reversible | `R` (`Y2`); `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r9*kon_NSH2,koff_NSH2 | 14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2. |
| 22 | Reversible | `R` (`Y2`); `R` (`Y1`, `Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r10*kon_CSH2,koff_CSH2 | 15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2. |
| 23 | Reversible | `R` (`Y1`, `Y2`); `R` (`Y2`); `S` (`NSH2`, `CSH2`, `PTP`) | forms the explicitly site-matched bond(s) | chi_r11*kon_CSH2,koff_CSH2 | 16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2. |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Molecules  pYR      R(Y1~P!?)`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>1000,n_steps=>100,steady_state=>1,atol=>1e-10,rtol=>1e-8,sparse=>0});`

## 9. Technical caveats and ambiguities

The receptor `R` and phosphatase `S` are abstract encodings of a pre-dimerized receptor and SHP2-like regulator. Multi-line rules enumerate receptor/SHP2 topologies; omitted sites are unconstrained, and exact bond labels are local to each pattern.
