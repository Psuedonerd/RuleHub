# Model Explanation: Yang 2008

## One-sentence summary

Trivalent ligand crosslinks bivalent receptors into reversible aggregates whose size is controlled by saturation and crosslinking propensity.

## What the model shows

This network-free aggregation model studies how multivalent binding produces a sol–gel transition. With its default subcritical parameters, it provides a clean comparison between stochastic aggregate formation and mean-field predictions for bond counts and free-site fractions.

## Biological story

A three-site ligand captures a two-site receptor, then uses another arm to recruit a receptor from a different complex. Repeated capture builds branched aggregates, while bond dissociation breaks them apart. Changing ligand saturation or crosslinking propensity can move the system from small clusters toward a macroscopic aggregate.

## Main biological players

Trivalent ligand, bivalent receptor, ligand–receptor bonds, free ligand sites, free receptor sites, and branched aggregates.

## Mechanism in plain English

The first bond captures a receptor with free ligand. A receptor-bound ligand then crosslinks a receptor belonging to another complex, avoiding rings. Any bond can dissociate. The competition among available sites, crosslinking, and dissociation determines equilibrium connectivity and proximity to the percolation threshold.

## Key modeled events

- Free ligand captures an available receptor site.
- A bound ligand uses a remaining arm to crosslink a separate receptor complex.
- Repeated crosslinking builds branched receptor aggregates without rings.
- Bond dissociation releases sites and limits aggregate growth.

## What the model measures

Readouts measure free ligand and receptor, total ligand–receptor bonds, and free sites on both partners. These quantities summarize aggregate formation without enumerating every cluster topology.

## Expected behavior in plots

From the all-free state, bond counts should rise rapidly while free ligand and receptor sites fall toward equilibrium. At the default below-threshold setting, these curves should stabilize without wholesale depletion into a gel; increasing crosslinking propensity would deepen site depletion and enlarge aggregates.

## Caveats

The partners are abstract and all sites are equivalent. The model excludes rings, membrane geometry, downstream receptor signaling, and biochemical heterogeneity.
