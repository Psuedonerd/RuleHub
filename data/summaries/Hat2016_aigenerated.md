# Model Explanation: Hat 2016

## 1. One-sentence summary

This model represents p53-system feedbacks in DNA-damage response and cell-fate decision-making, including p53 regulators, transcriptional outputs, and damage/repair modules.

## 2. Biological meaning

This model represents p53-system feedbacks in DNA-damage response and cell-fate decision-making, including p53 regulators, transcriptional outputs, and damage/repair modules. The local model comments and metadata give this context: This BioNetGen model code features the article: "Feedbacks, Bifurcations, and Cell Fate Decision-Making in the p53 System" by  Hat B, Kochanczyk M, Bogdal MN, and Lipniacki T (PLOS Computational Biology 2016). In order to learn how to execute this model, please read the accompanying ReadMe.txt file. -----------------------====[ simulation type ]====----------------------- # expression, respectively, *and* select a corresponding simulation method at the bottom of this file (i.e., method=>"ssa" or method=>"ode"). Please note that stochastic equilibration can take a lot of CPU time. -------------------------====[ stimulation ]====------------------------- # the actions section) -----------------------====[ on/off switches ]====----------------------- #. The explanation below is therefore based on the local BNGL model file `Published/Hat2016/Hat_2016.bngl` and metadata file `Published/Hat2016/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `DNA_DSB`: DNA_DSB. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `ATM`: ATM. It has state sites `S1981~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `SIAH1`: SIAH1. It has state sites `S19~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `HIPK2`: HIPK2. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Wip1`: Wip1. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `gene_Wip1`: gene_Wip1. It has state sites `tf~0~1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mRNA_Wip1`: mRNA_Wip1. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `p53`: p53 tumor suppressor. It has state sites `S15_S20~0~PP`, `S46~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Mdm2`: Mdm2 regulator. It has state sites `S166_S186~0~PP`, `S395~0~P`, `loc~Nuc~Cyt`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `gene_Mdm2`: gene_Mdm2. It has state sites `tf~0~1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mRNA_Mdm2`: mRNA_Mdm2. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PTEN`: PTEN. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `gene_PTEN`: gene_PTEN. It has state sites `tf~0~1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mRNA_PTEN`: mRNA_PTEN. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI3K`: PI3K. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `AKT`: AKT. It has state sites `T308~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PtdIns`: PtdIns. It has state sites `s~PP~PPP`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `p21`: p21. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mRNA_p21`: mRNA_p21. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `gene_p21`: gene_p21. It has state sites `tf~0~1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Cyclin_E`: Cyclin_E. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Rb`: Rb. It has binding/interaction sites `b` and regulated state sites `S567~0~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `E2F1`: E2F1. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Bax`: Bax. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `gene_Bax`: gene_Bax. It has state sites `tf~0~1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mRNA_Bax`: mRNA_Bax. It has no explicit sites in the declaration. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `BclXL`: BclXL. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Bad`: Bad. It has binding/interaction sites `b` and regulated state sites `S75_S99~0~PP`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Fourteen_3_3`: Fourteen_3_3. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Caspase`: Caspase. It has state sites `csp~Pro~Act`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `SIAH1(S19~0)                         SIAH1_total`
- `ATM(S1981~0)                         ATM_total`
- `PI3K()                              _total`
- `PtdIns(s~PP)                         PIP_total`
- `AKT(T308~0)                          AKT_total`
- `Rb(S567~0,b)                         Rb_total`
- `E2F1(b)                              E2F1_total`
- `BclXL(b)                             BclXL_total`
- `Bad(S75_S99~0,b)                     Bad_total`
- `Fourteen_3_3(b)               Fourteen_3_3_total`
- `gene_Wip1(tf~0)                      n_wip1_alleles`
- `gene_Mdm2(tf~0)                      n_mdm2_alleles`
- `gene_p21(tf~0)                       n_p21_alleles`
- `gene_PTEN(tf~0)                      n_pten_alleles`
- `gene_Bax(tf~0)                       n_bax_alleles`

Important parameters include:

