# Detailed Model Explanation: Hat 2016 DNA-damage and p53 decision network

## 1. Model identity and scope

`Hat_2016` models how DNA double-strand breaks drive ATM–p53 feedback, repair/arrest control, and Bax–caspase apoptosis. Sources: `Published/Hat2016/Hat_2016.bngl` and `Published/Hat2016/metadata.yaml`.

## 2. BNGL block inventory

The file contains 125 active parameter declarations, 30 molecule types, 15 initial-species declarations, 5 functions, 58 concrete reaction rules, 58 observable declarations, and 2 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

The namespace is organized around irradiation/damage (`IR_*`, `DNA_DSB_*`, `h1`–`h3`, `rep`), p53/ATM feedback (`p*`, `d*`, `M*`), transcription and translation (`q*`, `s*`, `t*`, `g*`), cell-cycle control, and apoptosis. The exhaustive list below keeps one declaration per bullet so values and comments can be scanned without a code block.

- `STOCHASTIC_GENES 0  # Pick 0 or 1 to have deterministic or stochastic gene`
- `IR_duration                 10*60  # time of exposure to IR [s]`
- `IR_Gy                           2  # dose of IR [Gy] (note: may be changed in`
- `DNA_DSB_per_1Gy                10  # number of DNA DSBs per 1 Gy of IR (~10)`
- `DNA_DSB_due_to_IR  DNA_DSB_per_1Gy*IR_Gy/IR_duration # expected DNA damaging rate`
- `is_IR_switched_on               0  # subject to change in simulation protocol`
- `has_DNA_DSB_repair              1`
- `can_Caspase_make_DNA_DSB        1`
- `_total                10^5`
- `SIAH1_total          _total  # total amount of SIAH1`
- `ATM_total            _total  # total amount of ATM`
- `AKT_total            _total  # total amount of AKT     [BMC Syst.Biol.2013: 2e5]`
- `PIP_total            _total  # total amount of PIP2 and PIP2`
- `Rb_total           3*_total  # total amount of Rb`
- `E2F1_total         2*_total  # total amount of E2F1`
- `BclXL_total          _total  # total amount of Bcl-xL  [BMC Syst.Biol.2013: 1e5]`
- `Bad_total          6*10^4    # total amount of Bad     [BMC Syst.Biol.2013:: gate AND: 6e4, gate OR: 2e5]`
- `Fourteen_3_3_total 2*10^5    # total amount of 14-3-3  [BMC Syst.Biol.2013: 2e5]`
- `rep       has_DNA_DSB_repair*10^-3 # DNA DSBs repair rate`
- `DNA_DSB_Repair_Cplx_total    20    # number of DNA repair complexes`
- `h1        is_IR_switched_on*10^-6  # rate of DNA DSB induction by IR`
- `h2 can_Caspase_make_DNA_DSB*10^-13 # rate of DNA DSB induction by active Caspase`
- `DNA_DSB_max                 10^6   # max number of DNA DSBs`
- `a1       3*10^-10  # activation of proCaspases by Bax  [BMC Syst.Biol.2013: 2e-10]`
- `a2         10^-12  # Caspases autoact'n                [BMC Syst.Biol.2013: 1e-12]`
- `_q0        10^-5`
- `q0_pten    _q0     # PTEN gene act'n, spontaneous`
- `q0_wip1    _q0     # Wip1 gene act'n, spontaneous`
- `q0_mdm2 10*_q0     # Mdm2 gene act'n, spontaneous`
- `q0_bax     _q0     # Bax  gene act'n, spontaneous`
- `q0_p21     _q0     # p21  gene act'n, spontaneous`
- `_q1      3*10^-13`
- `q1_pten    _q1     # PTEN gene act'n induced by p53_killer, 0 for PTEN non-inducible cells (MCF7)`
- `q1_mdm2    _q1     # Mdm2 gene act'n induced by p53_arrester`
- `q1_wip1    _q1     # Wip1 gene act'n induced by p53_arrester`
- `q1_p21     _q1     # p21  gene act'n induced by p53_arrester`
- `q1_bax     _q1     # Bax  gene act'n induced by p53_killer`
- `n_pten_alleles  2  #  :`
- `n_mdm2_alleles  2  #  \|`
- `n_wip1_alleles  2  #   > these parameters influence only STOCHASTIC gene expression`
- `n_p21_alleles   2  #  \|`
- `n_bax_alleles   2  #  ;`
- `q2      3*10^-3    # for genes of Mdm2, Wip1, p21, PTEN, Bax`
- `_s          0.1`
- `s1         _s      # Wip1 mRNA synthesis`
- `s2     0.3*_s      # PTEN mRNA synthesis`
- `s3         _s      # Mdm2 mRNA synthesis`
- `s4     0.3*_s      # Bax  mRNA synthesis  [BMC Syst.Biol.2013: 0.03]`
- `s5         _s      # p21  mRNA synthesis`
- `_t          0.1`
- `t1         _t      # Wip1 transl'n`
- `t2         _t      # PTEN transl'n`
- `t3         _t      # Mdm2 transl'n`
- `t4         _t      # Bax  transl'n  [BMC Syst.Biol.2013: 0.2]`
- `t5         _t      # p21  transl'n`
- `_ss        30`
- `s6      10*_ss     # p53 sythesis`
- `s7         _ss     # proCaspases sythesis  [BMC Syst.Biol.2013: 20]`
- `s8         _ss     # HIPK2 synthesis`
- `s9         _ss     # Cyclin E synthesis, induced by E2F1`
- `s10    0.1*_ss     # Cyclin E synthesis, spontaneous`
- `p1      3*10^-4    # ATM   p'ylation due to the presence of IR-induced DNA DSBs`
- `p2        10^-8    # SIAH1 p'ylation by ATM_p`
- `p3      3*10^-8    # p53   p'ylation by ATM_p at S15_S20`
- `p4        10^-10   # p53_arrester p'ylation by HIPK2 at S46`
- `p5        10^-8    # Mdm2_cyt p'ylation`
- `p6        10^-8    # Mdm2_nuc_S166p_S186p p'ylation by ATM_p at S395`
- `p7      3*10^-9    # Bad   p'ylation by AKT_p  [BMC Syst.Biol.2013: 3e-10]`
- `p8      3*10^-9    # PIP3  p'ylation by PI3K`
- `p9      3*10^-6    # Rb    p'ylation by Cyclin E`
- `p10        p9      # Rb    p'ylation by Cyclin E in Rb--E2F complex`
- `p11        p4      # p53   p'ylation by HIPK2 at S46`
- `p12       10^-9    # AKT   p'ylation at PIP3`
- `d1        10^-8    # ATM_p   dep'ylation by Wip1`
- `d2      3*10^-5    # SIAH1_p dep'ylation`
- `d3        10^-4    # p53_arrester dep'ylation, spontaneous`
- `d4        10^-10   # p53_killer   dep'ylation of S46p by Wip1`
- `d5        10^-4    # Mdm2_cyt_S166p_S186p       dep'ylation of S166p_186p, spontaneous`
- `d6        10^-10   # Mdm2_nuc_S166p_S186p_S395p dep'ylation of S395p by Wip1`
- `d7      3*10^-7    # PIP3    dep'ylation to PIP2 by PTEN`
- `d8        10^-4    # AKT_p   dep'ylation, spontaneous`
- `d9      3*10^-5    # Bad_p   dep'ylation, spontaneous   [BMC Syst.Biol.2013: 3e-5]`
- `d10        d3      # p53_killer dep'ylation of S15p_S20p, spontaneous`
- `d11        d4      # p53_S46 dep'ylation of S46p by Wip1`
- `d12       10^4     # Rb      dep'ylation`
- `_b         10^-5`
- `b1       3*_b      #   Bax & BclXL  [BMC Syst.Biol.2013: 3e-5]`
- `b2     300*_b      #   Bad & BclXL  [BMC Syst.Biol.2013: 3e-3]`
- `b3     300*_b      # Bad_p & 14-3-3 [BMC Syst.Biol.2013: 3e-3]`
- `b4         _b      #    Rb & E2F1`
- `b5         _b      #   p21 & Cyclin E`
- `_u         10^-3`
- `u1         _u      #   Bax--BclXL  complex  [BMC Syst.Biol.2013: 1e-4]`
- `u2         _u      #   Bad--BclXL  complex  [BMC Syst.Biol.2013: 1e-4]`
- `u3         _u      # Bad_p--14-3-3 complex  [BMC Syst.Biol.2013: 1e-4]`
- `u5     0.1*_u      #    Rb--E2F1   complex`
- `u6     0.1*_u      #   p21--Cyclin E complex`
- `i1        10^-3    # Mdm2_cyt_S166p_S186p nuclear import`
- `_g         10^-4`
- `g1       3*_g      # mRNA_Wip1 deg'n`
- `g2       3*_g      # mRNA_PTEN deg'n`
- `g3       3*_g      # mRNA_Mdm2 deg'n`
- `g4       3*_g      # mRNA_Bax  deg'n  [BMC Syst.Biol.2013: 1e-3]`
- `g5       3*_g      # mRNA_p21  deg'n`
- `_gg        10^-13`
- `g6     0.3*_g      # PTEN degr'n (delay of a positive feedback loop)`
- `g7         _gg     # Mdm2_nuc_2p- and SIAH1_u-driven HIPK2 degr'n`
- `g8       3*_g      # Wip1 (time lag to ATM_p dep'ylation)`
- `g9         _g      # Bax (delay of apoptosis)  [BMC Syst.Biol.2013: 1e-4]`
- `g10    0.1*_g      # p53 deg'n, spontaneous`
- `g101   0.1*_g      # p53 non-killer,non-S46 deg'n, spontaneous`
- `g11    100*_gg     # p53          deg'n induced by Mdm2_nuc_S166p_S186p`
- `g12        _gg     # p53_arrester deg'n induced by Mdm2_nuc_S166p_S186p`
- `g13        _gg     # p53_killer   deg'n induced by Mdm2_nuc_S166p_S186p`
- `g14        _g      # Mdm2_cyt_dep'ylated deg'n`
- `g15    0.3*_g      # Mdm2_{{cyt,nuc}_S166p_S186p,nuc_166p_186p_395p} deg'n, spontaneous`
- `g16        _g      # Mdm2_nuc_S166p_S186p_*395p* deg'n`
- `g17      3*_g      # proCaspase  [BMC Syst.Biol.2013: 2e-4]`
- `g18      3*_g      # Caspase`
- `g19      3*_g      # p21`
- `g20        _g      # Cyclin E`
- `h          2       # Hill coefficient (universal)`
- `M1         5       # Michaelis--Menten const. in ATM  p'ylation due to IR`
- `M2        10^5     # Michaelis--Menten const. in Rb dep'ylation at S567`
- `M3      2*10^5     # Michaelis--Menten const. in E2F1-induced Cyclin E synthesis`

