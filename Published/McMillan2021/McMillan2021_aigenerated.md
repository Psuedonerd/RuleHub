# Model Explanation: McMillan 2021

## One-sentence summary

Trimeric TNF recruits one, two, or three receptors with affinity that changes at each occupancy step.

## What the model shows

This model isolates sequential binding of a three-position TNF ligand to receptors. By assigning distinct affinities to the first, second, and third recruitment events, it tests how occupancy-dependent binding shapes receptor loading without adding downstream TNF signaling.

## Biological story

Free TNF first captures one receptor. The partially occupied ligand can then recruit a second and finally a third receptor, while every contact can dissociate. Receptor self-association routes are documented but inactive, so TNF occupancy—not ligand-independent receptor dimerization—drives complex formation.

## Main biological players

Trimeric TNF, a receptor with parallel and antiparallel interaction faces, and TNF complexes carrying one, two, or three receptors.

## Mechanism in plain English

Each equivalent face of TNF can bind a receptor. The first event has the strongest affinity, while the second and third use progressively weaker association constants. Dissociation returns receptors to the free pool. Because spontaneous receptor dimerization is disabled, the model cleanly attributes higher receptor occupancy to multivalent TNF.

## Key modeled events

- Free TNF binds the first receptor through any of its three equivalent positions.
- Singly occupied TNF recruits a second receptor with a different affinity.
- Doubly occupied TNF recruits a third receptor through the remaining position.
- Each TNF–receptor contact can dissociate, reversing occupancy.

## What the model measures

Readouts separate free TNF, monomeric receptor, and TNF carrying exactly one, two, or three bound receptors.

## Expected behavior in plots

Free TNF should decline as singly occupied complexes appear. Doubly and triply occupied TNF should develop later and may remain less abundant because successive binding steps are weaker; at equilibrium, the four TNF occupancy curves reveal how receptor availability competes with declining affinity.

## Caveats

The model describes ligand–receptor stoichiometry only. It omits receptor activation, membrane organization, internalization, and all downstream inflammatory or apoptotic signaling.
