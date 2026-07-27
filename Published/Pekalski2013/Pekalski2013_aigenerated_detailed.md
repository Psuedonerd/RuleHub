# Coder Model Explanation: Pekalski 2013 autocrine TNF–NF-κB model

## 1. Model identity and scope

`Pekalski_2013` models how autocrine tumor necrosis factor (TNF) signaling produces NF-κB pulses controlled by IκBα and A20 feedback. Sources: `Published/Pekalski2013/Pekalski_2013.bngl` and `Published/Pekalski2013/metadata.yaml`.

## 2. BNGL block inventory

The file contains 42 active parameter declarations, 14 molecule types, 29 initial-species declarations, 4 functions, 40 concrete reaction rules, 29 observable declarations, and 4 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Every active parameter declaration is listed below; expressions are retained verbatim so scaling and dependencies remain inspectable.

- `k_v         5        # ratio of C:N volumes`
- `R         7e+3       # median number of receptors`
- `K_N       1e+5       # number of IKKK molecules`
- `K_NN      2e+5       # number of IKK molecules`
- `NFkB_tot  1e+5       # number of NF-kB molecules`
- `c_deg         2e-4`
- `k_b         1.2e-5`
- `c_sec         1e-5`
- `c_b       1e+4`
- `k_f         1.2e-3`
- `k_a           1e-5`
- `k_A20     1e+5`
- `k_i           1e-2`
- `k_1           6e-10`
- `k_2       1e+4`
- `k_3           2e-3`
- `k_4           1e-3`
- `q_1           4e-7`
- `q_2           1e-6`
- `q_1t          4e-8`
- `q_2t          1e-6`
- `q_2tt         2e-3`
- `lambda      0.025    #  for SK-N-AS cells: 0.025, for MEFs: 0.004`
- `c_1           1e-1`
- `c_3         7.5e-4`
- `c_4           5e-1`
- `c_3t        7.5e-4`
- `c_4t          5e-2`
- `a_1           5e-7`
- `a_2           1e-7`
- `a_3           5e-7`
- `c_5           5e-4`
- `t_p           1e-2`
- `c_5a          1e-4`
- `c_5t          2e-4`
- `c_6a          2e-5`
- `i_1           1e-2`
- `e_2a          5e-2`
- `i_1a          2e-3`
- `e_1a          5e-3`
- `k_NFkBIkB     a_1 * k_v`
- `k_TNFdeg      c_sec + c_5t`

Functions are executable rate/readout logic:

- `k_Ractivation        c_sec/(TNFR_i+c_b)`
- `k_IKKKactivation     TNFR_a*k_a*k_A20/(k_A20+A20)`
- `k_IKKactivation      k_1*IKKK_a*IKKK_a`
- `k_IKKintermetiation  k_3/k_2*(k_2+A20)`

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `TNFR` | 1 | `st` | `st: a,i` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TNFR(st~a~i)             # active/inactive TNFR1 receptors` |
| `IKK` | 1 | `st` | `st: n,a,i,ii` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IKK(st~n~a~i~ii)      # neutral/active/inactive/inactive intermediate form of IKK kinase` |
| `IKKK` | 1 | `st` | `st: n,a` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IKKK(st~n~a)          # neutral/active  form of IKKK` |
| `IkBa` | 3 | `loc, pho, bin` | `loc: n,c; pho: 0,p` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IkBa(loc~n~c,pho~0~p,bin)    # nuclear/cytoplasmic, unphosphorylated/phosphorylated IkB` |
| `IkBa_mRNA` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `IkBa_mRNA()                # IkBa transcript` |
| `A20` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `A20()                 # cytoplasmic A20` |
| `A20_mRNA` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `A20_mRNA()                # A20 transcript` |
| `NFkB` | 2 | `loc, bin` | `loc: n,c` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `NFkB(loc~n~c,bin)     # nuclear/cytoplasmic NFkB` |
| `TNF` | 1 | `loc` | `loc: e,i` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TNF(loc~e~i)          # extracellular/intracellular TNFa` |
| `TNF_mRNA` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `TNF_mRNA()                # TNFa transcript` |
| `GIkBa` | 1 | `st` | `st: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `GIkBa(st~0~1)          # discrete random variable, st of IkBa gene` |
| `GA20` | 1 | `st` | `st: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `GA20(st~0~1)          # discrete random variable, st of A20 gene` |
| `GTNF` | 1 | `st` | `st: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `GTNF(st~0~1)          # discrete random variable, st of TNFa gene` |
| `Trash` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `Trash()` |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are declared. Initial patterns and amounts are exhaustive below:

