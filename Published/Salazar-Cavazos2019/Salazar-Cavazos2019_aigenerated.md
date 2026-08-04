# Model Explanation: Salazar-Cavazos 2019 MCF10A EGFR

## One-sentence summary

EGF-stabilized EGFR dimers move through active and receiver conformations that determine site-specific phosphorylation and adaptor recruitment.

## What the model shows

This selected MCF10A-cell model represents epidermal growth factor receptor (EGFR) activation with several dimer and kinase states. GRB2 is growth factor receptor-bound protein 2, and SHC1 is an adaptor protein with a phosphotyrosine-binding domain.

## Biological story

EGF binds EGFR and stabilizes dimers. Receptors occupy asymmetric kinase roles, phosphorylate Y1068, Y1173, and additional tail sites, then recruit GRB2 or SHC1. Ligand-dependent dimer lifetimes shape the duration of phosphorylation.

## Main biological players

EGF, EGFR monomers and dimers, active and receiver kinase states, phosphotyrosines Y1068/Y1173, GRB2, and SHC1.

## Mechanism in plain English

Ligand-bound receptors dimerize and adopt catalytic or receiver roles. Active dimers phosphorylate multiple tail sites. GRB2 recognizes phosphorylated Y1068, while SHC1 binds its preferred phosphorylated site. Rapid phosphate turnover and dimer dissociation compete with adaptor binding, connecting receptor lifetime to downstream recruitment.

## Key modeled events

- EGF binds EGFR and stabilizes receptor dimers.
- Dimers adopt active and receiver kinase conformations.
- EGFR tails become phosphorylated at Y1068, Y1173, and other sites.
- GRB2 and SHC1 bind their corresponding phosphotyrosines.

## What the model measures

Readouts separate ligand-bound receptor, monomeric and dimeric EGFR, active/receiver dimers, individual phosphotyrosines, unphosphorylated receptor, and GRB2/SHC1-bound receptor.

## Expected behavior in plots

Ligand-bound dimers should rise before phosphotyrosines and adaptor complexes. Active/receiver dimer populations should predict the phosphorylation pulse, while GRB2 and SHC1 recruitment may differ because their docking sites turn over differently.

## Caveats

This is one cell-line member of a larger calibrated collection. It does not extend adaptor recruitment through Ras, ERK, or transcription.