- `STOCHASTIC_GENES 0`
- `IR_duration                 10*60`
- `IR_Gy                           2`
- `DNA_DSB_per_1Gy                10`
- `DNA_DSB_due_to_IR  DNA_DSB_per_1Gy*IR_Gy/IR_duration`
- `is_IR_switched_on               0`
- `has_DNA_DSB_repair              1`
- `can_Caspase_make_DNA_DSB        1`
- `_total                10^5`
- `SIAH1_total          _total`
- `ATM_total            _total`
- `AKT_total            _total`
- `PIP_total            _total`
- `Rb_total           3*_total`
- `E2F1_total         2*_total`
- `BclXL_total          _total`
- `Bad_total          6*10^4`
- `Fourteen_3_3_total 2*10^5`
- `rep       has_DNA_DSB_repair*10^-3`
- `DNA_DSB_Repair_Cplx_total    20`
- `h1        is_IR_switched_on*10^-6`
- `h2 can_Caspase_make_DNA_DSB*10^-13`
- `DNA_DSB_max                 10^6`
- `a1       3*10^-10`
- `a2         10^-12`

Functions and simulation/action commands:

- `gene_Wip1_activity() (q0_wip1 + q1_wip1*p53_arr^h )/(q2 + q0_wip1 + q1_wip1*p53_arr^h )`
- `gene_Mdm2_activity() (q0_mdm2 + q1_mdm2*p53_arr^h )/(q2 + q0_mdm2 + q1_mdm2*p53_arr^h )`
- `gene_p21_activity()  (q0_p21  + q1_p21 *p53_arr^h )/(q2 + q0_p21  + q1_p21 *p53_arr^h )`
- `gene_PTEN_activity() (q0_pten + q1_pten*p53_kill^h)/(q2 + q0_pten + q1_pten*p53_kill^h)`
- `gene_Bax_activity()  (q0_bax  + q1_bax *p53_kill^h)/(q2 + q0_bax  + q1_bax *p53_kill^h)`
- `generate_network({overwrite=>1});`
- `writeSBML();`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **These 5 rules are used only in stochastic simulations:**: State change or catalytic conversion. The nearby model comment says: “These 5 rules are used only in stochastic simulations:”. The rule involves `gene_Wip1` and produces `gene_Wip1`. The encoded molecular change is `gene_Wip1` site `tf` changes from `0` to `1`; site `tf` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `q0_wip1+q1_wip1*p53_arr^h,  q2`.
- **These 5 rules are used only in stochastic simulations:**: State change or catalytic conversion. The nearby model comment says: “These 5 rules are used only in stochastic simulations:”. The rule involves `gene_Mdm2` and produces `gene_Mdm2`. The encoded molecular change is `gene_Mdm2` site `tf` changes from `0` to `1`; site `tf` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `q0_mdm2+q1_mdm2*p53_arr^h,  q2`.
- **These 5 rules are used only in stochastic simulations:**: State change or catalytic conversion. The nearby model comment says: “These 5 rules are used only in stochastic simulations:”. The rule involves `gene_p21` and produces `gene_p21`. The encoded molecular change is `gene_p21` site `tf` changes from `0` to `1`; site `tf` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `*p53_arr^h,  q2`.
- **These 5 rules are used only in stochastic simulations:**: State change or catalytic conversion. The nearby model comment says: “These 5 rules are used only in stochastic simulations:”. The rule involves `gene_PTEN` and produces `gene_PTEN`. The encoded molecular change is `gene_PTEN` site `tf` changes from `0` to `1`; site `tf` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `q0_pten+q1_pten*p53_kill^h,  q2`.
- **These 5 rules are used only in stochastic simulations:**: State change or catalytic conversion. The nearby model comment says: “These 5 rules are used only in stochastic simulations:”. The rule involves `gene_Bax` and produces `gene_Bax`. The encoded molecular change is `gene_Bax` site `tf` changes from `0` to `1`; site `tf` changes from `0` to `1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `*p53_kill^h,  q2`.
- **DNA damage due to ionizing radiation**: Production, removal, or biochemical conversion. The nearby model comment says: “DNA damage due to ionizing radiation”. The rule involves the listed reactant pattern and produces `DNA_DSB`. Rate parameter(s): `DNA_DSB_tot)`.
- **DNA damage introduced by active Caspases**: Production, removal, or biochemical conversion. The nearby model comment says: “DNA damage introduced by active Caspases”. The rule involves the listed reactant pattern and produces `DNA_DSB`. Rate parameter(s): `DNA_DSB_tot)`.
- **DNA damage repair**: Production, removal, or biochemical conversion. The nearby model comment says: “DNA damage repair”. The rule involves `DNA_DSB` and produces the listed product pattern. Rate parameter(s): `DNA_DSB_Repair_Cplx_total)`.
- **ATM: activation by DNA DSBs, deactivation by Wip1**: State change or catalytic conversion. The nearby model comment says: “ATM: activation by DNA DSBs, deactivation by Wip1”. The rule involves `ATM` and produces `ATM`. The encoded molecular change is `ATM` site `S1981` changes from `0` to `P`; site `S1981` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `DNA_DSB_tot^h),  d1*Wip1_tot`.
- **SIAH: phosphorylation by active ATM, dephosphorylation**: State change or catalytic conversion. The nearby model comment says: “SIAH: phosphorylation by active ATM, dephosphorylation”. The rule involves `SIAH1` and produces `SIAH1`. The encoded molecular change is `SIAH1` site `S19` changes from `0` to `P`; site `S19` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p2*ATM_p,  d2`.
- **HIPK2: synthesis, Mdm2- and SIAH1-mediated degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “HIPK2: synthesis, Mdm2- and SIAH1-mediated degradation”. The rule involves the listed reactant pattern and produces `HIPK2`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `+ Mdm2_nuc_2p)^2`.
- **Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Wip1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `(1-STOCHASTIC_GENES)*s1*gene_Wip1_activity(),  (1-STOCHASTIC_GENES)*g1`.
- **Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Wip1 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Wip1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `STOCHASTIC_GENES *g1`.
- **Wip1 translation**: Production, removal, or biochemical conversion. The nearby model comment says: “Wip1 translation”. The rule involves the listed reactant pattern and produces `Wip1`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `t1*mRNA_Wip1,  g8`.
- **p53 synthesis**: Production, removal, or biochemical conversion. The nearby model comment says: “p53 synthesis”. The rule involves the listed reactant pattern and produces `p53`. Rate parameter(s): `s6`.
- **53 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “53 degradations:”. The rule involves `p53` and produces the listed product pattern. Rate parameter(s): `g101`.
- **53 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “53 degradations:”. The rule involves `p53` and produces the listed product pattern. Rate parameter(s): `g11*Mdm2_nuc_2p^2`.
- **53 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “53 degradations:”. The rule involves `p53` and produces the listed product pattern. Rate parameter(s): `g12*Mdm2_nuc_2p^2`.
- **53 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “53 degradations:”. The rule involves `p53` and produces the listed product pattern. Rate parameter(s): `g12*Mdm2_nuc_2p^2`.
- **53 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “53 degradations:”. The rule involves `p53` and produces the listed product pattern. Rate parameter(s): `g12*Mdm2_nuc_2p^2`.
- **p53 modifications at arrester sites: p'ylation by activee ATM, dep'ylation**: State change or catalytic conversion. The nearby model comment says: “p53 modifications at arrester sites: p'ylation by activee ATM, dep'ylation”. The rule involves `p53` and produces `p53`. The encoded molecular change is `p53` site `S15_S20` changes from `0` to `PP`; site `S15_S20` changes from `0` to `PP`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p3*ATM_p,  d3`.
- **p53 modification at the killer site: p'ylation by HIPK2, dep'ylation by Wip1**: State change or catalytic conversion. The nearby model comment says: “p53 modification at the killer site: p'ylation by HIPK2, dep'ylation by Wip1”. The rule involves `p53` and produces `p53`. The encoded molecular change is `p53` site `S46` changes from `0` to `P`; site `S46` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p4*HIPK2_tot,  d4*Wip1_tot`.
- **Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Mdm2`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `(1-STOCHASTIC_GENES)*s3*gene_Mdm2_activity(),  (1-STOCHASTIC_GENES)*g3`.
- **Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Mdm2`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `STOCHASTIC_GENES *g3`.
- **Mdm2 translation**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 translation”. The rule involves the listed reactant pattern and produces `Mdm2`. Rate parameter(s): `t3*mRNA_Mdm2`.
- **Mdm2 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 degradations:”. The rule involves `Mdm2` and produces the listed product pattern. Rate parameter(s): `g14`.
- **Mdm2 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 degradations:”. The rule involves `Mdm2` and produces the listed product pattern. Rate parameter(s): `g15`.
- **Mdm2 degradations:**: Production, removal, or biochemical conversion. The nearby model comment says: “Mdm2 degradations:”. The rule involves `Mdm2` and produces the listed product pattern. Rate parameter(s): `g16`.
- **Mdm2 modifications at 2xSer site: p'ylation by AKT, dep'ylation**: State change or catalytic conversion. The nearby model comment says: “Mdm2 modifications at 2xSer site: p'ylation by AKT, dep'ylation”. The rule involves `Mdm2` and produces `Mdm2`. The encoded molecular change is `Mdm2` site `S166_S186` changes from `0` to `PP`; site `S166_S186` changes from `0` to `PP`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p5*AKT_p,  d5`.
- **Mdm2_cyt_2p import into the nucleus**: State change or catalytic conversion. The nearby model comment says: “Mdm2_cyt_2p import into the nucleus”. The rule involves `Mdm2` and produces `Mdm2`. The encoded molecular change is site `loc` changes from `Cyt` to `Nuc`. Rate parameter(s): `i1`.
- **Mdm2_nuc_2p modification at S395: p'ylation by ATM_p, dep'ylation by Wip1**: State change or catalytic conversion. The nearby model comment says: “Mdm2_nuc_2p modification at S395: p'ylation by ATM_p, dep'ylation by Wip1”. The rule involves `Mdm2` and produces `Mdm2`. The encoded molecular change is site `S395` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p6*ATM_p,  d6*Wip1_tot`.
- **PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_PTEN`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `(1-STOCHASTIC_GENES)*s2*gene_PTEN_activity(),  (1-STOCHASTIC_GENES)*g2`.
- **PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “PTEN gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_PTEN`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `STOCHASTIC_GENES *g2`.
- **PTEN translation, protein degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “PTEN translation, protein degradation”. The rule involves the listed reactant pattern and produces `PTEN`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `t2*mRNA_PTEN,  g6`.
- **PIP2--PIP3 interconversions**: State change or catalytic conversion. The nearby model comment says: “PIP2--PIP3 interconversions”. The rule involves `PtdIns` and produces `PtdIns`. The encoded molecular change is `PtdIns` site `s` changes from `PP` to `PPP`; site `s` changes from `PP` to `PPP`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p8*PI3K_tot,  d7*PTEN_tot`.
- **AKT activation (by PDK1, implicit), deactivation**: State change or catalytic conversion. The nearby model comment says: “AKT activation (by PDK1, implicit), deactivation”. The rule involves `AKT` and produces `AKT`. The encoded molecular change is `AKT` site `T308` changes from `0` to `P`; site `T308` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p12*PIP3,  d8`.
- **p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_p21`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `(1-STOCHASTIC_GENES)*s5*gene_p21_activity(),  (1-STOCHASTIC_GENES)*g5`.
- **p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “p21 gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_p21`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `STOCHASTIC_GENES *g5`.
- **p21 translation, protein degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “p21 translation, protein degradation”. The rule involves the listed reactant pattern and produces `p21`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `t5*mRNA_p21,  g19`.
- **cyclin E synthesis: spontaneous and E2F1-induced; degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “cyclin E synthesis: spontaneous and E2F1-induced; degradation”. The rule involves the listed reactant pattern and produces `Cyclin_E`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `E2F1_free^h),  g20`.
- **p21 and cyclin E binding, unbinding**: Reversible binding/release. The nearby model comment says: “p21 and cyclin E binding, unbinding”. The rule involves `Cyclin_E`, `p21` and produces `Cyclin_E`, `p21`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `b5,  u6`.
- **p21--cyclin E complex degradation**: Unbinding or disassembly. The nearby model comment says: “p21--cyclin E complex degradation”. The rule involves `Cyclin_E`, `p21` and produces the listed product pattern. Loss of matching `!` labels means a complex separates. Rate parameter(s): `g20`.
- **retinoblastoma p'ylation by cyclin E**: State change or catalytic conversion. The nearby model comment says: “retinoblastoma p'ylation by cyclin E”. The rule involves `Rb` and produces `Rb`. The encoded molecular change is `Rb` site `S567` changes from `0` to `P`; site `S567` changes from `0` to `P`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `+ Rb_p_free)`.
- **retinoblastoma (dep'ylated) and E2F1 binding, unbinding**: Reversible binding/release. The nearby model comment says: “retinoblastoma (dep'ylated) and E2F1 binding, unbinding”. The rule involves `E2F1`, `Rb` and produces `E2F1`, `Rb`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `b4,  u5`.
- **retinolblastoma--E2F1 complex disociaiton upon retinoblastoma p'ylation by cyclin E**: Unbinding or disassembly. The nearby model comment says: “retinolblastoma--E2F1 complex disociaiton upon retinoblastoma p'ylation by cyclin E”. The rule involves `E2F1`, `Rb` and produces `E2F1`, `Rb`. The encoded molecular change is `Rb` site `S567` changes from `0` to `P`; site `S567` changes from `0` to `P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `p10*CyclinE_free`.
- **Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Bax`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `(1-STOCHASTIC_GENES)*s4*gene_Bax_activity(),  (1-STOCHASTIC_GENES)*g4`.
- **Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective):**: Production, removal, or biochemical conversion. The nearby model comment says: “Bax gene transcription & degradation (only 1 of the following bidir. rules should be effective):”. The rule involves the listed reactant pattern and produces `mRNA_Bax`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `STOCHASTIC_GENES *g4`.
- **Bax translation, protein degradatoin**: Production, removal, or biochemical conversion. The nearby model comment says: “Bax translation, protein degradatoin”. The rule involves the listed reactant pattern and produces `Bax`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `t4*mRNA_Bax,  g9`.
- **Bax--BclXL binding, unbinding**: Reversible binding/release. The nearby model comment says: “Bax--BclXL binding, unbinding”. The rule involves `Bax`, `BclXL` and produces `Bax`, `BclXL`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `b1,  u1`.
- **Bax (complexed) degradation**: Unbinding or disassembly. The nearby model comment says: “Bax (complexed) degradation”. The rule involves `Bax`, `BclXL` and produces `BclXL`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `g16`.
- **BclXL and dep'ylated Bad binding, unbinding**: Reversible binding/release. The nearby model comment says: “BclXL and dep'ylated Bad binding, unbinding”. The rule involves `Bad`, `BclXL` and produces `Bad`, `BclXL`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `b2,  u2`.
- **BclXL unbinding from Bad upon Bad p'ylation by AKT**: Unbinding or disassembly. The nearby model comment says: “BclXL unbinding from Bad upon Bad p'ylation by AKT”. The rule involves `Bad`, `BclXL` and produces `Bad`, `BclXL`. The encoded molecular change is `Bad` site `S75_S99` changes from `0` to `PP`; site `S75_S99` changes from `0` to `PP`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `p7*AKT_p`.
- **Bad p'ylation by AKT, dep'ylation**: State change or catalytic conversion. The nearby model comment says: “Bad p'ylation by AKT, dep'ylation”. The rule involves `Bad` and produces `Bad`. The encoded molecular change is `Bad` site `S75_S99` changes from `0` to `PP`; site `S75_S99` changes from `0` to `PP`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `p7*AKT_p,  d9`.
- **Bad (p'ylated) and 14-3-3 binding, unbinding**: Reversible binding/release. The nearby model comment says: “Bad (p'ylated) and 14-3-3 binding, unbinding”. The rule involves `Bad`, `Fourteen_3_3` and produces `Bad`, `Fourteen_3_3`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `b3,  u3`.
- **unbinding of Bad from 14-3-3 upon Bad dep'ylation**: Unbinding or disassembly. The nearby model comment says: “unbinding of Bad from 14-3-3 upon Bad dep'ylation”. The rule involves `Bad`, `Fourteen_3_3` and produces `Bad`, `Fourteen_3_3`. The encoded molecular change is `Bad` site `S75_S99` changes from `PP` to `0`; site `S75_S99` changes from `PP` to `0`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `d9`.
- **procaspase synthesis**: Production, removal, or biochemical conversion. The nearby model comment says: “procaspase synthesis”. The rule involves the listed reactant pattern and produces `Caspase`. Rate parameter(s): `s7`.
- **caspase and procaspase degradation**: Production, removal, or biochemical conversion. The nearby model comment says: “caspase and procaspase degradation”. The rule involves `Caspase` and produces the listed product pattern. Rate parameter(s): `g17`.
- **caspase activation by Bax and by other caspases**: State change or catalytic conversion. The nearby model comment says: “caspase activation by Bax and by other caspases”. The rule involves `Caspase` and produces `Caspase`. The encoded molecular change is `Caspase` site `csp` changes from `Pro` to `Act`; site `csp` changes from `Pro` to `Act`. Rate parameter(s): `a1*Bax_free+a2*Caspase_act^2`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `DNA_DSB_tot` (Molecules) tracks patterns containing DNA_DSB. Pattern: `DNA_DSB()`.
- `ATM_tot` (Molecules) tracks patterns containing ATM. Pattern: `ATM()`.
- `ATM_p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `ATM(S1981~P)`.
- `gene_Wip1_on` (Molecules) tracks patterns containing gene_Wip1. Pattern: `gene_Wip1(tf~1)`.
- `mRNA_Wip1` (Molecules) tracks patterns containing mRNA_Wip1. Pattern: `mRNA_Wip1()`.
- `Wip1_tot` (Molecules) tracks patterns containing Wip1. Pattern: `Wip1()`.
- `SIAH1_tot` (Molecules) tracks patterns containing SIAH1. Pattern: `SIAH1()`.
- `SIAH1_u` (Molecules) tracks patterns containing SIAH1. Pattern: `SIAH1(S19~0)`.
- `SIAH1_p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `SIAH1(S19~P)`.
- `HIPK2_tot` (Molecules) tracks patterns containing HIPK2. Pattern: `HIPK2()`.
- `p53_tot` (Molecules) tracks patterns containing p53. Pattern: `p53()`.
- `p53_0p` (Molecules) tracks patterns containing p53. Pattern: `p53(S15_S20~0,S46~0)`.
- `p53_arr` (Molecules) tracks phosphorylated/modified molecules. Pattern: `p53(S15_S20~PP,S46~0)`.
- `p53_kill` (Molecules) tracks phosphorylated/modified molecules. Pattern: `p53(S15_S20~PP,S46~P)`.
- `gene_Mdm2_on` (Molecules) tracks patterns containing gene_Mdm2. Pattern: `gene_Mdm2(tf~1)`.
- `mRNA_Mdm2` (Molecules) tracks patterns containing mRNA_Mdm2. Pattern: `mRNA_Mdm2()`.
- `Mdm2_tot` (Molecules) tracks patterns containing Mdm2. Pattern: `Mdm2()`.
- `Mdm2_cyt_0p` (Molecules) tracks patterns containing Mdm2. Pattern: `Mdm2(S166_S186~0,S395~0,loc~Cyt)`.
- `Mdm2_cyt_2p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Mdm2(S166_S186~PP,S395~0,loc~Cyt)`.
- `Mdm2_nuc_2p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Mdm2(S166_S186~PP,S395~0,loc~Nuc)`.
- `Mdm2_nuc_3p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Mdm2(S166_S186~PP,S395~P,loc~Nuc)`.
- `PI3K_tot` (Molecules) tracks patterns containing PI3K. Pattern: `PI3K()`.
- `gene_PTEN_on` (Molecules) tracks patterns containing gene_PTEN. Pattern: `gene_PTEN(tf~1)`.
- `mRNA_PTEN` (Molecules) tracks patterns containing mRNA_PTEN. Pattern: `mRNA_PTEN()`.
- `PTEN_tot` (Molecules) tracks patterns containing PTEN. Pattern: `PTEN()`.
- `PIP2` (Molecules) tracks phosphorylated/modified molecules. Pattern: `PtdIns(s~PP)`.
- `PIP3` (Molecules) tracks phosphorylated/modified molecules. Pattern: `PtdIns(s~PPP)`.
- `AKT_p` (Molecules) tracks phosphorylated/modified molecules. Pattern: `AKT(T308~P)`.
- `gene_p21_on` (Molecules) tracks patterns containing gene_p21. Pattern: `gene_p21(tf~1)`.
- `mRNA_p21` (Molecules) tracks patterns containing mRNA_p21. Pattern: `mRNA_p21()`.
- `p21_tot` (Molecules) tracks patterns containing p21. Pattern: `p21()`.
- `p21_free` (Molecules) tracks patterns containing p21. Pattern: `p21(b)`.
- `CyclinE_tot` (Molecules) tracks patterns containing Cyclin_E. Pattern: `Cyclin_E()`.
- `CyclinE_free` (Molecules) tracks patterns containing Cyclin_E. Pattern: `Cyclin_E(b)`.
- `p21_CyclinE_cplx` (Molecules) tracks bound complexes. Pattern: `p21(b!4).Cyclin_E(b!4)`.
- `Rb_tot` (Molecules) tracks patterns containing Rb. Pattern: `Rb()`.
- `Rb_p_free` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Rb(S567~P,b)`.
- `E2F1_tot` (Molecules) tracks patterns containing E2F1. Pattern: `E2F1()`.
- `E2F1_free` (Molecules) tracks patterns containing E2F1. Pattern: `E2F1(b)`.
- `RB_u_E2F1_cplx` (Molecules) tracks bound complexes. Pattern: `Rb(S567~0,b!4).E2F1(b!4)`.
- `gene_Bax_on` (Molecules) tracks patterns containing gene_Bax. Pattern: `gene_Bax(tf~1)`.
- `mRNA_Bax` (Molecules) tracks patterns containing mRNA_Bax. Pattern: `mRNA_Bax()`.
- `Bax_tot` (Molecules) tracks patterns containing Bax. Pattern: `Bax()`.
- `Bax_free` (Molecules) tracks patterns containing Bax. Pattern: `Bax(b)`.
- `BclXL_tot` (Molecules) tracks patterns containing BclXL. Pattern: `BclXL()`.
- `BclXL_free` (Molecules) tracks patterns containing BclXL. Pattern: `BclXL(b)`.
- `Bax_BclXL_cplx` (Molecules) tracks bound complexes. Pattern: `Bax(b!1).BclXL(b!1)`.
- `Bad_tot` (Molecules) tracks patterns containing Bad. Pattern: `Bad()`.
- `Bad_free` (Molecules) tracks patterns containing Bad. Pattern: `Bad(b)`.
- `Bad_u_free` (Molecules) tracks patterns containing Bad. Pattern: `Bad(S75_S99~0,b)`.
- `Bad_p_free` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Bad(S75_S99~PP,b)`.
- `BclXL_Bad_u_cplx` (Molecules) tracks bound complexes. Pattern: `BclXL(b!2).Bad(S75_S99~0,b!2)`.
- `Bad_p_14_3_3_cplx` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `Bad(S75_S99~PP,b!3).Fourteen_3_3(b!3)`.
- `Fourteen_3_3_tot` (Molecules) tracks patterns containing Fourteen_3_3. Pattern: `Fourteen_3_3()`.
- `Fourteen_3_3_free` (Molecules) tracks patterns containing Fourteen_3_3. Pattern: `Fourteen_3_3(b)`.
- `Caspase_tot` (Molecules) tracks patterns containing Caspase. Pattern: `Caspase()`.
- `Caspase_pro` (Molecules) tracks phosphorylated/modified molecules. Pattern: `Caspase(csp~Pro)`.
- `Caspase_act` (Molecules) tracks patterns containing Caspase. Pattern: `Caspase(csp~Act)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Hat_2016`
- Title/name: `Hat 2016`
- Category: `regulation`
- Tags: `['published', 'hat', '2016', 'dna_dsb', 'atm', 'siah1', 'hipk2', 'wip1', 'gene_wip1', 'mrna_wip1', 'p53']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/cell-regulation/Hat_2016.bngl`
- Local BNGL file used: `Published/Hat2016/Hat_2016.bngl`
- Local YAML file used: `Published/Hat2016/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode', 'ssa']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