- `TNFR(st~a)           0`
- `TNFR(st~i)           R`
- `IKK(st~n)         K_NN`
- `IKK(st~a)            0`
- `IKK(st~i)            0`
- `IKK(st~ii)           0`
- `IKKK(st~n)         K_N`
- `IKKK(st~a)           0`
- `IkBa(loc~n,pho~p,bin)       0`
- `IkBa(loc~n,pho~0,bin)       0.06*NFkB_tot`
- `IkBa(loc~c,pho~0,bin)       0.1*NFkB_tot`
- `IkBa_mRNA()         10`
- `A20()           3*1e4`
- `A20_mRNA()          10`
- `NFkB(loc~n,bin)      0`
- `NFkB(loc~c,bin)   1e5-NFkB_tot`
- `TNF(loc~e)           0`
- `TNF(loc~i)           0`
- `TNF_mRNA()           0`
- `GIkBa(st~0)          2    #2 Number of IkBa gene copies`
- `GIkBa(st~1)          0`
- `GA20(st~0)           2    #2 Number of A20 gene copies`
- `GA20(st~1)           0`
- `GTNF(st~0)           2    #2 Number of TNFa gene copies`
- `GTNF(st~1)           0`
- `NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)   NFkB_tot`
- `NFkB(loc~n,bin!0).IkBa(loc~n,pho~0,bin!0)   0`
- `NFkB(loc~c,bin!0).IkBa(loc~c,pho~p,bin!0)   0`
- `Trash()     0`

## 6. Complete reaction-rule inventory

**Rule-family orientation.** The family/context column preserves the nearest active BNGL comment; the implementation column preserves every molecule, site, state, bond, direction, and rate expression. Thus repeated families remain one row per concrete rule rather than being collapsed.

