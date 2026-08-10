# Published YAML Feature and Citation Audit

Audited 10 models and created 10 `*_metadata_aigenerated.yaml` files. Inserted 109 missing values; 24 items require review.

## LinPrion2019

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_functions: true` — four active definitions occur in `begin functions` at lines 84–87 of `Lin_Prion_2019.bngl`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action at line 130.
- Review insertion: `default_sim_command: ode` — the first active simulation at line 140 is `simulate(...)` with `method=>"ode"`.
- Citation year: `2019`.
- Citation reference: `Lin et al., 2019` — the `Lin_Prion_2019.bngl` header identifies Lin, Feng, and Hlavacek's *Scaling methods for accelerating kinetic Monte Carlo simulations of chemical reaction networks* as the 2019 work whose Figure 2(b) simulation is implemented by this model.
- Citation URL: [arXiv source](https://arxiv.org/abs/1903.08615) — the same BNGL header supplies this article-specific URL; **warning: PMID unresolved**; [PubMed search](https://pubmed.ncbi.nlm.nih.gov/?term=%22Scaling+methods+for+accelerating+kinetic+Monte+Carlo+simulations+of+chemical+reaction+networks%22).

## LinERK2019

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_functions: true` — six active scaled-species definitions occur in `begin functions` at lines 269–274 of `Lin_ERK_2019.bngl`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action at line 466.
- Review insertion: `default_sim_command: ode` — the first active simulation at line 476 is `simulate(...)` with `method=>"ode"`.
- Citation year: `2019`.
- Citation reference: `Lin et al., 2019` — the `Lin_ERK_2019.bngl` header identifies Lin, Feng, and Hlavacek's *Scaling methods for accelerating kinetic Monte Carlo simulations of chemical reaction networks* as the 2019 work whose Figure 2(a) simulation is implemented by this ERK model.
- Citation URL: [arXiv source](https://arxiv.org/abs/1903.08615) — the same BNGL header supplies this article-specific URL; **warning: PMID unresolved**; [PubMed search](https://pubmed.ncbi.nlm.nih.gov/?term=%22Scaling+methods+for+accelerating+kinetic+Monte+Carlo+simulations+of+chemical+reaction+networks%22).

## Blinov2006

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Citation year: `2006`.
- Citation reference: `Blinov et al., 2006` — BNGLViz lists `Blinov_2006.bngl` as “A model of initial events in EGFR signaling” and attributes that exact entry to Blinov et al. (2006).
- Citation PMID: `16233948` — taken directly from the PubMed link on the BNGLViz `Blinov_2006` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/16233948/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.

## Dushek2011

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_functions`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action at line 192 of `Dushek_2011.bngl`.
- Review insertion: `default_sim_command: ode` — the first active simulation is `simulate_ode(...)` at line 193.
- Citation year: `2011`.
- Citation reference: `Dushek et al., 2011` — BNGLViz pairs `Dushek_2011.bngl` with “A model of ultrasensitivity in multisite phosphorylation of membrane-anchored proteins,” matching the BNGL's 20-site phosphorylation substrate.
- Citation PMID: `21354391` — taken directly from the PubMed link on the BNGLViz `Dushek_2011` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/21354391/).

## Kocieniewski2012

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `uses_generate_network: true` → `false` — `Kocieniewski_2012.bngl` contains no active `generate_network(...)` action.
- Review change: removed `default_sim_command: ode` — the BNGL contains no active simulation action from which to establish a default method.
- Citation year: `2012`.
- Citation reference: `Kocieniewski et al., 2012` — BNGLViz pairs `Kocieniewski_2012.bngl` with “A model of the interplay of double phosphorylation and scaffolding in MAPK pathways,” matching the model's MAP3K/MAP2K/MAPK scaffold system.
- Citation PMID: `22123371` — taken directly from the PubMed link on the BNGLViz `Kocieniewski_2012` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/22123371/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.

## McMillan2021

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `uses_multiple_identical_sites: true` → `false` — the active molecule types `R(p,a)` and `T(1,2,3)` contain no repeated component name.
- Citation year: `2021`.
- Citation reference: `McMillan et al., 2021` — BNGLViz pairs `McMillan_2021.bngl` with “A model of disruption of TNF-TNFR1 signalling by small molecules,” matching the model's TNF (`T`) and receptor (`R`) system.
- Citation PMID: `33495441` — taken directly from the PubMed link on the BNGLViz `McMillan_2021` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/33495441/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.

## Massole2023

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `uses_generate_network: true` → `false` — `Massole_2023.bngl` contains no active `generate_network(...)` action.
- Review change: removed `default_sim_command: ode` — the BNGL contains no active simulation action from which to establish a default method.
- Citation year: `2023`.
- Citation reference: `Massole et al., 2023` — BNGLViz pairs `Massole_2023.bngl` with *Optimization of Polydisperse Chemical Mixtures using Molecular Descriptors* and attributes that exact entry to Massole et al. (2023).
- Citation URL: [ChemRxiv source](https://chemrxiv.org/engage/chemrxiv/article-details/653a018348dad231205e586a) — taken directly from the paper link on the BNGLViz `Massole_2023` entry; **warning: PMID unresolved**; [PubMed search](https://pubmed.ncbi.nlm.nih.gov/?term=%22Optimization+of+Polydisperse+Chemical+Mixtures+using+Molecular+Descriptors%22).
- Citation comparison: original `reference` agrees with the audited value.
- Citation mismatch: `pmid`: `no id` → removed in favor of the audited ChemRxiv URL — `no id` is not a digits-only PubMed identifier and the exact-title PubMed search did not establish one; **review required**.

## Harmon2017

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_functions`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action at line 272 of `antigen_pulses_harmon2017.bngl`.
- Review insertion: `default_sim_command: ode` — the first active simulation at line 278 is `simulate(...)` with `method=>"ode"`.
- Review legacy placement: the source stores audited feature keys under `compatibility`; those entries were preserved, but the audited values were written under the schema-defined top-level `features` mapping.
- Citation year: `2017`.
- Citation reference: `Harmon et al., 2017` — the BNGL `@reference` header gives the full title *Timescale separation of positive and negative signaling creates history-dependent responses to IgE receptor stimulation* and its Harmon-led authorship.
- Citation PMID: `29138425` — PubMed search for the exact title and authors supplied by the BNGL header resolves to this record; [PubMed](https://pubmed.ncbi.nlm.nih.gov/29138425/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.

## BaruaFceRI2012

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_functions`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_multiple_identical_sites: true` — the active molecule-type declaration `L(l,l)` repeats component `l` at line 77 of `BaruaFceRI_2012.bngl`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action at line 201.
- Review insertion: `default_sim_command: ode` — the first active simulation is `simulate_ode(...)` at line 202.
- Citation year: `2012`.
- Citation reference: `Barua & Goldstein, 2012` — BNGLViz pairs `BaruaFceRI_2012.bngl` specifically with “A mechanistic model of early FcεRI signaling with lipid rafts,” distinguishing it from the separate Barua BCR model.
- Citation PMID: `23284735` — taken directly from the PubMed link on the BNGLViz `BaruaFceRI_2012` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/23284735/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.

## ChylekTCR2014

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_energy`, `uses_functions`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.
- Review insertion: `uses_multiple_identical_sites: true` — active declarations `Lig1(aCD28,aCD28)` and `Lig3(aCD3,aCD3)` repeat component names at lines 166 and 168 of `ChylekTCR_2014.bngl`.
- Citation year: `2014`.
- Citation reference: `Chylek et al., 2014` — BNGLViz pairs `ChylekTCR_2014.bngl` with *Phosphorylation site dynamics of early T-cell receptor signaling*, the same title and authors given in the BNGL header.
- Citation PMID: `25147952` — taken directly from the PubMed link on the BNGLViz `ChylekTCR_2014` entry; [PubMed](https://pubmed.ncbi.nlm.nih.gov/25147952/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.
