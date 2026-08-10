# Model Explanation: Faeder 2009 EGFR tutorial

## One-sentence summary

EGF-induced EGFR dimerization creates two phosphotyrosine docking routes for Grb2 and Shc.

## What the model shows

This tutorial-scale model presents the core early EGFR mechanism: ligand binding, receptor dimerization, phosphorylation of two receptor tyrosines, direct Grb2 recruitment, and Shc recruitment and phosphorylation. It is useful for comparing receptor assembly with site-specific signaling output.

## Biological story

EGF engages EGFR and brings receptors together. Dimerization enables phosphorylation at Y1 and Y2. Grb2 binds the first modified site, whereas Shc binds the second and is phosphorylated, creating two distinct adaptor branches from the same receptor dimer.

## Main biological players

EGF, EGFR, receptor sites Y1 and Y2, Grb2, and Shc.

## Mechanism in plain English

Ligand binds receptor reversibly and occupied receptors dimerize. Within dimers, both regulatory tyrosines gain phosphate and lose it through constitutive reversal. Grb2 directly docks on phosphorylated Y1. Shc docks on phosphorylated Y2, becomes phosphorylated, and can remain associated or dissociate according to its state.

## Key modeled events

- EGF binds EGFR and promotes reversible receptor dimerization.
- Dimerized receptors phosphorylate Y1 and Y2.
- Grb2 docks directly on phosphorylated Y1.
- Shc binds phosphorylated Y2 and becomes phosphorylated.

## What the model measures

Measurements include total ligand, receptor, Grb2, and Shc; receptor dimers; and phosphorylation of Y1, Y2, and both sites combined.

## Expected behavior in plots

Receptor dimers should rise first after ligand engagement. Y1 and Y2 phosphorylation should follow together because both require dimers, while adaptor occupancy would be inferred from depletion or complex populations rather than a dedicated plotted signal. Dephosphorylation should establish a finite plateau.

## Caveats

The site names are generic teaching labels, and the model stops before SOS, Ras, or ERK. It illustrates early receptor logic rather than a complete EGFR pathway.
