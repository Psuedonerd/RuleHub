# Model Explanation: Blinov egfr

## One-sentence summary

A compact EGFR example showing receptor-ligand binding and receptor complex formation.

## What the model shows

This model is a small EGFR-centered rule-based example. It shows how ligand engagement and receptor binding states can be represented as receptor complexes rather than as a single on/off variable.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

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

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
