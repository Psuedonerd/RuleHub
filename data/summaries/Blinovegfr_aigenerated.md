# Model Explanation: Blinov egfr

## One-sentence summary

A compact EGFR example showing receptor-ligand binding and receptor complex formation.

## What the model shows

This model is a small EGFR-centered rule-based example. It shows how ligand engagement and receptor binding states can be represented as receptor complexes rather than as a single on/off variable.

## Biological story

Blinov egfr is a compact receptor-complex example. It is useful for understanding how EGFR occupancy and receptor association can be modeled without including a large downstream network.

## Main biological players

EGF ligand, EGFR receptor, receptor binding sites, and compartment or membrane context if used by the model.

## Mechanism in plain English

Ligand associates with receptor, receptors can occupy different binding states, and the model tracks the formation and loss of receptor-containing complexes. The purpose is to demonstrate EGFR complex formation in a compact form rather than a full downstream signaling network.

## Key modeled events

- Ligand binding shifts EGFR from free receptor toward ligand-associated receptor complexes.
- Receptor interaction states are tracked as complexes rather than as a single active/inactive switch.
- The model emphasizes the formation and loss of receptor-containing assemblies as the central EGFR behavior.

## What the model measures

The readouts follow receptor or ligand-containing patterns and show how much receptor is free, ligand-associated, or complexed over time.

## Expected behavior in plots

Plots mainly distinguish free receptor from ligand-associated or complexed receptor. The important behavior is redistribution among receptor states, not a full signaling cascade.

## Caveats

Because this is a small EGFR example, biological interpretation should stay close to receptor binding and complex formation.
