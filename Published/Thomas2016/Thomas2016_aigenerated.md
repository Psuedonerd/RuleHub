# Model Explanation: Thomas 2016 trivalent-ligand fitting example

## One-sentence summary

A trivalent ligand crosslinks bivalent receptors, producing a dose-dependent bound fraction used for parameter estimation.

## What the model shows

This fitting example represents multivalent ligand–receptor aggregation. ECF means extracellular fluid, and the model rescales molecule numbers to a sampled fraction of a cell.

## Biological story

A free three-site ligand captures a receptor, then another ligand arm recruits a receptor from a different complex. Bonds dissociate, so ligand concentration and the two association strengths determine equilibrium receptor occupancy.

## Main biological players

Trivalent ligand, bivalent receptor, free ligand, ligand–receptor bonds, and extracellular volume scaling.

## Mechanism in plain English

The first association step captures receptor with free ligand. A tethered ligand uses a remaining site for crosslinking, while a common dissociation process reverses either contact. A ligand-dose scan converts bound ligand into a normalized fractional response for fitting.

## Key modeled events

- Free ligand binds the first receptor site.
- A bound ligand arm crosslinks an additional receptor.
- Ligand–receptor bonds dissociate reversibly.
- A concentration scan samples equilibrium binding across ligand doses.

## What the model measures

Readouts report total receptor, total ligand, free ligand, the bound fraction, and a scaled fluorescence-like response.

## Expected behavior in plots

At low ligand, the bound fraction should rise with dose. Intermediate concentrations favor crosslinking, while high dose can shift occupancy toward independently bound receptors. The fitted response scale changes magnitude without changing binding chemistry.

## Caveats

The partners are abstract and ring formation is excluded. The example is designed for parameter fitting rather than downstream receptor biology.
