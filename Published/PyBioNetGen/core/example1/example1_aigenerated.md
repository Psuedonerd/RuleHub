# Model Explanation: PyBioNetGen EGFR example

## One-sentence summary

EGF-dependent EGFR oligomerization links receptor cluster size to cytosolic-tail activation and phosphorylation.

## What the model shows

This PyBioNetGen reference example follows epidermal growth factor (EGF) binding to its receptor (EGFR), higher-order receptor assembly, kinase-tail association, and receptor phosphorylation.

## Biological story

EGF binds receptors with context-dependent affinity. Occupied receptors form extracellular contacts, their cytosolic tails open and associate, and associated tails phosphorylate one another. Ring closure permits receptor assemblies larger than dimers.

## Main biological players

EGF, EGFR extracellular contacts, EGFR cytosolic tails, receptor oligomers, and phosphorylated receptor tyrosines.

## Mechanism in plain English

Ligand capture changes receptor crosslinking and favors an open tail conformation. Receptor ectodomains and tails make reversible contacts, including closure within existing assemblies. Tail association enables phosphorylation, while deactivation and dephosphorylation oppose the signal.

## Key modeled events

- EGF binds monomeric and clustered EGFR.
- Receptor ectodomains form dimers and higher-order assemblies.
- Ligand occupancy opens cytosolic tails and permits tail association.
- Associated tails phosphorylate EGFR tyrosines.

## What the model measures

Readouts include free EGF and EGFR, receptor monomers, dimers, trimers and tetramers, overall cluster density, and phosphorylated EGFR.

## Expected behavior in plots

Ligand addition should reduce free receptor and increase dimers before larger oligomers accumulate. Phosphorylated EGFR should follow formation of active tail pairs, while cluster-size curves reveal how material partitions among oligomers.

## Caveats

This is one reference example selected from a broad software-support collection. It ends at receptor phosphorylation and omits trafficking and downstream Ras–ERK signaling.