Functions are executable rate/readout logic:

- `gene_Wip1_activity() (q0_wip1 + q1_wip1*p53_arr^h )/(q2 + q0_wip1 + q1_wip1*p53_arr^h )`
- `gene_Mdm2_activity() (q0_mdm2 + q1_mdm2*p53_arr^h )/(q2 + q0_mdm2 + q1_mdm2*p53_arr^h )`
- `gene_p21_activity()  (q0_p21  + q1_p21 *p53_arr^h )/(q2 + q0_p21  + q1_p21 *p53_arr^h )`
- `gene_PTEN_activity() (q0_pten + q1_pten*p53_kill^h)/(q2 + q0_pten + q1_pten*p53_kill^h)`
- `gene_Bax_activity()  (q0_bax  + q1_bax *p53_kill^h)/(q2 + q0_bax  + q1_bax *p53_kill^h)`

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `DNA_DSB` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `DNA_DSB()` |
| `ATM` | 1 | `S1981` | `S1981: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `ATM(S1981~0~P)` |
| `SIAH1` | 1 | `S19` | `S19: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `SIAH1(S19~0~P)` |
| `HIPK2` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `HIPK2()` |
| `Wip1` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `Wip1()` |
| `gene_Wip1` | 1 | `tf` | `tf: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `gene_Wip1(tf~0~1)` |
| `mRNA_Wip1` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `mRNA_Wip1()` |
| `p53` | 2 | `S15_S20, S46` | `S15_S20: 0,PP; S46: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `p53(S15_S20~0~PP,S46~0~P)` |
| `Mdm2` | 3 | `S166_S186, S395, loc` | `S166_S186: 0,PP; S395: 0,P; loc: Nuc,Cyt` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Mdm2(S166_S186~0~PP,S395~0~P,loc~Nuc~Cyt)` |
| `gene_Mdm2` | 1 | `tf` | `tf: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `gene_Mdm2(tf~0~1)` |
| `mRNA_Mdm2` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `mRNA_Mdm2()` |
| `PTEN` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `PTEN()` |
| `gene_PTEN` | 1 | `tf` | `tf: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `gene_PTEN(tf~0~1)` |
| `mRNA_PTEN` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `mRNA_PTEN()` |
| `PI3K` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `PI3K()` |
| `AKT` | 1 | `T308` | `T308: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `AKT(T308~0~P)` |
| `PtdIns` | 1 | `s` | `s: PP,PPP` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `PtdIns(s~PP~PPP)` |
| `p21` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `p21(b)` |
| `mRNA_p21` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `mRNA_p21()` |
| `gene_p21` | 1 | `tf` | `tf: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `gene_p21(tf~0~1)` |
| `Cyclin_E` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Cyclin_E(b)` |
| `Rb` | 2 | `S567, b` | `S567: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Rb(S567~0~P,b)` |
| `E2F1` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `E2F1(b)` |
| `Bax` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Bax(b)` |
| `gene_Bax` | 1 | `tf` | `tf: 0,1` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `gene_Bax(tf~0~1)` |
| `mRNA_Bax` | 0 | `none` | `none` | None | Nullary species/marker. | Declaration: `mRNA_Bax()` |
| `BclXL` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `BclXL(b)` |
| `Bad` | 2 | `S75_S99, b` | `S75_S99: 0,PP` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Bad(S75_S99~0~PP,b)` |
| `Fourteen_3_3` | 1 | `b` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Fourteen_3_3(b)` |
| `Caspase` | 1 | `csp` | `csp: Pro,Act` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Caspase(csp~Pro~Act)` |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are declared. Initial patterns and amounts are exhaustive below:

