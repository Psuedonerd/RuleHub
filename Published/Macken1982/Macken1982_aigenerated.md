# Model Explanation: Macken 1982

## One-sentence summary

Trivalent ligands crosslink bivalent receptors into finite branched aggregates below a sol–gel transition.

## What the model shows

This model tests classical multivalent aggregation theory by following ligand capture, receptor crosslinking, and bond dissociation. Its default regime remains below gelation, making small aggregate abundances and equilibrium free-site fractions directly comparable with branching-process predictions.

## Biological story

A three-armed ligand first captures a receptor, then its remaining arms recruit receptors belonging to other complexes. Receptors provide two ligand-binding positions, so repeated crosslinking builds branched structures. Bonds can break, and intracomplex ring closure is excluded, preserving tree-like aggregates.

## Main biological players

Trivalent ligand, bivalent receptor, ligand–receptor bonds, free binding sites, and finite branched aggregates.

## Mechanism in plain English

Free ligand arms bind free receptor sites. Once a ligand is receptor-bound, another available arm can capture a receptor from a different complex and expand the aggregate. Every bond dissociates with the same loss process. Ligand saturation and crosslinking propensity together determine whether most material remains small or approaches a macroscopic connected cluster.

## Key modeled events

- Free trivalent ligand captures an available site on a bivalent receptor.
- Additional ligand arms crosslink receptors from separate complexes, creating branches.
- Ligand–receptor bonds dissociate and release binding sites.
- Ring closure is excluded so aggregate statistics follow branching theory.

## What the model measures

Measurements include free ligand and receptor, total bonds, free sites on each partner, and selected small aggregates such as one-ligand/one-receptor pairs, trimers, and three-receptor stars.

## Expected behavior in plots

At the default subcritical setting, bonds and small aggregates should rise from the all-free state and settle within a few hundred seconds. Free-site readouts should fall toward equilibrium, while the selected small complexes remain appreciable rather than disappearing into a system-spanning aggregate.

## Caveats

The theory-oriented model assumes identical sites and excludes rings. It does not represent receptor signaling, membrane geometry, or molecular differences within an aggregate.
