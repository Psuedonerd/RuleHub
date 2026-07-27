# Detailed Model Explanation: Pekalski 2013 autocrine TNF–NF-κB model

## 1. Model identity and scope

`Pekalski_2013` models how autocrine tumor necrosis factor (TNF) signaling produces NF-κB pulses controlled by IκBα and A20 feedback. Sources: `Published/Pekalski2013/Pekalski_2013.bngl` and `Published/Pekalski2013/metadata.yaml`.

## 2. BNGL block inventory

The file contains 42 active parameter declarations, 14 molecule types, 29 initial-species declarations, 4 functions, 40 concrete reaction rules, 29 observable declarations, and 4 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

The namespace separates initial pools (`R`, `K_N`, `K_NN`, gene and transcript totals), receptor/IKK-cascade kinetics, NF-κB–IκB transport and binding, transcriptional feedback, TNF production/secretion, and degradation. The exhaustive list retains one declaration per bullet so each value remains easy to locate.

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

**Rule-family orientation.** Rules progress from TNF receptor and IKK-cascade activation through NF-κB/IκB trafficking, feedback-gene expression, and TNF secretion. Localization is represented by internal `loc` states, not compartments.

| # | Direction | Required molecules/sites | Net bond, state, or species edit | Rate/expression | Functional interpretation |
| ---: | --- | --- | --- | --- | --- |
| 1 | One-way | `TNF` (`loc`); `Trash` | routes the reactant to `Trash`; removes `TNF` | c_deg | Extracellular TNF is cleared, limiting persistence of the autocrine stimulus. |
| 2 | One-way | `TNFR` (`st`); `TNF` (`loc`) | `TNFR.st` i→a | k_b | Extracellular TNF catalytically activates TNFR; TNF is retained so one ligand can stimulate repeatedly. |
| 3 | One-way | `TNFR` (`st`); `TNF` (`loc`) | `TNFR.st` i→a | k_Ractivation | Internal TNF activates TNFR through the separate intracellular-feedback rate. |
| 4 | One-way | `TNFR` (`st`) | `TNFR.st` a→i | k_f | Active TNFR returns to its inactive state and terminates receptor-proximal signaling. |
| 5 | One-way | `IKKK` (`st`) | `IKKK.st` n→a | k_IKKKactivation | Basal upstream input activates IKKK, initiating the kinase relay. |
| 6 | One-way | `IKKK` (`st`) | `IKKK.st` a→n | k_i | Active IKKK relaxes to the neutral state, bounding each upstream pulse. |
| 7 | One-way | `IKK` (`st`) | `IKK.st` n→a | k_IKKactivation | IKKK-dependent input activates IKK, creating the form that targets IκBα. |
| 8 | One-way | `IKK` (`st`) | `IKK.st` a→i | k_IKKintermetiation | Active IKK enters the first inactive intermediate rather than returning directly to neutral. |
| 9 | One-way | `IKK` (`st`) | `IKK.st` i→ii | k_4 | IKK advances through the second refractory intermediate. |
| 10 | One-way | `IKK` (`st`) | `IKK.st` ii→n | k_4 | The refractory IKK cycle closes by returning the kinase to its neutral, activatable state. |
| 11 | One-way | `NFkB` (`loc`, `bin`); `GA20` (`st`) | `GA20.st` 0→1 | q_1 | Nuclear free NF-κB switches the A20 promoter on. |
| 12 | One-way | `NFkB` (`loc`, `bin`); `GIkBa` (`st`) | `GIkBa.st` 0→1 | q_1 | Nuclear free NF-κB switches the IκBα promoter on. |
| 13 | One-way | `IkBa` (`loc`, `pho`, `bin`); `GA20` (`st`) | `GA20.st` 1→0 | q_2 | Nuclear IκBα switches the A20 promoter off, implementing feedback termination. |
| 14 | One-way | `IkBa` (`loc`, `pho`, `bin`); `GIkBa` (`st`) | `GIkBa.st` 1→0 | q_2 | Nuclear IκBα switches its own promoter off, closing the IκBα negative-feedback loop. |
| 15 | One-way | `NFkB` (`loc`, `bin`); `GTNF` (`st`) | `GTNF.st` 0→1 | q_1t | Nuclear free NF-κB activates the TNF promoter and thereby the positive autocrine loop. |
| 16 | One-way | `IkBa` (`loc`, `pho`, `bin`); `GTNF` (`st`) | `GTNF.st` 1→0 | q_2t | Nuclear IκBα actively shuts the TNF promoter off. |
| 17 | One-way | `GTNF` (`st`) | `GTNF.st` 1→0 | q_2tt | The TNF promoter also turns off spontaneously, independently of IκBα. |
| 18 | One-way | `GTNF` (`st`); `TNF_mRNA` | creates `TNF_mRNA` | lambda | An active TNF promoter produces TNF mRNA without consuming the promoter state. |
| 19 | One-way | `GA20` (`st`); `A20_mRNA` | creates `A20_mRNA` | c_1 | An active A20 promoter produces A20 mRNA. |
| 20 | One-way | `GIkBa` (`st`); `IkBa_mRNA` | creates `IkBa_mRNA` | c_1 | An active IκBα promoter produces IκBα mRNA. |
| 21 | One-way | `A20_mRNA`; `Trash` | routes the reactant to `Trash`; removes `A20_mRNA` | c_3 | A20 mRNA is degraded, setting the lifetime of the delayed inhibitor transcript. |
| 22 | One-way | `IkBa_mRNA`; `Trash` | routes the reactant to `Trash`; removes `IkBa_mRNA` | c_3 | IκBα mRNA is degraded, setting the recovery timescale of the inhibitor loop. |
| 23 | One-way | `A20_mRNA`; `A20` | creates `A20` | c_4 | A20 mRNA produces A20 protein while the transcript is retained catalytically. |
| 24 | One-way | `IkBa_mRNA`; `IkBa` (`loc`, `pho`, `bin`) | creates `IkBa` | c_4 | IκBα mRNA produces unphosphorylated cytosolic IκBα with a free NF-κB-binding site. |
| 25 | One-way | `TNF_mRNA`; `Trash` | routes the reactant to `Trash`; removes `TNF_mRNA` | c_3t | TNF mRNA is degraded, limiting cytokine-production duration. |
| 26 | One-way | `TNF_mRNA`; `TNF` (`loc`) | creates `TNF` | c_4t | TNF mRNA produces intracellular TNF, which can activate receptor internally or be secreted. |
| 27 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`) | forms the explicitly site-matched bond(s) | a_1 | Nuclear NF-κB binds nuclear IκBα, initiating transcriptional shutoff. |
| 28 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`) | forms the explicitly site-matched bond(s) | k_NFkBIkB | Cytosolic NF-κB binds cytosolic IκBα, forming the sequestered inactive complex. |
| 29 | One-way | `IkBa` (`loc`, `pho`, `bin`); `IKK` (`st`) | `IkBa.pho` 0→p | a_2 | Active IKK phosphorylates free cytosolic IκBα and is carried through unchanged. |
| 30 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`); `IKK` (`st`) | `IkBa.pho` 0→p | a_3 | Active IKK phosphorylates IκBα while it is bound to NF-κB, priming inhibitor removal. |
| 31 | One-way | `A20`; `Trash` | routes the reactant to `Trash`; removes `A20` | c_5 | A20 protein turns over independently of its signaling targets. |
| 32 | One-way | `IkBa` (`loc`, `pho`, `bin`); `Trash` | routes the reactant to `Trash`; removes `IkBa` | t_p | Free phosphorylated IκBα is degraded rapidly. |
| 33 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`) | releases the explicitly site-matched bond(s); removes `IkBa` | t_p | Phosphorylated IκBα is removed from the NF-κB complex, releasing free cytosolic NF-κB. |
| 34 | One-way | `IkBa` (`loc`, `pho`, `bin`); `Trash` | routes the reactant to `Trash`; removes `IkBa` | c_5a | Unphosphorylated free IκBα undergoes basal degradation. |
| 35 | One-way | `TNF` (`loc`); `Trash` | routes the reactant to `Trash`; removes `TNF` | k_TNFdeg | Intracellular TNF is degraded before secretion or receptor activation. |
| 36 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`) | releases the explicitly site-matched bond(s); removes `IkBa` | c_6a | Unphosphorylated IκBα is removed from the complex, leaving cytosolic NF-κB free. |
| 37 | One-way | `NFkB` (`loc`, `bin`) | `NFkB.loc` c→n | i_1 | Free cytosolic NF-κB enters the nucleus to drive transcription. |
| 38 | One-way | `IkBa` (`loc`, `pho`, `bin`) | `IkBa.loc` c→n | i_1a | Free cytosolic IκBα enters the nucleus, where it can terminate promoter activity. |
| 39 | One-way | `IkBa` (`loc`, `pho`, `bin`) | `IkBa.loc` n→c | e_1a | Free nuclear IκBα is exported back to cytosol. |
| 40 | One-way | `NFkB` (`loc`, `bin`); `IkBa` (`loc`, `pho`, `bin`) | `NFkB.loc` n→c; `IkBa.loc` n→c | e_2a | The nuclear NF-κB–IκBα complex is exported as a unit, resetting both factors to cytosol. |

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