- `SIAH1(S19~0)                         SIAH1_total # (constant pool)`
- `ATM(S1981~0)                         ATM_total   # (constant pool)`
- `PI3K()                              _total       # (constant)`
- `PtdIns(s~PP)                         PIP_total   # (constant pool)`
- `AKT(T308~0)                          AKT_total   # (constant pool)`
- `Rb(S567~0,b)                         Rb_total    # (constant pool)`
- `E2F1(b)                              E2F1_total  # (constant pool)`
- `BclXL(b)                             BclXL_total # (constant pool)`
- `Bad(S75_S99~0,b)                     Bad_total   # (constant pool, logic gate-type dependent)`
- `Fourteen_3_3(b)               Fourteen_3_3_total # (constant pool)`
- `gene_Wip1(tf~0)                      n_wip1_alleles`
- `gene_Mdm2(tf~0)                      n_mdm2_alleles`
- `gene_p21(tf~0)                       n_p21_alleles`
- `gene_PTEN(tf~0)                      n_pten_alleles`
- `gene_Bax(tf~0)                       n_bax_alleles`

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules are ordered as gene switching, DNA-damage production/repair, ATM and p53 feedback, arrest/PTEN control, and mitochondrial apoptosis. The table states the molecular prerequisite and net edit without reproducing the full BNGL pattern.

