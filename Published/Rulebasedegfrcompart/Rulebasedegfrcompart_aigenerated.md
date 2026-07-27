# Model Explanation: Rule based EGFR compartments

## One-sentence summary

Compartment-resolved EGF–EGFR signaling links membrane dimerization to receptor and Shc phosphorylation.

## What the model shows

This model separates extracellular ligand, membrane receptor, and cytoplasmic adaptor pools while following the early EGFR activation sequence. EGF-bound receptors dimerize, phosphorylate two tyrosines, and recruit Shc, which itself becomes phosphorylated.

## Biological story

Extracellular EGF engages membrane EGFR. Ligand-occupied receptors pair through their transmembrane region and phosphorylate Y1068 and Y1173. Cytoplasmic Shc binds phosphorylated Y1173 and is modified while receptor and Shc phosphatases continually reverse activation.

## Main biological players

EGF, EGFR, receptor tyrosines Y1068 and Y1173, cytoplasmic Shc, and Grb2 as a declared but unused adaptor.

## Mechanism in plain English

EGF binding creates dimerization-competent EGFR. Receptor dimers phosphorylate both tyrosines, while constitutive dephosphorylation removes those marks. Shc recognizes phosphorylated Y1173, becomes phosphorylated while receptor-bound, and can dissociate into the cytoplasm before being dephosphorylated.

## Key modeled events

- Extracellular EGF binds membrane EGFR.
- Ligand-bound EGFR forms reversible membrane dimers.
- Dimerization enables phosphorylation of Y1068 and Y1173.
- Shc binds Y1173, becomes phosphorylated, and returns to the cytoplasmic pool.

## What the model measures

Readouts follow total receptor and extracellular ligand, EGFR dimers, phosphorylation at each receptor tyrosine, total receptor phosphorylation, cytoplasmic Shc, and phosphorylated cytoplasmic Shc.

## Expected behavior in plots

Dimers should rise soon after EGF binding, followed by Y1068 and Y1173 phosphorylation. Phosphorylated Shc should lag behind Y1173 because it requires receptor docking and modification; dephosphorylation should limit all three phosphotyrosine signals.

## Caveats

Only the first receptor/adaptor layer is active. Grb2 is declared but not used, and Ras–ERK signaling, receptor trafficking, and degradation are omitted.
