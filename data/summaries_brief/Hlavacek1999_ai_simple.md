# Model Explanation: Hlavacek 1999

## One-sentence summary

Steric hindrance in multivalent ligand binding to cell-surface receptors.

## What the model shows

This model shows how receptor binding to a multivalent ligand becomes progressively harder as already-bound receptors physically occupy space on the ligand surface. It is a steric-exclusion model rather than a detailed signaling pathway.

## Biological story

Hlavacek 1999 is a physical accessibility model. As receptors occupy a multivalent ligand surface, they make nearby binding sites harder to use, so binding capacity falls below the naive independent-site expectation.

## Main biological players

A multivalent ligand with many equivalent binding sites, monovalent cell-surface receptors, receptor occupancy classes, and steric hindrance.

## Mechanism in plain English

Free ligand binds receptors one at a time. Each bound receptor covers part of the ligand surface, reducing the probability that another receptor can bind nearby. As occupancy increases, the effective number of available sites drops below the simple count of unoccupied sites.

## Key modeled events

- A multivalent ligand gains receptors one at a time as receptor sites bind to available ligand surface.
- Each bound receptor covers physical space, reducing the chance that another nearby receptor can attach.
- The model therefore predicts less high-occupancy binding than would be expected from independent identical sites.

## What the model measures

The readouts track ligand species with different numbers of bound receptors. The model shows how steric crowding limits high-occupancy multivalent binding.

## Expected behavior in plots

Plots should show occupancy classes of ligand. If high-occupancy classes are suppressed compared with a non-steric model, that is the steric hindrance effect.

## Caveats

The model addresses geometric crowding in multivalent binding. It does not include downstream signaling or receptor movement beyond the steric approximation.