| # | Family / technical meaning | Direction | Exact site-level implementation and rate law |
| ---: | --- | --- | --- |
| 1 | TNFR1 activation and signal transduction cascade | One-way | `TNF(loc~e)               ->  Trash()                  c_deg` |
| 2 | TNFR1 activation and signal transduction cascade | One-way | `TNFR(st~i) + TNF(loc~e)  ->  TNFR(st~a)  + TNF(loc~e) k_b` |
| 3 | TNFR1 activation and signal transduction cascade | One-way | `TNFR(st~i) + TNF(loc~i)  ->  TNFR(st~a)  + TNF(loc~i) k_Ractivation` |
| 4 | TNFR1 activation and signal transduction cascade | One-way | `TNFR(st~a)               ->  TNFR(st~i)               k_f` |
| 5 | TNFR1 activation and signal transduction cascade | One-way | `IKKK(st~n)               ->  IKKK(st~a)               k_IKKKactivation` |
| 6 | TNFR1 activation and signal transduction cascade | One-way | `IKKK(st~a)               ->  IKKK(st~n)               k_i` |
| 7 | TNFR1 activation and signal transduction cascade | One-way | `IKK(st~n)                ->  IKK(st~a)                k_IKKactivation` |
| 8 | TNFR1 activation and signal transduction cascade | One-way | `IKK(st~a)                ->  IKK(st~i)                k_IKKintermetiation` |
| 9 | TNFR1 activation and signal transduction cascade | One-way | `IKK(st~i)                ->  IKK(st~ii)               k_4` |
| 10 | TNFR1 activation and signal transduction cascade | One-way | `IKK(st~ii)               ->  IKK(st~n)                k_4` |
| 11 | IkB, A20 and TNF gene expression | One-way | `NFkB(loc~n,bin) + GA20(st~0)        ->  NFkB(loc~n,bin) + GA20(st~1)       q_1` |
| 12 | IkB, A20 and TNF gene expression | One-way | `NFkB(loc~n,bin) + GIkBa(st~0)       ->  NFkB(loc~n,bin) + GIkBa(st~1)      q_1` |
| 13 | IkB, A20 and TNF gene expression | One-way | `IkBa(loc~n,pho~0,bin) + GA20(st~1)  ->  IkBa(loc~n,pho~0,bin)+ GA20(st~0)  q_2` |
| 14 | IkB, A20 and TNF gene expression | One-way | `IkBa(loc~n,pho~0,bin) + GIkBa(st~1) ->  IkBa(loc~n,pho~0,bin)+ GIkBa(st~0) q_2` |
| 15 | IkB, A20 and TNF gene expression | One-way | `NFkB(loc~n,bin) + GTNF(st~0)        ->  NFkB(loc~n,bin) + GTNF(st~1)       q_1t` |
| 16 | IkB, A20 and TNF gene expression | One-way | `IkBa(loc~n,pho~0,bin) + GTNF(st~1)  ->  IkBa(loc~n,pho~0,bin)+ GTNF(st~0)  q_2t` |
| 17 | IkB, A20 and TNF gene expression | One-way | `GTNF(st~1)  ->  GTNF(st~0)                q_2tt` |
| 18 | IkB, A20 and TNF gene expression | One-way | `GTNF(st~1)  ->  GTNF(st~1)  + TNF_mRNA()   lambda` |
| 19 | IkB, A20 and TNF gene expression | One-way | `GA20(st~1)  ->  GA20(st~1)  + A20_mRNA()   c_1` |
| 20 | IkB, A20 and TNF gene expression | One-way | `GIkBa(st~1) ->  GIkBa(st~1) + IkBa_mRNA()  c_1` |
| 21 | IkB, A20 and TNF gene expression | One-way | `A20_mRNA()   ->  Trash()                             c_3` |
| 22 | IkB, A20 and TNF gene expression | One-way | `IkBa_mRNA()  ->  Trash()                             c_3` |
| 23 | IkB, A20 and TNF gene expression | One-way | `A20_mRNA()   ->  A20_mRNA()  + A20()                 c_4` |
| 24 | IkB, A20 and TNF gene expression | One-way | `IkBa_mRNA()  ->  IkBa_mRNA() + IkBa(loc~c,pho~0,bin) c_4` |
| 25 | IkB, A20 and TNF gene expression | One-way | `TNF_mRNA()   ->  Trash()                             c_3t` |
| 26 | IkB, A20 and TNF gene expression | One-way | `TNF_mRNA()   ->  TNF_mRNA()  + TNF(loc~i)            c_4t` |
| 27 | Protein interactions | One-way | `NFkB(loc~c,bin) + IkBa(loc~c,pho~0,bin)  ->  NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)  a_1` |
| 28 | Protein interactions | One-way | `NFkB(loc~n,bin) + IkBa(loc~n,pho~0,bin)  ->  NFkB(loc~n,bin!0).IkBa(loc~n,pho~0,bin!0)  k_NFkBIkB` |
| 29 | Protein interactions | One-way | `IkBa(loc~c,pho~0,bin)+ IKK(st~a)   ->  IkBa(loc~c,pho~p,bin)+ IKK(st~a)   a_2` |
| 30 | Protein interactions | One-way | `NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)+IKK(st~a)->  NFkB(loc~c,bin!0).IkBa(loc~c,pho~p,bin!0)+IKK(st~a)  a_3` |
| 31 | Protein interactions | One-way | `A20()                   ->  Trash()           c_5` |
| 32 | Protein interactions | One-way | `IkBa(loc~c,pho~p,bin)   ->  Trash()           t_p` |
| 33 | Protein interactions | One-way | `NFkB(loc~c,bin!0).IkBa(loc~c,pho~p,bin!0)  ->  NFkB(loc~c,bin)   t_p` |
| 34 | Protein interactions | One-way | `IkBa(loc~c,pho~0,bin)   ->  Trash()           c_5a` |
| 35 | Protein interactions | One-way | `TNF(loc~i)              ->  Trash()           k_TNFdeg` |
| 36 | Protein interactions | One-way | `NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)  ->  NFkB(loc~c,bin)   c_6a` |
| 37 | Transport | One-way | `NFkB(loc~c,bin)        ->  NFkB(loc~n,bin)        i_1` |
| 38 | Transport | One-way | `IkBa(loc~c,pho~0,bin)  ->  IkBa(loc~n,pho~0,bin)  i_1a` |
| 39 | Transport | One-way | `IkBa(loc~n,pho~0,bin)  ->  IkBa(loc~c,pho~0,bin)  e_1a` |
| 40 | Transport | One-way | `NFkB(loc~n,bin!0).IkBa(loc~n,pho~0,bin!0)  ->  NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)  e_2a` |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Species  TNFR_a          TNFR(st~a)`
- `Species  TNFR_i          TNFR(st~i)`
- `Species  A20             A20()`
- `Species  IKKK_a          IKKK(st~a)`
- `Species  IKK_a           IKK(st~a)`
- `Species  NFkB_nuc        NFkB(loc~n,bin)`
- `Species  NFkB_cyt        NFkB(loc~c,bin)`
- `Species  NFkB_IkBa_p_cyt NFkB(loc~c,bin!0).IkBa(loc~c,pho~p,bin!0)`
- `Species  NFkB_IkBa_u_cyt NFkB(loc~c,bin!0).IkBa(loc~c,pho~0,bin!0)`
- `Species  NFkB_IkBa_u_nuc NFkB(loc~n,bin!0).IkBa(loc~n,pho~0,bin!0)`
- `Species  TNF_ext         TNF(loc~e)`
- `Species  TNF_int         TNF(loc~i)`
- `Species  IKK_n           IKK(st~n)`
- `Species  IKK_i           IKK(st~i)`
- `Species  IkBa_p_cyt      IkBa(loc~c,pho~p,bin)`
- `Species  IkBa_u_cyt      IkBa(loc~c,pho~0,bin)`
- `Species  IkBa_u_nuc      IkBa(loc~n,pho~0,bin)`
- `Species  tA20            A20_mRNA()`
- `Species  tIkB            IkBa_mRNA()`
- `Species  tTNF            TNF_mRNA()`
- `Species  gA20_a          GA20(st~1)`
- `Species  gA20_i          GA20(st~0)`
- `Species  gTNF_a          GTNF(st~1)`
- `Species  gTNF_i          GTNF(st~0)`
- `Species  gIkBa_a         GIkBa(st~1)`
- `Species  gIkBa_i         GIkBa(st~0)`
- `Molecules  IKK_tot_   IKK()`
- `Molecules  NFkB_tot_  NFkB()`
- `Molecules  IKKK_tot_  IKKK()`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>1});`
- `simulate_ode({suffix=>"ode1",t_end=>300*3600,n_steps=>1800});`
- `setConcentration("TNF(loc~e)",1);`
- `simulate_ode({suffix=>"ode2",t_end=>10*3600,n_steps=>600});`

## 9. Technical caveats and ambiguities

Localization is encoded by internal `loc` states rather than BNGL compartments. The two-stage ODE workflow first equilibrates without extracellular TNF and then applies one TNF unit. Observable pattern counts can include multiple embeddings.