| # | Direction | Required molecules/sites | Net bond, state, or species edit | Rate/expression | Functional interpretation |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | `gene_Wip1` (`tf`) | `gene_Wip1.tf` 0→1 | q0_wip1+q1_wip1*p53_arr^h,  q2 | Stochastic gene-state switching controlled by the appropriate p53 transcriptional program; this `q0_wip1+q1_wip1*p53_arr^h,  q2` variant requires `gene_Wip1` (`tf`) and `gene_Wip1.tf` 0→1. |
| 2 | Reversible | `gene_Mdm2` (`tf`) | `gene_Mdm2.tf` 0→1 | q0_mdm2+q1_mdm2*p53_arr^h,  q2 | Stochastic gene-state switching controlled by the appropriate p53 transcriptional program; this `q0_mdm2+q1_mdm2*p53_arr^h,  q2` variant requires `gene_Mdm2` (`tf`) and `gene_Mdm2.tf` 0→1. |
| 3 | Reversible | `gene_p21` (`tf`) | `gene_p21.tf` 0→1 | q0_p21 +q1_p21 *p53_arr^h,  q2 | Stochastic gene-state switching controlled by the appropriate p53 transcriptional program; this `q0_p21 +q1_p21 *p53_arr^h,  q2` variant requires `gene_p21` (`tf`) and `gene_p21.tf` 0→1. |
| 4 | Reversible | `gene_PTEN` (`tf`) | `gene_PTEN.tf` 0→1 | q0_pten+q1_pten*p53_kill^h, q2 | Stochastic gene-state switching controlled by the appropriate p53 transcriptional program; this `q0_pten+q1_pten*p53_kill^h, q2` variant requires `gene_PTEN` (`tf`) and `gene_PTEN.tf` 0→1. |
| 5 | Reversible | `gene_Bax` (`tf`) | `gene_Bax.tf` 0→1 | q0_bax +q1_bax *p53_kill^h, q2 | Stochastic gene-state switching controlled by the appropriate p53 transcriptional program; this `q0_bax +q1_bax *p53_kill^h, q2` variant requires `gene_Bax` (`tf`) and `gene_Bax.tf` 0→1. |
| 6 | One-way | Source `0`; current `DNA_DSB_tot` below `DNA_DSB_max` | Creates one `DNA_DSB` | `h1*DNA_DSB_due_to_IR*(DNA_DSB_max-DNA_DSB_tot)` | Ionizing radiation generates breaks only while irradiation is active and the modeled damage ceiling has not been reached. |
| 7 | One-way | Source `0`; active caspase signal; unsaturated damage capacity | Creates one `DNA_DSB` | `h2*Caspase_act*(DNA_DSB_max-DNA_DSB_tot)` | Active caspases feed additional damage back into the p53 network. |
| 8 | One-way | Existing `DNA_DSB` and the current repair-complex load | Removes one `DNA_DSB` to sink `0` | `rep/(DNA_DSB_tot+DNA_DSB_Repair_Cplx_total)` | Repairs damage with a load-dependent per-break rate. |
| 9 | Reversible | `ATM` (`S1981`) | `ATM.S1981` 0→P | , d1*Wip1_tot | ATM: activation by DNA DSBs, deactivation by Wip1. |
| 10 | Reversible | `SIAH1` (`S19`) | `SIAH1.S19` 0→P | p2*ATM_p, d2 | SIAH: phosphorylation by active ATM, dephosphorylation. |
| 11 | Reversible | `HIPK2` | creates the product species from source `0`; creates `HIPK2` | ^2 | HIPK2: synthesis, Mdm2- and SIAH1-mediated degradation. |
| 12 | Reversible | `mRNA_Wip1`; `gene_Wip1_activity` | creates the product species from source `0`; creates `gene_Wip1_activity`; creates `mRNA_Wip1` | *g1 | Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `*g1` variant requires `mRNA_Wip1`; `gene_Wip1_activity` and creates the product species from source `0`; creates `gene_Wip1_activity`; creates `mRNA_Wip1`. |
| 13 | Reversible | `mRNA_Wip1` | creates the product species from source `0`; creates `mRNA_Wip1` | STOCHASTIC_GENES *s1*gene_Wip1_on/n_wip1_alleles, STOCHASTIC_GENES *g1 | Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `STOCHASTIC_GENES *s1*gene_Wip1_on/n_wip1_alleles, STOCHASTIC_GENES *g1` variant requires `mRNA_Wip1` and creates the product species from source `0`; creates `mRNA_Wip1`. |
| 14 | Reversible | `Wip1` | creates the product species from source `0`; creates `Wip1` | t1*mRNA_Wip1, g8 | Wip1 translation. |
| 15 | One-way | `p53` (`S15_S20`, `S46`) | creates the product species from source `0`; creates `p53` | s6 | p53 synthesis. |
| 16 | One-way | `p53` | removes the reactant to sink `0`; removes `p53` | g101 | 53 degradations; this `g101` variant requires `p53` and removes the reactant to sink `0`; removes `p53`. |
| 17 | One-way | `p53` (`S15_S20`, `S46`) | removes the reactant to sink `0`; removes `p53` | g11*Mdm2_nuc_2p^2 | 53 degradations; this `g11*Mdm2_nuc_2p^2` variant requires `p53` (`S15_S20`, `S46`) and removes the reactant to sink `0`; removes `p53`. |
| 18 | One-way | `p53` (`S15_S20`, `S46`) | removes the reactant to sink `0`; removes `p53` | g12*Mdm2_nuc_2p^2 | 53 degradations; this `g12*Mdm2_nuc_2p^2` variant requires `p53` (`S15_S20`, `S46`) and removes the reactant to sink `0`; removes `p53`. |
| 19 | One-way | `p53` (`S15_S20`, `S46`) | removes the reactant to sink `0`; removes `p53` | g12*Mdm2_nuc_2p^2 | 53 degradations; this `g12*Mdm2_nuc_2p^2` variant requires `p53` (`S15_S20`, `S46`) and removes the reactant to sink `0`; removes `p53`. |
| 20 | One-way | `p53` (`S15_S20`, `S46`) | removes the reactant to sink `0`; removes `p53` | g12*Mdm2_nuc_2p^2 | 53 degradations; this `g12*Mdm2_nuc_2p^2` variant requires `p53` (`S15_S20`, `S46`) and removes the reactant to sink `0`; removes `p53`. |
| 21 | Reversible | `p53` (`S15_S20`) | `p53.S15_S20` 0→PP | p3*ATM_p, d3 | p53 modifications at arrester sites: p'ylation by activee ATM, dep'ylation. |
| 22 | Reversible | `p53` (`S46`) | `p53.S46` 0→P | p4*HIPK2_tot, d4*Wip1_tot | p53 modification at the killer site: p'ylation by HIPK2, dep'ylation by Wip1. |
| 23 | Reversible | `mRNA_Mdm2`; `gene_Mdm2_activity` | creates the product species from source `0`; creates `gene_Mdm2_activity`; creates `mRNA_Mdm2` | *g3 | Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `*g3` variant requires `mRNA_Mdm2`; `gene_Mdm2_activity` and creates the product species from source `0`; creates `gene_Mdm2_activity`; creates `mRNA_Mdm2`. |
| 24 | Reversible | `mRNA_Mdm2` | creates the product species from source `0`; creates `mRNA_Mdm2` | STOCHASTIC_GENES *s3*gene_Mdm2_on/n_mdm2_alleles, STOCHASTIC_GENES *g3 | Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `STOCHASTIC_GENES *s3*gene_Mdm2_on/n_mdm2_alleles, STOCHASTIC_GENES *g3` variant requires `mRNA_Mdm2` and creates the product species from source `0`; creates `mRNA_Mdm2`. |
| 25 | One-way | `Mdm2` (`S166_S186`, `S395`, `loc`) | creates the product species from source `0`; creates `Mdm2` | t3*mRNA_Mdm2 | Mdm2 translation. |
| 26 | One-way | `Mdm2` (`S166_S186`) | removes the reactant to sink `0`; removes `Mdm2` | g14 | Mdm2 degradations; this `g14` variant requires `Mdm2` (`S166_S186`) and removes the reactant to sink `0`; removes `Mdm2`. |
| 27 | One-way | `Mdm2` (`S166_S186`) | removes the reactant to sink `0`; removes `Mdm2` | g15 | Mdm2 degradations; this `g15` variant requires `Mdm2` (`S166_S186`) and removes the reactant to sink `0`; removes `Mdm2`. |
| 28 | One-way | `Mdm2` (`S166_S186`, `S395`, `loc`) | removes the reactant to sink `0`; removes `Mdm2` | g16 | Mdm2 degradations; this `g16` variant requires `Mdm2` (`S166_S186`, `S395`, `loc`) and removes the reactant to sink `0`; removes `Mdm2`. |
| 29 | Reversible | `Mdm2` (`S166_S186`, `S395`, `loc`) | `Mdm2.S166_S186` 0→PP | p5*AKT_p, d5 | Mdm2 modifications at 2xSer site: p'ylation by AKT, dep'ylation. |
| 30 | One-way | `Mdm2` (`S166_S186`, `S395`, `loc`) | `Mdm2.loc` Cyt→Nuc | i1 | Mdm2_cyt_2p import into the nucleus. |
| 31 | Reversible | `Mdm2` (`S166_S186`, `S395`, `loc`) | `Mdm2.S395` 0→P | p6*ATM_p, d6*Wip1_tot | Mdm2_nuc_2p modification at S395: p'ylation by ATM_p, dep'ylation by Wip1. |
| 32 | Reversible | `mRNA_PTEN`; `gene_PTEN_activity` | creates the product species from source `0`; creates `gene_PTEN_activity`; creates `mRNA_PTEN` | *g2 | PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `*g2` variant requires `mRNA_PTEN`; `gene_PTEN_activity` and creates the product species from source `0`; creates `gene_PTEN_activity`; creates `mRNA_PTEN`. |
| 33 | Reversible | `mRNA_PTEN` | creates the product species from source `0`; creates `mRNA_PTEN` | STOCHASTIC_GENES *s2*gene_PTEN_on/n_pten_alleles, STOCHASTIC_GENES *g2 | PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `STOCHASTIC_GENES *s2*gene_PTEN_on/n_pten_alleles, STOCHASTIC_GENES *g2` variant requires `mRNA_PTEN` and creates the product species from source `0`; creates `mRNA_PTEN`. |
| 34 | Reversible | `PTEN` | creates the product species from source `0`; creates `PTEN` | t2*mRNA_PTEN, g6 | PTEN translation, protein degradation. |
| 35 | Reversible | `PtdIns` (`s`) | `PtdIns.s` PP→PPP | p8*PI3K_tot,  d7*PTEN_tot | PIP2--PIP3 interconversions. |
| 36 | Reversible | `AKT` (`T308`) | `AKT.T308` 0→P | p12*PIP3, d8 | AKT activation (by PDK1, implicit), deactivation. |
| 37 | Reversible | `mRNA_p21`; `gene_p21_activity` | creates the product species from source `0`; creates `gene_p21_activity`; creates `mRNA_p21` | *g5 | p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `*g5` variant requires `mRNA_p21`; `gene_p21_activity` and creates the product species from source `0`; creates `gene_p21_activity`; creates `mRNA_p21`. |
| 38 | Reversible | `mRNA_p21` | creates the product species from source `0`; creates `mRNA_p21` | STOCHASTIC_GENES *s5*gene_p21_on/n_p21_alleles, STOCHASTIC_GENES *g5 | p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `STOCHASTIC_GENES *s5*gene_p21_on/n_p21_alleles, STOCHASTIC_GENES *g5` variant requires `mRNA_p21` and creates the product species from source `0`; creates `mRNA_p21`. |
| 39 | Reversible | `p21` (`b`) | creates the product species from source `0`; creates `p21` | t5*mRNA_p21, g19 | p21 translation, protein degradation. |
| 40 | Reversible | `Cyclin_E` (`b`) | creates the product species from source `0`; creates `Cyclin_E` | ,  g20 | cyclin E synthesis: spontaneous and E2F1-induced; degradation. |
| 41 | Reversible | `p21` (`b`); `Cyclin_E` (`b`) | forms the explicitly site-matched bond(s) | b5, u6 | p21 and cyclin E binding, unbinding. |
| 42 | One-way | `p21` (`b`); `Cyclin_E` (`b`) | releases the explicitly site-matched bond(s); removes the reactant to sink `0`; removes `Cyclin_E`; removes `p21` | g20 | p21--cyclin E complex degradation. |
| 43 | Reversible | Rb (`S567`) and the free Cyclin E readout | `Rb.S567` switches `0↔P` | forward `p9*CyclinE_free`; reverse `d12/(M2+Rb_p_free)` | Cyclin E phosphorylates Rb, while the reverse flux is reduced as free phosphorylated Rb accumulates. |
| 44 | Reversible | `Rb` (`S567`, `b`); `E2F1` (`b`) | forms the explicitly site-matched bond(s) | b4, u5 | retinoblastoma (dep'ylated) and E2F1 binding, unbinding. |
| 45 | One-way | `Rb` (`S567`, `b`); `E2F1` (`b`) | `Rb.S567` 0→P; releases the explicitly site-matched bond(s) | p10*CyclinE_free | retinolblastoma--E2F1 complex disociaiton upon retinoblastoma p'ylation by cyclin E. |
| 46 | Reversible | `mRNA_Bax`; `gene_Bax_activity` | creates the product species from source `0`; creates `gene_Bax_activity`; creates `mRNA_Bax` | *g4 | Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `*g4` variant requires `mRNA_Bax`; `gene_Bax_activity` and creates the product species from source `0`; creates `gene_Bax_activity`; creates `mRNA_Bax`. |
| 47 | Reversible | `mRNA_Bax` | creates the product species from source `0`; creates `mRNA_Bax` | STOCHASTIC_GENES* s4*gene_Bax_on/n_bax_alleles, STOCHASTIC_GENES *g4 | Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective); this `STOCHASTIC_GENES* s4*gene_Bax_on/n_bax_alleles, STOCHASTIC_GENES *g4` variant requires `mRNA_Bax` and creates the product species from source `0`; creates `mRNA_Bax`. |
| 48 | Reversible | `Bax` (`b`) | creates the product species from source `0`; creates `Bax` | t4*mRNA_Bax, g9 | Bax translation, protein degradatoin. |
| 49 | Reversible | `Bax` (`b`); `BclXL` (`b`) | forms the explicitly site-matched bond(s) | b1, u1 | Bax--BclXL binding, unbinding. |
| 50 | One-way | `Bax` (`b`); `BclXL` (`b`) | releases the explicitly site-matched bond(s); removes `Bax` | g16 | Bax (complexed) degradation. |
| 51 | Reversible | `BclXL` (`b`); `Bad` (`S75_S99`, `b`) | forms the explicitly site-matched bond(s) | b2, u2 | BclXL and dep'ylated Bad binding, unbinding. |
| 52 | One-way | `BclXL` (`b`); `Bad` (`S75_S99`, `b`) | `Bad.S75_S99` 0→PP; releases the explicitly site-matched bond(s) | p7*AKT_p | BclXL unbinding from Bad upon Bad p'ylation by AKT. |
| 53 | Reversible | `Bad` (`S75_S99`, `b`); `Bad` (`b`, `S75_S99`) | `Bad.S75_S99` 0→PP | p7*AKT_p, d9 | Bad p'ylation by AKT, dep'ylation. |
| 54 | Reversible | `Bad` (`S75_S99`, `b`); `Fourteen_3_3` (`b`); `Bad` (`b`, `S75_S99`) | forms the explicitly site-matched bond(s) | b3, u3 | Bad (p'ylated) and 14-3-3 binding, unbinding. |
| 55 | One-way | `Bad` (`S75_S99`, `b`); `Fourteen_3_3` (`b`) | `Bad.S75_S99` PP→0; releases the explicitly site-matched bond(s) | d9 | unbinding of Bad from 14-3-3 upon Bad dep'ylation. |
| 56 | One-way | `Caspase` (`csp`) | creates the product species from source `0`; creates `Caspase` | s7 | procaspase synthesis. |
| 57 | One-way | `Caspase` | removes the reactant to sink `0`; removes `Caspase` | g17 | caspase and procaspase degradation. |
| 58 | One-way | `Caspase` (`csp`) | `Caspase.csp` Pro→Act | a1*Bax_free+a2*Caspase_act^2 | caspase activation by Bax and by other caspases. |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Molecules DNA_DSB_tot  DNA_DSB()`
- `Molecules ATM_tot      ATM()`
- `Molecules ATM_p        ATM(S1981~P)`
- `Molecules gene_Wip1_on gene_Wip1(tf~1)`
- `Molecules mRNA_Wip1    mRNA_Wip1()`
- `Molecules Wip1_tot     Wip1()`
- `Molecules SIAH1_tot    SIAH1()`
- `Molecules SIAH1_u      SIAH1(S19~0)`
- `Molecules SIAH1_p      SIAH1(S19~P)`
- `Molecules HIPK2_tot    HIPK2()`
- `Molecules p53_tot      p53()`
- `Molecules p53_0p       p53(S15_S20~0,S46~0)`
- `Molecules p53_arr      p53(S15_S20~PP,S46~0)`
- `Molecules p53_kill     p53(S15_S20~PP,S46~P)`
- `Molecules gene_Mdm2_on gene_Mdm2(tf~1)`
- `Molecules mRNA_Mdm2    mRNA_Mdm2()`
- `Molecules Mdm2_tot     Mdm2()`
- `Molecules Mdm2_cyt_0p  Mdm2(S166_S186~0,S395~0,loc~Cyt)`
- `Molecules Mdm2_cyt_2p  Mdm2(S166_S186~PP,S395~0,loc~Cyt)`
- `Molecules Mdm2_nuc_2p  Mdm2(S166_S186~PP,S395~0,loc~Nuc)`
- `Molecules Mdm2_nuc_3p  Mdm2(S166_S186~PP,S395~P,loc~Nuc)`
- `Molecules PI3K_tot     PI3K()`
- `Molecules gene_PTEN_on gene_PTEN(tf~1)`
- `Molecules mRNA_PTEN    mRNA_PTEN()`
- `Molecules PTEN_tot     PTEN()`
- `Molecules PIP2         PtdIns(s~PP)`
- `Molecules PIP3         PtdIns(s~PPP)`
- `Molecules AKT_p        AKT(T308~P)`
- `Molecules gene_p21_on       gene_p21(tf~1)`
- `Molecules mRNA_p21          mRNA_p21()`
- `Molecules p21_tot           p21()`
- `Molecules p21_free          p21(b)`
- `Molecules CyclinE_tot       Cyclin_E()`
- `Molecules CyclinE_free      Cyclin_E(b)`
- `Molecules p21_CyclinE_cplx  p21(b!4).Cyclin_E(b!4)`
- `Molecules Rb_tot            Rb()`
- `Molecules Rb_p_free         Rb(S567~P,b)`
- `Molecules E2F1_tot          E2F1()`
- `Molecules E2F1_free         E2F1(b)`
- `Molecules RB_u_E2F1_cplx    Rb(S567~0,b!4).E2F1(b!4)`
- `Molecules gene_Bax_on       gene_Bax(tf~1)`
- `Molecules mRNA_Bax          mRNA_Bax()`
- `Molecules Bax_tot           Bax()`
- `Molecules Bax_free          Bax(b)`
- `Molecules BclXL_tot         BclXL()`
- `Molecules BclXL_free        BclXL(b)`
- `Molecules Bax_BclXL_cplx    Bax(b!1).BclXL(b!1)`
- `Molecules Bad_tot           Bad()`
- `Molecules Bad_free          Bad(b)`
- `Molecules Bad_u_free        Bad(S75_S99~0,b)`
- `Molecules Bad_p_free        Bad(S75_S99~PP,b)`
- `Molecules BclXL_Bad_u_cplx  BclXL(b!2).Bad(S75_S99~0,b!2)`
- `Molecules Bad_p_14_3_3_cplx Bad(S75_S99~PP,b!3).Fourteen_3_3(b!3)`
- `Molecules Fourteen_3_3_tot  Fourteen_3_3()`
- `Molecules Fourteen_3_3_free Fourteen_3_3(b)`
- `Molecules Caspase_tot       Caspase()`
- `Molecules Caspase_pro       Caspase(csp~Pro)`
- `Molecules Caspase_act       Caspase(csp~Act)`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>1});`
- `writeSBML();`

## 9. Technical caveats and ambiguities

The metadata label “Nuclear transport” does not capture the BNGL’s DNA-damage/p53/apoptosis scope. Several observables and functions combine patterns algebraically, so molecule-pattern multiplicity matters. The large rule set is a compact mechanistic network rather than a list of independently validated elementary reactions.
