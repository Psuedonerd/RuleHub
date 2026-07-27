# Coder Model Explanation: Barua 2007 receptor–SHP2 regulation model

## 1. Model identity and scope

`Barua_2007` models how a pre-dimerized phosphoreceptor recruits SHP2 and regulates its autoinhibition and receptor-directed phosphatase activity. Sources: `Published/Barua2007/Barua_2007.bngl` and `Published/Barua2007/metadata.yaml`.

## 2. BNGL block inventory

The file contains 24 active parameter declarations, 2 molecule types, 2 initial-species declarations, 0 functions, 23 concrete reaction rules, 1 observable declaration, and 2 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Every active parameter declaration is listed below; expressions are retained verbatim so scaling and dependencies remain inspectable.

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

**Rule-family orientation.** The family/context column preserves the nearest active BNGL comment; the implementation column preserves every molecule, site, state, bond, direction, and rate expression. Thus repeated families remain one row per concrete rule rather than being collapsed.

| # | Family / technical meaning | Direction | Exact site-level implementation and rate law |
| ---: | --- | --- | --- |
| 1 | Intra-complex phosphorylation | One-way | `R(DD!+,Y1~U) -> R(DD!+,Y1~P)  kkin_Y1` |
| 2 | Equilibrium between the closed form and open form of S | Reversible | `S(NSH2~C,PTP~C) <-> S(NSH2~O,PTP~O)  kopen,kclose` |
| 3 | Binding of S(CSH2) from cytosol | Reversible | `R(Y2~P) + S(CSH2) <-> R(Y2~P!1).S(CSH2!1)  kon_CSH2,koff_CSH2 exclude_reactants(2,R)` |
| 4 | Binding of S(NSH2~O) from cytosol | Reversible | `R(Y2~P) + S(NSH2~O) <-> R(Y2~P!1).S(NSH2~O!1)  kon_NSH2,koff_NSH2 exclude_reactants(2,R)` |
| 5 | Binding of S(PTP~O) from cytosol | Reversible | `R(Y1~P) + S(PTP~O) <-> R(Y1~P!1).S(PTP~O!1)  kon_PTP,koff_PTP exclude_reactants(2,R)` |
| 6 | Dephosphorylation of R(Y1~P) | One-way | `R(Y1~P!1).S(PTP~O!1) -> R(Y1~U) + S(PTP~O)  kcat_PTP` |
| 7 | Dephosphorylation of R(Y1~P) | One-way | `R(Y1~P!1).S(PTP~O!1) -> R(Y1~U).S(PTP~O)  kcat_PTP` |
| 8 | 1 Intra-complex binding: CSH2 bound, association of NSH2 (open) with other receptor | Reversible | `R(Y2~P).S(NSH2~O,CSH2!+,PTP~O) <-> R(Y2~P!1).S(NSH2~O!1,CSH2!+,PTP~O)  chi_r1*kon_NSH2,koff_NSH2` |
| 9 | 2 Intra-complex binding: CSH2 bound, association of PTP (open) with same receptor | Reversible | `R(Y1~P,Y2~P!1).S(NSH2~O,CSH2!1,PTP~O) <-> R(Y1~P!2,Y2~P!1).S(NSH2~O,CSH2!1,PTP~O!2)  chi_r2*kon_PTP,koff_PTP` |
| 10 | 3 Intra-complex binding: CSH2 bound, association of PTP (open) with other receptor | Reversible | `R(Y1~P).R(Y2~P!1).S(NSH2~O,CSH2!1,PTP~O) <-> R(Y1~P!2).R(Y2~P!1).S(NSH2~O,CSH2!1,PTP~O!2)  chi_r3*kon_PTP,koff_PTP` |
| 11 | 4 Intra-complex binding: NSH2 bound, association of CSH2 with other receptor | Reversible | `R(Y2~P).S(NSH2~O!+,CSH2,PTP~O) <-> R(Y2~P!1).S(NSH2~O!+,CSH2!1,PTP~O)  chi_r1*kon_CSH2,koff_CSH2` |
| 12 | 5 Intra-complex binding: NSH2 bound, association of PTP with other receptor | Reversible | `R(Y1~P).R(Y2~P!1).S(NSH2~O!1,CSH2,PTP~O) <-> R(Y1~P!2).R(Y2~P!1).S(NSH2~O!1,CSH2,PTP~O!2)  chi_r4*kon_PTP,koff_PTP` |
| 13 | 6 Intracomplex binding: NSH2 bound, association of PTP with same receptor | Reversible | `R(Y1~P,Y2~P!1).S(NSH2~O!1,CSH2,PTP~O) <-> R(Y1~P!2,Y2~P!1).S(NSH2~O!1,CSH2,PTP~O!2)  chi_r5*kon_PTP,koff_PTP` |
| 14 | 7 Intra-complex binding: PTP bound, association of CSH2 with same receptor | Reversible | `R(Y1~P!1,Y2~P).S(NSH2~O,CSH2,PTP~O!1) <-> R(Y1~P!1,Y2~P!2).S(NSH2~O,CSH2!2,PTP~O!1)  chi_r2*kon_CSH2,koff_CSH2` |
| 15 | 8 Intra-complex binding: PTP bound, association of CSH2 with other receptor | Reversible | `R(Y1~P!1).R(Y2~P).S(NSH2~O,CSH2,PTP~O!1) <-> R(Y1~P!1).R(Y2~P!2).S(NSH2~O,CSH2!2,PTP~O!1)  chi_r3*kon_CSH2,koff_CSH2` |
| 16 | 9 Intra-complex binding: PTP bound, association of NSH2 with other receptor | Reversible | `R(Y1~P!1).R(Y2~P).S(NSH2~O,CSH2,PTP~O!1) <-> R(Y1~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2,PTP~O!1)  chi_r4*kon_NSH2,koff_NSH2` |
| 17 | 10 Intra-complex binding: PTP bound, association of NSH2 with same receptor | Reversible | `R(Y1~P!1,Y2~P).S(NSH2~O,CSH2,PTP~O!1) <-> R(Y1~P!1,Y2~P!2).S(NSH2~O!2,CSH2,PTP~O!1)  chi_r5*kon_NSH2,koff_NSH2` |
| 18 | 11 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as CSH2 | Reversible | `R(Y1~P,Y2~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2!1,PTP~O) <-> R(Y1~P!3,Y2~P!1).R(Y2~P!2).S(NSH2~O!2,CSH2!1,PTP~O!3) chi_r6*kon_PTP,koff_PTP` |
| 19 | 12 Intra-complex binding: CSH2 & NSH2 bound, assoc. of PTP with same receptor as NSH2 | Reversible | `R(Y1~P,Y2~P!1).R(Y2~P!2).S(NSH2~O!1,CSH2!2,PTP~O) <-> R(Y1~P!3,Y2~P!1).R(Y2~P!2).S(NSH2~O!1,CSH2!2,PTP~O!3) chi_r7*kon_PTP,koff_PTP` |
| 20 | 13 Intra-complex binding: CSH2 & PTP bound to the same receptor, assoc. of NSH2 | Reversible | `R(Y1~P!1,Y2~P!2).R(Y2~P).S(NSH2~O,CSH2!2,PTP~O!1) <-> R(Y1~P!1,Y2~P!2).R(Y2~P!3).S(NSH2~O!3,CSH2!2,PTP~O!1) chi_r8*kon_NSH2,koff_NSH2` |
| 21 | 14 Intra-complex binding: CSH2 & PTP bound to different receptors, assoc. of NSH2 | Reversible | `R(Y2~P!1).R(Y1~P!2,Y2~P).S(NSH2~O,CSH2!1,PTP~O!2) <-> R(Y2~P!1).R(Y1~P!2,Y2~P!3).S(NSH2~O!3,CSH2!1,PTP~O!2) chi_r9*kon_NSH2,koff_NSH2` |
| 22 | 15 Intra-complex binding: PTP & NSH2 bound to different receptors, assoc. of CSH2 | Reversible | `R(Y2~P!1).R(Y1~P!2,Y2~P).S(NSH2~O!1,CSH2,PTP~O!2) <-> R(Y2~P!1).R(Y1~P!2,Y2~P!3).S(NSH2~O!1,CSH2!3,PTP~O!2) chi_r10*kon_CSH2,koff_CSH2` |
| 23 | 16 Intra-complex binding: PTP & NSH2 bound to same receptor, assoc. of CSH2 | Reversible | `R(Y1~P!1,Y2~P!2).R(Y2~P).S(NSH2~O!2,CSH2,PTP~O!1) <-> R(Y1~P!1,Y2~P!2).R(Y2~P!3).S(NSH2~O!2,CSH2!3,PTP~O!1) chi_r11*kon_CSH2,koff_CSH2` |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Molecules  pYR      R(Y1~P!?)`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>1});`
- `simulate_ode({t_end=>1000,n_steps=>100,steady_state=>1,atol=>1e-10,rtol=>1e-8,sparse=>0});`

## 9. Technical caveats and ambiguities

The receptor `R` and phosphatase `S` are abstract encodings of a pre-dimerized receptor and SHP2-like regulator. Multi-line rules enumerate receptor/SHP2 topologies; omitted sites are unconstrained, and exact bond labels are local to each pattern.
