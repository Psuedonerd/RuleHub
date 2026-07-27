# Model Explanation: Kozer 2013

## One-sentence summary

EGF binding drives higher-order EGFR oligomerization, kinase-tail association, and receptor phosphorylation.

## What the model shows

This model connects ligand occupancy to EGFR cluster size and phosphorylation. It distinguishes EGF binding to receptors in different oligomeric contexts, extracellular receptor crosslinking, cytosolic-tail activation, tail-to-tail association, and phosphorylation, allowing receptor clustering and signaling output to be compared directly.

## Biological story

EGFR can bind EGF as a monomer or within a crosslinked assembly. Ligand occupancy favors an open cytosolic conformation; open tails associate and phosphorylate receptor tyrosines. Receptor contacts can close within pre-existing assemblies, producing rings and oligomers beyond dimers.

## Main biological players

EGF, EGFR ectodomains, EGFR cytosolic kinase/juxtamembrane contacts, and phosphorylated EGFR tyrosines.

## Mechanism in plain English

EGF first occupies receptor ectodomains with affinities that depend on neighboring receptor occupancy. Ectodomain contacts join receptors, including closure reactions within larger assemblies. Ligand-bound receptors switch their cytosolic tails into an active conformation, active tails associate, and one tail phosphorylates another. Deactivation and dephosphorylation counter these processes.

## Key modeled events

- EGF binds free and crosslinked EGFR with context-dependent affinity.
- EGFR ectodomains form dimers and higher-order closed assemblies.
- Ligand occupancy promotes an active cytosolic-tail conformation and tail association.
- Associated active tails phosphorylate EGFR, while dephosphorylation removes the signal.

## What the model measures

Measurements include free EGF, free EGFR, total receptor-cluster density, monomers, dimers, trimers, larger oligomers, and phosphorylated EGFR.

## Expected behavior in plots

Increasing EGF should reduce free receptor and redistribute EGFR from monomers toward dimers and larger clusters. Phosphorylated EGFR should track the ligand-supported active-tail population, while cluster-size curves can reveal whether higher-order oligomers become prominent at the chosen dose.

## Caveats

The model concentrates on receptor assembly and phosphorylation. It does not follow downstream adaptor pathways, trafficking, degradation, or transcriptional responses.
